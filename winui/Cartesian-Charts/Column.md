---
layout: post
title: Column in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Column and Bar support in Syncfusion WinUI Cartesian Chart(SfCartesianChart) control with segment spacing and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Column Chart in WinUI Cartesian Charts (SfCartesianChart)

Column charts plot discrete rectangles for the given values. To render a column chart, create an instance of [ColumnSeries](), and add it to the series collection property of [SfCartesianChart](). The following properties can be used to customize the appearance:

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Column chart type in WinUI Cartesian Chart](Chart-Types_images/WinUI_column_chart.png)

## SegmentSpacing

The spacing property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue" SegmentSpacing="0.5"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    SegmentSpacing = 0.5
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Column spacing chart type in WinUI Cartesian Chart](Chart-Types_images/WinUI_column_chart_segment_spacing.png)
