---
layout: post
title: Line and Step Line Charts| SfChart | WinUI | Syncfusion
description: This section explains Line and Area Charts and its properties for customization in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Line and Step Line Charts in WinUI Chart (SfChart)

## Line

Line series join points on a plot by straight lines, showing data trends at equal intervals. The following code example explains how to create a simple [`LineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.LineSeries.html#) using given data.

{% tabs %}

{% highlight xaml %}

<chart:LineSeries  XBindingPath="Year

ItemsSource="{Binding List}" YBindingPath="India"/>

<chart:LineSeries  XBindingPath="Year"     

ItemsSource="{Binding List}" YBindingPath="America"/>

{% endhighlight %}

{% highlight c# %}

LineSeries series1 = new LineSeries()
{

    ItemsSource = new ViewModel().List,

    XBindingPath = "Year",

    YBindingPath = "India",

};

LineSeries series2 = new LineSeries()
{

    ItemsSource = new ViewModel().List,

    XBindingPath = "Year",

    YBindingPath = "America",

};

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Line chart type in WinUI](Series_images/line.png)

## Step Line

[`StepLineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.StepLineSeries.html) plots horizontal and vertical lines to connect data points resulting in a step line progression. The following code illustrates how to initialize the [`StepLineSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.StepLineSeries.html) in chart.

{% tabs %}

{% highlight xaml %}

<chart:StepLineSeries ItemsSource="{Binding Data}"  
                      
                      XBindingPath="XValue" 
                      
                      YBindingPath="YValue">
            
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

![StepLine Chart type in WinUI](Series_images/stepLine.png)