---
layout: post
title: Explode segments in WinUI Funnel Chart control | Syncfusion
description: Learn here all about Explode segments in Syncfusion WinUI Funnel Chart(SfFunnelChart) control with key features and more.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Explode segments in WinUI Funnel Chart (SfFunnelChart)

You can explode a funnel segment using the explodeIndex property. The explodeOffset property is used to specify the exploded segment’s distance. The following properties are used to explode the individual segments in Funnel.

[ExplodeAll]() - Used to explode all the segments of these series.
[ExplodeIndex]() - Used to explode any specific segment.
[ExplodeOffset]() - Used to define the explode distance like ExplodeRadius for Pie.
[ExplodeOnMouseClick]() - Used to explode the segment when segment is clicked.

## Explode Offset

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                Palette="BlueChrome"
                ExplodeIndex="3"  
                ExplodeOffset="70" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %} 

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ExplodeIndex = 3;
chart.ExplodeOffset = 70;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Explode segments in WinUI Funnel Chart](Explode-segments_images/WinUI_Funnel_chart_Explode_segments.png)

