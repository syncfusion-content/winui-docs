---
layout: post
title: Area Chart in WinUI Chart Control | Syncfusion
description: Learn about the area chart types and their features in the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: WinUI area chart, WinUI SfCartesianChart area chart, WinUI area chart customization, Syncfusion WinUI area chart, WinUI SfCartesianChart area chart settings.
---

# Area Chart in WinUI Charts (SfCartesianChart)

## Area Chart

The [WinUI Area Chart](https://www.syncfusion.com/winui-controls/charts/winui-area-chart) renders a collection of line segments connected to form a closed loop area, filled with the specified color. To create an area chart, instantiate an [AreaSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AreaSeries.html) and add it to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>   

    <chart:SfCartesianChart.Series>
        <chart:AreaSeries ItemsSource="{Binding Data}" 
                          XBindingPath="Demand" 
                          YBindingPath="Year2010"/>  
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

The [SplineAreaSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SplineAreaSeries.html) connects a series of data points using smooth bezier line curves, with the underlying areas filled.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>
            
    <chart:SfCartesianChart.Series>
        <chart:SplineAreaSeries ItemsSource="{Binding Data}" 
                                XBindingPath="Demand" 
                                YBindingPath="Year2010"/>  
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);
NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

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

N> You can refer to our [WinUI Spline Area Chart](https://www.syncfusion.com/winui-controls/charts/winui-spline-area-chart) feature tour page for its groundbreaking feature representations. You can also explore our [WinUI Spline Area Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/SplineArea) that demonstrates how to easily configure with built-in support for creating stunning visual effects.

## Step Area Chart

The [StepAreaSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StepAreaSeries.html) is similar to [AreaSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.AreaSeries.html), but it uses vertical and horizontal lines to connect data points, forming a step-like progression instead of employing bezier curves.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>

    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis />
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes> 

    <chart:SfCartesianChart.Series>
        <chart:StepAreaSeries XBindingPath="XValue" 
                              YBindingPath="YValue" 
                              ItemsSource="{Binding Data}"/> 
    </chart:SfCartesianChart.Series>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

N> You can refer to our [WinUI Step Area Chart](https://www.syncfusion.com/winui-controls/charts/winui-step-area-chart) feature tour page for its groundbreaking feature representations. You can also explore our [WinUI Step Area Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/StepArea) that demonstrates how to easily configure with built-in support for creating stunning visual effects.
