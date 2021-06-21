---
layout: post
title: Appearance in WinUI Polar Chart control | Syncfusion
description: This section explains about how to apply palettes and gradient in the Syncfusion WinUI Funnel Chart (SfPolarChart) control
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Appearance in WinUI Polar Chart (SfPolarChart)

The appearance of [SfPolarChart]() can be customize by using the predefined palettes, custom palettes and gradient that allows to enrich the application.

## Palettes

[SfPolarChart]() provides options to apply different kinds of palettes. We have some predefined palette such as

* Metro
* AutumnBrights
* FloraHues
* Pineapple
* TomatoSpectrum
* RedChrome
* PurpleChrome
* BlueChrome
* GreenChrome
* Elite
* LightCandy
* SandyBeach

### Applying palette to Series

Each palette applies a set of predefined brushes to the series in a predefined order. [Metro]() palette is the default palette. The following code example shows default Metro Palette for the polar chart series.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart"
                    Palette="Metro"
                    GridLineType="Polygon">
        ...
        <chart:SfPolarChart.Series>
            <chart:PolarLineSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Tree" Label="Tree">
            </chart:PolarLineSeries>

            <chart:PolarLineSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Weed" Label="Weed">
            </chart:PolarLineSeries>

            <chart:PolarLineSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Flower" Label="Flower">
            </chart:PolarLineSeries>
        </chart:SfPolarChart.Series>
        ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Palette = ChartColorPalette.Metro;
chart.GridLineType = PolarChartGridLineType.Polygon;
...
PolarAreaSeries series1 = new PolarAreaSeries();
series1.XBindingPath = "Direction";
series1.YBindingPath = "Tree";
series1.ItemsSource = viewModel.PlantDetails;

PolarAreaSeries series2 = new PolarAreaSeries();
series2.XBindingPath = "Direction";
series2.YBindingPath = "Weed";
series2.ItemsSource = viewModel.PlantDetails;

PolarAreaSeries series3 = new PolarAreaSeries();
series3.XBindingPath = "Direction";
series3.YBindingPath = "Flower";
series3.ItemsSource = viewModel.PlantDetails;
...
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Predefined palette in WinUI Polar Chart](Appearance_images/WinUI_PolarChart_default_metro_palette.png)

The following code example defined [`Palette`]() as [`BlueChrome`]().

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart" 
                Palette="BlueChrome"
                GridLineType="Polygon">
                ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Palette = ChartColorPalette.BlueChrome;
chart.GridLineType = PolarChartGridLineType.Polygon;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Palette support in WinUI Polar Chart](Appearance_images/WinUI_PolarChart_BlueChrome.png)

## Custom palette

[`SfPolarChart`]() provides support to define own brushes for chart with preferred order by using [`CustomBrushes`]() property of [`ChartColorModel`]() and [`Palette`]() value as [`Custom`]() as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart x:Name="chart" 
                Palette="Custom"
                GridLineType="Polygon">

    <chart:SfPolarChart.ColorModel>
        <chart:ChartColorModel>
            <chart:ChartColorModel.CustomBrushes>
                <SolidColorBrush Color="#0078DE" />
                <SolidColorBrush Color="#00CC6A" />
                <SolidColorBrush Color="#B146C2" />
            </chart:ChartColorModel.CustomBrushes>
        </chart:ChartColorModel>
    </chart:SfPolarChart.ColorModel>
. . .
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
ChartColorModel colorModel = new ChartColorModel();
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 120, 222)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 204, 106)));
colorModel.CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 177, 70, 194)));
chart.ColorModel = colorModel;
chart.Palette = ChartColorPalette.Custom;
. . .            
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom palette in WinUI polar Chart](Appearance_images/WinUI_PolarChart_CustomPalette.png)

