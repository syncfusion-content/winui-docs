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

        <chart:StackedColumnSeries Interior="#4A4A4A" GroupingLabel="Group1" XBindingPath="Year" 
         YBindingPath="Quarter1" ItemsSource="{Binding AnnualDetails}"/>

        <chart:StackedColumnSeries Interior="#BCBCBC" GroupingLabel="Group1" XBindingPath="Year" 
          YBindingPath="Quarter2" ItemsSource="{Binding AnnualDetails}"/>

        <chart:StackedColumnSeries Interior="#7F7F7F" GroupingLabel="Group2" XBindingPath="Year"
          YBindingPath="Quarter3" ItemsSource="{Binding AnnualDetails}"/>

        <chart:StackedColumnSeries Interior="#343434" GroupingLabel="Group2" XBindingPath="Year"
          YBindingPath="Quarter4" ItemsSource="{Binding AnnualDetails}"/>

{% endhighlight %}

{% highlight c# %}

            SfChart chart = new SfChart();

            StackedColumnSeries series1 = new StackedColumnSeries()
            {
                ItemsSource = new ViewModel().AnnualDetails,
                XBindingPath = "Year",
                YBindingPath = "Quarter1",
                GroupingLabel = "Group1",
                Interior = new SolidColorBrush(Color.FromRgb(0x4A, 0x4A, 0x4A))
            };

            StackedColumnSeries series2 = new StackedColumnSeries()
            {
                ItemsSource = new ViewModel().AnnualDetails,
                XBindingPath = "Year",
                YBindingPath = "Quarter2",
                GroupingLabel = "Group1",
                Interior = new SolidColorBrush(Color.FromRgb(0xBC, 0xBC, 0xBC))
            };

            StackedColumnSeries series3 = new StackedColumnSeries()
            {
                ItemsSource = new ViewModel().AnnualDetails,
                XBindingPath = "Year",
                YBindingPath = "Quarter3",
                GroupingLabel = "Group2",
                Interior = new SolidColorBrush(Color.FromRgb(0x7F, 0x7F, 0x7F))
            };

            StackedColumnSeries series4 = new StackedColumnSeries()
            {
                ItemsSource = new ViewModel().AnnualDetails,
                XBindingPath = "Year",
                YBindingPath = "Quarter4",
                GroupingLabel = "Group2",
                Interior = new SolidColorBrush(Color.FromRgb(0x34, 0x34, 0x34))
            };

            chart.Series.Add(series1);
            chart.Series.Add(series2);
            chart.Series.Add(series3);
            chart.Series.Add(series4);
{% endhighlight %}

{% endtabs %}

![Grouping of stacked series in WinUI Chart](Series_images/groupingstacking.png)