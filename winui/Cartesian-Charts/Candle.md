---
layout: post
title: Candle Chart in WinUI Chart control | Syncfusion
description: Learn all about candle chart and its features in Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: winui
control: SfCartesianChart
documentation: ug
keywords: winui candle chart, candle chart customization winui, syncfusion winui candle chart, cartesian candle chart winui, winui stock chart.
---

# Candle Chart in WinUI Chart

Candle charts (candlestick charts) show price movement of an asset over time using candlesticks that encode open, high, low and close values. In WinUI, use the `CandleSeries` and add it to `SfCartesianChart.Series`.

The same five-value data collection used for OHLC applies to Candle charts:

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>
        <chart:SfCartesianChart.PrimaryAxis>
            <chart:CategoryAxis />
        </chart:SfCartesianChart.PrimaryAxis>

        <chart:SfCartesianChart.SecondaryAxis>
            <chart:NumericalAxis />
        </chart:SfCartesianChart.SecondaryAxis>

        <chart:CandleSeries ItemsSource="{Binding StockData}"
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

var series = new CandleSeries()
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

![Candle chart type in WinUI Chart](Chart-types_images/CandleBasicRendering.png)

## Bull and Bear Color

Set `BullishBrush` for rising candles and `BearishBrush` for falling candles.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.XAxes>
            <chart:CategoryAxis/>
        </chart:SfCartesianChart.XAxes>

        <chart:SfCartesianChart.YAxes>
            <chart:NumericalAxis/>
        </chart:SfCartesianChart.YAxes>   

        <chart:CandleSeries ItemsSource="{Binding StockData}"
                            XBindingPath="Year"
                            Open="Open"
                            High="High"
                            Low="Low"
                            Close="Close"
                            BullishBrush="Blue"
                            BearishBrush="Yellow"/>

    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

CandleSeries series = new CandleSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
    BullishBrush = Colors.Blue,
    BearishBrush = Colors.Yellow,
};

chart.Series.Add(series);
this.Content = chart;
{% endhighlight %}

{% endtabs %}

![Candle chart fill color in MAUI Chart](Chart-types_images/CandleFillColor.png)

## EnableSolidCandle

Use `EnableSolidCandle` to switch between filled and hollow candles. Default is `false`.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.XAxes>
            <chart:CategoryAxis/>
        </chart:SfCartesianChart.XAxes>

        <chart:SfCartesianChart.YAxes>
            <chart:NumericalAxis/>
        </chart:SfCartesianChart.YAxes>   

        <chart:CandleSeries ItemsSource="{Binding StockData}"
                            XBindingPath="Year"
                            Open="Open"
                            High="High"
                            Low="Low"
                            Close="Close"
                            EnableSolidCandle="True"/>

    </chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);

NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

CandleSeries series = new CandleSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
    EnableSolidCandle = true,
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Solid candle in WinUI Chart](Chart-types_images/SolidCandles.png)

## Segment Width

The `SegmentWidth` property gets or sets a value to change the width of the data points (candles) across the series. It accepts values between 0 and 1; the default value is 0.8. A value of 1.0 makes the candle occupy the full category width, while smaller values make the candle narrower.

{% tabs %}

{% highlight xaml %}

    <chart:SfCartesianChart>

        <chart:SfCartesianChart.XAxes>
            <chart:CategoryAxis/>
        </chart:SfCartesianChart.XAxes>

        <chart:SfCartesianChart.YAxes>
            <chart:NumericalAxis/>
        </chart:SfCartesianChart.YAxes>   

        <chart:CandleSeries ItemsSource="{Binding StockData}"
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

CandleSeries series = new CandleSeries()
{
    ItemsSource = new ViewModel().StockData,
    XBindingPath = "Year",
    Open = "Open",
    High = "High",
    Low = "Low",
    Close = "Close",
    SegmentWidth = 0.4,
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Candle chart segment width in WinUI Chart](Chart-types_images/CandleSegmentWidth.png)
