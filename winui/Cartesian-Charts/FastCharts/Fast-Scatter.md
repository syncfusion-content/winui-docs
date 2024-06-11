---
layout: post
title: Fast Scatter Chart in WinUI Chart control | Syncfusion
description: Learn here all about Fast Scatter Chart of Syncfusion WinUI Chart (SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: fast scatter chart in winui, winui sfcartesianchart fast scatter chart, winui fast scatter chart customization, syncfusion winui fast scatter chart, winui   sfcartesianchart fast scatter chart configuration.
---

# Fast Scatter Chart in WinUI (SfCartesianChart)

A fast scatter chart is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. [FastScatterBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html) is used to render high number of scatter points. 

The [PointHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_PointHeight) and [PointWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_PointWidth) properties are used to change the height and width of scatter segments. [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastScatterBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastScatterBitmapSeries_Type) is used to change the rendering shape of fast scatter bitmap series. 

The available shapes are 
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
