---
layout: post
title: Explode segments in WinUI Chart control | Syncfusion
description: This section explains about how to explode single segment or all segments in Syncfusion WinUI Chart (SfFunnelChart) control.
platform: WinUI 
control: SfFunnelChart
documentation: ug
---

# Explode Segments in WinUI Chart (SfFunnelChart)

Exploding a segment is used to pull attention to a specific area of the funnel. The following properties are used to explode the segments in the funnel chart.

* [ExplodeAll]() - Used to explode all the segments of these series.
* [ExplodeIndex]() - Used to explode any specific segment.
* [ExplodeOffset]() - Used to define the explode distance of segment.
* [ExplodeOnTap]() - Used to explode the segment when segment is tapped/clicked.

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

![Explode segments in WinUI Chart](Explode-segments_images/WinUI_chart_explode_segments.png)
