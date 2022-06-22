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

And also minor tick lines can be added to the axis by defining the [MinorTicksPerInterval]() property. This property will add the minor tick lines to every interval based on value.

N> For category axis, minor tick lines are not applicable. Since it is rendered based on index positions.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis MinorTicksPerInterval="4"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis />
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
   MinorTicksPerInterval = 4 
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());

{% endhighlight %}

{% endtabs %}

## Size

Both major and minor tick lines height can be customized by using the [TickLineSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TickLineSize) and [MinorTickLineSize]() properties respectively.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis MinorTickLineSize="10" MinorTicksPerInterval="4" TickLineSize="15"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis />
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
   TickLineSize = 15,
   MinorTickLineSize = 10,
   MinorTicksPerInterval = 4
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());

{% endhighlight %}

{% endtabs %}

![Axis tick lines height support in WinUI Chart](Axis_images/winui_chart_axis_small_ticklines.png)

## Customization

Both major and minor tick lines can be customized by using the [MajorTickLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorTickLineStyle) and [MinorTickLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MinorTickLineStyle) properties respectively. 

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

<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis MinorTicksPerInterval="4" MinorTickLineStyle="{StaticResource lineStyle}"  MajorTickLineStyle="{StaticResource lineStyle}" />
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis />
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
    MinorTicksPerInterval = 4,
    MajorTickLineStyle = chart.Resources["lineStyle"] as Style,
    MinorTickLineStyle = chart.Resources["lineStyle"] as Style 
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis());

{% endhighlight %}

{% endtabs %}

![Axis tick lines customization support in WinUI Chart](Axis_images/winui_chart_axis_tickline_style.png)