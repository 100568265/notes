# C++



## 自动类型推导

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





## 智能指针













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





## Lambda表达式

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





## `std::function`

函数包装器是C++11引入的一种通用函数包装器，它可以存储任意可调用对象(函数，函数指针，lambda表达式等)，并提供统一的调用接口。





## 多线程与回调函数



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













## 面向对象



### 类





























































































































































































































