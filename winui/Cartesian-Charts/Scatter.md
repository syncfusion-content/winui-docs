---
layout: post
title: Scatter Chart in WinUI Chart control | Syncfusion
description: Learn here all about the scatter chart and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Scatter Chart in WinUI Charts (SfCartesianChart)

The [WinUI Scatter Chart](https://www.syncfusion.com/winui-controls/charts/winui-scatter-chart) is similar to bubble chart, where each data point being represented by a circle with equal size.

## Scatter Chart

To render a scatter chart, create an instance of [ScatterSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html), and add it to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html). The segment size can be defined by using the [ScatterHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_ScatterHeight) and [ScatterWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_ScatterWidth) properties.

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
        <chart:ScatterSeries ScatterHeight="7" ScatterWidth="7" ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
NumericalAxis primaryAxis = new NumericalAxis();
chart.XAxes.Add(primaryAxis);
NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

ScatterSeries series = new ScatterSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    ScatterHeight = 7,
    ScatterWidth = 7,
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Scatter chart type in WinUI Chart](Chart-types_images/WinUI_scatter_chart.png)

N> You can also explore our [WinUI Scatter Chart example](https://github.com/syncfusion/winui-demos/blob/master/chart/Views/Basic%20Charts/ScatterChart.xaml) that shows how to easily configure with built-in support for creating stunning visual effects.