---
layout: post
title: Selection in WinUI Circular Chart control | Syncfusion
description: This section explains about how to configure the selection support and its features applying in WinUI Circular Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Selection in WinUI Circular Chart

SfChart supports selection that allows you to select a segment in a series or series itself by using [ChartSelectionBehavior](). 

### Adding Selection Behavior to SfChart

You can create an instance [ChartSelectionBehavior]() and add it to the Behaviors collection of Circular Chart.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart >
    <chart:SfCircularChart.Behaviors>
        <chart:ChartSelectionBehavior/>
    </chart:SfCircularChart.Behaviors>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
ChartSelectionBehavior selection = new ChartSelectionBehavior();
chart.Behaviors.Add(selection);

{% endhighlight %}

{% endtabs %}

## SegmentSelection

Segment Selection allows to highlight a segment in a series. By default behavior enables the segment selection it will changed using selection [Type](). For highlighting a segment the brush color can be set using [SelectionBrush]() property of series.

**Segment Selection in ColumnSeries**

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
    <chart:SfCircularChart.Behaviors>
        <chart:ChartSelectionBehavior Type="Point"/>
    </chart:SfCircularChart.Behaviors>
<chart:SfCircularChart.Series>
    <chart:PieSeries SelectionBrush="BlueViolet"/>
</chart:SfCircularChart.Series>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();

ChartSelectionBehavior selection = new ChartSelectionBehavior();
selection.Type = SelectionType.Point;
chart.Behaviors.Add(selection);

PieSeries series = new PieSeries();
series.SelectionBrush = new SolidColorBrush(Colors.BlueViolet);
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Segment selection support in WinUI Circular Chart](Selection_Images/WinUI_Circular_chart_Segment_selection.png)

## Series Selection

Series selection is used in case of multiple series when you want to highlight a particular series. Series selection can be enabled by setting selection type as [Series](). The [SeriesSelectionBrush]() property is used to set the brush color to highlight the series.

The following code example demonstrates highlighting a series.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
    <chart:SfCircularChart.Behaviors>
        <chart:ChartSelectionBehavior SeriesSelectionBrush="BlueViolet" Type="Series"/>
    </chart:SfCircularChart.Behaviors>
<chart:SfCircularChart.Series>
    <chart:PieSeries Label="Continents" />
    <chart:PieSeries Label="Countries" />
</chart:SfCircularChart.Series>

</chart:SfCircularChart.Series>
{% endhighlight %}

{% highlight c# %}

ChartSelectionBehavior selection = new ChartSelectionBehavior();
selection.Type = SelectionType.Series;
selection.SeriesSelectionBrush = new SolidColorBrush(Colors.BlueViolet);
chart.Behaviors.Add(selection);

PieSeries series = new PieSeries() { Label = "Continents" };
PieSeries series1 = new PieSeries() { Label = "Countries" };
. . .
chart.Series.Add(series);
chart.Series.Add(series1);

{% endhighlight %}

{% endtabs %}

![Series selection support in WinUI Circular Chart](Selection_Images/WinUI_Circular_chart_Series_selection.png)

## Customizing the Selection

Circcular charts allows to select single or multiple segment\series using [Type]() property. By default the SelectionType is [Point]().

The following code snippet demonstrates multiple segment selection.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart.Behaviors>
    <chart:ChartSelectionBehavior Type="MultiPoint"/>
</chart:SfCircularChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartSelectionBehavior selection = new ChartSelectionBehavior();
selection.Type = SelectionType.MultiPoint;
chart.Behaviors.Add(selection);

{% endhighlight %}

{% endtabs %}

![Multiple Selection type support in WinUI Circular Chart](Selection_Images/WinUI_Circular_chart_Multiple_segment_selection.png)

## Events

The following events are available in SfChart for ChartSelectionBehavior.

### SelectionChanging

The [SelectionChanging]() event occurs before the data point is being selected. This is a cancelable event. This argument contains the following information.

* [SelectedSeries]() - Gets the series of the selected data point.
* [SelectedSegments]() - Gets or sets the segments collection of the selected series.
* [SelectedSegment]() - Gets the segment of the selected data point.
* [SelectedIndex]() - Gets the selected data point index.
* [PreviousSelectedIndex]() - Gets the previous selected data point index.
* [IsSelected]() - Gets a value that indicates whether the segment or series is selected.
* [IsDataPointSelection]() - Gets a value that indicates whether the selection is segment selection or series selection.
* [Cancel]() - Gets or Sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged]() event occurs after a data point has been selected. This argument contains the following information.

* [SelectedSeries]() - Gets the series of the selected data point.
* [SelectedSegments]() - Gets the segments collection of the selected series.
* [SelectedSegment]() - Gets the segment of the selected data point.
* [SelectedIndex]() - Gets the selected data point index.
* [PreviousSelectedSeries]() - Gets the previous selected series.
* [PreviousSelectedSegments]() - Gets the segments collection of previous selected series.
* [PreviousSelectedSegment]() - Gets the segment of previous selected data point.
* [PreviousSelectedIndex]() - Gets the previous selected data point index.
* [OldPointInfo]() - Gets the previous selected segment item value.
* [NewPointInfo]() - Gets the selected segment item value.
* [IsSelected]() - Gets a value that indicates whether the segment or series is being selected.
* [IsDataPointSelection]() - Gets a value that indicates whether the selection is segment selection or series selection.
* [SelectedSeriesCollection]() - Gets the series collection that has been selected through rectangle selection or mouse interaction.
