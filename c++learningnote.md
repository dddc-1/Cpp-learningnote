# 一、C++基础知识

## 1. 程序的注释
    1. 单行注释使用符号``//``

    2. 多行注释使用符号``/**/``

## 2. 常量
    1. ``#define 常量名 常量值``

    2. ``const 数据类型 常量名 = 常量值``

![alt text](image.png)

## 3. 标识符的命名规则
![alt text](image-1.png)

# 二、数据类型

## 1. 整型
![alt text](image-2.png)

## 2. sizeof关键字
统计所有类型所占内存大小

## 3. 实型（浮点型）
    1. 单精度float
    2. 双精度double
| 数据类型 | 占用空间 | 有效位数 |
|:--------:|:---------:|:-------:|
| float | 4 | 7位有效数字|
| double | 8 | 15-16位有效数字 |

## 4. 字符型
    1. 作用：字符型变量用于显示单个字符
    2. 语法：char ch = 'a';

## 5. 转义字符
常用的有：``\n \\ \t``
![alt text](image-3.png)

## 6. 字符串
c风格字符串:``char 变量名[] = "字符串值"``

c++风格字符串:``string 变量名 = "字符串值"``

## 7. 布尔类型值bool

## 8.数据的输入
    1. 关键字：cin
    2. 语法：cin >> 变量

# 运算符

## 1. 算数运算符

![alt text](image-4.png)
前置递增，++a先加1再参与表达式运算
后置递增，a++先参与表达式计算再加1

## 2. 逻辑运算符
![alt text](image-5.png)

# 三、程序流程结构

## 1. 选择结构
    1. 三目运算符：语法：``表达式1 ？ 表达式2 ：表达式3``

        表达式1为真运行表达式2

        表达式1为假运行表达式3

    2. switch语句：表达式类型只能是整形或者字符型

## 2. 循环结构

## 3. 跳转语句
    1. goto语句：
        语法：goto 标记

# 四、数组

## 1. 一维数组

一维数组名的用途：

![alt text](image-6.png)

## 2. 冒泡排序

![alt text](image-7.png)

# 五、函数

1. 定义

![alt text](image-8.png)

2. 语法
```

返回值类型 函数名 （参数列表）
{

    函数体语句

    return表达式
}

```

3. 函数的声明

![alt text](image-9.png)

4. 函数的分文件编写

![alt text](image-10.png)

# 六、指针

1. 基本概念
   1. 作用：间接访问内存
   2. 内存编号从0开始记录，一般为16进制表示
   3. 可以利用指针变量保存地址

语法：``数据类型 * 变量名;``

2. 空指针和野指针
   1. 空指针：
      1. 用于给指针变量初始化
      2. 空指针是不可以进行访问的
   2. 野指针：指针变量指向非法的内存空间

3. 常量指针和指针常量
   1. 常量指针
   ![alt text](image-12.png)
   2. 指针常量
   ![alt text](image-13.png)

# 七 结构体

1. 结构体是用户自定义的数据类型，允许用户存储不同的数据类型

2. 结构体的定义和使用：
   1. 语法：``struct 结构体名 {结构体成员列表};``
   2. 
   ![alt text](image-14.png)

    ![alt text](image-15.png)

3. 结构体数组
   1. 作用：将自定义的结构体放入到数组中方便维护
   2. 语法：``struct 结构体名 数组名[元素个数] = {{}，{}，{}}; ``

4. 结构体指针
   
   ![alt text](image-16.png)





# C++核心编程

# 1. 内存分模型
- 代码区：存放函数的二进制代码，由操作系统进行管理
- 全局区：存放全局变量和静态变量以及常量
- 栈区：由编译器自动分配释放，存放函数的参数值、局部变量等
- 堆区：由程序员进行分配和释放，若程序员不释放，程序结束时由操作系统回收

## 1.1 程序运行前

![alt text](image-17.png)

![alt text](image-18.png)

- C++在程序运行前分为全局区和代码区
- 代码区特点是只读和共享
- 全局区中存放全局变量、静态变量和常量
- 常量区中存放 const修饰的全局常量 和 字符串常量

## 1.2 程序运行后

![alt text](image-19.png)

![alt text](image-20.png)

## 1.3 new操作符

C++中利用new操作符在堆区开辟数据

语法：``new 数据类型``

利用new创建的数据，会返回数据对应的类型的指针

释放堆区数据用delete，数据类型为数组时用delete[]

# 2. 引用

## 2.1 引用的基本使用：
作用：给变量起别名

语法：``数据类型 &别名 = 原名``

## 2.2 注意事项

引用必须初始化

引用在初始化后不可改变

## 2.3 引用做函数参数

![alt text](image-21.png)

## 2.4 引用做函数返回值

- 作用：引用可以作为函数的返回值存在

- 注意：不要返回局部变量的引用

- 用法：函数调用作为左值

## 2.5 引用的本质

引用的本质在C++内部是一个指针常量

例如：``int& ref = &a``

//自动转换为``int* const ref = &a``，指针常量是指针指向不可以改，也说明为什么引用不可更改

## 2.6 常量引用

- 作用：常量引用主要用来修饰形参，防止误操作
- 在函数参数列表中，可以加const修饰形参，防止形参改变实参


# 3. 函数提高

## 3.1 函数默认参数

注意事项：
- 如果某个位置已经有默认参数，这个位置往后从左到右都必须有默认值

- 如果函数声明有默认参数，函数实现就不能有默认参数（声明和实现只能有一个有默认参数）

## 3.2 函数占位参数
 
 语法：``返回值类型 函数名 （数据类型）{}``

 占位也可以有默认参数

 ## 3.3 函数重载

### 3.3.1 概述

函数重载的满足条件：
- 同一个作用域
- 函数名称相同
- 函数类型不同，或者个数不同，或者顺序不同

注意事项：
- 函数的返回值不可以作为函数重载的条件
```
例如：
void func(){}

int func(){}

```

- 引用作为重载函数

- 函数重载碰到默认参数


# 4 类和对象
C++面向对象的三大特性为：``封装、继承和多态``

C++认为万事万物皆为对象，对象上有其属性和行为

## 4.1 封装

### 4.1.1 封装的意义
- 将属性和行为作为一个整体，表现生活中的事物
- 将属性和行为加以权限控制

语法：``class 类名{  访问权限： 属性 / 行为 }；``

```
class Circle
{
	//访问权限
public:
	//属性(半径)
	int m_r;
	//行为
	double caculateZC()
	{
		return 2 * PI * m_r;
	}
};

int main() {

	//创建圆类的对象，实例化
	Circle c1;

	//属性
	c1.m_r = 10;

	//行为
	double ZC = c1.caculateZC();
	cout << "圆的周长为：" << ZC << endl;
    
    system("pause");
	return 0;
}
```

封装的意义二：
- 类在设计时可以把属性和行为放在不同的权限下，加以控制

访问的权限有三种：

| 访问权限 | 解释 | 特点 | 区别 |
| :-----: | :-----: | :-----: | :-----: |
| public | 公共权限 | 类内可以访问，类外也可以访问 |
| protected | 保护权限 | 类内可以访问，类外不可以访问 | 子类可以访问父类中的保护内容 |
| private | 私有权限 | 类内可以访问，类外不可以访问 |子类不可以访问父类中的保护内容 |

### 4.1.2 struct和class的区别
默认的访问权限不同
- struct的默认访问权限为共有
- class的默认权限为私有

### 4.1.3 成员属性设置为私有

优点1：将所有的成员属性设置为私有，可以自己控制读写权限

优点2：对于写权限，可以检测数据的有效性


## 4.2 对象的初始化和清理

### 4.2.1 构造函数和析构函数
对象的初始化和清理

- 构造函数：主要作用在于创建对象时为对象的成员属性赋值，构造函数由编译器自动调用，无需手动调用
- 析构函数：主要作用在于对象销毁前系统自己调用，执行一些清理工作

构造函数语法：``类名(){}``
1. 构造函数，没有返回值也不写void
2. 函数名称与类名相同
3. 构造函数可以有参数，因此可以发生重载
4. 程序在调用对象的时候会自动调用构造，无需手动调用，而且只会调用一次

析构函数语法：``~类名(){}``
1. 析构函数，没有返回值也不写void
2. 函数名称与类名相同，在名称前加上符号~
3. 析构函数不可以有参数，因此不可以发生重载
4. 程序在调用对象的时候会自动调用析构，无需手动调用，而且只会调用一次

### 4.2.2 构造函数的分类及调用
两种分类方式：
- 按参数分为：有参构造和无参构造
- 按类型分为：普通构造和拷贝构造

三种调用方式：
- 括号法
- 显示法
- 隐式转换法

```
#include<iostream>;
using namespace std;

//分类
//按照参数分类  无参构造（默认构造）和有参构造
//按照类型分类  普通构造   拷贝构造
class Person
{
public:
	//构造函数
	Person()
	{
		cout << "person 的无参构造函数调用" << endl;
	}
	Person(int a)
	{
		age = a;
		cout << "person 的有参构造函数调用" << endl;
	}
	//拷贝构造函数
	Person(const Person &p)
	{
		//将传入人身上的属性，拷贝到当前对象身上
		age = p.age;
		cout << "person 的拷贝构造函数调用" << endl;
	}


	//析构函数
	~Person()
	{
		cout << "person 的析构函数调用" << endl;
	}

	int age;
};

void test()
{
	//1.括号法
	Person p1;//默认构造法
	Person p2(18);//有参构造法
	Person p3(p2);//拷贝造法

	//注意事项1
	//Person p1();程序会认为是函数声明，不会认为在创建对象


	//2.显示法
	Person p1;
	Person p2 = Person(18);//有参构造
	Person P3 = Person(p2);//拷贝构造

	//Person(10);//匿名对象，当前执行结束后，系统会立即回收掉匿名对象

	//注意事项2
	//不要用拷贝构造函数初始化匿名对象，编译器会认为Person (p3) == Person p3;(对象声明)

	//3.隐式括号法
	Person p4 = 10;//有参构造  相当于写了Person p4 = Person(10);
	Person p5 = p4;//拷贝构造
}

int main()
{
	test();

	system("pause");
	return 0;
}

```

### 4.2.3 拷贝构造函数的调用时机

- 使用一个已经创建完毕的对象来初始化一个新对象
- 值传递的方式给函数参数传值
- 以值方式返回局部变量

```
#include<iostream>;
using namespace std;

class Person
{
public:
	Person()
	{
		cout << "Person的默认构造函数调用" << endl;
	}
	Person(int age)
	{
		m_age = age;
		cout << "Person的有参构造函数调用" << endl;
	}
	Person(const Person &p)
	{
		m_age = p.m_age;
		cout << "Person的拷贝构造函数调用" << endl;
	}

	~Person()
	{
		cout << "Person的析构函数调用" << endl;
	}

	int m_age;
};

//已创建完毕的对象初始化另一个对象
void test01()
{
	Person p1;
	Person p2(p1);
}
//值传递的方式给函数参数传值
void dowork(Person p)
{

}

void test02()
{
	Person p;
	dowork(p);
}
//以值方式返回局部变量(这里未调用拷贝函数的原因：返回值优化)

Person dowork2()
{
	Person p1;
	cout << "p1的地址为：" << (int*) & p1 << endl;
	return p1;
}
void test03()
{
	Person p = dowork2();
	cout << "p的地址为：" << (int*)&p << endl;
}

int main()
{
	//test01();
	//test02();
	test03();

	system("pause");
	return 0;
}
```

### 4.2.4 构造函数调用规则
![alt text](image-22.png)

调用规则如下：
- 如果用户定义有参构造函数、c++不在提供默认无参构造，但是会提供默认拷贝构造
- 如果用户定义拷贝构造函数、c++不会再提供其他构造函数

### 4.2.5 深拷贝与浅拷贝

- 浅拷贝：简单的赋值操作
- 深拷贝：在堆区重新申请空间，进行拷贝工作

![alt text](image-23.png)

![alt text](image-24.png)

### 4.2.6 初始化列表
C++提供了初始化列表语法，用来初始化属性

语法：``构造函数():属性值1(值1),属性值2(值2)...{}``

### 4.2.7 类对象作为类成员
C++类中的成员可以是另一个类的对象，我们称该成员为对象成员

例如
```
class A{}

class B
{
	A a;
}

```
![alt text](image-25.png)

### 4.2.8 静态成员
静态成员就是在成员变量和成员函数前加上关键字静态、称为静态成员

![alt text](image-26.png)

静态成员变量两种访问方式：
- 通过对象
- 通过类名

![alt text](image-27.png)

静态成员函数两种访问方式：
- 通过对象
- 通过类名

## 4.3 C++对象模型和this指针

### 4.3.1 成员变量和成员函数分开存储
在C++中，类内的成员变量和成员函数分开存储

只有非静态成员变量才属于类的对象上

### 4.3.2 this指针概念
this指针用途：（this指针的本质是指针常量，指针的指向不可以修改）
- 当形参和成员变量同名时，可用this指针来区分
- 在类的非静态成员函数中返回对象本身，可使用``return *this``

![alt text](image-30.png)
![alt text](image-28.png)
![alt text](image-29.png)

### 4.3.3 空指针访问成员函数
C++中空指针也是可以调用成员函数的，但是也要注意有没有用到This指针

如果用到This指针，需要加以判断保证代码的健壮性

### 4.3.4 const修饰成员函数
![alt text](image-31.png)
常函数和常对象的例子：
```
//常函数
class Person
{
public:
	//this指针的本质是指针常量，指针的指向不可以修改
	//const Person* const this
	//在成员函数后面加const，修饰的是This指向，让指针指向的值也不可以修改
	void showperson() const
	{
		this->m_b = 100;
		//this->m_a = 100;
		//this = NULL;      //this指针不可以修改指针指向
	}

		void func()
	{

	}

	int m_a;
	mutable int m_b;   //特殊函数，即使在常函数中也可以修改这个值，加上关键字mutable
};

//常对象
void test02()
{
	const Person p;//在对象前加const，变为常对象
	//p.m_a = 100;
	p.m_b = 100;//m_b是特殊值，在常对象下也可以修改

	//常对象只能调用常函数
	p.showperson();
	//p.func();//常对象不可以调用普通成员函数，因为普通成员函数可以修改属性

}
```

## 4.4 友元
友元的关键字：``friend``
- 全局函数做友元
- 类做友元
- 成员函数做友元

1. 全局函数做友元
```
class Person
{
	friend void myfriend(Person* p);

public:
	string sittingroom = "客厅";

private:
	string bedroom = "卧室";

};

void myfriend(Person *p)
{
	cout << "正在访问：" << p->sittingroom << endl;
	cout << "正在访问：" << p->bedroom << endl;
}

void test02()
{
	Person p1;
	myfriend(&p1);
}
```
2. 类做友元
```
//类做友元
class Building;
class Goodfri
{
public:
	Goodfri();

	void visit();//参观函数 用来访问building中的属性

	Building* building;

};

class Building
{
	friend class Goodfri;
public:
	Building();
	string sittingroom;

private:
	string bedroom;

};

Building::Building()
{
	sittingroom = "客厅";
	bedroom = "卧室";
}

Goodfri::Goodfri()
{
	building = new Building;

}

void Goodfri::visit()
{
	cout << "好朋友正在访问：" << building->sittingroom << endl;
	cout << "好朋友正在访问：" << building->bedroom << endl;
}

void test01()
{
	Goodfri p1;
	p1.visit();
	
}
```
3. 成员函数做友元
```
#include<iostream>
using namespace std;

class Building;
class Goodfriend
{
public:

	Goodfriend();

	void visit01();//让visit01可以访问building中私有成员
	void visit02();//让visit02不可以访问building中私有成员

	Building* building;


};

class Building
{
	//告诉编译器 Goodfriend类中的visit01函数 是Building的好朋友，可以访问私有内容
	friend void Goodfriend::visit01();
public:
	Building();
	string sittingroom;

private:
	string bedroom;
};
//类外实现成员函数

Building::Building()
{
	sittingroom = "客厅";
	bedroom = "卧室";
}

Goodfriend::Goodfriend()
{
	building = new Building;
}

void Goodfriend::visit01()
{
	cout << "visit01函数正在访问：" << building->sittingroom << endl;
	cout << "visit01函数正在访问：" << building->bedroom << endl;
}

void Goodfriend::visit02()
{
	cout << "visit02函数正在访问：" << building->sittingroom << endl;
	//cout << "visit函数正在访问：" << building->bedroom << endl;
}

void test01()
{
	Goodfriend p1;
	p1.visit01();
	p1.visit02();

}


int main()
{
	test01();

	system("pause");
	return 0;
}
```

## 4.5 运算符重载
运算符重载概念:对已有的运算符重新进行定义，赋予其另一种功能，以适应不同的数据类型

### 4.5.1 加号运算符重载
作用:实现两个自定义数据类型相加的运算

```
#include<iostream>
using namespace std;

class Person
{
public:
	int m_a;
	int m_b;

	//通过成员函数重载+号
	/*Person operator+(Person& p)
	{
		Person temp;
		temp.m_a = this->m_a + p.m_a;
		temp.m_b = this->m_b + p.m_b;
		return temp;
	}*/

};

//通过全局函数重载+号
Person operator+(Person& p1, Person& p2)
{
	Person temp;
	temp.m_a = p1.m_a + p2.m_a;
	temp.m_b = p1.m_b + p2.m_b;
	return temp;
}

Person operator+(Person& p, int a)
{
	Person temp;
	temp.m_a = p.m_a + a;
	temp.m_b = p.m_b + a;
	return temp;
}

void test01()
{
	Person p1;
	p1.m_a = 10;
	p1.m_b = 20;

	Person p2;
	p2.m_a = 10;
	p2.m_b = 20;

	//成员函数原理
	//Person p3 = p1.operator+(p2);
	
	//全局函数原理
	//Person p3 = operator+(p1, p2);
	//Person p3 = p1 + p2;


	//相当于Person p3 = operator+(p1,10);
	Person p3 = p1 + 10;

	cout << p3.m_a << endl;
	cout << p3.m_b << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
- 总结一：对于内置的数据类型的表达式的运算符是不可能改变的
- 总结二：不要滥用运算符重载

### 4.5.2 左移运算符重载
作用：可以输出自定义数据类型
```
#include<iostream>
using namespace std;

class Person
{
	friend ostream& operator<<(ostream& cout, Person& p);

public:
	Person(int a, int b) :m_a(a), m_b(b){}

private:
	int m_a;
	int m_b;

};

//不能写成员函数原因，p.operator<<(cout)相当于p << cout 不是我们想要的

//想要实现链式法则输出，就需要返回一个值cout
//cout<<p1 相当于 operator<<(cout,p)
ostream& operator<<(ostream &cout,Person &p)
{
	cout << "p.m_a = " << p.m_a << "  p.m_b = " << p.m_b << endl;
	return cout;
}

void test01()
{
	Person p1(10, 20);
	Person p2(20, 30);
	//链式法则
	cout << p1 << p2;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 4.5.3 **递增运算符重载**

```
#include<iostream>
using namespace std;

class MyInteger
{
public:
	MyInteger()
	{
		m_num = 0;
	}
public:
	//前置递增运算符重载
	MyInteger& operator++()
	{
		++m_num;
		return *this;
	}

	//后置递增运算符重载
	//void operator++(int)   int代表占位参数，可以用于区分前置和后置递增
	MyInteger operator++(int)
	{
		//先记录当时的结果
		MyInteger temp = *this;
		//后递增
		m_num++;
		//最后将记录结果返回
		return temp;
	}

	int m_num;
};
//MyInteger myinteger这里不用引用的原因：后置递增运算符时返回值为局部变量temp,重载函数结束就会释放
// 非常量引用的初始值必须为左值（左值是指表达式结束后依然存在的持久对象）
ostream& operator<<(ostream& cout, MyInteger myinteger)
{
	cout << "m_num = " << myinteger.m_num << endl;
	return cout;
}

void test()
{
	MyInteger myinteger;
	cout << myinteger++ << endl;
	cout << "m_num = " << myinteger.m_num << endl;

}

int main()
{
	test();

	system("pause");
	return 0;
}
```

### 4.5.4 赋值运算符重载
C++编译器至少给一个类添加4个函数

- 默认构造函数(无参，函数体为空)
- 默认析构函数(无参，函数体为空)
- 默认拷贝构造函数，对属性进行值拷贝
- 赋值运算符运算符=，对属性进行值拷贝

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题
```
#include<iostream>
using namespace std;

class Person
{
public:
	Person(int a)
	{
		m_age = new int(a);
	}

	Person(const Person &p)
	{
		 m_age = new int(*p.m_age);
	}
	//考虑到链式法则实现 a = b = c,这里不用void operator=(Person& p)
	Person& operator=(Person& p)
	{
		//编译器是提供浅拷贝
		//m_age = p.m_age;

		//先判断是否有属性在堆区，有先释放干净，再深拷贝
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
		//深拷贝
		m_age = new int(*p.m_age);
		return *this;
	}

	~Person()
	{
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
	}
	int *m_age;
};

void test()
{
	Person p1(18);
	Person p2(20);
	Person p3(30);
	p3 = p2 = p1;

	cout << "p1.m_a = " << *p1.m_age << endl;
	cout << "p2.m_a = " << *p2.m_age << endl;
	cout << "p3.m_a = " << *p3.m_age << endl;
}

int main()
{
	test();
	system("pause");
	return 0;
}
```

### 4.5.5 关系运算符重载
作用:重载关系运算符，可以让两个自定义类型对象进行对比操作
```
#include<iostream>
using namespace std;

class Person
{
public:
	Person(string name, int age)
	{
		m_name = name;
		m_age = age;
	}

	bool operator==(Person& p)
	{
		if (m_name == p.m_name && m_age == p.m_age)
		{
			return true;
		}
		return false;
	}

	string m_name;
	int m_age;
};

void test()
{
	Person p1("dc", 22);
	Person p2("dc", 20);

	if (p1 == p2)
	{
		cout << "p1和p2是同一个人" << endl;
	}
	else
	{
		cout << "p1和p2不是同一个人" << endl;
	}
}

int main()
{
	test();

	system("pause");
	return 0;
}
```

### 4.5.6 函数调用运算符重载
- 函数调用运算符()也可以重载
- 由于重载后使用的方式非常像函数的调用，因此称为仿函数
- 仿函数没有固定写法，非常灵活

```
#include<iostream>
using namespace std;

class Myprint
{
public:
	//重载函数调用运算符
	void operator()(string test)
	{
		cout << test << endl;
	}
};

//仿函数非常灵活，没有固定的写法
//加法类

class Myadd
{
public:
	int operator()(int a, int b)
	{
		return a + b;
	}
};

void Myprint02(string test)
{
	cout << test << endl;
}

void test()
{
	Myprint myprint;
	
	myprint("hello world");//由于使用起来非常类似于函数调用，因此又称为：仿函数

	Myprint02("hello world");//函数调用
}

void test02()
{
	Myadd myadd;

	int add = myadd(10, 20);
	cout << "add = " << add << endl;

	//匿名函数对象
	cout << Myadd()(100, 100) << endl;
}

int main()
{
	//test();
	test02();

	system("pause");
	return 0;
}
```

## 4.6 继承
继承是面向对象三大特性之一

语法：``class A:public B;``

- A类称为 子类或派生类
- B类称为 父类或基类

![alt text](image-33.png)

![alt text](image-32.png)

### 4.6.2 继承方式
继承的语法：``class 子类: 继承方式 父类``

继承方式一共有三种：
- 公共继承
- 保护继承
- 私有继承

![alt text](image-34.png)

### 4.6.3 继承中的对象模型

```
#include<iostream>
using namespace std;

class Base
{
public:
	int m_a;
protected:
	int m_b;
private:
	int m_c; //私有成员只是被隐藏了，但是还是会被继承下去

};

class son :public Base
{
public:
	int a;
};

void test()
{
	//16
	cout << "sizeof(son) = " << sizeof(son) << endl;
}

int main()
{
	test();
	system("pause");
	return 0;
}
```

利用开发人员命令提示工具查看对象模型
1. 跳转盘符
2. 跳转文件路径
3. dir
4. 查看命令``cl /dl reportSingleClassLayout类名 文件名``
5. 在我们的版本中查看命令这样写（不会报错）：
   ``cl /EHsc /d1reportSingleClassLayout类名 文件名``

![alt text](image-35.png)

### 4.6.4 继承中的构造顺序
总结:继承中先调用父类构造函数，再调用子类构造函数，构顺序与构造相反

### 4.6.5 继承同名成员处理方式

问题:当子类与父类出现同名的成员，如何通过子类对象，访问到子类或父类中同名的数据呢？
- 访问子类同名成员直接访问即可
- 访问父类同名成员需要加作用域
```
#include<iostream>
using namespace std;

class Base
{
public:
	Base()
	{
		m_a = 100;
	}

	void func()
	{
		cout << "Base - func调用" << endl;
	}

	void func(int a)
	{
		cout << "Base - func(int a)调用" << endl;
	}

	int m_a;
};

class Son :public Base
{
public:
	Son()
	{
		m_a = 200;
	}

	void func()
	{
		cout << "Son - func调用" << endl;
	}

	int m_a;
};

void test()
{
	Son s1;
	cout << "Son 下 m_a = " << s1.m_a << endl;
	//如果通过子类对象访问到父类中同名成员，需要加作用域
	cout << "Base 下 m_a = " << s1.Base::m_a << endl;
}

void test02()
{
	Son s2;
	s2.Base::func();

	//如果子类中出现和父类同名的成员函数，子类的同名成员会隐藏掉父类中所有同名成员函数
	s2.Base::func(100);
}

int main()
{
	test02();

	system("pause");
	return 0;
}
```
![alt text](image-36.png)

### 4.6.6 继承同名静态成员处理

```
#include<iostream>
using namespace std;

class Base
{
public:

	static void func()
	{
		cout << "Base - func调用" << endl;
	}

	static void func(int a)
	{
		cout << "Base - func(int a)调用" << endl;
	}

	static int m_a;
};
int Base::m_a = 100;

class Son :public Base
{
public:

	static void func()
	{
		cout << "Son - func调用" << endl;
	}

	static int m_a;
};
int Son::m_a = 200;

//同名静态成员属性
void test()
{
	Son s1;
	cout << "通过对象访问" << endl;
	cout << "Son 下 static m_a = " << s1.m_a << endl;
	cout << "Base 下 static m_a = " << s1.Base::m_a << endl;

	cout << "通过类名访问" << endl;
	cout << "Son 下 static m_a =" << Son::m_a << endl;
	cout << "Base 下 static m_a = " << Son::Base::m_a << endl;
}

//同名静态成员函数
void test02()
{
	Son s2;
	cout << "通过对象访问" << endl;
	s2.func();
	s2.Base::func();
	s2.Base::func(100);

	cout << "通过类名访问" << endl;
	Son::func();
	Son::Base::func();
	Son::Base::func(100);
}

int main()
{
	test02();

	system("pause");
	return 0;
}
```
总结:同名静态成员处理方式和非静态处理方式一样，只不过有两种访问的方式(通过对象和通过类名)

### 4.6.7 多继承语法
C++允许一个类继承多个类

语法：``class 子类：继承方式 父类1，继承方式，父类2...``

多继承可能会引发父类中有同名成员出现，需要加作用域区分

**C++实际开发中不建议用多继承**

### 4.6.8 菱形继承
菱形继承概念：
- 两个派生类继承同一个基类
- 又有某个类同时继承者两个派生类
- 这种继承被称为菱形继承，或者钻石继承

![alt text](image-37.png)
菱形继承问题：
1. 羊继承了动物的数据，驼同样继承了动物的数据，当草泥马使用数据时，就会产生二义性.
2. 草泥马继承自动物的数据继承了两份，其实我们应该清楚，这份数据我们只需要一份就可以.

```
#include<iostream>
using namespace std;

class Animals
{
public:
	int m_Age;
};

//利用虚继承解决菱形继承的问题 virtual
//继承之前加上关键字虚拟变为虚继承
//动物类称为虚基类
class Sheep:virtual public Animals{};

class Tuo :virtual public Animals{};

class Sheeptuo :public Sheep, public Tuo{};


void test()
{
	Sheeptuo s1;

	s1.Sheep::m_Age = 18;
	s1.Tuo::m_Age = 28;
	//当菱形继承，两个父类拥有相同数据，需要加以作用域区分
	cout << "s1.Sheep::m_Age = "<< s1.Sheep::m_Age <<endl;
	cout << "s1.Tuo::m_Age = " << s1.Tuo::m_Age << endl;
	cout << "s1.m_Age = " << s1.m_Age << endl;
}


int main()
{
	test();

	system("pause");
	return 0;
}
```

![alt text](image-38.png)

总结：
- 菱形继承带来的主要问题是子类继承两份相同的数据，导致资源浪费以及毫无意义
- 利用虚继承可以解决菱形继承问题