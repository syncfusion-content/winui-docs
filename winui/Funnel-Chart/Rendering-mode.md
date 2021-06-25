---
layout: post
title: Rendering mode in WinUI Chart control | Syncfusion
description: This sections explains about the rendering mode types of Syncfusion WinUI Chart(SfFunnelChart) control
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Rendering mode in WinUI Chart (SfFunnelChart)

The [FunnelMode]() property defines the rendering mode of the funnel chart, which define where to bind your values (to height or width).The default value of [`FunnelMode`]() property is [ValueIsHeight]().  The following example demonstrates [ValueIsHeight]() and [ValueIsWidth]() of funnel mode.

**ValueIsHeight**

[ValueIsHeight]() is used to render the funnel chart segments based on the height for data point values

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

![Rendering mode with height in WinUI Chart](Rendering-mode_images/WinUI_funnel_chart_valueIsHeight.png)

**ValueIsWidth**

[ValueIsWidth]() is used to render the funnel chart segments based on the width for data point values.

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

![Rendering mode with width in WinUI Chart](Rendering-mode_images/WinUI_funnel_chart_valueIsWidth.png)

