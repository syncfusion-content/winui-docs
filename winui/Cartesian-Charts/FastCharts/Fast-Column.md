---
layout: post
title: Fast Column Series in WinUI Chart control | Syncfusion
description: Learn here all about Fast Column Bitmap Series of Syncfusion WinUI Chart (SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast Column Chart in WinUI (SfCartesianChart)

A fast column chart is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. [FastColumnBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastColumnBitmapSeries.html) is used to boost up the performance of the column series.

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
        <chart:FastColumnBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
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
