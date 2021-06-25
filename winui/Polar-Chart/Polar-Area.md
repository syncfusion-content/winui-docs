---
layout: post
title: Polar area chart | SfPolarChart | Syncfusion
description: Learn here all about the polar area chart and its features in Syncfusion WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Polar Area Chart in WinUI Charts (SfPolarChart)

To render a area series in polar chart, create an instance of the [PolarAreaSeries]() and add it to the [Series]() collection property of [SfPolarChart]().

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
...

{% endhighlight %}

{% endtabs %}

![PolarAreaSeries in WinUI chart](PolarArea_Images/WinUI_PolarChart_PolarAreaSeries.png)

## Grid line type 

The [GridLineType]() property is used to change the rendering type of axis grid lines. The default value of [GridLineType]() is `Circle`. By changing the grid line type as `Polygon`, we can shown the polar chart similar like spider chart or web chart. 

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

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![Spider/Web chart](PolarArea_Images/WinUI_PolarChart_GridlineType_polygon.png)

## Closing Path

[IsClosed]() property is used to render the series with or without closed path. The default value of [IsClosed]() is `true`. 

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

![Closing path support in WinUI chart](PolarArea_Images/WinUI_PolarChart_IsClosed.png)

