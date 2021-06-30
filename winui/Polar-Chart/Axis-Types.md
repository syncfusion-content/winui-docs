---
layout: post
title:  Axis types in WinUI Chart control | Syncfusion
description: Learn here all about the axis types and its features in  Syncfusion WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Types of Axis in WinUI Chart (SfPolarChart) 

Polar chart supports the following types of chart axis.

* CategoryAxis
* NumericalAxis
* DateTimeAxis

## Category Axis

The [CategoryAxis]() is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>

    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis/>
    </chart:SfPolarChart.PrimaryAxis>

    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Chart](Axis_Images/WinUI_Chart_CategoryAxis.png)

## Numerical Axis

The [NumericalAxis]() is used to plot the numerical values to the chart. [`NumericalAxis`]() can be defined for both [`PrimaryAxis`]() and [`SecondaryAxis`]().

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>

    <chart:SfPolarChart.PrimaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.PrimaryAxis>
    
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
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

![Numerical Axis support in WinUI Chart](Axis_Images/WinUI_Chart_NumericalAxis.png)

### Customizing the range

[Maximum]() and [Minimum]() properties of axis is used for setting the maximum and minimum value of the axis range respectively.

N> If  minimum or maximum value is set, the other value is calculated by default internally.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis Minimum="10" Maximum="90" Interval="20" />
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

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
...

{% endhighlight %}

{% endtabs %}

![Numerical axis range in WinUI Chart](Axis_Images/WinUI_Chart_NumericalAxis_AxisRange.png)

### Start from zero

[NumericalAxis]() will calculate the start range based on the data points binded to the chart. By defining the [StartRangeFromZero]() property to True, numerical axis start the range from zero.

N> By default, axis range is calculated between the minimum and maximum value of the data points.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis StartRangeFromZero="True" />
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.SecondaryAxis = new NumericalAxis()
{
   StartRangeFromZero = true
};
...

{% endhighlight %}

{% endtabs %}

![NumericalAxis support in WinUI Chart](Axis_Images/WinUI_Chart_NumericalAxis_StartRangeFromZero.png)

## DateTime Axis

The [DateTimeAxis]() is used to plot the chart with `DateTime` values.

{% tabs %}

{% highlight xaml %}

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

![DateTimeAxis support in WinUI Chart](Axis_Images/WinUI_Chart_DateTimeAxis.png)
