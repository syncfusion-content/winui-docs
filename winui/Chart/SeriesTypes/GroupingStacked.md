---
layout: post
title: Grouping Stacked charts | SfChart | WinUI | Syncfusion
description: This section explains Grouping Stacked charts and its properties for customization in WinUI Charts (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---

# Grouping Stacked Series in WinUI Chart (SfChart)

You can group the stacked similar series using [`GroupName`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StackedSeriesBase.html#Syncfusion_UI_Xaml_Charts_StackedSeriesBase_GroupName) property of stacked series. The stacked series which contains the same [`GroupName`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.StackedSeriesBase.html#Syncfusion_UI_Xaml_Charts_StackedSeriesBase_GroupName) will be stacked in a single group.

The following code example shows how to group the stacked series.

{% tabs %}

{% highlight xaml %}

<chart:StackedColumnSeries GroupName="Group1" XBindingPath="Year" 
         YBindingPath="Quarter1" ItemsSource="{Binding AnnualDetails}"/>

<chart:StackedColumnSeries GroupName="Group1" XBindingPath="Year" 
          YBindingPath="Quarter2" ItemsSource="{Binding AnnualDetails}"/>

<chart:StackedColumnSeries GroupName="Group2" XBindingPath="Year"
          YBindingPath="Quarter3" ItemsSource="{Binding AnnualDetails}"/>

<chart:StackedColumnSeries GroupName="Group2" XBindingPath="Year"
          YBindingPath="Quarter4" ItemsSource="{Binding AnnualDetails}"/>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

StackedColumnSeries series1 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter1",
    GroupName = "Group1",
};

StackedColumnSeries series2 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter2",
    GroupName = "Group1",
};

StackedColumnSeries series3 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter3",
    GroupName = "Group2",
};

StackedColumnSeries series4 = new StackedColumnSeries()
{
    ItemsSource = new ViewModel().AnnualDetails,
    XBindingPath = "Year",
    YBindingPath = "Quarter4",
    GroupName = "Group2",
};

chart.Series.Add(series1);
chart.Series.Add(series2);
chart.Series.Add(series3);
chart.Series.Add(series4);
{% endhighlight %}

{% endtabs %}

![Grouping of stacked series in WinUI Chart](Series_images/groupingstacking.png)