---
layout: post
title: Start Angle in WinUI Polar Chart control | Syncfusion
description: This sections explains about the polar StartAngle in Syncfusion WinUI Polar Chart(SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Start angle in WinUI Polar Charts (SfPolarChart)

SfPolarChart [StartAngle]() property is used to render the polar chart axes on 0, 90, 180 and 270 degrees. The [StartAngle]() property is of type [ChartPolarAngle]() and its default value is [Rotate270]().

### Rotate0

The below code snippet explains how the axes of polar chart has been rotated when [StartAngle]() value is Rotate0,

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

### Rotate90

The below code snippet explains how the axes of series has been rotated when [StartAngle]() value is Rotate90,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart StartAngle="Rotate90">
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.StartAngle = ChartPolarAngle.Rotate90;
...

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI polar chart](StartAngle_Images/WinUI_PolarChart_Rotate90.png)

### Rotate180

The below code snippet explains how the axes of series has been rotated when [StartAngle]() value is Rotate180,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart StartAngle="Rotate180">
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.StartAngle = ChartPolarAngle.Rotate180;
...

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI polar chart](StartAngle_Images/WinUI_PolarChart_Rotate180.png)

### Rotate270

The below code snippet explains how the axes of series has been rotated, when [StartAngle]() value is Rotate270,

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart StartAngle="Rotate270">
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.StartAngle = ChartPolarAngle.Rotate270;
...

{% endhighlight %}

{% endtabs %}

![Rotation support for polar series in WinUI polar chart](StartAngle_Images/WinUI_PolarChart_Rotate270.png)