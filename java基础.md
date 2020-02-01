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

Java中纯整数计算结果必为纯整数; Java中True False 不能用0和1表示  
数据类型 变量名 = 布尔类型表达式？结果1：结果2 
s+=1 仅进行**一次**运算，且**赋值运算符自带类型转换**，而s=s+1只进行**两次**运算，必须写明类型转换  
## 方法
方法定义不能嵌套--**【和python不同！！！】**


