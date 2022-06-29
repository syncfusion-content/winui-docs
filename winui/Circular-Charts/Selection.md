---
layout: post
title: Selection in WinUI Chart control | Syncfusion
description: This section explains about how to configure the selection support and its features applying in WinUI Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Selection in WinUI Chart (SfCircularChart)

The circular chart supports selection that allows the selection of a segment in a series by using the [DataPointSelectionBehavior](). 

## Enable Selection

To enable the selection in chart, create an instance of the [DataPointSelectionBehavior]() and set it to the `SelectionBehavior` property of the cirucular series. Also set the [SelectionBrush]() property to highlight the segment in the series.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet"/>
            </chart:PieSeries.SelectionBehavior>
        </chart:PieSeries>
    </chart:SfCircularChart.Series>
    
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.BlueViolet),
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Segment selection support in WinUI Pie Chart](Selection_Images/WinUI_pie_chart_selection.png)

## Multi-selection

The circular chart allows to select single or multiple segments using the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property. By default the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) value is [Single]().

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet" Type="Multiple" />
            </chart:PieSeries.SelectionBehavior>
        </chart:PieSeries>
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.BlueViolet),
    Type = SelectionType.Multiple
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Multi-selection support in WinUI Pie Chart](Selection_Images/WinUI_pie_chart_multiple_selection.png)

## Selection on initial rendering

### SelectedIndex

The circular chart provides support to select a point programmatically on a chart using the [SelectedIndex]() property of `DataPointSelectionBehavior`.

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet" 
                SelectedIndex="2"/>
            </chart:PieSeries.SelectionBehavior>
        </chart:PieSeries>
    </chart:SfCircularChart.Series>
    
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.BlueViolet),
    SelectedIndex = 2
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![SelectedIndex in WinUI Chart](Selection_images/WinUI_chart_selected_index.png)

### SelectedIndexes

The circular chart provides support to select multiple points programmatically on a chart using the [SelectedIndexes]() property of the `DataPointSelectionBehavior`.

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet" Type="Multiple" 
                SelectedIndexes="{Binding SelectedIndexes}" />
            </chart:PieSeries.SelectionBehavior>
        </chart:PieSeries>
    </chart:SfCircularChart.Series>

</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
PieSeries series = new PieSeries();
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.BlueViolet),
    Type = SelectionType.Multiple,
    SelectedIndexes = new List<int>() { 2, 3, 4 }
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![SelectedIndexes in WinUI Chart](Selection_images/WinUI_chart_selected_indexes.png)

## Events

The following events are available in the [ChartSelectionBehavior]().

### SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_SelectionChanging) event occurs before the data point is being selected. This is a cancelable event. This argument contains the following information.

* [CurrentIndex]() - Gets the selected data point index.
* [PreviousIndex]() - Gets the previous selected data point index.

* [Cancel]() - Gets or sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_SelectionChanged) event occurs after a data point has been selected. This argument contains the following information.

* [CurrentIndex]() - Gets the selected data point index.
* [PreviousIndex]() - Gets the previous selected data point index.
