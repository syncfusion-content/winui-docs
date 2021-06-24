---
layout: post
title: Fast Scatter Bitmap Series in WinUI Chart control | Syncfusion
description: Learn here all about Fast Scatter Bitmap Series feature of Syncfusion WinUI Chart(SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast Scatter Bitmap Series in WinUI Chart

A fast scatter bitmap series is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. 

[FastScatterBitmapSeries]() is used to render high number of scatter points. The [ScatterHeight]() and [ScatterWidth]() are also available as in [ScatterSeries](). [ShapeType]() is used to change the rendering shape of fast scatter bitmap series. 

The available shapes are 
* `Cross` 
* `Diamond` 
* `Ellipse` 
* `Hexagon` 
* `InvertedTriangle` 
* `Pentagon` 
* `Plus`
* `Rectangle`
* `Triangle`

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:FastScatterBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue" ScatterHeight="7" ScatterWidth="7"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight C# %}

FastScatterBitmapSeries series = new FastScatterBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    ScatterHeight = 7,
    ScatterWidth = 7
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastScatterBitmap chart type in WinUI](FastChart_images/fastscatterbitmap_chart.png)