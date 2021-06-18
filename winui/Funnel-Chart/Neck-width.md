---
layout: post
title: Neck width in WinUI Funnel Chart control | Syncfusion
description: Learn here all about Neck width in Syncfusion WinUI Funnel Chart(SfFunnelChart) control with key features.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Neck width in WinUI Funnel Chart (SfFunnelChart)

You can modify the neck width of funnel series using the [MinimumWidth]() property. It ranges from 0% to 100%.
The following code example shows how to use the funnel series:

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart"
        Palette="BlueChrome"
        MinimumWidth="20" 
        Height="388" Width="500" 
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
chart.MinimumWidth = 20;
chart.Height = 388;
chart.Width = 500;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Neck width support in WinUI Funnel Chart](Neck-width_images/WinUI_Funnel_chart_Neck_width.png)


