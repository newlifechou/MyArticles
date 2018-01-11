# LiveCharts文档-3开始-5序列Series
## Strokes和Fills 笔触和填充
所有的Series都有笔触和填充属来处理颜色，都支持的是System.Windows.Media.Brush.你也可以使用复杂的填充和笔触，请参阅其他的文章。  
```
mySeries.Fill = Brushes.Red;
mySeries.Stroke = Brushes.Blue;
```
## Stroke 间隔和粗细
使用Series.StrokeThickness属性设置笔触粗细，使用Series.StrokeDashArray属性来设置间隔。  
```
mySeries.StrokeDashArray = new DoubleCollection {2};
```
## ZIndex 叠放顺序
每个series绘制的每个形状都绑定在Panel.ZIndex属性上，所以你可以非常容易的控制每个Series的叠放顺序。这里有一个小例子。
```
System.Windows.Controls.Panel.SetZIndex(mySeries, 0);
System.Windows.Controls.Panel.SetZIndex(mySeries, 1);
System.Windows.Controls.Panel.SetZIndex(mySeries, 2);
```
## Visibility 可见性
所有绘制的形状也都绑定在Series.Visibility属性上，你可以在程序运行的时候很容易的控制series的可见性。   
注意：所有stacked series（包括pie series）不仅会在可见性上有变化，同时也会从stakced值中移除这个series，整个chart都会被更新，如果这个series不存在的话。  
## 特殊的属性
有一些属性只存在特定的series中，想要看关于定制series的更多信息，请查看之后的文章。  
请看下面这个例子：  
![](../Images/LiveCharts/customline.png)

```
using System;
using System.Drawing;
using System.Windows.Forms;
using LiveCharts;
using LiveCharts.Wpf;
 
namespace Winforms.Cartesian.Customized_Series
{
    public partial class CustomizedSeries : Form
    {
        public CustomizedSeries()
        {
            InitializeComponent();
 
            cartesianChart1.Series.Add(new LineSeries
            {
                Values = new ChartValues<double> { 3, 4, 6, 3, 2, 6 },
                StrokeThickness = 4,
                StrokeDashArray = new System.Windows.Media.DoubleCollection(20),
                Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(107, 185, 69)),
                Fill = System.Windows.Media.Brushes.Transparent,
                LineSmoothness = 0,
                PointGeometry = null
            });
            cartesianChart1.Series.Add(new LineSeries
            {
                Values = new ChartValues<double> { 5, 3, 5, 7, 3, 9 },
                StrokeThickness = 2,
                Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(28, 142, 196)),
                Fill = System.Windows.Media.Brushes.Transparent,
                LineSmoothness = 1,
                PointGeometrySize = 15,
                PointForeround =
                    new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(34, 46, 49))
            });
 
            cartesianChart1.Background = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(34, 46, 49));
 
            cartesianChart1.AxisX.Add(new Axis
            {
                IsMerged = true,
                Separator = new Separator
                {
                    StrokeThickness = 1,
                    StrokeDashArray = new System.Windows.Media.DoubleCollection(2),
                    Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
                }
            });
            cartesianChart1.AxisY.Add(new Axis
            {
                IsMerged = true,
                Separator = new Separator
                {
                    StrokeThickness = 1.5,
                    StrokeDashArray = new System.Windows.Media.DoubleCollection(4),
                    Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
                }
            });
 
        }
    }
}
```