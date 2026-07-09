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





























































































































































































































