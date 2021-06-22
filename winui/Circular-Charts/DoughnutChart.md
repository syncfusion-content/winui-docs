---
layout: post
title: Doughnut Series in WinUI Circular Chart control | Syncfusion
description: Learn here all about doughnut Series support in Syncfusion WinUI Circular Chart(SfCircularChart) control with custom support and more.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Doughnut Series in WinUI Circular Chart

[DoughnutSeries]() is similar to PieSeries. It is used to show the relationship between parts of data and whole data. 

The DoughnutSeries can be added to chart as in below code example:

{% tabs %}

{% highlight xaml %}

<chart:DoughnutSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

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

The Doughnut also having coefficient property, [DoughnutCoefficient]() which defines the inner circle. Also it has [DoughnutSize](), used to define the size for this series like [CircularCoefficient]() in PieSeries.

{% tabs %}

{% highlight xaml %}

<chart:DoughnutSeries DoughnutCoefficient="0.7" XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

{% endhighlight %}

{% highlight c# %}

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

![DoughnutCoefficient support in WinUI Circular Chart](Series_images/doughnut_coefficient.png)

**Size**

The size of doughnut series can be customized by using its [DoughnutSize]() property. The following code illustrates how to use the property in series.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart>

<syncfusion:DoughnutSeries DoughnutSize="0.8"/>
       
<syncfusion:DoughnutSeries DoughnutSize="0.8"/>

</syncfusion:SfChart>


{% endhighlight %}

{% highlight c# %}

DoughnutSeries doughnut = new DoughnutSeries();

doughnut.DoughnutSize = 0.8;

chart.Series.Add(doughnut);

DoughnutSeries doughnut1 = new DoughnutSeries();

doughnut1.DoughnutSize = 0.8;

chart.Series.Add(doughnut1);

{% endhighlight %}

{% endtabs %}

![DoughnutSize support in WinUI Circular Chart](Series_images/doughnut_size.png)

**Hole Size**

[DoughnutHoleSize]() is an attachable property. It gets or sets the double value, which is used to customize the doughnut hole size. Its value ranges from 0 to 1, and it can be set as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Chart:SfChart Chart:DoughnutSeries.DoughnutHoleSize="0.2">
    
</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

DoughnutSeries.SetDoughnutHoleSize(chart, 0.2);

{% endhighlight %}

{% endtabs %}

![DoughnutHoleSize support in WinUI Circular Chart](Series_images/doughnut_holesize.png)


## Semi Doughnut

By using custom [StartAngle]() and [EndAngle]() properties,  can draw doughnut series in different shapes such as semicircular or quarter circular series.

{% tabs %}

{% highlight xaml %}

<chart:DoughnutSeries StartAngle="180" EndAngle="360" XBindingPath="Utilization" YBindingPath="ResponseTime" ItemsSource="{Binding Data}"/>

{% endhighlight %}

{% highlight c# %}

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

* [CapStyle]() - Specifies the shapes of the start and end points of a circular segment. The supported values are [BothFlat](), [BothCurve](), [StartCurve](), and [EndCurve](). The default value of the this property is BothFlat.

* [SegmentSpacing]() - Changes the spacing between two individual segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 represents 100%, and 0 represents 0% of the available space.

* [MaximumValue]() - Represents the entire span of an individual circle. The default value of the this property is double.NaN.

* [TrackColor]() - Changes the color of the track area.

* [TrackBorderColor]() - Changes the color of the track border.

* [TrackBorderWidth]() - Changes the width of the track border.

{% tabs %}

{% highlight xaml %}

<chart:SfChart>
    …
    <chart:DoughnutSeries IsStackedDoughnut="True" CapStyle="BothCurve" SegmentSpacing="0.2" MaximumValue="100" XBindingPath="Category" YBindingPath="Expenditure" ItemsSource="{Binding ExpenditureData}">
    </chart:DoughnutSeries>

</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

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

![Stacked doughnut Circular chart in WinUI](Series_images/stackeddoughnut_chart.png)