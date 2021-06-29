---
layout: post
title: Axis Tick Line in WinUI Chart control | Syncfusion
description: Learn here all about chart axis tick line and its customization in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Tick Lines in WinUI Chart (SfCartesianChart)

Tick lines are the small lines which is drawn on the axis line representing the axis labels. Tick lines will be drawn outside of the axis by default. 

And also minor tick lines can be added to the axis by defining the [SmallTicksPerInterval]() property. This property will add the minor tick lines to every interval based on value.

N> For category axis, minor tick lines are not applicable. Since it is rendered based on index positions.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="4"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
   SmallTicksPerInterval = 4 
};

{% endhighlight %}

{% endtabs %}

## Size

Both major and minor tick lines height can be customized by using the [TickLineSize]() and [SmallTickLineSize]() properties respectively.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis SmallTickLineSize="10" SmallTicksPerInterval="4" TickLineSize="10"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
   TickLineSize = 10,
   SmallTickLineSize = 10,
   SmallTicksPerInterval = 4
};

{% endhighlight %}

{% endtabs %}

![Axis tick lines height support in WinUI Chart](Axis_images/WinUI_Chart_Axis_small_ticklines.png)

## Position

Tick lines can be positioned inside or outside of the chart area. By default the tick lines will positioned outside of the chart area. 

| Property | Description |
|--|--|
|TickLinesPosition | Used to position the major tick lines|
|SmallTickLinesPosition | Used to position the minor tick lines|

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis TickLinesPosition="Inside" SmallTickLinesPosition="Inside"/>
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
   TickLinesPosition = AxisElementPosition.Inside,
   SmallTickLinesPosition = AxisElementPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Axis tick lines positioning support in WinUI Chart](Axis_images/WinUI_Chart_Axis_tickline_position.png)

## Customization

Both major and minor tick lines can be customized by using the [MajorTickLineStyle]() and [MinorTickLineStyle]() properties respectively. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="1"/>
        <Setter Property="Stroke" Value="Red"/>
    </Style>
</chart:SfCartesianChart.Resources>

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis MinorTickLineStyle="{StaticResource lineStyle}"  MajorTickLineStyle="{StaticResource lineStyle}" />
</chart:SfCartesianChart.PrimaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    TickLineSize = 10,
    MajorTickLineStyle = chart.Resources["lineStyle"] as Style,
    MinorTickLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Axis tick lines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_tickline_style.png)