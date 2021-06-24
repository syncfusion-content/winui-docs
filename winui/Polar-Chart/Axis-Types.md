---
layout: post
title:  Axis types in WinUI Polar Chart control | Syncfusion
description: Learn here all about axis types and its features in  Syncfusion WinUI Polar Chart (SfPolarChart) control and more.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Types of axis in WinUI Polar Chart (SfPolarChart) 

Polar chart supports the following types of chart axis.

* NumericalAxis
* CategoryAxis
* DateTimeAxis

## NumericalAxis

[`NumericalAxis`]() is used to plot numerical values to the chart. [`NumericalAxis`]() can be defined for both [`PrimaryAxis`]() and [`SecondaryAxis`](). The following code snippet shows how to define the [`NumericalAxis`]().

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart >

    <syncfusion:SfPolarChart.PrimaryAxis>
        <syncfusion:NumericalAxis/>
    </syncfusion:SfPolarChart.PrimaryAxis>
    <syncfusion:SfPolarChart.SecondaryAxis>
        <syncfusion:NumericalAxis/>
    </syncfusion:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.PrimaryAxis = new NumericalAxis();
chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![NumericalAxis support in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_NumericalAxis.png)

### Customizing the range

[`Maximum`]() property used for setting the maximum value for the axis range and [`Minimum`]() property is used for setting the minimum value for the axis range.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfPolarChart.SecondaryAxis>
    <syncfusion:NumericalAxis Minimum="10" Maximum="90" Interval="20">
    </syncfusion:NumericalAxis>
</syncfusion:SfPolarChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.SecondaryAxis = new NumericalAxis()
{
    Maximum = 90,
    Minimum = 10,
    Interval = 20,
};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_NumericalAxis_AxisRange.png)

N> If  minimum or maximum value is set, the other value is calculated by default internally.

### Start from zero

[`NumericalAxis`]() will calculate the range based on the data points binded to the axis. To start the range from zero have to define the [`StartRangeFromZero`]() property to `True`. The following code example demonstrates the NumericalAxis range starting from zero.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfPolarChart.SecondaryAxis>
    <syncfusion:NumericalAxis StartRangeFromZero="True">
    </syncfusion:NumericalAxis>
</syncfusion:SfPolarChart.SecondaryAxis>
...

{% endhighlight %}

{% highlight c# %}

...
chart.SecondaryAxis = new NumericalAxis()
{
   StartRangeFromZero = true
};
...

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_NumericalAxis_StartRangeFromZero.png)

N> By default, Range is calculated between the minimum and maximum value of the data points.

## Category Axis

[`CategoryAxis`]() is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here. The following code example initializes the [`CategoryAxis`]().

{% tabs %}

{% highlight xaml %}

<syncfusion:SfPolarChart.PrimaryAxis>
    <syncfusion:CategoryAxis/>
</syncfusion:SfPolarChart.PrimaryAxis>

<syncfusion:SfPolarChart.SecondaryAxis>
    <syncfusion:NumericalAxis/>
</syncfusion:SfPolarChart.SecondaryAxis>
...

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Polar Chart](Axis_Images/WinUI_PolarChart_CategoryAxis.png)

## DateTime Axis

[DateTimeAxis]() is used to plot `DateTime` values. The `DateTimeAxis` is widely used to make financial charts in places like the Stock Market, where index plotting is done every day.

<chart:SfPolarChart>
            
    <chart:SfPolarChart.PrimaryAxis>
        <chart:DateTimeAxis Interval="1" IntervalType="Months" LabelFormat="MMM/dd"/>
    </chart:SfPolarChart.PrimaryAxis>
            
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new DateTimeAxis()
{
    Interval = 1,
    IntervalType = DateTimeIntervalType.Months,
    LabelFormat = "MMM/dd",
};

chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![DateTimeAxis support in WinUIPolar  Chart](Axis_Images/WinUI_PolarChart_DateTimeAxis_LabelFormat.png)
