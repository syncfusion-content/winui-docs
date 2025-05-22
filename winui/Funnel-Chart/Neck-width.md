---
layout: post
title: Neck Width in WinUI Chart Control | Syncfusion
description: This section explains how to customize the neck width in the Syncfusion® WinUI Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Neck Width in WinUI Chart (SfFunnelChart)

The neck width of the funnel chart can be customized using the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property. The default value of the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property is 40. The following code example demonstrates how to change the neck width.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart MinimumWidth="20" 
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
chart.MinimumWidth = 20;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Neck width support in WinUI Chart](Neck-width_Images/winui-chart_Neck_width.png)

## Inverted Pyramid

The funnel chart can be transformed into an inverted pyramid chart by setting the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property to 0.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart MinimumWidth="0" 
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
chart.MinimumWidth = 0;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Inversed Pyramid Chart in WinUI](Neck-width_Images/winui-chart_inversed_pyramid.png)
