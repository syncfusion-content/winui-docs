---
layout: post
title: Stacked group chart in WinUI Chart control | Syncfusion
description: Learn here all about the stacked group chart and its features in Syncfusion WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfChart
documentation: ug
keywords: stacked group chart in winui chart, winui stacked group chart customization, syncfusion winui stacked group chart, winui sfcartesianchart stacked group chart settings.
---

# Stacked Group Chart in WinUI Chart (SfCartesianChart)

Chart provides support to group the stacked similar series by using the [GroupName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StackedSeriesBase.html#Syncfusion_UI_Xaml_Charts_StackedSeriesBase_GroupName) property of stacked series. The stacked series which contains the same [GroupName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StackedSeriesBase.html#Syncfusion_UI_Xaml_Charts_StackedSeriesBase_GroupName) will be stacked in a single group.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis LabelPlacement="BetweenTicks"/>
    </chart:SfCartesianChart.XAxes>

    <chart:SfCartesianChart.YAxes>
        <chart:NumericalAxis />
    </chart:SfCartesianChart.YAxes>  
    
    <chart:StackedColumnSeries GroupName="Group1" 
                               XBindingPath="Year" 
                               YBindingPath="Quarter1" 
                               ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group1" 
                               XBindingPath="Year" 
                               YBindingPath="Quarter2"
                               ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group2" 
                               XBindingPath="Year"  
                               YBindingPath="Quarter3" 
                               ItemsSource="{Binding AnnualDetails}"/>

    <chart:StackedColumnSeries GroupName="Group2" 
                               XBindingPath="Year"
                               YBindingPath="Quarter4" 
                               ItemsSource="{Binding AnnualDetails}"/>

</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ViewModel viewModel = new ViewModel();
CategoryAxis primaryAxis = new CategoryAxis();
primaryAxis.LabelPlacement = LabelPlacement.BetweenTicks;
chart.XAxes.Add(primaryAxis);
NumericalAxis secondaryAxis = new NumericalAxis();
chart.YAxes.Add(secondaryAxis);

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
