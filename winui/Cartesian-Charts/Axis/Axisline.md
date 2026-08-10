---
layout: post
title: Axis Line in WinUI Chart | Syncfusion®
description: Axis line in the WinUI Chart defines the visual boundary of chart axes and supports customization of style, color, and appearance.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: axis line in winui chart, winui sfcartesianchart axis line, syncfusion winui chart axis line, customizing axis line in winui, winui sfcartesianchart axis line configuration.
---

# Axis Line in WinUI Chart

## Customization

Cartesian chart axis provides support to customize the style of the axis line by defining the [AxisLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineStyle) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.Resources>
        <Style TargetType="Line" x:Key="lineStyle">
            <Setter Property="StrokeThickness" Value="2"/>
            <Setter Property="Stroke" Value="Red"/>
            <Setter Property="StrokeDashArray" Value="6,2,3"/>
        </Style>
    </chart:SfCartesianChart.Resources>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis AxisLineStyle="{StaticResource lineStyle}"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// The 'lineStyle' resource is defined in XAML Resources and referenced here.
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

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis AxisLineOffset="25" AxisLineStyle="{StaticResource lineStyle}"/>
    </chart:SfCartesianChart.XAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// The 'lineStyle' resource is defined in XAML Resources and referenced here.
NumericalAxis primaryAxis = new NumericalAxis()
{
    AxisLineOffset = 25,
    AxisLineStyle = chart.Resources["lineStyle"] as Style
};
chart.XAxes.Add(primaryAxis);

{% endhighlight %}

{% endtabs %}

![Padding support for axis line in WinUI](Axis_images/WinUI_Chart_Axis_line_styles_offset.png)

## See Also

* [How to customize the axis labels of WinUI Chart (SfCartesianChart)](https://support.syncfusion.com/kb/article/13013)