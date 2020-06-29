## 一、Java入门

1. 优势：跨平台、可移植性
2. 高性能、面向对象、简单性、分布式、多线程、健壮性
3. 第一个Java例子
```java
	public static void main(String[] args){
	/*
	1.main方法，是一个程序执行的入口，每次程序执行都从这个方法开始。对于这个特殊的方法主要有两个特点：
		（1）格式固定
		（2）被jvm识别和调用
	2.public：因为权限必须是最大的。它是访问修饰符之一
	3.static：不需要对象，直接用主函数所属类名调用即可。static关键字，被它修饰的方法叫静态方法。
	4.void：表明main方法没有具体的返回值。
	5.Stringp[] args：这是main方法的参数列表，是一个数组类型的参数，而且元素都是字符串类型的。
	6.arg是arguments的缩写。
	*/
		System.out.println("我是videjin，大家好！");
		//这句话是非必须的，输出语句，作用只是在控制台打印这么一句话。
	}
	
```
4. java的终端（命令行）编译
   （1） dos命令 cd 打开Java文件所在目录
   （2）编译文件：javac xxx.java
   （3）运行文件：java xxx
   
   >编译文件生成xxx.class文件，就是运行时的文件，在bin目录中。

## 二、注释

>注释不会被执行，Java中有三种类型注释
1. 单行注释
	+ " // "开头，之后内容
2. 多行注释
	+ 以" /\* " 开头，以" \*/ "结尾
	+ 不可嵌套（无意义）
	+ 可做行内注释
3. 文档注释
	+ 以" /\*\* "开头，以" \*/ "结尾
	+ 可生成项目的API  

案例：
```java
	/**
	*这里是文档注释
	*/
	public class Welcome{
		public static void main/*这里是行内注释*/(String[] args){
		
			//下面是打印语句。输出双引号中的内容
			System.out.println("我是videjin！");
			System.out.println("你好！");
			/*
			前进！
			无所畏惧
			*/
			System.out.println("加油！");
		}
	}
```
## 三、标识符

>给变量、类、方法以及包进行命名
1. 遵守规则
    + 开头: 
      + ①字母 
      + ②下划线\_ 
      + ③美元符号$
    + 其他不部分:
      + ① 字母 
      + ②下划线\_ 
      + ③美元符号$ 
      + ④ 数字 （不能作为开头）的任意组合
    + Java标识符大小写敏感、长度无限制
    + 不可以是Java的关键字

>Java采用Unicode标准国际字符集(2个字节表示一个符号,2¹⁶=65536,中文一万多,英文26个字母,其他语言等等都可包含),而不是ASCII字符集(1个字节,1个字节2⁸=256)。故字母不仅仅包含英文,还包含汉字等等。但是不建议使用汉字。

2. 关键词  
   
   | abstract   | assert  | boolean   | break     | byte       | case         |
   | :---------- | :------- | :--------- | :--------- | :---------- | :------------ |
   | catch      | char    | class     | const     | continue   | default      |
   | do         | double  | else      | extends   | final      | finally      |
   | float      | for     | goto      | if        | implements | import       |
   | imstanceof | int     | interface | long      | native     | new          |
   | null       | package | private   | protected | public     | return       |
   | short      | static  | strictfp  | super     | switch     | synchronized |
   | this       | throw   | throws    | transient | try        | void         |
   | volatile   | while   |           |           |            |              |
   
>关键词不需要背，实战中自然熟悉  

3. 使用规范
   + 驼峰规则
   + 类：每个单词首字母大写，如Man
   + 方法或变量：第一个单词小写，从第二个字母开始首字母大写，如eat()，eatFood()  

## 四、变量（Variable）

1. 变量本质
   + 可操作的存储空间，如停车场的车位
   + 空间有大有小，如int是4个字节
   + 通过变量名访问对应存储空间，从而操作存储的值
   + Java是一种强类型语言，每个变量都必须声明其数据类型。数据类型决定变量占据存储空间的大小。  

2. 变量的声明

```java
	type varName[=value][,varName[=value]...];
	//[]中的内容为可选项，即可有可无
	数据类型 变量名 [=初始值][,变量名[=初始值]...]
	
	//eg.
	double salary;//8byte
	long earthPopulation;//8byte
	int age;//4byte
	//一个字节8位（1byte=8bit）
```

3. 注意事项
   + 每个变量都有类型。可是基本类型，也可是引用类型。
   + 变量名必须是合法的标识符。
   + 变量声明是一条完整的语句，因此每一个声明必须以分号(;)结束。
   + 局部变量（方法中的变量）变量使用前进行初始化
   + 可以一行声明多个变量，但不提倡
```java
	//不提倡
	int i, j;//两个变量的数据类型都是int
	//提倡
	int i = 0;
	int j = 0;
```
4. 变量的分类和作用域

   > 整体上分局部变量、成员变量（实例变量）、静态变量  
   | 类型 | 声明位置 | 从属于 | 生命周期（作用域）|
   | :----: | :---: | :---: | :----: |
   | 局部变量 | 方法或语句块内部|方法/语句块|从声明位置开始，直到方法或语句块执行完毕，局部变量消失|
   | 成员（实例）变量 | 类内部，方法外部|对象|对象创建，成员变量也跟着创建；对象消失，成员变量也跟着消失|
   |静态（类）变量|类内部，static修饰|类|类被加载，静态变量就有效；类被卸载，静态变量消失|

   （1）局部变量（local variable）
   + 使用前必须声明、初始化（赋初值）

   （2）成员变量（member variable）  
   
   + 如果不自行初始化，它会自动初始化成该类型的默认初始值。
	
   （3）静态变量（static variable）
   
   + 如果不自行初始化，与成员变量相同会自动初始化成该类型的默认初始值。

| 数据类型|初始值|
|:----:|:----:|
|int|0|
|double|0.0|
|char|'\u0000'|
|boolean|false|

例子：
```java
	public class VariableTest{
		int classroom;//成员变量
		static int world;//静态变量
		public static void main(String[] args){
			int i;//局部变量的声明
			i = 0;//初始化，赋初值
		}
	}
```

## 五、常量（Constant）

