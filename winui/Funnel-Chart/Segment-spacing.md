---
layout: post
title: Segment spacing in WinUI Funnel Chart control | Syncfusion
description: Learn here all about Segment spacing in Syncfusion WinUI Funnel Chart(SfFunnelChart) control with key features and more.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Segment spacing in WinUI Funnel Chart (SfFunnelChart)

## Gap Ratio

The gap between each segment using GapRatio property as in the following code example.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart"
        Palette="BlueChrome"
        ItemsSource="{Binding Data}" 
        XBindingPath="Category" 
        YBindingPath="Value" 
        GapRatio="0.5">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %} 

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.GapRatio = 0.5;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Gap Ratio in WinUI Funnel Chart](Segment-spacing_images/WinUI_Funnel_chart_Gap_Ratio.png)

