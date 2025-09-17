---
layout: post
title: Fast Step Line Chart in WinUI Chart Control | Syncfusion
description: Learn all about the Fast Step Line Chart of the Syncfusion® WinUI Chart control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI fast step line chart, WinUI SfCartesianChart, WinUI fast step line chart customization, Syncfusion WinUI fast step line chart, fast step line chart settings.
---

# Fast Step Line Chart in WinUI (SfCartesianChart)

A fast step line bitmap series is a specialized series that can efficiently render a large number of data points using `WriteableBitmap`. The [FastStepLineBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastStepLineBitmapSeries.html) is an optimized version of the step line series.

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
        <chart:FastStepLineBitmapSeries ItemsSource="{Binding Data}" 
                                        XBindingPath="XValue" 
                                        YBindingPath="YValue" />
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
DateTimeAxis xAxis = new DateTimeAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

### Anti-aliasing

The anti-aliasing mode can be enabled using the [EnableAntiAliasing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastStepLineBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastStepLineBitmapSeries_EnableAntiAliasing) property of the [FastStepLineBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastStepLineBitmapSeries.html), as shown in the following code sample.

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
        <chart:FastStepLineBitmapSeries EnableAntiAliasing="True" 
                                        ItemsSource="{Binding Data}" 
                                        XBindingPath="XValue" 
                                        YBindingPath="YValue" />
    </chart:SfCartesianChart.Series>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
DateTimeAxis xAxis = new DateTimeAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);
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

![Anti-aliasing support for FastStepLineBitmap chart in WinUI](FastChart_images/faststeplinebitmap_chart_antialiasing.png)
