---
layout: post
title: Rendering mode in WinUI Chart control | Syncfusion
description: This sections explains about the rendering surface mode and linear mode of Syncfusion WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Rendering Mode in WinUI Chart (SfPyramidChart)

The [Mode]() property is used to define the rendering mode of pyramid chart such as [Surface]() or [Linear](). The default value of [Mode]() property is `Linear`.

## Surface Mode

The [Surface]() mode is used to rendering the area of pyramid chart segments based on data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category" 
                YBindingPath="Value" 
                Mode="Surface">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartPyramidMode.Surface;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode with area in WinUI chart](Rendering-mode_images/WinUI_chart_surface.png)

## Linear Mode

The [Linear]() mode is used to rendering the height of pyramid chart segments based on data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart"
                Palette="BlueChrome"
                ItemsSource="{Binding Data}" 
                XBindingPath="Category" 
                YBindingPath="Value" 
                Mode="ValueIsWidth">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartPyramidMode.Linear;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode with height in WinUI chart](Rendering-mode_images/WinUI_chart_linear.png)
