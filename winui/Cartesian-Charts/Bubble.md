---
layout: post
title: Bubble Chart in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about the bubble series and its features in Syncfusion WinUI Cartesian Chart (SfCartesianChart) control.
platform: WinUI
control: SfChart
documentation: ug
---

# Bubble Chart in WinUI Cartesian Chart (SfCartesianChart)

## Bubble Chart

The [`BubbleSeries`]() is represented by closely packed circles, whose areas are proportional to the quantities. The size of the bubble series is relative proportional to the value bind with the series using the [`Size`]()  property. You can set the constraints on this size using the [`MinimumRadius`]() and [`MaximumRadius`]() properties.

To render a bubble series, create an instance of [BubbleSeries]() and add to the [Series]() collection property of [SfCartesianChart]() as shown in the following code.

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

## Show zero size bubbles

The zero size bubble segments can be enabled or disabled by using the [`ShowZeroBubbles`]() property. The defaule of this property is `True`.

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

![Show zero size bubbles support in WinUI Cartesian Chart](Bubble_Images/showzerobubble_true.png)

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

