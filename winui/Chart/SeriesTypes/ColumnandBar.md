---
layout: post
title: Column and Bar in WinUI Chart control | Syncfusion
description: Learn here all about Column and Bar support in Syncfusion WinUI Chart control with segment spacing and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Column and Bar in WinUI Chart

## Column

Column charts plot discrete rectangles for the given values. The following code example demonstrates the usage of [`ColumnSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ColumnSeries.html#).

{% tabs %}

{% highlight xaml %}

<chart:ColumnSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Column chart type in WinUI](Series_images/column_chart.png)

## Bar

Bar series is similar to column series, except the orientation. The following code example shows how to use [`BarSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BarSeries.html#).

{% tabs %}

{% highlight xaml %}

<chart:BarSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>

{% endhighlight %}

{% highlight c# %}

BarSeries series = new BarSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "XValue",

    YBindingPath = "YValue",

};

{% endhighlight %}

{% endtabs %}

![Bar chart type in WinUI](Series_images/bar_chart.png)

### Spacing

[`Spacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_SpacingProperty) property of series is used to decide the width of a segment. [`Spacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_SpacingProperty) value ranges from 0 to 1. The following code illustrates how to set [`Spacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_SpacingProperty) property of the series.

{% tabs %}

{% highlight xaml %}

<Chart:ColumnSeries Chart:ChartSeriesBase.Spacing="0.8"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()

ChartSeriesBase.SetSpacing(series, 0.8);

{% endhighlight %}

{% endtabs %}

![Column Spacing support in WinUI](Series_images/column_spacing.png)

**Segment Spacing**

The [`SegmentSpacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ColumnSeries.html#Syncfusion_UI_Xaml_Charts_ColumnSeries_SegmentSpacing) property is used to set the spacing between the segments when multiple series are added in chart. Its value ranges from 0 to 1. The following code illustrates how to use the [`SegmentSpacing`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ColumnSeries.html#Syncfusion_UI_Xaml_Charts_ColumnSeries_SegmentSpacing) property in series.

{% tabs %}

{% highlight xaml %}

<Chart:SfChart >

<Chart:ColumnSeries SegmentSpacing="0.6"/>

<Chart:ColumnSeries SegmentSpacing="0.6"/>

</Chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

ColumnSeries series1 = new ColumnSeries()
{

    SegmentSpacing = 0.6,

};

chart.Series.Add(series1);

ColumnSeries series2 = new ColumnSeries()
{

    SegmentSpacing = 0.6

};

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Column SegmentSpacing support in WinUI](Series_images/column_segmentspacing.png)
