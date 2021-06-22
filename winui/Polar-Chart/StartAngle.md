---
layout: post
title: Start Angle in WinUI Polar Chart control | Syncfusion
description: This sections explains about how to change the position of axis in Syncfusion WinUI Polar Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Rendering position in WinUI Polar Chart (SfPolarChart)

PolarChart provide support to change the rendering position of the axes on 0, 90, 180 and 270 degrees using the [StartAngle]() property. The [StartAngle]() property is of type [ChartPolarAngle]() and its default value is [Rotate270]().

The below code snippet explains how the axes of polar chart has been rotated when [StartAngle]() value is Rotate0.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart StartAngle="Rotate0">
...
</chart:SfPolarChart>


{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.StartAngle = ChartPolarAngle.Rotate0;
...

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI polar chart](StartAngle_Images/WinUI_PolarChart_Rotate0.png)