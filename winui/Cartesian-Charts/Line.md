---
layout: post
title: Line Chart in WinUI Chart control | Syncfusion
description: Learn here all about the line chart and its type in Syncfusion WinUI Chart (SfCartesianChart) control. 
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Line Chart in WinUI Chart (SfCartesianChart)

## Line Chart

Line chart is used to represent the data trends at equal intervals by connecting points on a plot with straight lines. To render a line chart, create an instance of [LineSeries](), and add it to the [Series]() collection property of [SfCartesianChart]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:LineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2010"/>
        <chart:LineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2011"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
LineSeries series1 = new LineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
};

LineSeries series2 = new LineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2011",

};

chart.Series.Add(series1);
chart.Series.Add(series2);

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Line Chart in WinUI](Chart-types_images/WinUI_line_chart.png)

### Dashed line

The [StrokeDashArray]() property of [LineSeries]() is used to render the line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:LineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2010" StrokeDashArray="5,2"/>
        <chart:LineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2011" StrokeDashArray="5,2"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
DoubleCollection doubleCollection = new DoubleCollection();
doubleCollection.Add(5);
doubleCollection.Add(2);
. . .
LineSeries series1 = new LineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    StrokeDashArray = doubleCollection

};

LineSeries series2 = new LineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2011",
    StrokeDashArray = doubleCollection
};

chart.Series.Add(series1);
chart.Series.Add(series2);

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Dashed line chart in WinUI](Chart-types_images/WinUI_dash_line_chart.png)

## Spline Chart 

The [SplineSeries]() resembles line series, but instead of connecting the data points with line segments, the data points are connected by smooth bezier curves.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:SplineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2010"/>
        <chart:SplineSeries XBindingPath="Demand" ItemsSource="{Binding Data}" YBindingPath="Year2011"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SplineSeries series1 = new SplineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
};

SplineSeries series2 = new SplineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2011",
};

chart.Series.Add(series1);
chart.Series.Add(series2);

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Spline chart type in WinUI Chart](Chart-types_images/WinUI_spline_chart.png)

## Step Line Chart 

The [StepLineSeries]() plots horizontal and vertical lines to connect the data points resulting in a step-like progression.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .            
    <chart:SfCartesianChart.Series>
        <chart:StepLineSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue"/>
        <chart:StepLineSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue1"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
StepLineSeries series1 = new StepLineSeries();
series1.ItemsSource = new ViewModel().Data;
series1.XBindingPath = "XValue";
series1.YBindingPath = "YValue";
chart.Series.Add(series);

StepLineSeries series2 = new StepLineSeries();
series2.ItemsSource = new ViewModel().Data;
series2.XBindingPath = "XValue";
series2.YBindingPath = "YValue1";
chart.Series.Add(series2);

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Step line Chart in WinUI](Chart-types_images/WinUI_step_line_chart.png)
