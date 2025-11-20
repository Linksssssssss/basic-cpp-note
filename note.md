<details> 
    <summary>English words</summary>

# English words
   - literal:常量 
   - default argument：默认参数 
   - assigned to:赋值
   - square brackets：方括号内
   - parenthese:圆括号
   - brace:大括号
   - underscore:下划线
   - encapsulated:封装
   - initialize:初始化	
   - inerface:接口 
   - ternary operator:三元运算符：（A？B：C）
   - pointer arithmetic 指针算数
   - indirection operator：'*'
   - subscript:下标
   - modify:修改  specify: 明确定义
   - pseudocode：伪代码 
   - encompasses:包含
   - block:代码块 {int a="19.06"} 
   - Terminate with a semicolon（分号）:以分号结束
   - stack:栈
   - Manipulat：操作
   - argument:参数、自变量  
   - include guard
   - object of the same class 类的实例化对象
   - terminate 终止
   - derived class 派生类
   - instantiate 实例化
   - insertion 输入
   - extraction  输出
   - cascated 连续调用
   - delimiter 终止符
   - truncated 截取的，缩短的
   - generic programming: 泛型编程
</details>          
<details>
    <summary>选择题话术</summary>

# 选择题话术
   - Software (i.e., the instructions you write) controls hardware (i.e., computers).
 - A multi-core processor implements several processors on a single integrated-circuit chip.
 - ASCII is a popular subset of Unicode
- Interpreted programs run slower than compiled programs.
- C++ functions other than main are executed:When they are explicitly called by another function
- the name of the values the method call passes to the method for the parameters：argument
- Specifying the order in which statements are to be executed in a computer program is called： Program control
- An uninitialized local variable contains: The value last stored in the memory location reserved for that variable
- Having a loop within a loop is known as: nesting
- break and continue statements alter the flow of control: "break" 和 "continue" 语句改变控制流程
- Converting from type int to type char will result in the loss of data

- 

- The preceding include guard prevents the code between #ifndef (which means “if not defined”) and #endif from being included if the name TIME_H has been defined.
- Outside a class’s scope, public class members are referenced through one of the handles on an object—an object name, a reference to an object or a pointer to an object. 
- The object or built-in array is created in the free store (also called the heap)—a region of memory assigned to each program for storing dynamically allocated objects.
-  many of the other for statements in class Array’s implementation with the C++11 range-based for statement. Unfortunately, range-based for does not work with dynamically allocated built-in arrays.
-  A class-scope variable hidden by a block-scope variable can be accessed by preceding the variable name with the class name followed by::
- Every object of the same class gets a copy of every member variable
- There is mechanism in C++ for a constructor to call another constructor in the same class. [C++ includes delegating constructors—that is constructors that can delegate their work to other constructors in the same class.]
- A destructor does not releases the object’s memory. 
- The constructor for a static local object is called only once, when execution first reaches the point where the object is defined.
- In an is-a relationship, an object of a derived class also can be treated as an object of its base class.
- Many languages use alphabets that contain more characters than a single-byte char can represent. The ASCII character set does not provide these characters; the Unicode character set does. Unicode is an extensive international character set that represents the majority of the world’s “commercially viable” languages, mathematical symbols and much more.
- In cpplib <iostream>, both unformatted- and formatted-I/O services are provided.
- The typedef iostream represents a basic_iostream<char> that enables both char input and output.
- Outputs to object cerr are unbuffered, implying that each stream insertion to cerr causes its output to appear immediately—this is appropriate for notifying a user promptly about errors.
- Function eof returns true only after the program attempts to read past the last character in the stream.
- If the specified file does not yet exist, then the ofstream object creates the file, using that filename.
- Prefix increment has slightly more overhead than postfix increment. 前置递增的开销比后置递增大
- Based on whether an operator is implemented as a member function or as a non-member function, the operator is used same in expressions.
- The colon ( : ) in the header of the class definition indicates inheritance.
- A base-class constructor's default arguments are not inherited. Instead, the compiler generatesoverloaded constructors in the derived class.
- Downcasting enables Making a base-class pointer into a derived-class pointer
  - dynamic_cast is often used to Downcast pointers
- C++ files include information about their structure.
- When opening a file, you can specify the name of the file as either a pointer-based string or a string object.
- A random access file is organized most like an Array.
- generic programming: class templates enable you to conveniently specify a variety of related (overloaded) function
- Default type parameters must be the rightmost (trailing) parameters in a template’s type-parameter list. 
- Variables, classes and functions in an unnamed namespace are accessible only in the current translation unit (a .cpp file and the files it includes).


- The typedef istream represents a basic_istream<char> that enables char input.
The typedef ostream represents a basic_ostream<char> that enables char output.
The typedef iostream represents a basic_iostream<char> that enables both char input and output.
- The typedef ifstream represents a specialization of basic_ifstream that enables char input from a file.
The typedef ofstream represents a specialization of basic_ofstream that enables char output to files.
The typedef fstream represents a specialization of basic_fstream that enables char input from, and output to, files.

</details>
<details> 
    <summary>类</summary>

# 类
***class定义的末尾要加上分号*** 
1. 类的属性(attribute)：数据成员(data member), aka成员变量
2. 类的成员函数定义后面加const  如：void message() const      这可以防止该函数修改class的数据成员
3. class中的数据默认是private
4. 类的构造函数(constructor)和析构函数(destructor):构造函数的名称必须与类同名，理论上来说可以放在private里面; default constructor：默认构造函数
   1. explicit:显式构造函数，防止参数传递的时候发生隐式类型转换：比如说double转成int 
   2. 构造函数可以是有参，也可以是无参，不能有返回值
   3. 自定义了构造函数，实例化就必须调用对应的参数列表
   4. 构造函数可以用于类的初始化，但函数中的形参与类的属性无关，构造和析构函数的末端不能加const
   5. 析构函数不能接收任何的参数，也不能返回任何的值
   6. 构造函数可以多次重载，***一个类只能有一个析构函数函数,而且必须放在public作用域内***
   7. 构造函数可以调用自己类的构造函数的重载版本(Delegating Constructors)
   8. 析构函数本身不释放内存，而是进行一些清理的工作
```
class one
{
	explicit one();
    ~ one();
};
void test(){
    one o();
}

//Delegating Constructors
Time::Time()
   Time( 0, 0, 0 ) //delegate to Time( int, int, int )
{
} // end constructor with no arguments

Time::Time( int hour )
   Time( hour, 0, 0 ) //delegate to Time( int, int, int )   
{
} // end constructor with one argument
```
1. 定义类：可以防止双重定义,使用ifndef或者pragma once
```
#ifndef TIME_H
#define TIME_H
 ...
#endif
//这个叫做include guard

# pragma once
```
6.   对象实例化方式：
```
    1. Time t(a,b,c)
    3. Time t={a,b,c}//list initializers 
    4. Time sunset;
    5. array <Time,5> arrayOfTimes;//类数组初始化
    6. Time &DinnerTime= sunset;//引用初始化
    7. Time *timePtr=&DinnerTime;//指针初始化
    8. array[0] = new Time(2,1,3)
```
7. 调用构造/析构函数的时期：
   1. 在全局区的类：在所有函数调用之前构造，在最后析构      
      1. 关于“最后”： main函数执行结束，一般有两种异常：
         1. exit(),when a fatal unrecoverable error occurs
         2. abort()，indicate an abnormal termination of the program
   2. 在local区的类：在local区构造和析构
   3. 静态局部对象（static class c）（***对应的构造函数只执行一次***）：在定义的时候就构造，遇到exit()析构，遇到abort()不析构
   4. staic and global的析构调用顺序为先static后global
8. 返回私有数据成员的引用或者指针，会破坏私有性，该引用或者指针能够修改私有的数据成员
   1. 公有成员函数可以返回对应的私有数据成员的引用
   ```
   public:
        int & geta(){ return a;}
    priavet:
        int a;
   ```
9.  可以通过构造函数逐一赋值：
```
     Time::Time(int a, int b)
        :date(a),month(b){}
```
1.  类中的拷贝构造函数： 
    1. Person p2(p1)： 注意实现的时候不能通过指针地址传递实现
    2. 深拷贝与浅拷贝：是否在代码中写出来
    3. 一定要调用对象的引用，否则会无限构造
    4. 拷贝函数 =delete   :防止调用拷贝构造函数
```
class(const class &); //应当为const引用，保证可以复制const对象
{
    ptr= new int(var); //浅拷贝
}

class a=b//调用默认拷贝构造函数

```
1. 转换构造函数(conversion constructor: **single-argument** construcors)
   1. 可以在user-defined types之间转换
   2. 不会被编译器隐式生成（如果没有显式定义）
   3. 常用于将内置类型转换为user-defined    
```
MyClass::operator char *() const; //将MaClass类转换为char *类，没有返回类型

```
2.   静态成员变量：所用成员共享
     1. 类内声明，类外初始化(C++ 11 允许int和enum类型的静态成员类内初始化)
     2. 静态成员函数：共享
     3. 静态成员函数，不可以访问非静态成员变量 
     4. 空对象占用内存为1，只用非静态成员变量属于某个对象，其他：静态成员变量，非/静态成员函数都不属于某个对象
     5. 访问：
         1.  ***public*** 在类内可以自由访问,类外也可以通过类名、引用、指针的方式访问
         2. ***private*** 类外要通过静态的成员函数进行访问，类内可以自由访问，友元函数也可以访问  
     6. 不能在静态成员函数中使用this指针
     7. ***静态成员变量不能在成员函数（包括静态成员函数）内进行初始化, 也不可以在类的构造函数中初始化***
```
class A{
public:
    static void test1();
private:
    static int b;
};
int A::b=1;
void A::test1(){
    b=2;
}
```
1.   只用常对象能够访问常成员函数:
     1.    常成员函数： void func() const
     2.    常成员函数不能调用非const成员函数
     3.    常数据成员可以通过构造函数初始化
     4.    构造和析构函数不能声明为const
```
const Time noon(a,1,2);
```
1.   mutable：修饰类的成员变量，使得该成员变量能够在const成员函数,const对象中被修改
     1. 如果没有mutable，那么要修改const的成员函数就要用const_cast
```
class testmutable{
private:
    mutable int a=0;
public:
    int changea() const{
        return ++a; //合法
    }
}
```
1.   Dot (.) and Arrow (->) Member Selection Operators:
     * dot: 引用的访问
     * ->： 指针的访问
2.  对于public的数据成员，可以直接通过指针/引用/对象进行访问
3.  访问函数与助手函数 
    1.  Access functions can read or display data. Another common use for access functions is to test the truth or falsity of conditions
    2.  Utility Functions is a private member function that supports the operation of a class’s other member functions， for developers.
4.  关于使用等号赋值：
    1.  如果不想要通过赋值被修改，就要加上const
```
p1=p2   // 可以将p2的值全部逐个赋值给p1，使用的是p2的副本，但不能够解决动态分配内存的指针的问题
```
1.  对象作为类成员：(composition, ***has-a relationship***) 
    1.  对应的类成员也要在构造函数那里进行初始化
    2.  ***先初始化composition(顺序由在类中的定义决定，不由构造函数调用顺序决定), 再初始化类对象, 析构反之***
```
public: 
    Employee(const class a, const class b, double d)//这里尤其要注意：在进行类的实例化的时候，因为传递的是临时化的对象，所以会出现两个编译器自动调用的拷贝构造函数
    : composition1(a),composition2(b),d(d){}
private:
    class composition1;
    class composition2;
    double d;
```
1.  与composition对比理解： ***is-a relationship： 继承***  ***只有公有继承才是is-a relationship，私有和保护继承不是***
2.  this指针：本质是一个访问类自己地址的指针
    1.  this的类型: 
        1.  非const成员函数： 指针常量
        2.  const成员函数：常量常指针
    2.  作用：可以在命名重复的时候访问到类的成员
    3.  *this: 对象本身
        1.  *this 可以让类串联函数调用
```
class t{
public: 
    void A(){return *this;}
    void B(){return *this;}
    void C(){return *this;}
};
void a(){
    t T;
    T.A().B().C();
}
```
1. 在类内的成员函数中，如果定义了一个新的类的实例化，那么这个实例化拥有class scope
## 友元： 类外访问类内的成员
1. 可以将 **（函数、类、成员函数）** 作为类的友元
```
friend class ClassTwo; //类
friend void setx(); //函数
friend void ClassTwo:: setx(); //成员函数
```
1. 友元的关系不传递也不对称(单向)也没有继承性(基类的友元不会继承给继承类)
2. 友元性质与在类的位置无关
3. 访问方式：通过实例化一个类的对象进行访问：
```
class A{
friend void seta(A &);//注意要传入一个类的引用
private:    
    int a=0;
};
void seta(A &AA){AA.a=1;} 其他的也一样
```
1. 友元函数可以重载，每次重载必须清晰写出对应的声明
2. 派生类的友元函数可以访问派生类对应的基类里面的public, protected的数据成员, 但是需要通过实例化的对象进行访问
## 继承与多态
### 继承 Inheritance
1. 继承语法
```
class father{};
class sun: public father{}     公有继承，父类中公有的和保护的内容在子类中不变  public还是public, private还是private 
class sun: protected father{}  保护继承，父类中公有的和保护的内容在子类中为保护
class son: private father{}    私有继承，父类中公有的和保护的内容在子类中为私有的
```
1. 父类中的private部分会被继承，但是是被隐藏了，无法直接通过子类访问
   1. 解决方案：写get,set函数
   2. 将private写道protected里面，能够直接访问
2. 保护权限类外无法访问
3. 构造析构顺序：构造是从子类推到父类，析构则是从父类推回到子类（先进后出）
4. 如果父类中的成员属性/成员函数与子类中的同名，如果是通过子类的对象进行访问，那么直接访问的就是子类的函数，那么访问父类的时候要加作用域  **是否是静态的都一样**
```
//子类中
int getsalary(){
    return base::getsalary+bonus;
}
```
1. 构造、析构函数和重载的赋值运算符不能被继承
2. 派生类构造函数需要显式调用基类的构造函数, 如果没有显示调用，编译器会自动调用隐式的构造函数，但是如果我们在基类自己写了一个构造函数(无论是什么构造函数都一样)，那么编译器就不会生成一个默认的构造函数了，因此就会编译错误
```
baseplus(const string &first, const string &last, double sales,double rate, double salary)
    : base(first,last, sales, rate) //显式调用
    {}
```
1. 在C++11中，可以直接继承基类的构造函数，但是要注意：只会调用默认的构造函数
   1. 构造函数的public、private、protected的性质默认由基类决定
```
class B: public A{
public: 
    using A::A;//使用继承构造函数
};
```
#### 多重继承 is-a relationship
1. 区分多个同名数据成员的方法：
   1. 加上作用域(::)来区分对应的同名类成员
   2. 用基类的指针接收派生类的对象
``` 
class son: public father1, public father2{
public:
    son(int a,int b, int c)
    : father1(a),father2(b),c(c){}//这里构造函数的顺序是根据class son: public father1, public father2的顺序决定
private:
    int c;
};
int main(){
    son s(a,b,c);
    s.father1::func();
    s.father2::func();
}
```
#### 虚继承：菱形继承 
1. 可能会遇到不同的重载的副本：使用virtual 多态进行解决
```
class son：virtual public father
```
### 多态：静态/动态 Polymorphism：指针/引用调用+虚函数
1. 静态：地址在编译阶段绑定(了解)
2. 动态：地址在运行阶段才绑定：  父类的指针或者引用指向子类
3. 多态通过指针或者引用实现，而不能通过类名实现
4. 如果子类重写了父类的虚函数，派生类中的虚函数表内部会替换成为基类虚函数的地址
5. 一定要用指针/引用调用虚函数
6. ***如果没有写成虚函数，那么用基类的指针指向派生类的对象就会调用基类的数据成员（前提是这个数据成员在基类和派生类中都存在）***
   1. 本质：如没有写成多态的形式，那么指针类型决定了调用哪个类的数据成员
7. 子类的函数中virtual 和 override 可以省略
8. 在某种程度上来讲，派生类对象可以通过基类进行处理，而基类的对象不能通过派生类进行处理
9.  利用基类指针，编译器只允许调用基类的成员函数，即使基类的指针指向派生类对象，也不能调用派生类的成员函数
   1. 解决方案： ***downcasting***: 强制类型转换: 危险的操作
   ```
   Son s1;
    Father* f = &s1;
    Son *s = (Son*)f;
    s->print1(); //调用派生类成员函数
   ```
10. 使用方法: 多态
```
virtual void function() const {} //这个是基类的虚函数
virtual void function() const override{} //这个是派生类对应的虚函数，注意const必须写在override前面 
```
1.  如果是虚函数，那么可以通过使用基类的指针完成对于派生类的函数的调用 
2.  override的函数必须有相同的函数签名和对应的返回值类型
3.  如果派生类没有重写对应的虚函数，那么直接继承基类的
4.  override的作用：编译器检查该函数是否是虚的，不是就报编译错误
5.  final: 告诉编译器这是函数的最终版本，接下来不能修改该函数，任何修改操作都是编译错误
    1.  **甚至可以将类定义为final,防止对应的类被当作基类**
#### 纯虚函数 
```
virtual int name（） = 0; 加入等于0
```
1. 能够避免编写没有明确目的的函数
2. 存在纯虚函数，那么该类为抽象类：
   1. 无法实例化对象
   2. 如果子类不重写纯虚函数，子类也无法实例化对象
   3. 有完整的实现的类就是完整类（concrete classes），能够实例化对象
   4. 能够作为指针或者引用的句柄，指向派生类
3. 纯虚函数也可以有具体的实现的代码
##### 虚析构和纯虚析构
***构造函数不能写虚函数***
1. 如果类里面存在虚函数的时候，建议destructor也写为虚析构，这样避免调用析构函数时无法delete 对应的指针
2. 纯虚析构和纯虚函数性质类似，但是纯虚析构需要有具体的代码实现
3. 虚析构可以用父类指针完全释放子类的内存
4. 如果在头文件的构造函数中写了默认参数，那么在源文件就不用写了
5. 虚函数没有实例化，不能够被调用
6. 如果派生类也是抽象类，就可以不用重写纯虚函数
```
virtual ~class() override{}//虚析构
virtual ~class() =0; //纯虚析构 ！！！纯虚析构必须有对应的实现

类外： class::~class(){}

virtual ~pluscalss() override{}// 派生类写法
```
##### 类型转化  
1. static_cast：不检查当前对象，直接进行转化
2. dynamic_cast: 检查当前的对象，并能够将指针类型转化
   1. 通过runtime来判断一个类的类型
   ```
   //将基类employee指针转化为派生类的basepulsemployee
   baseplusemployee *ptr = dynamic_cast<baseplusemployee *> (baseptr)
   if(ptr!=nullptr){    }//如果基类指针对应的对象是baseplusemployee的话，就会返回对应的地址；如果不是，就会返回空指针
   ```
3. 查看类型：typeid
     ```
     # include<typeinfo>
     typeid(* baseptr).name() //typeid返回了一个type_info的引用，然后调用type_info类中的name()函数返回对应的类的名称 
     ```
</details> 

<details> 
    <summary>输入输出流</summary>

# 输入输出流 
1. 打印\n等特殊符号：cout<<"\\n"<<endl;    输出结果：\n
2.  等待对应时间后输出：使用sleep(1),指的是间隔1秒后输出，需要include<unistd.h>
3.  C++默认输出共6位（整数+小数部分）
4.  C++中检查字符串是否为空的函数：empty(), 使用substr截取字符串, 用at()访问对应下标位置的字符
5.  头文件
    * 基类：ios，派生类：ostream,istream，子子类：iostream，cerr/clog/cout : ostream对象
      * cerr: 未缓冲的输出流，速度快
      * clog： 缓冲的数据流，
    * iomanip: 用于格式化输出
    * fstream: 文件处理
6.  输出流：
    1.  put()：只能够输出一个字符，如果超过一个字符的2位数，就会转换成为Ascill码对应的值
    ```
    cout.put('A').put('\n') //支持连续调用
    cout.put(65)
    ```
    2.  char*
        * 本来输出char *类型的指针应该输出对应的地址，但是C++将char *的输出定义为输出指针对应的值，因此要进行转化
        ```
        const char* const ptr= "lalala";
        cout<<static_cast<const void *>(ptr)<<endl; //void* 无类型指针，可以支持任何指针化为该指针
        ```
7.  输入流：
    1.  get和getline
        ```
        //get函数有三个重载， get是从缓冲区拿走字符
        while(cin.get()!=EOF){} ;  // 读取输入的内容，直到用户输入文件结束符(Ctrl+Z)
        char c;
        while(cin.get(c)){}; //这里一定要为char

        string a;
        a=cin.get()//这个版本的get函数只读取一个字符，并返回对应的值

        char ch[20];
        char* cha;
        cin.get(ch,20,'\n')// 变量名，长度，对应的终止符(长度优先),默认为'\n'，终止符不会被读入，读取到终止符前一个字符截止

        //getline是读取到换行符结尾, getline会将delimiter从流中删除
        cin.getline(var,length)
        ```
        * cin是读取到空白的输入符(比如space、enter等等)就停止读取，而get则是读取到Ctr+Z
    2.  peek,putback,ignore
        1.  ignore 忽略调输出的buffer里面的某些字符，比如说'\n'
        ```
        cin.ignore(n,'\n');// 忽略n个字节，直到遇到'\n',就直接terminate终止
        ```
        2. peek 查看并返回缓冲区的第一个字符，但并不取走
        3. putback 将get从缓冲区拿走的数据放回缓冲区
8.  read,write,gcount： 非格式化的I/O
    1.  read/write格式
    ```
    cin.read(var,length);
    cout.write(var,length);
    ```
    2. cin.gcount() 返回最近一次输入操作所读取的字符数
9.  流操纵符:
    1.  整形流的基数: dec(10进制),oct(8进制),hex(16进制),setbase(parameterized stream manipulator)    ***all sticky***
        1.  showbase: 显示当前进制前缀： 16进制： 0x， 8进制：0;  noshowbase,  ***sticky***  
        2.  uppercase/nouppercase: 表示数字的字母是否大/小写,默认为lowercase   ***sticky***
    ```
    # include<iomanip>// setbase()
    int number =10;
    cout<<showbase;
    cout<<uppercase;
    cout<<oct<<number<<endl;
    cout<<setbase(10)<<number;
    ```
    2.  浮点精度(precision,setprecision) ***sticky***
        1.  fixed,scientific: 
            1. fixed：保持浮点输出(3.141592653589790000)，
            2. scientif则是转化为科学计数法  (sticky)
         2. 关于length: 如果在输出前定义了fixed/scientific,那么length就是小数点后几位； 如果输出前没有定义fixed/scientifiic，那么length就是输出的有效数字
    ```
    #include<iomanip>
    cout.precision() //调用无参数类型，返回对应输出几位有效数字
    cout.precision(length) 
    cout<<setprecision(length)
    ``` 
    3.  域宽(width,setw) not sticky
        1.  对齐 justification  (left,right,internal) ***not sticky***, 默认是right(右对齐)
    ```
    cin.width(); //无参数调用，返回当前的width的值
    cin.width(5);
    cout<<setw(5);
    ```
    4.  自定义操作
        1.  返回值一定要是ostream的引用
    ```
    ostream& name(ostream &os){ return os<<"name";}
    cout<<name;
    ```
10. 流的格式状态和流操纵符：***sticky***
    1.  尾数零和小数点 trailing zeros and decimal points   
    ```
    cout<<showpoint; //输出当前精度的数，不省略0： 比如 9.9000，不showpoint就是9.9, showpoint之后就是9.9000
    cout<<noshowpoint;
    ``` 
    2.  内容填充  paddling (fill,setfill)  ***sticky***
        1.  默认填充' ',空格
    ```
    cout.fill('*');
    cout<<setw(10)<<'a'<<endl;
    cout<<setfill('~')<<setw(10)<<endl;  //setfill和setw前后顺序不重要
    ```
    3.  specifying boolean format: 指定布尔格式： (boolalpha, noboolalpha)      ***sticky***
    ```
    bool a= false;
    cout<<boolalpha<<a;
    ```
    4.  setting and resetting the format state: flags： 对于当前输出格式状态的存档，每一个flags对应一个固定的参数
    ```
    ios_base::fmtflags originalFormat= cout.flags() //存档,没有参数的flags返回当前的设定的输出格式
    cout.falgs(originalFormat)；//使用该存档
    ```
    5.  showpos: 在输出之前加入 '+', noshowpos,不受setw（）的影响 ***sticky***
11. 流的错误状态：
    1.   cin.eof()   是否遇到文件结尾
    2.   cin.fail()  发生格式错位，数据保留
         1.   ***只有read会设置failbit***
    3.   cin.bad()   发生数据丢失错误                       状态位：failbit/badbit：istream/ostream的数据成员
    4.   cin.good()  以上的状态为都没有被设置，这个改为true
    5.   cin.rdstate() 返回流是否存在错误，没有就是false
    6.   cin.clear()    清空状态位，全部复原
12. 输出流连接到输入流
    1.  编译器可能会自动连接
```
cin.tie(&cout);
cin.tie(0) //解除绑定
```
13. operator! 返回true如果badbit,failbit都被set了，而operator void * retrun false
1.   flush: 与endl用法类似，作用为刷新缓存区，能够清理缓存区的内存
2.   wchar_t 被设计用于存储Unicode 类型的数据
### C++使用类型安全的IO   C使用类型不安全的IO
### stream:二进制的数据
>>跳过空格、tab、newline等等
cin会返回istream对象的引用，对输入是否为空进行判断
</details> 
<details>
    <summary>函数</summary>

# 函数
1.  无形参函数：void func(void)    
2.  函数默认参数（default argument）：在申明函数的参数时候就给出对应的值，如果调用函数的时候没有传递参数，那么就用默认参数，如果多个参数只传递了其中的一部分，就按从前到后的方式是赋值
3.  内联函数 在函数定义前加inline： inline void a()，加速编译
4.  函数：值传递、地址传递、引用传递 ***地址传递和引用传递传递的都是地址，会直接修改对应地址的值***
    1.  引用传递 return-type fuction-name1(int &a)
    2.  地址传递 return-type  fuction-name2(int *c)
    3.  值传递，实参的值不改变 fuction-name1(b);
5.  函数的重载（function overloading）：定义相同函数名的函数，但是为了处理不同的数据，所有声明签名不同的函数
    * 返回值类型不同不能作为函数重载的条件
6. 函数签名：函数名+形参表（每个程序中，函数签名应该是独一无二的），如果调用时无法区分，那么程序会自动报错,函数签名（signature）:void func(int, double) 包括：返回值类型，函数名，形参表
7. 函数原型（protopype），就是先定义函数，给出函数的返回值类型和函数名（形参可以不用定义），然后在后面继续定义函数
   1. 数组和指针的函数原型写法:
   ```
   void name(int [])   
   void name(int *)   
   ```
8. 函数定义（definition）: 包括函数头+函数体 函数定义形参的时候，有默认值的参数一定要写在最后，没有默认值的写在前
9.  函数体中不能再定义新的函数
10. 函数的强制类型转换：比如int与double的互换，隐式类型转化，但是可能会丢失精度
11. 函数返回值类型为引用：比如: int& a(), 不能返回非静态成员变量，不能返回常量
12. 函数的模板：template <typename  T>,typename或者class都可以,typename和T之间不要加逗号！
    * T(或返回值) 函数名（T a, T b）函数的模板能够在实际编译的过程中去识别具体的变量数据类型（或其他）
</details>
<details>
    <summary>数组</summary>

# 数组
1.  size_t: 无符号整型数据类型，size_t储存对象的索引，unsigned int 储存对象的值
2.  C++数组排序：sort（start,end）排序，需要inlucde<algorithm>库,就直接sort，不返回： sort(a.start(),a.end());
3.  auto关键字，自动识别类型, 不能够直接作为参数类型定义变量，需要作为接收的一方
4.  vecto容器：include<vector> vector初始化
```
vector<数据类型> 变量名={1，2，3}；
vector<数据类型1> 变量名1(数据多少) vector <int> n(5);     用一个容器初始化另一个容器 voctor<数据类型1>变量名2（变量名1）：vector <int> n(m);   这种情况不能够初始化vector
增添元素：变量名1.push_back(所添加的函数)
1. vector二维数组的初始化：vector<vector<int>> ans(r, vector<int>(c));  定义的是行为r，列为c的二维数组
```
1.  数组中，如果想用新的变量去接收vector中的数的话，那么用vector.front()接收第一个，而不能用vector.begin()，array也一样
2.  数组容器的定义
```
array <type,arraySize> arrayName    
二维数组的定义：array<array<int,cloumns>,rows> b,数组容器的二维数组定义就直接按顺序写，不能如42一样操作
1.  数组的定义中array(int,size),size一定要是一个常量
```
1.  基于数组容器的for语句： for(int item:items) 用item遍历items里面的所有元素,item的数据类型必须跟items的一致(range-based for statement)
2.  多维数组的赋值：a[b][c]={{1，2，3}，{d,e,f}，{4，5，6}}:表示b行c列,每个大括号表示一行,c不能省略，必须给出，然后中间的{d,e,f}不能为空，定义空行必须填0
3.  内置数组：我们熟悉的数组， 初始化时大小的定义可以省略： int arrray[]={1,2,3,4,5,6,7}  内置数组的begin(array)和end（array）在头文件：<ierator>里面，
4.  数组名.size()可以获取数组的大小   变量名1.size()返回容器大小，内置数组不行
5.  static数组，如果没有初始化，那么编译器会自动初始化为0,数组也可以是静态的
</details>
<details>
    <summary>指针与引用</summary>

# 指针与引用
1.  引用：引用必须初始化,不可修改引用指向的地址（比如int &b=a,那么就不能改为&b=c了，当然，可以b=c，因为这是赋值操作）
2.  指针初始化：
```
int * ptr;	
```
1.  取址符&: y=&y1  y是指针     
2.  输出时，输出y是输出地址，输出*y输出对应地址的值
    1.  C++中，所有参数其实都是按值传递的
3.  
    1. 常量指针（constant pointer）：const修饰指针：可以修改指针的指向（即使指向的值变化了），不可修改值，但只是不能通过这个指针修改值，而通过别的方式修改变量的值之后，指针输出的值也会跟着修改
    ```
    const int *p=&a; 
    ```
    2. 指针常量（pointer constant）不可以修改指针的指向，可修改值，必须在定义行就初始化
    ```
    int * const p=&a;
    ```    
    3. 既修饰常量，又修饰指针:  不可以修改指针的指向，不可修改值
    ```
     const int * const p=a;   
    ```
4. The name of an array is a constant pointer：数组的名称是一个常量指针，也就是可以修改指向，不能修改值  
5. 对于将数据赋值给指针，如果没有申明数组第几位，那么默认是第一位
6. 指针的赋值：变量名（不带*）=&变量名
7.  ``*`` indirection operator :解引用操作符, 空指针不能被解引用
8.  获取内置数组长度的方式：
```
    sizeof(),sizeof(数组变量名)/sizeof(数组变量名[0])
```
1.  指针与数组：int *p, int arr[5] p=arr(这个地方不用加取址符)等价于p=&arr[0], 也就是指针获取了数组的首地址，指针的变量名等价于数组的名称（前面不用再加*号）
    1.  如果指针指向内置数组，那么指针可以进行加减运算
2.  用空指针赋值给对应的变量：  任意的指针之间是可以随意互相赋值的，包括空指针 
```
int* sPtr=nullptr(定义空指针)           
int number=*static_cast<int *>(sPtr;) 
```   
1.  指针字符串：
    1.  初始化：
    ```
    char color[]="absdfbsdf"  const char *colorprt="absdufua"      
    char color[]={'b','u','l','e','\0'}    （理论上来说必须要加'\0'），必须是单引号，char数组结尾默认是加'\0'的，所
    以在定义的时候char a[e]="bcd" e==4而不是3	用指针接收char数组名，比如char *p=color, 那么cout<<p<<endl; 的结果就是打印color字符串
    ```
2. unique_ptr
   1. 能够自动管理任意类型的资源（比如说动态内存）
   2. 超出定义域之后，自动调用delete 
</details>
<details>
    <summary>Technics</summary>

# Technics
1.  头文件：不能用using，要用std::域作用符,避免namespace命名空间混乱
2.  include： C++自己的库只能用"",但是官方的库可以用<>或者""
3.  C++ 截取字符串函数（在<string> 中）substr(start,end),截取后为[start,end],返回截取后的值
4.  end:str.size()获取长度
5.  C++中else与最近的if语句关联
6.  unsigned int: 无符号整数，用于存储非负整数，存储的范围是0~4,294,967,295
7.  显式强制转换数据类型： ***static_cast<double>（变量名） 变量名一定要加括号啊***
8.  C++赋值语句：1）数据类型 变量名=值  2）数据类型 变量名={值}  3）数据类型 变量名{值}
9.  ++操作可以在任意的语句中进行  a=0 cout<<a++<<endl;    cout<<a<<endl;     >>>0     >>>1
    1.   ++i是运算语句，所以无论在哪里，++i都是有效的（包括在if等语句中), i++也是如此       ++i返回的是i自增后的地址， i++返回的是i自增前的值
10. 乘方函数：pow(x,y) #include<cmath>    输出x的y次方  x,y均是double类型的数据   cmath库自动把x，y转换成double
11. switch语句格式：switch(variable(integer only))其中对应的整数不能在case中重复使用
```
case 1:
	skjdflksjd
	break;
default:
	sdkfsd;
	break;
```
1.  字符使用要用单引号，字符保存的是askcell码值
2.  在条件判断中使用赋值语句，如果赋值不是0，那么全为真  if(a=1)->真   if(a=0)->假
3.  \x16进制字符
4.  cmath库 几个好用的函数：fmod(x,y):浮点数取模，fabs(x):取绝对值   sqrt(x)：开平方根,x不能为负数
5.  register寄存器变量是单个变量,加快访问速度（没有地址）
6.  enum    variable{VARIABLE1, VARIABLE2, VARIABLE3.....}枚举算法：是一些传递整数值的常量（实际是变量，但初始化后不能改），用于赋值,variable variables=VARIABLE1
    1. 初始化：默认是从0开始递增，当然也可以自己初始化，不同的VARIABLEA可以有相同的值   enum是域作用的，也就是说可以定义与已经定义的字符名相同的变量，加上variable:VARIABLE1就可以了
    2. 或者可以用 enum class variable{}
7.  static 在函数的最初阶段就创造内存空间,并且会随着程序变化而变化，它的作用域在定义它的函数里面
8.  堆栈：后进先出
9.  一元作用域分辨运算符（scope resolution operator）  ：：访问的是全局变量,访问静态成员等等
10. binary_search():二分查找 在algorithm库里面，语法是： bool found=binary_search(数组的起始查找位置，数组的终止查找位置，查找目标)
11. debug
```
# include<stdexcept>
try:
{
	执行的操作
	catch(报错类型、名称)
	{
	    cerr<<jfksjldfk<<ex.what()<<endl;}
}


throw 报错类型(输出) 会立即返回，有点类似return 
#比如
    throw invalid_argument("sth. is out of range" );
```
1.  编译原理
    1.  editor: creats program and stores it on disk      
    2.  preprocessor: preprocessor program processes the code   
    3.  complier: creats object code and stores it on disk   
    4.  linker: links the object code with libraries, creat an executable file and stores it on disk  
    5.  loder: puts program in memory    
    6.  CPU: takes each instruction and executes it, storing new data values 
2.  C++中不用大括号： if...else 中if不用大括号的话只能有一行语句，多则else无法识别    else 识别的是离他最近的if语句
3.  占空间：指针：64位8个字节 32位4个字节（byte）Int：4个字节   float：4个字节    double: 8bytes   char: 1byte   long long: 8bytes bool: 1byte   short: 2bytes string: 8byte
4.  C++支持连续比较大小(x<y<z）
5.  source code:源文件 .cpp
6.  C++浮点除法的处理：整数/整数的话，就要1.0/2,这样返回的就是浮点数
7.  \t：水平的tab   \0: string的结束符, 必须要有，不然容易报错
8.  注意所有计数器、记录累加、累乘结果的变量都必须先初始化，再操作
9.  空白语句：只有一个分号的语句
10. 可以找到对应的数据类型的上限和下限：INT_MAX, INT_MIN 在库中：include<climits>   unsigned int 的最大值：UINT_MAX
11. do while语句
```
do{
statement
}
while();    其中do的大括号可以省略
```
1.  &&的优先级比||高
2.  编码：bit<character(byte)<field<record<file
3.  换行输出要在两行之间打<<         escape character:\
4.  取模和乘法的优先级相同
5.  +=，-=，*=，/=都是先算等号右边的结果然后再与左边的变量进行加减乘除运算
6.  const字符定义的变量都必须初始化（除了常量指针）
7.  for循环后如果不加括号，那么只能照顾到第一个语句（）比如if语句，或其他，接下来就直接跳出for循环了
8.  for循环中的边界条件如果有多个并列的，要用&&连接起来
9.  浮点数、整数之间理论上是可以互相赋值、转化的，但是要注意数据的准确性
10. ACSLL码值：0——48，a——97，A——65, 字符和整数的相互转化，就用static_cast<int/char> (a)
11. 使用typedef进行重命名：只能把已有的对象进行重命名
    ```
    typedef int INT
    INT a=1;
    ```
12. 使用const_cast强制将const或者volatile类型的限定去除
```
const char *mutablee='1';
char *mu=const_cast<char *>(mutablee);
mu='2';
```
1.  namespace 
    * using namespace std: 将std的namespace都用在这里
    * 如果命名空间在相同的函数中用不同的命名空间的值，那么global的就是：：variable
    ```
    namesapce name{
        int a=3;
        int b;
        namespace inner{
            int c=1;
        }
        void test();
    }
    namespace{   // unnamed namespace
        int a=5;
        int b;
    }
    int main(){
        cout<<a;   //输出5,from blank namespace
        cout<<name::a<<endl;  //输出3
        cout<<name::inner::c; //namesapce可以嵌套
    }
    void name::test{
        cout<<a<<inner::c<<endl;
    }
    ```
    * 还可以给namespace起别名
    ```
    namespace CPPHTP = CPlusPlusHowToProgram;
    ```
2.  位运算用英文单词表示：&& and || or   ! not
</details>
<details>
    <summary>运算符重载</summary>

# 运算符重载 
1. new的是创建数据的地址，用指针接收
   1. new的本质：调用对应对象的构造函数
```
double * p= new double (10)  
int * arr= new int [10]() (默认的初始化为0/flase/nullptr)
int *arr=new int[10]{}// C++11
Time *timeptr= new Time(12,45,0); 
```
1. 手动删除堆区的数据用delete:
```
delete p;
delete[] arr;
```
1. 空类的内存大小为：1
2. 左值： 能够修改      右值：返回的是对象的值，不能够修改
3. ptr初始化   ptr(new int[size])
4. 没有加句柄的默认是类的成员
5. 常量成员函数不能调用非常量成员函数,反之可以      
6. 动态内存管理，要自己写copy constructor: 用于pass by value, 能够初始化，隔离内存，确保不在同一个内存
7.  如果写一个自定义的数组类，记得写copy constructor, destructor , overloaded assignment operator
8.  Array (const Array&)=delete; 删除默认构造函数， 将运行错误转化为编译错误
9.  conversion constructor： 类型转换，（可能隐式调用：将整型转换为浮点型）
10. 类型转换：静态类型转化： static_cast<char *> (s) 转换为字符指针
11. 不能重载的运算符：. .*(pointer to member) ::   ?;
    1.  尽量不要重载的运算符：& && ||
12. 重载() [] ->的时候，重载函数一定要声明为类的成员函数，其他没有强制要求
13. 重载类型
    1.  重载输入输出运算符
    ```
    class a{
    friend  std::istream &operator>>(std::istream &, a &);
    friend std::ostream &operator<<(std::ostream &, const a &);
    private:
        bool output=false;
    };
    std::ostream &operator<<(std::ostream &output, const a &A){
        output<<"Output"<<A.output;
        return output; //这里return output是为了让<<运算符可以连续调用
    }
    std::istream &input &operator>>(std::istream &input, a &A){
        input>>A.output;
        return input;
    }
    ```
    2. 重载关系运算符： >,<, ==, >=, <=, ***必须成对重载***
    ```
    bool operator==(const classname & name) const ;// 返回布尔值，然后参数都是const 引用，作为成员函数重载
    bool operator<(const String &, const String &)  //2. 作为非成员函数
    ```
    3. 重载赋值运算符
    ```
    const Array & operator=(const Array & a){ //这个const防止(a=b)=z的情况发生 
        if(&a!=this) {   //第一步判断对应的地址是否相同
            //第二部赋值，对应的赋值操作自己想
        }
    }
    ```
    4. 重载前置和后置递增/递减运算符
    ```
    Date & operator++(); //类内的前置自增运算符
    Date & operator++(Date &); //类外的前置自增运算符

    Date operator++(int) //类内的后置自增运算符， int用于区分前后置
    Date operator++(Date &, int);//类外的后置自增运算符
    ```
    5. 重载下标访问运算符:subscript operator
    ```
    int & operator[](int subscirpt); //支持连续调用
    const int & operator[](int subscript) const;// 这里使用const int&， 这个const是防止由于返回引用导致修改对应的值，用于const对象的查询
    ```
    6. 重载函数调用运算符：
    ```
    String String::operator()(size_min index, size_max length) const
    ```
    7.  重载加号运算符    重载!运算符
    ```
    bool operator!() const{return !this->a};
    bool operator!(const String &){};    // non-memeber function

    Class &  operator+(class c){
        return 
    }
    ```
14. 重载== !=: 其实只需要写一个重载的逻辑代码，另外一个调用这个重载的代码就可以了
15. explicit 显示构造函数，防止发生隐式类型转换
16. **无法隐式重载“+=”**
</details>
<details>
    <summary>文件读写</summary>

# 文件读写
1. 流程：
   1. 文件读取
   * 文件读取类名： fstream,ofstream,ifstream
   * 然后包含对应的文件名，
   * 读写方式(ios::in|ios::out|ios::binary|ios::ate),注意使用ostream只能out，使用istream只能in
     * out: 顺序存储，删除掉之前的文件内容，重新从头开始写入
     * in: 顺序读取
     * app: 从上次文件结尾处开始写入
     * binary： 二进制（随机）文件读写
      1. sequential file: 
      ```
      ofstream outClientFile("name.txt",ios::out)  //ios::out会自动擦除原来的文件，并且从头开始输入， ios::app会从上次文件的结尾处开始添加所以的输出数据
      ofstream outClientFile;
      outClientFile.open("name.txt",ios::out)
      ```
      2. ramdom file: 
     ```
     ifstream inCredit("credit.dat", ios::in| ios::binary); 
     ```
   2.  检查读取是否成功
    ```
    # include <cstdlib>
        if(!outClientFile){
        cerr<<"Fail to open the file"<<endl;
        exit(EXIT_FAILURE);  //相当于return 0
        }
    ```
   3. 对应的文件操作, ***非常关键的步骤是在写入文件之后要seekg（）和clear（），不然文件无法顺利读取***
      1. 顺序文件读写
        ```
        //文件写入
        while(cin>>account>>name>>balance){
            outClientFile<<account<<' '<<name<<' '<<balance<<endl;
        }
        outClientFile.clear() //清空文件的状态
        outClientFile.seekg(0) //从头开始读
        //文件读取
        while(inClientFile>>account>>name>>balance){
            outputline(account,name,balance);// 封装好的函数
        }
        ```
        2. 随机文件读写：方式：首先要创建类，类中使用char数组存储字符串
        ```
            file.write(reinterpret_cast<const char*>(&pointer),sizeof(pointer))

            file.read(reinterpret_cast<char*>(&pointer)，长度) 
        ```
   4. 文件关闭： main函数结束会自动隐式调用析构函数，也可以显示调用
    ```
    outClientFile.close()
    ```

2. 即使没有对应的文件名，ios::out也会创建一个对应的文件名，但如果是ios::out和ios::in的组合，则不会自动创建
3. ios::out是ofstream的默认格式
4. seekp与seekg： 文件写/读的光标对应的指针
   1. seekp: "seek put" 在ofstream当中，重定位写入文件的光标
   2. seekg: "seek get" 在ifstream当中，重定位读取文件的光标 
   3. 相对应的，还有tellp()和tellg(),返回当前光标位置的long型的值
   ```
   // 定位到 fileObject 的第 n 个字节（假设是 ios::beg）
    fileObject.seekg( n );

    // 把文件的读指针从 fileObject 当前位置向后移 n 个字节
    fileObject.seekg( n, ios::cur );
 
    // 把文件的读指针从 fileObject 末尾往回移 n 个字节
    fileObject.seekg( n, ios::end );
   ```
* 二进制文件用于读写结构化的内容，比如对应的类，或者对应的结构体
* EOF——end of file 返回值为-1，是个常量  //TODO：：再查清楚一点
* ***二进制文件删除对象的方法：用一个空对象进行替换***
1. 检查文件结尾：使用void *, 如果遇到了文件EOF,failbit,badbit, 那么void * 都会变为false,就直接return， 不再进行读写
</details>
<details>
    <summary>类模板</summary>

# 类模板
1. 栈：stack 先进后出，后进先出
2. Class templates are called parameterized types, because they require one or more type parameters to specify how to customize a generic class template to form a class-template specialization.
3. 格式
```
template< typename T >
class stack{
public:
    void push(const T &pushvalue) //用于替代位置的数据类型
private:
    deque<T> name;
};

//类外定义成员函数
template< typename T >   
inline void Stack<T>::pop()
{
   stack.pop_front();
} // end function template pop    

//单独定义函数
template<typename T>
void func(const T& value1, const T& value2){}


//nontype template parameters
template < class T, size_t N >
class array{};
```
4. 作用：类模板提供了在类型不确定情况下对于某个数据结构进行操作，给出统一的指令，也就是说类模板是一个泛型
5. 实例化方式
```
stack<double> name;
array<double,1000> name;
func(1.1,1);
func(2,1.1);
```
1. 模板不允许在main里面声明
</details> 