---
layout: post
title: Series in WinUI Chart control | Syncfusion
description: Learn here all about Series support in Syncfusion WinUI Chart(SfChart) control with series types and more.
platform: WinUI
control: SfChart
documentation: ug
---

# Series in WinUI Chart

ChartSeries is the visual representation of the data. SfChart offers many types of series ranging from LineSeries to StackedSeries like StackedColumn and StackedBar. Based on your requirements and specifications, any type of Series can be added for data visualization. 

The following APIs are common for the most of the series types:

* [`XBindingPath`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_XBindingPath) - A string property that represents the X values for the series.
* [`YBindingPath`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.XyDataSeries.html#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) - A string property that represents the Y values for the series.
* [`Stroke`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_Stroke) - Represents the brush for the series outline.
* [`StrokeThickness`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeries.html#Syncfusion_UI_Xaml_Charts_ChartSeries_StrokeThickness) - Represents the thickness of the series outline.
* [`Interior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_Interior) - Represents the brush to fill the series.
* [`Palette`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_Palette) - Used to define the set of pre-defined or custom colors for the series.
* [`IsSeriesVisible`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_IsSeriesVisible) - A bool property, which is used to enable or disable the series visibility.
