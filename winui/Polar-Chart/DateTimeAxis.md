---
layout: post
title: DateTime Axis in WinUI Polar Chart control | Syncfusion
description: Learn here all about the datetime chart axis of Syncfusion WinUI Polar Chart (SfPolarChart) control and its customization in WPF Charts.
platform: WinUI
control: SfPolarChart
documentation: ug
---

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
