# LiveCharts文档-2FAQ
[原文链接](https://lvcharts.net/App/examples/v1/wf/start)  
LiveCharts基于的平台有WPF，UWP，WinForms；语言是C#，   
FAQ：  
**我怎么转换一个chart到image**  
请使用```RenderTargetBitmap``` 类  
**我怎么处理一个不再当前屏幕上的chart**  
现在还不支持，请继续关注更新。  
**我如何用编程的方式缩放chart**  
可以很容易的通过```Axis.MinValue```和```Axis.MaxValue```属性来操作。  
**为什么我的动画很丑？**  
对库来说，引用类型比值类型更容易追踪，如果你模仿的例子是用引用类型的Point，比如ObservableCollection类，而你却用的是值类型的double来代替，你就可能得到一个不同的动画。  
**为什么我的动画很慢？**  
试试```LiveCharts.Geared```。它是用来提高LiveCharts库性能的一个独立的加速包。当LiveCharts开始做的时候，我主要考虑的是美观，很少关注过性能，但是当这个库开始火的时候，我就必须添加这样一个包来提高性能，从而让LiveCharts更加完善。 
