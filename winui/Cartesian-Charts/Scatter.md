---
layout: post
title: Scatter Chart in WinUI Chart control | Syncfusion
description: Learn here all about the scatter chart and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: scatter chart in winui chart, winui sfcartesianchart scatter chart, winui scatter chart customization, syncfusion winui scatter chart, winui chart scatter chart properties.
---

# Scatter Chart in WinUI Charts (SfCartesianChart)

The [WinUI Scatter Chart](https://www.syncfusion.com/winui-controls/charts/winui-scatter-chart) is similar to bubble chart, where each data point being represented by a circle with equal size.

## Scatter Chart

To render a scatter chart, create an instance of the [ScatterSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html), and add it to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html). The segment size can be defined by using the [PointHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_PointHeight) and [PointWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_PointWidth) properties.

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
        <chart:ScatterSeries PointHeight="7" 
                             PointWidth="7" 
                             ItemsSource="{Binding Data}" 
                             XBindingPath="XValue" 
                             YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
NumericalAxis xAxis = new NumericalAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

ScatterSeries series = new ScatterSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    PointHeight = 7,
    PointWidth = 7,
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Scatter chart type in WinUI Chart](Chart-types_images/WinUI_scatter_chart.png)

N> You can also explore our [WinUI Scatter Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/Scatter) that shows how to easily configure with built-in support for creating stunning visual effects.