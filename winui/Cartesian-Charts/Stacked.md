---
layout: post
title: Stacked charts in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about stacked chart types column, line, and area in Syncfusion WinUI Chart(SfChart) control.
platform: WinUI
control: SfChart
documentation: ug
---

# Stacked Charts in WinUI Cartesian Chart (SfCartesianChart)

## Stacked Column Chart

The [`StackedColumnSeries`]() resembles multiple of column series and each series is vertically stacked one above the other. When there is only one series, then it is `ColumnSeries`. 

The following code example demonstrates how to define the `StackedColumnSeries`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedColumnSeries XBindingPath="CountryName"    
            YBindingPath="GoldMedals" ItemsSource="{Binding MedalDetails}"/>

    <chart:StackedColumnSeries XBindingPath="CountryName" 
            YBindingPath="SilverMedals" ItemsSource="{Binding MedalDetails}"/> 

    <chart:StackedColumnSeries XBindingPath="CountryName" 
            YBindingPath="BronzeMedals" ItemsSource="{Binding MedalDetails}"/>
    ...
</chart:SfCartesianChart>
{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ViewModel viewModel = new ViewModel();

...

StackedColumnSeries series1 = new StackedColumnSeries()
{
    ItemsSource = viewModel.MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath ="GoldMedals",
};

StackedColumnSeries series2 = new StackedColumnSeries()
{
    ItemsSource = viewModel.MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "SilverMedals",
};

StackedColumnSeries series3 = new StackedColumnSeries()
{
    ItemsSource = viewModel.MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "BronzeMedals",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedColumn chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedcolumn_chart.png)

## Stacked Line Chart

The [`StackedLineSeries`]() resembles multiple of line series and each series is vertically stacked one above the other. When there is only one series, then it is [`LineSeries`](). 

The following code example demonstrates how to define the `StackedLineSeries`.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...

    <chart:StackedLineSeries  
            XBindingPath="MonthlyExpenses"    
            YBindingPath="Father" 
            ItemsSource="{Binding Data}"/>

    <chart:StackedLineSeries
            XBindingPath="MonthlyExpenses" 
            YBindingPath="Mother"
            ItemsSource="{Binding Data}"/> 

    <chart:StackedLineSeries 
            XBindingPath="MonthlyExpenses" 
            YBindingPath="Son"
            ItemsSource="{Binding Data}" />
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ViewModel viewModel = new ViewModel();

...

StackedLineSeries series1 = new StackedLineSeries()
{
    ItemsSource = viewModel.Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath ="Father",
};

StackedLineSeries series2 = new StackedLineSeries()
{
    ItemsSource = viewModel.Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Mother",
};

StackedLineSeries series3 = new StackedLineSeries()
{
    ItemsSource = viewModel.Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Son",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedLine chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedline_chart.png)

## Stacked Area Chart

The [`StackedAreaSeries`]() is representing the multiple of area series are stacked vertically one above the other. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedAreaSeries XBindingPath="Month" 
        YBindingPath="Bus" ItemsSource="{Binding Accidents}" />

    <chart:StackedAreaSeries XBindingPath="Month"         
        YBindingPath="Car" ItemsSource="{Binding Accidents}" />

    <chart:StackedAreaSeries XBindingPath="Month"                 
        YBindingPath="Truck" ItemsSource="{Binding Accidents}" />
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ViewModel viewModel = new ViewModel();

...

StackedAreaSeries series1 = new StackedAreaSeries()
{
    ItemsSource = viewModel.Accidents,
    XBindingPath = "Month",
    YBindingPath = "Bus",
};

StackedAreaSeries series2 = new StackedAreaSeries()
{
    ItemsSource = viewModel.Accidents,
    XBindingPath = "Month",
    YBindingPath = "Car",
};

StackedAreaSeries series3 = new StackedAreaSeries()
{
    ItemsSource = viewModel.Accidents,
    XBindingPath = "Month",
    YBindingPath = "Truck",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![StackedArea chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedarea_chart.png)

