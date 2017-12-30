# CLR执行模型
本章的概念点

## CLR=Common Language Runtime
内存管理，程序集加载，安全性，异常处理和线程同步、CLR是基础，支持着面向它的各种语言。各种语言会被对应的编译器转换为托管模块。    
不同语言有各自的优点和不足。  
在需要托管程序运行的电脑上必须安装CLR(.NET Framework).

## 托管模块managed module
1. PE32,PE32+=portable Executable
2. CLR头（CLR版本，标志，IL入口的标记，元数据，资源，强名称，其他）
3. 元数据，定义和引用的类型和成员
4. IL中间代码

## 程序集Assembly
抽象概念，逻辑概念，重用，安全性，版本控制的最小单元，可以是一个文件，也可以是多个文件。组件。  
可能是exe，也可能是dll  
C#默认编译选项就是anycpu。  
WoW64允许64位系统运行32位程序。

## 清单manifest
描述构成程序集的文件。自描述self-describing，方便部署，XCopy的方式。
## 元数据metadata=数据表
### 元数据的作用
* 无需头文件和库文件
* 支持Intellisence
* 确保类型安全
* 序列化支持
* 垃圾回收

## 中间语言IL=Intermedite Language
可以将IL视为一种OO的机器语言。  
ILAsm.exe汇编器和ILDasm.exe反汇编器  
IL基于栈。  
IL是无类型的。  
对底层CPU的抽象。  
提供应用程序的健壮性和安全性。  
每个Windows进程放在一个独立的虚拟内存空间。  

## 即时编译JIT=just in time
JIT即时编译，首次编译有性能损失，第二次后会存入动态内存中，之后就快了。  
JIT会对IL本地化的时候进行优化，编译器的debug和optimize选项会影响优化。未优化的代码提供调试暂停功能，优化的代码有助于提高速度和减少体积。  
### PDB=program database
PDB帮助调试器查找局部变量并将IL指令映射到源代码。  
被JIT优化的托管代码性能可能比非托管更好。  
NGen.exe可以实现将IL编译成本地代码。  

## unsafe代码
## IL代码的知识产权
IL代码容易被反编译，但是现在很多情况是程序集是放在服务器上的，而分发出去的程序集可以使用混淆器，或者机密的部分使用非托管代码。
## AppDomain
后续了解
## FCL=Framework类库
.NET Framework的重要组成部分，微软已经造好的轮子，可以直接拿来用。  
为了使用一个功能，必须知道这个功能由什么类型提供，在哪个命名空间当中。  

## CTS=Common Type System通用类型系统
字段，方法，属性，事件。  
访问规则，public,private,protected,internal.  
语言会公开自己的语言语法和类型规则，在编译的时候，将特有的语法映射到IL。  
System.Object是万物之源。  
## CLS=Common Language Specification公共语言规范
可以理解为各个语言的规范接口，凡是遵守这个规范的，可以进行通信。  
## 和非托管代码的互操作
托管代码可以使用P/Invoke来调用dll中的非托管函数。  
托管代码可以使用现有的COM组件。  
非托管代码可以使用托管代码。  

