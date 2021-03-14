---
layout: post
title: Fast Chart | SfChart | WinUI | Syncfusion
description: Fast Chart support which render collection of data points using polyline segment in WinUI Charts (SfChart).
platform: WinUI
control: SfChart
documentation: ug
---

# Fast Series in WinUI Charts (SfChart)

A fast series is a special kind of line chart that can render a collection with a huge number of data points. Fast series is rendered using a polyline segment.

## Fast Line

The [`FastLineSeries`]() is a special kind of line series that can render a collection with a huge number of datapoints. FastLine is rendered using polyline segment. 

{% tabs %}

{% highlight xaml %}

<chart:FastLineSeries x:Name="FastLineSeries" ItemsSource="{Binding Data}"

XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

FastLineSeries series = new FastLineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![FastLine chart type in WinUI]()