# LiveCharts文档-3开始-6轴Axes
通常来说，你可以自定义LiveChart里的任何东西，Axes也不例外。下面这幅图展示了Axes。  
![](../Images/LiveCharts/axise.jpg)

## Title标题
可以使用Title属性给axis添加一个标签
```
myAxis.Title = "Population"
```
## 合并轴
当你想需要一些空间的时候，可以在chart中合并一些axis，可以将Axis.IsMerged属性设置为true。下面的图片展示了合并Axis和没有合并的Axis的区别。  
![](../Images/LiveCharts/axiscompare.png)

## 轴定位
不管你有1个还是10个轴，你总是可以制定轴的堆叠位置；使用 Axis.Position属性, 可以通过 RightTop, LeftBottom等可选选项进行调整。  
```
new Axis { Position = Position = AxisPosition.LeftBottom }
```
![](../Images/LiveCharts/multiax.jpg)

## 强制分隔
每个轴分隔都是根据chart的尺寸，值的范围，自动计算的,但是有些时候你需要静态的风格符，比如每30s，每10个单位，另外一个比较有用的应用就是显示所有的标签，这种情况下，设定分隔步长为1，将会强迫chart绘制所有的labels。如果要移除所有步长，可以设置回null，这样它又可以自动计算了。  
当然要注意，强制步长可能会产生严重的性能问题，如果没有正确使用，比如你的range是0到1000，如果你设置步长为1，那么它将绘制1000个分隔出来。  
//设置步长为1
```
new Axis
{
    Separator = new Separator
    {
        Step = 1,
        IsEnabled = false
    }
}
```
//下面这个例子使用30s作为步长，可以去时间相关的章节查看更多。
```
new Axis
{
    Separator = new Separator
    {
        Step = TimeSpan.FromSeconds(30).Ticks,
        IsEnabled = false
    }
}
```
## 分隔的样式
notice setting Axis.Separator.IsEnabled property to false will make the separator invisible.
注意，如果设置Axis.Separator.IsEnabled 为false的话，分隔就会不可见。

```
cartesianChart1.AxisX.Add(new Axis
{
   IsMerged = true,
   Separator = new Separator
   {
      StrokeThickness = 1,
      StrokeDashArray = new System.Windows.Media.DoubleCollection(new double[] { 2 }),
      Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
   }
});
 
cartesianChart1.AxisY.Add(new Axis
{
   IsMerged = true,
   Separator = new Separator
   {
      StrokeThickness = 1.5,
      StrokeDashArray = new System.Windows.Media.DoubleCollection(new double[] { 4 }),
      Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
   }
});
```

本节完