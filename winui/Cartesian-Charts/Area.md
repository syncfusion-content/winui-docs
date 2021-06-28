---
layout: post
title: Area Chart in WinUI Chart control | Syncfusion
description: Learn here all about the area chart types and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Area Chart in WinUI Charts (SfCartesianChart)

## Area Chart

The area chart is rendered by using a collection of line segments connected to form a closed loop area, filled with the specified color. To render a area chart, create an instance of [AreaSeries]() and add it to the [Series]() collection property of the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:AreaSeries ItemsSource="{Binding Data}" XBindingPath="Demand" YBindingPath="Year2010"/>  
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
AreaSeries series = new AreaSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Area chart type in WinUI Chart](Chart-types_images/WinUI_area_chart.png)

## Spline Area Chart

The [SplineAreaSeries]() connects a series of data points using smooth bezier line curves, with the underlying areas filled.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:SplineAreaSeries ItemsSource="{Binding Data}" XBindingPath="Demand" YBindingPath="Year2010"/>  
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SplineAreaSeries series = new SplineAreaSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Spline area chart type in WinUI Chart](Chart-types_images/WinUI_spline_area_chart.png)

## Step Area Chart

The [StepAreaSeries]() is similar to [AreaSeries](), but it does not use the shortest distance to connect the two data points using bezier curves. Instead, this series uses vertical and horizontal lines to connect the data points in a series forming a step-like progression.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:StepAreaSeries XBindingPath="XValue" YBindingPath="YValue" ItemsSource="{Binding Data}"/> 
    </chart:SfCartesianChart.Series>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
StepAreaSeries series = new StepAreaSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Step area chart type in WinUI](Chart-types_images/WinUI_step_area_chart.png)

