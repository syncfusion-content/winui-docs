---
layout: post
title: Axis line in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis line and its customization in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis line in WinUI Chart (SfCartesianChart)

## Customization

Cartesian chart axis provides support to customize the style of axis line by defining the [AxisLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineStyle) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="2"/>
        <Setter Property="Stroke" Value="Red"/>
        <Setter Property="StrokeDashArray" Value="6,2,3"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis AxisLineStyle="{StaticResource lineStyle}" />
</chart:SfCartesianChart.XAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
    AxisLineStyle = chart.Resources["lineStyle"] as Style 
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis line customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_line_styles.png)

## Offset

The padding to the axis line is defined by using the [AxisLineOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineOffset) property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis AxisLineOffset="25" AxisLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.XAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
    AxisLineOffset = 25
    AxisLineStyle = chart.Resources["lineStyle"] as Style
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Padding support for axis line in WinUI](Axis_images/WinUI_Chart_Axis_line_styles_offset.png)