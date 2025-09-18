---
layout: post
title: Zooming and Panning in WinUI Chart Control | Syncfusion
description: Learn all about the Zooming and Panning feature of the Syncfusion® WinUI Chart (SfCartesianChart) control.
platform: WinUI
control: SfCartesianChart
documentation: ug
keywords: zooming and panning in winui chart, winui sfcartesianchart zooming and panning, winui chart zooming and panning customization, syncfusion winui chart zooming and panning, winui sfcartesianchart zooming and panning settings, winui chart zooming and panning properties.
---

# Zooming and Panning in WinUI Chart (SfCartesianChart)

The [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html) allows you to zoom the chart area using the zoom feature. This functionality is particularly useful for viewing data points in specific areas when there are a large number of data points within the chart.

Zooming and panning enable you to take a close-up look at the data points plotted in the series.

## Enable Zooming

To enable zooming and panning in the chart, create an instance of [ChartZoomPanBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html) and assign it to the [ZoomPanBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html#Syncfusion_UI_Xaml_Charts_SfCartesianChart_ZoomPanBehavior) property of the [SfCartesianChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfCartesianChart.html).

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    ...
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior />
    </chart:SfCartesianChart.ZoomPanBehavior>
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior();
chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}

## Zooming the Chart Area

Zooming the chart area can be accomplished in various ways, including pinch zooming, mouse wheel zooming, selection zooming, and by using the properties [ZoomFactor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ZoomFactor) and [ZoomPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ZoomPosition).

### Pinch Zooming

Pinch zooming is enabled by setting the [EnablePinchZooming](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePinchZooming) property to `true`, as demonstrated in the code snippet below.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior EnablePinchZooming="True"/>
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnablePinchZooming = true
};

chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}

### Mouse Wheel Zooming

To perform zooming using mouse wheel actions, set the [EnableMouseWheelZooming](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnableMouseWheelZooming) property to `true`.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior EnableMouseWheelZooming="True"/>
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableMouseWheelZooming = true
};

chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}

### Zooming by Setting ZoomFactor and ZoomPosition

The [ZoomFactor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ZoomFactor) property defines the percentage of the visible range from the total range of axis values. The [ZoomPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ZoomPosition) property defines the position for ranges of values to be displayed as a result of the [ZoomFactor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ZoomFactor). 

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.XAxes>
        <chart:CategoryAxis ShowMajorGridLines="False" ZoomFactor="0.3" ZoomPosition="0.5"/>
    </chart:SfCartesianChart.XAxes>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
CategoryAxis primaryAxis = new CategoryAxis()
{
    ShowMajorGridLines = false,
    ZoomFactor = 0.3,
    ZoomPosition = 0.5
};
chart.XAxes.Add(primaryAxis);
...

{% endhighlight %}

{% endtabs %}

![Zooming support in WinUI Chart](Zooming-and-panning_images/WinUI_chart_zooming.png)

## Zooming Mode

Zooming can be performed both horizontally and vertically. The zooming direction is defined by the [ZoomMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_ZoomMode) property.

The following code example demonstrates restricting the chart to be zoomed only along the horizontal axis.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior ZoomMode="X" />
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
...
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    ZoomMode = ZoomMode.X
};

chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Chart](Zooming-and-panning_images/WinUI_chart_zoom_modeX.png)

The following code example demonstrates restricting the chart to be zoomed only along the vertical axis.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior ZoomMode="Y" />
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    ZoomMode = ZoomMode.Y
};

chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Chart](Zooming-and-panning_images/WinUI_chart_zoom_modeY.png)

## Enable Panning

The panning feature allows the movement of the visible area of the chart when it is zoomed in. To enable panning, set the [EnablePanning](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePanning) property to `true`.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart>
    <chart:SfCartesianChart.ZoomPanBehavior>
        <chart:ChartZoomPanBehavior EnableMouseWheelZooming="True" EnablePanning="True"/>
    </chart:SfCartesianChart.ZoomPanBehavior>
    ...
</chart:SfCartesianChart>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableMouseWheelZooming = true,
    EnablePanning = true
};

chart.ZoomPanBehavior = zooming;
...

{% endhighlight %}

{% endtabs %}