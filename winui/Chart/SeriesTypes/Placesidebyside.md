---
layout: post
title:  Side By Side Placement | SfChart | WinUI | Syncfusion
description: This section explains about placement pattern of bar type series like Column, Bar and RangeColumn in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Side By Side Placement in WinUI Chart (SfChart) 

It defines the placement pattern of bar type series like Column, Bar, StackedColumn, etc. 

It is a Boolean property and its default value is true, so the segment will be placed adjacent to each other (Clustered).

![Column chart type placed side by side](Series_images/sidebyside1.jpeg)


The following code example and image illustrates the placement of series while setting [`SideBySideSeriesPlacement`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartBase.html#Syncfusion_UI_Xaml_Charts_ChartBase_SideBySideSeriesPlacement) as false.

{% tabs %}

{% highlight xaml %}

<chart:SfChart x:Name="columnChart" AreaBorderBrush="DarkGray" 

Header="Usage of Metals"  

SideBySideSeriesPlacement="False"

AreaBorderThickness="1,1,1,1">

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis Header="Metals"/>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis Header="Usage" />                            

</chart:SfChart.SecondaryAxis>

<chart:SfChart.Legend>

<chart:ChartLegend Visibility="Visible" />

</chart:SfChart.Legend>

<chart:ColumnSeries ItemsSource="{Binding Data}"

 Label="2015"  

XBindingPath="Metals" 

YBindingPath="Count1" />

<chart:ColumnSeries ItemsSource="{Binding Data}"  

SegmentSpacing="0.5"

XBindingPath="Metals" 

Label="2014" YBindingPath="Count2"/>            

</chart:SfChart>

{% endhighlight %}

{% highlight C# %}

SfChart chart = new SfChart();

chart.Header = "Usage of Metals";

chart.AreaBorderBrush = new SolidColorBrush(Colors.DarkGray);

chart.SideBySideSeriesPlacement = false;

chart.AreaBorderThickness = new Thickness(1);

chart.PrimaryAxis = new CategoryAxis()
{

    Header = "Metals"

};

chart.SecondaryAxis = new NumericalAxis()
{

    Header = "Usage"

};

chart.Legend = new ChartLegend()
{

    Visibility = Visibility.Visible

};

ColumnSeries columnSeries1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Metals",

    YBindingPath = "Count1",

    Label = "2015",

};

ColumnSeries columnSeries2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Data,

    XBindingPath = "Metals",

    YBindingPath = "Count2",

    Label = "2014",

    SegmentSpacing = 0.5,

};

chart.Series.Add(columnSeries1);

chart.Series.Add(columnSeries2);

{% endhighlight %}

{% endtabs %}

![Column chart type place one over another.](Series_images/sidebyside2.jpeg)


N> As the series will be placed one over the other(overlapped), to differentiate between the series the `SegmentSpacing` is used.