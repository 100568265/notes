# 4.C++



## 基础语法



### const关键字

常量必须初始化，不能只声明。

```cpp
const int a;	// ❌
const int a = 10;	// ✅
```



**Q1：宏定义和const常量有什么区别？**

发生时机：宏定义在预处理时，const常量在编译时

类型检查：宏定义没有类型检查，只是做字符串替换，const有类型检查



**const修饰指针**

pointer to const：可以修改指针的指向，不能通过指针修改指针指向内存空间里的内容

const pointer：指针本身是一个const，因此指针的指向不能改变，但是可以改变指针指向内存空间里的值

```cpp
int a = 10;
const int *p1 = &a;		// pointer to const
int const *p2 = &a;		// pointer to const
int * const p3 = &a;	// const pointer
```

C 的声明遵循 **“螺旋法则（spiral rule）”**，并且 `const` 是 **类型限定符，绑定到它左边最近的声明元素；如果左边啥都没有，就绑定右边第一个**。





### new/delete

```cpp
int *p = new int(1);
std::cout << "*p = " << *p << std::endl;
delete p;

int *arr = new int[10];
delete [] arr;
```





### 引用

**定义：**

引用就是给一个已经存在的变量起一个别名，不是新变量，它和原变量共用同一块内存。

```cpp
int a = 1, b = 2;
int &r = a;
r = b;   // ✔ 只是把 b 的值赋值给 a，不是让 r 变成 b 的别名
```

**引用必须在定义时初始化**，不能先声明再赋值

一旦绑定，就不能改绑到别的变量

**没有空引用**，不像指针可以存 `nullptr`

普通引用不能绑定临时值



**Q：引用和指针的区别是什么？**

- **指针**：是独立变量，存的是地址，可以为空、可以随时改指向，有自己内存
- **引用**：别名，本质编译器常底层用指针实现，但语法层面：不能为空、不可改指向





### 强制转换

#### `static_cast`

静态转换

**语义**：编译期完成的显式合理转换，是现代 C++ 中使用频率最高、最安全的转换方式。

**主要场景**：

- 具有隐式转换路径的相关类型转换（如 `double` 转 `int`）。
- 指针类型的隐式反向转换（如 `void*` 转 `T*`）。

```cpp
double d = 3.14;
int i = static_cast<int>(d);
```



#### `const_cast`

**语义**：增加或剥离对象的 `const` 或 `volatile` 限定符。

**主要场景**：对接不支持 `const` 参数的历史 C 语言 API。

**未定义行为警告（UB）**：如果原始对象本身声明为 `const`（可能存放在只读内存区），通过 `const_cast` 去去除 `const` 属性并修改其内容，会直接触发严重的未定义行为。

```cpp
void legacy_c_api(char* str);

const char* msg = "hello";
// 仅在确定 API 内部不会改变 str 的内存时使用
legacy_c_api(const_cast<char*>(msg));
```



#### `dynamic_cast`

**语义**：运行期的多态类型检查与转换。

**主要场景**：多态继承体系中，将基类指针或引用安全的下行转换（Downcasting）或交叉转换（Cross-casting）。**要求源类与目标类必须包含至少一个虚函数（具有 RTTI）**。



#### `reinterpret_cast`

重新解释转换。

**语义**：底层二进制比特位的无条件重解释（如指针与整数互转、不相关指针类型互转）。

**主要场景**：硬件驱动开发、网络协议解析、内存池底层地址计算。

**未定义行为警告（UB）**：直接通过 `reinterpret_cast` 进行类型转换（Type-Punning）几乎总是违反严格别名规则（Strict Aliasing Rule），导致编译器优化破坏代码逻辑。现代 C++ 推荐优先使用标准库工具代替。

```cpp
uintptr_t addr = reinterpret_cast<uintptr_t>(ptr); // 仅用于指针地址的数值运算
```



### extern关键字

`extern` 是 C/C++ 中用于声明标识符具有外部链接性（External Linkage）的关键字。

它的核心作用是告知编译器：“该变量或函数的定义存在于当前翻译单元之外（如其他 `.cpp` 文件或 C 库中），请在链接阶段再去寻找它的具体实现”。



#### 1. 跨文件声明

在 C++ 中，为了遵循**单一定义规则（ODR, One Definition Rule）**，全局变量和全局函数通常需要将“声明”与“定义”分离。

**全局变量的共享**

- **定义**：分配内存空间，只能存在在一个 `.cpp` 文件中。
- **声明**：不分配内存，告知编译器该变量的存在，可以在多个头文件或 `.cpp` 中被 `extern` 声明。

```cpp
// global.cpp (定义并分配内存)
int g_shared_counter = 42; 

// main.cpp (显式声明，引入符号)
extern int g_shared_counter; // 声明，通知编译器在链接时寻找定义

int main() {
    g_shared_counter++; // 正常使用
}
```



#### 2.`extern "C"`

C++ 支持函数重载（Overloading），因此编译器在编译 C++ 代码时会对函数名进行**名字修饰（Name Mangling）**（如 `void foo(int)` 会被修饰为类似 `_Z3fooi` 的符号）。

而 C 语言不支持重载，编译器保持原始函数名（如 `_foo`）。

`extern "C"` 的作用是让 C++ 编译器按照 C 语言的命名与调用规范来处理指定的函数或变量。



**举例，假设有一组代码：**

```cpp
void func(int a);
void func(double a);
```

- **C++ 编译器编译后**（在符号表中）：
  - `func(int)` 会被改成类似 `_Z4funci` 这样的怪异符号。
  - `func(double)` 会被改成类似 `_Z4funcd` 这样的怪异符号。
- **C 语言编译器编译后**（C 不支持重载）：
  - `func` 编译后在符号表中就叫 `func`（或者 `_func`）。

这就产生了一个根本性的**跨语言/跨库调用难题**。

假设你在用 C++ 写一个视频播放器，需要调用底层用 C 语言写的库（比如 `FFmpeg` 或 `SQLite`）。

- **没有 `extern "C"` 时发生的问题**： 在 C++ 中写下 `sqlite3_open(...)` 时，C++ 编译器去链接器里寻找的符号是 `_Z12sqlite3_open...`（C++修饰过的名字）。但 `libsqlite3.so` 是用 C 编译出来的，里面的符号叫 `sqlite3_open`。
  - **结果**：链接失败，报 `Undefined reference to sqlite3_open` 错误！
- **加上 `extern "C"` 的作用**： 告诉 C++ 编译器：“这个函数来自 C 库，你**找符号时不要加 C++ 的修饰**，直接去目标文件里找 `sqlite3_open`！”



**关键误区澄清**

1. **`extern "C"` 并不影响函数体内部的 C++ 语法**： 在 `extern "C"` 包裹的函数内部，你依然可以写 `new`/`delete`、用 `std::string`、抛出异常或创建类。它**仅仅决定**了这个函数在“链接阶段”暴露出去的名字和参数传递规约（ABI）。
2. **`extern "C"` 包裹的函数不能再重载**： 因为 C 语言不支持重载，如果你写了两个同名的 `extern "C"` 函数，编译器在生成 C 符号时就会直接报重名冲突。



















































## C++新特性



### 自动类型推导

自动类型推导体现在代码中就是`auto`关键字

```cpp
#include <iostream>

int main(){
    auto x = 1;
    auto y = 3.14;
    auto z = 'a';
    
    std::cout << x << std::endl;
    std::cout << y << std::endl;
    std::cout << z << std::endl;
}
```





### 智能指针

### `shared_ptr`(共享指针)

通过共享指针，如果我们在同一个程序中将某个资源使用智能指针进行管理，那么该数据无论在多少个函数内进行传递，都不会发生资源的复制，运行效率会大大提高。

当所有的程序使用完毕后，还会自动回收，不会造成内存泄漏。

```cpp
#include <iostream>
#include <memory>

int main(){
    auto p1 = std::make_shared<std::string>("this is a str.");
    std::cout << "p1's reference count = " << p1.use_count() << ", points to addr: " << p1.get() << std::endl;  // count = 1, addr = 0x60cb0eab42c0

    auto p2 = p1;
    std::cout << "p2's reference count = " << p2.use_count() << ", points to addr: " << p2.get() << std::endl;  // count = 2, addr = 0x60cb0eab42c0

    p1.reset();
    std::cout << "p1's reference count = " << p1.use_count() << ", points to addr: " << p1.get() << std::endl;  // count = 0, addr : 0
}
```





### Lambda表达式

Lambda表达式是C++11引入的一种匿名函数，没有名字，但是也可以像正常函数一样调用。

Lambda表达式有自己的语法，格式如下：

`[capture_list] (parameters) -> return_type {function_body}`

capture_list表示捕获列表，可以用于捕获外部变量

parameters表示参数列表



```cpp
#include <iostream>
#include <algorithm>

int main(){
    // 定义了两个数相加的函数，捕获列表为空，a b 为参数，返回值类型是int，函数体是return a+b
    auto add = [](int a, int b) -> int { return a + b; };	
    
    // 接着调用add计算了2+5并存储在sum中
    int sum = add(2,5);
    
    // 此时又定义了一个函数print_sum,并且把上面计算的sum放进了捕获列表里
    auto print_sum = [sum]()-> void {std::cout << "3 + 5 = " << sum << std::endl; };
    print_sum();
}
```





### `std::function`

函数包装器是C++11引入的一种通用函数包装器，它可以存储任意可调用对象(函数，函数指针，lambda表达式等)，并提供统一的调用接口。





### 多线程与回调函数



```cpp
#include <iostream>
#include <thread>
#include <chrono>
#include <functional>
#include <cpp-httplib/httplib.h>

class Download{
public:
    void download(const std::string &host, 
                  const std::string &path,
                  const std::function<void(const std::string &, const std::string &)> &callback
                 )
    {
        std::cout << "线程ID: " << std::this_thread::get_id() << std::endl;
        httplib::Client client(host);
        auto response = client.Get(path);
        if(response && response->status == 200)
        	callback(path, response->body);
    }
    
    void start_download(const std::string &host, 
                        const std::string &path,
                       	const std::function<void(const std::string &, const std::string &)> &callback)
    {
        auto download_fun = std::bind(&Download::download,
                                      this,
                                      std::placeholders::_1,
                                      std::placeholders::_2,
                                      std::placeholders::_3);
        std::thread download_thread(download_fun, host, path, callback);
        download_thread.detach();	// 将线程与当前进程分离，使得线程可以在后台运行
    }
};

int main()
{
	Download download;
    auto download_finish_callback = [](const std::string &path, const std::string &result) -> void
    {
        std::cout << "下载完成:" << path << " 共: " << result.length() << "字， 内容为:" << result.substr(0,16) << std::endl;
    };
    
    download.start_download("http://localhost:8000", "/novel1.txt", download_finish_callback)
    download.start_download("http://localhost:8000", "/novel2.txt", download_finish_callback)
    download.start_download("http://localhost:8000", "/novel3.txt", download_finish_callback)
    
    std::this_thread::sleep_for(std::chrono::miliseconds(1000 * 10));
}
```































































































































































































































