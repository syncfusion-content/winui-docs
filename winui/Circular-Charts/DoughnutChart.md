---
layout: post
title: Doughnut chart in WinUI Circular Chart control | Syncfusion
description: Learn here all about doughnut chart and its features in Syncfusion WinUI Circular Chart(SfCircularChart) control.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Doughnut chart in WinUI Circular Chart

[DoughnutSeries]() is similar to [PieSeries](). It is used to show the relationship between parts of data and whole data. To render a [DoughnutSeries]() in circular chart, create an instance of the [DoughnutSeries]() and add it to the [Series]() collection property of [SfCircularChart]().

The following code example demonstrates how to define [DoughnutSeries]().

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:DoughnutSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

</syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Category",
    YBindingPath = "Value"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Doughnut series type in WinUI Circular chart](Series_images/doughnut_chart.png)

### Doughnut coefficient

The [DoughnutCoefficient]() proeprty of doughnut series is used to define the inner circle. It also has [DoughnutSize]() property, which is used to define the size for this series, similar to [CircularCoefficient]() in `PieSeries`.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:DoughnutSeries DoughnutCoefficient="0.7" XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

</syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Category",
    YBindingPath = "Value",
    DoughnutCoefficient = 0.7
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Doughnut coefficient support in WinUI Circular Chart](Series_images/doughnut_coefficient.png)

### Doughnut size

The size of doughnut series can be customized by using the [DoughnutSize]() property. The following code illustrates how to use this property in series.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart>

    <syncfusion:DoughnutSeries DoughnutSize="0.8"/>
       
    <syncfusion:DoughnutSeries DoughnutSize="0.8"/>

</syncfusion:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries doughnut = new DoughnutSeries();

doughnut.DoughnutSize = 0.8;

chart.Series.Add(doughnut);

DoughnutSeries doughnut1 = new DoughnutSeries();

doughnut1.DoughnutSize = 0.8;

chart.Series.Add(doughnut1);

{% endhighlight %}

{% endtabs %}

![Doughnut size support in WinUI Circular Chart](Series_images/doughnut_size.png)

## Semi doughnut

By using the [StartAngle]() and [EndAngle]() properties, you can draw doughnut series in different shapes such as semi-doughnut or quarter doughnut series.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:DoughnutSeries StartAngle="180" EndAngle="360" XBindingPath="Utilization" YBindingPath="ResponseTime" ItemsSource="{Binding Data}"/>

</syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries series = new DoughnutSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Utilization",
    YBindingPath = "ResponseTime",
    StartAngle = 180,
    EndAngle = 360
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Semi doughnut support in WinUI Circular Chart](Series_images/semi_doughnut_chart.png)

## Stacked doughnut

Doughnut segments can be separated as individual circles using the [IsStackedDoughnut]() property. The following properties are used to customize the stacked doughnut chart:

* [CapStyle]() - Specifies the shapes of the start and end points of a circular segment. The supported values are [BothFlat](), [BothCurve](), [StartCurve](), and [EndCurve](). The default value of this property is BothFlat.
* [SegmentSpacing]() - Changes the spacing between two individual segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 represents 100%, and 0 represents 0% of the available space.
* [MaximumValue]() - Represents the entire span of an individual circle. The default value of this property is double.NaN.
* [TrackColor]() - Changes the color of the track area.
* [TrackBorderColor]() - Changes the color of the track border.
* [TrackBorderWidth]() - Changes the width of the track border.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:DoughnutSeries IsStackedDoughnut="True" CapStyle="BothCurve" SegmentSpacing="0.2" MaximumValue="100"
    XBindingPath="Category" YBindingPath="Expenditure" ItemsSource="{Binding ExpenditureData}">
    </syncfusion:DoughnutSeries>
    
<syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

DoughnutSeries doughnutSeries = new DoughnutSeries()
{
    IsStackedDoughnut = true,
    CapStyle = DoughnutCapStyle.BothCurve,
    SegmentSpacing = 0.2,
    MaximumValue = 100,
    XBindingPath = "Category",
    YBindingPath = "Expenditure",
    ItemsSource = new ViewModel().ExpenditureData
};

chart.Series.Add(doughnutSeries);

{% endhighlight %}

{% endtabs %}

![Stacked doughnut chart in WinUI](Series_images/stackeddoughnut_chart.png)
