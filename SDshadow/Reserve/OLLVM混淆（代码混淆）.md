## OLLVM混淆（代码混淆）

将源代码复杂化，如

```
#include <stdlib.h>
int main(int argc, char** argv) {
  int a = atoi(argv[1]);
  if(a == 0)
    return 1;
  else
    return 10;
  return 0;
}
```

会变为

```
#include <stdlib.h>
int main(int argc, char** argv) {
  int a = atoi(argv[1]);
  int b = 0;
  while(1) {
    switch(b) {
      case 0:
        if(a == 0)
          b = 1;
        else
          b = 2;
        break;
      case 1:
        return 1;
      case 2:
        return 10;
      default:
        break;
    }
  }
  return 0;
}
```

可以用插件obpo或者d810去除混淆



## Movfuscator

包含大量`mov`指令的代码块

## 花指令

花指令实质就是一串垃圾指令，它与程序本身的功能无关，并不影响程序本身的逻辑。

## 虚拟化