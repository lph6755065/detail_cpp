# detail_cpp
## unsigned 和signed 类型有什么差别？  
* 【解答】前者为无符号类型，只能表示大于或等于0 的数。后者为带符号类型，可以表示正数、负数和0。*
## 如果在某机器上short 类型占16 位，那么可以赋给short 类型的最大数是什么？unsigned short 类型的最大数又是什么？  
* 【解答】若在某机器上short 类型占16 位，那么可以赋给short 类型的最大数是2^15-1，即32767；而unsigned short 类型的最大数为2^16-1，即65535。* 
## 当给16 位的unsigned short 对象赋值100000 时，赋的值是什么？  
* 【解答】34464。100000 超过了16 位的unsigned short 类型的表示范围，编译器对其二进制表示截取低16 位，相当于对65536 求余（求模，%），得34464。*  
## 解释下列字面值常量的不同之处。  
(a) 'a',L'a',"a",L"a"  
(b) 10,10u,10L,10uL,012,0xC  
(c) 3.14,3.14f,3.14L  
* 【解答】   
(a) 'a',L'a',"a",L"a"  
'a'为char 型字面值，L'a'为wchar_t 型字面值，"a"为字符串字面值，L"a"为宽字符串字面值。  
(b) 10,10u,10L,10uL,012,0xC  
10 为int 型字面值，10u 为unsigned 型字面值，10L 为long 型字面值，10uL为unsigned long 型字面值，012 为八进制表示的int 型字面值，0xC 为十六进制表示的int 型字面值。  
(c) 3.14,3.14f,3.14L  3.14 为double 型字面值，3.14f 为float 型字面值，3.14L 为long double 型字面值。  
## 确定下列字面值常量的类型：
(a) –10 (b) -10u (c) -10. (d) -10e-2  
* 解答】
(a) int 型
(b) unsigned int 型
(c) double 型
(d) double 型   
## 下列哪些（如果有）是非法的？
(a) "Who goes with F\145rgus?\012"
(b) 3.14e1L (c) "two" L"some"
(d) 1024f (e) 3.14UL
(f) "multiple line
comment"
* 【解答】
 (c) 非法。因为字符串字面值与宽字符串字面值的连接是未定义的。
(d) 非法。因为整数1024 后面不能带后缀f。
(e) 非法。因为浮点字面值不能带后缀U。
(f) 非法。因为分两行书写的字符串字面值必须在第一行的末尾加上反斜线。
## 下面两个定义是否不同？有何不同？  
int month = 9, day = 7;  
int month =09, day = 07;  
如果上述定义有错的话，那么应该怎样改正呢?  
* 【解答】  
这两个定义不同。前者定义了两个int 型变量，初值分别为9 和7；后者也定义了两个int 型变量，其中day 被初始化为八进制值7；而month 的初始化有错：试图将month 初始化为八进制值09，但八进制数字范围为0~7，所以出错。可将第二个定义改为：int month =011, day = 07;  
## 假设calc 是一个返回double 对象的函数。下面哪些是非法定义？改正所有的非法定义。 
(a) int car = 1024, auto = 2048;  
(b) int ival = ival;  
(c) std::cin >> int input_value;  
(d) double salary = wage = 9999.99;  
(e) double calc = calc();  
* 【解答】   
(a) 非法：auto 是关键字，不能用作变量名。使用另一变量名，如aut 即可更正。  
(c) 非法：>>运算符后面不能进行变量定义。改为：int input_value;std::cin >> input_value;  
(d) 非法：同一定义语句中不同变量的初始化应分别进行。改为：double salary = 9999.99, wage = 9999.99;  
注意，(b)虽然语法上没有错误，但这个初始化没有实际意义，ival 仍是未初始化的。  
## 下列变量的初始值（如果有）是什么？  
```C++
std::string global_str;
int global_int;
int main()
{
int local_int;
std::string local_str;
// ...
return 0;
}
```
* 【解答】  
global_str 和local_str 的初始值均为空字符串，global_int 的初始值为0，local_int 没有初始值。  
## 解释下列例子中name 的意义： 
extern std::string name;  
std::string name("exercise 3.5a");  
extern std::string name("exercise 3.5a");  
* 【解答】  
第一条语句是一个声明，说明std::string 变量name 在程序的其他地方定义。  
第二条语句是一个定义，定义了std::string 变量name，并将name 初始化为"exercise 3.5a"。  
第三条语句也是一个定义，定义了std::string 变量name，并将name 初始化为"exercise 3.5a"，但这个语句只能出现在函数外部（即，name 是一个全局变量）。  
## 下列程序中j 的值是多少？  
```C++
int i = 42;
int main()
{
int i = 100;
int j = i;
// ...
}
```
* 【解答】  
j 的值是100。j 的赋值所使用到的i 应该是main 函数中定义的局部变量i，因为局部变量的定义会屏蔽全局变量的定义。  
## 下列程序段将会输出什么？  
```C++ 
int i = 100, sum = 0;
for (int i = 0; i != 10; ++i)
sum += i;
std::cout << i << " " << sum << std::endl; 
```
* 【解答】  
输出为：  
100 45  
for 语句中定义的变量i，其作用域仅限于for 语句内部。输出的i 值是for 语句之前所定义的变量i 的值。   
## 下列程序合法吗？ 
```C++
int sum = 0;  
for (int i = 0; i != 10; ++i)  
sum += i;  
std::cout << "Sum from 0 to " << i  
<< " is " << sum << std::endl;  
```
* 【解答】
不合法。因为变量i 具有语句作用域，只能在for 语句中使用，输出语句中使用i 属非法  
## 下列代码输出什么？  
int i, &ri = i;
i = 5; ri =10;
std::cout << i << " " << ri << std::endl;
* 【解答】
输出：10 10
ri 是i 的引用，对ri 进行赋值，实际上相当于对i 进行赋值，所以输出i 和ri 的值均为10。
## extern    
* 1、函数的声明extern关键词是可有可无的，因为函数本身不加修饰的话就是extern。但是引用的时候一样需要声明的。  
* 2、全局变量在外部使用声明时，extern关键字是必须的，如果变量没有extern修饰且没有显式的初始化，同样成为变量的定义，因此此时必须加extern，而编译器在此标记存储空间在执行时加载内并初始化为0。而局部变量的声明不能有extern的修饰，且局部变量在运行时才在堆栈部分分配内存。  
* 3、全局变量或函数本质上讲没有区别，函数名是指向函数二进制块开头处的指针。而全局变量是在函数外部声明的变量。函数名也在函数外，因此函数也是全局的。  
* 4、谨记：声明可以多次，定义只能一次。  
* 5、extern int i; //声明，不是定义  int i; //声明，也是定义  
## 下列声明和定义哪些应该放在头文件中？哪些应该放在源文件中？请解释原因。  
(a) int var ;  
(b) const double pi = 3.1416;  
(c) extern int total = 255 ;  
(d) const double sq2 = squt (2.0) ;  
* 【解答】
(a)、(c)、(d)应放在源文件中，因为(a)和(c)是变量定义，定义通常应放在源文件中。(d)中的const 变量sq2 不是用常量表达式初始化的，所以也应该放在源文件中。
(b)中的const 变量pi 是用常量表达式初始化的，应该放在头文件中。参见<<C++ primer 习题>> 2.9.1 节。  

## 请说明string类的输入运算符和getline函数分别是如何处理空白字符的。

* 类似 is >> s 的读取，string对象会忽略开头的空白并从第一个真正的字符开始，直到遇见下一空白为止。
* 类似 getline(is, s) 的读取，string对象会从输入流中读取字符，直到遇见换行符为止。

## 编写一段程序，读入一个包含标点符号的字符串，将标点符号去除后输出字符串剩余的部分。 
```C++
 string s = "this, is. a :string!";
    string res;
    for (auto c : s){
        if(!ispunct(c)){
            res += c;
        }
    }
    cout << res << endl;
```  
## 下面的范围for语句合法吗？如果合法，c的类型是什么？  
`const string s = "Keep out!";`
`for(auto &c : s){ /* ... */ }` 
要根据for循环中的代码来看是否合法，c是string 对象中字符的引用，s是常量。因此如果for循环中的代码重新给c赋值就会非法，如果不改变c的值，那么合法。  
## 下列的vector对象各包含多少个元素？这些元素的值分别是多少？
```cpp
vector<int> v1;         // size:0,  no values.
vector<int> v2(10);     // size:10, value:0
vector<int> v3(10, 42); // size:10, value:42
vector<int> v4{ 10 };     // size:1,  value:10
vector<int> v5{ 10, 42 }; // size:2,  value:10, 42
vector<string> v6{ 10 };  // size:10, value:""
vector<string> v7{ 10, "hi" };  // size:10, value:"hi"
vector<string> v8(10,"hi");    // size:10, value:"hi"  
```
## 下面的程序合法吗？如果不合法，你准备如何修改？

vector<int> ivec;
ivec[0] = 42;

## 如果想定义一个含有10个元素的vector对象，所有元素的值都是42，请例举三种不同的实现方法，哪种方式更好呢？

如下三种：
```cpp
vector<int> ivec1(10, 42);
vector<int> ivec2{ 42, 42, 42, 42, 42, 42, 42, 42, 42, 42 };
vector<int> ivec3;
for (int i = 0; i < 10; ++i)
	ivec3.push_back(42);
```   
* 第一种方式最好。    
		       
## 在100页的二分搜索程序中，为什么用的是 mid = beg + (end - beg) / 2, 而非 mid = (beg + end) / 2 ; ?
 因为迭代器支持的运算只有 - ，而没有 + 。end - beg 意思是相距若干个元素，将之除以2然后与beg相加，表示将beg移动到一半的位置。   
## 假设txt_size 是一个无参函数，它的返回值是int。请回答下列哪个定义是非法的，为什么？
```cpp
unsigned buf_size = 1024;
(a) int ia[buf_size];
(b) int ia[4 * 7 - 14];
(c) int ia[txt_size()];
(d) char st[11] = "fundamental";
```  
* (a) 非法。纬度必须是一个常量表达式。
* (b) 合法。
* (c) 非法。txt_size() 的值必须要到运行时才能得到。
* (d) 非法。数组的大小应该是12。
## 下列数组中元素的值是什么？
```C++
string sa[10];
int ia[10];
int main() {
	string sa2[10];
	int ia2[10];
}
```
* 数组的元素会被默认初始化。sa 的元素值全部为空字符串，ia 的元素值全部为0。sa2 的元素值全部为空字符串，ia2 的元素值全部未定义。  
## 相比于vector 来说，数组有哪些缺点，请例举一些。

* 数组的大小是确定的。
* 不能随意增加元素
* 不允许拷贝和赋值
## 假定p1 和 p2 都指向同一个数组中的元素，则下面程序的功能是什么？什么情况下该程序是非法的？
* p1 += p2 - p1;
* 将 p1 移动到 p2 的位置。任何情况下都合法。
## 编写一段程序，比较两个数组是否相等。再写一段程序，比较两个vector对象是否相等。
```cpp
#include <iostream>
#include <vector>
#include <iterator>

using namespace std;

bool compare(int* const pb1, int* const pe1, int* const pb2, int* const pe2)
{
	if ((pe1 - pb1) != (pe2 - pb2)) 
		return false;
	else
	{
		for (int* i = pb1, *j = pb2; (i != pe1) && (j != pe2); ++i, ++j)
		if (*i != *j) return false;
	}

	return true;
}

int main()
{
	int arr1[3] = { 0, 1, 2 };
	int arr2[3] = { 0, 2, 4 };

	if (compare(begin(arr1), end(arr1), begin(arr2), end(arr2)))
		cout << "The two arrays are equal." << endl;
	else
		cout << "The two arrays are not equal." << endl;

	cout << "==========" << endl;

	vector<int> vec1 = { 0, 1, 2 };
	vector<int> vec2 = { 0, 1, 2 };

	if (vec1 == vec2)
		cout << "The two vectors are equal." << endl;
	else
		cout << "The two vectors are not equal." << endl;

	return 0;
}
		       
```
