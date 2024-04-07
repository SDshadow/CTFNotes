# PHP基础

#### [PHP基础 - Hello CTF](https://ctf.tj.cn/HC_Web/php_basic/#_7)

``````
#example
<?php
class test{
    public $a = 'satoru';
    protected $b = '555';
    private $c = false;
    public function __displayVar()
    {
        echo $this->a;
    }
}
$user=new test();
$e = serialize($user);
$d = unserialize($e);
var_dump($e);
var_dump($d);
?>
``````

1、在上面的代码中，我们定义一个类后，其中的成员变量类型有三种：**public、protected、private**

```php
public：公用的，在整个程序中都可使用；
protected：受保护的，只可在该类及该类的子类中使用；
private：私有的，只可在该类中使用。
```

2、初始化类

```
$user=new test();

```

3、序列化后[字符串](https://so.csdn.net/so/search?q=字符串&spm=1001.2101.3001.7020)的组成

```php
string(75) "O:4:"test":3:{s:1:"a";s:6:"satoru";s:4:" * b";s:3:"555";s:7:" test c";b:0;}"
```

字母	含义
a	array数组
b	bool判断类型
d	double浮点数
i	integer整型
o	common object 一般的对象
r	reference引用类型
s	string字符串类型
C	custom object
O	class
N	null
R	pointer reference
U	unicode string
——————————————
4为属性数量
s为string
1为字符串长度

----------------------------

#### PHP eval() 函数

把字符串当成 PHP 代码来计算：该字符串必须是合法的 PHP 代码，且必须以分号结尾。

