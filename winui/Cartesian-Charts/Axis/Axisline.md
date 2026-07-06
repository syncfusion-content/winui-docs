---
layout: post
title: Axis line in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis line and its customization in Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: axis line in winui chart, winui sfcartesianchart axis line, syncfusion winui chart axis line, customize axis line in winui, winui sfcartesianchart axis line configuration.
---

# Axis line in WinUI Chart (SfCartesianChart)

## Customization

You can customize the axis line style using the [AxisLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineStyle) property, as shown below.

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
        <chart:NumericalAxis AxisLineStyle="{StaticResource lineStyle}"/>
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

![Axis line customization support in WinUI Chart](Axis_Images/WinUI_Chart_Axis_line_styles.png)

## Offset

The [AxisLineOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineOffset) property is used to add offset (padding) to the axis line. The default value is `0`.

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
    AxisLineOffset = 25,
    AxisLineStyle = chart.Resources["lineStyle"] as Style
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Axis line offset support in WinUI Chart](Axis_Images/WinUI_Chart_Axis_line_styles_offset.png)