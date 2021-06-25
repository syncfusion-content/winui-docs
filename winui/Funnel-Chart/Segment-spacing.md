---
layout: post
title: Segment spacing in WinUI Chart control | Syncfusion
description: This section explains about how to set segment spacing for the Syncfusion WinUI Chart (SfFunnelChart) control
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Segment Spacing in WinUI Chart (SfFunnelChart)

The gap between each segment in the funnel chart can be set using the [GapRatio]() property. The default value of [GapRatio]() property property is 0 and its value ranges from 0 to 1.

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

![Segment spacing in WinUI Chart](Segment-spacing_Images/winui-chart_gap_ratio.png)
