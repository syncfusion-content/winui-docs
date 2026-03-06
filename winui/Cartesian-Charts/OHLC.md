---
layout: post
title: OHLC Chart in WinUI Chart control | Syncfusion
description: Learn all about OHLC chart and its features in Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: winui
control: SfCartesianChart
documentation: ug
keywords: winui ohlc chart, winui chart ohlc type, ohlc chart customization winui, syncfusion winui ohlc chart, winui cartesian ohlc visualization.
---

# OHLC Chart in WinUI Chart

OHLC (Open-High-Low-Close) charts represent the price movement of an asset over a specific period. Each data point requires the X-value, open, high, low and close values. To render an OHLC chart in WinUI, use the `HiLoOpenCloseSeries` and add it to the `Series` collection of `SfCartesianChart`.

A collection of five values is required to plot a point on an OHLC chart, for example:

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.PrimaryAxis>
            <chart:CategoryAxis />
        </chart:SfCartesianChart.PrimaryAxis>

        <chart:SfCartesianChart.SecondaryAxis>
            <chart:NumericalAxis />
        </chart:SfCartesianChart.SecondaryAxis>

        <chart:HiLoOpenCloseSeries ItemsSource="{Binding StockData}"
                                    XBindingPath="Year"
                                    Open="Open"
                                    High="High"
                                    Low="Low"
                                    Close="Close"/>
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

var series = new HiLoOpenCloseSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
};

chart.Series.Add(series);
this.Content = chart;
{% endhighlight %}

{% highlight VM %}

ObservableCollection<Model> StockData = new ObservableCollection<Model>();
StockData.Add(new Model { Year = "2000", High = 50, Low = 40, Open = 47, Close = 45 });
StockData.Add(new Model { Year = "2001", High = 50, Low = 35, Open = 45, Close = 40 });
StockData.Add(new Model { Year = "2002", High = 40, Low = 30, Open = 37, Close = 40 });
StockData.Add(new Model { Year = "2003", High = 50, Low = 35, Open = 40, Close = 45 });
StockData.Add(new Model { Year = "2004", High = 45, Low = 30, Open = 35, Close = 32 });
StockData.Add(new Model { Year = "2005", High = 50, Low = 35, Open = 40, Close = 45 });
StockData.Add(new Model { Year = "2006", High = 40, Low = 31, Open = 36, Close = 34 });
StockData.Add(new Model { Year = "2007", High = 48, Low = 38, Open = 43, Close = 40 });
StockData.Add(new Model { Year = "2008", High = 55, Low = 45, Open = 48, Close = 50 });
StockData.Add(new Model { Year = "2009", High = 45, Low = 30, Open = 35, Close = 40 });
StockData.Add(new Model { Year = "2010", High = 50, Low = 40, Open = 40, Close = 35 });

{% endhighlight %}

{% endtabs %}

![OHLC chart type in WinUI Chart](Chart-types_images/OHLCBasicRendering.png)

## Bull and Bear Color

Use `BullishBrush` to specify the fill color for increasing segments (bull) and `BearishBrush` for decreasing segments (bear).

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.PrimaryAxis>
            <chart:CategoryAxis />
        </chart:SfCartesianChart.PrimaryAxis>

        <chart:SfCartesianChart.SecondaryAxis>
            <chart:NumericalAxis />
        </chart:SfCartesianChart.SecondaryAxis>

        <chart:HiLoOpenCloseSeries ItemsSource="{Binding StockData}"
                                    XBindingPath="Year"
                                    Open="Open"
                                    High="High"
                                    Low="Low"
                                    Close="Close"
                                    BullishBrush="Blue"
                                    BearishBrush="Orange"/>
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

var series = new HiLoOpenCloseSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
    BullishBrush = Colors.Blue,
    BearishBrush = Colors.Orange,
};

chart.Series.Add(series);
this.Content = chart;
{% endhighlight %}

{% endtabs %}

![OHLC chart fill color in WinUI Chart](Chart-types_images/OhlcFillColor.png)

## Segment Width

The `SegmentWidth` property gets or sets a value to change the width of the data points (candles) across the series. It accepts values between 0 and 1; the default value is 0.8. A value of 1.0 makes the candle occupy the full category width, while smaller values make the candle narrower.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.PrimaryAxis>
            <chart:CategoryAxis />
        </chart:SfCartesianChart.PrimaryAxis>

        <chart:SfCartesianChart.SecondaryAxis>
            <chart:NumericalAxis />
        </chart:SfCartesianChart.SecondaryAxis>

        <chart:HiLoOpenCloseSeries ItemsSource="{Binding StockData}"
                                    XBindingPath="Year"
                                    Open="Open"
                                    High="High"
                                    Low="Low"
                                    Close="Close"
                                    SegmentWidth="0.4"/>
    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

var series = new HiLoOpenCloseSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
    SegmentWidth = 0.4
};

chart.Series.Add(series);
this.Content = chart;
{% endhighlight %}

{% endtabs %}

![OHLC chart segment width in WinUI Chart](Chart-types_images/OhlcSegmentWidth.png)
