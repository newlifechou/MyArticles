# C#压缩解压的方法
## 小概念
zlib是一种数据压缩库，用来处理数据流。gzip是一种文件压缩工具，压缩单个文件，基于DEFLATE算法。zip可以压缩多个文件，包含目录结构，是压缩容器，可以使用多种压缩算法。DEFlATE是一种压缩算法。tar只是把多个文件归档为一个文件包。rar算法专有。
## 使用System.IO.Compression
参考资料[MSDN-System.IO.Compression][1]
### ZipFile类
需引用System.IO.Compression.FileSystem项目中的程序集  
压缩文件夹，解压缩文件夹  
辅助，ZipArchive类和ZipArchiveEntry类   
需引用System.IO.Compression项目中的程序集
用法看MSDN,非常简单。
### DeflateStream类
deflate是zip压缩文件的默认算法，是霍夫曼编码的加强，，其他的压缩格式也在使用。  
输入流后对流进行压缩和解压。
### GZipStream类
标准的gzip数据格式，使用的是DeflateStream类，扩展名gz，但是不提供添加和提取zip文档的功能。  
具体的用法两个类差不多一样，参考msdn文档很容易使用。
不过优先使用GZip，它添加了CRC校验码，创建的文档可以被压缩软件识别；  
## 使用SharpZipLib库
SharpZipLib是icsharpcode的库（大名鼎鼎的开源IED—sharpdevelop的组织，支持Zip,GZip,Tar和BZip2;  
在nuget中可以直接安装；  
[项目地址][2]  
安装好库后，直接在VS的对象管理器中查看相关的命名空间和类对象，结合一点其他的经验，差不多也就知道怎么用了。  

### 我用过的命名空间和类
[项目API地址][3] 这里是对命名空间和类的解析，里面东西还是挺多的，下面我会罗列一些我使用过的命名空间和类。   
ICSharpCode.SharpZipLib.Zip命名空间  
ZipFile类，FastZip类，ZipEntry类=压缩包里的一个文件,ZipOutStream类=压缩包
其余的命名空间和类库看API介绍，用的时候再研究。
## 借用7Zip进行操作
使用7zip要先安装7zip，然后通过process的方式启动7zip加命令行参数来操作。也有人弄了封装的7zip库。


[1]:https://msdn.microsoft.com/zh-cn/library/system.io.compression(v=vs.110).aspx
[2]:http://icsharpcode.github.io/SharpZipLib/
[3]:https://icsharpcode.github.io/SharpZipLib/help/api/index.html