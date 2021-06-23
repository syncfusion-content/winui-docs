---
layout: post
title: Category Axis in WinUI Polar Chart control | Syncfusion
description: Learn here all about the category chart axis of Syncfusion WinUI Polar Chart (SfPolarChart) control and its customization in WPF Charts.
platform: WinUI
control: SfPolarChart
documentation: ug
---

## CategoryAxis in WinUI Polar Chart (SfPolarChart)

[`CategoryAxis`]() is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here. The following code example initializes the [`CategoryAxis`]().

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis>

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis();

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Polar Chart](Axis_images/Axis_img45.jpeg)