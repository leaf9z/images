# Python面向对象



# 一、面向对象的基本概念



OOA：面向对象分析

OOD：面向对象设计

OOP：面向对象编程

<img src="C:\Users\sun\AppData\Roaming\Typora\typora-user-images\image-20220602114821633.png" alt="image-20220602114821633" style="zoom:33%;" />

### ⭐ 对象

对象，object，现实业务逻辑的一个动作实体就对应着OOP编程中的一个对象！

<img src="C:\Users\sun\AppData\Roaming\Typora\typora-user-images\image-20220602115001960.png" alt="image-20220602115001960" style="zoom: 67%;" />

> ① 对象使用属性（property）保存数据！
>
> ② 对象使用方法（method）管理数据！



### ⭐ 类

对象如何产生？又是如何规定对象的属性和方法呢？

答：==在Python中，采用类（class）来生产对象，用类来规定对象的属性和方法！也就是说，在Python中，要想得到对象，必须先有类！==



为什么要引入类的概念？ 类本来就是对现实世界的一种模拟，在现实生活中，任何一个实体都有一个类别，==类就是具有相同或相似属性和动作的一组实体的集合！==所以，在Python中，对象是指现实中的一个具体的实体，而既然现实中的实体都有一个类别，所以，OOP中的对象也都应该有一个类！



一个对象的所有应该具有特征特性信息，都是由其所属的类来决定的，但是每个对象又可以具有不同的特征特性信息，比如，我自己（人类）这个对象，名字叫老王，性别男，会写代码，会教书；另一个对象（人类）可能叫赵薇，性别女，会演戏，会唱歌！



## 1.类的定义

在Python中，我们可以有两种类的定义方式：

==Python2（经典类）==和 ==Python3（新式类）==

经典类：不由任意内置类型派生出来的类，称之为经典类。

```python
class 类名:
    # 属性
    # 方法
```

新式类：

```python
class 类名():
    # 属性
    # 方法
```

==类名不区分大小写，遵守一般的标识符的命名规则（以字母、数字和下划线构成，并且不能以数字开头），一般为了和方法名相区分，类名的首字母一般大写！（大驼峰法）==



基本语法：

```python
class Person():
    # 属性
    # 方法 (函数)
    def eat(self):
        print('我喜欢吃零食')
    def drink(self):
        print('我喜欢喝可乐')
        
```



## 2.类的实例化（创建对象）

类的实例化就是把抽象的事务具体为现实世界的实体。

==类的实例化就是通过类得到对象==

类只是对象的一种规范，类本身基本上什么都做不了，必须利用类得到对象，这个过程就叫作类的实例化！

基本语法：

```python
对象名 = 类名()
```

>在其他的编程语言中，类的实例化一般是通过new关键字实例化生成的，但是在Python中，我们不需要new关键字，只需要  类名 + ( )   括号就代表类的实例。



案例：把Person类实例化为对象p1

```python
# 1.定义一个类
class Person():
    # 定义相关方法
    def eat(self):
        print('我喜欢吃零食')
    def drink(self):
        print('我喜欢喝可乐')
        
# 2.实例化对象
p1 = Person()

# 3.调用类中的方法
p1.eat()
p1.drink()
```



## 3.类中的self关键字

self也是Python内置的关键字之一，其==指向了类实例对象本身。==

```python
# 1.定义一个类
class Person():
    # 定义一个方法
    def speak(self):
        print(self)
        print('nice to meet you')
        
# 2.类的实例化(生成对象)
p1 = Person()
print(p1)
p1.speak()

p2 = Person()
print(p2)
p2.speak()
```

>总结：类中的self就是谁实例化了对象，其就指向谁。



## 4.对象的属性添加与获取

### ①.什么是属性

在Python中，任何一个对象都应该由两部分组成：属性 +  方法

属性即是特征，比如：人的姓名、年龄、身高、体重…都是对象的属性。

对象属性既可以在类外面添加和获取，也能在类里面添加和获取。



### ②.在类的外面添加属性或获取属性

#### 🌵设置

```python
对象名.属性 = 属性值
```

案例：

```python
# 1.定义一个Person类
class Perosn():
    pass

# 2.实例化Person类，生成p1对象
p1 = Person()
# 3.为p1对象添加属性
p1.name = '斌斌'
p1.age = 18
p1.address = '秦皇岛'
```



#### 🌵获取

在Python中，获取对象属性的方法我们可以通过 ==对象名.属性== 来获取。

```python
# 1.定义一个Person类
class Person():
    pass

# 2.实例化Person类，生成p1对象
p1 = Person()
# 3.为p1对象添加属性
p1.name = '斌斌'
p1.age = 18
p1.address = '秦皇岛'

# 4.获取p1对象的属性
print(f'我的姓名：{p1.name}')
print(f'我的年龄：{p1.age}')
print(f'我的地址：{p1.address}')
```



### ③.在类的内部获取外部定义的属性

```python
# 1.定义一个Person类
class Person():
    def speak(self):
        print(f'我的名字：{self.name}, 我的年龄：{self.age}, 我的地址：{self.address}')
        
# 2.实例化Person类，生成p1对象
p1 = Person()
# 3.添加属性
p1.name = '仙人掌'
p1.age = 18
p1.address = '沙漠'
# 4.调用speak方法
p1.speak()
```





## 5.魔术方法



### ① 什么是魔术方法

在Python中，==_ _ xxx_ _()== 的函数叫做魔法方法，指的是具有特殊功能的函数。

### ② \_ _init\_ _()方法（初始化方法或构造方法）

思考：人的姓名、年龄等信息都是与生俱来的属性，可不可以在生产过程中就赋予这些属性呢？

答：可以，使用\_ _init\_ _()方法，其作用：实例化对象时，连带其中的参数，会一并传给 \_ _init\_ _()函数自动并执行它。\_ _init\_ _()函数的参数列表会在开头多出一项，它永远指代新建的那个实例对象，Python语法要求这个参数必须要有，名称为self。



```python
# 1.定义一个类
class Person():
    # 初始化实例对象属性
    def __init__(self, name, age):
        # 赋予name属性、age属性给实例化对象本身
        # self.实例化对象本身 = 参数
        self.name = name
        self.age = age


# 2.实例化对象并传入初始化属性值
p1 = Person('金沙江', 17)
# 3.调用p1对象自身属性name与age
print(p1.name)
print(p1.age)
```

>① \_ _init\_ _()方法，在创建一个对象时默认被调用，不需要手动调用
>
>② \_ _init\_ _(self)中的self参数，不需要开发者传递，python解释器会自动把当前的对象引用传递过去。
>



### ③ \_ _ str\_ _()方法

当使用print输出对象的时候，默认打印对象的内存地址。如果类定义了\_ _ str\_ _()方法，那么就会打印从在这个方法中 return 的数据。

```python
# 1.定义一个类
class Car():
    # 首先定义一个__init__方法，用于初始化实例对象属性
    def __init__(self, brand, model, color):
        self.brand = brand
        self.model = model
        self.color = color

    # 定义一个__str__内置魔术方法，用于输出car的相关信息
    def __str__(self):
        return f'汽车品牌：{self.brand}, 汽车型号：{self.model}, 汽车颜色：{self.color}'

# 2.实例化对象c1
c1 = Car('五菱宏光', '面包车', '白色')
print(c1)
```

>① _ _str\_ _这个魔术方法是在类的外部，使用print(对象)时，自动被调用的。
>
>② 在类的内部定义 _ _ str_ _方法时，必须使用return返回一个字符串类型的数据。



### ④ _ _ del_ _ ()方法    （删除方法或析构方法）

当删除对象时，python解释器也会默认调用\_ _del\_ _()方法。

```python
class Person():
    # 构造函数__init__
    def __init__(self, name, age):
        self.name = name
        self.age = age

    # 析构方法__del__
    def __del__(self):
        print(f'{self}对象已经被删除')


# 实例化对象
p1 = Person('鱼', 10)

# 删除对象p1
del p1
```



> _ _ del_ _()方法在使用过程中，比较简单，但是其在实际开发中，主要用于关闭文件操作、关闭数据库连接等。



> 总结：
>
> 提到魔术方法：① 这个方法在什么情况下被触发 ② 这个方法有什么实际的作用
>
> _ _ init_ _()：初始化方法或者称之为“构造函数”，在对象初始化时执行，其主要作用就是在对象初始化时，对对象进行初始化操作（如赋予属性）
>
> _ _ str_ _()：对象字符串方法，当我们在类的外部，使用print方法输出对象时被触发，其主要功能就是对对象进行打印输出操作，要求方法必须使用return返回字符串格式的数据。
>
> _ _del _ _()：删除方法或者称之为“析构方法”，在对象被del删除时触发，其主要作用就是适用于关闭文件、关闭数据库连接等等。



## 6.综合案例

案例1：定义学员信息类，包含姓名、成绩属性，定义成绩打印方法（90分及以上显示优秀，80分及以上显示良好，70分及以上显示中等，60分及以上显示合格，60分以下显示不及格）

学员对象（属性、方法）

```python
# 1.定义学员信息类
class Student():
    # 2. 定义学员对象属性
    def __init__(self, name, score):
        self.name = name
        self.score = score
    # 3.定义一个方法，用于打印学员的成绩等级
    def print_grade(self):
        if self.score >= 90:
            print(f'学员姓名：{self.name}, 学员成绩：{self.score}, 优秀')
        elif self.score >= 80:
            print(f'学员姓名：{self.name}, 学员成绩：{self.score}, 良好')
        elif self.score >= 70:
            print(f'学员姓名：{self.name}, 学员成绩：{self.score}, 中等')
        elif self.score >= 60:
            print(f'学员姓名：{self.name}, 学员成绩：{self.score}, 及格')
        else:
            print(f'学员姓名：{self.name}, 学员成绩：{self.score}, 不及格')
            
# 4.实例化对象
tom = Student('tom', 80)
tom.print_grade()

jenny = Student('jenny', 59)
jenny.print_grade()
```





案例2：小明体重75.0公斤，小明每次跑步会减掉0.50公斤，小明每次吃东西体重增加1公斤

分析：① 对象：小明  ② 属性：姓名、体重   ③ 方法：跑步、吃东西

```python
# 1.定义一个Person类
class Person():
    # 2.初始化对象属性，name和weight
    def __init__(self, name, weight):
        self.name =name
        self.weight= weight
        
    # 3.定义一个__str__方法打印对象的信息
    def __str__(self):
        return f'姓名：{self.name}, 目前体重：{self.weight}Kg'
    
    # 4.定义一个run方法代表跑步
    def run(self):
        self.weight -= 0.5
        
    # 5.定义一个eat方法代表吃饭
    def eat(self):
        self.weight += 1
        
# 6.实例化对象
xiaoming = Person('小明', 75.0)
print(xiaoming)

# 7.吃饭
xiaoming.eat()
print(xiaoming)

# 8.减肥跑步
xiaoming.run()
print(xiaoming)
```











# 二、面向对象高级





## ⭐ 面向对象三大特性



面向对象的三大特性：封装、继承、多态



① 封装

将属性和方法书写到类的里面的操作即为封装，封装可以为属性和方法添加私有权限。

② 继承

子类默认继承父类的所有属性和方法，与此同时子类也可以重写父类属性和方法。

③ 多态

多态是同一类事物具有的多种形态。不同的对象调用同一个接口（方法），表现出不同的状态，称为多态。



# 三、Python中的封装

在Python代码中，封装有两层含义：

① 把现实世界中的主体中的属性和方法书写到类里面的操作即为封装。

```python
class Person():
    # 封装属性
    # 封装方法
```

② 封装可以为属性和方法添加私有权限。



## 1. 封装中的私有属性和私有方法

在面向对象代码中，我们可以把属性和方法分为两大类：公有（属性、方法）、私有（属性、方法）

公有属性和公有方法：无论在类的内部还是在类的外部我们都可以对属性和方法进行操作。

但是有些情况下，我们不希望在类的外部对类内部的属性和方法进行操作。我们就可以把这个属性或方法封装成私有形式。



## 2. 私有属性的访问限制



在Python中，可以为实例属性和方法设置私有权限，即设置某个实例属性或实例方法不继承给子类。

设置私有属性和私有方法的方式非常简单：在属性名和方法名 前面 加上两个下划线 "_ _" 即可。

基本语法：

```python
class Girl():
    def __init__(self, name):
        self.name = name
        self.__age = 18
    
xiaomei = Girl('小美')
print(xiaomei.name)
print(xiaomei.__age)       # 报错，提示Girl对象没有__age属性
```

>类中的私有属性和私有方法，不能被其子类继承。

由以上代码运行可知，私有属性不能在类的外部被直接访问。但是出于种种原因，我们想在外部对私有属性进行访问，我们可以定义一个统一的访问“接口”（函数），专门用于实现私有属性的访问。



## 3. 私有属性设置与访问接口

在Python中，一般定义函数名 'get_xx' 用来获取私有属性，定义 'set_xx' 用来修改私有属性值。

```python
class Girl():
    def __init__(self, name):
        self.name = '小美'
        self.__age = 18
    # 公共方法：提供给外部的访问接口    
    def get_age(self):
        # 实际工作中，私有属性的访问还需加工
        return self.__age
    
    # 公共方法：提供给外部的访问接口
    def set_age(self, age):
        self.__age = age


girl = Girl('小美')
girl.set_age(19)
print(girl.get_age())
```



## 4. 私有方法

私有方法的定义方式与私有属性基本一致，在方法名的前面添加两个下划线 ==_ _方法名（）==



## 5. 封装的意义

① 以面向对象的编程思想进行项目开发

② 封装数据属性：明确的区分内外，控制外部对隐藏的属性的操作行为。

```python
class People(object):
    def __init__(self, name, age):
        self.__name = name
        self.__age = age
        
    def tell_info(self):
        print('Name:<%s> Age:<%s>' % (self.__name, self.__age))
        
    def set_info(self, name, age):
        if not isinstance(name, str):
            print('名字必须是字符串类型')
            return
        if not isinstance(age, int):
            print('年龄必须是数字类型')
            return
        self.__name = name
        self.__age = age
        

p = People('jack', 39)
p.tell_info()

p.set_info('jenny', 18)
p.tell_info()

p.set_info(123, 35)
p.tell_info()
```

③ 私有方法封装的意义：降低程序的复杂度。

```python
class ATM:
    def __card(self):
        print('插卡')
    def __auth(self):
        print('用户认证')
    def __input(self):
        print('输入取款金额')
    def __print_bill(self):
        print('打印账单')
    def __take_money(self):
        print('取款')
        
    # 定义一个对外提供服务的公共方法
    def withdraw(self):
        self.__card()
        self.__auth()
        self.__input()
        self.__print_bill()
        self.__take_money()
        
atm = ATM()
atm.withdraw()
```













# 四、Python中的继承



## 1. 什么是继承

类是用来描述现实世界中同一组事务的共有特性的抽象模型，但是类也有上下级和范围之分，比如：生物 => 动物 => 哺乳动物 => 灵长型动物 => 人类 => 黄种人



从哲学上说，就是共性与个性之间的关系，比如：白马和马！所以，我们在OOP代码中，也一样要体现出类与类之间的共性与个性关系，这里就需要通过类的继承来体现。简单来说，如果一个类A使用了另一个类B的成员（属性和方法），我们就可以说A类继承了B类，同时这也体现了OOP中代码重用的特性！

## 2. 继承的基本语法

基本语法：

```python
# 父类B
class B(object):
    pass

#子类A
class A(B):
    pass

a = A()
a.B中的所有公共属性
a.B中的所有公共方法
```

>在Python中，所有类默认继承object类，object类是顶级类或基类；其他子类叫做派生类。

案例：Person类与Teacher、Student类之间的继承关系

```python
class Person(object):
    def eat(self):
        print('i can eat food')
    
    def speak(self):
        print('i can speak')

class Teacher(Person):
    pass

class Student(Person):
    pass

teacher = Teacher()
teacher.eat()
teacher.speak()

student = Student()
student.eat()
student.speak()
```



## 3. 与继承相关的概念

继承：一个类从另一个已有的类获得其成员的相关特性，就叫作继承！

派生：从一个已有的类产生一个新的类，称为派生！

很显然，继承和派生其实就是从不同的方向来描述的相同的概念而已，本质上是一样的！



父类：也叫作基类，就是指已有被继承的类！

子类：也叫作派生类或扩展类



扩展：在子类中增加一些自己特有的特性，就叫作扩展，没有扩展，继承也就没有意义了！

单继承：一个类只能继承自一个其他的类，不能继承多个类，单继承也是大多数面向对象语言的特性！

多继承：一个类同时继承了多个父类， （C++、Python等语言都支持多继承）

## 4. 单继承

单继承：一个类只能继承自一个其他的类，不能继承多个类。这个类会有具有父类的属性和方法。

基本语法：

```python
# 1.定义一个共性类(父类)
class Person(object):
    pass
# 2.定义一个个性类(子类)
class Teacher(Person):
    pass
```

案例：比如汽车可以分为两种类型（汽油车，电动车）

```python
# 1.定义一个共性类
class Car(object):
    def run():
        print('i can run')
# 2.定义汽油车
class GasolineCar(Car):
    pass
# 3.定义电动车
class EletricCar(Car):
    pass

bwm = GasolineCar()
bwm.run()
```



## 5. 单继承特性：传递性

在Python继承中，如A类继承了B类，B类又继承了C类。则根据继承的传递性，则A类也会自动继承C类中的所有属性和方法(公共)。

```python
class C(object):
    def fun(self):
        print('我是C类中的相关方法fun')
        
class B(C):
    pass

class A(B):
    pass

a = A()
a.fun()
```



## 6. 编写面向对象代码中的常见问题

问题1：在定义类时，没有遵循类的命名规则。

在Python中，类理论上是不区分大小写的。但是要遵循一定的命名规范：首字母必须是字母或下划线，其中可以包含字母、数字和下划线，而且要求命名方式采用大驼峰。



问题2：父类一定要继承object吗？

在Python面向对象代码中，建议编写父类时，让其自动继承object类。不写也可以，因为默认情况下，Python中的所有类都继承自object。

<img src="Python面向对象.assets/image-20220611140243688.png" alt="image-20220611140243688" style="zoom: 50%;" />



问题3：打印属性和方法，都喜欢用print

```python
class Person():
    def __init__(self, name):
        self.name = name
        
    def speak(self):
        print('i can speak')
        
# 创建对象，打印属性和方法
p = Person('tom')
print(p.name)
p.speak()
```



## 7. 多继承

Python语言时少数支持多继承的一门编程语言，所谓的多继承就是允许一个类同时继承多个类的特性。

基本语法：

```python
class B(object):
    pass
class C(object):
    pass
class A(B, C):
    pass

a = A()
a.B中的所有属性和方法
a.C中的所有属性和方法
```

案例：汽油车、电动车=>混合动力汽车（汽车+电动）

```python
class GasolineCar(object):
    def run_with_gasoline(self):
        print('i can run with gasolinecar')
        
class EletricCar(object):
    def run_with_eletric(self):
        print('i can run with eletric')
        
class HybirdCar(GasolineCar, EletricCar):
    pass

t = HybirdCar()
t.run_with_gasoline()
t.run_with_eletric()
```

>注意：虽然多继承允许我们同时继承多个类，但是实际开发中，应尽量避免使用多继承，因为如果两个类中出现了相同的属性和方法就会产生命名冲突。



## 8. 子类扩展：重写父类属性和方法

扩展特性：继承让子类继承父类的所有公共属性和方法，但是如果仅仅是为了继承公共属性和方法，继承就没有实际的意义了，应该是在继承以后，子类应该有一些自己的属性和方法。

重写也叫作覆盖，就是当子类成员与父类成员名字相同的时候，从父类继承下来的成员会重新定义！



此时，通过子类实例化出来的对象访问相关成员的时候，真正其作用的是子类中定义的成员！



上面单继承例子中 Animal 的子类 Cat和Dog 继承了父类的属性和方法，但是我们狗类Dog 有自己的叫声'汪汪叫'，猫类 Cat 有自己的叫声 '喵喵叫' ，这时我们需要对父类的 call() 方法进行重构。如下：

```python
class Animal(object):
    def eat(self):
        print('i can eat')

    def call(self):
        print('i can call')


class Dog(Animal):
    pass


class Cat(Animal):
    pass


wangcai = Dog()
wangcai.eat()
wangcai.call()

mao = Cat()
mao.eat()
mao.call()
```

Dog、Cat子类重写父类Aniaml中的call方法：

```python
class Animal(object):
    def eat(self):
        print('i can eat')
    # 公共方法
    def call(self):
        print('i can call')
        
class Dog(Animal):
    # 重写父类方法
    def call(self):
        print('i can wangwang')
        
class Cat(Animal):
    # 重写父类方法
    def call(self):
        print('i can miaomiao')    
        
wangcai = Dog()
wangcai.eat()
wangcai.call()

mao = Cat()
mao.eat()
mao.call()
```

思考一个问题：此时父类中的call方法还在不在？

答：还在，只不过是在其子类中找不到了。类方法的调用顺序，当我们在子类中重构父类的方法后，Cat子类的实例先会在自己的类 Cat 中查找该方法，当找不到该方法时才会去父类 Animal 中查找对应的方法。



## 9. 调用父类属性和方法

super()：调用父类属性或方法，完整写法：==super(当前类名, self).属性或方法()==

在Python3以后版本中，调用父类的属性和方法我们只需要使用 ==super().属性或super().方法名()==

就可以完成调用了。

案例：Car汽车类：GasolineCar汽油车、ElectricCar电动车

```python
class Car(object):
    def __init__(self, brand, model, color):
        self.brand = brand
        self.model = model
        self.color = color
    def run(self):
        print('i can run')
        
class GasolineCar(Car):
    def __init__(self, brand, model, color):
        super().__init__(brand, model, color)
        
    def run(self):
        print('i can run with gasoline')
        
class ElectricCar(Car):
    def __init__(self, brand, model, color):
        super().__init__(brand, model, color)
        # 电池属性
        self.battery = 70
        
    def run(self):
        print('i can run with electric,remain:{self.battery}')

bwm = GasolineCar('宝马', 'X5', '白色')
bwm.run()

tesla = ElectricCar('特斯拉', 'Model S', '红色')
tesla.run()
```



## 10. mro属性或mro方法

MRO(Method Resolution Order)：方法解析顺序，我们可以通过==类名._ _mro\_ _或类名.mro()==获得“类的层次结构”，方法解析顺序也是按照这个“类的层次结构”寻找到。

```python
class Car(object):
    def __init__(self, brand, model, color):
        self.brand = brand
        self.model = model
        self.color = color
    def run(self):
        print('i can run')
        
class GasolineCar(Car):
    def __init__(self, brand, model, color):
        super().__init__(brand, model, color)
        
    def run(self):
        print('i can run with gasoline')
        
class ElectricCar(Car):
    def __init__(self, brand, model, color):
        super().__init__(brand, model, color)
        # 电池属性
        self.battery = 70
        
    def run(self):
        print('i can run with electric,remain:{self.battery}')

print(ElectricCar.__mro__)
print(ElectricCar.mro())
```

![image-20220611152219343](Python面向对象.assets/image-20220611152219343.png)

说明：由MRO方法解析顺序可知，在类的继承中，当某个类创建了一个对象时，调用属性或方法，首先在自身类中去寻找，如找到直接使用，停止后续的查找。如果未找到，继续向上一级继承的类中去寻找，如找到，则直接使用，没有继续向上寻找...直到object类，这就是Python类继承中，其方法解析顺序。

>综上：oject类还是所有类的基类（因为这个查找关系到object才终止）





# 五、Python中的多态

## 

## 1.什么是多态

多态指的是一类事物有多种形态。



定义：多态是一种使用对象的方式，子类重写父类方法，调用不同子类对象的相同父类方法，可以产生不同的执行结果

① 多态依赖继承

② 子类方法必须要重写父类方法

>首先定义一个父类，其可能有多个子类对象。当我们调用一个公共方法时，传递的对象不同，则返回的结果不同。

好处：调用灵活，有了多态，更容易编写出通用的代码，做出通用的编程，以适应需求的不断变化！



## 2. 多态原理图

![image-20220611153731625](Python面向对象.assets/image-20220611153731625.png)

公共接口就是多态的体现，随着传入水果对象的不同，能返回不同的结果。



## 3. 多态代码实现

多态：可以基于继承也可以不基于继承

实现步骤：

- 定义父类，并提供公共方法

- 定义子类，并重写父类方法

- 传递子类对象给调用者，可以看到不同子类执行效果不同

```python
class Fruit(object):
    # 公共方法
    def makejuice(self):
        print('i can make juice')
        
class Apple(Fruit):
    def makejuice(self):
        print('i can make apple juice')
        
class Banana(Fruit):
    def makejuice(self):
        print('i can make banana juice')

class Orange(Fruit):
    def makejuice(self):
        print('i can make orange juice')  
 
# 定义公共方法如service
def service(obj):
    obj.makejuice()

apple = Apple()
banana = Banana()
orange = Orange()

for i in (apple, banana, orange):
    service(i)
```



# 六、面向对象其他属性



## 1. 类属性

Python中，属性可以分为实例属性和类属性。

类属性就是 ==类对象中定义的属性，它被该类的所有实例对象所共有。==通常用来记录 与这类相关 的特征，类属性 不会用于记录 具体对象的特征。

>在Python中，一切皆为对象。类也是一个特殊的对象，我们可以单独为类定义属性。

```python
class Person(object):
    # 定义类属性
    count = 0
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
p1 = Person('tom', 22)
p2 = Person('jack', 33)
```



## 2. 类属性操作

定义count类属性，用于记录实例化Person类，产生对象的数量。

```python
class Person(object):
    # 定义类属性
    count = 0
    # 定义一个__init__魔术方法，用于初始化操作
    def __init__(self, name, age):
        self.name = name
        self.age = age
        # 对count类属性进行+1操作，用于记录这个Person类一共生成了多少个对象
    	Person.count += 1
        
# 1.实例化对象p1
p1 = Person('tom', 22)
p2 = Person('jen', 33)
p3 = Person('amy', 44)
# 2.在类外部输出类的属性count
print(f'我们共使用Person类生成了{Person.count}个对象')
```



## 3. 类方法

类方法就是==针对类对象定义的方法，在类方法中可以直接访问类属性或者调用其他类方法。==

基本语法：

```python
@classmethod
def 类名(cls):
    pass
```



类方法需要用修饰器" ==@classmethod== "来标识，告诉解释器这是一个类方法，类方法的第一个参数应该是" ==cls== "。

① 有哪一个类调用的方法，方法内的" cls "就是哪一个类的引用

② 这个参数和示例方法的第一个参数是"self"类似

③ 提示使用其他名称也可以，不过习惯使用" cls " 通过类名.调用类方法，调用方法时，不需要传递" cls "参数



在方法内部：

① 可以通过"cls."访问类的属性         

② 也可以通过 "cls." 调用其他的类方法

为什么需要类方法，在面向对象中，特别强调数据封装性。所以不建议直接在类的外部对属性进行直接设置和获取。所以我们如果想操作类属性，建议使用类方法。

```python
class Tool(object):
    # 定义一个类属性count
    count = 0
    # 定义一个__init__初始化方法
    def __init__(self, name):
        self.name = name
        Tool.count += 1
    # 封装一个类方法：专门实现对Tool.count类属性进行操作
    @classmethod
    def get_count(cls):           # cls 指向了Tool
        print(f'我们使用Tool类共实例化了{cls.count}个工具')
        
t1 = Tool('斧头')
t2 = Tool('锤子')
t3 = Tool('剪刀')

Tool.get_count()
```

>类方法主要用于操作类属性或类中的其他方法。



## 4. 静态方法



基本语法：

```python
@staticmethod
def 静态方法名():
    pass
```

在开发时，如果需要在类中封装一个方法，这个方法：

① 既不需要访问实例属性或者调用实例方法

② 也不需要访问类属性或者调用类方法

这个时候，可以把这个方法封装成一个静态方法。



```python
# 开发一款游戏
class Game(object):
    # 开始游戏，打印游戏功能菜单
    @staticmethod
    def menu():
        print('1.开始游戏')
        print('2.游戏暂停')
        print('3.退出游戏')
        
# 开始游戏、打印菜单
Game.menu()
```



## 5. 综合案例

需求分析：

设计一个`Game`类

属性：

定义一个类属性`top_score`记录游戏的历史最高分

定义一个实例属性`player_name`记录当前游戏的玩家姓名



方法：

静态方法`show_help`显示游戏帮助信息

类方法`show_top_score`显示历史最高分

实例方法`start_game`开始当前玩家的游戏

实例代码：

```python
class Game(object):
    # 1.定义属性top_score
    top_score = 0
    # 2.定义初始化方法__init__
    def __init__(self, player_name):
        self.player_name = player_name
        
    # 3.定义静态方法，用于输出帮助信息
    @staticmethod
    def show_help():
        print('游戏帮助信息')
    # 4.定义类方法
    @classmethod
    def show_top_score(cls):
        print(f'本游戏历史最高分：{cls.top_score}')
        
    # 5.定义实例方法，start_game()
    def start_game(self):
        print(f'{self.player_name},游戏开始了，你准备好了吗')
        
# 实例化类生成实例对象
mario = Game('tom')
mario.start_game()

# 显示历史最高分
Game.show_top_score()

# 弹出帮助信息
Game.show_
```







# 七、面向对象中的单例模式



## 1. 什么是设计模式

设计模式就是前人根据实际的问题提出的问题解决方案，我们把这种称之为设计模式。



## 2. 单例模式

单例模式是一种常见的设计模式！

所谓的设计模式，不是一种新的语法，而是人们在实际的应用中，面对某种特定的情形而设计出来的某种常见的有效的解决方案，所以，设计模式只是经验的总结！



什么又是单例模式？单例，就是单一实例！

在实际的运用中，存在一些类，只需要实例化一个对象，就可以完成其所有的功能操作。所以，如果我们能够通过某些技巧，使得一个类只能开辟一个对象空间的话，这样就可以节省相应的对象资源，这种模式就叫作单例模式！

![image-20220612100536877](Python面向对象.assets/image-20220612100536877.png)

应用场景：音乐播放器对象、回收站对象、打印机对象

```python
# 定义一个音乐播放器类
class MusicPlayer(object):
    # 初始化方法
    def __init__(self, name):
        self.name = name
        
    # 定义播放音乐方法
    def start(self):
        print('开始播放音乐')
        
# 实例化对象
mp1 = MusicPlayer('明天会更好')
# 调用start方法实现音乐播放
mp1.start()



```

## 3. \_ _new\_ _()方法

使用类名()创建对象时，Python的解释器首先会调用\_ _new\_ _方法为对象分配空间。

__new__是一个由object积累提供的内置的静态方法，主要作用有两个：

○ ==在内存中为对象分配空间==

○ ==返回对象的应用==

Python解析器获得对象的引用后，将引用作为第一个参数，传递给_ _init\_ _方法重写\_ _new\_ _方法的代码非常固定，一定要使用==return super(). \_ _new\_ _(cls)==，否则Python解释器得不到分配了空间的对象引用，就不会调用对象的初始化方法。

>_ _new\_ _方法是一个静态方法，在调用时，要求将自身类信息cls作为参数传递到这个方法中，这个方法就属于object类中的一个静态方法。

案例：

```python
# 定义一个播放器类
class MusicPlayer(object):
    # 重写__new__()魔术方法
    def __new__(cls, *args, **kwargs):
        print('1. 开辟内存空间')
        print('2. 返回实例化对象')
        return super().__new__(cls)
        
    def __init__(self, name):
        self.name = name

# 实例化mp1对象
mp1 = MusicPlayer('红色高跟鞋')
print(mp1)

# 实例化mp2对象
mp2 = MusicPlayer('一路生花')
print(mp2)
```



## 4. 单例模式的代码实现

单例：让类创建的对象，在系统中只有唯一的一个示例

① 定义一个类属性，初始值为None，用于记录单例对象的应用

② 重写_ _new\_ _方法

③ 如果类属性is None，调用父类方法分配空间，并在类属性中记录结果

④ 返回类属性中记录的对象引用

```python
# 定义一个播放器类
class MusicPlayer(object):
    # 定义一个类属性，如instance，用于记录之前实例化对象返回的内存引用
    instance = None
    # 重写__new__()魔术方法
    def __new__(cls, *args, **kwargs):    
        # 判断实例化时有没有分配过内存空间
        if cls.instance is None:
            cls.instance = super().__new__(cls)
        return cls.instance
                       
    def __init__(self, name):
        self.name = name

# 实例化mp1对象
mp1 = MusicPlayer('红色高跟鞋')
print(mp1)

# 实例化mp2对象
mp2 = MusicPlayer('一路生花')
print(mp2)
```

>注意：类属性在内存中是一个特殊的存在，其不用于之前的局部变量(局部变量当函数执行完毕后，其会被内存销毁)。但是类属性一旦定义，除非对象以及这个类在内存中被销毁了，否则其不会自动销毁。







# 八、Python异常



## 1. 什么是异常

当检测到一个错误时，解释器就无法继续执行了，反而出现了一些错误的提示，这就是所谓的"异常"。



## 2. 异常演示

```python
# 运算符
print(10/0)

# 文件异常
f = open('python.txt', 'r')
content = f.readlines()
print(content)
```



## 3. 异常捕获

基本语法：

```python
try:
    可能发生错误的代码
except(捕获):
    如果出现异常执行的代码
```

案例：

````python
try:
    f = open('python.txt', 'r')
    content = f.readlines()
    print(content, end='')
except:
    f = open('python.txt', 'w', encoding='uts-8')
    f.write('发生异常，执行except语句中的代码')
    
f.close()

... 代码可以继续向下执行
````



## 4. 捕获指定异常

在以上案例代码中，except相当于捕获了所有异常，无论遇到什么错误都会自动执行except中封装的代码。但是有些情况下，我们想针对性的捕获异常，并执行相应的代码。

基本语法：

```python
try:
    可能遇到异常的代码
except 异常类型:
    捕获到对应的错误以后，执行的代码
```

>① 如果尝试执行的代码的异常类型和要捕获的异常类型不一致，则无法捕获异常。
>
>② 一般try下方只放一行尝试执行的代码。



案例：捕获FileNotFoundError异常

````python
try:
    f = open('python.txt', 'r')
except FileNotFoundError as e:
    print(e)
````



## 5. 捕获多个异常

当捕获多个异常时，可以把要捕获的异常类型的名字，放到except 后，并使用元组的方式进行书写。

```python
try:
    print(name)
    print(10/0)
except (NameError, ZeroDivisionError) as e:
    print(e)
```



## 6. 捕获所有未知异常

无论我们在except后面定义多少个异常类型，实际应用中，也可能会出现无法捕获的未知异常。这个时候，可以考虑使用Exception异常类型捕获可能遇到的所有未知异常：

```python
try:
    可能遇到的错误代码
except Exception as e:
    print(e)
```

案例：打印一个未定义变量，使用Exception来捕获

```python
try:
    print(name)
except Exception as e:
    print(e)
```



## 7. 异常捕获中的else语句

else表示的是如果没有异常要执行的代码。

```python
try:
    可能出现异常的代码
except Exception as e:
    print(e)
else:
    print('当try语句中的代码没有任何异常时，则else语句中的代码才会执行')
```

案例：

```python
try:
    f = open('python.txt', 'r')
except Exception as e:
    print(e)
else:
    content = f.readlines()
    print(content, end='')
    f.close
```



## 8. 异常捕获中的finally语句

finally表示的是无论是否异常都要执行的代码，例如关闭文件、关闭数据库连接。

```python
try:
    f = open('python.txt', 'r')
except:
    f = open('python.txt', 'w')
else:
    print('没有异常')
finally:
    print('关闭文件')
    f.close()
```



## 9. 异常的综合案例



### ⭐ 异常的传递

需求：① 尝试只读方式打开test.txt文件，如果文件存在则读取文件内容，文件不存在则提示用户即可。

​      ② 读取内容要求：尝试循环读取内容，读取过程中如果检测到用户意外终止程序，则`except`捕获

```python
import time

try:
    f = open('python.txt', 'r')
    try:
        while True:
            content = f.readline()
            if len(content) == 0:
                break
            time.sleep(3)
            print(content, end='')
    except:
        print('python.txt未全部读取完成，中断了...')
	finally:
        f.close()
except:
    print('python.txt未找到...')
```



### ⭐ raise抛出异常

在Python中，抛出自定义异常的语法为`raise 异常类对象`。

需求：密码长度不足，则报异常（用户输入密码，如果输入的长度不足3位，则报错，即抛出自定义异常，并捕获该异常）。

原生方法：

```python
def input_password():
    password = input('请输入您的密码,不少于6位：')
    if len(password) < 6:
        # 抛出异常
        raise Exception('您的密码长度少于6位')
        return
    # 如果密码长度正常，则直接显示密码
    print(password)
    
input_password()
```

![image-20220612115545327](Python面向对象.assets/image-20220612115545327.png)



面向对象抛出自定义异常：

```python
class ShortInputError(Exception):
    # length代表输入密码长度，min_length代表ShortInputError最小长度
    def __init__(self, length, min_length):
        self.length = length
        self.min_length = min_length

    # 定义一个__str__方法，用于输出字符串信息
    def __str__(self):
        return f'您输入的密码长度为{self.length}, 不能少于{self.min_length}个字符'

try:
    password = input('请输入您的密码，不少于6位：')
    if len(password) < 6:
        raise ShortInputError(len(password), 6)
except Exception as e:
    print(e)
else:
    print(f'密码输入完成，您的密码是:{password}')
```









# 九、Python模块



## 1. 什么是模块

Python 模块(Module)，==是一个 Python 文件==，以 .py 结尾，包含了 Python 对象定义和Python语句。==模块能定义函数，类和变量==，模块里也能包含可执行的代码。



## 2. 模块的分类

在Python中，模块通常可以分为两大类：==内置模块== 和 ==自定义模块==



## 3. 模块的导入方式



⭐ import 模块名

⭐ from 模块名 import 功能名

⭐ from 模块名 import *

⭐ import 模块名 as 别名

⭐ from 模块名 import 功能名 as 别名



### 3.1 使用import导入模块

基本语法：

```python
import 模块名称
或
import 模块名称1， 模块名称2，...
```

使用模块中封装好的方法：

```python
模块名称.方法()
```

案例：使用import导入math模块

```python
import math

# 求数字9的平方根
print(math.sqrt(9))
```

案例：使用import导入math与random模块

```python
import math, random

print(math.sqrt(9))
print(random.randint(-100, 100))
```



### 3.2 使用from模块名 import功能名

import代表导入某个或多个模块中的所有功能，但是有些情况下，我们只希望使用这个歌模块下的某些方法，而不需要全部导入，这个时候建议采用 from 模块名 import 功能名

⭐ from 模块名import *

这个导入方法代表导入这个模块的所有功能（等价于import模块名）

案例：

```python
from math import *
```

案例：

```python
from math import sqrt, floor
```

注意：以上两种方式都可以用于导入某个模块中的某些方法，但是调用具体的方法时，我们只需要==功能名（）==即可

```python
功能名()
```



案例：

```python
# from math import *
# 或
from math import sqrt, floor

# 调用方式
print(sqrt(9))
print(floor(10.88))
```



### 3.3 使用as关键字为导入模块定义别名

在有些情况下，如导入的模块名称过长，建议使用as关键字对其重命名操作，以后在调用这个模块时，我们就可以使用别名进行操作。

```python
import time as t

# 调用方式
print('python')
t.sleep(3)
print('linux')
```

>在Python中，如果给模块定义别名，命名规则建议使用大驼峰。



### 3.4 使用as关键字为导入功能定义别名

```python
from 模块 import 功能名 as 功能名别名
```

案例：

````python
from time import sleep as sl, time as t

# 调用方式
print('python')
sl(3)
print('linux')
````



### 3.5. 扩展：time模块中的time()方法

在Python中，time模块除了sleep方法以外，还有一个方法叫time（）方法

```python
time.time()
```

主要功能：就是返回格林制时间到当前时间的秒数



案例：求运行递归代码的执行时间

```python
import time

# 返回格林制时间到当前时间的秒数
start = time.time()
print(start)

# 编写递归函数
def fun(n):
    if n == 10:
        return 1
    return (fun(n+1) + 1) * 2

print(fun(1))

end = time.time()
print(f'以上代码共执行了{end - start}s')
```



## 4. Python中的自定义模块

### 4.1 什么是自定义模块

在Python中，模块一共可以分为两大类：内置系统模块和自定义模块

模块的本质：在Python中，模块的本质就是一个Python的独立文件(后缀名.py)，里面可以包含全局变量、函数以及类。

> 在Python中，每个Python文件都可以作为一个模块，模块的名字就是文件的名字。也就是说自定义模块名必须要符合标识符命名规则。



### 4.2 定义一个自定义模块

案例：在Python项目中创建一个自定义文件,如my_module.py

```python
# 定义一个功能，用于求两个数的和
def sum_num(num1, num2):
    return num1 + num2
```



### 4.3 导入自定义模块

```python
import 模块名称
或
from 模块名称 import 功能名
```

案例：

```python
import my_module

# 调用my_module模块中自定义的sum_num方法
print(my_module.sum_num(10, 20))
```



### 4.4 自定义模块中功能测试

在我们编写完自定义模块以后，最好在模块中对代码进行提前测试，防止异常

引入一个魔术方法：`__name__`其保存的内存就是一个字符串类型的数据。

随着运行页面的不同，其返回结果也是不同的：

① 如果`__name__`是在当前页面运行时，其返回结果为`__main__`

② 如果`__name__`在第三方页面运行时，其返回结果为模块名称

基于以上特性，我们可以把`__name__`编写在自定义模块中，语法如下：

```python
if __name__ == '__main__':
    # 执行测试代码
```

`__name__`魔术方法除了可以在自定义模块中使用，还可以用于编写程序的入口：

```python
# 定义一个main方法(入口)
def main():
    # 执行我们要执行的功能
    
# 调用执行入口
if __name__ == '__main__':
    main()
```



### 4.5 多模块中功能命名冲突问题

当我们编写了多个模块时，可能在导入到其他页面时，会产生一个问题：全局变量、函数、类出现重名情况，我们把这种情况称为“命名冲突”。

如导入my_module2和my_module3，里面都封装了一个fun()方法，其在导入后，my_module3中的fun()方法就会覆盖my_module2中的fun()方法。

my_module2.py:

```python
def fun():
    print('my_module2中的fun方法')
```

my_module3.py:

```python
def fun():
    print('my_module3中的fun方法')
```

导入到其他Python文件中，测试效果：

````python
from my_module2 import fun
from my_module3 import fun

# 调用fun方法
fun()
````

⭐ **解决方案：**

① 把所有模块的导入方式都写入文件的最上面，如果发现命名冲突了，马上进行功能核对

② 给重名的方法进行 as 重命名

```python
from my_module2 import fun as my_module2_fun
from my_module3 import fun as my_module3_fun

my_module2_fun()
my_module3_fun()
```



### 4.6 模块命名的注意事项

在实际项目开发中，一定要特别注意：我们自定义的模块名称一定不能和系统内置的		模块名称相同，否则会导致代码无法正常执行。



### 4.7 \_ _all\_ _魔术方法

如果一个模块文件中有`__all__`变量，当使用`from xxx import *`导入时，只能导入这个列表中的元素。

主要功能：限制使用模块中的某些功能，也就是说你导入后可以使用的方法只能是`__all__`中封装好的方法。

案例：

my_module.py

````python
__all__ = ['fun1']

def fun1():
    print('fun1方法')
    
def fun2():
    print('fun2方法')
````

限制引用模块中的方法：

```python
from my_module import *

fun1()
fun2()  # 报错
```







# 十、Python中的包



## 1. 什么是包

包将有联系的模块组织在一起，即放到同一个文件夹下，并且在这个文件夹创建一个名字为`__init__.py` 文件，那么这个文件夹就称之为包。



## 2. 包的制作

![image-20220612163341785](Python面向对象.assets/image-20220612163341785.png)

![image-20220612163642545](Python面向对象.assets/image-20220612163642545.png)

>注意：新建包后，包内部会自动创建`__init__.py`文件，这个文件控制着包的导入行为。



## 3. 在包中创建多个模块

在mypackage包中创建多个模块：my_module1和my_module2

my_module1.py:

```python
print('my_module1')
def fun1():
    print('mypackage包中的my_module1模块中的fun1方法')    
```

my_module2.py:

```python
print('my_module1')
def fun2():
    print('mypackage包中的my_module2模块中的fun2方法')   
```



## 4. 在项目代码中导入包Package

方法一：使用import导入包

```python
import 包名.模块名

# 调用模块中的方法
包名.模块名.方法名()
```

方法二：使用from导入包

```python
from 包名 import 模块名

# 调用模块方法
模块名.方法名()
```

>注意：必须在`__init__.py`文件中添加`__all__ = [] `控制允许导入的模块列表。

