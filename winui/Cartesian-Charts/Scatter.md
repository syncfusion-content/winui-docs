---
layout: post
title: Scatter in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Scatter feature of Syncfusion WinUI Cartesian Chart(SfCartesianChart) control with key features and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Scatter Chart in WinUI Cartesian Charts (SfCartesianChart)

ScatterSeries is similar to bubble series, where each point being represented by an ellipse with equal size. To render a scatter chart, create an instance of [ScatterSeries](), and add it to the series collection property of [SfCartesianChart](). This size can be defined by using [ScatterHeight]() and [ScatterWidth]() properties.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:ScatterSeries ScatterHeight="7" ScatterWidth="7" ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
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

![Scatter chart type in WinUI Cartesian Chart](Chart-Types_images/WinUI_scatter_chart.png)

