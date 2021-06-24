---
layout: post
title: Zooming and Panning in WinUI Cartesian Chart control | Syncfusion
description: Learn here all about Zooming and Panning feature of Syncfusion WinUI Cartesian Chart(SfCartesianChart) control and Events.
platform: WinUI
control: SfCartesianChart
documentation: ug
---

# Zooming and Panning in WinUI Cartesian Chart (SfCartesianChart)

SfCartesianChart allows you to zoom the chart area with the help of the zoom feature. This behavior is mostly used to view the data point in the specific area, when there are a number of data points inside the chart.

Zooming and panning provides you to take a close-up look of the data point plotted in the series

## Define ZoomPanBehavior

To enable the Zooming and Panning in chart, create an instance of [ChartZoomPanBehavior]() and add it to the `Behaviors` collection of Cartesian chart.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior />
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfCartesianChart chart = new SfCartesianChart();
. . .
ChartZoomPanBehavior zooming = new ChartZoomPanBehavior();
chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

## Zooming the ChartArea

### Zooming by setting ZoomFactor and ZoomPosition

[ZoomFactor]() defines the percentage of visible range from the total range of axis values. [ZoomPosition]() defines the ranges of values that need to be displayed as a result of [ZoomFactor](). 

The following code example demonstrates the zooming the chart axis by setting zoom position and zoom factor.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.PrimaryAxis>
    <chart:CategoryAxis ShowGridLines="False" ZoomFactor="0.3" ZoomPosition="0.5"/>
</chart:SfCartesianChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{
    ShowGridLines = false,
    ZoomFactor = 0.3,
    ZoomPosition = 0.5
};

{% endhighlight %}

{% endtabs %}

![Zooming support in WinUI Cartesian Chart](Zooming-and-panning_images/WinUI_cartesian_chart_zooming.png)

### Mouse Wheel Zooming

Zooming can be performed by mouse wheel action by setting [`EnableMouseWheelZooming`]() property to true.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnableMouseWheelZooming="True"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableMouseWheelZooming = true
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

### Pinch Zooming

If you want to zoom using fingers by touch, then you have to set [EnablePinchZooming]() property to true as shown in the below code snippet.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnablePinchZooming="True"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnablePinchZooming = true
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

 ### Zooming Relative to Cursor

To enable the zooming relative to cursor position you can set [ZoomRelativeToCursor]() property to true. This support is applicable only for mouse wheel zooming.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior ZoomRelativeToCursor="True"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    ZoomRelativeToCursor = true
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

 ### SelectionZooming

SelectionZooming helps us to zoom a particular area by selecting the region using rectangle. To enable the selection, you have to set [EnableSelectionZooming]() property to true.

The following code snippet demonstrated selection zooming.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnableSelectionZooming="True"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableSelectionZooming = true
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Selection zooming support in WinUI Cartesian Chart](Zooming-and-panning_images/WinUI_cartesian_chart_selection_zooming.png)


### Customization of Selection Rectangle

Selection rectangle can be customized by setting the following properties: 

* [Fill]() - Represents the brush filled in selection rectangle. 
* [Stroke]() - Represents the outer line color of selection rectangle.
* [StrokeThickness]()- Represents the selection rectangle outer line thickness. 

The following code example demonstrates the customization of selection rectangle

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnableSelectionZooming="True" Fill="LightSkyBlue" Stroke="Blue" StrokeThickness="2"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableSelectionZooming = true,
    Fill = new SolidColorBrush(Colors.LightSkyBlue),
    Stroke = new SolidColorBrush(Colors.Blue),
    StrokeThickness = 2
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Customizing selection rectangle support in WinUI Cartesian Chart](Zooming-and-panning_images/WinUI_cartesian_customizing_selection_rectangle_zooming.png)


### Zooming Mode

The zooming can be done both horizontally and vertically. The zooming direction is defined using [ZoomMode]() property.

Following code example illustrates how to restrict the chart to be zoomed only along horizontal axis,

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior ZoomMode="X" />
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    ZoomMode = ZoomMode.X
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Cartesian Chart](Zooming-and-panning_images/WinUI_cartesian_chart_zoom_modeX.png)


Following code example illustrates how to restrict the chart to be zoomed only along vertical axis,

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior ZoomMode="Y" />
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    ZoomMode = ZoomMode.Y
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Cartesian Chart](Zooming-and-panning_images/WinUI_cartesian_chart_zoom_modeY.png)

### Maximum Zoom Level

The [MaximumZoomLevel]() property defines the maximum zooming level. Zooming will be stopped after reaching this value.

{% tabs %}

{% highlight xaml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnableSelectionZooming="True" MaximumZoomLevel="100"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableSelectionZooming = true,
    MaximumZoomLevel = 100
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

## Panning the ChartArea

Panning feature allows moving the visible area of the chart when it is zoomed in. To enable panning, you have to set [EnablePanning]() property to true.

{% tabs %}

{% highlight xml %}

<chart:SfCartesianChart.Behaviors>
    <chart:ChartZoomPanBehavior EnableMouseWheelZooming="True" EnablePanning="True"/>
</chart:SfCartesianChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{
    EnableMouseWheelZooming = true,
    EnablePanning = true
};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

## Events

The following events are available in SfCartesianChart for ChartZoomPanBehavior:

### ZoomChanging

The [ZoomChanging]() event occurs when users start zooming the chart. This is a cancelable event. This argument contains the following information.

* [Axis]() - Gets an instance of the axis whose range is changed through zooming. This event is triggered for each axis in the chart.
* [Cancel]() - Gets or Sets a value that indicates whether the zooming should be canceled.
* [CurrentFactor]() - Gets the current zoom factor of the axis.
* [CurrentPosition]() - Gets the current zoom position of the axis.
* [OldRange]() - Gets the old visible range of the axis.
* [PreviousFactor]() - Gets the previous zoom factor of the axis.
* [PreviousPosition]() - Gets the previous zoom position of the axis.

### ZoomChanged

The [`ZoomChanged`]() event occurs after the zooming has been completed. This argument contains the following information.

* [Axis]() - Gets an instance of the axis whose range is changed through zooming. This event is triggered for each axis in the chart.
* [CurrentFactor]() - Gets the current zoom factor of the axis.
* [CurrentPosition]() - Gets the current zoom position of the axis.
* [OldRange]() - Gets the old visible range of the axis.
* [NewRange]() - Gets the new visible range of the axis.
* [PreviousFactor]() - Gets the previous zoom factor of the axis.
* [PreviousPosition]() - Gets the previous zoom position of the axis.
