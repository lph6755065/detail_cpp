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
## 函数指针: 一种特殊的指针，它指向函数的入口；
* 定义一个函数指针p，只能指向返回值为int，形参为两个int的函数. 
* int (*p)(int,int);  
## 指针函数:返回指针的函数，一个函数，它的返回值是指针；
* 这是一个形参为两个int类型，返回值是int型指针的函数
* int *p(int,int);  
## 指针数组: 首先它是一个数组，数组的元素都是指针   `int *p1[10]`;
## 数组指针:首先它是一个指针，它指向一个数组。在32 位系统下永远是占4 个字节   `int (*p2)[10]`;
## 指针常量  指针常量是指指针所指向的位置不能改变，即指针本身是一个常量，但是指针所指向的内容可以改变。声明：int * const p=&a;
## 常量指针 ： 具有只能够读取内存中数据，却不能够修改内存中数据的属性的指针，称为指向常量的指针，简称常量指针 声明：const int * p; int const * p;
![](https://github.com/lph6755065/detail_cpp/blob/main/picture/1631735536(1).png) 
## 请问为什么两个指针相加没有意义？
* 将两个指针相减可以表示两个指针(在同一数组中)相距的距离，将指针加上一个整数也可以表示移动这个指针到某一位置。但是两个指针相加并没有逻辑上的意义，因此两个指针不能相加。
	
## 编写一段程序，用整型数组初始化一个vector对象。
```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
	int arr[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
	vector<int> v(begin(arr), end(arr));

	for (auto i : v) cout << i << " ";
	cout << endl;

	return 0;
}
```  
## 编写一段程序，将含有整数元素的vector对象拷贝给一个整型数组。
```cpp
	
	#include <iostream>
#include <vector>

using namespace std;

int main()
{
	vector<int> v{ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
	int arr[10];
	for (int i = 0; i != v.size(); ++i) 
		arr[i] = v[i];

	for (auto i : arr) cout << i << " ";
	cout << endl;

	return 0;
}
``` 
## 编写3个不同版本的程序，令其均能输出ia的元素。版本1使用范围for语句管理迭代过程；版本2和版本3都使用普通for语句，其中版本2要求使用下标运算符，版本3要求使用指针。此外，在所有3个版本的程序中都要直接写出数据类型，而不能使用类型别名、auto关键字和decltype关键字。
```cpp
	#include <iostream>

using std::cout;
using std::endl;

int main()
{
	int arr[3][4] =
	{
		{ 0, 1, 2, 3 },
		{ 4, 5, 6, 7 },
		{ 8, 9, 10, 11 }
	};

	// range for
	for (const int(&row)[4] : arr)
		for (int col : row) cout << col << " ";

	cout << endl;

	// for loop
	for (size_t i = 0; i != 3; ++i)
		for (size_t j = 0; j != 4; ++j) cout << arr[i][j] << " ";

	cout << endl;

	// using pointers.
	for (int(*row)[4] = arr; row != arr + 3; ++row)
		for (int *col = *row; col != *row + 4; ++col) cout << *col << " ";

	cout << endl;

	return 0;
}
```
## 溢出是何含义？写出三条将导致溢出的表达式。

* 当计算的结果超出该类型所能表示的范围时就会产生溢出。
```cpp
short svalue = 32767; ++svalue; // -32768
unsigned uivalue = 0; --uivalue;  // 4294967295
unsigned short usvalue = 65535; ++usvalue;  // 0
``` 
## 说明在逻辑与、逻辑或及相等性运算符中运算对象的求值顺序。

* 逻辑与运算符和逻辑或运算符都是先求左侧运算对象的值再求右侧运算对象的值，当且仅当左侧运算对象无法确定表达式的结果时才会计算右侧运算对象的值。这种策略称为 短路求值。
相等性运算符未定义求值顺序。
## 假设i、j 和k 是三个整数，说明表达式 i != j < k 的含义。  
* 这个表达式等于 i != (j < k)。首先得到 j < k 的结果为 true 或 false，转换为整数值是 1 和 0，然后判断 i 不等于 1 和 0 ，最终的结果为 bool 值。  
## 下面的赋值是非法的，为什么？应该如何修改？  
double dval; int ival; int *pi;   
dval = ival = pi = 0;  
p 是指针，不能赋值给 int ，应该改为：  
 
dval = ival = 0;  
pi = 0;  
## 假设 ptr 的类型是指向 int 的指针、vec 的类型是vector、ival 的类型是int，说明下面的表达式是何含义？如果有表达式不正确，为什么？应该如何修改？
```cpp
(a) ptr != 0 && *ptr++  
(b) ival++ && ival
(c) vec[ival++] <= vec[ival] 
	
``` 
* (a) 判断ptr 不是一个空指针，并且ptr 当前指向的元素的值也为真，然后将ptr指向下一个元素
* (b) 判断 ival 的值为真，并且 (ival + 1) 的值也为真
* (c) 表达式有误。C++并没有规定 <= 运算符两边的求值顺序，应该改为 vec[ival] <= vec[ival+1]
## 假设 iter 的类型是 vector::iterator, 说明下面的表达式是否合法。如果合法，表达式的含义是什么？如果不合法，错在何处？
```cpp
(a) *iter++;
(b) (*iter)++;
(c) *iter.empty();
(d) iter->empty();
(e) ++*iter;
(f) iter++->empty();  
```
* (a)合法。返回迭代器所指向的元素，然后迭代器递增。
* (b)不合法。因为vector元素类型是 string，没有 ++ 操作。
* (c)不合法。这里应该加括号。
* (d)合法。判断迭代器当前的元素是否为空。
* (e)不合法。string 类型没有 ++ 操作。
(f)合法。判断迭代器当前元素是否为空，然后迭代器递增。
## C语言中a&0x0表示什么？ a&0x01就是取a的最低位值的运算  
```cpp
	eg：
（1）当a=0x00时
a = a&0x01 ---> 0000 0000 = 0000 0000 & 0000 0001
（2）当a=0x01时
a = a&0x01 ---> 0000 0001 = 0000 0001 & 0000 0001
（3）当a=0x11时
a = a&0x01 ---> 0000 0001 = 0001 0001 & 0000 0001
二：应用实例
1.判断一个数是奇数还是偶数
#include <stdio.h>
#include <stdlib.h>
int main (void)
{
	int i;
	scanf ("%d",&i);
	if (i&0x01)
	printf("奇数\n");
	else
	printf("偶数\n");
	system ("pause");
	return 0;
}
2.取一个数的最低位的相反数
Warm=(~Warm)&0x01;
（1）当Warm=0x00时
Warm=(~Warm)&0x01; ---> 0000 0001 = 1111 1111 & 0000 0001
（2）当Warm=0x01时
Warm=(~Warm)&0x01; ---> 0000 0000 = 1111 1110 & 0000 0001
（3）当Warm=0x11时
Warm=(~Warm)&0x01; ---> 0000 0000 = 1110 1110 & 0000 0001
``` 
## 注意代码可读性 
```cpp
#include <iostream>
using std::cout; using std::cin; using std::endl;

int main()
{
	for (unsigned g; cin >> g;)
	{
		auto result = g > 90 ? "high pass" : g < 60 ? "fail" : g < 75 ? "low pass" : "pass";
		cout << result << endl;

		// -------------------------
		if (g > 90)         cout << "high pass";
		else if (g < 60)    cout << "fail";
		else if (g < 75)    cout << "low pass";
		else                cout << "pass";
		cout << endl;
	}

	return 0;
}	
```  
## 因为运算符的优先级问题，下面这条表达式无法通过编译。根据4.12节中的表指出它的问题在哪里？应该如何修改？
```cpp
string s = "word";
string pl = s + s[s.size() - 1] == 's' ? "" : "s" ;
加法运算符的优先级高于条件运算符。因此要改为：

string pl = s + (s[s.size() - 1] == 's' ? "" : "s") ;
```   
## 下列表达式的结果是什么？
```cpp
unsigned long ul1 = 3, ul2 = 7;
(a) ul1 & ul2 
(b) ul1 | ul2 
(c) ul1 && ul2
(d) ul1 || ul2 
(a) 3
(b) 7
(c) true
(d) ture
```   
## 在下述表达式的适当位置加上括号，使得加上括号之后的表达式的含义与原来的含义相同。
```cpp
(a) sizeof x + y      
(b) sizeof p->mem[i]  
(c) sizeof a < b     
(d) sizeof f()  
(a) (sizeof x) + y
(b) sizeof(p->mem[i])
(c) sizeof(a) < b
(d) sizeof(f())
```  
## 说明下面这条表达式的含义。
```cpp
someValue ? ++x, ++y : --x, --y
逗号表达式的优先级是最低的。因此这条表达式也等于：
(someValue ? ++x, ++y : --x), --y
```  
## 假设有如下的定义：
```cpp
char cval;
int ival;
unsigned int ui;
float fval;
double dval;
请回答在下面的表达式中发生了隐式类型转换吗？如果有，指出来。

(a) cval = 'a' + 3;
(b) fval = ui - ival * 1.0;
(c) dval = ui * fval;
(d) cval = ival + fval + dval;
(a) 'a' 转换为 int ，然后与 3 相加的结果转换为 char
(b) ival 转换为 double，ui 转换为 double，结果转换为 float
(c) ui 转换为 float，结果转换为 double
(d) ival 转换为 float，与fval相加后的结果转换为 double，最后的结果转换为char
```  
## 用命名的强制类型转换改写下列旧式的转换语句。
```cpp
int i; double d; const string *ps; char *pc; void *pv;
(a) pv = (void*)ps;
(b) i = int(*pc);
(c) pv = &d;
(d) pc = (char*)pv;
改写之后的
(a) pv = static_cast<void*>(const_cast<string*>(ps));
(b) i = static_cast(*pc);
(c) pv = static_cast<void*>(&d);
(d) pc = static_cast<char*>(pv);

```  
## C++ 四种强制类型转换 1、static_cast，2、const_cast，3、reinterpret_cast，4、dynamic_cast
###1）static_cast 用法为 static_cast<type-id> (expression)。
  * 该运算符把 expression 转换为 type-id 类型，但没有运行时类型检查来保证转换的安全性。
#### 主要用法如下：
    （1）用于类层次结构中基类（父类）和派生类（子类）之间指针或引用的转换。  
        进行上行转换（把派生类的指针或引用转换成基类表示）是安全的；  
        进行下行转换（把基类指针或引用转换成派生类表示）时，由于没有动态类型检查，所以是不安全的。  
    （2）用于基本数据类型之间的转换，如把int转换成char，把int转换成enum。这种转换的安全性也要开发人员来保证。  
    （3）把空指针转换成目标类型的空指针。  
    （4）把任何类型的表达式转换成void类型。  
  ```cpp
最常用的应该还是基本数据类型之间的转换，如下：

	const auto a1 = 11;	// int
	const auto a2 = 4;	// int

// C style
	double res1 = (double)(a1) / (double)(a2);	// 其实写一个 (double) 就行
	cout << "res1 = " << res1 << endl;			// res1 = 2.75

// C++ style
	auto res2 = static_cast<double>(a1) / static_cast<double>(a2);
	cout << "res2 = " << res2 << endl;			// res2 = 2.75
	cout << typeid(res2).name() << endl;		// double

```  
### 2）const_cast 上边的 static_cast 不能将 const int* 转成 int*，const_cast 就可以，用法为 const_cast<type-i> (expression)    
	#### const_cast<>里边的内容必须是引用或者指针，就连把 int 转成 int 都不行。一般的，只是转换类型，但是指向的地址不变。
```cpp
const int a = 10;
	const int * p = &a;
	*p = 20;						 // Compile error: Cannot assign readonly type 'int const'
	int res1 = const_cast<int>(a);   // Compile error: Cannot cast from 'int' to 'int' via const_cast
									 // only conversions to reference or pointer types are allowed
	int* res2 = const_cast<int*>(p); // ok

```  
### 3）reinterpret_cast  reinterpret_cast 主要有三种强制转换用途：
 * 1、改变指针或引用的类型
 * 2、将指针或引用转换为一个足够长度的整形
 * 3、将整型转换为指针或引用类型。
 * 用法为 reinterpret_cast <type-id> (expression)。
   - type-id 必须是一个指针、引用、算术类型、函数针或者成员指针。它可以把一个指针转换成一个整数，也可以把一个整数转换成一个指针（先把一个指针转换成一个整数，在把该整数转换成原类型的指针，还可以得到原先的指针值）。 
   - 我们映射到的类型仅仅是为了故弄玄虚和其他目的，这是所有映射中最危险的。(这句话是C++编程思想中的原话)。因此, 你需要谨慎使用 reinterpret_cast。
### 4）dynamic_cast 
    * 用法为 dynamic_cast<type-id> (expression)。
  * 几个特点如下：
  *（1）其他三种都是编译时完成的，dynamic_cast 是运行时处理的，运行时要进行类型检查。
  *（2）不能用于内置的基本数据类型的强制转换
  *（3）dynamic_cast 要求 <> 内所描述的目标类型必须为指针或引用。dynamic_cast 转换如果成功的话返回的是指向类的指针或引用，转换失败的话则会返回 nullptr
  *（4）在类的转换时，在类层次间进行上行转换（子类指针指向父类指针）时，dynamic_cast 和 static_cast 的效果是一样的。在进行下行转换（父类指针转化为子类指针）时，dynamic_cast 具有类型检查的功能，比 static_cast 更安全。 向下转换的成功与否还与将要转换的类型有关，即要转换的指针指向的对象的实际类型与转换以后的对象类型一定要相同，否则转换失败。在C++中，编译期的类型转换有可能会在运行时出现错误，特别是涉及到类对象的指针或引用操作时，更容易产生错误。Dynamic_cast操作符则可以在运行期对可能产生问题的类型转换进行测试。
  * （5）使用 dynamic_cast 进行转换的，基类中一定要有虚函数，否则编译不通过（类中存在虚函数，就说明它有想要让基类指针或引用指向派生类对象的情况，此时转换才有意义）。这是由于运行时类型检查需要运行时类型信息，而这个信息存储在类的虚函数表中，只有定义了虚函数的类才有虚函数表（C++中的虚函数基本原理这篇文章写得不错，https://blog.csdn.net/xiejingfa/article/details/50454819）。
```cpp
	class base {
public:
	void print1() { cout << "in class base" << endl; }
};

class derived : public base {
public:
	void print2() { cout << "in class derived" << endl; }
};

int main() {
	derived *p, *q;
	// p = new base;	//  Compilr Error: 无法从 "base * " 转换为 "derived * "

	// Compile Error: Cannot cast from 'base*' to 'derived*' via dynamic_cast: expression type is not polymorphic(多态的)
	// p = dynamic_cast<derived *>(new base);

	q = static_cast<derived*>(new base);	// ok, but not recommended

	q->print1();	// in class base
	q->print2();	// in class derived
}

```  
### 小结：static_cast 强制类型转换时并不具有保证类型安全的功能，而 C++ 提供的 dynamic_cast 却能解决这一问题，dynamic_cast 可以在程序运行时检测类型转换是否类型安全。当然 dynamic_cast 使用起来也是有条件的，它要求所转换的 expression 必须包含多态类类型（即至少包含一个虚函数的类）。 去const属性用const_cast。基本类型转换用static_cast。多态类之间的类型转换用daynamic_cast。不同类型的指针类型转换用reinterpreter_cast。
## 如果在程序的某个地方，语法上需要一条语句但是逻辑上不需要，此时应该使用空语句。
`while (cin >> s && s != sought) ;`
## 说明下列例子的含义，如果存在问题，试着修改它。

`(a) while (string::iterator iter != s.end()) { /* . . . */ }`  
`(b) while (bool status = find(word)) { /* . . . */ }`  
		`if (!status) { /* . . . */ }`
* (a) 这个循环试图用迭代器遍历string，但是变量的定义应该放在循环的外面，目前每次循环都会重新定义一个变量，明显是错误的。
* (b) 这个循环的 while 和 if 是两个独立的语句，if 语句中无法访问 status 变量，正确的做法是应该将 if 语句包含在 while 里面，
## 学生成绩显示小程序 
```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;
int main()
{
    vector<string> scores = { "F", "D", "C", "B", "A", "A++" };
    int count = 0;
    int grade = 0;

    while ( 1 ) {
        cin >> grade;
        if ( grade > 100){
            count++;
            cout << "your choices have : :"<< 5 - count  << endl;
            if (5 - count > 0)
            cout << "coutinue print grade :"<< endl;
            
            if (count >= 5){
                cout << "your choices have finished:"<< endl;
                break;
            }
        }else{

                string lettergrade = grade < 60 ? scores[0] : scores[(grade - 50) / 10];
                lettergrade += (grade == 100 || grade < 60) ? "" : (grade % 10 > 7) ? "+" : (grade % 10 < 3) ? "-" : "";
                cout << lettergrade << endl;
        }
    }
    return 0;
}
``` 
## 下面显示的每个程序都含有一个常见的编码错误，指出错误在哪里，然后修改它们。
```cpp
(a) unsigned aCnt = 0, eCnt = 0, iouCnt = 0;
    char ch = next_text();
    switch (ch) {
        case 'a': aCnt++;
        case 'e': eCnt++;
        default: iouCnt++;
    }
(b) unsigned index = some_value();
    switch (index) {
        case 1:
            int ix = get_value();
            ivec[ ix ] = index;
            break;
        default:
            ix = ivec.size()-1;
            ivec[ ix ] = index;
    }
(c) unsigned evenCnt = 0, oddCnt = 0;
    int digit = get_num() % 10;
    switch (digit) {
        case 1, 3, 5, 7, 9:
            oddcnt++;
            break;
        case 2, 4, 6, 8, 10:
            evencnt++;
            break;
    }
(d) unsigned ival=512, jval=1024, kval=4096;
    unsigned bufsize;
    unsigned swt = get_bufCnt();
    switch(swt) {
        case ival:
            bufsize = ival * sizeof(int);
            break;
        case jval:
            bufsize = jval * sizeof(int);
            break;
        case kval:
            bufsize = kval * sizeof(int);
            break;
    }
```
## 说明下列循环的含义并改正其中的错误。
```cpp
(a) for (int ix = 0; ix != sz; ++ix) { /* ... */ }
    if (ix != sz)
    	// . . .
(b) int ix;
    for (ix != sz; ++ix) { /* ... */ }
(c) for (int ix = 0; ix != sz; ++ix, ++sz) { /*...*/ }
应该改为下面这样：

(a) int ix;
    for (ix = 0; ix != sz; ++ix)  { /* ... */ }
    if (ix != sz)
    // . . .
(b) int ix;
    for (; ix != sz; ++ix) { /* ... */ }
(c) for (int ix = 0; ix != sz; ++ix) { /*...*/ }
```
## 假设有两个包含整数的vector对象，编写一段程序，检验其中一个vector对象是否是另一个的前缀。为了实现这一目标，对于两个不等长的vector对象，只需挑出长度较短的那个，把它的所有元素和另一个vector对象比较即可。例如，如果两个vector对象的元素分别是0、1、1、2 和 0、1、1、2、3、5、8，则程序的返回结果为真。
```cpp
#include <iostream>
#include <vector>

using std::cout; using std::vector;

bool is_prefix(const vector<int>& lhs, const vector<int>& rhs)
{
	if (lhs.size() > rhs.size())
		return is_prefix(rhs, lhs);
	for (unsigned i = 0; i != lhs.size(); ++i)
		if (lhs[i] != rhs[i]) 
			return false;
	return true;
}

int main()
{
	vector<int> l{ 0, 1, 1, 2 };
	vector<int> r{ 0, 1, 1, 2, 3, 5, 8 };
	cout << (is_prefix(r, l) ? "yes\n" : "no\n");

	return 0;
}
```  
## 关于eof函数
* fstream / ifstream / ofstream 类中的 成员函数eof()用来检测是否到达文件尾，如果到达文件尾返回非0值，否则返回0。原型是int eof(); 
## 除法的异常检测操作 
```cpp
#include <iostream>
#include "stdexcept"
using namespace std;

int main(){
  int i, j ;
 while(cin >> i >> j){
     try {
         if (j == 0){
             throw runtime_error("divisor is 0\n");
         }
         cout << i/j<<endl;
     }catch(runtime_error err) {
         cout << err.what() <<"Try Again or not ? Enter y or n" <<endl;
         char c;
         cin >> c;
         if (c != 'y')
             break;
     }
     cout << "please input two numbers : ";
 }
  return 0;
}
```
## 举一个形参应该是引用类型的例子，再举一个形参不能是引用类型的例子。
例如交换两个整数的函数，形参应该是引用
```cpp
void swap(int& lhs, int& rhs)
{
	int temp = lhs;
	lhs = rhs;
	rhs = temp;
}
```
当实参的值是右值时，形参不能为引用类型
```cpp
int add(int a, int b)
{
	return a + b;
}

int main()
{
	int i = add(1,2);
	return 0;
}
```
## 下面的这个函数虽然合法，但是不算特别有用。指出它的局限性并设法改善。

`bool is_empty(string& s) { return s.empty(); }`
局限性在于常量字符串和字符串字面值无法作为该函数的实参，如果下面这样调用是非法的：

`const string str;`
`bool flag = is_empty(str); `//非法
`bool flag = is_empty("hello");` //非法
所以要将这个函数的形参定义为常量引用：
`bool is_empty(const string& s) { return s.empty(); }`
## 编写一个函数，令其交换两个int指针。
```cpp
	#include <iostream>
#include <string>

void swap(int*& lft, int*& rht)
{
	auto tmp = lft;
	lft = rht;
	rht = tmp;
}

int main()
{
	int i = 42, j = 99;
	auto lft = &i;
	auto rht = &j;
	swap(lft, rht);
	std::cout << *lft << " " << *rht << std::endl;

	return 0;
}
	```
## 描述下面这个函数的行为。如果代码中存在问题，请指出并改正。

```cpp 
void print(const int ia[10])
{
	for (size_t i = 0; i != 10; ++i)
		cout << ia[i] << endl;
}
```
当数组作为实参的时候，会被自动转换为指向首元素的指针。因此函数形参接受的是一个指针。如果要让这个代码成功运行，可以将实参改为数组的引用。
```cpp
void print(const int (&ia)[10])
{
	for (size_t i = 0; i != 10; ++i)
		cout << ia[i] << endl;
}
```

## 编写一个递归函数，输出vector对象的内容。
```cpp
#include <iostream>
#include <string>
#include <vector>
using std::cout; using std::endl; using std::string;
using Iter = std::vector<int>::const_iterator;//这一步比较新颖
void print(Iter first,Iter last){
    if(first == last){
        std::cout<<"over"<<endl;
        return;
    }
    cout<<*first<<endl;
    print(++first,last);
}
int main()
{
    std::vector<int> vec{1,2,3,4,5,6,7,8};
    print(vec.begin(),vec.end());

    return 0;
}
```
## 编写一个函数声明，使其返回数组的引用并且该数组包含10个string对象。不用使用尾置返回类型、decltype或者类型别名。  
`string (&fun())[10];`
### 为上一题的函数再写三个声明，一个使用类型别名，另一个使用尾置返回类型，最后一个使用decltype关键字。 
```cpp
typedef string str_arr[10];
str_arr& fun();

auto fun()->string(&)[10];

string s[10];
decltype(s)& fun();  
我觉得尾置返回类型最好。
```  
## 说明在下面的每组声明中第二条语句是何含义。如果有非法的声明，请指出来。
```cpp
(a) int calc(int, int);
	int calc(const int, const int);
(b) int get();
	double get();
(c) int *reset(int *);
	double *reset(double *);
(d) char *init(int ht = 24, int wd, char bckgrnd);
```
* (a) 非法。因为顶层const 不影响传入函数的对象，所以第二个声明无法与第一个声明区分开来。
* (b) 非法。对于重载的函数来说，它们应该只有形参的数量和形参的类型不同。返回值与重载无关。
* (c) 合法。
* (d) 错误。因为一旦某个形参被赋予了默认值，那么它之后的形参都必须要有默认值。
## 如果有非法的声明，请指出来。
```cpp
(a) int calc(int&, int&); 
	int calc(const int&, const int&); 
(b) int calc(char*, char*);
	int calc(const char*, const char*);
(c) int calc(char*, char*);
	int calc(char* const, char* const);
```
* (c) 不合法。顶层const不影响传入函数的对象。
## 下面的哪个调用是非法的？为什么？哪个调用虽然合法但显然与程序员的初衷不符？为什么？
```cpp
char *init(int ht, int wd = 80, char bckgrnd = ' ');
(a) init();
(b) init(24,10);
(c) init(14,'*');
```
* (a) 非法。第一个参数不是默认参数，最少需要一个实参。
* (b) 合法。
* (c) 合法，但与初衷不符。字符 * 被解释成 int 传入到了第二个参数。而初衷是要传给第三个参数。
## 你会把下面的哪个声明和定义放在头文件中？哪个放在源文件中？为什么？
```cpp
(a) inline bool eq(const BigInt&, const BigInt&) {...}
(b) void putValues(int *arr, int size);
```
* 全部都放进头文件。(a) 是内联函数`(一般来说，内联机制用于优化规模小、流程直接、频繁调用的函数。)`，(b) 是声明。
