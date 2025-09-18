---
layout: post
title: Bar Chart in WinUI Chart Control | Syncfusion
description: Learn all about the bar chart and its features in the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI bar chart, WinUI SfCartesianChart, WinUI bar chart customization, Syncfusion WinUI bar chart, WinUI bar chart settings.
---

# Bar Chart in WinUI Chart (SfCartesianChart)

A bar chart uses bars to represent data points and compare values across different categories. To render a bar chart, initialize the [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) and set the [IsTransposed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_IsTransposed) property to `true`. Then, create an instance of [ColumnSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ColumnSeries.html) and add it to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of the [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html).

N> By default, the [IsTransposed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_IsTransposed) property of the [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) is `false`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart IsTransposed="True">

    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>   

    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" 
                            XBindingPath="XValue" 
                            YBindingPath="YValue"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.IsTransposed = true;
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

![Bar chart type in WinUI Chart](Chart-Types_images/WinUI_bar_chart.png)

## Segment spacing

## Segment Spacing

The [SegmentSpacing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ColumnSeries.html#Syncfusion_UI_Xaml_Charts_ColumnSeries_SegmentSpacing) property is used to change the spacing between two segments. The default value of spacing is `0`, and the value ranges from `0` to `1`. Here, `1` and `0` correspond to `100%` and `0%` of the available space, respectively.


{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart IsTransposed="True">

    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes> 

    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" 
                            XBindingPath="XValue" 
                            YBindingPath="YValue" 
                            SegmentSpacing="0.5"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.IsTransposed = true;
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

![Bar segment spacing in WinUI Chart](Chart-Types_images/WinUI_bar_chart_segment_spacing.png)

N> You can also explore our [WinUI Bar Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/Bar) that shows how to easily configure with built-in support for creating stunning visual effects.
