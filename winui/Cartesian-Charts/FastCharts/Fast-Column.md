---
layout: post
title: Fast Column Series in WinUI Chart control | Syncfusion
description: Learn here all about Fast Bitmap Series feature of Syncfusion WinUI Chart(SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast Column Chart in WinUI Chart (SfCartesianChart)

A fast column chart is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. [FastColumnBitmapSeries]() is used to boost up the performance of the column series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Series>
        <chart:FastColumnBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
FastColumnBitmapSeries series = new FastColumnBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastColumnBitmap chart type in WinUI Chart](FastChart_images/fastcolumnbitmap_chart.png)