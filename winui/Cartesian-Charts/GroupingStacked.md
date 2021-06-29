---
layout: post
title: Stacked group chart in WinUI Chart control | Syncfusion
description: Learn here all about the stacked group chart and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfChart
documentation: ug
---

# Stacked Group Chart in WinUI Chart (SfCartesianChart)

Chart provides support to group the stacked similar series by using the [`GroupName`]() property of stacked series. The stacked series which contains the same [`GroupName`]() will be stacked in a single group.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <chart:SfCartesianChart.PrimaryAxis>
        <chart:CategoryAxis LabelPlacement="BetweenTicks"/>
    </chart:SfCartesianChart.PrimaryAxis>

    <chart:SfCartesianChart.SecondaryAxis>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.SecondaryAxis>  
    
    <chart:StackedColumnSeries GroupName="Group1" XBindingPath="Year" 
            YBindingPath="Quarter1" ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group1" XBindingPath="Year" 
            YBindingPath="Quarter2" ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group2" XBindingPath="Year"
            YBindingPath="Quarter3" ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group2" XBindingPath="Year"
            YBindingPath="Quarter4" ItemsSource="{Binding AnnualDetails}"/>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ViewModel viewModel = new ViewModel();
CategoryAxis primaryAxis = new CategoryAxis();
primaryAxis.LabelPlacement = LabelPlacement.BetweenTicks;
chart.PrimaryAxis = primaryAxis;
NumericalAxis secondaryAxis = new NumericalAxis();
chart.SecondaryAxis = secondaryAxis;

StackedColumnSeries series1 = new StackedColumnSeries()
{
    ItemsSource = viewModel.AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter1",
    GroupName = "Group1",
};

StackedColumnSeries series2 = new StackedColumnSeries()
{
    ItemsSource = viewModel.AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter2",
    GroupName = "Group1",
};

StackedColumnSeries series3 = new StackedColumnSeries()
{
    ItemsSource = viewModel.AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter3",
    GroupName = "Group2",
};

StackedColumnSeries series4 = new StackedColumnSeries()
{
    ItemsSource = viewModel.AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter4",
    GroupName = "Group2",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
chart.Series.Add(series4);
...

{% endhighlight %}

{% endtabs %}

![Stacked group chart in WinUI Chart](Grouped_Stacking_Images/WinUI_Chart_GroupingStacked.png)
