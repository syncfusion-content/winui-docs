---
layout: post
title: Bubble and Scatter in WinUI Chart control | Syncfusion
description: Learn here all about Bubble and Scatter feature of Syncfusion WinUI Chart control with zero bubble support and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Bubble and Scatter in WinUI Chart

## Bubble 

[`BubbleSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#) is represented by closely packed circles, whose areas are proportional to the quantities. 

The size of the bubble series is relative proportional to the value bind with the series using [`Size`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_Size)  property. You can set the constraints on this size using [`MinimumRadius`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_MaximumRadius) and [`MaximumRadius`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_MaximumRadius).

{% tabs %}

{% highlight xaml %}

<chart:BubbleSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue" Size="Size" MinimumRadius="5" MaximumRadius="10"/>

{% endhighlight %}

{% highlight c# %}

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

{% endhighlight %}

{% endtabs %}

![Bubble chart type in WinUI](Series_images/bubble_chart.png)

**Show Zero Bubbles**

The zero size bubble segments can be enabled or disabled by using the [`ShowZeroBubbles`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_ShowZeroBubblesProperty) property. By default, the property value is True.

The following code illustrates how to set the value to the property.

{% tabs %}

{% highlight xaml %}

<chart:BubbleSeries ShowZeroBubbles="True">
</chart:BubbleSeries>

{% endhighlight %}

{% highlight c# %}

BubbleSeries series = new BubbleSeries();

series.ShowZeroBubbles = true;

{% endhighlight %}

{% endtabs %}

![ShowZeroBubbles support in WinUI](Series_images/showzerobubble_true.png)

The following code example and screenshots describes when [`ShowZeroBubbles`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_ShowZeroBubblesProperty) value is false.

{% tabs %}

{% highlight xaml %}

<chart:BubbleSeries ShowZeroBubbles="False">
</chart:BubbleSeries>

{% endhighlight %}

{% highlight c# %}

BubbleSeries series = new BubbleSeries();

series.ShowZeroBubbles = false;

{% endhighlight %}

{% endtabs %}

![ShowZeroBubbles support in WinUI Chart](Series_images/showzerobubble_false.png)

## Scatter

[`ScatterSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#) is similar to bubble series when each point being represented by an ellipse with equal size. This size can be defined by using [`ScatterHeight`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_ScatterHeight) and [`ScatterWidth`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ScatterSeries.html#Syncfusion_UI_Xaml_Charts_ScatterSeries_ScatterWidth) properties.

{% tabs %}

{% highlight xaml %}

<chart:ScatterSeries ScatterHeight="7" ScatterWidth="7" ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

ScatterSeries series = new ScatterSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

    ScatterHeight = 7,

    ScatterWidth = 7,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Scatter chart type in WinUI](Series_images/scatter_chart.png)
