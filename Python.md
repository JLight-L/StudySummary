# 蟒基本语法
## From DeepSeek
以下是Python基础语法的详细介绍，包含代码示例：

---

### 一、基本数据类型
Python有5种核心基础数据类型：

| 类型         | 示例                    | 说明                 |
| ---------- | --------------------- | ------------------ |
| `int`      | `5`, `-3`, `0b1010`   | 整数（支持二进制、八进制、十六进制） |
| `float`    | `3.14`, `-2.5e3`      | 浮点数（科学计数法表示）       |
| `str`      | `"Hello"`, `'Python'` | 字符串（单/双引号等价，不可变）   |
| `bool`     | `True`, `False`       | 布尔值（首字母必须大写）       |
| `NoneType` | `None`                | 空值（类似其他语言的null）    |

**类型转换函数**：
```python
num_str = "123"
num_int = int(num_str)  # 字符串→整数 → 123
num_float = float("3.14")  # → 3.14
bool_val = bool(0)  # → False
```

---

### 二、变量与动态类型
- **变量声明**：直接赋值即声明
  ```python
  age = 25             # 整数类型
  price = 9.99         # 浮点类型
  name = "Alice"       # 字符串
  is_student = True    # 布尔值
  ```
- **动态类型**：变量可随时改变类型
  ```python
  var = 10      # 此时是int
  var = "text"  # 变为str类型
  ```

---

### 三、函数声明与调用
#### 1. 基本函数结构
```python
def greet(name, times=1):  # 默认参数times=1
    """打印欢迎信息（文档字符串）"""
    for _ in range(times):
        print(f"Hello, {name}!")

# 调用方式
greet("Bob")            # 位置参数 → Hello, Bob!
greet(times=3, name="Charlie")  # 关键字参数 → 打印3次
```

#### 2. 返回多个值（实际返回元组）
```python
def calculate(a, b):
    return a+b, a*b  # 返回元组 → (sum, product)

sum_result, product_result = calculate(3,4)
```

---

### 四、控制结构
#### 1. 条件语句
```python
score = 85
if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'  # 执行此分支
else:
    grade = 'C'
```

#### 2. 循环结构
**for循环**：
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit.upper())  # 输出全大写

# 配合range使用
for i in range(3):  # 0,1,2
    print(i**2)
```

**while循环**：
```python
count = 3
while count > 0:
    print(count)
    count -= 1  # 3,2,1
```

---

### 五、注释与代码块
1. **注释**：
   ```python
   # 这是单行注释

   """
   这是多行注释（实际是字符串字面量）
   通常用于函数/类的文档说明
   """
   ```

2. **代码块**：通过缩进（4空格建议）划分
   ```python
   if True:
       print("属于if块")  # 缩进4空格
       print("同一代码块")
   print("已退出代码块")
   ```

---

### 六、容器型数据类型
#### A. 列表、元组、字典、集合
##### 1. **列表（List）**
- **特性**：有序、可变、可重复元素
- **创建方式**：`[]` 或 `list()`
- **常用操作**：
  ```python
  # 创建列表
  fruits = ["apple", "banana", "cherry"]
  numbers = list(range(5))  # [0,1,2,3,4]

  # 增删改查
  fruits.append("orange")      # 末尾添加 → ["apple", "banana", "cherry", "orange"]
  fruits.insert(1, "mango")    # 插入到索引1 → ["apple", "mango", "banana", ...]
  popped = fruits.pop(2)       # 删除索引2元素 → popped="banana"
  fruits[0] = "kiwi"           # 修改元素 → ["kiwi", ...]

  # 切片操作
  print(fruits[1:3])   # 输出索引1到2的元素（左闭右开）
  print(fruits[::-1])  # 反转列表

  # 列表推导式（高效创建）
  squares = [x**2 for x in range(10) if x%2==0]  # [0,4,16,36,64]
  ```

##### 2. **元组（Tuple）**
- **特性**：有序、**不可变**、可重复元素（适合存储常量数据）
- **创建方式**：`()` 或 `tuple()`，单元素需加逗号 `(1,)`
  ```python
  colors = ("red", "green", "blue")
  coordinates = ( (1,2), (3,4) )  # 嵌套元组

  # 不可变性示例
  # colors[0] = "yellow"  # 会报错（TypeError）

  # 解包（unpacking）
  x, y = (5, 10)
  print(f"x={x}, y={y}")  # → x=5, y=10
  ```

##### 3. **字典（Dict）**
- **特性**：键值对、**无序**、键不可重复
- **创建方式**：`{}` 或 `dict()`
  ```python
  # 创建字典
  student = {
      "name": "Alice",
      "age": 20,
      "courses": ["Math", "CS"]
  }

  # 增删改查
  student["gender"] = "Female"        # 添加键值对
  del student["age"]                  # 删除键
  student["name"] = "Bob"             # 修改值
  print(student.get("score", 0))      # 安全获取 → 0（默认值）

  # 字典推导式
  square_dict = {x: x**2 for x in range(5)}  # {0:0, 1:1, 2:4, ...}

  # 遍历
  for key, value in student.items():
      print(f"{key}: {value}")
  ```

##### 4. **集合（Set）**
- **特性**：无序、元素唯一、可数学运算（并/交/差集）
- **创建方式**：`{}`*（需有元素）* 或 `set()`
  ```python
  a = {1,2,3,3}        # 自动去重 → {1,2,3}
  b = set([2,3,4])

  print(a | b)  # 并集 → {1,2,3,4}
  print(a & b)  # 交集 → {2,3}
  print(a - b)  # 差集 → {1}
  ```

---

#### B. 各类型对比表

| 类型    | 可变性 | 有序性 | 元素要求       | 典型应用场景               |
|---------|--------|--------|----------------|--------------------------|
| `list`  | 可变   | 有序   | 允许重复       | 动态数据集合、队列/栈      |
| `tuple` | 不可变 | 有序   | 允许重复       | 固定配置项、数据库记录     |
| `dict`  | 可变   | 无序   | 键必须可哈希   | 键值映射、JSON数据存储     |
| `set`   | 可变   | 无序   | 元素必须可哈希 | 去重、集合运算、成员检测   |

---

#### C.高级操作技巧

##### 1. **嵌套数据结构**
```python
# 列表嵌套字典
employees = [
    {"name": "John", "dept": "Sales"},
    {"name": "Lisa", "dept": "IT"}
]

# 字典嵌套列表
school = {
    "classes": ["A", "B", "C"],
    "teachers": {
        "Math": ["Mr. Smith"],
        "English": ["Ms. Lee"]
    }
}
```

##### 2. **类型转换**
```python
nums_tuple = (1,2,3)
nums_list = list(nums_tuple)  # 元组→列表 → [1,2,3]

keys = ["a", "b"]
values = [10, 20]
mapping = dict(zip(keys, values))  # → {'a':10, 'b':20}
```

---

#### D. 实际应用示例
**统计文本词频**：
```python
text = "apple banana apple cherry banana apple"
words = text.split()

word_count = {}
for word in words:
    word_count[word] = word_count.get(word, 0) + 1

print(word_count)  # → {'apple':3, 'banana':2, 'cherry':1}
```

---

### 七、综合示例1
```python
def is_prime(n):
    """判断是否为质数"""
    if n <= 1:
        return False
    for i in range(2, int(n**0.5)+1):
        if n % i == 0:
            return False
    return True

# 找出100以内的质数
primes = [x for x in range(100) if is_prime(x)]
print(f"质数列表：{primes}")
```

---

### 八、类与对象基础

#### 1. 类定义与对象创建
```python
class Dog:
    # 类属性（所有实例共享）
    species = "Canis familiaris"

    # 构造方法（初始化实例属性）
    def __init__(self, name, age):
        self.name = name  # 实例属性
        self.age = age

    # 实例方法
    def bark(self):
        print(f"{self.name} says: Woof!")

# 创建对象
my_dog = Dog("Buddy", 3)
print(my_dog.species)  # 访问类属性 → "Canis familiaris"
my_dog.bark()          # 调用方法 → "Buddy says: Woof!"
```

#### 2. 特殊方法（双下划线方法）
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    # 实现加法运算符重载
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    # 定义对象的字符串表示
    def __str__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(2, 3)
v2 = Vector(1, 4)
print(v1 + v2)  # 输出 Vector(3, 7)
```

---

### 九、继承与多态
#### 1. 基础继承
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        raise NotImplementedError("子类必须实现此方法")

class Cat(Animal):  # 继承Animal类
    def speak(self):  # 方法重写
        return "Meow"

class Dog(Animal):
    def speak(self):
        return "Woof"

# 多态演示
animals = [Cat("Kitty"), Dog("Buddy")]
for animal in animals:
    print(f"{animal.name} says {animal.speak()}")
# 输出：
# Kitty says Meow
# Buddy says Woof
```

#### 2. 多重继承
```python
class Camera:
    def take_photo(self):
        print("Taking photo")

class Phone:
    def make_call(self):
        print("Making call")

class SmartPhone(Camera, Phone):  # 多重继承
    def unlock(self):
        print("Face recognition unlock")

iphone = SmartPhone()
iphone.take_photo()  # 继承自Camera
iphone.make_call()   # 继承自Phone
```

---

### 十、高级特性
#### 1. 类属性 vs 实例属性
```python
class Student:
    school = "XYZ School"  # 类属性

    def __init__(self, name):
        self.name = name    # 实例属性

s1 = Student("Alice")
s2 = Student("Bob")

print(s1.school)  # → "XYZ School"
Student.school = "ABC School"  # 修改类属性
print(s2.school)  # → "ABC School"
```

#### 2. 私有属性（约定式）
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # 双下划线前缀表示私有

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):  # 通过方法访问私有属性
        return self.__balance

account = BankAccount(1000)
# print(account.__balance)  # 会报错
print(account.get_balance())  # 正确访问方式 → 1000
```

---

### 十一、装饰器应用
#### 1. @property 装饰器
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        """Get radius (readonly)"""
        return self._radius

    @property
    def area(self):
        """计算属性"""
        return 3.14 * self._radius ** 2

c = Circle(5)
print(c.area)  # → 78.5
# c.radius = 10  # 会报错（因为是只读属性）
```

#### 2. @classmethod 与 @staticmethod
```python
class DateUtil:
    @classmethod
    def from_string(cls, date_str):  # cls指类本身
        year, month, day = map(int, date_str.split('-'))
        return cls(year, month, day)  # 创建新实例

    @staticmethod
    def is_valid_date(date_str):  # 无self/cls参数
        try:
            year, month, day = map(int, date_str.split('-'))
            return 1 <= month <=12 and 1<= day <=31
        except:
            return False

date = DateUtil.from_string("2023-08-15")
print(DateUtil.is_valid_date("2023-13-01"))  # → False
```

---

### 十二、综合示例2：电商系统
```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def display_info(self):
        print(f"Product: {self.name} (￥{self.price})")

class ShoppingCart:
    def __init__(self):
        self.items = []

    def add_item(self, product, quantity=1):
        self.items.append( (product, quantity) )

    def calculate_total(self):
        return sum(p.price * q for p, q in self.items)

# 使用示例
phone = Product("Smartphone", 2999)
case = Product("Phone Case", 99)

cart = ShoppingCart()
cart.add_item(phone)
cart.add_item(case, 2)

print(f"Total: ￥{cart.calculate_total()}")  # → 2999 + 99*2 = 3197
```

---
### 十三、类型注释
以下是类型注释（Type Hints）在各部分内容中的具体添加方式，按照Python PEP 484规范整理：

---

#### A. 添加类型注释
##### 1. **变量与动态类型**部分（添加变量类型标注）
```python
# 原代码
age = 25
price = 9.99
name = "Alice"

# 添加类型注释
age: int = 25
price: float = 9.99
name: str = "Alice"
is_student: bool = True
```

##### 2. **函数声明与调用**部分（参数/返回值类型标注）
```python
# 原函数定义
def greet(name, times=1):
    for _ in range(times):
        print(f"Hello, {name}!")

# 添加类型注释
def greet(name: str, times: int = 1) -> None:
    """打印欢迎信息"""
    for _ in range(times):
        print(f"Hello, {name}!")

# 返回多个值的类型标注
from typing import Tuple
def calculate(a: int, b: int) -> Tuple[int, int]:
    return a+b, a*b
```

---

#### B. 高级类型注释技巧
##### 1. 复合类型标注（需导入typing模块）
```python
from typing import List, Dict, Union, Optional

# 列表类型
scores: List[int] = [90, 85, 78]

# 字典类型（键值类型标注）
student: Dict[str, Union[str, int]] = {
    "name": "Alice",
    "age": 20
}

# 可选类型（可能为None）
def find_user(id: int) -> Optional[str]:
    return "Alice" if id == 1 else None
```

##### 2. 自定义类型别名
```python
from typing import Tuple

# 定义坐标类型别名
Coordinate = Tuple[float, float]

def move(point: Coordinate, delta: Coordinate) -> Coordinate:
    return (point[0]+delta[0], point[1]+delta[1])
```

---

#### C. 各模块类型注释完整示例
##### 1. 函数增强版
```python
from typing import Iterable

def filter_even(numbers: Iterable[int]) -> list[int]:
    return [n for n in numbers if n % 2 == 0]
```

##### 2. 类增强版
```python
class Vector:
    def __init__(self, x: float, y: float) -> None:
        self.x: float = x
        self.y: float = y

    def __add__(self, other: 'Vector') -> 'Vector':
        return Vector(self.x + other.x, self.y + other.y)
```

##### 3. 电商系统示例增强
```python
from typing import List, Tuple

class Product:
    def __init__(self, name: str, price: float) -> None:
        self.name: str = name
        self.price: float = price

class ShoppingCart:
    def __init__(self) -> None:
        self.items: List[Tuple[Product, int]] = []

    def add_item(self, product: Product, quantity: int = 1) -> None:
        self.items.append( (product, quantity) )
```

---

#### E. 类型注释的价值
- 提高代码可读性：明确参数/返回值的预期类型
- 增强IDE支持：获得更好的代码补全和错误提示
- 静态类型检查：通过mypy等工具提前发现潜在问题
- 便于团队协作：明确接口契约，降低沟通成本
### 十四、总结
**关键特性总结**：
- **动态类型**：变量无需声明类型
- **缩进规则**：用缩进代替大括号定义代码块
- **灵活的函数参数**：支持默认参数、关键字参数
- **简洁的语法**：列表推导式等特性简化代码

**面向对象编程要点**：
- **封装**：通过类将数据与操作封装在一起
- **继承**：实现代码复用和层次化结构
- **多态**：不同对象对相同方法做出不同响应
- **组合优于继承**：优先使用对象组合而非复杂继承链
- **特殊方法**：通过`__method__`实现运算符重载等特性

## From Kimi
### 1. **基本数据类型**

Python 有多种基本数据类型，以下是最常用的：

#### **整数 (int)**

```python
x = 42
print(x)  # 输出 42
```

#### **浮点数 (float)**

```python
y = 3.14
print(y)  # 输出 3.14
```

#### **字符串 (str)**

字符串可以使用单引号 `'` 或双引号 `"` 定义。

```python
name = "Alice"
print(name)  # 输出 Alice

# 字符串拼接
greeting = "Hello, " + name
print(greeting)  # 输出 Hello, Alice
```

#### **布尔值 (bool)**

布尔值只有两个值：`True` 和 `False`。

```python
is_valid = True
print(is_valid)  # 输出 True
```

### 2. **变量**

Python 是动态类型语言，变量不需要声明类型，直接赋值即可。

```python
x = 10        # 整数
x = "Python"  # 字符串
print(x)      # 输出 Python
```

### 3. **运算符**

#### **算术运算符**

```python
a = 10
b = 3

print(a + b)  # 加法：13
print(a - b)  # 减法：7
print(a * b)  # 乘法：30
print(a / b)  # 除法：3.333...
print(a % b)  # 取模：1
print(a ** b) # 幂运算：1000
```

#### **比较运算符**

```python
print(3 == 4)   # 等于：False
print(3 != 4)   # 不等于：True
print(3 > 4)    # 大于：False
print(3 < 4)    # 小于：True
print(3 >= 4)   # 大于等于：False
print(3 <= 4)   # 小于等于：True
```

#### **逻辑运算符**

```python
x = True
y = False

print(x and y)  # 逻辑与：False
print(x or y)   # 逻辑或：True
print(not x)    # 逻辑非：False
```

### 4. **函数声明与调用**

#### **函数声明**

使用 `def` 关键字声明函数，语法如下：

```python
def greet(name):
    print("Hello, " + name + "!")
```

#### **函数调用**

```python
greet("Alice")  # 输出 Hello, Alice!
```

#### **带返回值的函数**

使用 `return` 关键字返回值：

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 输出 8
```

#### **默认参数**

可以给函数参数设置默认值：

```python
def greet(name="World"):
    print("Hello, " + name + "!")

greet()          # 输出 Hello, World!
greet("Alice")   # 输出 Hello, Alice!
```

#### **位置参数与关键字参数**

```python
def describe_pet(animal, name):
    print(f"I have a {animal} named {name}.")

# 位置参数
describe_pet("dog", "Buddy")  # 输出 I have a dog named Buddy.

# 关键字参数
describe_pet(name="Buddy", animal="dog")  # 输出 I have a dog named Buddy.
```

### 5. **常用内置函数**

Python 提供了许多内置函数，以下是一些常用示例：

#### **输入和输出**

```python
# 输入
name = input("Enter your name: ")  # 等待用户输入
print("Hello, " + name + "!")

# 输出
print("Hello, Python!")  # 显示文本
```

#### **类型转换**

```python
num_str = "123"
num_int = int(num_str)  # 转换为整数
print(num_int + 1)      # 输出 124

num_float = float(num_int)  # 转换为浮点数
print(num_float)           # 输出 123.0
```

#### **数学运算**

```python
import math

print(math.sqrt(16))  # 开平方：4.0
print(abs(-5))        # 绝对值：5
```

### 6. **注释**

Python 中的注释使用 `#`。多行注释可以用三引号 `'''` 或 `"""`。

```python
# 这是单行注释

"""
这是多行注释
可以跨越多行
"""
```

### 7. **列表 (List)**

列表是 Python 中最常用的数据结构之一，用 `[]` 表示。

#### **创建列表**

```python
fruits = ["apple", "banana", "cherry"]
print(fruits)  # 输出 ['apple', 'banana', 'cherry']
```

#### **访问元素**

```python
print(fruits[0])  # 访问第一个元素：apple
print(fruits[-1]) # 访问最后一个元素：cherry
```

#### **添加元素**

```python
fruits.append("orange")  # 在末尾添加元素
print(fruits)            # 输出 ['apple', 'banana', 'cherry', 'orange']
```

#### **删除元素**

```python
fruits.remove("banana")  # 删除指定元素
print(fruits)            # 输出 ['apple', 'cherry', 'orange']
```

### 8. **条件语句**

条件语句使用 `if`、`elif` 和 `else`。

```python
age = 18

if age < 18:
    print("未成年人")
elif age == 18:
    print("刚成年")
else:
    print("成年人")
```

### 9. **循环**

Python 支持 `for` 和 `while` 循环。

#### **for 循环**

```python
for i in range(5):
    print(i)  # 输出 0, 1, 2, 3, 4
```

#### **while 循环**

```python
count = 0
while count < 5:
    print(count)  # 输出 0, 1, 2, 3, 4
    count += 1
```

### ai关于类的思考
在探索Python类和对象的过程中，我意识到这是一个关于面向对象编程（OOP）的重要主题。我开始思考，如何通过类来创建可重用的代码结构，以及如何通过对象来实例化这些结构。

我首先想到的是，类应该是一个包含属性和方法的模板。我尝试定义一个简单的类，比如`Person`，然后给它添加一些属性，比如`name`和`age`。我写道：

```python
class Person:
    pass
```

但这样显然不够，我需要给这个类添加一些内容。我想到，可以通过`__init__`方法来初始化类的属性。我尝试这样写：

```python
class Person:
    def __init__(self):
        self.name = "Unknown"
        self.age = 0
```

但这样似乎有点局限，我不能为每个人设置不同的名字和年龄。我意识到我需要让这个类更加灵活，所以我尝试接受参数：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

这个看起来好多了，我可以为每个人设置不同的名字和年龄。我创建了一个`Person`对象：

```python
person1 = Person("Alice", 25)
```

然后我尝试打印这个对象的属性：

```python
print(person1.name)  # 输出 Alice
print(person1.age)   # 输出 25
```

这似乎行得通。但我觉得还不够，我应该给这个类添加一些方法。我尝试添加一个方法，比如`introduce`，让它可以输出这个人的介绍：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."
```

然后我调用这个方法：

```python
print(person1.introduce())  # 输出 My name is Alice and I am 25 years old.
```

这看起来很好。但我又想到，如果我想改变这个人的年龄，我需要直接修改属性，这似乎不太优雅。我想到可以添加一个方法来更新年龄：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."
    
    def set_age(self, new_age):
        self.age = new_age
```

然后我尝试更新年龄：

```python
person1.set_age(26)
print(person1.introduce())  # 输出 My name is Alice and I am 26 years old.
```

这似乎更合理了。我继续思考，如果我想展示这个人的信息，我应该怎么做。我想到了`__str__`方法：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."
    
    def set_age(self, new_age):
        self.age = new_age
    
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"
```

然后我打印这个对象：

```python
print(person1)  # 输出 Person(name=Alice, age=26)
```

这看起来很清晰。但我想知道，如果我想计算这个人的出生年份，我应该怎么做。我假设当前年份是2023：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."
    
    def set_age(self, new_age):
        self.age = new_age
    
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"
    
    def get_birth_year(self, current_year=2023):
        return current_year - self.age
```

然后我获取出生年份：

```python
print(person1.get_birth_year())  # 输出 1997
```

这似乎是对的。但我又想到，如果我想确保年龄是正数，我应该怎么做。我添加一个条件检查：

```python
class Person:
    def __init__(self, name, age):
        if age < 0:
            raise ValueError("Age cannot be negative.")
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."
    
    def set_age(self, new_age):
        if new_age < 0:
            raise ValueError("Age cannot be negative.")
        self.age = new_age
    
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"
    
    def get_birth_year(self, current_year=2023):
        return current_year - self.age
```

然后我尝试设置一个负数的年龄：

```python
person1.set_age(-1)  # 这会抛出 ValueError
```

这确保了年龄的合理性。通过这一系列的探索、尝试、犯错、思路调整、顿悟、实施想法、验证，我最终找到了创建和使用Python类的关键思路。我感到非常满意，因为我不仅解决了问题，还学到了很多关于面向对象编程的知识。

好的！除了基本语法、数据类型和函数，Python 还有一个非常重要的部分：**面向对象编程（OOP）**。这里介绍一下 Python 中的类与对象。

### 10. **类（Class）的基本概念**

在 Python 中，`类` 是一种用户自定义的数据类型，它可以包含数据（属性）和函数（方法）。类是对象的蓝图或模板，用于创建对象。

```python
# 定义一个类
class Dog:
    # 类的属性
    species = "Canis familiaris"  # 类变量，所有实例共享

    # 初始化方法（构造函数）
    def __init__(self, name, age):
        self.name = name  # 实例变量
        self.age = age    # 实例变量

    # 实例方法
    def bark(self):
        return f"{self.name} says woof!"

    # 另一个实例方法
    def sit(self):
        return f"{self.name} is sitting."
```

- `__init__` 是一个特殊方法，用于初始化对象的属性。
    
- `self` 是实例方法的第一个参数，代表类的实例本身。
    

### 11. **创建对象（实例）**

通过类创建对象的过程称为**实例化**。每个对象都有自己的属性和方法。

```python
# 创建 Dog 类的实例
dog1 = Dog("Buddy", 3)
dog2 = Dog("Charlie", 5)

# 访问属性
print(dog1.name)  # 输出: Buddy
print(dog2.age)   # 输出: 5

# 调用方法
print(dog1.bark())  # 输出: Buddy says woof!
print(dog2.sit())   # 输出: Charlie is sitting.
```

### 12. **类变量与实例变量**

- **类变量**：在类中定义，所有实例共享。
- **实例变量**：在 `__init__` 方法中定义，每个实例私有。

```python
class Dog:
    species = "Canis familiaris"  # 类变量

    def __init__(self, name, age):
        self.name = name  # 实例变量
        self.age = age    # 实例变量

# 创建实例
dog1 = Dog("Buddy", 3)
dog2 = Dog("Charlie", 5)

# 类变量
print(dog1.species)  # 输出: Canis familiaris
print(dog2.species)  # 输出: Canis familiaris

# 修改类变量会影响所有实例
Dog.species = "Canis Lupus"
print(dog1.species)  # 输出: Canis Lupus
print(dog2.species)  # 输出: Canis Lupus
```

### 13. **继承（Inheritance）**

继承允许一个类（子类）继承另一个类（父类）的属性和方法。

```python
# 父类
class Animal:
    def __init__(self, name):
        self.name = name

    def eat(self):
        return f"{self.name} is eating."

# 子类
class Dog(Animal):
    def bark(self):
        return f"{self.name} says woof!"

# 创建子类实例
dog = Dog("Buddy")
print(dog.eat())  # 调用父类方法：输出 Buddy is eating.
print(dog.bark()) # 调用子类方法：输出 Buddy says woof!
```

### 14. **多态（Polymorphism）**

多态允许不同类的对象对同一方法或属性有不同的实现。

```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

# 多态
def animal_sound(animal):
    return animal.speak()

dog = Dog()
cat = Cat()

print(animal_sound(dog))  # 输出: Woof!
print(animal_sound(cat))  # 输出: Meow!
```

### 15. **封装（Encapsulation）**

封装通过将数据（属性）和行为（方法）组合在一起，隐藏内部实现细节。

- **私有属性**：在属性名前加双下划线 `__`，使其对外不可见。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.__age = age  # 私有属性

    def get_age(self):
        return self.__age  # 提供访问私有属性的方法

    def set_age(self, new_age):
        if new_age > 0:
            self.__age = new_age
        else:
            print("Age cannot be negative.")

person = Person("Alice", 25)
print(person.get_age())  # 输出: 25
person.set_age(30)
print(person.get_age())  # 输出: 30
```

### 16. **特殊方法（Magic Methods）**

Python 提供了一些特殊方法（如 `__init__`、`__str__`、`__len__` 等），用于自定义对象的行为。

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def __str__(self):  # 自定义字符串表示
        return f"{self.title} by {self.author}"

    def __len__(self):  # 自定义长度
        return len(self.title)

book = Book("1984", "George Orwell")
print(book)      # 输出: 1984 by George Orwell
print(len(book)) # 输出: 4 (title的长度)
```

### 17. **装饰器（Decorator）**

装饰器用于修改函数或方法的行为，通常用于日志、权限检查等。

```python
# 定义一个装饰器
def log_method(func):
    def wrapper(self):
        print(f"Calling method: {func.__name__}")
        return func(self)
    return wrapper

class Dog:
    @log_method
    def bark(self):
        return "Woof!"

dog = Dog()
print(dog.bark())
# 输出:
# Calling method: bark
# Woof!
```
## From 真人
这个人很懒，什么都没写……