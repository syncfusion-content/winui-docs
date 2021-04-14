---
layout: post
title: Grouping Stacked in WinUI Chart control | Syncfusion
description: Learn here all about Grouping Stacked feature of Syncfusion WinUI Chart control and more details.
platform: WinUI
control: SfChart
documentation: ug
---

# Grouping Stacked in WinUI Chart

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

![Grouping of stacked series in WinUI Chart](Series_images/groupingstacked.png)
