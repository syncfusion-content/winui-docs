---
layout: post
title: Axis gridlines in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis gridlines and its customization in syncfusion WinUI Chart(SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Gridlines in WinUI Chart (SfCartesianChart)

## Major Gridlines

By default, major gridlines are automatically added to the [ChartAxis]() in its defined intervals. The visibility of the gridlines can be controlled using the [ShowGridLines]() property. The default value of [ShowGridLines]() is true. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis ShowGridLines="False"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    ShowGridLines = false
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_major_gridlines.png)

### Customization

The [MajorGridLineStyle]() property in the chart axis is used to customize the appearance of major gridlines.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
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

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_major_gridlines_styles.png)

## Minor Gridlines

Minor gridlines will be added automatically when the small tick lines is defined using the [SmallTicksPerInterval]() property of chart axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="3" />
</chart:SfCartesianChart.SecondaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.SecondaryAxis = new NumericalAxis()
{
    SmallTicksPerInterval = 3,
};

{% endhighlight %}

{% endtabs %}

### Customization

The [MinorGridLineStyle]() property in the chart axis is used to customize the appearance of minor gridlines.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="2"/>
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="StrokeDashArray" Value="3,3"/>
    </Style>
</chart:SfCartesianChart.Resources>
. . .
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="3" MinorGridLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.SecondaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . . 
chart.SecondaryAxis = new NumericalAxis()
{
    SmallTicksPerInterval = 3,
    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_Images/WinUI_Chart_Axis_minor_gridlines_styles.png)

