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

By default, major gridlines are automatically added to the [ChartAxis](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html?tabs=tabid-7%2Ctabid-5%2Ctabid-9%2Ctabid-45%2Ctabid-20%2Ctabid-32%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-18%2Ctabid-36%2Ctabid-34%2Ctabid-11%2Ctabid-46%2Ctabid-22%2Ctabid-24%2Ctabid-38%2Ctabid-3%2Ctabid-1%2Ctabid-30%2Ctabid-42%2Ctabid-40%2Ctabid-44%2Ctabid-28%2Ctabid-26%2Ctabid-47%2Ctabid-49) in its defined intervals. The visibility of the gridlines can be controlled using the [ShowMajorGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html?tabs=tabid-7%2Ctabid-5%2Ctabid-9%2Ctabid-45%2Ctabid-20%2Ctabid-32%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-18%2Ctabid-36%2Ctabid-34%2Ctabid-11%2Ctabid-46%2Ctabid-22%2Ctabid-24%2Ctabid-38%2Ctabid-3%2Ctabid-1%2Ctabid-30%2Ctabid-42%2Ctabid-40%2Ctabid-44%2Ctabid-28%2Ctabid-26%2Ctabid-47%2Ctabid-49#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowMajorGridLines) property. The default value of [ShowMajorGridLines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html?tabs=tabid-7%2Ctabid-5%2Ctabid-9%2Ctabid-45%2Ctabid-20%2Ctabid-32%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-18%2Ctabid-36%2Ctabid-34%2Ctabid-11%2Ctabid-46%2Ctabid-22%2Ctabid-24%2Ctabid-38%2Ctabid-3%2Ctabid-1%2Ctabid-30%2Ctabid-42%2Ctabid-40%2Ctabid-44%2Ctabid-28%2Ctabid-26%2Ctabid-47%2Ctabid-49#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowMajorGridLines) is true. 

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

The [MajorGridLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html?tabs=tabid-7%2Ctabid-5%2Ctabid-9%2Ctabid-45%2Ctabid-20%2Ctabid-32%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-18%2Ctabid-36%2Ctabid-34%2Ctabid-11%2Ctabid-46%2Ctabid-22%2Ctabid-24%2Ctabid-38%2Ctabid-3%2Ctabid-1%2Ctabid-30%2Ctabid-42%2Ctabid-40%2Ctabid-44%2Ctabid-28%2Ctabid-26%2Ctabid-47%2Ctabid-49#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorGridLineStyle) property in the chart axis is used to customize the appearance of major gridlines.

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

Minor gridlines will be added automatically when the minor tick lines is defined using the [MinorTicksPerInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html?tabs=tabid-1%2Ctabid-7%2Ctabid-5%2Ctabid-3%2Ctabid-9%2Ctabid-11#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorTicksPerInterval) property of the chart axis.

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

The [MinorGridLineStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html?tabs=tabid-1%2Ctabid-7%2Ctabid-5%2Ctabid-3%2Ctabid-9%2Ctabid-11#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorGridLineStyle) property in the chart axis is used to customize the appearance of minor gridlines.

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

