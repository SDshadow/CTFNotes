# TEA,XTEA,XXTEA加解密

用的**Feistel分组加密框架**             m                                                       n

![img](D:\桌面\CTF\CTFNotes\SDshadow\pictures\1586953-20220307130936480-855092292.png)

1、首先TEA加密解密是以原文以8字节，所以从两边各自传入四个字节

2、右边传入的4个字节，这里将这4个字节称呼为M，M进行了三个部分的操作，M左移4位与密钥[0]相加，M右移5位与密钥[1]相加，M与δ相加，最后这三个算出的值再异或

3、左边传入的4个字节，这里将这4个字节称呼为N，N=N+M

## TEA算法的实现

```cpp
#include <stdio.h>
#include <stdint.h>
 
//加密函数
void encrypt (uint32_t* v, uint32_t* k) {
    uint32_t v0=v[0], v1=v[1], sum=0, i;           /* set up */
    uint32_t delta=0x9e3779b9;                     /* a key schedule constant */
    uint32_t k0=k[0], k1=k[1], k2=k[2], k3=k[3];   /* cache key */
    for (i=0; i < 32; i++) {                       /* basic cycle start */
        sum += delta;
        v0 += ((v1<<4) + k0) ^ (v1 + sum) ^ ((v1>>5) + k1);
        v1 += ((v0<<4) + k2) ^ (v0 + sum) ^ ((v0>>5) + k3);
    }                                              /* end cycle */
    v[0]=v0; v[1]=v1;
}
 
//解密函数
void decrypt (uint32_t* v, uint32_t* k) {
    uint32_t v0=v[0], v1=v[1], sum=0xC6EF3720, i;  /* set up */
    uint32_t delta=0x9e3779b9;                     /* a key schedule constant */
    uint32_t k0=k[0], k1=k[1], k2=k[2], k3=k[3];   /* cache key */
    for (i=0; i<32; i++) {                         /* basic cycle start */
        v1 -= ((v0<<4) + k2) ^ (v0 + sum) ^ ((v0>>5) + k3);
        v0 -= ((v1<<4) + k0) ^ (v1 + sum) ^ ((v1>>5) + k1);
        sum -= delta;
    }                                              /* end cycle */
    v[0]=v0; v[1]=v1;
}
 
int main()
{
    uint32_t v[2]={1,2},k[4]={2,2,3,4};
    // v为要加密的数据是两个32位无符号整数
    // k为加密解密密钥，为4个32位无符号整数，即密钥长度为128位
    printf("加密前原始数据：%u %u\n",v[0],v[1]);
    encrypt(v, k);
    printf("加密后的数据：%u %u\n",v[0],v[1]);
    decrypt(v, k);
    printf("解密后的数据：%u %u\n",v[0],v[1]);
    return 0;
}
```
