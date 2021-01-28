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

