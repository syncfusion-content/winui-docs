---
layout: post
title: Fast Chart | SfChart | WinUI | Syncfusion
description: This section explains about the fast line chart and its properties to create a high performance chart in WinUI Charts (SfChart).
platform: WinUI
control: SfChart
documentation: ug
---

# FastLine Series in WinUI Charts (SfChart)

## FastLine Chart

The [`FastLineSeries`]() is a special kind of line series that can render a collection with huge number of datapoints using the polyline segment. 

{% tabs %}

{% highlight xaml %}

<chart:FastLineSeries ItemsSource="{Binding Data}"

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

![FastLine chart type in WinUI](FastChart_images/fastline_chart.png)