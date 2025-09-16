---
layout: post
title: Fast Scatter Chart in WinUI Chart Control | Syncfusion
description: Learn all about the Fast Scatter Chart of the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI fast scatter chart, WinUI SfCartesianChart, WinUI fast scatter chart customization, Syncfusion WinUI fast scatter chart, fast scatter chart configuration.
---

# Fast Scatter Chart in WinUI (SfCartesianChart)

A fast scatter chart is a type of series that can efficiently render a large collection of data points using `WriteableBitmap`. The [FastScatterBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html) is employed to render a high number of scatter points.

The [PointHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_PointHeight) and [PointWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_PointWidth) properties allow customization of the height and width of scatter segments. The [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_Type) property is used to modify the rendering shape of the fast scatter bitmap series.

The available shapes include:
* `Cross`
* `Diamond`
* `Circle`
* `Hexagon`
* `InvertedTriangle`
* `Pentagon`
* `Plus`
* `Rectangle`
* `Triangle`

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes> 

    <chart:SfCartesianChart.Series>
        <chart:FastScatterBitmapSeries ItemsSource="{Binding Data}" 
                                       XBindingPath="XValue" 
                                       YBindingPath="YValue" 
                                       PointHeight="7" 
                                       PointWidth="7"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight C# %}

SfCartesianChart chart = new SfCartesianChart();
NumericalAxis xAxis = new NumericalAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

FastScatterBitmapSeries series = new FastScatterBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    PointHeight = 7,
    PointWidth = 7
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastScatterBitmap chart type in WinUI](FastChart_images/fastscatterbitmap_chart.png)
