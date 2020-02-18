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
String创建后不能修改，所以在内存中可以被共享  
java.lang.String不需要导入 
构造方法：String(char[] value)/String(byte[] bytes)使用平台的默认字符集解码当前参数中的字节数组来构造新的
String    
```
String str = "abc";
相当于：
char data[] = {'a', 'b', 'c'};
String str = new String(data);
```
