### Scanner 类
解析基本类型和字符串的简单文本扫描器,一个scanner对象可以接受多次输入，注意**System.in**参数  
**nextInt:将下一个输入解析为int**
```
import java.util.Scanner;
public class Test01Scanner {
  public static void main(String[] args) {
  // 创建对象
  Scanner sc = new Scanner(System.in);
  // 接收数据
  System.out.println("请输入第一个数据：");
  int a = sc.nextInt();
  System.out.println("请输入第二个数据：");
  int b = sc.nextInt();
  // 对数据进行求和
  int sum = a + b;
  System.out.println("sum:" + sum);
  }
}
```
或者可以直接使用匿名对象  
```
new Scanner(System.in).nextInt();
```
此时一个对象只能接受一次输入，如果重复输入需要定义多个对象，浪费内存  
匿名对象可以作为方法的参数和返回值  
### Random 类
生成伪随即数
```
import java.util.Random;

Random r = new Random();
int number = r.nextInt(100) + 1;
//nextInt(n):生成0～n-1随机数
```
### ArrayList 类
普通创建数组: Student[] students = new Student[3];  
ArrayList: 大小可变的数组  java.util.ArrayList <E>,此处<E>为泛型，用引用数据类型替换，不能存基本数据类型如int/char/float/double/short/byte,但可以存储其对应的包装类型Integer/Character/Short/Double/Float/Byte等。  
包装类（引用类型，包装类都位于java.lang包下）  
```
import java.util.ArrayList
构造方法 public ArrayList() ：构造一个内容为空的集合。
ArrayList<String> list = new ArrayList<String>();
list.add("abc"); //add方法添加元素至尾部
list.remove(1); //删除index=1位置的元素
list.get(1); //获取index=1的元素
list.size(); //获取size
```
### String 类
- String创建后不能修改，所以在内存中可以被共享  
- java.lang.String不需要导入   
- 构造方法：String(char[] value)/String(byte[] bytes)使用平台的默认字符集解码当前参数中的字节数组来构造新的
String   
- 字符串常量池：程序当中直接写上的双引号字符串，就在字符串常量池中。
- 对于基本类型来说，==是进行数值的比较。
- 对于引用类型来说，==是进行**【地址值】**的比较
```
String str = "abc";
相当于：
char data[] = {'a', 'b', 'c'};
String str = new String(data);
相当于：
byte bytes[] = { 97, 98, 99 };
String str3 = new String(bytes);
```
1. s1.equals(s2) 字符串是否一样--考虑大小写
2. s1.equalsIgnoreCase(s2) 忽略大小写
3. s.length()
4. s.concat(s2)
5. s.charAt(index) 指定索引处的 char值
6. s.indexOf(substr) 子字符串第一次出现在该字符串内的索引
7. s.substring(beginIndex,endIndex)  
8. s.toCharArray ()
9. s.getBytes ()
10. s.replace("it", "IT") 所有出现的都替换
11. s.split("|")
### Static
`spublic static int numberOfStudent = 0;`设定变量为类变量，即所有该类对象共享同一个类变量值，任何对象都可以更改
该类变量的值，也可以在不创建该类的对象的情况下对类变量进行操作   
`public static void showNum()`定义静态方法  
   - 静态方法只能访问静态成员【静态方法+类变量】。
   - 静态方法不能直接访问普通成员变量或成员方法。反之，成员方法可以直接访问类变量或静态方法。
   - 静态方法中，不能使用this关键字。
   - 通过**类名.静态成员名**访问，而不是对象名.静态成员名   
static成员随着类的加载而加载，且只加载一次。栈内存中是对象地址，对象本身存在堆内存，有静态标记指向方法区内固定的静态区   
##### 静态代码块
给类变量进行初始化赋值，随着类的加载而执行且执行一次，优先于main方法和构造方法的执行
```
public class Game {
  public static int number;
  public static ArrayList<String> list;
  static {
    // 给类变量赋值
    number = 2;
    list = new ArrayList<String>();
    // 添加元素到集合中
    list.add("张三");
    list.add("李四");
    }
}
```
**Static主要目的还是想在不创建对象的情况下，去调用方法,例如java.util.Arrays中有操作数组的静态方法，Arrays.toString(arr);Arrays.sort(arr);等**  
### Math 类
java.lang.Math
Math.abs(int)/ceil/floor/round

