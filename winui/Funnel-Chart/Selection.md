---
layout: post
title: Selection in WinUI Chart control | Syncfusion®
description: Learn here all about selection and multi-selection support in Syncfusion® WinUI Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Selection in WinUI Chart (SfFunnelChart)

The funnel chart supports selection that allows the selection of a segment in the chart by using the [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_SelectionBehavior). 

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

To enable the selection in the chart, create an instance of the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html) and set it to the [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_SelectionBehavior) of funnel the chart. Also, set the [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) property to highlight the segment in the funnel chart.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                     Height="388"
                     Width="500"
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value">

    <chart:SfFunnelChart.SelectionBehavior>
        <chart:DataPointSelectionBehavior SelectionBrush="Red"/>
    </chart:SfFunnelChart.SelectionBehavior>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.Red),
};
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Selection support in WinUI Chart](Selection_images/winui-chart_segment_selection.png)

## Multi-selection

The funnel chart provides support to select multiple segments by using the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property as [Multiple](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionType.html#Syncfusion_UI_Xaml_Charts_ChartSelectionType_Multiple). By default, the value of the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) is [Single](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionType.html#Syncfusion_UI_Xaml_Charts_ChartSelectionType_Single) and it is used for a single selection.

N> The `Series` and `MultiSeries` selection types are not supported for the funnel chart

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart"  
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value">

    <chart:SfFunnelChart.SelectionBehavior>
        <chart:DataPointSelectionBehavior SelectionBrush="Red"
										  Type="Multiple"/>
    </chart:SfFunnelChart.SelectionBehavior>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.Red),
    Type = ChartSelectionType.Multiple,
};
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Multi selection support in WinUI Chart](Selection_images/winui-chart_multi_selection.png)

## Selection on initial rendering

### SelectedIndex

The funnel chart provides support to select a point programmatically on a chart using the the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndex) property of the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                     Height="388" Width="500"
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value">

    <chart:SfFunnelChart.SelectionBehavior>
        <chart:DataPointSelectionBehavior SelectionBrush="Red"
										  SelectedIndex="2"/>
    </chart:SfFunnelChart.SelectionBehavior>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.Red),
    SelectedIndex= 2
};
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![SelectedIndex in WinUI Chart](Selection_images/WinUI_chart_selected_index.png)

### SelectedIndexes

Funnel chart provides support to select multiple points programmatically on a chart using the [SelectedIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndexes) property of [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart"  
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value">

    <chart:SfFunnelChart.SelectionBehavior>
        <chart:DataPointSelectionBehavior SelectionBrush="Red" 
										  Type="Multiple"
        SelectedIndexes="{Binding SelectedIndexes}"/>
    </chart:SfFunnelChart.SelectionBehavior>
. . .
</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.SetBinding(SfFunnelChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
    SelectionBrush = new SolidColorBrush(Colors.Red),
    Type = ChartSelectionType.Multiple,
    SelectedIndexes = new List<int>() { 2, 3, 4 }
};
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![SelectedIndexes in WinUI Chart](Selection_images/WinUI_chart_selected_indexes.png)

## Events

The following selection events are available in the [ChartSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html).

### SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanging) event occurs before the data point is being selected. This is a cancelable event. The [ChartSelectionChangingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html) contains the following information.

* [NewIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangingEventArgs_NewIndexes) - Gets the collection of selected data point index. Here, NewIndexes[0] is the current selected index.
* [OldIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangingEventArgs_OldIndexes) - Gets the collection of previous selected data point index. Here, OldIndexes[0] is the current unselected index.
* [Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel?view=net-6.0) - Gets or sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanged) event occurs after a data point has been selected. The [ChartSelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html) contains the following information.

* [NewIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangedEventArgs_NewIndexes) - Gets the collection of selected data point index. Here, NewIndexes[0] is the current selected index.
* [OldIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartSelectionChangedEventArgs_OldIndexes) - Gets the collection of previous selected data point index. Here, OldIndexes[0] is the current unselected index.
