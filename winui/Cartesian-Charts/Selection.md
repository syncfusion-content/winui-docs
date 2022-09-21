---
layout: post
title: Selection in WinUI Chart control | Syncfusion
description: Learn here all about selection and multi-selection support in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Selection in WinUI Chart (SfCartesianChart)

Cartesian chart supports selection that allows to select a segment or series in the chart by using [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_SelectionBehavior) property. 

## Enable DataPoint Selection

To enable the datapoint selection in chart, create an instance of [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html) and set it to the `SelectionBehavior` property of chart series. And also need to set the [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) property to highlight the segment in the chart.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    
    <chart:ColumnSeries ItemsSource="{Binding Data}" 
                        XBindingPath="Demand"
                        YBindingPath="Year2010">
		<chart:ColumnSeries.SelectionBehavior>
		    <chart:DataPointSelectionBehavior SelectionBrush="Red"/>
		</chart:ColumnSeries.SelectionBehavior>
	</chart:ColumnSeries>				
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010"
};

DataPointSelectionBehavior selection = new DataPointSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
series.SelectionBehavior = selection;

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Segment selection support in WinUI Chart](Selection_images/WinUI_chart_segment_selection.png)

## Segment Selection in Linear Series

In linear type series the segment selection can be viewed by changing the data label interior.

The following code example demonstrates the spline series segment selection by changing the data label interior.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    
    <chart:SplineSeries ItemsSource="{Binding Data}" 
                        XBindingPath="Demand"
                        YBindingPath="Year2010"
                        ShowDataLabels="True">
		<chart:SplineSeries.SelectionBehavior>
		    <chart:DataPointSelectionBehavior SelectionBrush="Red"/>
		</chart:SplineSeries.SelectionBehavior>
	</chart:SplineSeries>				
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .

SplineSeries series = new SplineSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010"
    ShowDataLabels="True" 
};

DataPointSelectionBehavior selection = new DataPointSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
series.SelectionBehavior = selection;

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Segment selection support in WinUI Chart SplineSeries](Selection_images/WinUI_chart_spline_series_segment_selection.png)

## Enable Series Selection

Series selection is used to highlight a particular series when using multiple series. Series selection is enabled by create an instance of [SeriesSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SeriesSelectionBehavior.html) and set it to the [SelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_SelectionBehavior) property of [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html). The [SelectionBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionBrush) property is used to set the brush color to highlight the series.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.SelectionBehavior>
	    <chart:SeriesSelectionBehavior SelectionBrush="Red"/>
	</chart:SfCartesianChart.SelectionBehavior>	
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SeriesSelectionBehavior selection = new SeriesSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Series selection support in WinUI Chart](Selection_images/WinUI_chart_series_selection.png)

## Multi-selection

Cartesian chart provides support to select single or multiple segments/series by using the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property. [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) property with [Multiple]() value is used to select multiple segments/series. By default, the [Type](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_Type) value is [Single]().

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    
    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}"  
                            XBindingPath="Demand"
                            YBindingPath="Year2010">
            <chart:ColumnSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="Red" 
                                                  Type="Multiple"/>
            </chart:ColumnSeries.SelectionBehavior>
        </chart:ColumnSeries>				
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010"
};

DataPointSelectionBehavior selection = new DataPointSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
selection.Type = ChartSelectionType.Multiple;
series.SelectionBehavior = selection;

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Multi Segment selection support in WinUI Chart](Selection_images/WinUI_chart_multi_segment_selection.png)

The following code snippet demonstrates multiple series selection.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.SelectionBehavior>
        <chart:SeriesSelectionBehavior SelectionBrush="Red"
                                       Type="Multiple"/>
    </chart:SfCartesianChart.SelectionBehavior>	
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SeriesSelectionBehavior selection = new SeriesSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
selection.Type = ChartSelectionType.Multiple;
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Multi Series selection support in WinUI Chart](Selection_images/WinUI_chart_multi_series_selection.png)

## Selection on initial rendering

### SelectedIndex

Cartesian chart provides support to select a point programmatically on a chart using the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndex) property of [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .   
    <chart:SfCartesianChart.Series>
        <chart:ColumnSeries ItemsSource="{Binding Data}" 
                            XBindingPath="Demand"
                            YBindingPath="Year2010">
            <chart:ColumnSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectedIndex="3" 
                                                  SelectionBrush="Red"/>
            </chart:ColumnSeries.SelectionBehavior>
        </chart:ColumnSeries>	
    </chart:SfCartesianChart.Series>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .

ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010"
};

DataPointSelectionBehavior selection = new DataPointSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
selection.SelectedIndex = 3;
series.SelectionBehavior = selection;

chart.Series.Add(series);
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Initial selection rendering support in WinUI Chart](Selection_images/WinUI_chart_selected_index.png)

Select a series programmatically on a chart using the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndex) property of the [SeriesSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SeriesSelectionBehavior.html).

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
. . .
    <chart:SfCartesianChart.SelectionBehavior>
        <chart:SeriesSelectionBehavior SelectionBrush="Red" 
                                       SelectedIndex="1"/>
    </chart:SfCartesianChart.SelectionBehavior>	
. . .
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
SeriesSelectionBehavior selection = new SeriesSelectionBehavior();
selection.SelectionBrush = new SolidColorBrush(Colors.Red);
selection.SelectedIndex = 1;
chart.SelectionBehavior = selection;
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Initial series selection rendering support in WinUI Chart](Selection_images/WinUI_charts_selected_serie_index.png)

### SelectedIndexes

Cartesian chart provides support to select multiple points programmatically on a chart using the [SelectedIndexes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectedIndexes) property of [DataPointSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.DataPointSelectionBehavior.html).

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
. . .
    <chart:ColumnSeries ItemsSource="{Binding Data}" 
                        XBindingPath="Demand"
                        YBindingPath="Year2010">
            <chart:ColumnSeries.SelectionBehavior>
                <chart:DataPointSelectionBehavior SelectionBrush="BlueViolet" 
                                                  Type="Multiple" 
                                                  SelectedIndexes="{Binding SelectedIndexes}" />
            </chart:ColumnSeries.SelectionBehavior>
    </chart:ColumnSeries>
</chart:SfCircularChart>

{% endhighlight %}

{% highlight c# %}

SfCircularChart chart = new SfCircularChart();
. . .
ColumnSeries series = new ColumnSeries()
{
    ItemsSource = new ViewModel().Data,
    XBindingPath = "Demand",
    YBindingPath = "Year2010"
};

DataPointSelectionBehavior selection = new DataPointSelectionBehavior()
{
	SelectionBrush = new SolidColorBrush(Colors.BlueViolet),
    Type = ChartSelectionType.Multiple,
    SelectedIndexes = new List<int>() { 1, 3 }
};

series.SelectionBehavior = selection;
chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Initial series selection rendering support in WinUI Chart](Selection_images/WinUI_chart_selected_Datapoint_indexes.png)

## Events

The following selection events are available in the [ChartSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html).

### SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanging) event occurs before the data point or series is being selected. This is a cancelable event. The `ChartSelectionChangingEventArgs` contains the following information.

* [NewIndexes[0]](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangingEventArgs_CurrentIndex) - Gets the selected data point or series index.
* [OldIndexes[0]](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangingEventArgs_PreviousIndex) - Gets the previous selected data point or series index.
* [Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel?view=net-6.0) - Gets or sets a value that indicates whether the selection should be canceled.

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartSelectionBehavior.html#Syncfusion_UI_Xaml_Charts_ChartSelectionBehavior_SelectionChanged) event occurs after a data point or series has been selected. The `ChartSelectionChangedEventArgs` contains the following information.

* [NewIndexes[0]](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangedEventArgs_CurrentIndex) - Gets the selected data point or series index.
* [OldIndexes[0]](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionChangedEventArgs_PreviousIndex) - Gets the previous selected data point or series index.
