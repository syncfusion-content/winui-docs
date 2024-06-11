---
layout: post
title: Bubble Chart in WinUI Chart control | Syncfusion
description: Learn here all about the bubble series and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfChart
documentation: ug
keywords: bubble chart in winui chart, winui sfcartesianchart bubble chart, winui bubble chart customization, syncfusion winui bubble chart, winui sfcartesianchart bubble chart settings.
---

# Bubble Chart in WinUI Chart (SfCartesianChart)

## Bubble Chart

The [BubbleSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BubbleSeries.html) is represented by closely packed circles, whose areas are proportional to the quantities. The size of the bubble series is relative proportional to the value bind with the series using the [Size](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_Size)  property. You can set the constraints on this size using the [MinimumRadius](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_MinimumRadius) and [MaximumRadius](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BubbleSeries.html#Syncfusion_UI_Xaml_Charts_BubbleSeries_MaximumRadius) properties.

To render a bubble series, create an instance of [BubbleSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.BubbleSeries.html) and add to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) as shown in the following code.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes> 

    <chart:BubbleSeries ItemsSource="{Binding Data}" 
                        XBindingPath="XValue" 
                        YBindingPath="YValue" 
                        Size="Size" 
                        MinimumRadius="5" 
                        MaximumRadius="10"/>
    ...
<chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);
. . .
BubbleSeries series = new BubbleSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "XValue",
    YBindingPath = "YValue",
    Size = "Size",
    MinimumRadius = 5,
    MaximumRadius = 10
};

chart.Series.Add(series);
...

{% endhighlight %}

{% endtabs %}

![Bubble chart type in WinUI Chart](Bubble_Images/WinUI_bubble_chart.png)

N> Refer to our [WinUI Bubble Chart](https://www.syncfusion.com/winui-controls/charts/winui-bubble-chart) feature tour page for its groundbreaking feature representations. You can also explore our [WinUI Bubble Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/Bubble) that shows how to easily configure with built-in support for creating stunning visual effects.