# ESP定律脱壳

例：buuctf 新年快乐
用ollydgb打开发现

查壳出UPX壳，用ollydbg打开发现popad，于是在popad后的第一个jmp后下断点，F9运行到此处，直接F8，找到OEP，右键脱壳，ida查看发现反编译正常了

![image-20240423232817150](./../pictures/image-20240423232817150.png)