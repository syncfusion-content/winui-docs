---
layout: post
title: Neck width in WinUI Funnel Chart control | Syncfusion
description: This section explains about how to customize the neck width in Syncfusion WinUI Funnel Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Neck width in WinUI Funnel Chart (SfFunnelChart)

The neck width of funnel chart can be customized by using the [MinimumWidth]() property. The following code example shows how to change the neck width.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart
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

