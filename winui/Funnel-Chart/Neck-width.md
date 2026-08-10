---
layout: post
title: Neck Width in WinUI Funnel Chart | Syncfusion®
description: Neck width in the WinUI Funnel Chart controls the width of the funnel neck, enabling customization of chart appearance and data presentation.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Neck Width in WinUI Funnel Chart

The neck width of the funnel chart can be customized by using the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property. The default value of the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property is 40. The following code example explains how to change the neck width.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart 
    MinimumWidth="20" 
    ItemsSource="{Binding Data}" 
    XBindingPath="Category"
    YBindingPath="Value">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();

chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() 
{ 
    Path = new PropertyPath("Data")    
});

chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.MinimumWidth = 20;

// Configure additional chart elements
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Neck width support in WinUI Chart](Neck-width_Images/winui-chart_Neck_width.png)

## Inverted Pyramid

The funnel chart can be customized to the inverted pyramid chart by setting the [MinimumWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_MinimumWidth) property to 0.

{% tabs %} 

{% highlight xaml %}

<chart:SfFunnelChart 
    MinimumWidth="0" 
    ItemsSource="{Binding Data}" 
    XBindingPath="Category"
    YBindingPath="Value">
</chart:SfFunnelChart>
 
{% endhighlight %}

{% highlight C# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding()
{ 
    Path = new PropertyPath("Data")
});

chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.MinimumWidth = 0;

// Configure additional chart elements
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Inverted Pyramid Chart in WinUI](Neck-width_Images/winui-chart_inversed_pyramid.png)
