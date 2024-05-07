# RC4

- 加密：原文和Keystream进行异或得到密文

- 解密：密文和Keystream进行异或得到原文

### 加密过程

step1：对S表进行填充，s[0]=0,s[1]=1,s[2]=2······s[255]=255

step2：用输入的密钥填充另一个256字节的K表

step3：用K表对S表进行初始置换

step4：生成密钥流(keystream)，表S一旦完成初始化，输入的密钥就不再使用

### Keystream生成

密钥流的生成由两部分组成：

1. KSA（the Key-Scheduling Algorithm)
2. PRGA(the Pseudo-Random Generation Algorithm)

### 利用Key生成S盒——The key-scheduling algorithm (KSA)

```c
/* 得到S-box */
int i = 0;
for (i = 0; i < 256; i++) {
    S[i] = i;
    T[i] = puc_key[i % key_length];
}
 
for (i = 0; i < 256; i++) {
    j = (j + S[i] + T[i]) % 256;
    swap_uchar(&S[i], &S[j]); //交换S[i]和S[j]
}
```

### 利用S盒生成密钥流——The pseudo-random generation algorithm(PRGA)

![img](D:\desktop\CTF\CTFNotes\SDshadow\pictures\1344097-20210115114116132-568699983.png)

```c
/* 生成密钥流 Keystream */
int i = 0;
int j = 0;
int t = 0;
unsigned long k = 0;
 
for (k = 0; k < ul_data_length; k++) {
    i = (i + 1) % 256;
    j = (j + puc_sbox[i]) % 256;
    swap_uchar(&puc_sbox[i], &puc_sbox[j]);
    t = (puc_sbox[i] + puc_sbox[j]) % 256;
    puc_key_stream[k] = puc_sbox[t];
}
```

## 代码实现（C语言）

```c
#include<stdio.h>
#include<string.h>
 
#define SBOX_LEN 256
 
#define rc4_encrypt rc4_crypt
#define rc4_decrypt rc4_crypt
 
static inline void swap_uchar(unsigned char *puc_x, unsigned char *puc_y)
{
    *puc_x = *puc_x ^ *puc_y;
    *puc_y = *puc_x ^ *puc_y;
    *puc_x = *puc_x ^ *puc_y;
}
 
void hexdump(unsigned char *puc_data, int length)
{
    int i = 0;
 
    for (i = 0; i < length; i++) {
        printf("%02X", puc_data[i]);
        if (i && (i + 1) % 16 == 0) {
            putchar('\n');
        }
    }
    printf("\n");
}
 
/**
 * 利用Key生成S盒
 * the Key-Scheduling Algorithm
 */
static void rc4_ksa(unsigned char *puc_sbox, unsigned char *puc_key, int key_length)
{
    int i = 0;
    int j = 0;
    char tmp[SBOX_LEN] = {0};
 
    for (i = 0; i < SBOX_LEN; i++) {
        puc_sbox[i] = i;
        tmp[i] = puc_key[i % key_length];
    }
 
    for (i = 0; i < SBOX_LEN; i++) {
        j = (j + puc_sbox[i] + tmp[i]) % SBOX_LEN;
        swap_uchar(&puc_sbox[i], &puc_sbox[j]); //交换puc_sbox[i]和puc_sbox[j]
    }
}
 
/**
 * 利用S盒生成密钥流
 * The pseudo-random generation algorithm(PRGA)
 */
static void rc4_prga(unsigned char *puc_sbox, unsigned char *puc_key_stream, unsigned long ul_data_length)
{
    int i = 0;
    int j = 0;
    int t = 0;
    unsigned long k = 0;
 
    for (k = 0; k < ul_data_length; k++) {
        i = (i + 1) % SBOX_LEN;
        j = (j + puc_sbox[i]) % SBOX_LEN;
        swap_uchar(&puc_sbox[i], &puc_sbox[j]);
        t = (puc_sbox[i] + puc_sbox[j]) % SBOX_LEN;
        /* 为了更清晰理解rc4算法流程，此处保存keystream，不直接进行XOR运算 */
        puc_key_stream[k] = puc_sbox[t];
    }
}
 
/* 加解密 */
void rc4_crypt(unsigned char *puc_data, unsigned char *puc_key_stream, unsigned long ul_data_length)
{
    unsigned long i = 0;
 
    /* 把PRGA算法放在加解密函数中可以不需要保存keystream */
    for (i = 0; i < ul_data_length; i++) {
        puc_data[i] ^= puc_key_stream[i];
    }
}
 
int main(int argc, char *argv[])
{
    unsigned char sbox[SBOX_LEN] = {0};
    char key[SBOX_LEN] = {"abcdefghijklmnopqrstuvwxyz"}; //秘钥内容随便定义
    char data[512] = "lsRJ@.0 lvfvr#9527";
    unsigned char puc_keystream[512] = {0};
    unsigned long ul_data_length = strlen(data);
 
    printf("key=%s, length=%d\n\n", key, strlen(key));
    printf("Raw data string:%s\n", data);
    printf("Raw data hex:\n");
    hexdump(data, ul_data_length);
 
    /* 生成S-box */
    rc4_ksa(sbox, (unsigned char *)key, strlen(key));
 
    /* 生成keystream并保存,S-box也会被更改 */
    rc4_prga(sbox, puc_keystream, ul_data_length);
 
    printf("S-box final status:\n");
    hexdump(sbox, sizeof(sbox));
 
    printf("key stream:\n");
    hexdump(puc_keystream, ul_data_length);
 
    /* 加密 */
    rc4_encrypt((unsigned char*)data, puc_keystream, ul_data_length);
 
    printf("cipher hexdump:\n");
    hexdump(data, ul_data_length);
 
    /* 解密 */
    rc4_decrypt((unsigned char*)data, puc_keystream, ul_data_length);
 
    printf("decypt data:%s\n", data);
 
    return 0;
}
```

### Python

    SBOX_LEN = 256
    
    def swap_uchar(x, y):
        x[0] = x[0] ^ y[0]
        y[0] = x[0] ^ y[0]
        x[0] = x[0] ^ y[0]
    
    def hexdump(data):
        for i, byte in enumerate(data):
            print(f"{byte:02X}", end="")
            if (i + 1) % 16 == 0:
                print()
        print()
    
    def rc4_ksa(sbox, key):
        j = 0
        tmp = [0] * SBOX_LEN
        for i in range(SBOX_LEN):
            sbox[i] = i
            tmp[i] = key[i % len(key)]
        for i in range(SBOX_LEN):
            j = (j + sbox[i] + tmp[i]) % SBOX_LEN
            swap_uchar(sbox[i:i+1], sbox[j:j+1])
    
    def rc4_prga(sbox, data_length):
        key_stream = bytearray(data_length)
        i = j = t = 0
        for k in range(data_length):
            i = (i + 1) % SBOX_LEN
            j = (j + sbox[i]) % SBOX_LEN
            swap_uchar(sbox[i:i+1], sbox[j:j+1])
            t = (sbox[i] + sbox[j]) % SBOX_LEN
            key_stream[k] = sbox[t]
        return key_stream
    
    def rc4_crypt(data, key_stream):
        for i in range(len(data)):
            data[i] ^= key_stream[i]
    
    def main():
        sbox = bytearray(SBOX_LEN)
        key = b"abcdefghijklmnopqrstuvwxyz"  # 随便定义的密钥内容
        data = bytearray(b"lsRJ@.0 lvfvr#9527")
        data_length = len(data)
    	print(f"key={key.decode()}, length={len(key)}\n")
    	print("Raw data string:", data.decode())
    	print("Raw data hex:")