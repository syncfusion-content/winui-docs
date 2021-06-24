---
layout: post
title: About Axis in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about the chart axis gridlines of syncfusion WinUI Cartesian Chart(SfCartesianChart) and its customization.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Gridlines in WinUI Cartesian Chart

## Major gridlines

By default, gridlines are automatically added to the [ChartAxis]() in its defined intervals. SfChart supports customization of gridline. The visibility of the gridlines can be controlled using the [ShowGridLines]() property.

The following code example illustrates the [ShowGridLines]() property as false in the primary axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis ShowGridLines="False"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    ShowGridLines = false
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_major_gridlines.png)

Style can also be applied to Major and Minor Gridlines using [MajorGridLineStyle]() and [MinorGridLineStyle]() properties.

**Major Gridline Style**

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="2"/>
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="StrokeDashArray" Value="3,3"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis MajorGridLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_major_gridlines_styles.png)

**Minor Gridline Style**

Minor gridlines will be added automatically when the small tick lines is defined inside the chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="2"/>
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="StrokeDashArray" Value="3,3"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="3" MinorGridLineStyle="{StaticResource lineStyle}" 
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    SmallTicksPerInterval = 3,
    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_Images/WinUI_Chart_Axis_minor_gridlines_styles.png)