---
layout: post
title: Axis line in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about the chart axis line of Syncfusion WinUI Cartesian Chart(SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis Line in WinUI Cartesian Chart

## Line Style
Cartesian chart axis provides support to customize the style of the axis line by defining the [AxisLineStyle]() property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="2"/>
        <Setter Property="Stroke" Value="Red"/>
        <Setter Property="StrokeDashArray" Value="6,2,3"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis AxisLineStyle="{StaticResource lineStyle}" />
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    AxisLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![AxisLine customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_line_styles.png)

## Offset

The padding to the axis line is defined using [AxisLineOffset]() property. The following code example demonstrates the setting [AxisLineOffset]() for x axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis AxisLineOffset="25" AxisLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    AxisLineOffset = 25
    AxisLineStyle = chart.Resources["lineStyle"] as Style
};

{% endhighlight %}

{% endtabs %}

![Padding support for axis line in WinUI](Axis_images/WinUI_Chart_Axis_line_styles_offset.png)


