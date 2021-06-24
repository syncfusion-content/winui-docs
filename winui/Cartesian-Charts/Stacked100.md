---
layout: post
title: Stacked 100% series in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about stacked 100% support in Syncfusion WinUI Chart(SfChart) control with stacked 100% line, area, column chart types support and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Stacked100 in WinUI Cartesian Chart (SfCartesianChart)

## 100% stacked line

[`StackedLine100Series`]() resembles [`StackedLineSeries`]() but the cumulative portion of each stacked element always comes to a total of 100%. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...

    <chart:StackedLine100Series ItemsSource="{Binding Data}" 
            XBindingPath="MonthlyExpenses" 
            YBindingPath="Father" />

    <chart:StackedLine100Series ItemsSource="{Binding Data}"
            XBindingPath="MonthlyExpenses"  
            YBindingPath="Mother" />

    <chart:StackedLine100Series ItemsSource="{Binding Data}"
            XBindingPath="MonthlyExpenses" 
            YBindingPath="Son"/>
    ...
<chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedLine100Series series1 = new StackedLine100Series()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Father",
};

StackedLine100Series series2 = new StackedLine100Series()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Mother",
};

StackedLine100Series series3 = new StackedLine100Series()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Son",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedLine100 chart type in WinUI Cartesian Chart](Stacking100_Series_Images/stackedline100_chart.png)

## 100% stacked column

[`StackedColumn100Series`]() resembles StackedColumnSeries but the cumulative portion of each stacked element always comes to a total of 100%. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedColumn100Series XBindingPath="CountryName" 
            YBindingPath="GoldMedals" ItemsSource="{Binding MedalDetails}"/>

    <chart:StackedColumn100Series XBindingPath="CountryName"
            YBindingPath="SilverMedals" ItemsSource="{Binding MedalDetails}"/>

    <chart:StackedColumn100Series XBindingPath="CountryName" 
            YBindingPath="BronzeMedals" ItemsSource="{Binding MedalDetails}"/>
    ...
</chart:SfCartesianChart>
{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedColumn100Series series1 = new StackedColumn100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "GoldMedals",
};

StackedColumn100Series series2 = new StackedColumn100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "SilverMedals",
};

StackedColumn100Series series3 = new StackedColumn100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "BronzeMedals",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedColumn100 chart type in WinUI Cartesian Chart](Stacking100_Series_Images/stackedcolumn100_chart.png)

## 100% stacked bar

[`StackedBar100Series`]() resembles a StackedBarSeries. StackedBar100Series displays multiple series as stacked bars and the cumulative portion of each stacked element is always 100%. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedBar100Series XBindingPath="CountryName" 
        YBindingPath="GoldMedals" ItemsSource="{Binding MedalDetails}" />

    <chart:StackedBar100Series XBindingPath="CountryName"                          
        YBindingPath="SilverMedals" ItemsSource="{Binding MedalDetails}" />

    <chart:StackedBar100Series XBindingPath="CountryName" 
        YBindingPath="BronzeMedals" ItemsSource="{Binding MedalDetails}" />

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedBar100Series series1 = new StackedBar100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "GoldMedals",
};

StackedBar100Series series2 = new StackedBar100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "SilverMedals",
};

StackedBar100Series series3 = new StackedBar100Series()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "BronzeMedals",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedBar100 chart type in WinUI Cartesian Chart](Stacking100_Series_Images/stackedbar100_chart.png)

## 100% stacked area

StackedArea100Series is similar to StackedAreaSeries, but the cumulative portion of each stacked element always totals 100%. 

The following code example shows the way to add Stacked area 100 series:

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedArea100Series XBindingPath="Month"         
        YBindingPath="Bus" ItemsSource="{Binding Accidents}" />

    <chart:StackedArea100Series XBindingPath="Month" 
        YBindingPath="Car" ItemsSource="{Binding Accidents}" />

    <chart:StackedArea100Series XBindingPath="Month" 
        YBindingPath="Truck" ItemsSource="{Binding Accidents}" />
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedArea100Series series1 = new StackedArea100Series()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Bus",
};

StackedArea100Series series2 = new StackedArea100Series()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Car",
};

StackedArea100Series series3 = new StackedArea100Series()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Truck",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedArea100 chart type in WinUI Cartesian Chart](Stacking100_Series_Images/stackedarea100_chart.png)
