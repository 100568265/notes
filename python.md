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























