---
layout: post
title: Pie chart in WinUI Circular Chart control | Syncfusion
description: Learn here all about pie chart and its features in Syncfusion WinUI Circular Chart(SfCircularChart) control.
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Pie chart in WinUI Circular Chart

To render a [PieSeries]() in circular chart, create an instance of the [PieSeries]() and add it to the [Series]() collection property of [SfCircularChart]().

The following code example demonstrates how to define [PieSeries]().

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:PieSeries XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

</syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

PieSeries series = new PieSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Category",
    YBindingPath = "Value"
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Pie chart type in WinUI](Series_images/pie_chart.png)

### Circular coefficient

The rendering size of the [PieSeries]() can be controlled using the [CircularCoefficient]() property as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:PieSeries CircularCoefficient="0.9" XBindingPath="Category" ItemsSource="{Binding Data}" YBindingPath="Value"/>

</syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

PieSeries series = new PieSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Category",
    YBindingPath = "Value",
    CircularCoefficient = 0.9
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Circular coefficient support in WinUI Circular Chart](Series_images/pie_circularcoefficient.png)

### Group small data points into “others”

The small segments in the pie chart can be grouped into the “others” category using the [GroupTo]() and [GroupMode]() properties of [PieSeries]().

* [GroupMode]() - used to specify the grouping type based on slice [Angle](), actual data point [Value](), or [Percentage](). 
* [GroupTo]() - used to set the limit to group data points into a single slice. The grouped segment is labeled as “Others” in legend and toggled as other segment. 

The default value of the [GroupTo]() property is `double.NAN`, and the default value of the [GroupMode]() property is Value.

**Pie series without grouping**

![Pie series without grouping feature](Series_images/nongrouping_pie.png)

**Pie series with grouping (Mode - Value)**

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Value" GroupTo="1000">
    <syncfusion:PieSeries.DataMarker>
        <syncfusion:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </syncfusion:ChartDataMarker>
    </syncfusion:PieSeries.DataMarker>
</syncfusion:PieSeries>

{% endhighlight %}

{% highlight c# %}

PieSeries pieSeries = new PieSeries();
pieSeries.GroupMode = PieGroupMode.Value;
pieSeries.GroupTo = 1000;
ChartDataMarker datamarker = new ChartDataMarker()
{
    ShowConnectorLine = true,
    ShowLabel = true,
    ConnectorHeight = 80,
    LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
    SegmentLabelContent = LabelContent.LabelContentPath,

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in value mode](Series_images/pie_groupmode_value.png)

**Pie series with grouping (Mode - Angle)**

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Angle" GroupTo="30">
    <syncfusion:PieSeries.DataMarker>
        <syncfusion:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </syncfusion:ChartDataMarker>
    </syncfusion:PieSeries.DataMarker>
</syncfusion:PieSeries>

{% endhighlight %}

{% highlight c# %}

PieSeries pieSeries = new PieSeries();
pieSeries.GroupMode = PieGroupMode.Angle;
pieSeries.GroupTo = 30;

ChartDataMarker datamarker = new ChartDataMarker()
{
        ShowConnectorLine = true,
        ShowLabel = true,
        ConnectorHeight = 80,
        LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
        SegmentLabelContent = LabelContent.LabelContentPath,
};

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in angle mode](Series_images/pie_groupmode_angle.png)

**Pie series with grouping (Mode - Percentage)**

{% tabs %}

{% highlight xaml %}

<syncfusion:PieSeries ItemsSource="{Binding Data}" XBindingPath="Country" YBindingPath="Count" GroupMode="Percentage" GroupTo="10">
    <syncfusion:PieSeries.DataMarker>
        <syncfusion:ChartDataMarker ShowConnectorLine="True" 
                                  ConnectorHeight="80" 
                                  ShowLabel="True" 
                                  LabelTemplate="{StaticResource DataLabelTemplate}"  
                                  SegmentLabelContent="LabelContentPath">
        </syncfusion:ChartDataMarker>
    </syncfusion:PieSeries.DataMarker>
</syncfusion:PieSeries>

{% endhighlight %}

{% highlight c# %}

PieSeries pieSeries = new PieSeries();
pieSeries.GroupMode = PieGroupMode.Percentage;
pieSeries.GroupTo = 10;

ChartDataMarker datamarker = new ChartDataMarker()
{
        ShowConnectorLine = true,
        ShowLabel = true,
        ConnectorHeight = 80,
        LabelTemplate = this.RootGrid.Resources["DataLabelTemplate"] as DataTemplate,
        SegmentLabelContent = LabelContent.LabelContentPath,
};

pieSeries.DataMarker = datamarker;

{% endhighlight %}

{% endtabs %}

![Pie series with grouping feature in percentage mode](Series_images/pie_groupmode_value.png)

## Semi pie

By using the [StartAngle]() and [EndAngle]() properties, you can draw pie series in different shapes such as semi-pie or quarter pie series.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfCircularChart.Series>

    <syncfusion:PieSeries StartAngle="180" EndAngle="360" XBindingPath="Utilization" YBindingPath="ResponseTime" ItemsSource="{Binding Data}"/>

<syncfusion:SfCircularChart.Series>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

PieSeries series = new PieSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Utilization",
    YBindingPath = "ResponseTime",
    StartAngle = 180,
    EndAngle = 360
};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Semi pie support in WinUI Chart](Series_images/semi_pie_chart.png)
