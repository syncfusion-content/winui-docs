---
layout: post
title: PolarAreaSeries in WinUI Polar Chart control | Syncfusion
description: Learn all about the PolarAreaSeries support in Syncfusion WinUI Polar Chart(SfPolarChart) control, its elements and more details.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# PolarAreaSeries in WinUI Polar Charts (SfPolarChart)

To render a polar or radar chart with area type, create an instance of the [PolarAreaSeries]() and add it to the [PolarChart]() [Series]() collection property. The following code example shows how to use [PolarAreaSeries]().

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart Palette="BlueChrome">
...
    <chart:SfPolarChart.Series>
        <chart:SfPolarChart.Series>
            <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Tree" Label="Tree">
            </chart:PolarAreaSeries>

            <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Weed" Label="Weed">
            </chart:PolarAreaSeries>

            <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                        XBindingPath="Direction"
                        YBindingPath="Flower" Label="Flower">
            </chart:PolarAreaSeries>
        </chart:SfPolarChart.Series>

    </chart:SfPolarChart.Series>
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.Palette = ChartColorPalette.BlueChrome;
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
chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);

{% endhighlight %}

{% endtabs %}

![PolarAreaSeries in WinUI polar chart](PolarArea_Images/WinUI_PolarChart_PolarAreaSeries.png)

## PolarChart GridLineType

The PolarChart [GridLineType]() property used to change the grid line type as `Circle` or `Polygon`. The PolarChart default [GridLineType]() value is `Circle` and type of `PolarChartGridLineType`. The following code example show the `PolarAreaSeries` with [GridLineType]() as `Polygon`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart GridLineType="Polygon">
...
    <chart:SfPolarChart.Series>
        <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                    XBindingPath="Direction"
                    YBindingPath="Tree" >
        </chart:PolarAreaSeries>
    </chart:SfPolarChart.Series>
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.GridLineType= PolarChartGridLineType.Polygon;
...
PolarAreaSeries series = new PolarAreaSeries();
series.XBindingPath = "Direction";
series.YBindingPath = "Tree";
series.ItemsSource = viewModel.PlantDetails;
...
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![PolarAreaSeries in WinUI polar chart polygon](PolarArea_Images/WinUI_PolarChart_GridlineType_polygon.png)

## IsClosed

[PolarAreaSeries]() [IsClosed]() property used to draw the polar arew with or without closed area path. The default value of [IsClosed]() is `true`. The following code example of the [IsClosed]() value as `false`.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart GridLineType="Polygon">
...
    <chart:SfPolarChart.Series>
        <chart:PolarAreaSeries ItemsSource="{Binding PlantDetails}" 
                    XBindingPath="Direction"
                    YBindingPath="Tree" 
                    IsClosed="False">
        </chart:PolarAreaSeries>
    </chart:SfPolarChart.Series>
...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.GridLineType= PolarChartGridLineType.Polygon;
...
PolarAreaSeries series = new PolarAreaSeries();
series.XBindingPath = "Direction";
series.YBindingPath = "Tree";
series.ItemsSource = viewModel.PlantDetails;
series.IsClosed= false;
...
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Closed PolarAreaSeries series in WinUI polar chart](PolarArea_Images/WinUI_PolarChart_IsClosed.png)