---
layout: post
title: Explode Segments in WinUI Chart Control | Syncfusion
description: This section explains how to explode a single segment or all segments in the Syncfusion® WinUI Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Explode Segments in WinUI Chart (SfFunnelChart)

Exploding a segment is used to draw attention to a specific area of the funnel. The following properties are used to explode the segments in the funnel chart:

* [ExplodeIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_ExplodeIndex) - Used to explode a specific segment.
* [ExplodeOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_ExplodeOffset) - Used to define the explode distance of the segment.
* [ExplodeOnTap](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_ExplodeOnTap) - Used to explode the segment when it is tapped or clicked.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                ExplodeIndex="3"  
                ExplodeOffset="30" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ExplodeIndex = 3;
chart.ExplodeOffset = 30;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Explode segments in WinUI Chart](Explode-segments_Images/winui-chart_explode_segments.png)
