---
layout: post
title: Numerical Axis in WinUI Polar Chart control | Syncfusion
description: Learn here all about the numerical chart axis of Syncfusion WinUI Polar Chart (SfPolarChart) control and its customization in WPF Charts.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# NumericalAxis

## NumericalAxis in WinUI Polar Chart (SfPolarChart) 

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

![NumericalAxis support in WinUI Chart](Axis_images/Axis_img42.jpeg)


**Customizing** **the** **NumericalAxis** **Range**

[`Maximum`]() property used for setting the maximum value for the axis range and [`Minimum`]() property is used for setting the minimum value for the axis range.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfPolarChart.SecondaryAxis>
    <syncfusion:NumericalAxis Maximum="100" Minimum="0">
    </syncfusion:NumericalAxis>
</syncfusion:SfPolarChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.SecondaryAxis = new NumericalAxis()
{
    Maximum = 100,
    Minimum = 0,
};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Chart](Axis_images/Axis_img43.jpeg)


N> If  minimum or maximum value is set, the other value is calculated by default internally.

**StartRangeFromZero**

[`NumericalAxis`]() will calculate the range based on the data points binded to the axis. To start the range from zero have to define the [`StartRangeFromZero`]() property to `True`. The following code example demonstrates the NumericalAxis range starting from zero.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfPolarChart.SecondaryAxis>
    <syncfusion:NumericalAxis StartRangeFromZero="True">
    </syncfusion:NumericalAxis>
</syncfusion:SfPolarChart.SecondaryAxis>

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

![NumericalAxis customization support in WinUI Chart](Axis_images/Axis_img44.jpeg)


N> By default, Range is calculated between the minimum and maximum value of the data points.