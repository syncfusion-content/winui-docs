---
layout: post
title: Rendering mode in WinUI Pyramid Chart control | Syncfusion
description: This sections explains about the rendering mode of Syncfusion WinUI Pyramid Chart(SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Rendering mode in WinUI Pyramid Chart (SfPyramidChart)

The [PyramidMode]() is used to define the rendering mode of pyramid chart such as [Surface]() or [Linear](). The default value of [PyramidMode]() property is `Linear`.

## Pyramid mode as surface

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

![Rendering mode with area in WinUI Pyramid chart](Rendering-mode_images/WinUI_pyramid_chart_surface.png)

## Pyramid mode as linear

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

![Rendering mode with height in WinUI Pyramid chart](Rendering-mode_images/WinUI_pyramid_chart_linear.png)

