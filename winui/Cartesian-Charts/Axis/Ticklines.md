---
layout: post
title: Axis Tickline in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Tickline for chart axis of Syncfusion WinUI Cartesian Chart(SfCartesianChart) control and its features.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Axis Tickline support in WinUI Cartesian Chart

Tick line are the small lines which is drawn on the axis line representing the axis labels. Tick lines will be drawn outside of the axis by default. 

And Minor tick lines can be added by defining [SmallTicksPerInterval]() property. This property will add the tick lines to every interval.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="4"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
   SmallTicksPerInterval = 4 
};

{% endhighlight %}

{% endtabs %}

N> For category axis, minor tick lines is not applicable since it is rendered based on index positions.

## Tickline Size

Tick lines height can be customized using [TickLineSize]() and [SmallTickLineSize]() property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis SmallTickLineSize="10" SmallTicksPerInterval="4" TickLineSize="10"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
   TickLineSize = 10,
   SmallTickLineSize = 10,
   SmallTicksPerInterval = 4
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_small_ticklines.png)

## Position

Tick lines can be positioned inside or outside of the chart area. By default the tick lines will positioned outside of the chart area. 

| Property | Description |
|--|--|
|TickLinesPosition | Used to position the Major ticklines|
|SmallTickLinesPosition| Used to position the Minor ticklines|

The following code example demonstrates the positioning tick lines inside chart area.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis TickLinesPosition="Inside" SmallTickLinesPosition="Inside"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
   TickLinesPosition = AxisElementPosition.Inside,
   SmallTickLinesPosition = AxisElementPosition.Inside
};

{% endhighlight %}

{% endtabs %}

![Ticklines positioning support in WinUI Chart](Axis_images/WinUI_Chart_Axis_tickline_position.png)

## Customization

Style can be applied to major tick lines using [MajorTickLineStyle]() and [MinorTickLineStyle]() property. The following code snippet demonstrates the styling of tick lines.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="1"/>
        <Setter Property="Stroke" Value="Red"/>
    </Style>
</chart:SfCartesianChart.Resources>

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis MinorTickLineStyle="{StaticResource lineStyle}"  MajorTickLineStyle="{StaticResource lineStyle}" />
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{
    TickLineSize = 10,
    MajorTickLineStyle = chart.Resources["lineStyle"] as Style,
    MinorTickLineStyle = chart.Resources["lineStyle"] as Style 
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_tickline_style.png)