---
layout: post
title: Explode Segments in WinUI Pyramid Chart | Syncfusion®
description: Explode segments in the WinUI Pyramid Chart emphasize individual or multiple chart segments for improved data visibility and analysis.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Explode segments in WinUI pyramid charts

Exploding a segment is used to draw attention to a specific area of the pyramid. The following properties are used to explode the segments in the pyramid chart.

* [ExplodeIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeIndex) - Used to explode any specific segment.
* [ExplodeOffset](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeOffset) - Used to define the explode distance of the segment.
* [ExplodeOnTap](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_ExplodeOnTap) - Used to explode the segment when it is tapped/clicked.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart 
    x:Name="chart" 
    ExplodeIndex="3"  
    ExplodeOffset="30" 
    ItemsSource="{Binding Data}" 
    XBindingPath="Category"
    YBindingPath="Value">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();

chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() 
{ 
    Path = new PropertyPath("Data") 
});

chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.ExplodeIndex = 3;
chart.ExplodeOffset = 30;

// Configure additional chart elements
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Explode segments in WinUI Chart](Explode-segments_images/WinUI_chart_explode_segments.png)
