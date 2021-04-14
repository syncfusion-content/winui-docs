---
layout: post
title: Line and StepLine in WinUI Chart control | Syncfusion
description: Learn here all about Line and StepLine support in Syncfusion WinUI Chart control and more details.
platform: WinUI
control: SfChart
documentation: ug
---

# Line and StepLine in WinUI Chart

## Line

Line series join points on a plot by straight lines, showing data trends at equal intervals. The following code example explains how to create a simple [`LineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.LineSeries.html#) using given data.

{% tabs %}

{% highlight xaml %}

<chart:LineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value"/>

<chart:LineSeries XBindingPath="Year" ItemsSource="{Binding Data}" YBindingPath="Value1"/>

{% endhighlight %}

{% highlight c# %}

LineSeries series1 = new LineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value",

};

LineSeries series2 = new LineSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Year",

    YBindingPath = "Value1",

};

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Line chart type in WinUI](Series_images/line_chart.png)

## Step Line

[`StepLineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.StepLineSeries.html) plots horizontal and vertical lines to connect data points resulting in a step line progression. The following code illustrates how to initialize the [`StepLineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.StepLineSeries.html) in chart.

{% tabs %}

{% highlight xaml %}

<chart:StepLineSeries ItemsSource="{Binding Data}" XBindingPath="XValue" YBindingPath="YValue">       
</chart:StepLineSeries>

{% endhighlight %}

{% highlight c# %}

StepLineSeries stepLine = new StepLineSeries();

stepLine.ItemsSource = new ViewModel().Data;

stepLine.XBindingPath = "XValue";

stepLine.YBindingPath = "YValue";

SteplineChart.Series.Add(stepLine);

{% endhighlight %}

{% endtabs %}

![StepLine Chart type in WinUI](Series_images/stepline_chart.png)
