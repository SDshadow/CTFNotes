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