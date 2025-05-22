---
layout: post
title: Axis Grid Lines in WinUI Chart Control | Syncfusion
description: Learn all about the chart axis grid lines and their customization in Syncfusion® WinUI Chart (SfCartesianChart).
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: grid lines in WinUI chart, WinUI SfCartesianChart grid lines, WinUI chart grid lines customization, Syncfusion WinUI chart grid lines, WinUI SfCartesianChart grid lines settings.
---

# Grid Lines in WinUI Chart (SfCartesianChart)

## Major Grid Lines

By default, major gridlines are automatically added to the [ChartAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html) at defined intervals. The visibility of the gridlines can be controlled using the [ShowMajorGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowMajorGridLines) property. The default value of [ShowMajorGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowMajorGridLines) is true.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis ShowMajorGridLines="False"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis />
</chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
NumericalAxis primaryAxis = new NumericalAxis()
{
    ShowMajorGridLines = false
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis();

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
<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis MajorGridLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis />
</chart:SfCartesianChart.YAxes>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
chart.PrimaryAxis = new NumericalAxis()
{
    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
};
chart.XAxes.Add(primaryAxis);

chart.YAxes.Add(new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/winui_chart_axis_major_gridlines_styles.png)

## Minor Grid Lines

Minor gridlines are added automatically when minor tick lines are defined using the [MinorTicksPerInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorTicksPerInterval) property of the chart axis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis MinorTicksPerInterval="3" />
</chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.XAxes.Add(new NumericalAxis();
NumericalAxis secondaryAxis = new NumericalAxis()
{
    MinorTicksPerInterval = 3,
};
chart.YAxes.Add(secondaryAxis);
. . .

{% endhighlight %}

{% endtabs %}

### Customization

The [MinorGridLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorGridLineStyle) property in the chart axis is used to customize the appearance of minor gridlines.

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

<chart:SfCartesianChart.XAxes>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.XAxes>

<chart:SfCartesianChart.YAxes>
    <chart:NumericalAxis MinorTicksPerInterval="3" 
                         MinorGridLineStyle="{StaticResource lineStyle}"/>
</chart:SfCartesianChart.YAxes>
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.XAxes.Add(new NumericalAxis());
NumericalAxis secondaryAxis = new NumericalAxis()
{
    MinorTicksPerInterval = 3,
    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
};
chart.YAxes.Add(secondaryAxis);
. . .

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_Images/winui_chart_axis_minor_gridlines_style.png)

