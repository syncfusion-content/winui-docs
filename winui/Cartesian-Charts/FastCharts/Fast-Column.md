---
layout: post
title: Fast Column Series in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Fast Bitmap Series feature of Syncfusion WinUI Chart(SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast Column Bitmap Series in WinUI Cartesian Chart

A fast column bitmap series is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. [FastColumnBitmapSeries]() is used to boost up the performance of the column series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:FastColumnBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

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