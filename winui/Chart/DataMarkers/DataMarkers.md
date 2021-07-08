---
layout: post
title: Data Markers in WinUI Chart control | Syncfusion
description: Learn hera all about Data Markers feature of Syncfusion WinUI Chart control with chart segment element and more.
platform: WinUI
control: Chart
documentation: ug
---

# Data Markers in WinUI Chart

Data markers are used to display values related to a chart segment element. Values from data point(x, y) or other custom properties from a data source can be displayed. 

Each data marker can be represented by the following:

* Label - Displays the segment label content at the (X, Y) point.
* Connector Line - Used to connect the (X, Y) point and the label element.

The following code example illustrates how to initialize the data marker.

{% tabs %}

{% highlight xaml %}

<chart:SfChart>
. . .
<chart:ColumnSeries ShowDataLabels="True">
    <chart:ColumnSeries.DataLabelSettings>
        <chart:CartesianDataLabelSettings />
    </chart:ColumnSeries.DataLabelSettings>
</chart:ColumnSeries>
</chart:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();
ColumnSeries series = new ColumnSeries();
. . .
series.DataLabelSettings = new CartesianDataLabelSettings();

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Data Markers in WinUI Chart](DataMarkers_images/datamarker_label_overview.png) 
