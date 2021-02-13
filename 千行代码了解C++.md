//C++核心编程代码集合
//内存分区模型：
//代码区：存放函数体的二进制代码，由操作系统进行管理的。
//全局区，存放全局变量和静态变量以及常量
//栈区：由编译器自动分配释放，存放函数的参数值，局部变量等
//堆区：由程序员分配和释放，若程序员不释放，程序结束时由操作系统回收。
//代码区：
//​		存放 CPU 执行的机器指令
//​		代码区是**共享**的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可
//​		代码区是**只读**的，使其只读的原因是防止程序意外地修改了它的指令
//全局区：
//​		全局变量和静态变量存放在此.
//​		全局区还包含了常量区, 字符串常量和其他常量也存放在此.
//​ 该区域的数据在程序结束后由操作系统释放
//#include<iostream>
//using namespace std;
//
全局变量
//int g_a = 10;
//int g_b = 10;
全局常量
//const int c_g_a = 10;
//const int c_g_b = 10;
//
//int main()
//{
//	//局部变量
//	int a = 10;
//	int b = 10;
//	//打印地址
//	cout << "局部变量a的地址为：" << (int)&a << endl;
//	cout << "局部变量b的地址为：" << (int)&b << endl;
//
//	cout << "全局变量g_a的地址为：" << (int)&g_a << endl;
//	cout << "全局变量g_b的地址为：" << (int)&g_b << endl;
//
//	//静态变量
//	static int s_a = 10;
//	static int s_b = 10;
//	cout << "静态变量s_a地址为： " << (int)&s_a << endl;
//	cout << "静态变量s_b地址为： " << (int)&s_b << endl;
//
//	cout << "字符串常量地址为： " << (int)&"hello world" << endl;
//	cout << "字符串常量地址为： " << (int)&"hello world1" << endl;
//
//	cout << "全局常量c_g_a地址为： " << (int)&c_g_a << endl;
//	cout << "全局常量c_g_b地址为： " << (int)&c_g_b << endl;
//
//	const int c_l_a = 10;
//	const int c_l_b = 10;
//	cout << "局部常量c_l_a地址为： " << (int)&c_l_a << endl;
//	cout << "局部常量c_l_b地址为： " << (int)&c_l_b << endl;
//	system("pause");
//	return 0;
//}

//C++ 程序运行前分代码区和全局区
//代码区共享与只读
//全局区存放全局变量，静态变量，常量
//常量区存放const修饰的全局常量和字符串常量

//不要返回局部变量的地址，栈区开辟的数据由编译器自动释放
//#include<iostream>
//using namespace std;
//int * func()
//{
//	int a = 10;
//	return &a;
//}
//
//int main() {
//	int * p = func();
//	cout << *p << endl;
//	cout << *p << endl;//编译器是由保留的。
//	system("pause");
//	return 0;
//}

//堆区：由程序员分配释放，若程序员不释放，程序结束时由操作系统回收
//在C++中主要利用ｎｅｗ在堆区开辟内存
//#include<iostream>
//using namespace std;
//
//int * func()
//{
//	int * a = new int(10);
//	return a;
//}
//
//int main()
//{
//	int * p = func();
//	cout << *p << endl;
//	cout << *p << endl;
//	delete p;
//	system("pause");
//	return 0;
//}

//#include<iostream>
//using namespace std;
//
//int main()
//{
//	int * arr = new int[10];
//	for (int i = 0; i < 10; i++)
//	{
//		arr[i] = i + 100;
//	}
//
//	for (int i = 0; i < 10; i++)
//	{
//		cout << arr[i] << endl;
//	}
//
//	delete[] arr;
//
//	system("pause");
//	return 0;
//}

//引用：给变量起别名
//#include<iostream>
//using namespace std;
//
//int main() {
//	int a = 10;
//	int &b = a;
//	cout << a << endl;
//	cout << b << endl;
//	b = 100;
//	cout << a << endl;
//	cout << b << endl;
//	system("pause");
//	return 0;
//}
//修改引用的变量值，原变量值也会发生改变

//引用必须初始化
//引用在初始化后，不可以改变

//#include<iostream>
//using namespace std;
//
//int main()
//{
//	int a = 10;
//	int b = 20;
//	int &c = a;
//	c = b;
//
//	cout << a << endl;
//	cout << b << endl;
//	cout << c << endl;
//	system("pause");
//	return 0;
//}

//引用可以做函数参数，从而让形参修饰实参，参数会发生改变。
//#include<iostream>
//using namespace std;
//
值传递
//void mySwap01(int a, int b)
//{
//	int temp = a;
//	a = b;
//	b = temp;
//}
地址传递
//void mySwap02(int *a, int *b)
//{
//	int temp = *a;
//	*a = *b;
//	*b = temp;
//}
引用传递
//void mySwap03(int &a, int &b)
//{
//	int temp = a;
//	a = b;
//	b = temp;
//}
//
//int main()
//{
//	int a = 10;
//	int b = 20;
//
//	mySwap01(a, b);
//	cout << a << '\t' << b << endl;
//
//	mySwap02(&a, &b);
//	cout << a << '\t' << b << endl;
//
//	mySwap03(a, b);
//	cout << a << '\t' << b << endl;
//	system("pause");
//	return 0;
//}
//通过引用参数产生的效果同按地址传递是一样的。引用的语法更清楚简单

//引用是可以作为函数的返回值存在的
//注意：**不要返回局部变量引用**
//用法：函数调用作为左值

//#include<iostream>
//using namespace std;
//
返回局部变量引用
//int & test01() {
//	int a = 10;
//	return a;
//}
返回静态变量引用
//int & test02() {
//	static int a = 20;
//	return a;
//}
//
//int main()
//{
//	int& ref = test01();
//	cout << ref << endl;
//	cout << ref << endl;
//
//	int& ref2 = test02();
//	cout << ref2 << endl;
//	cout << ref2 << endl;
//
//	test02() = 1000;
//	cout << ref2 << endl;
//	cout << ref2 << endl;
//	system("pause");
//	return 0;
//}

//引用的本质是在C++内部是一个指针常量
//#include<iostream>
//using namespace std;
//
//void fun(int& ref)
//{
//	ref = 100;
//}
//
//int main() {
//	int a = 10;
//	//int *const ref = &a
//	int& ref = a;
//	//*ref = 20;
//	ref = 20;
//	cout << a << endl;
//	cout << ref << endl;
//	fun(a);
//	system("pause");
//	return 0;
//}

//引用使用的场景，通常用来修饰形参
//#include<iostream>
//using namespace std;
//
//void showValue(const int& v) {
//	//v += 10;
//	cout << v << endl;
//}
//
//int main() {
//
//	//int& ref = 10;  引用本身需要一个合法的内存空间，因此这行错误
//	//加入const就可以了，编译器优化代码，int temp = 10; const int& ref = temp;
//	const int& ref = 10;
//
//	//ref = 100;  //加入const后不可以修改变量
//	cout << ref << endl;
//
//	//函数中利用常量引用防止误操作修改实参
//	int a = 10;
//	showValue(a);
//
//	system("pause");
//
//	return 0;
//}
//函数的默认参数
//#include<iostream>
//using namespace std;
//
//int func(int a, int b = 10, int c = 10) {
//	return a + b + c;
//}
1. 如果某个位置参数有默认值，那么从这个位置往后，从左向右，必须都要有默认值
2. 如果函数声明有默认值，函数实现的时候就不能有默认参数
//int func2(int a = 10, int b = 10);
//int func2(int a, int b) {
//	return a + b;
//}
//
//int main() {
//
//	cout << "ret = " << func(20, 20) << endl;
//	cout << "ret = " << func(100) << endl;
//
//	system("pause");
//
//	return 0;
//}

//函数重载
//函数名可以相同提高复用性
//在同一个作用域下，函数名称相同，函数参数的类型、个数、顺序不同
//#include<iostream>
//using namespace std;
//
 函数重载需要函数都在同一个作用域下
//void func()
//{
//	cout << "func 的调用！" << endl;
//}
//void func(int a)
//{
//	cout << "func (int a) 的调用！" << endl;
//}
//void func(double a)
//{
//	cout << "func (double a)的调用！" << endl;
//}
//void func(int a, double b)
//{
//	cout << "func (int a ,double b) 的调用！" << endl;
//}
//void func(double a, int b)
//{
//	cout << "func (double a ,int b)的调用！" << endl;
//}
//
函数返回值不可以作为函数重载条件
int func(double a, int b)
{
	cout << "func (double a ,int b)的调用！" << endl;
}
//
//
//int main() {
//
//	func();
//	func(10);
//	func(3.14);
//	func(10, 3.14);
//	func(3.14, 10);
//
//	system("pause");
//
//	return 0;
//}

//#include<iostream>
//using namespace std;
//
函数重载注意事项
1、引用作为重载条件
//
//void func(int &a)
//{
//	cout << "func (int &a) 调用 " << endl;
//}
//
//void func(const int &a)
//{
//	cout << "func (const int &a) 调用 " << endl;
//}
//
//
2、函数重载碰到函数默认参数
//
//void func2(int a, int b = 10)
//{
//	cout << "func2(int a, int b = 10) 调用" << endl;
//}
//
//void func2(int a)
//{
//	cout << "func2(int a) 调用" << endl;
//}
//
//int main() {
//
//	int a = 10;
//	func(a); //调用无const
//	func(10);//调用有const
//
//
//			 //func2(10); //碰到默认参数产生歧义，需要避免
//
//	system("pause");
//
//	return 0;
//}

//封装、继承、多态
//万物皆对象，对象上有其属性和行为
//具有相同性质的对象，抽象为类
//封装：将属性和行为作为一个整体，表现生活中的事物
//将属性和行为加以权限限制
//#include<iostream>
//using namespace std;
圆周率
//const double PI = 3.14;
//
1、封装的意义
将属性和行为作为一个整体，用来表现生活中的事物
//
封装一个圆类，求圆的周长
class代表设计一个类，后面跟着的是类名
//class Circle
//{
//public:  //访问权限  公共的权限
//
//		 //属性
//	int m_r;//半径
//
//			//行为
//			//获取到圆的周长
//	double calculateZC()
//	{
//		//2 * pi  * r
//		//获取圆的周长
//		return  2 * PI * m_r;
//	}
//};
//
//int main() {
//
//	//通过圆类，创建圆的对象
//	// c1就是一个具体的圆
//	Circle c1;
//	c1.m_r = 10; //给圆对象的半径 进行赋值操作
//
//				 //2 * pi * 10 = = 62.8
//	cout << "圆的周长为： " << c1.calculateZC() << endl;
//
//	system("pause");
//
//	return 0;
//}

//#include<iostream>
//using namespace std;
//#include <string>
//
学生类
//class Student {
//public://行为
//	void setName(string name) {
//		m_name = name;
//	}
//	void setID(int id) {
//		m_id = id;
//	}
//
//	void showStudent() {
//		cout << "name:" << m_name << " ID:" << m_id << endl;
//	}
//public://属性
//	string m_name;
//	int m_id;
//};
//
//int main() {
//
//	Student stu;//创建一个具体的对象
//	stu.setName("德玛西亚");
//	stu.setID(250);
//	stu.showStudent();
//
//	system("pause");
//
//	return 0;
//}

//public:公共权限
//protected:保护权限
//private:私有权限
//
//#include<iostream>
//using namespace std;
三种权限
公共权限  public     类内可以访问  类外可以访问
保护权限  protected  类内可以访问  类外不可以访问
私有权限  private    类内可以访问  类外不可以访问
//
//class Person
//{
//	//姓名  公共权限
//public:
//	string m_Name;
//
//	//汽车  保护权限
//protected:
//	string m_Car;
//
//	//银行卡密码  私有权限
//private:
//	int m_Password;
//
//public:
//	void func()
//	{
//		m_Name = "张三";
//		m_Car = "拖拉机";
//		m_Password = 123456;
//	}
//};
//
//int main() {
//
//	Person p;
//	p.m_Name = "李四";
//	//p.m_Car = "奔驰";  //保护权限类外访问不到
//	//p.m_Password = 123; //私有权限类外访问不到
//
//	system("pause");
//
//	return 0;
//}

//struct和class的默认权限不同
//struct默认权限为公共，class的默认权限是私有
//#include<iostream>
//using namespace std;
//class C1
//{
//	int m_A;
//};
//
//struct C2
//{
//	int m_A;
//};
//int main() {
//	C1 c1;
//	C2 c2;
//
//	c2.m_A = 10;
//	system("pause");
//	return 0;
//}

//成员属性设置为私有
//可以自己控制读写权限
//可以检测数据的有效性

//#include<iostream>
//using namespace std;
//#include<string>
//class Person
//{
//public:
//	void setName(string name) {
//		m_Name = name;
//	}
//	string getName()
//	{
//		return m_Name;
//	}
//	//设置年龄
//	void setAge(int age) {
//		if (age < 0 || age > 150) {
//			cout << "你个老妖精!" << endl;
//			return;
//		}
//		m_Age = age;
//	}
//	//获取年龄 
//	int getAge() {
//		return m_Age;
//	}
//	//情人设置为只写
//	void setLover(string lover) {
//		m_Lover = lover;
//	}
//private:
//	string m_Name; //可读可写  姓名
//	int m_Age; //只读  年龄
//	string m_Lover; //只写  情人
//};
//int main() {
//
//	Person p;
//	//姓名设置
//	p.setName("张三");
//	cout << "姓名： " << p.getName() << endl;
//
//	//年龄设置
//	p.setAge(50);
//	cout << "年龄： " << p.getAge() << endl;
//
//	//情人设置
//	p.setLover("苍井");
//	//cout << "情人： " << p.m_Lover << endl;  //只写属性，不可以读取
//
//	system("pause");
//
//	return 0;
//}
//对象的初始化和清理
//构造函数和析构函数
//c++利用了**构造函数**和**析构函数**解决上述问题，这两个函数将会被编译器自动调用，完成对象初始化和清理工作。
//对象的初始化和清理工作是编译器强制要我们做的事情，因此如果**我们不提供构造和析构，编译器会提供**
//**编译器提供的构造函数和析构函数是空实现。
//构造函数：主要作用在于创建对象时为对象的成员属性赋值，构造函数由编译器自动调用，无需手动调用
//析构函数: 主要作用于对象销毁钱系统自动调用，执行一些清理工作。
//构造函数语法：
//没有返回值也不需要写void
//函数名称和类名相同
//构造函数可以有参数，因此可以发生重载
//程序在调用对象的时候会自动的调用构造无需手动调用，而且只会调用一次
//析构函数语法：
//没有返回值也不需要写void
//函数名称与类名相同，在名称前面加上符号~
//析构函数不可以有参数，因此不能发生重载
//程序在对象销毁前会自动调用析构，无需手动调用，而且只会调用一次
//#include<iostream>
//using namespace std;
//
//class Person
//{
//public:
//	//构造函数
//	Person()
//	{
//		cout << "Person的构造函数调用" << endl;
//	}
//	//析构函数
//	~Person()
//	{
//		cout << "Person的析构函数调用" << endl;
//	}
//};
//
//void test01()
//{
//	Person p;
//}
//
//int main() {
//	test01();
//	system("pause");
//	return 0;
//}

//构造函数的分类调用
//分类方式：有参构造、无参构造
//普通构造和拷贝构造
//调用方式：括号法、显示法、隐式转换法

//#include<iostream>
//using namespace std;
//class Person {
//public:
//	//无参（默认）构造函数
//	Person() {
//		cout << "无参构造函数!" << endl;
//	}
//	//有参构造函数
//	Person(int a) {
//		age = a;
//		cout << "有参构造函数!" << endl;
//	}
//	//拷贝构造函数
//	Person(const Person& p) {
//		age = p.age;
//		cout << "拷贝构造函数!" << endl;
//	}
//	//析构函数
//	~Person() {
//		cout << "析构函数!" << endl;
//	}
//public:
//	int age;
//};
//void test01()
//{
//	Person p;
//}
调用有参的构造函数
//void test02() {
//
//	//2.1  括号法，常用
//	Person p1(10);
//	//注意1：调用无参构造函数不能加括号，如果加了编译器认为这是一个函数声明
//	//Person p2();
//
//	//2.2 显式法
//	Person p2 = Person(10);
//	Person p3 = Person(p2);
//	//Person(10)单独写就是匿名对象  当前行结束之后，马上析构
//
//	//2.3 隐式转换法
//	Person p4 = 10; // Person p4 = Person(10); 
//	Person p5 = p4; // Person p5 = Person(p4); 
//
//					//注意2：不能利用 拷贝构造函数 初始化匿名对象 编译器认为是对象声明
//					//Person p5(p4);
//}
//
//int main()
//{
//	
//	/*test01();*/
//	test02();
//	system("pause");
//	return 0;
//
//}

//拷贝构造函数调用时机
//使用一个已经创建完毕的对象来初始化一个新对象
//值传递的方式给函数参数传值
//以值的方式返回局部对象
//#include<iostream>
//using namespace std;
//
//class Person {
//public:
//	Person() {
//		cout << "无参构造函数!" << endl;
//		mAge = 0;
//	}
//
//	Person(int age) {
//		cout << "有参构造函数!" << endl;
//		mAge = age;
//	}
//
//	Person(const Person& p) {
//		cout << "拷贝构造函数!" << endl;
//		mAge = p.mAge;
//	}
//
//	//析构函数在释放内存之前调用
//	~Person() {
//		cout << "析构函数!" << endl;
//	}
//
//public:
//	int mAge;
//
//};
//
1. 使用一个已经创建完毕的对象来初始化一个新对象
//void test01() {
//
//	Person man(100); //p对象已经创建完毕
//	Person newman(man); //调用拷贝构造函数
//	Person newman2 = man; //拷贝构造
//
//						  //Person newman3;
//						  //newman3 = man; //不是调用拷贝构造函数，赋值操作
//}
//
2. 值传递的方式给函数参数传值
相当于Person p1 = p;
//void doWork(Person p1) {}
//void test02() {
//	Person p; //无参构造函数
//	doWork(p);
//}
//
3. 以值方式返回局部对象
//Person doWork2()
//{
//	Person p1;
//	cout << (int *)&p1 << endl;
//	return p1;
//}
//
//void test03()
//{
//	Person p = doWork2();
//	cout << (int *)&p << endl;
//}
//
//
//int main() {
//
//	//test01();
//	test02();
//	//test03();
//
//	system("pause");
//
//	return 0;
//}

//#include<iostream>
//using namespace std;
//
//class Person {
//public:
//	Person() {
//		cout << "无参数调用" << endl;
//		mAge = 0;
//	}
//
//	Person(int a) {
//		mAge = a;
//		cout << "有参数调用" << endl;
//	}
//
//	Person(const Person &a) {
//		mAge = a.mAge;
//		cout << "拷贝调用" << endl;
//	}
//
//	~Person() {
//		cout << "析构函数" << endl;
//	}
//
//public:
//	int mAge;
//
//};
//
//void test01() {
//	Person man(100);
//	Person newman(man);
//	Person newman2 = man;
//}
//
//void doWork(Person p1){}
//void test02() {
//	Person p;
//	doWork(p);
//}
//
//Person doWork2() {
//	Person p1;
//	cout << (int*)&p1 << endl;
//	return p1;
//}
//void test03() {
//	Person p = doWork2();
//	cout << (int*)&p << endl;
//}
//int main() {
//	/*test01();*/
//	/*test02();*/
//	test03();
//	system("pause");
//	return 0;
//}

//构造函数调用规则

//#include<iostream>
//using namespace std;
//class Person {
//public:
//	//无参（默认）构造函数
//	Person() {
//		cout << "无参构造函数!" << endl;
//	}
//	//有参构造函数
//	Person(int a) {
//		age = a;
//		cout << "有参构造函数!" << endl;
//	}
//	//拷贝构造函数
//	Person(const Person& p) {
//		age = p.age;
//		cout << "拷贝构造函数!" << endl;
//	}
//	//析构函数
//	~Person() {
//		cout << "析构函数!" << endl;
//	}
//public:
//	int age;
//};
//
//void test01()
//{
//	Person p1(18);
//	//如果不写拷贝构造，编译器会自动添加拷贝构造，并且做浅拷贝操作
//	Person p2(p1);
//
//	cout << "p2的年龄为： " << p2.age << endl;
//}
//
//void test02()
//{
//	//如果用户提供有参构造，编译器不会提供默认构造，会提供拷贝构造
//	Person p1; //此时如果用户自己没有提供默认构造，会出错
//	Person p2(10); //用户提供的有参
//	Person p3(p2); //此时如果用户没有提供拷贝构造，编译器会提供
//
//				   //如果用户提供拷贝构造，编译器不会提供其他构造函数
//	Person p4; //此时如果用户自己没有提供默认构造，会出错
//	Person p5(10); //此时如果用户自己没有提供有参，会出错
//	Person p6(p5); //用户自己提供拷贝构造
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}
//用户定义有参数构造函数，C++不在提供无参数构造，但是会提供默认拷贝构造
//用户提供了拷贝构造，C++就不会再提供其他构造函数。

//浅拷贝：简单的赋值拷贝操作
//深拷贝：在堆区重新申请空间，进行拷贝操作

//#include<iostream>
//using namespace std;
//class Person {
//
//public:
//	Person() {
//		cout << "无参数构造函数" << endl;
//	}
//
//	Person(int age,int height) {
//		cout << "有参数构造函数" << endl;
//
//		m_age = age;
//		m_height = new int(height);
//	}
//
//	Person(const Person & p) {
//		cout << "拷贝构造函数" << endl;
//
//		m_age = p.m_age;
//		m_height = new int(*p.m_height);
//	}
//
//	~Person() {
//		cout << "析构函数" << endl;
//		if (m_height != NULL) {
//			delete m_height;
//			m_height = NULL;
//		}
//	}
//
//public:
//	int m_age;
//	int* m_height;
//};
//
//void test01() {
//	Person p1(18, 180);
//	Person p2(p1);
//	cout << "p1的年龄：" << p1.m_age << "p1的体重：" << *p1.m_height << endl;
//	cout << "p2的年龄：" << p2.m_age << "p2的体重：" << *p2.m_height << endl;
//
//}
//int main() {
//	test01();
//	system("pause");
//	return 0;
//}
//浅拷贝后，指向同一个内存空间，深拷贝重新开辟一段内存空间用于存放数据。

//初始化列表
//#include<iostream>
//using namespace std;
//class Person {
//public:
//	Person(int a,int b,int c) :m_A(a),m_B(b),m_C(c){}
//	void PrintPerson() {
//		cout << "mA:" << m_A << endl;
//		cout << "mB:" << m_B << endl;
//		cout << "mC:" << m_C << endl;
//	}
//
//private:
//	int m_A;
//	int m_B;
//	int m_C;
//};
//int main() {
//
//	Person p(1, 2, 3);
//	p.PrintPerson();
//
//
//	system("pause");
//
//	return 0;
//}

//#include<iostream>
//using namespace std;
//#include<string>
//
//class Phone
//{
//public:
//	Phone(string name)
//	{
//		m_PhoneName = name;
//		cout << "Phone构造" << endl;
//	}
//
//	~Phone()
//	{
//		cout << "Phone析构" << endl;
//	}
//
//
//public:
//	string m_PhoneName;
//
//};
//
//
//class Person
//{
//public:
//
//	//初始化列表可以告诉编译器调用哪一个构造函数
//	Person(string name, string pName) :m_Name(name), m_Phone(pName)
//	{
//		cout << "Person构造" << endl;
//	}
//
//	~Person()
//	{
//		cout << "Person析构" << endl;
//	}
//
//	void playGame()
//	{
//		cout << m_Name << " 使用" << m_Phone.m_PhoneName << " 牌手机! " << endl;
//	}
//
//public:
//
//	string m_Name;
//	Phone m_Phone;//类对象作为类成员
//
//};
//void test01()
//{
//	//当类中成员是其他类对象时，我们称该成员为 对象成员
//	//构造的顺序是 ：先调用对象成员的构造，再调用本类构造
//	//析构顺序与构造相反
//	Person p("张三", "苹果X");
//	p.playGame();
//
//}
//
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//静态成员：在成员变量和成员函数前加上关键字static，称为静态成员//
//静态成员变量
//所有对象共享一份数据
//在编译阶段分配内存
//类内声明，类外初始化
//静态成员函数
//所有对象共享同一函数
//静态成员函数只能访问静态成员变量

//#include<iostream>
//using namespace std;
//class Person {
//public:
//	static int m_A;
//
//private:
//	static int m_B;
//};
//
//int Person::m_A = 10;
//int Person::m_B = 10;
//
//void test01() {
//	//tongguoduixiang
//	Person p1;
//	p1.m_A = 100;
//	cout << p1.m_A << endl;
//
//	Person p2;
//	p2.m_A = 200;
//	cout << p2.m_A << endl;
//	cout << p1.m_A << endl;
//
//	//tongguoleiming
//	cout << Person::m_A << endl;
//	/*cout << Person::m_B << endl;*/
//}
//
//int main() {
//	test01();
//	system("pause");
//	return 0;
//}

//#include<iostream>
//using namespace std;
//class Person {
//public:
//	static void func() {
//		cout << "func的调用" << endl;
//		m_A = 100;
//	}
//
//	static int m_A;
//	int m_B;
//private:
//	static void func2() {
//		cout << "func2的调用" << endl;
//	}
//};
//int Person::m_A = 10;
//
//void test01() {
//	//tongguoduixiang
//	Person p1;
//	p1.func();
//
//	//tongguoleiming
//	Person::func();
//
//}
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//C++中，类内成员变量和成员函数是分开存储的，只有非静态成员变量才属于类的对象上
//#include<iostream>
//using namespace std;
//
//class Person {
//public:
//	Person() {
//		mA = 0;
//	}
//	int mA;
//
//	static int mB;
//
//	void func() {
//		cout << "ma: " << mA << endl;
//	}
//
//	static void func1() {
//
//	}
//};
//int main() {
//
//	cout << sizeof(Person) << endl;
//
//	system("pause");
//
//	return 0;
//}

//对象指针：this指针指向被调用的成员函数所属于的对象
//重名时，形参和成员变量
//在类的非静态成员函数中返回对象本身。
//#include<iostream>
//using namespace std;
//
//class Person {
//public:
//	Person(int age) {
//		this->age = age;
//	}
//
//	Person& PersonAddPerson(Person p) {
//		this->age += p.age;
//		return *this;
//	}
//
//public:
//	int age;
//};
//void test01() {
//	Person p1(10);
//	cout << p1.age << endl;
//
//	Person p2(10);
//	p2.PersonAddPerson(p1);
//	cout << p2.age << endl;
//}
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//空指针可以调用成员函数，但是如果成员函数用到了this指针，就不可以了
//成员函数后加const我们称为常函数
//常函数内不可以修改成员属性
//成员属性声明是加关键字mutable，在常函数中依然可以修改
//声明对象前加const称该对象为常对象
//常对象只能调用常函数


//#include<iostream>
//using namespace std;
//
//class Person {
//
//public:
//	Person() {
//		m_A = 0;
//		m_B = 0;
//	}
//
//	void ShowPerson()const {
//		this->m_B = 100;
//	}
//	void MyFunu() {
//	}
//public:
//	int m_A;
//	mutable int m_B;
//};
//void test01() {
//	const Person person;
//	cout << person.m_A << endl;
//	person.m_B = 100;
//	/*person.MyFunu();*/
//	person.ShowPerson();
//}
//int main() {
//	test01();
//
//	system("pause");
//	return 0;
//}

//友元：friend，全局函数做友元，成员函数做友元，类做友元
//在程序中，有些私有属性，也想让类外特殊的一些函数或者类进行访问，就需要用到友元的技术
//友元的目的就是让一个函数或者类，访问另一个类中私有成员

#include<iostream>
using namespace std;
#include<string>

//class Building {
//	friend void goodGay(Building * building);//友元
//public:
//	Building()
//	{
//		this->m_SittingRoom = "客厅";
//		this->m_BedRoom = "卧室";
//	}
//public:
//	string m_SittingRoom; //客厅
//
//private:
//	string m_BedRoom; //卧室
//};
//void goodGay(Building * building)
//{
//	cout << "好基友正在访问： " << building->m_SittingRoom << endl;
//	cout << "好基友正在访问： " << building->m_BedRoom << endl;
//}
//void test01()
//{
//	Building b;
//	goodGay(&b);
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//	return 0;
//}

//class Building;
//
//class goodGay
//{
//public:
//
//	goodGay();
//	void visit();
//
//private:
//	Building *building;
//};
//
//
//class Building
//{
//	//告诉编译器 goodGay类是Building类的好朋友，可以访问到Building类中私有内容
//	friend class goodGay;
//
//public:
//	Building();
//
//public:
//	string m_SittingRoom; //客厅
//private:
//	string m_BedRoom;//卧室
//};
//
//Building::Building()
//{
//	this->m_SittingRoom = "客厅";
//	this->m_BedRoom = "卧室";
//}
//
//goodGay::goodGay()
//{
//	building = new Building;
//}
//
//void goodGay::visit()
//{
//	cout << "好基友正在访问" << building->m_SittingRoom << endl;
//	cout << "好基友正在访问" << building->m_BedRoom << endl;
//}
//
//void test01()
//{
//	goodGay gg;
//	gg.visit();
//
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//	return 0;
//}


//class Building;
//class goodGay
//{
//public:
//
//	goodGay();
//	void visit(); //只让visit函数作为Building的好朋友，可以发访问Building中私有内容
//	void visit2();
//
//private:
//	Building *building;
//};
//
//
//class Building
//{
//	//告诉编译器  goodGay类中的visit成员函数 是Building好朋友，可以访问私有内容
//	friend void goodGay::visit();
//
//public:
//	Building();
//
//public:
//	string m_SittingRoom; //客厅
//private:
//	string m_BedRoom;//卧室
//};
//
//Building::Building()
//{
//	this->m_SittingRoom = "客厅";
//	this->m_BedRoom = "卧室";
//}
//
//goodGay::goodGay()
//{
//	building = new Building;
//}
//
//void goodGay::visit()
//{
//	cout << "好基友正在访问" << building->m_SittingRoom << endl;
//	cout << "好基友正在访问" << building->m_BedRoom << endl;
//}
//
//void goodGay::visit2()
//{
//	cout << "好基友正在访问" << building->m_SittingRoom << endl;
//	//cout << "好基友正在访问" << building->m_BedRoom << endl;
//}
//
//void test01()
//{
//	goodGay  gg;
//	gg.visit();
//
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//	return 0;
//}

//#include<iostream>
//using namespace std;
//
//class Person
//{
//	friend ostream& operator<<(ostream& out, Person& p);
//public:
//	Person(int a, int b) {
//		this->m_A = a;
//		this->m_B = b;
//	}
//private:
//	int m_A;
//	int m_B;
//};
//ostream& operator<<(ostream& out, Person& p) {
//	out << "a:" << p.m_A << " b:" << p.m_B << endl;
//	return out;
//}
//void test01() {
//	Person p1(10, 20);
//	cout << p1 << endl;
//}
//int main() {
//	test01();
//	system("pause");
//	return 0;
//}

//#include<iostream>
//using namespace std;
//
//class MyInteger {
//	friend ostream& operator<<(ostream& out, MyInteger p);
//public:
//	MyInteger() {
//		m_Num = 0;
//	}
//	MyInteger& operator++() {
//		m_Num++;
//		return *this;
//	}
//	//后置++
//	MyInteger operator++(int) {
//		//先返回
//		MyInteger temp = *this; //记录当前本身的值，然后让本身的值加1，但是返回的是以前的值，达到先返回后++；
//		m_Num++;
//		return temp;
//	}
//private:
//	int m_Num;
//};
//ostream& operator<<(ostream& out, MyInteger p) {
//	out << p.m_Num;
//}
//void test01() {
//	MyInteger myInt;
//	cout << ++myInt << endl;
//	cout << myInt << endl;
//}
后置++ 先返回 再++
//void test02() {
//
//	MyInteger myInt;
//	cout << myInt++ << endl;
//	cout << myInt << endl;
//}
//int main() {
//
//	test01();
//	//test02();
//
//	system("pause");
//
//	return 0;
//}
//类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题
//#include<iostream>
//using namespace std;
//
//class Person {
//public:
//	Person(int age) {
//		m_Age = new int(age);
//	}
//
//	Person& operator=(Person &p) {
//
//		if (m_Age != NULL)
//		{
//			delete m_Age;
//			m_Age = NULL;
//		}
//		//编译器提供的代码是浅拷贝
//		//m_Age = p.m_Age;
//
//		//提供深拷贝 解决浅拷贝的问题
//		m_Age = new int(*p.m_Age);
//
//		//返回自身
//		return *this;
//	}
//	~Person() {
//		if (m_Age != NULL)
//		{
//			delete m_Age;
//			m_Age = NULL;
//		}
//	}
//
//public:
//	int *m_Age;
//};
//void test01()
//{
//	Person p1(18);
//
//	Person p2(20);
//
//	Person p3(30);
//
//	p3 = p2 = p1; //赋值操作
//
//	cout << "p1的年龄为：" << *p1.m_Age << endl;
//
//	cout << "p2的年龄为：" << *p2.m_Age << endl;
//
//	cout << "p3的年龄为：" << *p3.m_Age << endl;
//}
//
//int main() {
//
//	test01();
//
//	//int a = 10;
//	//int b = 20;
//	//int c = 30;
//
//	//c = b = a;
//	//cout << "a = " << a << endl;
//	//cout << "b = " << b << endl;
//	//cout << "c = " << c << endl;
//
//	system("pause");
//
//	return 0;
//}
//#include<iostream>
//using namespace std;
//
//class Person
//{
//public:
//	Person(string name, int age)
//	{
//		this->m_Name = name;
//		this->m_Age = age;
//	};
//
//	bool operator==(Person & p)
//	{
//		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
//		{
//			return true;
//		}
//		else
//		{
//			return false;
//		}
//	}
//
//	bool operator!=(Person & p)
//	{
//		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
//		{
//			return false;
//		}
//		else
//		{
//			return true;
//		}
//	}
//
//public:
//	string m_Name;
//	int m_Age;
//};
//
//void test01()
//{
//	//int a = 0;
//	//int b = 0;
//
//	Person a("孙悟空", 18);
//	Person b("孙悟空", 18);
//
//	if (a == b)
//	{
//		cout << "a和b相等" << endl;
//	}
//	else
//	{
//		cout << "a和b不相等" << endl;
//	}
//
//	if (a != b)
//	{
//		cout << "a和b不相等" << endl;
//	}
//	else
//	{
//		cout << "a和b相等" << endl;
//	}
//}
//
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}
//#include<iostream>
//using namespace std;
//
//class MyPrint
//{
//public:
//	void operator()(string text)
//	{
//		cout << text << endl;
//	}
//};
//
//void test01()
//{
//	MyPrint myFunc;
//	myFunc("hello");
//}
//
//class MyAdd
//{
//public:
//	int operator()(int v1, int v2)
//	{
//		return v1 + v2;
//	}
//};
//
//void test02()
//{
//	MyAdd add;
//	int ret = add(10, 10);
//	cout << "ret = " << ret << endl;
//
//	//匿名对象调用  
//	cout << "MyAdd()(100,100) = " << MyAdd()(100, 100) << endl;
//}
//
//int main() {
//
//	test01();
//	test02();
//
//	system("pause");
//
//	return 0;
//}

//#include<iostream>
//using namespace std;
//class Base
//{
//public:
//	int m_A;
//protected:
//	int m_B;
//private:
//	int m_C; //私有成员只是被隐藏了，但是还是会继承下去
//};
//
公共继承
//class Son :public Base
//{
//public:
//	int m_D;
//};
//
//void test01()
//{
//	cout << "sizeof Son = " << sizeof(Son) << endl;
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//#include <iostream>
//using namespace std;
//
//class Base {
//public:
//	static void func()
//	{
//		cout << "Base - static void func()" << endl;
//	}
//	static void func(int a)
//	{
//		cout << "Base - static void func(int a)" << endl;
//	}
//
//	static int m_A;
//};
//int Base::m_A = 100;
//class Son :public Base {
//public:
//	static void func()
//	{
//		cout << "Son - static void func()" << endl;
//	}
//	static int m_A;
//};
//int Son::m_A = 200;
//void test01() {
//	cout << "通过对象访问" << endl;
//	Son s;
//	cout << "Son 下m_A = " << s.m_A << endl;
//	cout << "Base 下m_A = " << s.Base::m_A << endl;
//
//	cout << "通过类名访问" << endl;
//	cout << "Son 下m_A = " << Son::m_A << endl;
//	cout << "Son 下m_A = " << Son::Base::m_A << endl;
//}
//int main() {
//
//	test01();
//	/*test02();*/
//
//	system("pause");
//
//	return 0;
//}

//多继承
//#include <iostream>
//using namespace std;
//
//class Base1 {
//public:
//	Base1()
//	{
//		m_A = 100;
//	}
//public:
//	int m_A;
//};
//
//class Base2 {
//public:
//	Base2()
//	{
//		m_A = 200;  //开始是m_B 不会出问题，但是改为mA就会出现不明确
//	}
//public:
//	int m_A;
//};
//
语法：class 子类：继承方式 父类1 ，继承方式 父类2 
//class Son : public Base2, public Base1
//	//class Son : public Base2,public Base1
//{
//public:
//	Son()
//	{
//		m_C = 300;
//		m_D = 400;
//	}
//public:
//	int m_C;
//	int m_D;
//};
//
//
多继承容易产生成员同名的情况
通过使用类名作用域可以区分调用哪一个基类的成员
//void test01()
//{
//	Son s;
//	cout << "sizeof Son = " << sizeof(s) << endl;
//	cout << s.Base1::m_A << endl;
//	cout << s.Base2::m_A << endl;
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//#include <iostream>
//using namespace std;
//
//class Animal
//{
//public:
//	int m_Age;
//};
//
继承前加virtual关键字后，变为虚继承
此时公共的父类Animal称为虚基类
//class Sheep : virtual public Animal {};
//class Tuo : virtual public Animal {};
//class SheepTuo : public Sheep, public Tuo {};
//
//void test01()
//{
//	SheepTuo st;
//	st.Sheep::m_Age = 100;
//	st.Tuo::m_Age = 300;
//
//	cout << "st.Sheep::m_Age = " << st.Sheep::m_Age << endl;
//	cout << "st.Tuo::m_Age = " << st.Tuo::m_Age << endl;
//	cout << "st.m_Age = " << st.m_Age << endl;
//}
//
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//多态：
//静态多态，函数重载、运算符重载属于静态多态。复用函数名
//动态多态，派生类和虚函数实现运行时多态

//静态多态的函数地址早绑定，编译阶段确定函数地址
//动态多态的函数地址晚绑定，运行阶段确定函数地址

//#include <iostream>
//using namespace std;
//
//class Animal
//{
//public:
//	//Speak函数就是虚函数
//	//函数前面加上virtual关键字，变成虚函数，那么编译器在编译的时候就不能确定函数调用了。
//	virtual void speak()
//	{
//		cout << "动物在说话" << endl;
//	}
//};
//
//class Cat :public Animal
//{
//public:
//	void speak()
//	{
//		cout << "小猫在说话" << endl;
//	}
//};
//
//class Dog :public Animal
//{
//public:
//
//	void speak()
//	{
//		cout << "小狗在说话" << endl;
//	}
//
//};
我们希望传入什么对象，那么就调用什么对象的函数
如果函数地址在编译阶段就能确定，那么静态联编
如果函数地址在运行阶段才能确定，就是动态联编
//
//void DoSpeak(Animal & animal)
//{
//	animal.speak();
//}

多态满足条件： 
1、有继承关系
2、子类重写父类中的虚函数
多态使用：
父类指针或引用指向子类对象
//
//void test01()
//{
//	Cat cat;
//	DoSpeak(cat);
//
//
//	Dog dog;
//	DoSpeak(dog);
//}
//
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//#include <iostream>
//using namespace std;
//
普通实现
//class Calculator {
//public:
//	int getResult(string oper)
//	{
//		if (oper == "+") {
//			return m_Num1 + m_Num2;
//		}
//		else if (oper == "-") {
//			return m_Num1 - m_Num2;
//		}
//		else if (oper == "*") {
//			return m_Num1 * m_Num2;
//		}
//		//如果要提供新的运算，需要修改源码
//	}
//public:
//	int m_Num1;
//	int m_Num2;
//};
//
//void test01()
//{
//	//普通实现测试
//	Calculator c;
//	c.m_Num1 = 10;
//	c.m_Num2 = 10;
//	cout << c.m_Num1 << " + " << c.m_Num2 << " = " << c.getResult("+") << endl;
//
//	cout << c.m_Num1 << " - " << c.m_Num2 << " = " << c.getResult("-") << endl;
//
//	cout << c.m_Num1 << " * " << c.m_Num2 << " = " << c.getResult("*") << endl;
//}
//
//
//
多态实现
抽象计算器类
多态优点：代码组织结构清晰，可读性强，利于前期和后期的扩展以及维护
//class AbstractCalculator
//{
//public:
//
//	virtual int getResult()
//	{
//		return 0;
//	}
//
//	int m_Num1;
//	int m_Num2;
//};
//
加法计算器
//class AddCalculator :public AbstractCalculator
//{
//public:
//	int getResult()
//	{
//		return m_Num1 + m_Num2;
//	}
//};
//
减法计算器
//class SubCalculator :public AbstractCalculator
//{
//public:
//	int getResult()
//	{
//		return m_Num1 - m_Num2;
//	}
//};
//
乘法计算器
//class MulCalculator :public AbstractCalculator
//{
//public:
//	int getResult()
//	{
//		return m_Num1 * m_Num2;
//	}
//};
//
//
//void test02()
//{
//	//创建加法计算器
//	AbstractCalculator *abc = new AddCalculator;
//	abc->m_Num1 = 10;
//	abc->m_Num2 = 10;
//	cout << abc->m_Num1 << " + " << abc->m_Num2 << " = " << abc->getResult() << endl;
//	delete abc;  //用完了记得销毁
//
//				 //创建减法计算器
//	abc = new SubCalculator;
//	abc->m_Num1 = 10;
//	abc->m_Num2 = 10;
//	cout << abc->m_Num1 << " - " << abc->m_Num2 << " = " << abc->getResult() << endl;
//	delete abc;
//
//	//创建乘法计算器
//	abc = new MulCalculator;
//	abc->m_Num1 = 10;
//	abc->m_Num2 = 10;
//	cout << abc->m_Num1 << " * " << abc->m_Num2 << " = " << abc->getResult() << endl;
//	delete abc;
//}
//
//int main() {
//
//	//test01();
//
//	test02();
//
//	system("pause");
//
//	return 0;
//#include<iostream>
//using namespace std;
//
//class Base
//{
//public:
//	//纯虚函数
//	//类中只要有一个纯虚函数就称为抽象类
//	//抽象类无法实例化对象
//	//子类必须重写父类中的纯虚函数，否则也属于抽象类
//	virtual void func() = 0;
//};
//
//class Son :public Base
//{
//public:
//	virtual void func()
//	{
//		cout << "func调用" << endl;
//	};
//};
//
//void test01()
//{
//	Base * base = NULL;
//	//base = new Base; // 错误，抽象类无法实例化对象
//	base = new Son;
//	base->func();
//	delete base;//记得销毁
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}
//#include<iostream>
//using namespace std;
//
//class Animal {
//public:
//
//	Animal()
//	{
//		cout << "Animal 构造函数调用！" << endl;
//	}
//	virtual void Speak() = 0;
//
//	//析构函数加上virtual关键字，变成虚析构函数
//	//virtual ~Animal()
//	//{
//	//	cout << "Animal虚析构函数调用！" << endl;
//	//}
//
//
//	virtual ~Animal() = 0;
//};
//
//Animal::~Animal()
//{
//	cout << "Animal 纯虚析构函数调用！" << endl;
//}
//
和包含普通纯虚函数的类一样，包含了纯虚析构函数的类也是一个抽象类。不能够被实例化。
//
//class Cat : public Animal {
//public:
//	Cat(string name)
//	{
//		cout << "Cat构造函数调用！" << endl;
//		m_Name = new string(name);
//	}
//	virtual void Speak()
//	{
//		cout << *m_Name << "小猫在说话!" << endl;
//	}
//	~Cat()
//	{
//		cout << "Cat析构函数调用!" << endl;
//		if (this->m_Name != NULL) {
//			delete m_Name;
//			m_Name = NULL;
//		}
//	}
//
//public:
//	string *m_Name;
//};
//
//void test01()
//{
//	Animal *animal = new Cat("Tom");
//	animal->Speak();
//
//	//通过父类指针去释放，会导致子类对象可能清理不干净，造成内存泄漏
//	//怎么解决？给基类增加一个虚析构函数
//	//虚析构函数就是用来解决通过父类指针释放子类对象
//	delete animal;
//}
//
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}

//#include<fstream>
//
//void test01() {
//	ofstream ofs;
//	ofs.open("test.txt", ios::out);
//	ofs << "姓名：刘强" << endl;
//
//	ofs.close();
//}
//
//int main() {
//	test01();
//	system("pause");
//	return 0;
//}

//#include<fstream>
//#include<string>
//
//void test01() {
//	ifstream ifs;
//	ifs.open("test.txt", ios::in);
//
//	if (!ifs.is_open()) {
//		cout << "文件打开失败！" << endl;
//		return;
//	}
//	
//	char c;
//	while ((c = ifs.get()) != EOF) {
//		cout << c;
//	}
//	ifs.close();
//}
//int main() {
//
//	test01();
//
//	system("pause");
//
//	return 0;
//}


