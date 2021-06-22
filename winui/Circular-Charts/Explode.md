---
layout: post
title: Explode in WinUI Circular Chart control | Syncfusion
description: Learn here all about explode support in Syncfusion WinUI Circular Chart(SfCircularChart) control with custom support and more.
platform: WinUI
control: SfCircularChart
documentation: ug
---

## Explode Segments

Highlighting the segment appearance of [SfCircularChart]() can be customize by using Explode support.

The following properties are used to explode the individual segments in Pie and Doughnut.

* [ExplodeAll]()  - Used to explode all the segments of these series.

* [ExplodeIndex]() - Used to explode any specific segment.

* [ExplodeRadius]() - Used to define the explode distance.

* [ExplodeOnMouseClick]() - Used to explode the segment when segment is clicked.

**Explode** **Index**

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries x:Name="PieSeries" ItemsSource="{Binding Data}"    
ExplodeIndex="2" ExplodeRadius="10" XBindingPath="Utilization" 
YBindingPath="ResponseTime" />

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Utilization",

    YBindingPath = "ResponseTime",

    ExplodeIndex = 2,

    ExplodeRadius = 10

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Exploding a segment of accumlation series in WinUI Chart](Series_images/pie_exploderadius.png)

N> We have defined ExplodeRadius as 30, by default its value is zero. So you need to define explode, when you set ExplodeIndex or ExplodeAll.

**Explode** **All**

{% tabs %}

{% highlight xaml %}

<chart:PieSeries  ExplodeAll="True" ExplodeRadius="15"

XBindingPath="Category" ItemsSource="{Binding Data}" 

YBindingPath="Value">

{% endhighlight %}

{% highlight c# %}

PieSeries series = new PieSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Category",

    YBindingPath = "Value",

    ExplodeAll = true,

    ExplodeRadius = 15

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Exploding all the segments of accumulation series in WinUI Chart](Series_images/pie_explodeall.png)
