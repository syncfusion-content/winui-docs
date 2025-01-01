---
layout: post
title: Segment spacing in WinUI Chart control | Syncfusion
description: This section explains about how to set segment spacing for the Syncfusion® WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Segment Spacing in WinUI Chart (SfPyramidChart)

The gap between each segment in the pyramid chart can be set using the [GapRatio](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_GapRatio) property. The default value of [GapRatio](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_GapRatio) property is 0 and its value ranges from 0 to 1.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart"
                      ItemsSource="{Binding Data}" 
                      XBindingPath="Category" 
                      YBindingPath="Value" 
                      GapRatio="0.3">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.GapRatio = 0.3;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Segment spacing in WinUI Chart](Segment-spacing_images/WinUI_chart_gap_ratio.png)
