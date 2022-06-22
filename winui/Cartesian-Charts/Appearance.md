---
layout: post
title: Appearance in WinUI Chart control | Syncfusion
description: This section explains about how to apply palettes and gradient in the Syncfusion WinUI Chart(SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Appearance in WinUI Chart (SfCartesianChart)

The appearance of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) can be customized by using the predefined palettes, custom palettes and gradient, which allows to enrich the application.

## Applying PaletteBrushes for Chart

By default, chart applies a set of predefined brushes to the series in a predefined order. [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) provides [PaletteBrushes] property for applying various kinds of custom palettes brushes.

### Predefined PaletteBrushes

Currently, Chart supports only one predefined palette and it is the default palette for SfCartesianChart. The following screenshot shows the default appearance of multiple series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart x:Name="chart">

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Predefined PaletteBrushes in WinUI Chart](Appearance_images/WinUI_chart_predefined_palette.png)

### Custom PaletteBrushes

[SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) provides support to define own brushes for the chart with preferred order by using the [PaletteBrushes]() property, as shown in the following code example.

## Applying PaletteBrushes for Series

Cartesian chart provides support to set the palette to series for applying predefined brushes to the segment. The following code example shows you how to set the [PaletteBrushes]() for the series.

{% tabs %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
List<Brush> CustomBrushes = new List<Brush>();
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 188, 212)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    PaletteBrushes = CustomBrushes,
};
. . .
chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom PaletteBrushes in WinUI Chart](Appearance_images/WinUI_chart_custom_palette.png)

## Applying Gradient

Gradient for the chart can be set by using the [PaletteBrushes]() property with the help of `LinearGradientBrush` or `RadialGradientBrush`.

The following code sample and screenshot illustrates how to apply the gradient brushes for the series using the [PaletteBrushes]() property.

{% tabs %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
List<Brush> CustomBrushes = new List<Brush>();
LinearGradientBrush gradientColor1 = new LinearGradientBrush();
GradientStop stop1 = new GradientStop() { Offset = 1, Color = Color.FromRgb(255, 231, 199) };
GradientStop stop2 = new GradientStop() { Offset = 0, Color = Color.FromRgb(252, 182, 159) };
gradientColor1.GradientStops.Add(stop1);
gradientColor1.GradientStops.Add(stop2);
LinearGradientBrush gradientColor2 = new LinearGradientBrush();
stop1 = new GradientStop() { Offset = 1, Color = Color.FromRgb(250, 221, 125) };
stop2 = new GradientStop() { Offset = 0, Color = Color.FromRgb(252, 204, 45) };
gradientColor2.GradientStops.Add(stop1);
gradientColor2.GradientStops.Add(stop2);
...
CustomBrushes.Add(gradientColor1);
CustomBrushes.Add(gradientColor2);
...
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    PaletteBrushes = CustomBrushes,
};
chart.Series.Add(series);
. . .            
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Gradient support in WinUI Chart](Appearance_images/WinUI_chart_gradient_color.png)