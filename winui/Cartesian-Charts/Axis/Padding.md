---
layout: post
title: Axis padding in WinUI Chart control | Syncfusion
description: Learn here all about how to set padding for chart axis in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis Padding in WinUI Chart (SfCartesianChart)

The [PlotOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffset) property is used to provide padding to the axis. The following code sample demonstrates the padding applied to both x and y-axes.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis PlotOffset="30"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis PlotOffset="30"/>
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
CategoryAxis primaryAxis = new CategoryAxis()
{
   PlotOffset = 30
};
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis()
{
   PlotOffset = 30
};
chart.YAxes.Add(secondaryAxis);
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![PlotOffset support in WinUI Chart](Axis_images/winui_chart_axis_plot-offset.png)

## PlotOffsetStart

The [PlotOffsetStart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffsetStart) property is used to provide padding to the axis at start position. The following code sample demonstrates the padding applied to Start position for both x and y-axes.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis PlotOffsetStart="30"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis PlotOffsetStart="30"/>
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
CategoryAxis primaryAxis = new CategoryAxis()
{
   PlotOffsetStart = 30
};
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis()
{
   PlotOffsetStart = 30
};
chart.YAxes.Add(secondaryAxis);
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![PlotOffsetStart support in WinUI Chart](Axis_images/winui_chart_axis_plot-offset-start.png)

## PlotOffsetEnd

The [PlotOffsetEnd](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffsetEnd) property is used to provide padding to the axis at end position. The following code sample demonstrates the padding applied to end position for both x and y-axes.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:CategoryAxis PlotOffsetEnd="30"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis PlotOffsetEnd="30"/>
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
CategoryAxis primaryAxis = new CategoryAxis()
{
   PlotOffsetEnd = 30
};
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis()
{
   PlotOffsetEnd = 30
};
chart.YAxes.Add(secondaryAxis);
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![PlotOffsetEnd support in WinUI Chart](Axis_images/winui_chart_axis_plot-offset-end.png)