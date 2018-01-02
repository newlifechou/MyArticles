# Cp18 定制Attribute
## 意义
利用Attribute，可以声明性的给自己的代码结构创建注解，从而实现一些特殊的功能；最终在元数据中生成，这种可扩展的元数据信息可以在运行时的时候查询，从而动态的改变代码的运行方式；大多数Attribute对编译器没有什么特别的意义，只是在元数据中生成它们；  
System.Attribute类；  默认可以省略Attribute后缀，C#会默认加上；  
顺序无关紧要，应用的时候会调用这个Attribute的构造函数；  
System.AttributeUsageAttribute类指明该特性用途；  
## 如何起作用
特性本来只是被额外生成一些元数据，没有其他意义；而类和方法等行为之所以会改变是因为它们自己在运行的时候会自己检查自己关联的特性值，从而决定自己的行为。用的技术就是反射；  
## 如何检查
IsDefined;GetCustomAttributes;GetCustomAttribute;
## 重写Match方法
在Attribute中重写；  
## 检查定制Attribute的时候不创建从Attribute派生的对象
System.Reflection.CustomAttributeData类的GetCustomAttributes静态方法；  
## 条件Attribute类
System.Diagnostics.CodnitionalAttribute类；
