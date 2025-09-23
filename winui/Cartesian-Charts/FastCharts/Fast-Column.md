---
layout: post
title: Fast Column Series in WinUI Chart Control | Syncfusion
description: Learn all about Fast Column Bitmap Series in the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI fast column chart, WinUI SfCartesianChart, WinUI fast column chart customization, Syncfusion WinUI fast column chart, WinUI fast column chart configuration.
---

# Fast Column Chart in WinUI (SfCartesianChart)

A fast column chart is a unique series type that can render a collection with a large number of data points using `WriteableBitmap`. The [FastColumnBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastColumnBitmapSeries.html) is used to enhance the performance of rendering column series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.XAxes>
        <chart:DateTimeAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>  

    <chart:SfCartesianChart.Series>
        <chart:FastColumnBitmapSeries ItemsSource="{Binding Data}" 
                                      XBindingPath="XValue" 
                                      YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
DateTimeAxis xAxis = new DateTimeAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

FastColumnBitmapSeries series = new FastColumnBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastColumnBitmap chart type in WinUI](FastChart_images/fastcolumnbitmap_chart.png)
