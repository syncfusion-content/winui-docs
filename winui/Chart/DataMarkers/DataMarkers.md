---
layout: post
title: Data Markers in WinUI Chart control | Syncfusion
description: Learn hera all about Data Markers feature of Syncfusion WinUI Chart control and more. It is used to display values related to a chart segment element.
platform: WinUI
control: Chart
documentation: ug
---

# Data Markers in WinUI Chart

Chart Data Markers are used to display values related to a chart segment element. Values from data point(x, y) or other custom properties from a data source can be displayed. 

Each data marker can be represented by the following:

* Label - Displays the segment label content at the (X, Y) point.
* Marker - Displays the desired marker at the (X, Y) point.
* ConnectorLine - Line used to connect the (X, Y) point and the label element.

The following code example illustrates how to initialize the data marker.

{% tabs %}

{% highlight xaml %}

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}" XBindingPath="Category" YBindingPath="Value">
        <syncfusion:ColumnSeries.DataMarker>
            <syncfusion:ChartDataMarker ShowLabel="True">
            </syncfusion:ChartDataMarker>
        </syncfusion:ColumnSeries.DataMarker>
</syncfusion:ColumnSeries> 

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = ViewModel().Demands,
    XBindingPath = "Category",
    YBindingPath = "Value",
};
ChartDataMarker datamarker = new ChartDataMarker();
datamarker.ShowLabel = true;
series.DataMarker = datamarker;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data Markers in WinUI](DataMarkers_images/datamarker_label_overview.png) 
