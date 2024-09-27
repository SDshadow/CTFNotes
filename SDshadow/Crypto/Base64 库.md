# Base64 库

**编码字符串到Base64**：

```
import base64

text = "Hello, world!"
encoded_text = base64.b64encode(text.encode('utf-8'))
print(encoded_text.decode('utf-8'))
```

**解码Base64编码的字符串**：

```
import base64

encoded_text = "SGVsbG8sIHdvcmxkIQ=="
decoded_text = base64.b64decode(encoded_text)
print(decoded_text.decode('utf-8'))
```

**编码文件到Base64**：

```
import base64

with open('example.jpg', 'rb') as file:
    encoded_image = base64.b64encode(file.read())
```

**解码Base64编码的文件**：

```
import base64

with open('example.txt', 'r') as file:
    encoded_text = file.read()

decoded_data = base64.b64decode(encoded_text)
with open('decoded_file.jpg', 'wb') as file:
    file.write(decoded_data)
```

**URL安全的Base64编码**：

```
import base64

text = "Hello, world!"
encoded_text = base64.urlsafe_b64encode(text.encode('utf-8'))
print(encoded_text.decode('utf-8'))
```





Python decode() 方法以 *encoding* 指定的编码格式解码字符串。默认编码为字符串编码。

decode()方法语法：

```
str.decode(encoding='UTF-8')
encoding -- 要使用的编码，如"UTF-8"。
```

在 Python 中，文本通常被存储为 Unicode 字符串，而不是特定的字节编码。当你要将文本编码成字节序列（如 Base64 编码）时，你需要选择一个字节编码格式。

如果base解码出来的是b'\x04\xdd\x07e\x96\xd8\x99!w\x0f\xad\x0bH\xfe\xca;\xc0x\xb8\x96\r\xbfS\xcb(\x96\x07\xc4\xaab\x11\x18/\x1e\xf18Um\xaa\xa8\x13\xc1\x1e?\x17`C\x8a\x05?\xed\x8e!tVA\xf3\x1b'

形式的，要用以下的方式来转换成10进制数

Python 中可以直接操作字节串来进行十六进制和十进制之间的转换。下面是一个示例：

```
hex_bytes = b'\x04\xdd\x07e\x96\xd8\x99!w\x0f\xad\x0bH\xfe\xca;\xc0x\xb8\x96\r\xbfS\xcb(\x96\x07\xc4\xaab\x11\x18/\x1e\xf18Um\xaa\xa8\x13\xc1\x1e?\x17`C\x8a\x05?\xed\x8e!tVA\xf3\x1b\xf5 ZAU?tqv\xca\x1fZ\x18N"\xf1\xe5\x8b\xbc\xf5\xd1\x90\xd2U\xfe\xdaw\x08\xedZ\x83\xda04\xbb\xb7H\x0eB\\\'0\xe6\xc5\xcb\x9c \x14G\x15\xea\xc7\xae\xd3\x05\x93\xcc\xa3\x1c\xe1]\xd8G\xf3\x06U\xa3\xb4\x9dXJ\x9e\xce!\x87=\xb9\xcf`\x97\xba\xb2L?d\x13g\xb7S\n\x87~\nC\x94/\x88\xb2\x14h\x81h\xf2*\xa4\xbe\xb3\xfd/\xbd\xf3\x8c\xbb\xfcE^\xbd\x87P\xff3>\xab\\\xc6\x90B\xd5e\x94\x982u\xfe\xd2b\xe8\x1d\xb2k\x0f\x05\x93\x82/\xea\xfa\xe9\xb8\xc9.E\x81\x07\xfd\xef\x85\'vb+5y\xf1ip\x9a\xe5\xf1z\xd9+VZ=\x96\x80:D1;\xa6\xa9\x9d\xb2F\xfc\x91\x01\x8f\xcb\x13\x84P\x0f\xedg\xd3'

# 将十六进制字节串转换为十进制整数
decimal_value = int.from_bytes(hex_bytes, byteorder='big')

print(decimal_value)
```

### 

```
encodecipher="ugd3ja903L5C6AKtyNNLu2r4OQTYhf+uV1OGQke8LgRUkiB+"
cipher=int.from_bytes(base64.b64decode(encodecipher))
print(cipher)
#cipher=361393077702759738807681933145091917163245366270893924102681869074979826951365344764030
```



base64换表脚本

```
import base64
import string

str1 = "x2dtJEOmyjacxDemx2eczT5cVS9fVUGvWTuZWjuexjRqy24rV29q"

string1 = "ZYXABCDEFGHIJKLMNOPQRSTUVWzyxabcdefghijklmnopqrstuvw0123456789+/"
string2 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"

print (base64.b64decode(str1.translate(str.maketrans(string1,string2))))

```

