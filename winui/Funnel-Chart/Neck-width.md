---
layout: post
title: Neck width in WinUI Chart control | Syncfusion
description: This section explains about how to customize the neck width in Syncfusion WinUI Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Neck Width in WinUI Chart (SfFunnelChart)

The neck width of funnel chart can be customized by using the [MinimumWidth]() property. The default value of [MinimumWidth]() property is 40. The following code example explains how to change the neck width.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart
        Palette="BlueChrome"
        MinimumWidth="20" 
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
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Neck width support in WinUI Chart](Neck-width_images/WinUI_chart_neck_width.png)

## Inverted Pyramid

The funnel chart can be customized to the inverted pyramid chart by setting the [MinimumWidth]() property to 0.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart
        Palette="BlueChrome"
        MinimumWidth="0" 
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
chart.MinimumWidth = 0;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Inversed Pyramid Chart in WinUI](Neck-width_images/WinUI_chart_inversed_pyramid.png)
