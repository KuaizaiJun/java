# java

## Atom

Sitting-核心设置-title bar-hidden

好家伙, 我一直下载不了jdk 15.0.1

整了十几分钟发现变成15.0.2了

原来是在更新包

## java编程基础

文件名跟主函数名必须一致

类： class Hello

方法/函数：main(method)

语句：System.out.println("Hello Java!");

常量：final double PI = 3.14;

引用类型：String s = "hello";

>引用类型的变量类似于C语言的指针，它内部存储一个“地址”，指向某个对象在内存的位置。

运算：精确度、溢出，溢出会被允许却不出错；

```math
要解释上述结果，我们把整数2147483640和15换成二进制做加法：

  0111 1111 1111 1111 1111 1111 1111 1000
+ 0000 0000 0000 0000 0000 0000 0000 1111
-----------------------------------------
  1000 0000 0000 0000 0000 0000 0000 0111
由于最高位计算结果为1，因此，加法结果变成了一个负数。
```

简写的运算符，即+=，-=，*=，/=，自增/自减 ++运算和--运算.

移位运算

```java
int n = 1;
int a = n << 1; //a = 2  相当于 n * 2^1
int b = n << 4; //b = 16 相当于 n * 2^4
```

位运算：与 或 非 异或  & | ~ ^

强制转型

```java
int n1 = (int) 12.3; // 12
```

布尔运算是一种关系运算，包括以下几类：

比较运算符：>，>=，<，<=，==，!=

与运算 &&

或运算 ||

非运算 !

短路运算

布尔运算的一个重要特点是短路运算。如果一个布尔运算的表达式能提前确定结果，则后续的计算不再执行，直接返回结果。

三元运算符

Java还提供一个三元运算符b ? x : y，它根据第一个布尔表达式的结果，分别返回后续两个表达式之一的计算结果。

字符串类型

常见的转义字符包括：

\" 表示字符"  
\' 表示字符'  
\\ 表示字符\  
\n 表示换行符  
\r 表示回车符  
\t 表示Tab  
\u#### 表示一个Unicode编码的字符

字符串连接: 可以使用+连接任意字符串和其他数据类型

多行字符串: 可以用"""..."""表示多行字符串（Text Blocks）, 多行字符串前面共同的空格会被去掉

```java
        String s = """
                   SELECT * FROM
                     users
                   WHERE id > 100
                   ORDER BY name DESC
                   """;
```

字符串不可变, 观察执行结果，难道字符串s变了吗？其实变的不是字符串，而是变量s的“指向”。

数组: 是引用类型, 长度不可改变, 通过指针指向新的数组(地址)

```java
int[] ns = new int[] { 68, 79, 91, 85, 62 };
int[] ns = { 68, 79, 91, 85, 62 };
```

字符串数组:

```java
String[] names = {
    "ABC", "XYZ", "zoo"
};
names[1] = "cat";
```

## 流程语句

输入和输出: 格式化输出 ("%.2f", d);

### 输入

```java

        Scanner scanner = new Scanner(System.in); //创建Scanner对象, 并传入Syste.in
        String name = scanner.nextLine();
        int    age  = scanner.nextInt();
```

if语句的基本语法是：

```java
if (条件0) {
    System.out.printf("\n");
} else if (条件1) {
    System.out.printf("\n");
} else {
    System.out.printf("\n");
}
```

判断double类型是否相等

```java
    Math.abs(x - 0.1) < 0.00001 //绝对值
```

判断基本类型是否相等可以使用 == 运算符

判断引用类型是否相等,比如String类型, 用 == 表示是否指向同一个对象, 用equals()方法判断String内容是否相等.

```java
s1.equals(s2)
s1 != null && s1.equals("hello")  //使用短路运算符避免s1为null报错
```

switch表达式

```java
        String fruit = "apple";
        switch (fruit) {
        case "apple" -> System.out.println("Selected apple");
        case "pear" -> System.out.println("Selected pear");
        case "mango" -> {
            System.out.println("Selected mango");
            System.out.println("Good choice!");
        }
        default -> System.out.println("No fruit selected");
        }
```

```java
        String fruit = "apple";
        int opt = switch (fruit) {
            case "apple" -> 1;
            case "pear", "mango" -> 2;
            default -> 0;
        }; // 注意赋值语句要以;结束
        System.out.println("opt = " + opt);
````

while条件循环, 注意循环条件的判断

```java
while (条件表达式) {
    循环语句
}
// 继续执行后续代码
```

do while循环

```java
        do {
            执行循环语句
        } while (条件表达式);
```

for循环

```java
        for (初始条件; 循环检测条件; 循环后更新计数器) {
           // 执行语句
}
```

for each循环，它可以更简单地遍历数组：遍历所有“可迭代”的数据类型, List、Map等  
在for (int n : ns)循环中，变量n直接拿到ns数组的元素，而不是索引。

```java
        int[] ns = { 1, 4, 9, 16, 25 };
        for (int n : ns) {
            System.out.println(n);
```

break语句跳出当前循环

```java
            if (i == 100) {
                break;
            }
```

continue则是提前结束本次循环，直接继续执行下次循环

```java
            if (i % 2 == 0) {
                continue; // continue语句会结束本次循环
            }
```

## 数组操作

遍历数组: for循环, for each,

打印数组: 打印地址, Arrays.toString()

数组排序: 冒泡排序

```java

                if (ns[j] > ns[j+1]) {
                    // 交换ns[j]和ns[j+1]:
                    int tmp = ns[j];
                    ns[j] = ns[j+1];
                    ns[j+1] = tmp;
                }
```

Java的标准库已经内置了排序功能 Arrays.sort()

二维数组

```java

        int[][] ns = {
            { 1, 2, 3, 4 },
            { 5, 6, 7, 8 },
            { 9, 10, 11, 12 }
        };
```

要打印一个二维数组，可以使用两层嵌套的for循环：

```java
for (int[] arr : ns) {
    for (int n : arr) {
        System.out.print(n);
        System.out.print(', ');
    }
    System.out.println();
}
```

## 面向对象编程

基本概念:  
类
实例
方法

实现方式:  
继承
多态

Java语言本身提供的机制:  
package
classpath
jar

核心类:  
字符串
包装类型
JavaBean
枚举
常用工具类

完全可以理解并掌握面向对象的基本思想

类（class）(抽象,归类), 实例（instance）(具体)  
class Person { };---------Person ming = new Person()  
class Book { }------------Book book1 = new Book()

创建实例

```java
Person ming = new Person();
```

注意区分Person ming是定义Person类型的变量ming，  
而new Person()是创建Person实例。

使用方法（method）来让外部代码可以间接修改private field：  
外部代码可以调用方法setName()和setAge()来间接修改private字段。  
通过getName()和getAge()间接获取private字段的值。

调用方法的语法是实例变量.方法名(参数);。例如：ming.setName("Xiao Ming");。

定义方法

```java
修饰符 方法返回类型 方法名(方法参数列表) {
    若干方法语句;
    return 方法返回值;
}
```

this变量 指向当前实例

this.field 访问当前实例的字段

当局部变量和字段重名，那么局部变量优先级更高

方法的参数

预设 调用方法的参数变量

可变参数

```java
    public void setNames(String... names) {
        this.names = names;
    }
```

基本类型参数的传递，是调用方值的复制。

引用类型参数的传递，调用方的变量，和接收方的参数变量，指向的是同一个对象。

构造方法

初始化方法

```java
Person ming = new Person();
ming.setName("小明");
ming.setAge(12);
```

由于构造方法是如此特殊，所以构造方法的名称就是类名。构造方法的参数没有限制，在方法内部，也可以编写任意语句。但是，和普通方法相比，构造方法没有返回值（也没有void），调用构造方法，必须用new操作符。

```java
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
```

如果既要能使用带参数的构造方法，又想保留不带参数的构造方法，那么只能把两个构造方法都定义出来：

```java
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
```

多构造方法  
可以定义多个构造方法，在通过new操作符调用的时候，编译器通过构造方法的参数数量、位置和类型自动区分：

一个构造方法可以调用其他构造方法，这样做的目的是便于代码复用。调用其他构造方法的语法是this(…)：

有参数有所不

继承

首先可以复用代码

子类无法访问父类的private字段或者private方法。

用protected修饰的字段可以被子类访问, 把字段和方法的访问权限控制在继承树内部

任何class的构造方法，第一行语句必须是调用父类的构造方法。

向上转型

Person p = new Student(); // ???

多态

在继承关系中，子类如果定义了一个与父类方法签名完全相同的方法，被称为覆写（Override）。

引用变量的声明类型可能与其实际类型不符，例如：

Person p = new Student();

Java的实例方法调用是基于运行时的实际类型的动态调用，而非变量的声明类型。

## 上面的错了

## 面向对象基本概念

人 -> 抽象 -> 类 class  
小明 -> 具体的人 -> 实例 instance  
书 -> 抽象 -> 类 class  

### 创建一个类 -- 包含定义字段 field , 控制语句

```java
class Person {
    public String name;
    public int age;
}

class Book {
    public String name;
    public String author;
    public String ISBN;
    public double price;  //价格
}
```

### 创建实例 -- 然后定义变量指向该实例

new 创建实例  
var 定义引用变量指向该实例

注意等式 = 语句的逻辑顺序, 是先运算右边的, 再赋值左边的;

### 访问变量 -- 对实例赋值

```java
ming.name = "小明";
ming.age = 12;
```

## 方法 method

### 封装字段 -- 拒绝外部直接访问

```java
public int age;  //允许外部访问
private String name;  //拒绝外部访问
```

### 使用方法 method 间接访问, 修改字段 field

```java
private String name;

public String getName(){  //返回 return 字符串引用类型
    return this.name;  //this指向本类, name是类的字段
}

public void setName(String name){
    this.name = name;
}

### 调用语法 实例.方法(参数);

### 定义方法

```java
访问类型 返回类型 方法名 (传入参数列表) {
    语句;
    return 返回;
}
```

private 方法

### this 变量

局部变量与字段重名, 此时,局部变量优先级更高, 要访问字段就要加上this

this.name = name  //前面访问字段, 后面访问局部变量

### 方法参数

按照定义顺序, 一一传递

### 可变参数

```java
class Group {
    private String[] names;
u
    public void setNames(String... names) {
        this.names = names;
    }
}
```

调用时

```java
Group g = new Group();
g.setNames("Xiao Ming", "Xiao Hong", "Xiao Jun"); // 传入3个String
g.setNames("Xiao Ming", "Xiao Hong"); // 传入2个String
g.setNames("Xiao Ming"); // 传入1个String
g.setNames(); // 传入0个String
```

基本类型参数的传递，是调用方值的复制。双方各自的后续修改，互不影响。

引用类型参数的传递，调用方的变量，和接收方的参数变量，指向的是同一个对象。双方任意一方对这个对象的修改，都会影响对方（因为指向同一个对象嘛）。

传入字符串: p.setName(bob)  // p.name -> "Bob"

传入字符串数组: p.setName(fullname); //p.name[0] -> fullname[0] -> "Homer"

## 构造方法

在主类创建实例时, 初始化实例的字段

未调用方法时, 字段状态不正确

创建实例时通过构造方法初始化实例

```java
public Person(String name, int age) {
    this.name = name;
    this.age = age;
}
```

构造方法名是类名, 没有返回值, 调用构造方法, 必须用new操作符

### 多构造方法

通过 new 创建方法的时候, 通过构造方法的参数数量, 位置和类型自动区分;

```java
class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Persong(String name) {
        this.name = name;
        this.age = 12;
    }

    public Person() {
    }
}
```

this 代表了 本方法名

```java
class Person {
    private String name;
    private int age;

    public Person(Sting name, int age) {
        this.name = name;
        this.age = age;
    }

    public Person(Sting name) {
        this(name, 18);
    }

    public Person() {
        this.("Unname");
    }
}
```

## 方法重载 --参数不一样, 方法名相同, 返回类型通常相同

```java
class Hello {
    public void hello() {
        System.out.println("hello, world!");
    }

    public void hello(String name) {
        Systen.out.println("hi, " + name + "!");
    }

    public void hello(String name, int age) {
        if(age < 18) {
            System.out.println("hello, " + name + "!");
        } else {
            System.out.println("hi, " + name + "!");
        }
    }
}
```

## 继承 --复用代码 extends

```java
class Person {
    private String name;
    private int age;
    
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

class Student extends Person {
    private int score;

    public void setScore(int score) {
        this.score = score;
    }

    public int getScore() {
        return score;
    }
}
```

Student extends Person extends Object;

protected 修饰的字段 可以被子类访问;

### super 关键字 表示父类方法名, 用来访问父类字段

在构造方法 (与类名相同的方法, 无返回值) 中, 第一行自动添加为super();

子类不继承父类的构造方法

### 阻止继承 final class

### 指定继承 

```java
public sealed class Person permits Student, Teacher {

}
```

### 向上转型  --子类实例声明为父类 父类引用变量指向子类的实例

String s = s;

### 向下转型

```java
Person p = new Student();
Student s = (Student) p;
```

### 区分继承和组合

### 多态 Polymorphic

在继承关系中, 子类定义了定义了一个与父类方法 完全相同 的方法,被称为覆写 override, 方法名相同, 参数不同,则称为重载 overload

```java
class Person {
    public void run() {
        System.out.println("Person.run");
    }
}
```

```java
class Student extends Person {
    @Override
    public void run() {
        System.out.println("Student.run");
    }
}
```

Java的实例方法调用是基于运行时的实际类型的动态调用，而非变量的声明类型。这就是多态

## 多态

针对某个类型的方法调用，其真正执行的方法取决于运行时期实际类型的方法。多态的特性就是，运行期才能动态决定调用的子类方法。对某个类型调用某个方法，执行的实际方法可能是某个子类的覆写方法。

多态具有一个非常强大的功能，就是允许添加更多类型的子类实现功能扩展，却不需要修改基于父类的代码。

加上@Override可以让编译器帮助检查是否进行了正确的覆写。

## 覆写 Object方法

所有的类 class 最终都继承自Object, 而Object定义了几个重要的方法:

toString(): 把实例 instance输出为String;

equals(): 判断两个instance是否逻辑相等;

hashCode(): 计算一个instance的哈希值

## 调用super

```java
        class Person {
            protected String name;
            public String hello() {
                return "Hello, " + name;
            }
        }

        Student extends Person {
            @Override
            public String hello() {
                return super.hello() + "!";
            }
        }
```

final 修饰的方法不能被覆写 Override:

```java
        class Person {
            protected String name;
            public final String hello() {
                return "Hello, " + name;
            } 
        }

        class Student extends Person {
            @Override
            public String hello() {
            }
        }
```

final 修饰的类不能被继承:

```java
        final class Person {
            protected String name;
        }

        class Student extends Person {
        }
```

final 修饰的字段在初始化后不能被修改.

class Person {
    public final String name = "Unnamed"
}

可以在构造方法中初始化final字段:

```java
        class Person {
            protected final String name;
            public setPersonName(String name) {
                this.name = name;
            }
        }
```

