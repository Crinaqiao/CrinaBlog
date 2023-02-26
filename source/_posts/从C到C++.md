---
title: 从C到C++
tags:
  - C
  - C++
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=121
feature: false
date: 2022-08-16 17:35:05
---
# 从C到C++（2022/02/23）

### 一、名称空间 && 输入输出

```cpp
/**
 * 名称空间。
 * 防止名称冲突，在头部使用using namespace后，
 * 代码里就可以不用写std::cout这么复杂
 */
using namespace std;

/**
 * 在C++中，<<表示输出，>>表示输入，endl表示换行
 */
cout << "请输入一个整数：" << endl;
int num = 0;
cin >> num;// 接收输入赋值给num
cout << num;// 输出num
```

### 二、引用参数

```cpp
/**
 * 引用参数，修改引用参数的值会修改原始值
 * @param x
 * @param y
 */
void sum(int &x, int &y) {
    x += y;
    y = x + 1;
    cout << x << &x << " " << y << &y;
}

// 使用
int a = 10;
int b = 20;
cout << a << &a << " " << b << &b;
sum(a, b);
cout << a << &a << " " << b << &b;
```

### 三、函数的默认参数

```cpp
/**
 * 默认参数，有默认值的参数必须放在最右边
 * @param a 必须传
 * @param b 可以不传，不传用默认值
 */
void add(int a, int b = 10) {
    cout << a + b << endl;
}

// 使用
int a = 66, b;
add(a);
add(a, b = 20);
```

### 四、函数重载

```cpp
/**
 * 函数重载。
 * C++允许同一作用域里有同名的函数，只要他们的形参不同
 * 函数名和形参列表构造了函数的签名
 * 函数重载不能根据返回类型区分函数
 */
int fn(int x, int y);

// 类型不同ok
double fn(double x, double y);

// 个数不同ok
int fn(int x);

// 报错：Functions that differ only in their return type cannot be overloaded
//double fn(int x);
```

### 五、函数模板

```cpp
/**
 * 函数模板（泛型算法）:用template关键字增加一个模板头，将数据类型变成类型模板参数
 * 编译器会自动进行类型推断，如果是两个不同类型，可以使用(int)x格式进行指定
 * @tparam T 模板参数1
 * @tparam Y 模板参数2
 * @param x 形参1
 * @param y 形参2
 * @return
 */
template<typename T, typename Y>
Y fn1(T x, Y y) {
    return x + y;
}

// 函数模板使用
cout << fn1(10, 10.12) << endl;
int num1 = 20;
double num2 = 20.21;
cout << fn1(num2, num1) << endl;
```

### 六、C++的string（需要头文件：`#include <string>`）

```cpp
/**
 * C++ String
 */
// 三种定义方式
    string s = "hello", s2("world"), s3{"C++"};
    cout << s << endl << s2 << endl << s3 << endl;
// 可以使用成员访问运算符(.)访问string类的成员
    cout << "s的长度为:" << s.size() << "\n截取s2字符串的1-3:" << s2.substr(1, 3) << "\n给s3追加字符：" << s3.append("真棒") << endl;
    cout << "s字符串中l出现的位置:" << s.find("l") << endl;
    s2.insert(3, "AAA");
    cout << "在s2字符串的第三个位置后插入AAA:" << s2 << endl;
// 用运算符对string对象进行运算
    cout << s[1] << endl;
    cout << s + "你好" << endl;
    s[2] = 'A';
    cout << s << endl;
```

### 七、vector（即向量，需要头文件：`#include <vector>`）

```cpp
/**
 * vector:向量，类似于数组，但是可以动态增长，需要头文件<vector>
 * 是一个类模板，实例化产生一个类，如vector<int>产生一个数据元素是int的vector<int>类（向量）。
*/

// 展示数组的函数
void showArr(vector<int> v) {
    cout << "====展示数组====" << endl;
    for (int i = 0; i < v.size(); ++i) {
        cout << v[i] << endl;
    }
}

vector<int> v = {7, 5, 16, 8};
// push_back(),数组最后面添加一个元素，不返回任何数据
v.push_back(66);
showArr(v);
// pop_back(),删除数组最后一个元素，不返回任何数据
v.pop_back();
showArr(v);
// resize(),重新设置数组的长度，元素数量大于长度会被截断，反之填充数组类型的默认值
v.resize(2);
showArr(v);
v.resize(20);
showArr(v);
```

### 八、C++的动态分配内存空间

```cpp
/**
 * 在C++中，我们使用new关键字来代替malloc函数，使用delete关键字来释放内存
 */
int *pInt = new int;
*pInt = 10;
cout << &pInt << "\t" << pInt << "\t" << *pInt << endl;
// 养成用完就释放的好习惯
delete pInt;

int size = 5;
int *pIntArr = new int[size];
pIntArr[2] = 12;
for (int i = 0; i < size; ++i) {
    cout << pIntArr[i] << endl;
}
// 对于数组，要加上[]，否则只是释放了数组第一个元素的内存
delete[] pIntArr;
```

### 九、C++的类和对象

- 第一种：使用struct创建类
    
    ```cpp
    /**
     * C++可以使用struct创建类，使用时不需要再像C那样使用struct student声明，
     * 可以直接使用student声明
     */
    struct student {
        string name;
        double score;
    
        // 类体内部定义函数
        void show() {
            cout << name << "的成绩是：" << score << endl;
        }
    
        // 类体外部定义函数，在内部声明，外部实现
        void outFn();
    };
    
    // 类体外部定义函数，需要指定类作用域
    void student::outFn() {
        cout << "这是在类体外部实现的函数" << endl;
    }
    
    // 使用
    student stu1;
    stu1.name = "李四";
    stu1.score = 99.5;
    cout << stu1.name << endl;
    stu1.show();
    stu1.outFn();
    ```
    
- 第二种：使用class关键字创建类
    
    定义:
    
    ```cpp
    /**
     * C++也可以用class关键字创建类
     */
    class Animal {
    // 私有成员属性
    private:
        string name;
        string type;
        int age;
    // 公开的成员
    public:
        // Animal的构造函数，跟Java一样，如果我们定义类时没有定义构造函数，C++会默认定义一个无参构造函数
        Animal() {
            cout << "Animal的无参构造函数" << endl;
        }
    
        // 如果我们定义了构造函数，那么默认的无参构造函数就没了，我们必须手动定义无参构造
        Animal(string name, string type, int age) {
            this->name = name;
            this->type = type;
            this->age = age;
            cout << "Animal的全参构造函数" << endl;
        }
    
        // Animal的get/set函数
        void setName(string name) {
            this->name = name;
        }
    
        string getName() {
            return name;
        }
    
        // 展示animal实例
        void show() {
            cout << name << "\t" << type << "\t" << age << endl;
        }
    };
    ```
    
    实例化&&调用:
    
    ```cpp
    Animal animal;
    Animal *pAnimal = new Animal("小黑猫", "猫科", 3);
    pAnimal->show();
    cout << "pAnimal自身的地址：" << &pAnimal << endl;
    cout << "pAnimal指向的地址：" << pAnimal << endl;
    pAnimal->setName("小猴子");
    pAnimal->show();
    string pAnimalName = pAnimal->getName();
    cout << "使用get函数取到的Name：" << pAnimalName << endl;
    ```
    
    控制台输出：
    
    ```cpp
    Animal的无参构造函数
    Animal的全参构造函数
    小黑猫	猫科	3
    pAnimal自身的地址：0x89705ff618
    pAnimal指向的地址：0x27ae5014640
    小猴子	猫科	3
    使用get函数取到的Name：小猴子
    ```
    

### 十、运算符重载、友元函数

- 友元函数：
    
    定义：
    
    ```cpp
    /**
     * C++也可以用class关键字创建类
     */
    class Animal {
    // 私有成员属性
    private:
        string name;
        string type;
        int age;
    // 公开的成员
    public:
        ....
        /**
         * C++控制对类对象私有部分的访问。
         * 通常，公有类方法提供唯一的访问途径，
         * 但是有时候这种限制太严格，
         * 以致于不适合特定的编程问题。
         * 在这种情况下，
         * C++提供了另外一种形式的访问权限：友元。
         * 友元有3种：
         *    友元函数；
         *    友元类；
         *    友元成员函数。
         * @param os
         * @param animal
         * @return
         */
        // 友元函数：通过使用friend关键字让函数成为类的友元，可以赋予该函数与类的成员函数相同的访问权限
        // 重写输出<<
        friend ostream &operator<<(ostream &os, const Animal &animal) {
            os << "name: " << animal.name << " type: " << animal.type << " age: " << animal.age;
            return os;
        }
    };
    ```
    
    使用：
    
    ```cpp
    ....
    // 重写输出流之后我们可以直接使用cout<<来输出animal类的属性
    cout << *pAnimal; // 即 operator<<(cout,*pAnimal);
    ```
    
    控制台输出：
    
    ```cpp
    name: 小猴子 type: 猫科 age: 3
    ```
    

### 十一、String类、拷贝构造函数、析构函数

- 代码
    
    ```cpp
    /**
     * C语言风格的字符串
     */
    class String {
        char *data;
        int n;
    public:
        // 拷贝构造函数
        String(const char *s = 0) {
            if (s == 0) {
                data = 0;
                n = 0;
                return;
            }
            const char *p = s;
            while (*p) { p++; }
            n = p - s;
            // 这里分配了内存，要在析构函数里面销毁
            // 注意：如果我们没有自定义这个拷贝构造函数，在执行类似str=str1这样的操作时，C++会调用默认的拷贝构造函数
            // 即：str.data=str1.data......指向的是同一片空间
            // 这样的操作在我们执行析构函数时，会重复释放空间，造成程序崩溃
            data = new char[n + 1];
            for (int i = 0; i <= n; ++i) {
                data[i] = s[i];
            }
            data[n] = '\0';
        }
    
        // 析构函数
        // 以~符号开头，定义一个析构函数，用于释放分配的内存，这个析构函数会在对象销毁时自动调用
        // 对象销毁的顺序是先创建的后销毁
        ~String() {
            if (data) delete[] data;
        }
    };
    ```
    

### 十二、类模板