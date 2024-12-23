---
layout: post
title: Selection in WinUI Chart control | Syncfusion®
description: This section explains about how to configure the selection support and its features applying in WinUI Chart (SfCircularChart).
platform: WinUI
control: SfCircularChart
documentation: ug
---

# Selection in WinUI Chart (SfCircularChart)

The circular chart supports selection that allows the selection of a segment in a series by using the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html). 

## Properties

The Selection feature can be configured using the following properties:

* [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) - Gets or Sets the [ChartSelectionType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionType.html) Enum value for the Selection Behavior.     
The following [ChartSelectionType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionType.html) can be achieved during Selection:
    * Single - Allows to select a single segment.
    * SingleDeselect -  Allows to select and deselect a single segment.
    * Multiple - Allows to select multiple segments.
    * None - Restricts the segment selection.
* [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) - Gets or Sets  the SelectionBrush color value for Selection Behavior.
* [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndex) - Gets or Sets  the index value of the segment that should be selected during the Selection.
* [SelectedIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndexes) - Gets or Sets  the list of indexes of the segments that should be selected during the Selection.

## Enable Selection

To enable the selection in chart, create an instance of the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html) and set it to the [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSeries.html?tabs=tabid-24%2Ctabid-22%2Ctabid-4%2Ctabid-11%2Ctabid-6%2Ctabid-18%2Ctabid-8%2Ctabid-13%2Ctabid-15%2Ctabid-17%2Ctabid-1%2Ctabid-3%2Ctabid-10%2Ctabid-20#Syncfusion_UI_Xaml_Charts_ChartSeries_SelectionBehavior) property of the circular series. Also set the [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) property to highlight the segment in the series.

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

The circular chart allows to select single or multiple segments using the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property. By default the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) value is [Single](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionType.html#Syncfusion_UI_Xaml_Charts_ChartSelectionType_Single).

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet"
												  Type="Multiple" />
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
    Type = ChartSelectionType.Multiple
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Multi-selection support in WinUI Pie Chart](Selection_Images/WinUI_pie_chart_multiple_selection.png)

## Selection on initial rendering

### SelectedIndex

The circular chart provides support to select a point programmatically on a chart using the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndex) property of [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xaml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior
							SelectionBrush="BlueViolet" 
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

The circular chart provides support to select multiple points programmatically on a chart using the [SelectedIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndexes) property of the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xml %}

<chart:SfCircularChart>
. . .
    <chart:SfCircularChart.Series>
        <chart:PieSeries>
            <chart:PieSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior
							SelectionBrush="BlueViolet"
							Type="Multiple" 
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
    Type = ChartSelectionType.Multiple,
    SelectedIndexes = new List<int>() { 2, 3, 4 }
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![SelectedIndexes in WinUI Chart](Selection_images/WinUI_chart_selected_indexes.png)

## Events

The following events are available in the [ChartSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html).

### SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanging) event occurs before the data point is being selected. This is a cancelable event. The [ChartSelectionChangingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html) contains the following information.

* [NewIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangingEventArgs_NewIndexes) - Gets the collection of selected data point index. Here, NewIndexes[0] is the current selected index.
* [OldIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangingEventArgs_OldIndexes) - Gets the collection of previous selected data point index. Here, OldIndexes[0] is the current unselected index.

* [Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel?view=net-6.0) - Gets or sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanged) event occurs after a data point has been selected. The [ChartSelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html) argument contains the following information.

* [NewIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangedEventArgs_NewIndexes) - Gets the collection of selected data point index. Here, NewIndexes[0] is the current selected index.
* [OldIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangedEventArgs_OldIndexes) - Gets the collection of previous selected data point index. Here, OldIndexes[0] is the current unselected index.
