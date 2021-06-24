---
layout: post
title: Stacked series in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about stacked support in Syncfusion WinUI Chart(SfChart) control with stacked line, area, column chart types support and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Stacked in WinUI Cartesian Chart (SfCartesianChart)

## Stacked line

[`StackedLineSeries`]() resembles multiple types of series of the [`LineSeries`](). Each series is vertically stacked one above the other. When there is only one series, then it is [`LineSeries`](). 

The following code example illustrates how to use [`StackedLineSeries`]():

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
...
StackedLineSeries series1 = new StackedLineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath ="Father",
};

StackedLineSeries series2 = new StackedLineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "MonthlyExpenses",
    YBindingPath = "Mother",
};

StackedLineSeries series3 = new StackedLineSeries()
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

![StackedLine chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedline_chart.png)

## Stacked column

[`StackedColumnSeries`]() resembles multiple types of ColumnSeries. Each series is vertically stacked one above the other. When there is only one series, then it is ColumnSeries. 

The following code example illustrates how to use StackedColumnSeries:

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
...
StackedColumnSeries series1 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath ="GoldMedals",
};

StackedColumnSeries series2 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "SilverMedals",
};

StackedColumnSeries series3 = new StackedColumnSeries()
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

![StackedColumn chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedcolumn_chart.png)

## Stacked bar

[`StackedBarSeries`]() is a multiple series type of BarSeries. Each BarSeries is then stacked horizontally, side by side to each other. When there exists only one series, it resembles a simple BarSeries. 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedBarSeries XBindingPath="CountryName"        
            YBindingPath="GoldMedals" ItemsSource="{Binding MedalDetails}">
    </chart:StackedBarSeries>

    <chart:StackedBarSeries XBindingPath="CountryName" 
            YBindingPath="SilverMedals" ItemsSource="{Binding MedalDetails}">
    </chart:StackedBarSeries>

    <chart:StackedBarSeries XBindingPath="CountryName" 
            YBindingPath="BronzeMedals" ItemsSource="{Binding MedalDetails}">
    </chart:StackedBarSeries>
</chart:SfCartesianChart>
{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedBarSeries series1 = new StackedBarSeries()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "GoldMedals",
};

StackedBarSeries series2 = new StackedBarSeries()
{
    ItemsSource = new ViewModel().MedalDetails,
    XBindingPath = "CountryName",
    YBindingPath = "SilverMedals",
};

StackedBarSeries series3 = new StackedBarSeries()
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

![StackedBar chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedbar_chart.png)

## Stacked area

[`StackedAreaSeries`]() is representing areas stacked vertically one above the other. 

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
...
StackedAreaSeries series1 = new StackedAreaSeries()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Bus",
};

StackedAreaSeries series2 = new StackedAreaSeries()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Car",
};

StackedAreaSeries series3 = new StackedAreaSeries()
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

![StackedArea chart type in WinUI Cartesian Chart](Stacking_Series_Images/stackedarea_chart.png)

You can draw open curve like Area using this [`IsClosed`]() property.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    ...
    <chart:StackedAreaSeries Stroke="Black" StrokeThickness="3"
            IsClosed="False" XBindingPath="Month" 
            YBindingPath="Bus" ItemsSource="{Binding Accidents}"/>

    <chart:StackedAreaSeries Stroke="White" StrokeThickness="3"
            IsClosed="False" XBindingPath="Month"             
            YBindingPath="Car" ItemsSource="{Binding Accidents}"/>

    <chart:StackedAreaSeries Stroke="Black" StrokeThickness="3"  
            IsClosed="False" XBindingPath="Month" 
            YBindingPath="Truck" ItemsSource="{Binding Accidents}"/>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
StackedAreaSeries series1 = new StackedAreaSeries()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Bus",
    Stroke = new SolidColorBrush(Colors.Black),
    StrokeThickness = 3,
    IsClosed = false,
};

StackedAreaSeries series2 = new StackedAreaSeries()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Car",
    Stroke = new SolidColorBrush(Colors.White),
    StrokeThickness = 3,
    IsClosed = false,
};

StackedAreaSeries series3 = new StackedAreaSeries()
{
    ItemsSource = new ViewModel().Accidents,
    XBindingPath = "Month",
    YBindingPath = "Truck",
    Stroke = new SolidColorBrush(Colors.Black),
    StrokeThickness = 3,
    IsClosed = false,
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
...

{% endhighlight %}

{% endtabs %}

![IsClosed support for Stacked area series in WinUI Chart](Stacking_Series_Images/stackedarea_isclosed_false.png)
