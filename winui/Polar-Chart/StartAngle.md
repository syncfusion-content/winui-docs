---
layout: post
title: Start Angle in WinUI Chart Control | Syncfusion
description: This section explains how to change the angle position of rendering in the Syncfusion® WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Rendering Position in WinUI Chart (SfPolarChart)

By using the [StartAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPolarChart.html#Syncfusion_UI_Xaml_Charts_SfPolarChart_StartAngle) property of the polar chart, you can modify the rendering position of the series at four different degree values: 0, 90, 180, and 270. The default value of the [StartAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPolarChart.html#Syncfusion_UI_Xaml_Charts_SfPolarChart_StartAngle) property is [Rotate270](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartPolarAngle.html#Syncfusion_UI_Xaml_Charts_ChartPolarAngle_Rotate270).

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart StartAngle="Rotate0">
...
</chart:SfPolarChart>


{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
chart.StartAngle = ChartPolarAngle.Rotate0;
...

{% endhighlight %}

{% endtabs %}

![Rendering position for polar series in WinUI chart](StartAngle_Images/WinUI_Chart_Rotate0.png)
