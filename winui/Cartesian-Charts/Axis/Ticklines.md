---
layout: post
title: Tick Lines in WinUI Chart | Syncfusion®
description: Tick lines in the WinUI Chart indicate axis intervals and support customization of size, position, style, and appearance settings.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: tick lines in winui chart, winui sfcartesianchart tick lines, winui chart tick lines customization, syncfusion winui chart tick lines.
---

# Tick Lines in WinUI Chart

Tick lines are the small lines which are drawn on the axis line representing the axis labels. Tick lines will be drawn outside of the axis by default. 

The minor tick lines can be added to the axis by defining the [MinorTicksPerInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorTicksPerInterval) property. This property will add the minor tick lines to every interval based on the value.

N> For category axis, minor tick lines are not applicable since it is rendered based on index positions.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis MinorTicksPerInterval="4"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis/>
    </chart:SfCartesianChart.YAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
NumericalAxis primaryAxis = new NumericalAxis()
{
   MinorTicksPerInterval = 4 
};

chart.XAxes.Add(primaryAxis);
chart.YAxes.Add(new NumericalAxis());

{% endhighlight %}

{% endtabs %}

## Size

Both major and minor tick lines height can be customized by using the [TickLineSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TickLineSize) and [MinorTickLineSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorTickLineSize) properties, respectively.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis MinorTickLineSize="10" MinorTicksPerInterval="4" TickLineSize="15"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis/>
    </chart:SfCartesianChart.YAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// Configure additional chart elements
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

Both major and minor tick lines can be customized by using the [MajorTickStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorTickStyle) and [MinorTickStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_MinorTickStyle) properties, respectively. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <!-- Configure additional chart elements -->
    <chart:SfCartesianChart.Resources>
        <Style TargetType="Line" x:Key="lineStyle">
            <Setter Property="StrokeThickness" Value="1"/>
            <Setter Property="Stroke" Value="Red"/>
        </Style>
    </chart:SfCartesianChart.Resources>

    <chart:SfCartesianChart.XAxes>
        <chart:NumericalAxis 
            MinorTicksPerInterval="4" 
            MinorTickStyle="{StaticResource lineStyle}"  
            MajorTickStyle="{StaticResource lineStyle}"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis/>
    </chart:SfCartesianChart.YAxes>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

// The 'lineStyle' resource is defined in XAML Resources and referenced here.
NumericalAxis primaryAxis = new NumericalAxis()
{
    MinorTicksPerInterval = 4,
    MajorTickStyle = chart.Resources["lineStyle"] as Style,
    MinorTickStyle = chart.Resources["lineStyle"] as Style 
};

chart.XAxes.Add(primaryAxis);
chart.YAxes.Add(new NumericalAxis());

{% endhighlight %}

{% endtabs %}

![Axis tick lines customization support in WinUI Chart](Axis_images/winui_chart_axis_tickline_style.png)

## See Also

* [How to customize the axis labels of WinUI Chart (SfCartesianChart)](https://support.syncfusion.com/kb/article/13013)