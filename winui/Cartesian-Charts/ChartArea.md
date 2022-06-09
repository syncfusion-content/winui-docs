---
layout: post
title: Chart area in WinUI Chart control | Syncfusion
description: Learn here all about chart area and its customization in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Chart Area in WinUI Chart (SfCartesianChart)

Chart area represents the entire chart and all its elements. It’s a virtual rectangular area that includes all the chart elements like title, axis, legends, series, etc.

## Customization

Chart provides the properties like [PlotAreaBorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_PlotAreaBorderBrush), [PlotAreaBorderThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_PlotAreaBorderThickness) and [PlotAreaBackground](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_PlotAreaBackground) for customizing the plot area.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart Header="Chart Area Header" PlotAreaBackground="LightCyan" Background="LightBlue"
                        PlotAreaBorderBrush="Blue" PlotAreaBorderThickness="3">
. . .
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis/>
    </chart:SfCartesianChart.YAxes>

    <chart:SfCartesianChart.Legend>
        <chart:ChartLegend/>
    </chart:SfCartesianChart.Legend>

    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand" 
                            YBindingPath="Year2010" 
                            Label="Year 2010">
        </chart:ColumnSeries>
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
chart.Header = "Chart Area Header";
chart.PlotAreaBackground = new SolidColorBrush(Colors.LightCyan);
chart.PlotAreaBorderBrush = new SolidColorBrush(Colors.Blue);
chart.Background = new SolidColorBrush(Colors.LightBlue);
chart.PlotAreaBorderThickness = new Thickness(3);

CategoryAxis primaryAxis = new CategoryAxis();
chart.XAxes.Add(primaryAxis);
NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

ChartLegend legend = new ChartLegend();
chart.Legend = legend;

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    Label = "Year 2010"
};

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Chart area customization in WinUI chart](Chart-Area_images/WinUI_chart_area.png)
