---
layout: post
title: Axis grid lines in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis grid lines and its customization in syncfusion WinUI Chart(SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Grid Lines in WinUI Chart (SfCartesianChart)

## Major Grid Lines

By default, major gridlines are automatically added to the [ChartAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html) in its defined intervals. The visibility of the gridlines can be controlled using the [ShowGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowGridLines) property. The default value of [ShowGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowGridLines) is true. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis ShowGridLines="False"/>
</chart:SfCartesianChart.PrimaryAxis>

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis />
</chart:SfCartesianChart.SecondaryAxis>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    ShowGridLines = false
};

chart.SecondaryAxis = new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/winui_chart_axis_major_gridlines.png)

### Customization

The [MajorGridLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorGridLineStyle) property in the chart axis is used to customize the appearance of major gridlines.

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

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis />
</chart:SfCartesianChart.SecondaryAxis>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
};

chart.SecondaryAxis = new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/winui_chart_axis_major_gridlines_styles.png)

## Minor Grid Lines

Minor gridlines will be added automatically when the small tick lines is defined using the [SmallTicksPerInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_SmallTicksPerInterval) property of chart axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.PrimaryAxis>

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="3" />
</chart:SfCartesianChart.SecondaryAxis>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.PrimaryAxis = new NumericalAxis();
chart.SecondaryAxis = new NumericalAxis()
{
    SmallTicksPerInterval = 3,
};
. . .

{% endhighlight %}

{% endtabs %}

### Customization

The [MinorGridLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MinorGridLineStyle) property in the chart axis is used to customize the appearance of minor gridlines.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
<chart:SfCartesianChart.Resources>
    <Style TargetType="Line" x:Key="lineStyle">
        <Setter Property="StrokeThickness" Value="0.8"/>
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="StrokeDashArray" Value="3,3"/>
    </Style>
</chart:SfCartesianChart.Resources>

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.PrimaryAxis>

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis SmallTicksPerInterval="3" MinorGridLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.SecondaryAxis>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.PrimaryAxis = new NumericalAxis();
chart.SecondaryAxis = new NumericalAxis()
{
    SmallTicksPerInterval = 3,
    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
};
. . .

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_Images/winui_chart_axis_minor_gridlines_style.png)

