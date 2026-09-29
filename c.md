# 1.C



## 常量&变量

**定义**

变量：在程序的运行期间可以发生改变的量

常量：在程序的运行期间**不可以**发生改变的量



**常量和常量表达式之间的区别？**

常量表达式：在编译期可以直接求值的表达式



```c
#define N 5

const int M = 10; // 它是常量，但是不是常量表达式 

int main(){
    int arr1[N];	// 这个可以，因为N是常量表达式
    // int arr2[M];	// 这个不行，M不算常量表达式
}
```



## 标识符&关键字

**标识符：**为变量，宏，函数等起的名字

**关键字：**对C语言有特殊意义的名字



## 格式化输入&输出

### **printf函数**

格式：%m.pX

m：(minimum field width)最小字符宽度，表明要显示的最少字符数量

p：(precision)精度，精度的含义依赖转换说明符(X)

​	%d - p代表待显示数字的最小个数(必要时会在前面补0)；如果省略p，则默认为1

​	%f - p代表小数点后数字的个数(默认为6)；

| X    | 含义                                   |
| ---- | -------------------------------------- |
| %d   | 以10进制形式解释这片内存空间，并输出   |
| %f   | 以浮点数的形式解释这片内存空间，并输出 |
| %s   | 以字符串的形式解释这片内存空间，并输出 |
| %c   | 以字符的形式解释这片内存空间，并输出   |
| %o   | 无符号8进制                            |
| %x   | 无符号16进制                           |





### scanf函数

**SYNOPSIS**

`#include <stdio>`

`int scanf(const char *restrict format, ...);`



**说明**

scanf本质上是一个"模式匹配函数"，试图把输入的字符与转换说明进行匹配。

它从左到右依次处理转换说明；

如果成功，则继续处理后续的字符串；

如果失败，则立即返回，返回值表示处理的转换说明成功的个数。

```c
#include <stdio.h>

int main(void) {
    int i;
    float f;
    int n = scanf("%d%f", &i, &f);	// 转换说明：表示将字符数据转换成对应的二进制数据

    return 0;
}
```

scanf注意事项：

1. 永远不会包含空白字符
2. scanf不会检查数组越界



**读写字符**

**SYNOPSIS**

`int getchar(void);`	  从标准输入中读取下一个字符

`int putchar(int c);`	写一个字符到标准输出

**注意：**这两个函数效率比printf/scanf高，如果只是处理字符类型，用这两个。

```c
#include <stdio.h>

int main(void) {
    // 从标准输入中读取字符串
    char buf[50];
    int i = 0;
    int ch;
    while ((ch = getchar()) != '\n') {
        buf[i] = ch;
        i++;
    }
    buf[i] = '\0';  // 手动添加字符串结束标志
    printf("your input = %s", buf);
    return 0;
}

```





## 数据类型&类型转换

### 基本数据类型

**整型**

`char`：大小为1个字节，并且采用ASCII编码表示

`short`

`int` 

`long`

`long long`



**浮点型**

`float`（IEEE754标准）

`double`



**布尔类型**

C99中定义了布尔类型，在`<stdbool.h>`头文件中





### 类型转换

**隐式类型转换：**编译器做的类型转换，不用程序员手动说明

从小数据向大数据转换；

有符号和无符号运算时，向无符号转换；



**显式类型转换：**强制类型转换





### typedef

可以使用typedef给类型起别名

格式：`typedef type_name alias;`

 

**Q:宏定义也可以取别名，宏定义和typedef有什么区别？**

宏定义是在预处理阶段进行处理的(简单文本替换)，编译器是不能识别宏定义的，因此编译器无法给出提示。

typedef，编译器能够识别typedef定义的别名，如果出错，可以给出提示。





### sizeof运算符

语法：`sizeof(type_name)`

作用：计算某类型数据所占内存空间

sizeof运算符在编译阶段就求值了，因此以下的代码是合法的。

```c
int i = 3;
int arr[sizeof(i)];
```





## 表达式&运算符

**表达式：**计算某个值的公式。

最简单的表达式：变量，常量。



**运算符：**连接表达式，创建更复杂的表达式。





## 数组&指针

### **基本概念**

计算机最小的寻址单位：字节。

变量的地址：变量第一个字节的地址。

指针变量/指针：存放地址的变量。

空指针：不指向任何对象的指针(用宏NULL，其值为0)



**Q1：指针变量只是存放了变量的首地址，那么计算机是如何访问指针指向的对象？**

因为声明指针时，需要指明基础类型。



**野指针：**未初始化的指针，或是指向未知区域的指针。

```c
int *p;
int *q = 0x7F;
```

对野指针进行解引用运算，会导致未定义的行为。



**指针的核心用法：**作为参数传递。

函数调用时，将实参的值完整拷贝一份赋值给形参。

因此通过指针传递，可以达到省内存空间的目的。



### 指针和数组

**1.数组名可以作为指针**

数组名作为指针时是一个指针常量(const pointer)，指针不可以修改❌️

```c
int main() {
    int arr[10] = {0,1,2,3,4,5,6,7,8,9};
    *arr = 100;
    *(arr+7) = 700;
    // arr++; ❌️
    return 0;
}
```



**2.指针也可以作为数组名**(可以对指针使用[]运算符)

```c
int find_largest(int *arr, int n){
    int max = arr[0];
    for(int i = 0; i < n; i++){
        if(arr[i] > max) max = arr[i];	//arr[i] 等价于 *(arr+i)
    }
}
```





**一维数组**

一维数组作为参数传递的时候，会退化为指针

```c
int sum_array(int arr[]，int n){	// 形式上好像是数组，实际上是一个指针
    int sum = 0;
    for(int i=0;i<n;i++){
        sum+=arr[i];
    }
    return sum;
}
```



**二维数组**

二维数组作为参数传递，必须指定列的个数

```c
int sum_array(int matrix[][4]，int row){	
    int sum = 0;
    for(int i=0;i<n;i++){
        for(int j=0;j<4;j++){
            sum += matrix[i][j];
        }
    }
    return sum;
}
```

**原因：**编译器必须知道**列数（Cols）**，才能算出“跳过一行需要跨越多少个字节”。如果没有列数，编译器就无法对 `arr[i][j]` 进行正确的内存寻址。



**Q2：那么，怎么才能传递一个列数不固定的二维数组呢？**

降维拍平成一维指针。将二维数组当做一维连续内存传递，传入总行数和总列数，手动计算偏移：

```c
int sum_matrix(int* arr, int rows, int cols) {
    // 访问第 i 行第 j 列：arr[i * cols + j]
    int sum = 0;
    for(int i = 0; i < rows * cols; i++){
        sum += arr[i];
    }
    return sum;
}

int main(void) {
    int matrix[3][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12}};
    int sum = sum_matrix(&matrix[0][0],3,4);
    printf("%d", sum);
    return 0;
}
```





## 字符串

### **字符串字面量**

用双引号括起来的字符序列就是字符串字面量。

编译器会把两个相邻的字符串字面量合并成一个字符串字面量。

相邻：当两个字符串字面量仅以空白字符分割时，就认为它们是相邻的。

```c
printf("I love xixi!\n");
printf("I love xixi!"
      "  --From Thomax He");
```



**Q1：字符串字面量是如何存储的？**

C语言会用字符数组来存储字符串字面量。

```c
char* ch1 = "abc";	// a b c \0
char* ch2 = "";		// \0
printf("hello kitty.\n");	// 这里传递的其实是一个字符指针char*
```



### 字符串变量

C语言没有专门的字符串类型，它依赖于字符数组存在。(但它们不是等价的)

```c
char name[10] = "Allen";	//  A   l   l   e   n   \0   \0   \0   \0   \0
						    //  0   1   2   3   4    5    6    7    8    9 
							//  |<----这部分是字符串--->|
```



比如说，这样打印出来的，就是乱码：

```c
char name[5] = "Allen";
printf("%s",name);
```



**字符串的初始化**

```c
char name[10] = "Allen";
char name2[] = "Allen";		// 数组的初始化式(可以修改)
```



**字符指针的初始化**

```c
char *name = "Allen";	// 字符串字面量(不可以修改)
```



**读写字符串**

```c
// 打印到标准输出
char name[] = "Beyonce";
printf("%s\n",name);
puts(name);			// 等价于上面一条

// 从标准输入读取
char name[10];
gets(name);		//gets不会检查数组是否越界
```



### 字符串的库函数

**strlen**

`#include <string.h>`
`size_t strlen(const char *s);	// const指明在strlen中不会修改s指向的内容`



**strcmp**

`#include <string.h>`
`int strcmp(const char *s1, const char *s2);`

```c
// 如果S1 > S2，返回正数
//如果S1 = S2，返回0
// 如果S1 < S2，返回负数
```



**strcpy**

`#include <string.h>`
`char *strcpy(char *restrict dst, const char *restrict src);`

```c
char s[4];
strcpy(s, "hello");
```



**strncpy**

`char* strncpy( char* restrict dest, const char* restrict src, size_t count );`

安全的strcpy

```c
char s1[10];
strncpy(s1,"Hello",4);	// Hell
strncpy(s1,"Hello",6);	// Hello\0
strncpy(s1,"Hello",8);	// Hello\0\0\0\0
```



**strcat**

`char *strcat(char *restrict dst, const char *restrict src);`

把字符串src的内容追加到字符串dest的末尾，并返回dest。(不会检查数组越界)



**字符指针数组**

```c
char* planets[] = {"Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune", "Pluto"};
```







## 结构体&枚举

**结构体对象的初始化**

```c
struct student_s{
	int number;
	char name[25];
	bool gender;
	int chinese;
	int math;
	int english;
};

int main(){
    struct student_s s1 = {1, "liuyifei", false, 100, 100, 100};
    struct student_s s2 = {1, "huasheng", true};	// 未初始化的成员会被赋值为0
}
```



**结构体的操作**

```c
// 获取成员
s1.name;

// 赋值
struct student_s s3 = s1;
```

**注意：**当结构体作为参数或者返回值时，会拷贝整个结构体中的数据。

为了避免拷贝数据，可以传递指向结构体的指针。

```c
void print_student(struct student_s s){
    printf("%d %s %d\n",s.number, s.name, s.gender);
    s.number = 100;	// 这里并不会影响被传入的结构体本身，只是拷贝了一份s
}

// 传递指针
void print_student(struct student_s* s){
    printf("%d %s %d\n",s->number, s->name, s->gender);
}
```





**enum**

在程序中有一些变量只能取一些离散的值

```c
typedef enum suit {
    SPADE, 
    HEART, 
    CLUB, 
    DIAMOND
}Suit;

int main(){
	Suit s = SPADE;   
}
```

枚举类型的值，其实是一些整数常量。

当然，我们也可以显式的指定枚举的值。

```c
typedef enum suit {
    SPADE, 
    HEART = 7, 
    CLUB, 
    DIAMOND = 16
}Suit;
```





## 动态内存分配

在头文件`<stdlib.h>`中定义了3个动态内存分配的函数

`#include <stdlib.h>`

**malloc**

`void *malloc(size_t size);`					

分配size个字节的内存；

不会清空内存块；

若分配不成功，返回空指针。



**calloc**

`void *calloc(size_t nmemb, size_t size);`	  

为nmemb个元素分配内存空间，每个元素的大小为size个字节；

会清空内存块；

若分配不成功，返回空指针



**realloc**

`void *realloc(void *_Nullable ptr, size_t size);`

调整先前分配内存块的大小;

如果分配成功，返回指向新内存块的指针;

否则返回空指针



**练习1：实现一个字符串拼接函数**

```c
char* my_strcat(const char *s1, const char *s2){
    // 1. 空指针保护
    if (s1 == NULL || s2 == NULL) return NULL;
    
    // 2. 暂存长度，避免重复遍历
    size_t len1 = strlen(s1);
    size_t len2 = strlen(s2);

    // 3. 分配内存（包含 '\0' 的空间）
    char *s = (char *)malloc(len1 + len2 + 1);
    if (s == NULL) return NULL;
    
    // 4. 拷贝数据
    memcpy(s, s1, len1);
    memcpy(s + len1, s2, len2 + 1); // len2 + 1 会把 s2 末尾的 '\0' 一并拷入
}
```

注意：这个函数会申请堆内存空间，需要手动释放，否则可能造成内存泄漏。



**free**

`void free(void* ptr);`

ptr必须是先前调用malloc，calloc，realloc返回的指针。



**Q1：ptr只是指向申请内存块的首地址，那么free函数如何知道该释放多大的内存空间？**

当你调用 `malloc(size)` 时，系统实际分配的内存空间比你请求的 `size` **要大**。`malloc` 会在返回给你的指针**正前方**，悄悄存入这块内存的“账本”——即**元数据（Metadata）**，其中就记录了这块内存的大小。





## 函数指针

指向函数的指针，函数也有地址。



**语法：**

函数指针的声明看起来有些别扭，核心在于用括号把指针符号和变量名括起来。

`返回值类型 (*指针变量名)(参数列表);`



**基础使用：**

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    // 1. 声明函数指针
    int (*func_ptr)(int, int);

    // 2. 赋值：函数名本身就是地址（也可以写 &add，效果相同）
    func_ptr = add; 

    // 3. 调用：直接像普通函数一样用，或者使用解引用写法
    int res1 = func_ptr(10, 20);     // 推荐：简洁明了
    int res2 = (*func_ptr)(10, 20);  // 显式解引用：语义等价

    printf("res1: %d, res2: %d\n", res1, res2); // 输出 30, 30
    return 0;
}
```





**qsort**

```c
void qsort( void* ptr, size_t count, size_t size,
            int (*comp)(const void*, const void*) );
```

ptr：指向要排序的数组

count：数组中元素的个数

size：元素的大小

comp：比较函数



使用方法：这里可以通过定义一个自定义的比较规则的函数，来传给qsort，qsort会根据这个自定义的比较规则去排序数组。

```c
qsort(students, SIZE(students), sizeof(Student), compare); 
```

