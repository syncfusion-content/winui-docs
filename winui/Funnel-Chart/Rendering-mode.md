---
layout: post
title: Rendering mode in WinUI Funnel Chart control | Syncfusion
description: Learn here all about Rendering mode in Syncfusion WinUI Funnel Chart(SfFunnelChart) control with key features and more.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Rendering mode in WinUI Funnel Chart (SfFunnelChart)

The FunnelMode defines a rendering mode for the funnel series which define, where to bind your values (to height or width). The following example demonstrates [ValueIsHeight]() and [ValueIsWidth]() funnel mode:

**ValueIsHeight**

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category" 
                YBindingPath="Value" 
                Mode="ValueIsHeight">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %} 

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartFunnelMode.ValueIsHeight;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode in WinUI Funnel Chart](Rendering-mode_images/WinUI_Funnel_chart_ValueIsHeight_mode.png)

**ValueIsWidth**

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category" 
                YBindingPath="Value" 
                Mode="ValueIsWidth">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %} 

SfFunnelChart chart = new SfFunnelChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartFunnelMode.ValueIsWidth;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode in WinUI Funnel Chart](Rendering-mode_images/WinUI_Funnel_chart_ValueIsWidth_mode.png)





