---
layout: post
title: Selection in WinUI Chart control | Syncfusion
description: Learn here all about selection and multi-selection support in Syncfusion WinUI Chart (SfFunnelChart) control.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Selection in WinUI Chart (SfFunnelChart)

The funnel chart supports selection that allows the selection of a segment in the chart by using the [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfFunnelChart.html#Syncfusion_UI_Xaml_Charts_SfFunnelChart_SelectionBehavior). 

## Enable Selection

To enable the selection in the chart, create an instance of the [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html) and set it to the `SelectionBehavior` of funnel the chart. Also, set the [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) property to highlight the segment in the funnel chart.

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

The funnel chart provides support to select multiple segments by using the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property as [Multiple](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionType.html#Syncfusion_UI_Xaml_Charts_SelectionType_Multiple). By default, the value of the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) is [Single](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionType.html#Syncfusion_UI_Xaml_Charts_SelectionType_Single) and it is used for a single selection.

N> The `Series` and `MultiSeries` selection types are not supported for the funnel chart

{% tabs %}

{% highlight xml %}

<chart:SfFunnelChart x:Name="chart"  
                     ItemsSource="{Binding Data}" 
                     XBindingPath="Category"
                     YBindingPath="Value">

    <chart:SfFunnelChart.SelectionBehavior>
        <chart:DataPointSelectionBehavior SelectionBrush="Red" Type="Multiple"/>
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
    Type = SelectionType.Multiple,
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
        <chart:DataPointSelectionBehavior SelectionBrush="Red" SelectedIndex="2"/>
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
        <chart:DataPointSelectionBehavior SelectionBrush="Red" Type="Multiple"
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
    Type = SelectionType.Multiple,
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

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_SelectionChanging) event occurs before the data point is being selected. This is a cancelable event. This argument contains the following information.

* [CurrentIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangingEventArgs_CurrentIndex) - Gets the selected data point index.
* [PreviousIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangingEventArgs_PreviousIndex) - Gets the previous selected data point index.
* [Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel?view=net-6.0) - Gets or sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_SelectionChanged) event occurs after a data point has been selected. This argument contains the following information.

* [CurrentIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangedEventArgs_CurrentIndex) - Gets the selected data point index.
* [PreviousIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangedEventArgs_PreviousIndex) - Gets the previous selected data point index.
