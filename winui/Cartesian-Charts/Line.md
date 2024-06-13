---
layout: post
title: Line Chart in WinUI Chart control | Syncfusion
description: Learn here all about the line chart and its type in Syncfusion WinUI Chart (SfCartesianChart) control. 
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: line chart in winui chart, winui sfcartesianchart line chart, winui line chart customization, syncfusion winui line chart,  winui sfcartesianchart line chart configuration.
---

# Line Chart in WinUI Chart (SfCartesianChart)

## Line Chart

[WinUI Line Chart](https://www.syncfusion.com/winui-controls/charts/winui-line-chart) is used to represent the data trends at equal intervals by connecting points on a plot with straight lines. To render a line chart, create an instance of [LineSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LineSeries.html), and add it to the [Series](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_Series) collection property of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html).

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
        <chart:LineSeries XBindingPath="Demand" 
	                      ItemsSource="{Binding Data}" 
                          YBindingPath="Year2010"/>
        <chart:LineSeries XBindingPath="Demand" 
                          ItemsSource="{Binding Data}" 
                          YBindingPath="Year2011"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

The [StrokeDashArray](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LineSeries.html#Syncfusion_UI_Xaml_Charts_LineSeries_StrokeDashArray) property of [LineSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.LineSeries.html) is used to render the line series with dashes. Odd value is considered as rendering size and even value is considered as gap.

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
        <chart:LineSeries XBindingPath="Demand" 
                          ItemsSource="{Binding Data}" 
                          YBindingPath="Year2010" 
                          StrokeDashArray="5,2"/>
        <chart:LineSeries XBindingPath="Demand" 
                          ItemsSource="{Binding Data}" 
                          YBindingPath="Year2011" 
                          StrokeDashArray="5,2"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

## Step Line Chart 

The [StepLineSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StepLineSeries.html) plots horizontal and vertical lines to connect the data points resulting in a step-like progression.

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
        <chart:StepLineSeries ItemsSource="{Binding Data}" 
                              XBindingPath="XValue" 
                              YBindingPath="YValue"/>
        <chart:StepLineSeries ItemsSource="{Binding Data}" 
                              XBindingPath="XValue" 
                              YBindingPath="YValue1"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

N> You can refer to our [WinUI Step Line Chart](https://www.syncfusion.com/winui-controls/charts/winui-step-line-chart) feature tour page for its groundbreaking feature representations. You can also explore our [WinUI Step Line Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/StepLine) that shows how to easily configure with built-in support for creating stunning visual effects.

## Spline Chart 

The [SplineSeries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SplineSeries.html) resembles line series, but instead of connecting the data points with line segments, the data points are connected by smooth bezier curves.

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
        <chart:SplineSeries XBindingPath="Demand" 
                            ItemsSource="{Binding Data}" 
                            YBindingPath="Year2010"/>
        <chart:SplineSeries XBindingPath="Demand" 
                            ItemsSource="{Binding Data}" 
                            YBindingPath="Year2011"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

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

### Spline rendering types

The [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_Type) property allows you to change the spline curve in series. By default, the value of the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SplineSeries.html#Syncfusion_UI_Xaml_Charts_SplineSeries_Type) is [Natural](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SplineType.html#Syncfusion_UI_Xaml_Charts_SplineType_Natural).

The following types are used in SplineSeries:

* `Natural`
* `Monotonic`
* `Cardinal`
* `Clamped`

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
        <chart:SplineSeries XBindingPath="Demand" 
                            ItemsSource="{Binding Data}" 
                            YBindingPath="Year2010" 
                            Type="Cardinal"/>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis xAxis = new CategoryAxis();
chart.XAxes.Add(xAxis);
NumericalAxis yAxis = new NumericalAxis();
chart.YAxes.Add(yAxis);

SplineSeries series = new SplineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    Type = SplineType.Cardinal
};

chart.Series.Add(series);

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Spline types chart in WinUI Chart](Chart-types_images/WinUI_spline_types_chart.png)

N> You can refer to our [WinUI Spline Chart](https://www.syncfusion.com/winui-controls/charts/winui-spline-chart) feature tour page for its groundbreaking feature representations. You can also explore our [WinUI Spline Chart example](https://github.com/syncfusion/winui-demos/tree/master/chart/Views/Cartesian%20Charts/Spline) that shows how to easily configure with built-in support for creating stunning visual effects.