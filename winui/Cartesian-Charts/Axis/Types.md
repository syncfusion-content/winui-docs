---
layout: post
title: Axis types in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about axis types and its features in Syncfusion WinUI Cartesian Chart(SfCartesianChart) control and more.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Types of Axis in WinUI Cartesian Chart

[ChartAxis]() of Cartesian chart supports the following types.

* NumericalAxis
* CategoryAxis
* DateTimeAxis

Can choose any type of [ChartAxis](), like [DateTimeAxis](), [NumericalAxis](), [CategoryAxis]() depending on the value type. 

## NumericalAxis

[NumericalAxis]() is used to plot numerical values to the chart. [NumericalAxis]() can be defined for both [PrimaryAxis]() and [SecondaryAxis](). The following code snippet shows how to define the [NumericalAxis]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.PrimaryAxis>
<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis();

chart.SecondaryAxis = new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![NumericalAxis support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types.png)

**Customizing the NumericalAxis Range**

[Maximum]() property used for setting the maximum value for the axis range and [Minimum]() property is used for setting the minimum value for the axis range.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis Maximum="2750" Minimum="250" Interval="250"/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{
    Maximum = 2750,
    Minimum = 250,
    Interval = 250
};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_Numeric.png)

N> If  minimum or maximum value is set, the other value is calculated by default internally.

**StartRangeFromZero**

[NumericalAxis]() will calculate the range based on the data points binded to the axis. To start the range from zero have to define the [StartRangeFromZero]() property to True. The following code example demonstrates the NumericalAxis range starting from zero.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis StartRangeFromZero="True"/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{
   StartRangeFromZero = true
};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_startZero.png)

N> By default, Range is calculated between the minimum and maximum value of the data points.

## CategoryAxis

[CategoryAxis]() is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here. The following code example initializes the [CategoryAxis]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis();

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_category.png)

**LabelPlacement**

In [CategoryAxis](), labels is placed based on tick lines using [LabelPlacement]() property. By default the labels is placed `OnTicks`. The following code example demonstrates placing the label between ticks.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis LabelPlacement="BetweenTicks"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    LabelPlacement = LabelPlacement.BetweenTicks
};

{% endhighlight %}

{% endtabs %}

![Axis label placement support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_betweenTicks.png)


**IsIndexed**

By default, [CategoryAxis]() plots the values based on the index of the data points. However, the [CategoryAxis]() can be made to plot the data points based on its data, instead of index value by disabling the [IsIndexed]() property of `CategoryAxis`, and it is shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis IsIndexed="False"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    IsIndexed = false,
};

{% endhighlight %}

{% endtabs %}

### DateTimeAxis

[DateTimeAxis]() is used to plot DateTime values. The `DateTimeAxis` is widely used to make financial charts in places like the Stock Market, where index plotting is done every day.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis LabelFormat="MMM-yy"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
    LabelFormat = "MMM-yy"
};

{% endhighlight %}

{% endtabs %}

![DateTimeCategoryAxis support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_datetime.png)

**Customizing the Range**

[Minimum]() and [Maximum]() properties behavior is same as in NumericalAxis instead of setting numerical value, have to set date time values.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis Minimum="2021/05/1" Maximum="2021/11/01"  LabelFormat="MMM-yy"/>
</chart:SfCartesianChart.PrimaryAxis>


{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
    Minimum = new DateTime(2021,05,10),
    Maximum = new DateTime(2021,11,01),
    LabelFormat = "MMM-dd",
};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_range_datetime.png)


**Business Hours Range Calculation**

SfChart provides support to plot only the business hours in DateTimeAxis. This support is enabled by setting [EnableBusinessHours]() property to true.

The following properties are used for business hour range calculation,

* [OpenTime]()- Represents the open working time of a day.
* [CloseTime]()- Represents the close working time of a day.
* [WorkingDays]()- Represents the working [days]() of a week.

The following code snippet demonstrates the business hours support in DateTimeAxis.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:DateTimeAxis LabelFormat="dd-MMM" EnableBusinessHours="True" OpenTime="9" 
                        CloseTime="24" 
                        WorkingDays="Friday,Saturday,Sunday,Monday,Tuesday,Wednesday,Sunday"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
    EnableBusinessHours = true,
    OpenTime = 9,
    CloseTime = 24,
    WorkingDays = Day.Friday | Day.Saturday | Day.Sunday |
                Day.Monday | Day.Tuesday| Day.Wednesday| Day.Sunday
};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range customization support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_workdays.png)

## Inverting axis

Axis can be inverted using the [IsInversed]() property. The default value of this property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.SecondaryAxis>
    <chart:NumericalAxis IsInversed="True"/>
</chart:SfCartesianChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

this.Chart.SecondaryAxis.IsInversed = true;

{% endhighlight %}

{% endtabs %}

![Inversed axis support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_inverse.png)

## Multiple Axes

Cartesian charts provides a way to arrange multiple series inside the same chart area, giving the chart more space than x-axis and y-axis. These axes can be arranged in a stacking order or in a side by side pattern.

By default, all the series are plotted based on primary and secondary axis. Can add more axes by adding additional axis to the series. There are two properties [XAxis]() and [YAxis]() in all the Cartesian series type which is used to provide Multiple axes support.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Series>
    <chart:ColumnSeries ItemsSource="{Binding Data1}" 
                     XBindingPath="Date"
                     YBindingPath="Value">
        <chart:ColumnSeries.XAxis>
            <chart:DateTimeAxis LabelFormat="dd-MMM"/>
        </chart:ColumnSeries.XAxis>
        <chart:ColumnSeries.YAxis>
            <chart:NumericalAxis/>
        </chart:ColumnSeries.YAxis>
    </chart:ColumnSeries>
    <chart:SplineSeries ItemsSource="{Binding Data}" 
                     XBindingPath="Date"
                     YBindingPath="Value"/>
</chart:SfCartesianChart.Series>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{
    ItemsSource = new ViewModel().Demands,
    XBindingPath = "Demand",
    YBindingPath = "Year2011"
};

SplineSeries series2 = new SplineSeries()
{
    ItemsSource = new ViewModel().Demands,
    XBindingPath = "Date",
    YBindingPath = "Year2011",
};

series1.XAxis = new DateTimeAxis()
{
    LabelFormat = "dd-MMM"
};
series2.YAxis = new NumericalAxis();

chart.Series.Add(series1);
chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Multiple axes support in WinUI Chart](Axis_images/WinUI_Chart_Axis_types_multipleAxis.png)

In the above screenshot, the Column is plotted based on additional X & Y axes, and SplineSeries (or remaining series) is plotted based on the primary and secondary axes.