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
```cpp
#include <iostream>
using namespace std;

int mmin(int x, int y) {
    if (x < y) return x;
    return y;
}
int main()
{
    int (*f ) (int x, int y);
    f = mmin;
    int a = 10, b =20;
    std::cout << (*f)(a,b) << std::endl;

    return 0;
}

```
## 指针函数:返回指针的函数，一个函数，它的返回值是指针；
* 这是一个形参为两个int类型，返回值是int型指针的函数
* int *p(int,int);  
## 指针数组: 首先它是一个数组，数组的元素都是指针   `int *p1[10]`;
* 表示有10个指针类型的数组元素，p+1是错误操作，因为p是个不可知的表示。可以p[0],p[1]....
* 如果表示二维数组。可以`*(p[i]+j)`, `*(*(p+i)+j)`, `(*(p+i))[j]`, `p[i][j]`
## 数组指针:首先它是一个指针，它指向一个数组。在32 位系统下永远是占4 个字节   `int (*p2)[10]`;
* 如果发生p+1,那么指针指向下一个长度为10个int的首地址处，在二维数组里面，p+1就可以直接指到下一行。一般地，数组指针是一维数组指针，也叫行指针。
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

	// Compile Error: Cannot cast from 'base*' to 'derived*' via dynamic_cast: expression type is not polymorphic(
	
	
	
	
	的)
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
## 编写函数的声明，令其接受两个int形参并返回类型也是int；然后声明一个vector对象，令其元素是指向该函数的指针。
```cpp
	int func(int, int);
	vector<decltype(func)*> v; //尖括号里面等同于：int (*)(int,int)
```
## 编写4个函数，分别对两个int值执行加、减、乘、除运算；在上一题创建的vector对象中保存指向这些函数的指针。
```cpp
#include <iostream>
#include <vector>

using namespace std;

int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }
int multiply(int a, int b) { return a * b; }
int divide(int a, int b) { return b != 0 ? a / b : 0; }

int main()
{
	int func(int, int);
	vector<decltype(func)*> v;
	v.push_back(add);
	v.push_back(subtract);
	v.push_back(multiply);
	v.push_back(divide);
	
	for (auto i : v)
	{
		cout << i(6, 2) << ", "; // 8, 4, 12, 3
	}
	cout << endl;
	return 0;
}
```
## 使用class 和 struct 时有区别吗？如果有，是什么？
* class 和 struct 的唯一区别是默认的访问级别不同。
	* （一）默认继承权限。如果不明确指定，来自class的继承按照private继承处理，来自struct的继承按照public继承处理；
	* （二）成员的默认访问权限。class的成员默认是private权限，struct默认是public权限。
## 封装是何含义？它有什么用处？
* 将类内部分成员设置为外部不可见，而提供部分接口给外面，这样的行为叫做封装。封装隐藏了具体的实现，当我们使用某个抽象数据类型时，只需要考虑它提供什么接口操作，而不用去考虑它的具体实现。
## 友元在什么时候有用？请分别举出使用友元的利弊。
* 当其他类或者函数想要访问当前类的私有变量时，这个时候应该用友元。
* 利：
	* 与当前类有关的接口函数能直接访问类的私有变量。
* 弊：
	* 牺牲了封装性与可维护性。
```cpp
#include<iostream>
using namespace std;
/*
若一个类为另一个类的友元，则此类的所有成员都能访问对方类的私有成员。
声明语法：将友元类名在另一个类中使用friend修饰说明。
*/

/*
如果声明B类是A类的友元，B类的成员函数就可以访问A类的私有和保护数据，
但A类的成员函数却不能访问B类的私有、保护数据。
*/
class A{
  friend class B;
  public:
    void Display(){
      cout<<x<<endl;
    }
    private:
      int x;
};
class B
{   public:
      void Set(int i);
      void Display();
    private:
      A a;
};
void B::Set(int i)
{
   a.x=i;
}
void B::Display()
{
   a.Display();
}

int main(int argc, char const *argv[])
{
    B b;
    b.Set(10);
    b.Display();

    system("pause");
    return 0;
}

/*
如果声明B类是A类的友元，B类的成员函数就可以访问A类的私有和保护数据，但A类的成员函数却不能访问B类的私有、保护数据
*/
```
```cpp
//使用友元函数计算两点间距离
#include <iostream>
#include <cmath>
using namespace std;
class Point{
  public:
    Point(int x=0,int y=0):X(x),Y(y){}
    int GetX(){
      return X;
    }
    int GetY(){
      return Y;
    }
    friend float Distance(Point &a,Point &b);
  private:
    int X,Y;//私有数据成员
};
//通过将一个模块声明为另一个模块的友元，一个模块能够引用到另一个模块中本是被隐藏的信息。
float Distance(Point &a, Point &b){
  double dx = a.X-b.X;
  double dy = a.Y-b.Y;
  return sqrt(dx*dx+dy*dy);
}

int main()
{  
    Point p1(3.0,5.0),p2(4.0,6.0);
    cout<<"两点距离为："<<Distance(p1,p2)<<endl;
    system("pause");
    return 0;
}
```
## 通过this指针使用成员的做法虽然合法，但是有点多余。讨论显示使用指针访问成员的优缺点。

* 优点：

	* 程序的意图更明确

	* 函数的参数可以与成员同名，如

  `void setAddr(const std::string &addr) { this->addr = addr; }`
* 缺点：

	* 有时候显得有点多余，如

 ` std::string getAddr() const { return this->addr; }` 
## 定义一对类X 和Y，其中X 包含一个指向 Y 的指针，而Y 包含一个类型为 X 的对象。
```cpp
class Y;
class X{
	Y* y = nullptr;	
};

class Y{
	X x;
};
```  
## 如果我们给Screen类添加一个如下所示的size成员将发生什么情况？如果出现了问题，请尝试修改它。
```cpp
pos Screen::size() const
{
	return height * width;
}
```
* 未定义标识符 pos。应该改为：
```cpp
Screen::pos Screen::size() const
{
	return height * width;
}
```  
## 解释下面代码的含义，说明其中的Type和initVal分别使用了哪个定义。如果代码存在错误，尝试修改它。
```cpp
typedef string Type;
Type initVal(); 
class Exercise {
public:
    typedef double Type;
    Type setVal(Type);
    Type initVal(); 
private:
    int val;
};
Type Exercise::setVal(Type parm) { 
    val = parm + initVal();     
    return val;
}
```
*书上255页中说：
	* 然而在类中，如果成员使用了外层作用域中的某个名字，而该名字代表一种类型，则类不能在之后重新定义该名字。因此重复定义 Type 是错误的行为。

* 虽然重复定义类型名字是错误的行为，但是编译器并不为此负责。所以我们要人为地遵守一些原则.
## 下面的初始值是错误的，请找出问题所在并尝试修改它。
```cpp
struct X {
	X (int i, int j): base(i), rem(base % j) {}
	int rem, base;
};
```
应该改为：
```cpp
struct X {
	X (int i, int j): base(i), rem(base % j) {}
	int base, rem;
};  

```  
## 下面哪些论断是不正确的？为什么？

* (a) 一个类必须至少提供一个构造函数。
* (b) 默认构造函数是参数列表为空的构造函数。
* (c) 如果对于类来说不存在有意义的默认值，则类不应该提供默认构造函数。
* (d) 如果类没有定义默认构造函数，则编译器将为其生成一个并把每个数据成员初始化成相应类型的默认值。

	
* (a) 不正确。如果我们的类没有显式地定义构造函数，那么编译器就会为我们隐式地定义一个默认构造函数，并称之为合成的默认构造函数。
* (b) 不完全正确。为每个参数都提供了默认值的构造函数也是默认构造函数。
* (c) 不正确。哪怕没有意义的值也需要初始化。
* (d) 不正确。只有当一个类没有定义任何构造函数的时候，编译器才会生成一个默认构造函数。
## C++之constexpr详解 
* constexpr表达式是指值不会改变并且在编译过程就能得到计算结果的表达式。声明为constexpr的变量一定是一个const变量，而且必须用常量表达式初始化：
```cpp
	constexpr int mf = 20;  //20是常量表达式
constexpr int limit = mf + 1; // mf + 1是常量表达式
constexpr int sz = size(); //之后当size是一个constexpr函数时才是一条正确的声明语句
```
### 指针和constexpr 
* 必须明确一点，在constexpr声明中如果定义了一个指针，限定符conxtexpr仅对指针有效，与指针所指的对象无关。
```cpp
const int*p = nullptr;        //p是一个指向整形常量的指针
constexpr int* q = nullptr;   //q是一个指向整数的常量指针
```
* p是一个指向常量的指针，q是一个常量指针，其中的关键在于constexpr把它所定义的对象置为了顶层(顶层实际上就是const在星号的右边，指针的方向不能变，所指向的值可以改变)const.
* 使用GNU gcc编译器时，constexpr指针所指变量必须是全局变量或者static变量(既存储在静态数据区的变量)。
## 编写函数，接受一个istream&参数，返回值类型也是istream&。此函数须从给定流中读取数据，直至遇到文件结束标识时停止。它将读取的数据打印在标准输出上。完成这些操作后，在返回流之前，对流进行复位，使其处于有效状态。
```cpp
#include <iostream>
#include <string>

using namespace std;

istream& func(istream &is)
{
	string buf;
	while (is >> buf)
		cout << buf << endl;
	is.clear();
	return is;
}

int main()
{
	istream& is = func(std::cin);
	cout << is.rdstate() << endl;
	return 0;
}
```
## 编写函数，以读模式打开一个文件，将其内容读入到一个string的vector中，将每一行作为一个独立的元素存于vector中。
```cpp
void ReadFileToVec(const string& fileName, vector<string>& vec)
{
    ifstream ifs(fileName);
    if (ifs)
    {
        string buf;
        while (ifs >> buf)
            vec.push_back(buf);
    }
}
``` 
## 对于下面的程序任务，vector、deque和list哪种容器最为适合？解释你的选择的理由。如果没有哪一种容器优于其他容器，也请解释理由。
* (a) 读取固定数量的单词，将它们按字典序插入到容器中。我们将在下一章中看到，关联容器更适合这个问题。
* (b) 读取未知数量的单词，总是将单词插入到末尾。删除操作在头部进行。
* (c) 从一个文件读取未知数量的整数。将这些数排序，然后将它们打印到标准输出。
* (a) list ，因为需要频繁的插入操作。
* (b) deque ，总是在头尾进行插入、删除操作。
* (c) vector ，不需要进行插入删除操作。
## 构成迭代器范围的迭代器有何限制？
* 两个迭代器 begin 和 end需满足以下条件：
	* 它们指向同一个容器中的元素，或者是容器最后一个元素之后的位置。
	* 我们可以通过反复递增 begin 来到达 end。换句话说，end 不在 begin 之前。
## c++中iterator，const iterator，const_iterator与begin(),cbegin()
```cpp
#include <iostream>
#include <iterator>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 = {0,1,2,3,4,5,6,7};
    vector<int>::iterator it1 = v1.begin();
    vector<int>::iterator it2 = v1.end();
    vector<int>::reverse_iterator it3 = v1.rbegin();
    vector<int>::reverse_iterator it4 = v1.rend();


    vector<int>::const_iterator it5 = v1.begin();       //指向可变，值不变
    it5++;
    it5 = it2;
    //*it5 = 333;  //不可以
    v1[0] = 333;

    const vector<int>::iterator it6 = v1.begin();       //指向不变，值可变
    //it6++;  //不可以
    *it6 = 333;

    const vector<int>::const_iterator it7 = v1.begin(); //指向不变，值不变
    //it7++;        //不可以
    //*it7 = 333;   //不可以

    vector<int>::const_iterator it8 = v1.cbegin();      //指向可变，值不变
    it8++;
    cout << "cbegin:" << *it8 << endl;
    //*it8 = 444;   //不可以

    //const vector<int>::iterator it9 = v1.cbegin();    //不可以

    const vector<int>::const_iterator it10 = v1.cbegin();
    //it10++;       //不可以
    //*it10 = 333;  //不可以

}


``` 
### 总结：
* cbegin()只能赋值给 const_iterator; 所以不会出现 c语言中 int *p = const int a; 可以通过p改a的值的情况。cbegin()和cend()是C++11新增的，它们返回一个const的迭代器，不能用于修改元素。
	```cpp 
	auto i1 = Container.begin();  // i1 is Container<T>::iterator 
	auto i2 = Container.cbegin(); // i2 is Container<T>::const_iterator
	```
* begin() 的左边 有无const都可以; 若有const_iterator, 也可以直接改vector的值
* const_iterator 表示无法用迭代器改值 类似 const *p。
* const iterator 表示无法改迭代器指向 类似 *const p。
## 编写函数，接受一对指向vector的迭代器和一个int值。在两个迭代器指定的范围中查找给定的值，返回一个布尔值来指出是否找到。
```cpp
	bool find(vector<int>::const_iterator begin, vector<int>::const_iterator end, int i)
{
	while (begin++ != end)
	{
		if (*begin == i) 
			return true;
    }	
    return false;
}
```  
## 重写上一题的函数，返回一个迭代器指向找到的元素。注意，程序必须处理未找到给定值的情况。
```cpp
	vector<int>::const_iterator find(vector<int>::const_iterator begin, vector<int>::const_iterator end, int i)
{
	while (begin != end)
	{
		if (*begin == i) 
			return begin;
		++begin;
    }	
    return end;
}
``` 
## vector 初始化细节 
*  动态分配是在加入元素时再分配空间，即没加入前空间还没有分配，所以不允许使用下标操作，因为下标指向的位置并不存在。所以先提前定义容器的大小，这是提前分配好空间，分配后，里面的数会默认初始化，也就可以使用下标访问了，但是的注意和数组一样，下标不得越界。   
## 为了索引int 的 vector中的元素，应该使用什么类型？
	* vector<int>::size_type
## 为了读取string 的list 中的元素，应该使用什么类型？如果写入list，又应该使用什么类型？
* list<string>::const_iterator // 读
* list<string>::iterator // 写
## 对6种创建和初始化 vector 对象的方法，每一种都给出一个实例。解释每个vector包含什么值。
```cpp
vector<int> vec;    // 0
vector<int> vec(10);    // 0
vector<int> vec(10, 1);  // 1
vector<int> vec{ 1, 2, 3, 4, 5 }; // 1, 2, 3, 4, 5
vector<int> vec(other_vec); // 拷贝 other_vec 的元素
vector<int> vec(other_vec.begin(), other_vec.end()); // 拷贝 other_vec 的元素
```
## 对于接受一个容器创建其拷贝的构造函数，和接受两个迭代器创建拷贝的构造函数，解释它们的不同。 
* 接受一个容器创建其拷贝的构造函数，必须容器类型和元素类型都相同。
* 接受两个迭代器创建拷贝的构造函数，只需要元素的类型能够相互转换，容器类型和元素类型可以不同。
## 如何从一个list初始化一个vector？从一个vector又该如何创建？编写代码验证你的答案。
```cpp
list<int> ilst(5, 4);
vector<int> ivc(5, 5);

vector<double> dvc(ilst.begin(), ilst.end());
vector<double> dvc2(ivc.begin(), ivc.end());
```
## 编写程序，将一个list中的char * 指针元素赋值给一个vector中的string。
```cpp
    std::list<const char*> l{ "hello", "world" };
    std::vector<std::string> v;
    v.assign(l.cbegin(), l.cend());

``` 
## 比较一个list中的元素和一个vector中的元素。
```cpp
	    std::list<int>      li{ 1, 2, 3, 4, 5 };
    std::vector<int>    vec2{ 1, 2, 3, 4, 5 };
    std::vector<int>    vec3{ 1, 2, 3, 4 };

    std::cout << (std::vector<int>(li.begin(), li.end()) == vec2 ? "true" : "false") << std::endl;
    std::cout << (std::vector<int>(li.begin(), li.end()) == vec3 ? "true" : "false") << std::endl;

```
	
## 浅拷贝和深拷贝的区别 
* 浅拷贝：一般地，发生拷贝时，用到了编译器默认的拷贝构造函数（无参数）（就算自己new了内存也无济于事），这样如果拷贝后的接收对象是指针的话，会让拷贝者和被拷贝者都指向同一个内存地址，这样在析构时候，会造成析构2次，而造成内存泄漏。
* 深拷贝：一般地，发生深拷贝时，用到了自己定义的拷贝构造函数（有参数的），同时也New了内存，这样拷贝者和被拷贝者指向不同的内存空间。把之前的对象数据完全复制到了新的空间里面。
```cpp
#include <stdio.h>
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
using namespace std;
class A{
    public:
A(int size) {
    cout<<"constructor"<<endl;
    this->size = size;
    if(size) data = new int[size];
    for(int i = 0;i < size; ++i) data[i] = i;
}
A(const A& o) {
    cout<<"copy constructor"<<endl;  //深拷贝
    this->size = o.size;
    data = new int[size];
    memcpy(data,o.data,size*sizeof(int));
}
A(A &&o) {
    cout<<"move constructor"<<endl;  //浅拷贝
    data = o.data;
    this->size = o.size;
    o.data = nullptr;
    o.size = 0;
}

private:
    int size = 0;
    int * data = nullptr;
};

int main()
{   
    A a(10);
    A b = move(a);
    
  

    return 0;
}
```
## strcpy和memcpy的区别
* strcpy ：strcpy 函数和 strcpy_s 函数在拷贝过程中，如果遇到'\0'结束符，那么直接结束拷贝。
* memcpy ：memcpy 函数拷贝过程中就算遇到'\0'结束符也不会结束0.memcpy 函数内存拷贝的时候，'\0'仅仅是当作了内存中的数据，并不代表拷贝结尾  
## 判断系统大端还是小端
	
假如现有一32位int型数0x12345678，那么其MSB(Most Significant Byte，最高有效字节)为0x12，其LSB (Least Significant Byte，最低有效字节)为0x78，
```cpp
#include <iostream>
using namespace std;
   int main(){
	int a = 0x12345678;
	char b = *((char*)(&a));		// 指针方式其实就是共用体的本质
	if (0x78 == b)
		cout << "小端" << endl;
	else if (0x12 == b)
		cout << "大端" << endl;
	return 0;
}
```
![](https://github.com/lph6755065/detail_cpp/blob/main/picture/1637757841(1).jpg)
## 静态函数和数据
* 静态数据成员在类中声明，在类外定义，定义前需要加`类名::`。一次定义类中所有对象共享该数据。
* 静态成员函数在类中声明，类外定义时，也需要加`类名::`。
* 静态成员不会因为对象的产生而产生，也不会因为对象的消亡而消亡，和对象没必然联系，所以静态成员没有this指针。因为this指向对象的首地址。静态成员一般在main函数结束或者exit后生命周期结束。
* 静态成员数据不占据对象的内存空间。
## 一个对象所占的内存空间
* 比较权威的解释：非静态成员变量总和加上编译器为CPU计算做出的数据对齐处理和支持虚函数产生的内存总和。
* 空类不占空间，内存空间表示占1个字节，由编译器决定。
* 构造函数析构函数也不占空间。
* 但是虚析构函数占空间，因为有指针指向虚函数表头的地址，在64位操作系统里面为8个字节。
```cpp
	#include <iostream>
using namespace std;

class A{
public:
  A(){};
  virtual ~A(){};
};
int main()
{
   A a;
    std::cout << sizeof(a) << std::endl;

    return 0;
}

```
* 继承和多重继承只要空类都是1，除了虚继承是8.
# this指针
* this 指针指向对象的首地址. `*this`就是this所指向的对象。
以下的3个用法是一个意思。
```
return (height * width * length);
return (this->height * this->width * this->length);
return ((*this).height * (*this).width * (*this).length);
```
* 只能在成员函数中使用，在全局和静态函数中不能使用。
![](https://github.com/lph6755065/detail_cpp/blob/main/picture/1637781099(1).png)  
## 多态
* 向不同对象调用同一个方法，不同对象在执行时会产生不同的行为。
```cpp
#include <iostream>
using namespace std;
class A {
public:
	A(){}
	virtual void foo() {
			cout << "this is A"<<endl;
		}	
};
class B : public A {
public:
	B() {

	}
	void foo() {
		cout << "this is B";
	}
};
int main() {
	A a;
	B b;

	a.foo(); 
	b.foo();//this is A
			//this is B
	return 0;
}
```
## 类模板
```cpp
#include <iostream>
using namespace std;
template<class T>
class A{
public:
  A(T a, T b) : x(a), y(b) {}
  T add(){
      return x+y;
  }
private:
    T x,y;
};
 
int main()
{
    A<int>a(1,2);
     std::cout << a.add()<<endl;
    A<double>a1(1.1,2.2);
    std::cout << a1.add();
    return 0;
}
```
## 构造函数和析构函数
* 在全局中定义的对象，最先调用构造函数。
* 一般地，越早构造的析构越迟。
![](https://github.com/lph6755065/detail_cpp/blob/main/picture/1637782566(1).jpg)
## 单例模式 
* 使用类的私有静态指针变量指向类的唯一实例对象，并用共有的静态方法获取该实例。保证程序的整个声明周期里面，实例对象只有一个。
* 其构造函数是私有的，这样不会在其他地方产生实例。
```cpp
#include <iostream>
using namespace std;
class Singleton {
private:
	Singleton(){}
	static Singleton* instance;
	~Singleton(){}
public:
	static Singleton* getInstace() {
		if (instance == nullptr) {
			instance = new Singleton();
			cout << "I am Singleton!"<<endl;
		}
		return instance;
	}
};
Singleton* Singleton::instance = nullptr;
int main() {
	Singleton* S1 = Singleton::getInstace();
	Singleton* S2 = Singleton::getInstace();
	if (S1 == S2) cout << "S1 == S2";//I am Singleton!
					 //S1 == S2
	return 0;
}
```
### 各个变量作用域
```cpp
#include<iostream>
using namespace std;
int i=1;  // i 为全局变量，具有静态生存期。
int main(void)   
{ 
    static int a;  // 静态局部变量，有全局寿命，局部可见。
    int b=-10;  // b, c为局部变量，具有动态生存期。
    int c=0;
    void other(void);
    cout<<"---MAIN---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;//1 0 -10 0
    c=c+8;  other();// 33 4 0 15
    cout<<"---MAIN---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;//33 0 -10 8 
    i=i+10; other();  //75 6 4 15
    other(); //107 8 6 15
    system("pause");
    return 0;
}
void other(void)
{
    static int a=2;
    static int b;
    // a,b为静态局部变量，具有全局寿命，局部可见。
    //只第一次进入函数时被初始化。
    int c=10;   // C为局部变量，具有动态生存期
    //每次进入函数时都初始化。
    a=a+2; i=i+32; c=c+5;
    cout<<"---OTHER---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;
    b=a;
}

	---MAIN---
 i: 1 a: 0 b: -10 c: 0
---OTHER---
 i: 33 a: 4 b: 0 c: 15
---MAIN---
 i: 33 a: 0 b: -10 c: 8
---OTHER---
 i: 75 a: 6 b: 4 c: 15
---OTHER---
 i: 107 a: 8 b: 6 c: 15
sh: 1: pause: not found
	
```
### 使用联合体判断大小端 
* 小端：低地址字节存储在低地址，反之，大端：低->高
* 联合体的特点是使用数据类型最大的数据作为联合体的大小，因此，char a和int b公用内存地址空间，判断a的值就是判断b的低地址空间的值。
```cpp
#include<stdio.h>

union un
{
	char a;
	int b;
};

int main()
{
	union un un1;
	un1.b = 1;

	if (un1.a == 1)
	{
		printf("little-endian\n");
	}
	else
	{
		printf("big-endian\n");
	}

	return 0;
}
```
### 仿函数
* 仿函数(functor)，就是使一个类的使用看上去象一个函数。其实现就是类中实现一个operator()，这个类就有了类似函数的行为，就是一个仿函数类了。
> 有些功能的的代码，会在不同的成员函数中用到，想复用这些代码。

                            1）公共的函数，可以，这是一个解决方法，不过函数用到的一些变量，就可能成为公共的全局变量，再说为了复用这么一片代码，就要单立出一个函数，也不是很好维护。

                            2）仿函数，写一个简单类，除了那些维护一个类的成员函数外，就只是实现一个operator()，在类实例化时，就将要用的，非参数的元素传入类中。

```cpp
#include <iostream>
#include <algorithm>
 
using namespace std;
template<typename T>
class display
{
public:
	void operator()(const T &x)
	{
		cout<<x<<" "; 
	} 
}; 
 
 
int main()
{
	int ia[]={1,2,3,4,5};
	for_each(ia,ia+5,display<int>()); 
	
	return 0; 
} 
```
```cpp
#include <functional>
#include <iostream>
 
struct Foo {
    Foo(int num) : num_(num) {}
    void print_add(int i) const { std::cout << num_+i << '\n'; }
    int num_;
};
 
void print_num(int i)
{
    std::cout << i << '\n';
}
 
struct PrintNum {
    void operator()(int i) const
    {
        std::cout << i << '\n';
    }
};
 
int main()
{
    // store a free function
    std::function<void(int)> f_display = print_num;
    f_display(-9);
 
    // store a lambda
    std::function<void()> f_display_42 = []() { print_num(42); };
    f_display_42();
 
    // store the result of a call to std::bind
    std::function<void()> f_display_31337 = std::bind(print_num, 31337);
    f_display_31337();
 
    // store a call to a member function
    std::function<void(const Foo&, int)> f_add_display = &Foo::print_add;
    const Foo foo(314159);
    f_add_display(foo, 1);
    f_add_display(314159, 1);
 
    // store a call to a data member accessor
    std::function<int(Foo const&)> f_num = &Foo::num_;
    std::cout << "num_: " << f_num(foo) << '\n';
 
    // store a call to a member function and object
    using std::placeholders::_1;
    std::function<void(int)> f_add_display2 = std::bind( &Foo::print_add, foo, _1 );
    f_add_display2(2);
 
    // store a call to a member function and object ptr
    std::function<void(int)> f_add_display3 = std::bind( &Foo::print_add, &foo, _1 );
    f_add_display3(3);
 
    // store a call to a function object
    std::function<void(int)> f_display_obj = PrintNum();
    f_display_obj(18);
 
    auto factorial = [](int n) {
        // store a lambda object to emulate "recursive lambda"; aware of extra overhead
        std::function<int(int)> fac = [&](int n){ return (n < 2) ? 1 : n*fac(n-1); };
        // note that "auto fac = [&](int n){...};" does not work in recursive calls
        return fac(n);
    };
    for (int i{5}; i != 8; ++i) { std::cout << i << "! = " << factorial(i) << ";  "; }
}
```
```cpp
#include <iostream>
#include <numeric>
#include <vector> 
#include <functional> 
using namespace std;
 
int main()
{
	int ia[]={1,2,3,4,5};
	vector<int> iv(ia,ia+5);
	cout<<accumulate(iv.begin(),iv.end(),1,multiplies<int>())<<endl; 
	
	cout<<multiplies<int>()(3,5)<<endl;
	cout<<plus<int>()(3,5)<<endl;
	cout<<minus<int>()(3,5)<<endl;
	cout<<negate<int>()(2)<<endl;
	cout<<greater_equal<int>()(ia[1],ia[0])<<endl;
	modulus<int>  modulusObj;
	cout<<modulusObj(3,5)<<endl; // 3 
	return 0; 
} 
```
### 读取文件的四种方式
```cpp
#include <fstream>
#include<iostream>
#include<string>
using namespace std;
 
 
//文本文件读文件
void test01() {
	//1、包含头文件
 
	//2、创建流对象
	ifstream ifs;
 
	//3、打开文件并且判断是否打开成功
	ifs.open("test.txt",ios::in) ;
	if (!ifs.is_open()) {
		cout << "文件打开失败" << endl;
		return;
	}
 
	//4、读数据
	//第一种
	/**
	char buf[1024] = { 0 };
	while (ifs >> buf) {
		cout << buf << endl;
	}
	*/
 
	//第二种
	/**
	char buf[1024] = { 0 };
	while (ifs.getline(buf,sizeof(buf))) {
		cout << buf << endl;
	}
	*/
 
	//第三种
	/*string buf;
	while (getline(ifs,buf)){
		cout << buf << endl;
	}
	*/
 
	//第四种
	char c;
	while ((c = ifs.get()) != EOF) { // EOF end of file
		cout << c;
	}
 
	//5、关闭文件
	ifs.close();
}
 
int main() {
	test01();
	system(" pause");
}
```
### 二分法注意：
```cpp
#include <stdio.h>
#include<iostream>
#include <vector>
using namespace std;
void findDuplicate(vector<int>& nums) {
        int l = 0;

        int r = nums.size() - 1;
        while (l < r) {
            int mid = l + (r - l) / 2;
            int cnt = 0;
            for (int c : nums) {
                if (c <= mid) {
                    cnt += 1;
                }
            }
            if (cnt > mid) {
                r = mid ;
            }else{
                l = mid + 1;
            }
        }
        cout<<nums[l]<<" ";
	cout<<l;  
        //return l;
        
    }
   
int main()
{   
    vector<int> nums = {1, 2, 3, 6, 4, 5, 6};
    //int res = findDuplicate(arr);
    findDuplicate(nums);
    //cout<<res;
    
    return 0;
}
```
### C++ emplace_back 和 push_back效率区别 . emplace_back传入参数必须是右值时才会触发右值引用比如:emplace_back(10)或者emplace_back(move(a));不然emplace_back(a)功能和push_back(a)一样。
```cpp
#include <iostream>
#include <cstring>
#include <vector>
using namespace std;
 
class A {
public:
    A(int i){
        str = to_string(i);
        cout << "构造函数" << endl; 
    }
    ~A(){cout<<"析"<<endl;}
    A(const A& other): str(other.str){
        cout << "拷贝构造" << endl;
    }
 
public:
    string str;
};
 
int main()
{
    vector<A> vec;
    vec.reserve(10);
    for(int i=0;i<10;i++){
        //vec.push_back(A(i)); //调用了10次构造函数和10次拷贝构造函数,
     vec.emplace_back(i);  //调用了10次构造函数一次拷贝构造函数都没有调用过
    }
 
}

```
### 父类与子类之间的转换
  >子类转换成父类：可以。    
  父类转换成子类：不可以。

 > 如果父类对象的引用指向的实际是一个子类的对象，那么父类对象的引用可以强制转化成子类对象的引用。如：  
  Parent   p=new   Son()  
  Son   s=(Son)p;  --正确

 >Parent   p=new   Parent()  
  Son   s=(Son)p;  --错误

>因为继承的概念就是子孙类会越来越比祖先类详细，所以可以将子孙类强制转换成祖先类，因为祖先有的行为子孙类示例都有了（重新定义的或者是默认的）；但是当将祖先类示例强制转换成子孙类示例的时候，一些子孙类有的行为祖先是没有的（即使的是默认的实现也没有）。
### 智能指针
* unique_ptr  
	
**小结：**

（1）我们需要了解子类向基类的隐式转换，通过将移动构造函数变为带模板的移动构造函数，要明白两者共存情况与只有带模板的移动或者其他构造函数对编译器生成规则的影响！上述代码，此时还不能完成基类向子类的转换！例如:unique_ptr<circle>转unique_ptr<shape>。

（2）auto_ptr与unique_tr都是独占所有权，每次只能被单个对象所拥有，unique_ptr与auto_ptr不同的是使用移动语义来显示的编写。auto_ptr是可以说你随便赋值,但赋值完了之后原来的对象就不知不觉的报废.搞得你莫名其妙。而unique_ptr就干脆不让你可以随便去复制,赋值.如果实在想传个值就哪里,显式的说明内存转移std:move一下。然后这样传值完了之后,之前的对象也同样报废了.只不过整个move你让明显的知道这样操作后会导致之前的unique_ptr对象失效。scope_ptr则是直接不允许拷贝。由于防拷贝的特性，**使其管理的对象不能共享所有权。**
* shared_ptr
	
unique_ptr 算是一种较为安全的智能指针了。但是，一个对象只能被单个 unique_ptr所拥有，这显然不能满足所有使用场合的需求。一种常见的情况是，多个智能指针同时拥有一个对象；当它们全部都失效时，这个对象也同时会被删除。这也就是 shared_ptr 了。

两者区别如下：

多个shared_ptr不仅共享一个对象，同时还得共享同一个计数。当最后一个指向对象(和共享计数)的shared_ptr析构时，它需要删除对象和共享计数。

### 二分法用泛型实现  
```cpp
#include <iostream>
 
using namespace std;
 
template<typename T>
int binary_search(const T s[],const int size,const T &m)
{
 if(size <= 0){
  return -1;
 }
 int i = size/2;
 int k = 1;
 int step = 1;
 
 while(step > 0 && i >= 0 && i < size){
  step = size/(2*++k);
  if(m == s[i]){
   return i;
  }else if(m > s[i]){
   i += step;
  }else{
   i -= step;
  }
 }
 
 return -1;
}
 
int main()
{
 long s[]={1,3,5,6,19,27,38,45,687,6789,10000};
 
 int len = sizeof(s)/sizeof(long);
 
 cout<<"0:"<<binary_search<long>(s,len,1)<<endl;
 cout<<"1:"<<binary_search<long>(s,len,3)<<endl;
 cout<<"5:"<<binary_search<long>(s,len,27)<<endl;
 cout<<"10:"<<binary_search<long>(s,len,10000)<<endl;
 cout<<"-1:"<<binary_search<long>(s,len,10001)<<endl;
 cout<<"-1:"<<binary_search<long>(s,len,44)<<endl;
 cout<<"-1:"<<binary_search<long>(s,len,0)<<endl;
 
 return 0;
}
 
```
### 力扣151 反转字符串里面的单词 
```cpp
#include<string>
#include<iostream>
using namespace std;
  string reverseWords(string s) {
        int len = s.length(), i = 0;
        string ans = "";
        int c = 0;
        while(i < len){
            c = 0; //精彩异常 每次刷新c的数值 而且c的值是每个单词的长度
            while(i < len && s[i] == ' ') i++;  // i = 1,2    i = 8
            while(i < len && s[i] != ' '){    // end loop i = 6 
                i++; c++;    
                 cout << "c: " << c << endl;// i = [3,4,5,6,7]   c = [1-5]              
            }
            cout <<endl;
            cout << "c: " << c << endl;
            if(c){                                       
                ans =  s.substr(i - c, c)+ " " + ans;     
            }
            
        }
         
        return ans.substr(0, ans.length()-1);
    }
int main()
{
  string s("  hello world hi ");

    s = reverseWords(s);


 //获得字符串s中 从第0位开始的长度为2的字符串//默认时的长度为从开始位置到尾

cout << s<< endl;
cout<<s.size()<<endl;

}
``` 
```cpp
class Solution {
public:
    string reverseWords(string s) {
        int i = s.size() - 1;
        string ans;
        while(i >= 0)
        {
            int c = 0;
            while(i >= 0 && s[i] == ' ') --i;
            while(i >= 0 && s[i] != ' ')
            {
                --i;
                ++c;
            }
            if(c)
                ans += s.substr(i+1, c) + " ";
        }

        return ans.substr(0, ans.size()-1);
    }
};

```
### 致命性错误 
* 清楚||的意义
	```cpp
	 if (!st.empty() || c == st.top()) {
                    st.pop();
	```  
	- 上述例子说明栈还是有可能是空的  这样会报异常
	
	```cpp
	if (st.empty() || s != st.top()) {
                st.push(s);
	```  
	- st.empty() || s != st.top()顺序不能颠倒 s != st.top()  || st.empty() 不然也会报错
