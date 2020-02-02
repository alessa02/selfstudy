- JVM
   1. 依靠JVM实现跨平台
   1. JVM本身不跨平台，各平台有各自JVM
- JRE (Java Runtime Environment)：JVM+核心类库
- JDK (Java Development Kit)：JRE+开发工具
- 命名：下划线/字母开头
   1. 类名规范：首字母大写，后面每个单词首字母大写（大驼峰式）。
   1. 方法名规范： 首字母小写，后面每个单词首字母大写（小驼峰式）
   1. 变量名规范：全部小写
   
[mark down table 生成](http://tablesgenerator.com/markdown_tables)

| 数据类型     | 关键字         | 内存占用 | 取值范围               |
|--------------|----------------|----------|------------------------|
| 字节型       | byte           | 1个字节  | -128~127               |
| 短整型       | short          | 2个字节  | -32768~32767           |
| 整型         | int（默认）    | 4个字节  | -231次方~2的31次方-1   |
| 长整型       | long           | 8个字节  | -2的63次方~2的63次方-1 |
| 单精度浮点数 | ﬂoat           | 4个字节  | 1.4013E-45~3.4028E+38  |
| 双精度浮点数 | double（默认） | 8个字节  | 4.9E-324~1.7977E+308   |
| 字符型       | char           | 2个字节  | 0-65535                |
| 布尔类型     | boolean        | 1个字节  | true，false            |

小数一律默认double,float要在末尾加f,如float a=4.4f--**【和python不同】**  
*****
数据类型转换：  
- 自动小范围转为大范围 byte、short、char‐‐>int‐‐>long‐‐>float‐‐>double
   - 损失精度
- 强制 int i = (int)1.5; 浮点型转整型直接抹小数点; 整型转short 4字节去掉前两个字节
   - 数据错误，尽量不要大-->小
- ascii: 
```int a='a';
//char转int
char b = 97;
//int转char
System.out.print((char)Integer.parseInt(str));
//数字字符串转char
byte[] bytestr = str.getBytes();
//字符串转对应编码byte数组
```
[getBytes()](https://blog.csdn.net/qq_38922435/article/details/80639621)

1. Java中纯整数计算结果必为纯整数; Java中True False 不能用0和1表示  
1. 数据类型 变量名 = 布尔类型表达式？结果1：结果2;**必须同时保证结果1和2都符合左侧数据类型的要求。** 
1. s+=1 仅进行**一次**运算，且**赋值运算符自带类型转换**，而s=s+1只进行**两次**运算，必须写明类型转换  
1. 若byte/short/char三种类型变量等号右侧赋值的数值没有超过范围，那么javac编译器将会自动隐含地为补上(byte)(short)(char)。如果右侧超过了左侧范围，那么直接编译器报错。因为常量可预测和判定范围，所以能够直接判定/报错，变量不能预测范围，所以
   ```
   byte b1=1;
   byte b2=2;
   byte b4=b1 + b2;
   //会报错，因为无法判断两个常量相加结果是否仍在byte范围内
   ```
1. byte/short/char这三种类型在运算的时候，都会被首先提升成为int类型，然后再计算。
1. boolean类型不能发生数据类型转换
1. +只有针对char和数字时会强制转为int,str中时字符串连接
1. ''只用于char,""只用于string  
**********
1. if...else if ...else  
2. switch  
switch语句中，表达式的数据类型，可以是byte，short，int，char，enum（枚举），JDK7后可以接收字符串  
执行case后，如果该case没有break，程序会一直向后走，不继续判断case直接执行直到下一个break  
```
switch(表达式) {
case 常量值1:
语句体1;
break;
case 常量值2:
语句体2;
break;
...
default:
语句体n+1;
break;
}
```
3. while{}
4. do{}while
5. for循环第一个表达式必须是变量赋值表达式，不能是纯数字或者变量  
在循环体外部定义且初始化的变量出了循环还可以继续使用，否则会被回收内存  
break只能跳出一层循环，跳出多层循环有三种方法，其中第一种最常用
```
       System.out.println("---------java中跳出多重循环的三种方式：---------");  
       System.out.println("---------第一种，使用带有标号的的break语句---------");  
       String a1 = "";  
       String b1 = "";  
       here:  
       for (int i = 1; i <= 4; i++) {  
           a1 = "外层循环第"+i+"层";  
           for (int j = 1; j <= 4; j++) {  
               b1 = "内层循环第"+j+"层";  
               if (2 == j & 2 == i) {  
                   break here;  
               }  
           }  
       }  
       System.out.println(a1+b1);  
       System.out.println("---------第二种，外层的循环条件收到内层的代码控制限制---------");  
       String a2 = "";  
       String b2 = "";  
       Boolean state =  true;  
       for (int i = 1; i <= 4 && state; i++) {  
           a2 = "外层循环第"+i+"层";  
           for (int j = 1; j <= 4 && state; j++) {  
               b2 = "内层循环第"+j+"层";  
               if (2 == j & 2 == i) {  
                   state = false;  
               }  
           }  
       }  
       System.out.println(a2+b2);  
       System.out.println("---------第三种，使用try/catch强制跳出循环---------");  
       String a3 = "";  
       String b3 = "";  
       try {  
           for (int i = 1; i <= 3; i++) {  
               a3 = "外层循环第"+i+"层";  
               for (int j = 1; j <= 3; j++) {  
                   b3 = "内层循环第"+j+"层";  
                   if (2 == j & 2 == i) {  
                       throw new Exception();  
                   }  
               }  
           }  
       } catch (Exception e) {  
           System.out.println(a3+b3);  
       }  
       System.out.println("---------java中跳出多重循环的两种方式---------");  
```
## 方法
方法定义不能嵌套--**【和python不同！！！】**  
函数回传值可以不用变量接着，直接用来参与计算或者if判断--**【和python相同】**    
#### 方法重载

