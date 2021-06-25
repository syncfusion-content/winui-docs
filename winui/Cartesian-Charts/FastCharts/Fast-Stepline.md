---
layout: post
title: Fast StepLine Chart in WinUI Chart control | Syncfusion
description: Learn here all about Fast StepLine Chart of Syncfusion WinUI Chart(SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Fast StepLine Chart in WinUI Chart (SfCartesianChart)

A fast stepline bitmap series is a special kind of series that can render a collection with huge number of data points using `WriteableBitmap`. [FastStepLineBitmapSeries]() is the high performance version of step line series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Series>
        <chart:FastStepLineBitmapSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue" />
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
FastStepLineBitmapSeries series = new FastStepLineBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastStepLineBitmap chart type in WinUI Chart](FastChart_images/faststeplinebitmap_chart.png)

The anti aliasing mode can be enabled using the [EnableAntiAliasing]() property of FastStepLineBitmapSeries as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.Series>
        <chart:FastStepLineBitmapSeries EnableAntiAliasing="True" ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue" />
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
FastStepLineBitmapSeries series = new FastStepLineBitmapSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    EnableAntiAliasing = true
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![AntiAliasing support for FastStepLineBitmap chart type in WinUI Chart](FastChart_images/faststeplinebitmap_chart_antialiasing.png)
