---
layout: post
title: Explode segments in WinUI Chart control | Syncfusion
description: This section explains about how to explode single segment or all segments in Syncfusion WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Explode Segments in WinUI Chart (SfPyramidChart)

Exploding a segment is used to pull attention to a specific area of the pyramid. The following properties are used to explode the segments in the pyramid chart.

* [ExplodeIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeIndex) - Used to explode any specific segment.
* [ExplodeOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeOffset) - Used to define the explode distance of segment.
* [ExplodeOnTap](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeOnTap) - Used to explode the segment when segment is tapped/clicked.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                Palette="BlueChrome"
                ExplodeIndex="3"  
                ExplodeOffset="30" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ExplodeIndex = 3;
chart.ExplodeOffset = 30;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Explode segments in WinUI Chart](Explode-segments_images/WinUI_chart_explode_segments.png)
