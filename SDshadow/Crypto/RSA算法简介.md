# RSA算法简介

选择两个大质数p和q，计算出N = p * q 。

计算φ(N) = ( p-1 ) * ( q-1 ) 即N的欧拉函数，然后选择一个e（1 < e < φ(N) ) ，且和 e 和 φ(N) 互素。

取e的模反数为d(逆元)，计算方法:e * d mod (φ(N)) = 1 。

对明文m进行加密:c=m^e%N

c= pow(m，e，N)，得到的c即为密文

对密文c进行解密:m=c^d%N

m= pow(c，d，N)，得到的m即为明文。

---------------------------------------

 p 和 q : 大整数N的两个因子 (factor)

N : 大整数N，我们称之为模数 (modulus)

e 和 d : 互为模反数的两个指数 (exponent)

c 和 m : 分别是密文和明文，这里一般指的是一个十进制的数