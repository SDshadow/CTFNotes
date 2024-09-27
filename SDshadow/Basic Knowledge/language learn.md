# C++

## 类外重载和类内重载

1.类内重载

```cpp
#include <iostream>
using namespace std;

class Point{
public:
    Point(){};
    Point (int x, int y): x(x),y(y) {};
    Point operator+(const Point &b){ //类内重载，运算符重载函数作为类的成员函数
        Point ret;
        ret.x = this->x + b.x;
        ret.y = this->y + b.y;
        return ret;
    }
    int x,y;
};

int main() {
    Point a(2,4),b(5,3);
    Point c = a + b;      //这里c++编译器会，自动去找 + 运算符的重载函数
	cout<< "x :" << c.x << endl;
    cout<<"y :" << c.y << endl;
```

2.类外重载（用友元函数的方法实现）

```cpp
#include <iostream>
using namespace std;

class Point{
public:
    Point(){};
    Point (int x, int y): x(x),y(y) {};
    friend Point operator+(const Point &, const Point &);   //声明类的友元函数
    int x,y;
};

Point operator+(const Point &a,const Point &b){//类外重载,运算符重载函数作为类的友元函数
    Point ret;
    ret.x = a.x + b.x;
    ret.y = a.y + b.y;
    return ret;
}

int main() {
     Point a(2,4),b(5,3);
    Point c = a + b;
	cout<< "x :" << c.x << endl;
    cout<<"y :" << c.y << endl;
}
```

