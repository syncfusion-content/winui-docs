---
layout: post
title: Bubble series in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Bubble series feature of Syncfusion WinUI Chart (SfCartesianChart) control with zero bubble support and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Bubble in WinUI Cartesian Chart (SfCartesianChart)

## Bubble 

[`BubbleSeries`]() is represented by closely packed circles, whose areas are proportional to the quantities. 

The size of the bubble series is relative proportional to the value bind with the series using [`Size`]()  property. You can set the constraints on this size using [`MinimumRadius`]() and [`MaximumRadius`]().

To render a cartesian chart bubble series, create an instance of [BubbleSeries]() and add to the Series collection property of SfCartesianChart as shown in the following code.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:BubbleSeries ItemsSource="{Binding Data}" XBindingPath="XValue" 
                        YBindingPath="YValue" Size="Size"
                        MinimumRadius="5" MaximumRadius="10"/>
    ...
<chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...

BubbleSeries series = new BubbleSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    Size = "Size",
    MinimumRadius = 5,
    MaximumRadius = 10
};

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![Bubble chart type in WinUI Cartesian Chart](Bubble_Images/bubble_chart.png)

**Show Zero Bubbles**

The zero size bubble segments can be enabled or disabled by using the [`ShowZeroBubbles`]() property. By default, the property value is `True`.

The following code illustrates how to set the value to the property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:BubbleSeries ItemsSource="{Binding Data}" XBindingPath="XValue" 
                        YBindingPath="YValue" Size="Size"
                        ShowZeroBubbles="True"/>
    ...
<chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...

BubbleSeries series = new BubbleSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    Size = "Size",
    ShowZeroBubbles = true,
};

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![ShowZeroBubbles support in WinUI Cartesian Chart](Bubble_Images/showzerobubble_true.png)

The following code example and screenshots describes when [`ShowZeroBubbles`]() value is `false`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:BubbleSeries ItemsSource="{Binding Data}" XBindingPath="XValue" 
                        YBindingPath="YValue" Size="Size"
                        ShowZeroBubbles="False"/>
    ...
<chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...

BubbleSeries series = new BubbleSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    Size = "Size",
    ShowZeroBubbles = false,
};

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![ShowZeroBubbles support in WinUI Cartesian Chart](Bubble_Images/showzerobubble_false.png)