---
layout: post
title: Rendering Mode in WinUI Chart Control | Syncfusion
description: This section explains the rendering surface mode and linear mode of the Syncfusion® WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Rendering Mode in WinUI Chart (SfPyramidChart)

The [Mode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_Mode) property is used to define the rendering mode of the pyramid chart, such as [Surface](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html#Syncfusion_UI_Xaml_Charts_ChartPyramidMode_Surface) or [Linear](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html#Syncfusion_UI_Xaml_Charts_ChartPyramidMode_Linear). The default value of the [Mode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_Mode) property is `Linear`.

## Surface Mode

The [Surface](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html#Syncfusion_UI_Xaml_Charts_ChartPyramidMode_Surface) mode is used to render the area of pyramid chart segments based on data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart"
                      ItemsSource="{Binding Data}" 
                      XBindingPath="Category" 
                      YBindingPath="Value" 
                      Mode="Surface">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
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

The [Linear](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartPyramidMode.html#Syncfusion_UI_Xaml_Charts_ChartPyramidMode_Linear) mode is used to render the height of pyramid chart segments based on data point values.

{% tabs %} 

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart"
                      ItemsSource="{Binding Data}" 
                      XBindingPath="Category" 
                      YBindingPath="Value" 
                      Mode="Linear">
</chart:SfPyramidChart>
 
{% endhighlight %}

{% highlight C# %}

SfPyramidChart chart = new SfPyramidChart();
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.Mode = ChartPyramidMode.Linear;
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rendering mode with height in WinUI chart](Rendering-mode_images/WinUI_chart_linear.png)
