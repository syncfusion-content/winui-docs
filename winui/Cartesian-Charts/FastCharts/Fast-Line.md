---
layout: post
title: Fast Line Chart in WinUI Chart Control | Syncfusion
description: Learn all about the Fast Line Series feature of the Syncfusion® WinUI Chart control (SfCartesianChart) and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI fast line chart, WinUI SfCartesianChart, fast line chart, WinUI fast line chart customization, Syncfusion WinUI fast line chart, fast line chart settings.
---

# Fast Line Chart in WinUI (SfCartesianChart)

## Fast Line Chart

The [FastLineSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineSeries.html) is a specialized line series capable of rendering a large collection of data points using a polyline segment efficiently.

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
        <chart:FastLineSeries ItemsSource="{Binding Data}" 
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

## Fast Line Bitmap Chart

The [FastLineBitmapSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html) displays a series of line segments rendered using `WriteableBitmap`. This series type can render a million data points in just a fraction of a second.

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
        <chart:FastLineBitmapSeries ItemsSource="{Binding Data}" 
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

### Anti-aliasing

Since it is rendered using a bitmap, there might be some jagged lines at the edges. This can be reduced by using the [EnableAntiAliasing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineBitmapSeries.html#Syncfusion_UI_Xaml_Charts_FastLineBitmapSeries_EnableAntiAliasing) property.

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
        <chart:FastLineBitmapSeries EnableAntiAliasing="True" 
                                    ItemsSource="{Binding Data}" 
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

![Anti-aliasing in fast line bitmap chart in WinUI](FastChart_images/fastlinebitmap_chart_antialiasing.png)
