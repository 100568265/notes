# Python



## 环境配置

虚拟环境：

```shell
# 创建虚拟环境
python3 -m venv venv
# 激活虚拟环境
source venv/bin/activate
```

**说明：**通过虚拟的运行环境，可以保证每个python项目都在一个相对独立隔离的运行环境中运行，项目之间互不影响。





## 数据类型

**常见的基础数据类型**

`int` 

`float` 

`str` 

`bool` 

`NoneType`

说明：通过`type()`可以获取数据的类型



## **字符串格式化**

通过%占位符的形式完成字符串和变量的快速拼接

```python
name = "Watson"
age = 18
print("大家好，我是 %s，我今年 %s" % (name,age))
```

也可以通过f的形式来完成快速格式化

```python
print(f"大家好，我是{name}, 我今年{age}")
```





## for循环

for-in语法

```python
num = [1,2,3,4,5,6]
for s in num:
    print(s)
```



for-range语法

```python
# 用法1: range(end) -> 从0开始获取，直到end前
for s in range(100):	# 打印0-99	
	print(s)
    
# 用法2: range(start,end) 左开右闭
for s in range(0,100)   # 打印0-99
	print(s)

# 用法3: range(start,end,step)
for s in range(0,100,2)
	print(s)
```





## 数据容器

### list

有序容器，索引访问，元素可重复，可以修改

```python
list1 = [1,2,3,4,5]
```



**列表的常见方法：**

| 方法        | 作用                                                   | 样例               |
| ----------- | ------------------------------------------------------ | ------------------ |
| `append()`  | 在列表的尾部追加元素                                   | `s.append(10086)`  |
| `insert()`  | 在指定索引前，插入该元素                               | `s.insert(0,92)`   |
| `remove()`  | 移除列表中第一个匹配到的值                             | `s.remove(75)`     |
| `pop()`     | 删除列表中指定索引位置的元素(如未指定，默认删最后一个) | `s.pop(2)/s.pop()` |
| `sort()`    | 对列表进行排序(列表元素的数据类型一致，才可以进行排序) | `s.sort()`         |
| `reserve()` | 反转列表元素                                           | `s.reverse()`      |



### str

有序容器，索引访问，不可修改

```python
s = "hello-python"
```



**字符串的常用方法：**

| 方法              | 作用                                       | 样例                     |
| ----------------- | ------------------------------------------ | ------------------------ |
| `find()`          | 查找子串第一次出现的索引位置，找不到返回-1 | `s.find('Python')`       |
| `count()`         | 统计子串出现的次数                         | `s.count('H')`           |
| `upper()/lower()` | 切换大小写                                 | `s.upper()/s.lower()`    |
| `split()`         | 按照指定分隔符分割成列表                   | `s.split(' ')`           |
| `strip()`         | 去除字符串两端的空白字符/指定字符          | `s.strip()/s.strip('*')` |
| `replace()`       | 将字符串中的指定子串替换为新的子串         | `s.replace('H','C')`     |
| `startswith()`    | 检查字符串是否以指定子串开头，返回布尔值   | `s.startswith('P')`      |





### tuple

有序容器，索引访问，元素可重复，不可修改(元组一旦定义完成，不可修改)

```python
t1 = (1,2,3,4,5,6,7)
t2 = (1,)	# 单元素的元组后面要加逗号
#定义空元组
t2 = ()	
t3 = tuple()
```



**元组的查询方法：**

| 方法    | 作用                                 | 样例          |
| ------- | ------------------------------------ | ------------- |
| count() | 统计指定元素的数量                   | `t1.count(7)` |
| index() | 获取指定元素的索引，如果不存在将报错 | `t1.index(7)` |



**组包和解包**

组包(Packing)：将多个值合并到一个容器(列表，元组)中

```python
# 定义元组，组包
t1 = (5,7,9,1)
t2 = 5,7,9,1
```

解包(Unpacking)：将容器(元组，列表)解开成独立的元素，分别赋值给多个变量

```python
# 基础解包
a,b,c,d = t1

# 扩展解包
x, *y, z = t2 # x为5，y为[7,9]，z为1
```



### set

无序容器，不可重复，可修改

```python
s1 = {1,2,3,4,5}

# 定义空集合
s2 = set() 
```



**集合的常见方法：**

| 方法             | 作用                       | 样例                  |
| ---------------- | -------------------------- | --------------------- |
| `add(..)`        | 添加元素                   | `s1.add('t')`         |
| `remove(..)`     | 移除指定元素(不存在将报错) | `s1.remove('t')`      |
| `pop()`          | 随机删除元素并返回         | `e = s1.pop()`        |
| `clear()`        | 清空集合                   | `s1.clear()`          |
| `difference`     | 差集                       | `s1.defference(s2)`   |
| `union()`        | 并集                       | `s1.union(s2)`        |
| `intersection()` | 交集                       | `s1.intersection(s2)` |



**为什么要用集合？**

**场景：**在业务中，需要定义一个变量，来批量存储用户的手机号(唯一的)？

list和tuple可以吗？不能，因为它们是可以存储重复元素的。

这时候使用set，set会自动去重，存储不重复的元素。





### dict

字典容器存储的是键值对类型的数据，key不能重复，可修改

key必须得是不可变类型(str, int, float, tuple)，不能是list, set, dict

```python
dict1 = {"watson":100,"yummi":99}

# 定义空字典
dict2 = {}
dict2 = dict()

# 根据key获取value
score = dict1["watson"]
```



**字典的增删改查操作：**

| 方法                | 作用                                  | 样例                          |
| ------------------- | ------------------------------------- | ----------------------------- |
| `pop(key)`          | 删除指定的key，并返回该key对应的value | `score = dict1.pop("watson")` |
| `del 字典名称[key]` | 删除字典中指定的键值对                | `del dict1["watson"]`         |
| `keys()`            | 获取所有的key                         | `dict1.keys()`                |
| `values()`          | 获取所有的value                       | `dict1.values()`              |
| `items()`           | 获取所有的键值对                      | `dict1.items()`               |







## 函数

**定义与调用：**

```python
def circle_area(r):
    area = 3.14 * r ** 2
    return area

# 调用
area = circle_area(5)
```



**函数说明文档：**

```python
# 定义一个函数，根据半径，计算圆的周长，面积
def circle_area_len(r):
    """
    该函数用于根据圆的半径，计算面积和周长
    :param r: 圆的半径
    :return: 圆的面积 , 圆的周长
    """
    return 3.14*r*r, 2*r*3.14
```



**global关键字**

global关键字用于明确告诉python解释器，在函数中要使用全局变量，使得可以再函数内部修改全局变量的值。

```python
num1 = 1
def fun1():
    global num1 
    num1 = 100	# 如果这里不声明global，则这行代码会被认为创建了一个叫num1的局部变量
    print(num1)

fun1()		# 100
print(num1) # 100
```



**不定长参数**

不定长参数分为位置类型和关键字类型

```python
def calc_data(*args, **kwargs):
    min_data = min(args) 			# 取最小值
    max_data = max(args) 			# 取最大值
    avg_data = sum(args)/len(args)	# 取平均值
	
    if kwargs.get('round') is not None:
        avg_data = round(avg_data, kwargs.get('round'))

    if kwargs.get('print'):
        print(f"min:{min_data}, max:{max_data}")
    
    return min_data, max_data, avg_data

# 调用函数
calc_data(1,2,3,4,5,6,7,8,round=3,print=True)
```



**函数作为参数**

```python
def add(x,y):
    return x + y

def subtract(x,y):
    return x - y

def calc(x,y,oper):
    return oper(x,y)

result = calc(10,20,add)	# add作为函数参数传入
print(result)
```



**匿名函数(lambda表达式)**

匿名函数指的是没有名称的函数，需要lambda表达式来声明函数，可以简化简单函数的编写(单行表达式)。

语法：`lambda 参数列表 : 函数体`

```python
# 需求：完成如下列表的排序操作，按照每个元素的字符个数，从小到大排序
data_list = ["C++", "C", "Python", "Jack", "PHP", "Java", "Go", "JavaScript", "Rust"]
print(data_list)

data_list.sort(key=lambda item : len(item))
print(data_list)
```



**递归**

```python
# 计算n的阶乘
def factorial(n):
    if n == 1:
    	return 1
    return n * factorial(n-1)
```



**类型注解**

类型注解是一种语法特性，用于明确标识变量，函数参数和返回值的数据类型，增加可维护性。

```python
# 定义变量
a: int = 695
score: float = 98.5

names: list[str] = ["A","C","E"]
goods: tuple[str,int,int] = ("phone", 5999, 1)

# 参数和返回值注解
def calc(scores: list[int]) -> float:
    return sum(scores) / len(scores)
```





## 模块和包



### 模块

**模块：**单个`.py`文件就是一个模块(module)，里面包含普通变量，函数，类

**功能：**模块里面装的所有东西，都叫成员/功能。

文件名叫什么，模块名就叫什么



**导入模块：**

| 导入形式                    | 代码样例                             | 调用方式        | 调用样例                 |
| --------------------------- | ------------------------------------ | --------------- | ------------------------ |
| `import 模块名`             | `import random, os`                  | `模块名.功能名` | `random.randint(10,100)` |
| `from 模块名 import 功能名` | `from random import randint, choice` | `功能名`        | `randint(10,100)`        |
| `from 模块名 import *`      | `from random import *`               | `功能名`        | `randint(10,100)`        |

如果导入的是模块，调用的时候就要`模块名.功能名`

如果导入的是功能，直接调用`功能名`



### **特殊变量**

`__name__`：Python中的内置变量，表示当前模块的名字

- 直接运行当前模块，`__name__`的值为`"__main__"`
- 当该模块被导入时，`__name__`的值就是模块名



`__name__`有什么用？

可以用作测试函数

```python
# 执行当前文件，则会执行如下代码；如果被当做模块导入，如下代码则不会执行
def some_func():
    print('---')
    
if __name__ == '__main__':
    some_func()
```



### 包

本质就是一  个**文件夹**，该文件夹中可以包含多个python模块，文件夹下还包含了一个`__init__.py`

作用：模块文件较多时，用来管理多个模块(包的本质也是一个模块)



**包的导入方式：**

| 导入形式                         | 调用方式             |
| -------------------------------- | -------------------- |
| `import 包名.模块名`             | `包名.模块名.功能名` |
| `from 包名 import 模块名`        | `模块名.功能名`      |
| `from 包名 import *`             | `模块名.功能名`      |
| `from 包名.模块名 import 功能名` | `功能名`             |
| `from 包名.模块名 import *`      | `功能名`             |





## 异常

语法格式：

```python
try:
    可能出现异常的业务代码1
    可能出现异常的业务代码1
    ...
except [异常类型 as 变量名]:
    出现异常时的预案
finally:
    不管是否出现异常，都会执行的代码
```



样例：

```python
try:
    print("================")
    print(my_name)
    print("================")
except Exception as e:
    print("程序运行报错,错误信息: ", e)
finally:
    print("释放资源~")
```



**异常的传递：**

异常传递就是在函数调用中层层上报的过程，直到有人处理它，或者程序崩溃。









## 面向对象



### **定义类**

```python
class Car:
    # 类属性
    wheel = 4
    tax_rate = 0.1
    
    def __init__(self, c_brand, c_name, c_price):
        self.brand = c_brand
        self.name = c_name
        self.price = c_price
        
    # 实例方法
    def run(self):
        print(f"{self.brand} {self.name} 正在高速行驶")
        
# 创建对象
c1 = Car("BMW","X5",500000)
print(c1.__dict__)	# 会将对象中的所有属性以字典的形式输出
c1.run()
```





### 封装

约定：在属性名/方法名前加双下划线

```python
def __init__(self, c_brand, c_name, c_price, c_owner):
        self.brand = c_brand
        self.name = c_name
        self.price = c_price
        self.__owner = c_owner

# 创建对象
c1 = Car("BMW","X5",500000,"Watson")
```



### 继承



```python
class Car:
    def __init__(self, c_brand, c_name, c_price):
        self.brand = c_brand
        self.name = c_name
        self.price = c_price
        
    def start(self):
        print(f'{self.brand} {self.name} 正在行驶...')
        
    def charge(self):
        print(f'{self.brand} {self.name} 正在补充燃料...')

# 定义子类
class FuelCar(Car):
    # 重写父类方法
    def charge(self):
        print(f'{self.brand} {self.name} 正在加油...')

# 定义子类
class EVCar(Car):
    # 重写父类方法
    def charge(self):
        print(f'{self.brand} {self.name} 正在充电...')

if __name__ == '__main__':
    c1 = FuelCar("BMW", "X5", 500000)
    c1.start()
    c1.charge()
```





### 多态

```python
def handle_charge(car: Car):	# 参数类型声明，指定的是父类型
    car.charge()
```



鸭子类型：python中，关注的是对象的行为(它有什么方法)，而不是对象的类型(他是什么类)。

```python
class Dog:
    def __init__(self,age,name):
        self.age = age
        self.name = name 
        
    def swimming(self):
        print(f'{self.age}岁的{self.name}正在游泳...')
        
class Duck:
    def __init__(self,age,name):
        self.age = age
        self.name = name 
        
    def swimming(self):
        print(f'{self.age}岁的{self.name}正在游泳...')
        
class Pig:
    def __init__(self,age,name):
        self.age = age
        self.name = name 
        
    def swimming(self):
        print(f'{self.age}岁的{self.name}正在游泳...')

def go_swimming(duck):
    duck.swimming()
    
if __name__ == '__main__':
    go_swimming(Dog("旺财",4))
    go_swimming(Duck("唐老鸭",2))
    go_swimming(Pig("佩奇",3))
```







## 多线程与回调函数

我们将函数A作为参数传递给函数B，并在函数B通过该参数调用函数A，从而实现对执行结果的处理，比如下载完成后调用回调函数用于反馈下载结果。

下面使用python来实现多线程下载小说：

```python
import threading	# python线程库
import requests		# HTTP请求库

class Download:
    # 1.download方法接收下载的url和回调函数callback作为参数，然后输出当前的线程id和下载的url
    def download(self, url, callback):
        print(f'thread : {threading.get_ident()} start downloading: {url}')
        
        # 2.接着调用requests请求数据，
        response = requests.get(url)	# 阻塞IO
        response.encoding = 'utf-8'
        
        # 3.最后将url和数据文本通过回调函数传递出去
        callback(url, response.text)

    # 1.start_doanload方法同样接收下载的url和回调函数callback作为参数
    def start_download(self, url, callback):
        # 2.然后在函数里新建一个线程thread来运行目标函数download，并将url和callback作为参数传递
        thread = threading.Thread(target=self.download, args=(url, callback))
        # 3.启动线程
        thread.start()

# 定义一个回调函数，用于处理/展示下载完成的数据        
def download_finish_callback(url, result):
    print(f'{url}download completed, total:{len(result)} words, content: {result[:5]}...')

def main():
    d = Download()	# 实例化对象
    # 分别调用下载小说，并将download_finish_callback作为回调函数使用
    d.start_download('http://localhost:8000/novel1.txt', download_finish_callback)
    d.start_download('http://localhost:8000/novel2.txt', download_finish_callback)
    d.start_download('http://localhost:8000/novel3.txt', download_finish_callback)

if __name__ == '__main__':
    main()
```



**思考：**为什么要将`download_finish_callback`回调函数作为参数传进download方法？直接在download方法体里面调用`download_finish_callback`函数不行吗？

答案：为了解耦，重点在于把`下载`和`下载后的处理`分离，谁使用这个模块，谁才决定数据来了以后干什么。

可以把callback理解成：占个位置，下载器说：我下载完后会通知你，后续怎么处理我不管了。























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







# ROS2



## 安装Ubuntu24.04

安装好ubuntu系统后，还需要安装一些常用工具：

1.更新镜像源：

```shell
sudo apt update
sudo apt upgrade
```

2.安装软件开发基础工具包：

```shell
sudo apt install build-essential dkms linux-headers-$(uname -r)
```





## 安装ROS2 Jazzy

跟着官方文档教程，从System setup开始，依次执行，直到Setup environment后结束。https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html



**常见问题**：curl: (7) Failed to connect to github.com port 443，网络无法直接访问 GitHub

不需要从 GitHub 下载，直接使用清华源配置 ROS 2：

```shell
# 1. 添加 ROS 2 清华源的 GPG 密钥
sudo curl -sSL https://mirrors.tuna.tsinghua.edu.cn/rosdistro/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# 2. 添加 ROS 2 清华源（Ubuntu 24.04 Noble 对应 ROS 2 Jazzy）
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] https://mirrors.tuna.tsinghua.edu.cn/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# 3. 重新下载ros2开发工具
sudo apt update && sudo apt install ros-dev-tools
```





## 启动Jupyterlab

在学习`Raspbot`控制小车硬件的时候，可以配合`Jupyterlab`编写`Python`代码测试。



标准启动流程：

```shell
# 1. 进入存放虚拟环境的目录
cd ~/my_robot_env

# 2. 激活虚拟环境 (你会看到命令行开头多了个 (venv))
source venv/bin/activate

# 3. 启动 JupyterLab (允许远程访问)
jupyter lab --ip=0.0.0.0

# 4.打开电脑浏览器，输入下方地址
http://192.168.0.104:8888/lab
```





## 编写第一个节点



### Python版本

python源代码：

```python
# ros2_python_node.py
import rclpy    # ros2 client library
from rclpy.node import Node

def main():
    rclpy.init()
    node = Node("python_node") # create a node instance
    node.get_logger().info('hello python node')
    rclpy.spin(node)

    rclpy.shutdown()


if __name__ == "__main__":
    main()
```



运行程序：

```shell
python3 ros2_python_node.py
```





### C++版本



C++源代码：

```cpp
#include "rclcpp/rclcpp.hpp"

int main(int argc, char **argv)
{
    rclcpp::init(argc,argv);
    auto node = std::make_shared<rclcpp::Node>("cpp_node");
    RCLCPP_INFO(node->get_logger(),"hello cpp node");
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
    
}
```



CMakeLists.txt：

```shell
cmake_minimum_required(VERSION 3.25)
project(ros2_cpp)
add_executable(ros2_cpp_node ros2_cpp_node.cpp)

find_package(rclcpp REQUIRED)
target_include_directories(ros2_cpp_node PUBLIC ${rclcpp_INCLUDE_DIRS})
target_link_libraries(ros2_cpp_node ${rclcpp_LIBRARIES})
```



**查看节点信息**

```shell
ros2 node list				# 查看节点列表及信息
ros2 node info /cpp_node	# 对应cpp文件里创建的节点名称
```





## 创建功能包



### Python版本

打开集成终端，输入代码：

```shell
ros2 pkg create demo_python_pkg --build-type ament_python
```



在`demo_python_pkg`目录下新建`python_node.py`，输入如下代码：

```python
import rclpy
from rclpy.node import Node

def main():
    rclpy.init()
    node = Node("python_node")
    node.get_logger().info('hello python node!')
    rclpy.spin(node)
    rclpy.shutdown()
```

仔细看以上代码会发现只定义了main函数，但并没有调用。

运行main函数的方法：通过setup.py，添加`'python_node=demo_python_pkg.python_node:main'`，到`console_scripts`下，添加的代码及位置如下：

```python
entry_points={
        'console_scripts': [
            'python_node = demo_python_pkg.python_node:main', 
        ],
```

添加这句话的含义是：当执行python_node时就相当于执行`demo_python_pkg`目录下`python_node`文件中的`main`函数。

添加完成后打开`demo_python_pkg/package.xml`，添加依赖信息，代码如下：

```xml
<depend>rclpy</depend>
```



接下来，就可以在功能包的上层目录使用`colcon build`命令构建功能包了，这个命令可以构建当前及子目录下的所有功能包。

构建完成后，你会发现在功能包同级目录下会多出`build`， `install`和`log`三个文件夹。

**build/** 里面是构建过程中产生的中间文件。

**install/** 是放置构建结果的文件夹。

**log/** 里面是构建过程中的各种日志信息。



构建完成后如何运行？

```shell
ros2 run demo_python_pkg python_node
---
Package 'demo_python_pkg' not found
```

运行时会提示找不到包，因为ros2 run命令会通过`AMENT_PREFIX_PATH`环境变量的值来查找功能包，该值默认是ros2系统的安装目录，demo_python_pkg的安装目录是在install下，我们需要修改`AMENT_PREFIX_PATH`来帮助ros2找到该功能包。在install目录下有个`setup.bash`的脚本，直接运行该脚本就可以自动修改`AMENT_PREFIX_PATH`环境变量：

```shell
source install/setup.bash
# 再次运行
ros2 run demo_python_pkg python_node
```





### C++版本

创建包：

```shell
ros2 pkg create demo_cpp_pkg --build-type ament_cmake
```



在src目录下添加`node_cpp.cpp`文件：

```cpp
#include "rclcpp/rclcpp.hpp"

int main(int argc, char **argv)
{
    rclcpp::init(argc,argv);
    auto node = std::make_shared<rclcpp::Node>("cpp_node");
    RCLCPP_INFO(node->get_logger(),"hello cpp node");
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
    
}
```



编辑`CMakeLists.txt`文件,在`find_pakackage(ament_cmake REQUIRED)`后面添加：

```cmake
# 1.find rclcpp headers and libs
find_package(rclcpp REQUIRED)
# 2.add executable cpp_node
add_executable(cpp_node src/cpp_node.cpp)
# 3.add dependencies for cpp_node
ament_target_dependencies(cpp_node rclcpp)
# 4. copy cpp_node to install repo
install(TARGETS
cpp_node
DESTINATION lib/${PROJECT_NAME}
)
```



编辑`packages.xml`添加依赖声明：

```xml
<depend>rclcpp</depend>
```



运行该文件：

```shell
source install/setup.bash
ros2 run demo_cpp_pkg cpp_node
```





## 多功能包最佳实践-Workspace

进入chapt2目录，输入以下命令：

```shell
mkdir -p chapt2_ws/src
```

开发过程中，我们会将所有的功能包放到`src`目录下，并在`src`同级目录运行`colcon`进行构建，此时构建出来的`build，install，log`等目录则和`src`同级。



如果只想构建某个功能包，只需要使用`--packages-select`命令加上功能包名：

```shell
colcon build --packages-select demo_cpp_pkg
```



如果构建某个包依赖另一个包(比如python的包依赖`cpp`的包)，只需要在功能包的清单文件中声明依赖关系即可，打开`demo_python_pkg/package.xml`，添加依赖：

```xml
<depend>rclpy</depend>
<depend>demo_cpp_pkg</depend>
```







## 订阅与发布



### ros2常用相关命令

```shell
# 打开海龟模拟器
ros2 run turtlesim turtlesim_node
---
/turtlesim
  Subscribers:
    /parameter_events: rcl_interfaces/msg/ParameterEvent
    /turtle1/cmd_vel: geometry_msgs/msg/Twist
  Publishers:
    /parameter_events: rcl_interfaces/msg/ParameterEvent
    /rosout: rcl_interfaces/msg/Log
    /turtle1/color_sensor: turtlesim/msg/Color
    /turtle1/pose: turtlesim/msg/Pose


# 使用命令行查看节点信息
ros2 node info /turtlesim

# 输出海龟当前的位姿
ros2 topic echo /turtle1/pose

# 查看某个话题的具体信息
ros2 topic info /turtle1/cmd_vel _vel -v

# 查看消息接口的详细定义
ros2 interface show geometry_msgs/msg/Twist

# 使用命令行发布线速度
ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 1.0}}"

# 使用命令行发布角速度
ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{angular: {z: 1.0}}"
```



### **C++发布主题**

1.创建demo_cpp_topic功能包并添加依赖

```shell
# ros2 创建包-demo_cpp_topic 包类型-cpp 依赖-rclcpp(ros2核心),geometry_msgs(消息类型包),turtlesim(功能包-小乌龟模拟)
ros2 pkg create demo_cpp_topic --build-type ament_cmake --dependencies rclcpp geometry_msgs turtlesim
```



2.添加cpp代码：

```cpp
// src/demo_cpp_topic/src/turtle_circle.cpp

#include "rclcpp/rclcpp.hpp"
#include "geometry_msgs/msg/twist.hpp"
#include <chrono>

using namespace std::chrono_literals;

class TurtleCircle : public rclcpp::Node{
public:
    // 只有当构造函数只有 1 个参数时，建议写 explicit
    explicit TurtleCircle(const std::string &node_name) : Node(node_name){
        // 创建发布主题，geometry_msgs::msg::Twist - 话题的接口类型， 10 - 历史队列长度
        publisher_ = this->create_publisher<geometry_msgs::msg::Twist>("/turtle1/cmd_vel",10);
        // 初始化定时器
        timer_ = this->create_wall_timer(1000ms, std::bind(&TurtleCircle::timer_callback, this));
    }

private:
    void timer_callback(){
        auto msg = geometry_msgs::msg::Twist();		// 创建geometry_msgs::msg::Twist类型的消息对象
        msg.linear.x = 1.0;
        msg.angular.z = 0.5;
        publisher_->publish(msg);					// 发布主题
    }

private:
    rclcpp::TimerBase::SharedPtr timer_;                                // timer smart pointer
    rclcpp::Publisher<geometry_msgs::msg::Twist>::SharedPtr publisher_; // publisher smart pointer
};

int main(int argc, char **argv){
    rclcpp::init(argc,argv);
    auto node = std::make_shared<TurtleCircle>("turtle_square");
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```



3.配置cmake添加节点，添加依赖

在`ament_package()`前面添加：

```cmake
add_executable(turtle_circle src/turtle_circle.cpp)
ament_target_dependencies(turtle_circle rclcpp geometry_msgs)

install(TARGETS
        turtle_circle
        DESTINATION lib/${PROJECT_NAME}
)
```



4.构建与运行

```shell
# 在src目录上一层构建节点
colcon build

# 添加环境变量
source install/setup.bash

# 运行节点 ros2 run 包名 节点名
ros2 run demo_cpp_topic turtle_circle
```



 





### C++订阅主题



**订阅Pose实现闭环控制**  

通过发布速度控制命令到话题便可以控制海龟移动，

通过订阅实时位置主题可以获取海龟的实时位置。

实时速度和实时位置都有了，就可以闭环控制海龟移动到指定位置。

所谓闭环控制就是指通过对输出进行测量和反馈来调节系统的输入，使系统的输出更加接近期望值。



我们将通过不断检测海龟当前位置和目标位置之间的误差，来实时调整发布的指令，最终使海龟到达指定目标点。

```cpp
// src/demo_cpp_topic/src/turtle_control.cpp
#include "geometry_msgs/msg/twist.hpp"
#include "rclcpp/rclcpp.hpp"
#include "turtlesim/msg/pose.hpp"

class TurtleController : public rclcpp::Node{
public:
    TurtleController() : Node("turtle_controller"){
        velocity_publisher_ = this->create_publisher<geometry_msgs::msg::Twist>("/turtle1/cmd_vel",10);
        pose_subscription_ = this->create_subscription<turtlesim::msg::Pose>("/turtle1/pose",10,
            std::bind(&TurtleController::on_pose_received_, this, std::placeholders::_1));
    }

private: 
    void on_pose_received_(const turtlesim::msg::Pose::SharedPtr pose){
        auto message = geometry_msgs::msg::Twist();
        // 1. 获取海龟的位置
        double current_x = pose->x;
        double current_y = pose->y;
        RCLCPP_INFO(this->get_logger(), " current pos:(x=%f,y=%f)",current_x,current_y);

        // 2. 通过欧式距离公式求出当前位置和目标位置之间的距离和角度
        double distance = std::sqrt((target_x_ - current_x) * (target_x_ - current_x) + (target_y_ - current_y) * (target_y_ - current_y));
        double angle = std::atan2(target_y_ - current_y, target_x_ - current_x) - pose->theta;

        // 3. 控制策略：距离大于0.1继续运动，觉督查大于0.2则原地旋转，否则直行
        if(distance > 0.1){
            if(fabs(angle) > 0.2){
                message.angular.z = fabs(angle);
            }else{
                // 
                message.linear.x = k_ * distance;
            }
        }

        // 4. 限制最大速度并发布消息
        if(message.linear.x > max_speed_) message.linear.x = max_speed_;

        velocity_publisher_->publish(message);
    }

private:
    rclcpp::Subscription<turtlesim::msg::Pose>::SharedPtr pose_subscription_;
    rclcpp::Publisher<geometry_msgs::msg::Twist>::SharedPtr velocity_publisher_;
    double target_x_{1.0};
    double target_y_{1.0};
    double k_{1.0};
    double max_speed_{3.0};
};

int main(int argc, char **argv){
    rclcpp::init(argc,argv);
    auto node = std::make_shared<TurtleController>();
    rclcpp::spin(node);
    rclcpp::shutdown();
    return 0;
}
```



配置cmake

```cmake
add_executable(turtle_control src/turtle_control.cpp)
ament_target_dependencies(turtle_control rclcpp geometry_msgs turtlesim)

install(TARGETS
        turtle_control
        DESTINATION lib/${PROJECT_NAME}
)
```







### 自定义通信接口



**需求：**

1. 通过小公具可以查看系统的实时状态信息，包括记录信息的时间，主机名称，CPU使用率，内存使用率，内存总大小，剩余内存，网络接收数据量，网络发送数据量
2. 简单的界面，将信息展示
3. 能在局域网内其他主机上查看数据



**方案：**

1. 写一个节点，用来获取信息，并通过话题发布出来
2. 写一个显示节点，订阅这个话题并进行显示



**实现：**

第一步：创建接口功能包

```shell
ros2 pkg create status_interfaces --build-type ament_cmake --dependencies rosidl_default_generators builtin_interfaces
```

`builtin_interfaces`是ros2中已有的一个消息接口功能包

`rosidl_default_generators` 用于将自定义的消息文件转换为C++, Python源码的模块



ROS2中，话题消息定义文件需要放置到功能包的msg目录下，文件名必须大写字母开头。

接下来，在功能包下新建`msg/`目录，在该目录下创建文件`SystemStatus.msg`，在文件中编写以下内容：

```python
builtin_interfaces/Time stamp 	# 记录时间戳
string host_name 				# 系统名称
float32 cpu_percent				# CPU使用率
float32 memory_percent			# 内存使用率
float32 memory_total 			# 内存总量
float32 memory_available		# 剩余有效内存
float64 net_sent				# 网络发送数据总量
float64 net_recv				# 网络接收数据总量
```

定义好数据接口文件后，需要在`CMakeLists.txt`中对该文件进行注册，声明其为消息接口文件，并为其添加`builtin_interfaces`依赖，内容如下所示：

```cmake
rosidl_generate_interfaces(${PROJECT_NAME}
    "msg/SystemStatus.msg"
    DEPENDENCIES builtin_interfaces
)

ament_package()
```

在`package.xml`中声明该功能包是一个消息接口功能包，方便ROS2对其做额外处理：

```xml
<member_of_group>rosidl_interface_packages</member_of_group>

<buildtool_depend>ament_cmake</buildtool_depend>
```



完成后查看消息接口是否构建成功：

```shell
# 回到workspace目录
colcon build
source install/setup.bash
ros2 interface show status_interfaces/msg/SystemStatus
```



第二步：创建`status_publsiher`功能包

```shell
# 回到src目录
ros2 pkg create status_publisher --build-type ament_python --dependencies rclpy status_interfaces
```

编写python代码：

```python
# 在status_publisher/status_publisher目录下创建sys_status_pub.py
import rclpy 
from rclpy.node import Node
from status_interfaces.msg import SystemStatus
import psutil
import platform

class SystemStatusPub(Node):
    def __init__(self,node_name):
        super().__init__(node_name)
        self.status_publisher_ = self.create_publisher(SystemStatus, 'sys_status', 10)
        self.timer = self.create_timer(1, self.timer_callback)

    def timer_callback(self):
        cpu_percent = psutil.cpu_percent()
        memory_info = psutil.virtual_memory()
        net_io_counters = psutil.net_io_counters()

        msg = SystemStatus()
        msg.stamp = self.get_clock().now().to_msg()
        msg.host_name = platform.node()
        msg.cpu_percent = cpu_percent
        msg.memory_percent = memory_info.percent
        msg.memory_total = memory_info.total / 1024 / 1024
        msg.memory_available = memory_info.available / 1024 / 1024
        msg.net_sent = net_io_counters.bytes_sent / 1024 / 1024
        msg.net_recv = net_io_counters.bytes_recv / 1024 / 1024

        self.get_logger().info(f'publish:{str(msg)}')
        self.status_publisher_.publish(msg)


def main():
    rclpy.init()
    node = SystemStatusPub('sys_status_pub')
    rclpy.spin(node)
    rclpy.shutdown()
```

构建，运行，并查看话题数据：

```shell
colcon build
ros2 run status_publisher sys_status_pub
ros2 topic echo /sys_status
```





第三步，创建qt界面展示

```shell
ros2 pkg create status_display --build-type ament_cmake --dependencies rclcpp status_interfaces 
```

新建sys_status_display.cpp

```cpp
#include <QApplication>
#include <QLabel>
#include <QString>
#include "rclcpp/rclcpp.hpp"
#include "status_interfaces/msg/system_status.hpp"
using SystemStatus = status_interfaces::msg::SystemStatus;

class SysStatusDisplay : public rclcpp::Node{
public:
    SysStatusDisplay() : Node("sys_status_display"){
        subscription_ = this->create_subscription<SystemStatus>("sys_status", 10, [&](const SystemStatus::SharedPtr msg) -> void {
            label_->setText(get_qstr_from_msg(msg));
        });
    
    // create an empty SystemStatus object, 
    label_ = new QLabel(get_qstr_from_msg(std::make_shared<SystemStatus>()));
    label_->show();
    }

    QString get_qstr_from_msg(const SystemStatus::SharedPtr msg){
        std::stringstream show_str;
        show_str
            << "==========系统状态可视化工具==========\n"
            << "数据时间:\t" << msg->stamp.sec << "\ts\n"
            << "主机名称:\t" << msg->host_name << "\t\n"
            << "CPU使用率:\t" << msg->cpu_percent << "\t%\n"
            << "内存使用率:\t" << msg->memory_percent << "\t%\n"
            << "内存总大小:\t" << msg->memory_total << "\tMB\n"
            << "剩余有效内存:\t" << msg->memory_available << "\tMB\n"
            << "网络发送量:\t" << msg->net_sent << "\tMB\n"
            << "网络接收量:\t" << msg->net_recv << "\tMB\n"
            << "===================================";
        return QString::fromStdString(show_str.str());
    }

private:
    rclcpp::Subscription<SystemStatus>::SharedPtr subscription_;
    QLabel* label_;
};

int main(int argc, char **argv){
    rclcpp::init(argc,argv);
    QApplication app(argc,argv);
    auto node = std::make_shared<SysStatusDisplay>();
    std::thread spin_thread([&]()-> void{rclcpp::spin(node);});
    spin_thread.detach();
    app.exec();
    rclcpp::shutdown();
    return 0;
}
```



配置cmake

```cmake
...
find_package(Qt5 REQUIRED COMPONENTS Widgets)

add_executable(sys_status_display src/sys_status_display.cpp)
target_link_libraries(sys_status_display Qt5::Widgets)
ament_target_dependencies(sys_status_display rclcpp status_interfaces)

install(TARGETS sys_status_display
    DESTINATION lib/${PROJECT_NAME}
)
...
```



构建并运行

```shell
colcon build 
source install/setup.bash
ros2 run status_display sys_status_display
```





# 机器人系统岗技术栈

![](./assets/robotics_system_engineer_tech_stack.svg)



## 第一阶段：C++核心





### 第1天：STL容器实战

**目标：用熟vector/map/unordered_map，知道什么场景选哪个**



#### std::vector

```cpp
#include <iostream>
#include <vector>

int main() {
    // 创建和初始化
    std::vector<int> v1;
    std::vector<int> v2(5,0);
    std::vector<int> v3 = {1,2,3,4,5};

    // 添加元素
    v1.push_back(10);           // 尾部添加，可能触发扩容
    v2.emplace_back(20);          // 直接构造，比push_back高效

    // 预分配（重要！避免反复扩容）
    v1.reserve(100);            // 预留100个空间，size不变
    v1.resize(10);        // 改变size，新元素默认初始化

    // 访问
    std::cout << v1[0] << std::endl;        // 下标访问，不检查越界
    std::cout << v1.at(0) << std::endl;   // 检查越界，越界抛异常
    v1.front();                             // 第一个
    v1.back();                              // 最后一个

    // 大小
    std::cout << v1.size() << std::endl;        // 大小
    std::cout << v1.capacity() << std::endl;    // 容量
    std::cout << v1.empty() << std::endl;       // 检查为空

    // 删除
    v1.pop_back();                              // 删除最后一个
    v1.clear();                                 // 清空

    // 遍历
    for (const auto &i : v3) {
        std::cout << i << std::endl;
    }
    
    return 0;
}

```



**reserve vs resize的区别**

```cpp
std::vector<int> v;
v.reserve(10);	// capacity=10, size=10, 没有元素
v.resize(10);	// capacity=10, size=10, 有10个默认元素
```



#### map 和 unordered_map

```cpp
#include <iostream>
#include <map>
#include <unordered_map>

int main() {
    // map：有序，底层红黑树，查找O(logN)
    std::map<std::string, int> ordered;
    ordered["device_003"] = 1;
    ordered["device_002"] = 2;
    ordered["device_001"] = 3;
    // 遍历是按照key字母序的 001 002 003

    //unordered_map：无序，底层哈希表，查找O(1)
    std::unordered_map<std::string, int> unordered;
    unordered["device_003"] = 1;
    unordered["device_002"] = 2;
    unordered["device_001"] = 3;
    // 遍历顺序不确定

    // 两者操作API基本一致
    std::cout << unordered.count("device_001") << std::endl;    // 存在返回1，不存在返回0
    unordered.count("device_002");                              // 返回迭代器
    unordered.erase("device_003");                              // 删除

    // 安全访问
    auto it = unordered.find("device_002");
    if (it != unordered.end()) {
        std::cout << it->second << std::endl;
    }

    // 不要用[]访问不存在的key，会自动插入默认值
    std::cout << unordered["device_004"] << std::endl;  // ← 这会插入一个0，是bug
    
    return 0;
}
```





#### 迭代器

```cpp
// 三种遍历方法，都需要掌握
std::vector<int> v = {1,2,3,4,5};

// 方式1：范围for(最简洁)
for (const auto& i : v) {}

// 方式2：下标(需要用到index的时候)
for (size_t i = 0; i < v.size(); i++) {}

// 方式3：迭代器，需要删除元素的时候必须用这个(这是常见bug来源，记住这个写法)
for (auto it = v.begin(); it!=v.end(); ++it) {
    if (*it == 3) it = v.erase(it);   // erase返回下一个有效迭代器
    else ++it;
}
```





#### 小练习

```cpp
// 设备管理器练习
// 文件名：device_manager.cpp
// 编译：g++ -std=c++17 -Wall device_manager.cpp -o device_manager

#include <iostream>
#include <unordered_map>
#include <map>
#include <vector>
#include <string>
#include <chrono>

// 设备状态
enum class DeviceStatus {
    ONLINE,
    OFFLINE,
    ERROR
};

// 事件日志
struct LogEntry {
    std::string device_id;
    std::string message;
    DeviceStatus status;
};

// 要实现的功能：

// 1. 注册设备（device_id → status）
std::unordered_map<std::string, DeviceStatus> devices;

// 2. 更新设备状态
bool updateDeviceStatus(const std::string& device_id, DeviceStatus status) {
    auto it = devices.find(device_id);
    if (it == devices.end()) {
        std::cerr << "No device with id " << device_id << std::endl;
        return false;
    }

    // devices[device_id] = status;    // 又查一次，浪费
    it->second = status;
    return true;
}


// 3. 查询设备状态
//    返回bool，通过引用参数返回status
bool getDeviceStatus(const std::string& device_id, DeviceStatus& status) {
    auto it = devices.find(device_id);
    if (it == devices.end()) {
        std::cerr << "No device with id " << device_id << std::endl;
        return false;
    }

    status = it->second;
    return true;
}

// 4. 记录日志（timestamp → LogEntry）
//    用map存储（时间戳有序）
//    timestamp用 chrono::steady_clock::now().time_since_epoch().count()
std::map<long long, LogEntry> log;
void write_log(const std::string &device_id, const std::string &message, DeviceStatus status) {
    LogEntry entry;
    entry.device_id = device_id;
    entry.message = message;
    entry.status = status;
    long long timestamp = std::chrono::steady_clock::now().time_since_epoch().count();
    log.emplace(timestamp, entry);
}

// 5. 打印最近N条日志
//    map是有序的，从end()往前数N条
void print_logs(int count) {
    if (log.empty()) {
        std::cerr << "No log entries found" << std::endl;
        return;
    }
    auto it = log.end();
    while (count > 0) {
        --it;     // 先移动，再解引用，这样第一次拿到的就是end()前面一个迭代器，没有bug
        std::cout << it->first << ": " << (int)it->second.status << "\n";
        --count;
    }
}

// 6. 打印所有在线设备
//    遍历unordered_map，筛选ONLINE的
void print_online_devices() {
    for (auto it = devices.begin(); it != devices.end(); ++it) {
        if (it->second == DeviceStatus::ONLINE) {
            std::cout << "ONLINE:" << it->first << std::endl;
        }
    }
}

// main函数测试：
// 注册 device_001 device_002 device_003
// 更新 device_002 状态为 ERROR
// 查询 device_001 状态
// 打印最近2条日志
// 打印所有在线设备

int main() {
    // 注册设备
    devices["device_001"] = DeviceStatus::ONLINE;
    write_log("device_001","设备1",DeviceStatus::ONLINE);
    devices["device_002"] = DeviceStatus::ONLINE;
    write_log("device_002","设备2",DeviceStatus::ONLINE);
    devices["device_003"] = DeviceStatus::ONLINE;
    write_log("device_003","设备2",DeviceStatus::ONLINE);

    // 更新device_002状态
    devices["device_002"] = DeviceStatus::ERROR;

    // 查询device_001状态
    DeviceStatus status001;
    bool flag = getDeviceStatus("device_001", status001);
    std::cout << "device_001的状态为 : " << int(status001) << std::endl;

    print_logs(2);
    print_online_devices();

}
```











### 第2天：类的完整写法

**目标：能独立写一个工程级别的类**



#### **构造函数全家桶**

```cpp
#include <iostream>
#include <string>

class Device {
public:
    // 普通构造函数
    Device(const std::string &id, int port)
        :id_(id), port_(port)               // 初始化列表，比在函数体里赋值高效
    {
        std::cout << "Device构造: " << id << std::endl;
    }

    // 析构函数
    ~Device() {
        std::cout << "Device析构: " << id_ << std::endl;
        if (fd_ >= 0) {
            // close(fd_);  // 真实场景关闭文件描述符
        }
    }

    // 拷贝构造函数
    Device(const Device &other)
        :id_(other.id_), port_(other.port_)
    {
        std::cout << "Device拷贝构造: " << id_ << std::endl;
    }

    // 移动构造
    Device(Device&& other) noexcept
        :id_(std::move(other.id_)), port_(other.port_), fd_(other.fd_)
    {
        other.fd_ = -1; // 把原对象置空
    }

private:
    std::string id_;
    int port_;
    int fd_;
};
```



#### **const成员函数**

```cpp
class Device{
public:
    // const成员函数：承诺不修改成员变量
    // 只读操作都要加const
    std::string getId() const { return id_; }
    int getPort() const { return port_; }
    bool isConnected() const { return fd_ >= 0; }
    
    // 非const成员函数：会修改成员变量
    void setPort(int port){ port_ = port; }
    bool connect(){
        fd_ = 1;	// 模拟连接
        return true;
    }

private:
    std::string id_;
    int port_;
    int fd_ = -1;
};

// 为什么要加const：
// const Device d("001", 8080);
// d.getId();   // ✅ const函数可以被const对象调用
// d.setPort(9090);  // ❌ 编译错误，const对象不能调用非const函数
```



#### **static成员**

```cpp
class Device{
public:
    Device(const std::string& id)
        : id_(id)
    {
        count_++;	// 每创建一个设备，计数+1
    }
    
    ~Device(){
        count_--;	// 析构时计数-1
    }
    
    // static成员函数：不属于某个对象，属于类本身
    // 不能访问非static成员变量
    static int getCount(){ return count_; }
    
private:
    std::string id_;
    // static成员变量：所有对象共享同一份
    // 类内声明，类外定义
    static int count_;
};

// 使用
int main(){
    std::cout << Device::getCount() << "\n";  // 0
    Device d1("001");
    Device d2("002");
    std::cout << Device::getCount() << "\n";  // 2
}
```

`static`成员变量为什么要在类外定义?

类内是**声明**，类外是**定义**，定义才会分配内存。如果在类内定义，每个包含这个头文件的`.cpp`都会分配一份，链接时报重复定义错误。

所以类内只能**声明**，类外在**某一个cpp文件里定义一次**



#### 小练习

```cpp
// 文件名：device_manager2.cpp
// 编译：g++ -std=c++17 -Wall device_manager2.cpp -o device_manager2

#include <iostream>
#include <unordered_map>
#include <map>
#include <string>
#include <chrono>

enum class DeviceStatus { ONLINE, OFFLINE, ERROR };

struct LogEntry {
    std::string device_id;
    std::string message;
    DeviceStatus status;
};

class DeviceManager {
public:
    // 构造函数：初始化管理器名称
    DeviceManager(const std::string& manager_name)
        : name_(manager_name) {
        instance_count_++;
    }

    // 析构函数：打印还有多少设备没注销
    ~DeviceManager() {
        std::cout << devices_.size() << " 个设备未注销" << std::endl;
        instance_count_--;
    }
    // 禁止拷贝（设备管理器不应该被复制）
    DeviceManager(const DeviceManager &) = delete;

    // 1. 注册设备
    //    device_id已存在时返回false
    bool registerDevice(const std::string &device_id) {
        auto it = devices_.find(device_id);
        if (it != devices_.end()) {
            std::cout << "注册失败：设备已注册" << std::endl;
            return false;
        }
        devices_[device_id] = DeviceStatus::ONLINE;
        write_log(device_id, "设备注册", DeviceStatus::ONLINE);  // 加这行
        return true;
    }
    // 2. 注销设备
    //    device_id不存在时返回false
    bool unregisterDevice(const std::string &device_id) {
        auto it = devices_.find(device_id);
        if (it == devices_.end()) {
            std::cout << "注销失败：设备不存在" << std::endl;
            return false;
        }
        devices_.erase(it);
        return true;
    }

    // 3. 更新设备状态
    //    device_id不存在时返回false
    bool updateStatus(const std::string &device_id,DeviceStatus status) {
        auto it = devices_.find(device_id);
        if (it == devices_.end()) {
            std::cout << "更新失败，设备不存在" << std::endl;
            return false;
        }
        it->second = status;
        return true;
    }

    // 4. 查询设备状态
    //    返回bool，通过引用参数返回status
    bool getStatus(const std::string &device_id, DeviceStatus &status) {
        auto it = devices_.find(device_id);
        if (it == devices_.end()) {
            std::cout << "查询失败，设备不存在" << std::endl;
            return false;
        }
        status = it->second;
        return true;
    }



    // 6. 打印最近N条日志
    //    修复昨天的越界bug：count > log_.size()时只打印全部
    void printLogs(int count) {
        if (count > log_.size()) count = log_.size();
        auto it = log_.end();
        while (count) {
            --it;
            std::cout << it->first << ":" << (int)it->second.status << "\n";
            --count;
        }
    }

    // 7. 打印所有在线设备
    void printOnlineDevices() {
        for ( auto device : devices_) {
            if (device.second == DeviceStatus::ONLINE) {
                std::cout << device.first << ":" << (int)device.second << std::endl;
            }
        }
    }
    // 8. static函数：返回总共创建过多少个DeviceManager实例
    static int getInstanceCount() {
        return instance_count_;
    }

private:
    // 5. 记录日志（内部调用，private）
    void write_log(const std::string &device_id, const std::string &message, DeviceStatus status) {
        LogEntry entry;
        entry.device_id = device_id;
        entry.message = message;
        entry.status = status;
        long long timestamp = std::chrono::steady_clock::now().time_since_epoch().count();
        log_.emplace(timestamp, entry);
    }

    std::string name_;
    std::unordered_map<std::string, DeviceStatus> devices_;
    std::map<long long, LogEntry> log_;
    static int instance_count_;
};

int DeviceManager::instance_count_ = 0;

int main() {
    DeviceManager mgr("机器人设备管理器");

    mgr.registerDevice("lidar_01");
    mgr.registerDevice("camera_01");
    mgr.registerDevice("imu_01");

    mgr.updateStatus("camera_01", DeviceStatus::ERROR);
    mgr.updateStatus("imu_01", DeviceStatus::OFFLINE);

    DeviceStatus s;
    if (mgr.getStatus("lidar_01", s)) {
        std::cout << "lidar_01状态: " << int(s) << "\n";
    }

    mgr.printLogs(10);   // 故意传比日志条数多的值，测试边界
    mgr.printOnlineDevices();

    std::cout << "创建了" << DeviceManager::getInstanceCount()
              << "个管理器实例\n";
}
```









### 第3天：智能指针

**目标：彻底搞懂unique_ptr/shared_ptr，知道什么时候用哪个**



**为什么需要智能指针?**

```cpp
// 裸指针的问题
void bad_example() {
    Device* d = new Device("lidar_01");
    
    if (some_error) {
        return;  // ← 忘记delete，内存泄漏
    }
    
    delete d;  // 正常路径才会释放
}

// 智能指针：离开作用域自动释放，不用手动delete
void good_example() {
    auto d = std::make_unique<Device>("lidar_01");
    
    if (some_error) {
        return;  // ← 自动析构，没有泄漏
    }
}  // ← 自动析构
```





#### unique_ptr

**所有权：**在 C++ 里，所有权（Ownership）指的是：谁负责在最后调用 `delete` 来销毁对象、释放内存

**`std::unique_ptr`（独占所有权）：** 它是唯一的领主。它死死盯着这个对象，当它自己生命周期结束（比如出作用域）时，它会自动调用 `delete`。



```cpp
#include <memory>
#include <string>
#include <iostream>

class Device {
public:
    Device(const std::string& device_id)
        :device_id_(device_id){}

    auto getId() const { return device_id_; }
private:
    std::string device_id_;
};

// 工厂函数：返回unique_ptr
std::unique_ptr<Device> createDevice(const std::string& device_id) {
    return std::make_unique<Device>(device_id);
}

int main() {
    // 创建：永远用make_unique，不要用new
    auto d1 = std::make_unique<Device>("lidar001");

    // 不能拷贝，只能移动
    //auto d2 = d1;   // ❌ 编译错误
    auto d2 = std::move(d1);   // ✅ 所有权转移，d1变成nullptr
    // 判断是否有效
    if (d1) { std::cout << "d1" << std::endl; }                // d1已经是nullptr，条件为false
    if (d2) { std::cout << "d2" << std::endl; }                  // d2有效，条件为true

    // 访问
    d2->getId();    // 和裸指针一样用->
    (*d2).getId();  // 或者解引用

    // 获取裸指针（只用于需要传给C接口的场景）
    Device* raw = d2.get();    // 不转移所有权
    
    // 释放所有权（变成裸指针，自己管理，一般不用）
	Device* raw = d2.release();

    // 提前释放
    d2.reset();                // d2变nullptr，Device被析构
    d2.reset(new Device("x")); // 替换为新对象

    auto d = createDevice("imu_01");  // 所有权从函数转移出来
}
```



#### shared_ptr

**`std::shared_ptr`（共享所有权）：** 几个人共同拥有。内部有一个计数器，最后离开的那个人（计数器归零时）负责调用 `delete`。



```cpp
#include <memory>
#include <iostream>
#include <string>

class Device {
public:
    Device(const std::string& device_id)
        :device_id_(device_id){}

    auto getId() const { return device_id_; }
private:
    std::string device_id_;
};

int main() {
    // 创建
    auto d1 = std::make_shared<Device>("lidar001");

    // 可以拷贝，引用计数+1
    auto d2 = d1;   // d1和d2指向同一个Device，引用计数=2
    auto d3 = d1;   // 引用计数=3

    // 查看引用计数（调试用）
    std::cout << d1.use_count() << std::endl;   // 3

    // 离开作用域引用计数-1，降到0时才析构
    {
        auto d4 = d1;   // 引用计数=4
    }                                    // d4析构，引用计数=3，Device还活着

    d2.reset();         // 引用计数=2
    d3.reset();         // 引用计数=1
    d1.reset();         // 引用计数=0，Device被析构

}
```





#### weak_ptr

`std::weak_ptr` 永远不能单独存在，它必须依附于 `std::shared_ptr`。

如果说 `std::unique_ptr` 是**独占地主**，`std::shared_ptr` 是**合伙股东**，那么 `std::weak_ptr` 的身份最特殊：它是一个“旁观者”，对对象拥有【零所有权】。



**1.什么是“零所有权”？**

当你把一个 `shared_ptr` 赋值给一个 `weak_ptr` 时：

- **不抢占领地：** 对象的**引用计数（Reference Count）不会加 1**。
- **不决定生死：** 就算外面所有的 `weak_ptr` 都还指着这个对象，只要最后一个 `shared_ptr` 挂了，对象就会被**立刻销毁、释放内存**。
- **不能直接使用：** 因为它没有所有权，它没办法直接去调用对象的方法（比如 `wp->show()` 是编译不通过的）。



**2.经典致命场景：循环引用（为什么需要它？）**

假设你正在写一个游戏，里面有“老板”和“员工”两个类。老板手里有员工的指针，员工心里也记着老板的指针。

如果都用 `shared_ptr`：

```cpp
struct Employee;

struct Boss {
    std::shared_ptr<Employee> worker; // 老板拥有员工
};

struct Employee {
    std::shared_ptr<Boss> my_boss;    // 员工也拥有老板
};
```

当你在程序里创建了他们：

```cpp
{
    auto boss = std::make_shared<Boss>();
    auto worker = std::make_shared<Employee>();
    
    boss->worker = worker;
    worker->my_boss = boss;
} // 离开作用域了！按理说该释放内存了
```

**💥 灾难发生：**

离开作用域时，`boss` 准备自杀，但发现 `worker` 还在引用它（计数为1），所以 `boss` 无法销毁；而 `worker` 想要销毁，又发现 `boss` 还在引用它（计数为1）。 

结果：**两个人都死不掉，内存永远留在堆里，发生内存泄漏！**



**🛠️ 用 `weak_ptr` 破局**

```cpp
struct Employee {
    std::weak_ptr<Boss> my_boss; // 只是静静地看着老板，不增加他的引用计数
};
```



**3.没有所有权，它怎么安全地使用对象？**

既然 `weak_ptr` 连调用对象方法的权力都没有，那它拿来干嘛？

它的最大作用叫“安全观测”。它在用之前，必须先探口气：“喂，你还活着吗？”

因为对象随时可能被真正的拥有者（`shared_ptr`）给消灭掉，`weak_ptr` 必须先调用 **`.lock()`** 方法。这个方法会做一件升级的事情：

- 如果对象**还活着**，`.lock()` 会临时返回一个强大的 `std::shared_ptr`，让计数临时 +1，保证你在使用的这几行代码里，对象绝对不会被别人删掉。
- 如果对象**已经死了**，`.lock()` 会返回一个空指针（`nullptr`）。

```cpp
std::weak_ptr<Device> wp = d2; // d2 是一个 shared_ptr

// ... 过了一段时间，d2 可能在别的地方被释放了 ...

// 准备使用 wp：
if (std::shared_ptr<Device> temp_sp = wp.lock()) {
    // 成功“借尸还魂”！此时 temp_sp 是一个强指针，对象安全了
    temp_sp->working(); 
} else {
    // 对象已经死了，wp 成功感知到了，不会踩雷（避免了野指针崩溃）
    std::cout << "设备已经被销毁了，无法操作！" << std::endl;
}
```





#### 小练习

在昨天的`DeviceManager`基础上改造：

```cpp
// 文件名：device_manager3.cpp
// 编译：g++ -std=c++17 -Wall device_manager3.cpp -o device_manager3

#include <iostream>
#include <unordered_map>
#include <map>
#include <memory>
#include <string>
#include <chrono>

enum class DeviceStatus { ONLINE, OFFLINE, ERROR };

// 把Device抽出来做一个真正的类
class Device {
public:
    Device(const std::string& id, int port)
        : id_(id), port_(port)
    {
        std::cout << "Device创建: " << id_ << "\n";
    }

    ~Device() {
        std::cout << "Device销毁: " << id_ << "\n";
    }

    // 禁止拷贝
    Device(const Device&) = delete;
    Device& operator=(const Device&) = delete;

    // 只读访问加const
    const std::string& getId() const { return id_; }
    int getPort() const { return port_; }
    DeviceStatus getStatus() const { return status_; }
    void setStatus(DeviceStatus s) { status_ = s; }

private:
    std::string id_;
    int port_;
    DeviceStatus status_ = DeviceStatus::ONLINE;
};

class DeviceManager {
public:
    DeviceManager(const std::string& name) : name_(name) {}
    ~DeviceManager() {
        std::cout << name_ << " 析构，剩余设备: " << devices_.size() << "\n";
    }
    DeviceManager(const DeviceManager&) = delete;

    // 1. 注册设备
    //    内部用make_unique创建Device
    //    存入devices_（unique_ptr不能拷贝，用move）
    //    设备已存在返回false
    bool registerDevice(const std::string& id, int port) {
        auto it = devices_.find(id);
        if (it != devices_.end()) {
            std::cout << "设备: " << id << "已存在，注册失败" << std::endl;
            return false;
        }

        auto d1 = std::make_unique<Device>(id,port);
        devices_[id] = std::move(d1);
        return true;
    }

    // 2. 注销设备（unique_ptr从map移除，自动析构Device）
    bool unregisterDevice(const std::string& id) {
        auto it = devices_.find(id);
        if (it == devices_.end()) {
            std::cout << "设备:" << id << "不存在，注销失败" << std::endl;
            return false;
        }
        devices_.erase(it); // // 连key一起删，unique_ptr自动析构Device
        return true;
    }

    // 3. 更新状态
    bool updateStatus(const std::string& id, DeviceStatus status) {
        auto it = devices_.find(id);
        if (it == devices_.end()) {
            std::cout << "设备: "<< id << "不存在，更新失败" << std::endl;
            return false;
        }
        it->second->setStatus(status);
        return true;
    }

    // 4. 获取设备的观察指针（不转移所有权）
    //    返回Device*（裸指针），调用方不拥有这个对象
    //    设备不存在返回nullptr
    Device* getDevice(const std::string& id) {
        auto it = devices_.find(id);
        if (it == devices_.end()) { return nullptr; }
        return it->second.get();
    }

    // 5. 打印所有设备信息
    void printAll() const {
        for (auto it = devices_.begin(); it != devices_.end(); ++it) {
            std::cout << it->first << ":" << (int)it->second->getStatus() <<std::endl;
        }
    }

private:
    std::string name_;
    // unique_ptr管理Device的生命周期
    std::unordered_map<std::string, std::unique_ptr<Device>> devices_;
};

int main() {
    DeviceManager mgr("主控系统");

    mgr.registerDevice("lidar_01", 1);
    mgr.registerDevice("camera_01", 2);
    mgr.registerDevice("imu_01", 3);
    mgr.registerDevice("lidar_01", 4);  // 重复注册，应该失败

    mgr.updateStatus("camera_01", DeviceStatus::ERROR);

    // 获取设备观察指针
    Device* d = mgr.getDevice("lidar_01");
    if (d) {
        std::cout << "找到设备: " << d->getId()
                  << " 状态: " << int(d->getStatus()) << "\n";
    }

    mgr.unregisterDevice("imu_01");  // 应该打印"Device销毁: imu_01"
    mgr.printAll();

}  // mgr析构，剩余Device自动销毁
```







### 第4天：移动语义

**目标：看懂移动构造，知道为什么要用**



#### **1.左值和右值**

```cpp
// 左值：有名字，有地址，可以取地址
int x = 10;       // x是左值
Device d("001");  // d是左值

// 右值：临时的，没有名字，不能取地址
int y = x + 1;           // x+1是右值，计算完就消失
Device d2 = Device("002"); // Device("002")是右值，临时对象
createDevice("003")        // 函数返回值是右值

// 简单判断：能不能对它取地址
&x;           // ✅ 左值
&(x + 1);     // ❌ 右值
```



#### 2.拷贝的代价

```cpp
// 假设Buffer内部有个很大的vector
#include <iostream>
#include <vector>
#include <cstdint>
#include <chrono>

class Buffer {
public:
    Buffer(size_t size) : data_(size,0){}

    // 拷贝构造，把data_完整复制一份，很慢
    Buffer(const Buffer& other) : data_(other.data_) {
        std::cout << "拷贝构造，复制了" << data_.size() << "个字节\n";
    }

private:
    std::vector<uint8_t> data_;
};

int main() {
    Buffer b1(1024 * 1024);     // 1MB buffer
    auto t0 = std::chrono::high_resolution_clock::now();
    Buffer b2 = b1;              // 拷贝构造，复制1MB，慢
    auto t1 = std::chrono::high_resolution_clock::now();
    auto us = std::chrono::duration_cast<std::chrono::microseconds>(t1 - t0).count();
    std::cout << "耗时: " << us << " μs\n";
}
```



#### 3.移动构造

```cpp
#include <iostream>
#include <vector>
#include <cstdint>
#include <chrono>
#include <thread>

class Buffer {
public:
    Buffer(size_t size) : data_(size,0){}

    // 拷贝构造：深拷贝，复制数据
    Buffer(const Buffer& other) : data_(other.data_) {
        std::cout << "拷贝构造，复制了" << data_.size() << "个字节\n";
    }

    // 移动构造：把other的资源偷过来，other变成空的
    // noexcept很重要，告诉编译器这个操作不会抛异常
    // vector等容器在扩容时会优先用移动构造（前提是noexcept）
    Buffer(Buffer&& other) noexcept : data_(std::move(other.data_)) {
        std::cout << "移动构造: 偷了" << data_.size() << "字节\n";
        // other.data_现在是空的，不需要手动置空
    }

    // 移动赋值运算符
    Buffer& operator=(Buffer&& other) noexcept {
        if (this != &other) {   // 防止自赋值
            data_ = std::move(other.data_);
        }
        return *this;
    }

private:
    std::vector<uint8_t> data_;
};

int main() {
    Buffer b1(1024 * 1024 * 1024);     // 1GB buffer

    // 拷贝构造性能测试
    auto t0 = std::chrono::high_resolution_clock::now();
    Buffer b2 = b1;             // 拷贝构造
    auto t1 = std::chrono::high_resolution_clock::now();
    auto us_copy = std::chrono::duration_cast<std::chrono::microseconds>(t1 - t0).count();
    std::cout << "拷贝构造耗时: " << us_copy << " μs\n";

    // 移动构造性能测试
    auto t2 = std::chrono::high_resolution_clock::now();
    Buffer b3 = std::move(b1);  // 移动构造，偷走b1的数据，b1变空
    auto t3 = std::chrono::high_resolution_clock::now();
    auto us_move = std::chrono::duration_cast<std::chrono::microseconds>(t3 - t2).count();
    std::cout << "移动构造耗时: " << us_move << " μs\n";
    
}
```





#### 4.std::move是什么

```cpp
// std::move不移动任何东西
// 它只是把左值强制转换成右值引用，告诉编译器"可以偷这个对象的资源"
// 真正的移动发生在移动构造/移动赋值里

Buffer b1(1024);
Buffer b2 = std::move(b1);  // std::move(b1)把b1变成右值
                             // 触发移动构造，资源转移

// move之后b1处于"有效但未指定"状态
// 不能再用b1，但可以重新赋值
b1 = Buffer(512);  // 重新赋值，b1又有效了
```



**什么时候该用std::move：**

```cpp
// 1. 把局部变量转移给unique_ptr容器（你昨天已经用过）
auto d = std::make_unique<Device>("001");
devices_[id] = std::move(d);  // d转移后变nullptr

// 2. 函数返回局部对象（其实不需要，编译器自动优化，加了反而可能更慢）
Buffer createBuffer() {
    Buffer b(1024);
    return b;        // ✅ 直接返回，编译器会做RVO优化
    return std::move(b);  // ❌ 反而阻止了RVO
}

// 3. 转移不再需要的对象
std::vector<Buffer> buffers;
Buffer b(1024);
buffers.push_back(std::move(b));  // b不再需要，move进vector
```



#### 小练习

```cpp
// 文件名：move_semantics.cpp
// 编译：g++ -std=c++17 -Wall move_semantics.cpp -o move_semantics

#include <iostream>
#include <vector>
#include <string>
#include <cstring>
#include <cstdint>

// 练习1：给这个类加上移动构造和移动赋值
// 这个类管理一块原始内存（不用vector，手动管理）
class RawBuffer {
public:
    RawBuffer(size_t size)
        : size_(size), data_(new uint8_t[size])
    {
        std::memset(data_, 0, size_);
        std::cout << "构造: " << size_ << "字节\n";
    }

    // 拷贝构造（已实现）
    RawBuffer(const RawBuffer& other)
        : size_(other.size_), data_(new uint8_t[other.size_])
    {
        std::memcpy(data_, other.data_, size_);
        std::cout << "拷贝构造: " << size_ << "字节\n";
    }

    ~RawBuffer() {
        delete[] data_;
        std::cout << "析构: " << size_ << "字节\n";
    }

    // 你来实现：
    // 移动构造：把other的data_指针偷过来
    //           other的data_置nullptr，size_置0
    //           （否则other析构时会delete已经被偷走的内存，崩溃）
    RawBuffer(RawBuffer&& other) noexcept : size_(other.size_), data_(other.data_) {
        other.data_ = nullptr;
        other.size_ = 0;
        std::cout << "移动构造: " << size_ << "字节\n";
    }

    // 移动赋值：先释放自己的内存，再偷other的
    //           注意防止自赋值
    RawBuffer& operator=(RawBuffer&& other) noexcept {
        if (this != &other) {
            delete[] data_;
            this->data_ = other.data_;
            this->size_ = other.size_;
            other.data_ = nullptr;
            other.size_ = 0;
        }
        return *this;
    }

    size_t size() const { return size_; }
    uint8_t* data() { return data_; }

private:
    size_t size_;
    uint8_t* data_;
};


// 练习2：实现这个函数
// 把src的内容移动到dst，src变成空buffer(size=0)
// 不能拷贝，只能移动
void transferBuffer(RawBuffer& dst, RawBuffer& src) {
    dst = std::move(src);
}

int main() {
    // 测试移动构造
    RawBuffer b1(1024);
    RawBuffer b2 = std::move(b1);  // 移动构造
    std::cout << "b1 size: " << b1.size() << "\n";  // 应该是0
    std::cout << "b2 size: " << b2.size() << "\n";  // 应该是1024

    // 测试移动赋值
    RawBuffer b3(512);
    b3 = std::move(b2);  // 移动赋值
    std::cout << "b2 size: " << b2.size() << "\n";  // 应该是0
    std::cout << "b3 size: " << b3.size() << "\n";  // 应该是1024

    // 测试transferBuffer
    RawBuffer src(2048);
    RawBuffer dst(1);
    transferBuffer(dst, src);
    std::cout << "src size: " << src.size() << "\n";  // 应该是0
    std::cout << "dst size: " << dst.size() << "\n";  // 应该是2048

    // 测试vector存RawBuffer（会触发移动构造）
    std::vector<RawBuffer> buffers;
    buffers.reserve(3);  // 先reserve，避免扩容时反复移动
    buffers.emplace_back(256);
    buffers.emplace_back(512);
    buffers.emplace_back(1024);
    std::cout << "buffer数量: " << buffers.size() << "\n";
}
```









### 第5天：RAII + 异常安全

**目标：理解RAII，这是C++最重要的思想**



RAII = Resource Acquisition Is Initialization 资源获取即初始化，说人话就是：

```cpp
// 没有RAII的世界
void bad() {
    int fd = open("file.txt", O_RDONLY);
    
    if (error1) {
        close(fd);  // 每个退出路径都要手动释放
        return;
    }
    
    if (error2) {
        close(fd);  // 忘了一个就泄漏
        return;
    }
    
    close(fd);  // 正常路径
}

// RAII的世界
void good() {
    FileGuard f("file.txt");  // 构造时获取资源
    
    if (error1) return;  // 自动析构，自动释放
    if (error2) return;  // 自动析构，自动释放
    
}  // 自动析构，自动释放
```

**核心思想：把资源的生命周期绑定到对象的生命周期。**



#### **std::lock_guard**

```cpp
#include <mutex>
std::mutex mtx;

// 没有RAII的锁
void bad_lock(){
    mtx.lock();
    
    if(error){
        mtx.unlock();	// 忘了就死锁
    }
    
    mtx.unlock();
}

// lock_guard：RAII锁
void good_lock(){
    std::lock_guard<std::mutex> lock(mtx);	// 构造时lock
    
    if(error) return; // 析构时自动unlock
}	// 析构时自动unlock
```



#### **std::unique_lock**

```cpp
// lock_guard：简单，不能手动解锁
// unique_lock：灵活，可以手动控制

std::mutex mtx;

void flexible_lock(){
    std::unique_lock<std::mutex> lock(mtx);	// 构造时lock
    
    // 做一些需要锁的操作
    lock.unlock();   // 可以提前解锁
    
    // 做一些不需要锁的耗时操作
    lock.lock();     // 再次加锁
}	// 析构时自动unlock（如果还持有锁）
```



#### **异常安全**

```cpp
// 异常安全的三个级别：

// 1. 基本保证：抛异常后对象还处于有效状态
// 2. 强保证：抛异常后状态完全回滚（要么成功要么不变）
// 3. 不抛异常：noexcept，移动构造应该是这个级别

// 实际工程里追求基本保证就够了
// 关键：有RAII就自动有基本保证

class DeviceManager{
public:
    bool registerDevice(const std::string& id){
        auto device = std::make_unique<Device>(id);		// unique_ptr在栈上
        // device是栈上的unique_ptr，自动析构。没有内存泄漏，这就是基本保证
        
        // 假设这里抛异常
        // 异常导致直接跳出函数
        // 栈上的device（unique_ptr）自动析构
		devices_[id] = std::move(device);	// 比如map内存不足抛异常
        return true;
    }
}
```



**`mutable`关键字：**

```cpp
// const成员函数不能修改成员变量
// 但mutex需要在const函数里lock
// mutable告诉编译器：这个变量即使在const函数里也可以修改
mutable std::mutex mtx_;

int get() const {
    std::lock_guard<std::mutex> lock(mtx_);  // const函数里lock
    return count_;
}
```



#### 小练习

```cpp
// 文件名：raii_practice.cpp
// 编译：g++ -std=c++17 -Wall raii_practice.cpp -o raii_practice

#include <iostream>
#include <mutex>
#include <thread>
#include <vector>
#include <stdexcept>
#include <chrono>

// 练习1：实现一个ScopedTimer
// 构造时记录开始时间
// 析构时自动打印耗时和标签
// 用法：
// {
//     ScopedTimer t("数据库查询");
//     // 做一些操作
// }  // 自动打印："数据库查询 耗时: XXX ms"
class ScopedTimer {
public:
    ScopedTimer(const std::string& name)
        : name_(name) {
         start_ = std::chrono::high_resolution_clock::now();
    }

    ~ScopedTimer() {
        auto end = std::chrono::high_resolution_clock::now();
        auto duration = std::chrono::duration_cast<std::chrono::milliseconds>(end - start_);
        std::cout << name_ << ": " << duration.count() << " ms\n";
    }

private:
    std::string name_;
    std::chrono::time_point<std::chrono::high_resolution_clock> start_;
};

// 练习2：实现一个ScopedLock（不要用std::lock_guard，自己写一个）
// 构造时lock，析构时unlock
// 禁止拷贝
class ScopedLock {
public:
    // 构造函数：传入mutex引用，然后lock它
    ScopedLock(std::mutex& mtx) : mtx_(mtx) {
        mtx_.lock();
    }

    // 析构函数：unlock
    ~ScopedLock() {
        mtx_.unlock();
    }

    // 禁止拷贝
    ScopedLock(const ScopedLock&) = delete;
    ScopedLock& operator=(const ScopedLock&) = delete;

private:
    std::mutex& mtx_;  // 注意是引用，不是值
};

// 练习3：实现一个线程安全的计数器
// 用ScopedLock保护
class SafeCounter {
public:
    void increment() {
        // 用ScopedLock加锁
        ScopedLock lock(mtx_);	// 你可以试着把ScopedLock去掉,能直观感受到数据竞争
        count_++;
    }

    void decrement() {
        // 用ScopedLock加锁
        ScopedLock lock(mtx_);
        count_--;
    }

    int get() const {
        // 用ScopedLock加锁
        ScopedLock lock(mtx_);
        return count_;
    }

private:
    mutable std::mutex mtx_;  // mutable：const函数里也能lock
    int count_ = 0;
};

int main() {
    // 测试ScopedTimer
    {
        ScopedTimer t("测试计时");
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
    }  // 应该打印：测试计时 耗时: 100 ms左右

    // 测试SafeCounter线程安全
    SafeCounter counter;
    std::vector<std::thread> threads;

    // 10个线程各increment 100000次
    for (int i = 0; i < 10; i++) {
        threads.emplace_back([&counter]() {
            for (int j = 0; j < 100000; j++) {
                counter.increment();
            }
        });
    }

    for (auto& t : threads) t.join();

    // 如果线程安全，结果应该是1000000
    std::cout << "最终计数: " << counter.get() << "\n";
    // 不安全的话结果会小于1000000（数据竞争导致increment丢失）
}
```







### 第6天：多线程基础

**目标：能写线程安全的代码**





#### **std::thread基础**

```cpp
#include <thread>

// 创建线程的几种方式
void task() {
    std::cout << "线程执行\n";
}

// 方式1：函数指针
std::thread t1(task);

// 方式2：lambda(最常用)
std::thread t2([]{
    std::cout << "lambda线程\n";
});

// lambda带参数
std::thread t3([](int id, std::string name){
    std::cout << "线程" << id << ": " << name << "\n";
},1,"sensor");

// join vs detach
t1.join();		// 等待线程结束，主线程阻塞
t2.detach();  	// 线程独立运行，主线程不等待

// 注意：thread对象析构前必须join或detach
// 否则程序崩溃
```



#### 数据竞争

```cpp
int count = 0;

// count++不是原子操作，实际是三步：
// 1. 读count到寄存器
// 2. 寄存器+1
// 3. 写回count

// 两个线程同时执行：
// 线程A读count=5
// 线程B读count=5
// 线程A写count=6
// 线程B写count=6  ← 丢了一次increment
```



#### mutex用法

mutex锁的是"代码段"

谁拿到锁，谁才能执行锁里面的代码

```cpp
#include <mutex>

std::mutex mtx;
int count = 0;

void increment() {
    std::lock_guard<std::mutex> lock(mtx);  // 加锁
    count++;
}  // 自动解锁
```



**mutex的几个注意点：**



1. 不能递归加锁(死锁)

```cpp
void bad() {
    std::lock_guard<std::mutex> lock(mtx);
    // 如果这里调用了另一个也lock同一个mtx的函数
    // 死锁
}
```



2. 锁的粒度要小

```cpp
void good(){
    // 准备数据
    auto data = prepareData();
    
    {
        std::lock_guard<std::mutex> lock(mtx);
        count++;	// 只锁真正需要保护的部分
    }
    
    // 后续处理（不需要锁）
    process(data);
}
```



3. 加锁顺序要一致（多个mutex时）

```cpp
std::mutex mtx1, mtx2;

void thread_a() {
    std::lock_guard<std::mutex> l1(mtx1);  // 先锁1
    std::lock_guard<std::mutex> l2(mtx2);  // 再锁2
}

void thread_b() {
    std::lock_guard<std::mutex> l1(mtx1);  // 也是先锁1
    std::lock_guard<std::mutex> l2(mtx2);  // 再锁2
    // 顺序一致，不会死锁
}
```



#### 线程间数据传递

```cpp
// 方式1：共享变量+mutex（你已经会了）

// 方式2：lambda捕获
int result = 0;
std::thread t([&result]{
   result = 42; 	// 通过引用写结果
});
t.join();

// 方式3：std::future（异步获取返回值）
#include <future>

auto fut = std::async(std::launch::async, []{
    return 42;	// 线程返回值
});

int val = fut.get();  // 阻塞等待结果
std::cout << val << "\n";  // 42
```



#### 小练习

```cpp
// 文件名：thread_practice.cpp
// 编译：g++ -std=c++17 -Wall -pthread thread_practice.cpp -o thread_practice

#include <iostream>
#include <thread>
#include <mutex>
#include <vector>
#include <queue>
#include <string>
#include <chrono>

// 练习：实现线程安全的消息队列
// 这是ROS2节点内部通信的基础模型

struct Message {
    int id;
    std::string data;
};

class MessageQueue {
public:
    // 1. push：往队列里放消息
    //    加锁保护queue_
    void push(const Message& msg) {
        std::lock_guard<std::mutex> lock(mtx_);
        queue_.push(msg);
    }

    // 2. pop：取出一条消息
    //    队列为空时返回false
    //    取到消息通过引用参数返回，返回true
    bool pop(Message& msg) {
        std::lock_guard<std::mutex> lock(mtx_);
        if (queue_.empty())  return false;
        msg = queue_.front();
        queue_.pop();
        return true;
    }

    // 3. size：返回队列长度
    size_t size() const {
        std::lock_guard<std::mutex> lock(mtx_);
        return queue_.size();
    }

    // 4. empty：是否为空
    bool empty() const {
        std::lock_guard<std::mutex> lock(mtx_);
        return queue_.empty();
    }

private:
    std::queue<Message> queue_;
    mutable std::mutex mtx_;
};

int main() {
    MessageQueue mq;

    // 生产者线程：往队列里放100条消息
    std::thread producer([&mq]{
        for (int i = 0; i < 100; i++) {
            mq.push({i, "msg_" + std::to_string(i)});
            std::this_thread::sleep_for(std::chrono::milliseconds(1));
        }
        std::cout << "生产者完成\n";
    });

    // 消费者线程：不断取消息处理
    std::thread consumer([&mq]{
        int count = 0;
        while (count < 100) {
            Message msg;
            if (mq.pop(msg)) {
                count++;
                // 每10条打印一次
                if (count % 10 == 0) {
                    std::cout << "已消费: " << count
                              << " 条，最新: " << msg.data << "\n";
                }
            }
        }
        std::cout << "消费者完成\n";
    });

    producer.join();
    consumer.join();

    std::cout << "队列剩余: " << mq.size() << "\n";
}
```

有个缺陷：**消费者在队列为空时一直在空转**，疯狂调用`pop`返回false，浪费CPU。

这就是明天要解决的问题，用条件变量让消费者在队列为空时挂起，有消息来了再唤醒。



































































### 第7天：条件变量 + 线程通信

**目标：能用条件变量做线程同步**



#### 为什么需要条件变量

昨天的消费者有个问题：

```cpp
// 昨天的写法：忙等待
while (count < 100) {
    Message msg;
    if (mq.pop(msg)) {  // 队列空时一直返回false
        count++;
    }
    // 队列为空时CPU空转，浪费资源
}
```

真实机器人系统里，传感器数据不是连续的，消费者大部分时间在等待，空转会把CPU跑满，其他线程就没资源了。



#### 条件变量基础

```cpp
#include <condition_variable>

std::mutex mtx;
std::condition_variable cv;
bool ready = false;

// 等待方
void waiter(){
    std::unique_lock<std::mutex> lock(mtx);		// 必须用unique_lock
    cv.wait(lock, []{ return ready; });			// 等待条件成立
    
    // 条件成立后继续执行
    std::cout << "收到通知\n";
}

// 通知方
void notifier(){
    {
        std::lock_guard<std::mutex> lock(mtx);
        ready = true;
    }
    cv.notify_one();	// 唤醒一个等待线程
    // cv.notify_all() 唤醒所有等待线程
}
```



**wait内部发生了什么：**

```cpp
cv.wait(lock, []{ return ready; });

// 等价于：
while (!ready) {
    // 1. 原子性地释放lock，挂起线程
    // 2. 等待notify
    // 3. 被唤醒后重新获取lock
    // 4. 检查条件，不满足继续等
}
// 条件满足，带着lock继续执行
```



**为什么wait需要lambda条件：**

```cpp
// 虚假唤醒：线程可能在没有notify的情况下被唤醒
// 这是操作系统层面的问题，POSIX标准允许这种情况

// 没有条件判断：虚假唤醒就出bug
cv.wait(lock);  // 危险

// 有条件判断：虚假唤醒会重新检查条件，继续等
cv.wait(lock, []{ return ready; });  // 安全
```



#### notify_one vs notify_all

```cpp
// notify_one：唤醒一个等待线程（随机选）
// 适合：一个消息只需要一个消费者处理

// notify_all：唤醒所有等待线程
// 适合：状态变化需要通知所有线程
//       比如系统关闭，所有线程都要退出

// 机器人系统里的典型用法：
// 传感器数据来了 → notify_one（一个处理线程就够）
// 系统急停 → notify_all（所有线程都要响应）
```



#### 优雅关闭

```cpp
// 真实系统里队列需要支持关闭
// 关闭后等待中的线程要能退出，不能永远卡着

class MessageQueue{
public:
    void shutdown(){
        {
            std::lock_guard<std::mutex> lock(mtx_);
            shutdown_ = true;	// 标记关闭
        }
        cv_.notify_all();		// 唤醒所有等待线程
    }
    
    bool pop(Meesage& msg){
        std::unique_lock<std::mutex> lock(mtx_);
        cv_.wait(lock,[this]{
           return !queue_.empty() || shutdown_; 	// 有消息或关闭都退出等待
        });
        
        if(shutdown_ && queue.empty()) return false;	// 关闭且没消息
        
        msg = queue_.front();
        queue_.pop();
        return true;
    }
    
private:
    bool shutdown_ = false;
};
```



#### 小练习

```cpp
// 文件名：condvar_practice.cpp
// 编译：g++ -std=c++17 -Wall -pthread condvar_practice.cpp -o condvar_practice

#include <iostream>
#include <thread>
#include <mutex>
#include <condition_variable>
#include <queue>
#include <string>
#include <chrono>

struct Message {
    int id;
    std::string data;
};

class MessageQueue {
public:
    // 1. push：放消息，放完notify_one唤醒等待的消费者
    void push(const Message& msg) {
        {
            std::lock_guard<std::mutex> lock(mtx_);
            queue_.push(msg);
        }
        cv_.notify_one();  // 放完锁再notify，性能更好
    }

    // 2. pop：队列为空时挂起等待，不再空转
    //    返回false表示队列已关闭且为空
    bool pop(Message& msg) {
        std::unique_lock<std::mutex> lock(mtx_);
        cv_.wait(lock, [this]{
            return !queue_.empty() || shutdown_;
        });

        if (shutdown_ && queue_.empty()) return false;

        msg = queue_.front();
        queue_.pop();
        return true;
    }

    // 3. shutdown：关闭队列，唤醒所有等待线程
    void shutdown() {
        {
            std::lock_guard<std::mutex> lock(mtx_);
            shutdown_ = true;
        }
        cv_.notify_all();
    }

    // 4. size
    size_t size() const {
        std::lock_guard<std::mutex> lock(mtx_);
        return queue_.size();
    }

private:
    std::queue<Message> queue_;
    mutable std::mutex mtx_;
    std::condition_variable cv_;
    bool shutdown_ = false;
};

int main() {
    MessageQueue mq;

    // 生产者：放50条消息后关闭队列
    std::thread producer([&mq]{
        for (int i = 0; i < 50; i++) {
            mq.push({i, "msg_" + std::to_string(i)});
            std::this_thread::sleep_for(std::chrono::milliseconds(10));
        }
        std::cout << "生产者完成，关闭队列\n";
        mq.shutdown();  // 关闭队列
    });

    // 消费者：pop返回false时退出
    std::thread consumer([&mq]{
        Message msg;
        int count = 0;
        while (mq.pop(msg)) {  // pop返回false自动退出循环
            count++;
            if (count % 10 == 0) {
                std::cout << "已消费: " << count
                          << " 条，最新: " << msg.data << "\n";
            }
        }
        std::cout << "消费者退出，共消费: " << count << " 条\n";
    });

    producer.join();
    consumer.join();

    std::cout << "队列剩余: " << mq.size() << "\
```







### 第8天：原子操作 + 线程实战(TODO)

**目标：知道atomic，复习前两天内容**



#### 原子操作

```cpp
#include <atomic>

// 普通int，多线程下不安全
int count = 0;
count++;  // 三步操作，非原子

// atomic<int>，多线程下安全
std::atomic<int> atomic_count = 0;
atomic_count++;  // 原子操作，一步完成

// 常用操作
atomic_count.load();           // 读取值
atomic_count.store(10);        // 写入值
atomic_count.fetch_add(1);     // +1，返回旧值
atomic_count.fetch_sub(1);     // -1，返回旧值
atomic_count.exchange(5);      // 写入新值，返回旧值

// compare_exchange：CAS操作
int expected = 5;
bool ok = atomic_count.compare_exchange_strong(expected, 10);
// 如果atomic_count==expected，则写入10，返回true
// 如果atomic_count!=expected，则把当前值写入expected，返回false
```



**什么时候用atomic，什么时候用mutex：**

```cpp
// 用atomic：
// 简单的计数器、标志位、状态码
// 单个变量的读写
std::atomic<bool> running = true;
std::atomic<int> error_count = 0;

// 用mutex：
// 多个变量需要同时保护
// 复杂数据结构（queue、map）
// 需要保证一段代码的原子性
std::mutex mtx;
// 同时更新多个变量
{
    std::lock_guard<std::mutex> lock(mtx);
    count++;
    last_update = now();	// 这两个操作要同时保护
}
```



**memory_order（了解概念就行）：**

```cpp
// atomic操作默认是memory_order_seq_cst（顺序一致）
// 最安全但最慢

// 性能敏感场景可以用relaxed
atomic_count.fetch_add(1, std::memory_order_relaxed);
// 只保证原子性，不保证顺序
// 适合纯计数器，不需要和其他变量同步

// 实际工程里默认就好，不要过早优化
```































































































### 第9天：CMake基础

**目标：能独立建工程，会写CMakeLists.txt**



### 第10天：Lambda + 函数式

**目标：熟练用lambda，这是ROS2回调函数的基础**



### 第11天：模板基础

**目标：能看懂模板代码，会写简单模板**



### 第12天：设计模式

**目标：掌握机器人系统岗最常用的三个模式(单例模式 观察者模式 工厂模式)**



### 第13天：代码质量

**目标：写出工程级别的C++代码**



### 第14天：综合项目

**目标：串联所有知识点，验收学习成果**











## 第二阶段：Linux系统编程



### 第1天：文件IO基础

**目标：能用C读写文件，理解文件描述符**

前2小时：

- 文件描述符概念（0=stdin 1=stdout 2=stderr）
- `open` / `close` / `read` / `write`
- `O_RDONLY` / `O_WRONLY` / `O_RDWR` / `O_NONBLOCK`标志
- errno错误处理

后2小时，写练习：

cpp

```cpp
// 实现一个简单的文件读写工具
// open打开文件，read读内容，write写内容
// 每次操作后检查返回值和errno
// 用RAII封装fd，析构自动close
```

------



### 第2天：串口编程

**目标：能用C++读写串口，直接对应你的项目**

前2小时：

- `termios`结构体
- 波特率设置（`B9600` `B115200`）
- 数据位/停止位/校验位
- 原始模式 vs 规范模式

后2小时，写练习：

cpp

```cpp
// 封装SerialPort类
// open(port, baudrate)
// read(buf, len, timeout_ms)  带超时
// write(buf, len)
// 析构自动close
// 这就是raspbot项目底盘驱动的核心
```

------



### 第3天：串口协议收发

**目标：在串口基础上实现帧收发，和你的网关经验直接挂钩**

前2小时：

- 粘包问题（TCP有，串口也有）
- 帧定界：起始符+长度+校验
- 循环buffer做接收缓冲
- CRC校验基础

后2小时，写练习：

cpp

```cpp
// 在SerialPort基础上实现FrameParser
// 接收字节流，识别完整帧
// 帧格式：[0xAA][len][data...][crc8]
// 帧不完整时缓存，等下一次read
```

------



### 第4天：I2C编程

**目标：能用Linux I2C接口读写传感器**

前2小时：

- I2C协议基础（地址/寄存器/读写时序）
- Linux I2C-dev接口
- `ioctl(fd, I2C_SLAVE, addr)`
- `i2cdetect`工具扫描设备

后2小时，写练习：

cpp

```cpp
// 封装I2CDevice类
// 读寄存器：readReg(reg_addr)
// 写寄存器：writeReg(reg_addr, value)
// 读多字节：readRegs(reg_addr, buf, len)
// 在树莓派上读MPU6050的设备ID验证
```

------



### 第5-6天：多进程基础

**目标：理解进程，会用fork/exec，知道进程和线程的区别**

第5天前2小时：

- 进程 vs 线程（资源隔离 vs 共享）
- `fork()` / `exec()` / `waitpid()`
- 僵尸进程是什么，怎么避免
- 信号基础：`SIGINT` `SIGTERM` `SIGKILL`

第5天后2小时：

cpp

```cpp
// 写一个简单的进程管理器
// fork子进程执行任务
// 父进程监控子进程状态
// 子进程崩溃时自动重启（看门狗雏形）
```

第6天：信号处理

cpp

```cpp
// 注册SIGTERM处理函数
// 收到信号时优雅退出（清理资源）
// 这是ROS2节点退出的基础
```

------



### 第7-8天：进程间通信

**目标：掌握共享内存和管道，这是ROS2底层的思路**

第7天：管道和命名管道

cpp

```cpp
// pipe()：父子进程通信
// mkfifo()：无关进程通信
// 写一个简单的日志收集器
// 多个进程写入命名管道，一个进程读取打印
```

第8天：共享内存

cpp

```cpp
// shmget/shmat/shmdt/shmctl
// 两个进程共享一块内存
// 用信号量保护共享内存（sem_wait/sem_post）
// 写一个共享状态板：一个进程写传感器数据，另一个读
```

------



### 第9-10天：epoll与非阻塞IO

**目标：理解IO多路复用，能同时监控多个fd**

第9天前2小时：

- 阻塞IO vs 非阻塞IO vs IO多路复用
- `select` → `poll` → `epoll`演进
- `epoll_create` / `epoll_ctl` / `epoll_wait`
- ET（边缘触发）vs LT（水平触发）

第9天后2小时：

cpp

```cpp
// 用epoll同时监控多个串口
// 哪个串口有数据来就读哪个
// 不需要多线程，单线程处理多路IO
```

第10天：

cpp

```cpp
// 升级SerialPort类支持非阻塞读
// 用epoll监控串口fd
// 超时处理：epoll_wait的timeout参数
// 这是机器人系统里多设备并发读取的基础
```

------



### 第11-12天：定时器与实时性

**目标：理解Linux定时器，知道实时性怎么保证**

第11天：

cpp

```cpp
// timerfd_create：基于fd的定时器，可以用epoll监控
// clock_gettime：高精度时间戳（CLOCK_MONOTONIC）
// 测量代码执行耗时
// 写一个周期性任务调度器（固定频率执行任务）
```

第12天：实时性基础（概念为主）

- PREEMPT_RT补丁是什么
- 实时进程优先级：`SCHED_FIFO` / `SCHED_RR`
- CPU亲和性：把进程绑定到指定核
- 内存锁定：`mlockall`避免缺页中断
- 实际操作：用`chrt`命令设置进程优先级

cpp

```cpp
// 测量任务调度抖动
// 周期1ms的任务，实际执行间隔是多少
// 普通进程 vs 实时进程对比
```

------



### 第13天：综合练习

**目标：把串口、epoll、定时器串起来**

cpp

```cpp
// 多设备通信管理器
// epoll监控3个串口fd + 1个timerfd
// 串口有数据来：读取解析帧
// 定时器触发：发送心跳包，检查设备超时
// SIGTERM信号：优雅退出
// 这就是raspbot项目驱动层的完整模型
```

------



### 第14天：移植到树莓派

**目标：在真实硬件上跑通**

- 交叉编译基础（或直接在树莓派上编译）
- 串口设备路径：`/dev/ttyAMA0` `/dev/ttyUSB0`
- 权限问题：`dialout`用户组
- 用`strace`调试系统调用
- 把SerialPort + FrameParser在树莓派上跑通







## 第三阶段：ROS2



### 第1-3天：环境搭建+基础概念

第1天：

- Ubuntu 22.04安装（虚拟机或树莓派）
- ROS2 Humble安装
- `colcon build`第一个包
- 理解工作空间结构：`src` / `build` / `install`

第2天：核心概念

```
Topic    发布订阅  异步  传感器数据
Service  请求响应  同步  查询/控制
Action   长任务    异步+反馈  导航/机械臂
Param    运行时配置
```

第3天：

- 用C++写第一个发布者/订阅者
- 自定义消息类型（`.msg`文件）
- `ros2 topic list/echo/hz`命令

------



### 第4-6天：C++节点开发

第4天：

cpp

```cpp
// 发布者节点
// 继承rclcpp::Node
// 创建Publisher<msg>
// 定时器定期发布
```

第5天：

cpp

```cpp
// 订阅者节点
// 创建Subscription<msg>
// 回调函数处理消息
// 和发布者节点同时运行
```

第6天：

cpp

```cpp
// Service服务端+客户端
// 自定义srv文件
// 同步调用 vs 异步调用
```

------



### 第7-9天：DDS深化

第7天：QoS配置

cpp

```cpp
// RELIABILITY: RELIABLE vs BEST_EFFORT
// DURABILITY: TRANSIENT_LOCAL vs VOLATILE
// DEADLINE: 超时告警
// HISTORY: KEEP_LAST vs KEEP_ALL

// 什么时候用什么：
// 传感器数据 → BEST_EFFORT（允许丢包，要低延迟）
// 控制指令   → RELIABLE（不能丢）
// 状态信息   → TRANSIENT_LOCAL（新订阅者能收到最新值）
```

第8天：

- Fast-DDS基本原理
- 域（Domain）和参与者（Participant）
- 发现机制（Discovery）
- 多机通信配置

第9天：

cpp

```cpp
// 实战：配置不同QoS，观察行为差异
// 用ros2 topic hz测量发布频率
// 用ros2 topic delay测量端到端延迟
```

------



### 第10-12天：Lifecycle Node

第10天：

cpp

```cpp
// 生命周期状态机：
// Unconfigured → Inactive → Active → Finalized
// on_configure() on_activate() on_deactivate() on_cleanup()

// 为什么用Lifecycle：
// 普通节点：启动就跑，无法控制初始化顺序
// Lifecycle节点：可以控制启动顺序，系统状态管理
```

第11天：

cpp

```cpp
// 把SerialPort驱动包装成Lifecycle节点
// configure阶段：打开串口，初始化参数
// activate阶段：开始收发数据
// deactivate阶段：停止收发，保持连接
// cleanup阶段：关闭串口
```

第12天：

cpp

```cpp
// 多Lifecycle节点编排
// Launch文件控制启动顺序
// 节点管理器监控各节点状态
```

------



### 第13-15天：Launch文件+参数

第13天：

python

```python
# launch文件基础
# 启动多个节点
# 传递参数
# 条件启动
```

第14天：

cpp

```cpp
// 参数服务器
// 声明参数：declare_parameter
// 读取参数：get_parameter
// 动态修改：参数回调
// yaml配置文件
```

第15天：

cpp

```cpp
// 把raspbot项目的所有参数外部化
// 串口路径/波特率/发布频率都从yaml读
// 不同硬件配置不改代码，只换yaml
```

------



### 第16-20天：raspbot项目实战

**这五天是重点，把之前学的全部用上**

第16天：底盘驱动节点

cpp

```cpp
// 串口通信（用Linux阶段写的SerialPort）
// 订阅/cmd_vel话题
// 麦克纳姆轮运动学解算
// 发布电机指令到驱动板
```

第17天：传感器节点

cpp

```cpp
// 超声波传感器节点
// 摄像头节点（V4L2或OpenCV）
// 发布标准ROS2消息类型
// sensor_msgs/Range
// sensor_msgs/Image
```

第18天：系统状态机节点

cpp

```cpp
// IDLE/MOVING/AVOIDING/FAULT/ESTOP
// Lifecycle Node实现
// 订阅传感器话题
// 发布系统状态话题
```

第19天：传感器健康监控节点

cpp

```cpp
// 订阅所有传感器话题
// 监控发布频率
// 超时检测：>200ms没收到数据→告警
// 发布/system/sensor_health话题
```

第20天：整合+调试

cpp

```cpp
// 写完整Launch文件启动所有节点
// rqt_graph查看节点图
// ros2 bag录制传感器数据
// 调试端到端延迟
```

------



### 第21-23天：调试工具链

第21天：

- `rqt_graph`：节点通信图
- `rqt_plot`：实时数据曲线
- `rviz2`：传感器数据可视化

第22天：

- `ros2 bag`：数据录制回放
- 回放数据调试算法（不需要真实硬件）
- bag文件分析

第23天：

- 性能分析：话题延迟测量
- `ros2 doctor`：系统诊断
- 常见问题排查

------



### 第24-26天：进阶话题

第24天：组件（Component）

cpp

```cpp
// 把节点编译成动态库
// 多个节点跑在同一进程
// 零拷贝通信（进程内）
// 降低延迟
```

第25天：执行器（Executor）

cpp

```cpp
// SingleThreadedExecutor
// MultiThreadedExecutor
// 回调组（CallbackGroup）
// 控制并发
```

第26天：自定义消息和服务

cpp

```cpp
// 设计raspbot专用消息
// WheelSpeed.msg
// SystemStatus.msg
// DeviceHealth.srv
```

------



### 第27-30天：项目收尾

第27天：

- 代码整理，统一命名规范
- 加单元测试（gtest）
- 补充注释

第28天：

- 录演示视频
- 写README（架构图+功能说明+运行方法）
- rqt_graph截图放进去

第29天：

- 简历描述写好（用之前给你的模板）
- 整理面试能讲的技术点清单

第30天：

- 模拟面试，把项目从头讲一遍
- 计时，控制在15分钟内
- 找朋友或者来找我练

















































































































































































































