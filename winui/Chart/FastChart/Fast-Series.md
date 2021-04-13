---
layout: post
title: Fast Series in WinUI Chart control | Syncfusion
description: Learn about Fast Series support in Syncfusion WinUI Chart control and more details.
platform: WinUI
control: SfChart
documentation: ug
---

# Fast Series in WinUI Chart

## FastLine Chart

The [`FastLineSeries`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.FastLineSeries.html) is a special kind of line series that can render a collection with huge number of datapoints using the polyline segment. 

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
