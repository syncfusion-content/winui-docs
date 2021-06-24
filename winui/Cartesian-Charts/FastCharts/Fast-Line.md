---
layout: post
title: Fast Line chart in WinUI Chart control | Syncfusion
description: Learn here all about Fast Line Series feature of Syncfusion WinUI Chart control(SfCartesianChart) and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast Line Chart in WinUI Cartesian Chart

## Fast Line

The [FastLineSeries]() is a special kind of line series that can render a collection with huge number of datapoints using the polyline segment. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:FastLineSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

FastLineSeries series = new FastLineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastLine chart type in WinUI](FastChart_images/fastline_chart.png)

## Fast Line Bitmap

[FastLineBitmapSeries]() displays a series of line segments, rendered using `WriteableBitmap`. The advantage of FastLineBitmapSeries is, it renders a million data point in a fraction of seconds.

The following code example shows how to use the fast line bitmap series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:FastLineBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

FastLineBitmapSeries series = new FastLineBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastLineBitmap chart type in WinUI](FastChart_images/fastlinebitmap_chart.png)

N> As it was rendered using bitmap, there might be some jagged lines at the edges. This is can be reduced using the [`EnableAntiAliasing`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastLineBitmapSeries_EnableAntiAliasing) property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:FastLineBitmapSeries EnableAntiAliasing="True" ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

FastLineBitmapSeries series = new FastLineBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    EnableAntiAliasing = true
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![AntiAliasing support for fast line bitmap chart in WinUI](FastChart_images/fastlinebitmap_chart_antialiasing.png)