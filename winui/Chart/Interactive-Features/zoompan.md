---
layout: post
title: Zooming and Panning in WinUI Chart control | Syncfusion
description: Learn here all about Zooming and Panning feature of Syncfusion WinUI Chart control and more details.
platform: WinUI
control: SfChart
documentation: ug
---

# Zooming and Panning in WinUI Chart

SfChart allows you to zoom the chart area with the help of the zoom feature. This behavior is mostly used to view the data point in the specific area, when there are a number of data points inside the chart.

Zooming and panning provides you to take a close-up look of the data point plotted in the series

## Adding ZoomPanBehavior to the SfChart

You can create an instance ChartZoomPanBehavior and add it to the Behaviors collection.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior >                                             

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior();

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}


## Zooming the ChartArea

**Zooming** **by** **setting** **ZoomFactor** **and** **ZoomPosition**

[`ZoomFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBase2D.html#Syncfusion_UI_Xaml_Charts_ChartAxisBase2D_ZoomFactor) defines the percentage of visible range from the total range of axis values. [`ZoomPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBase2D.html#Syncfusion_UI_Xaml_Charts_ChartAxisBase2D_ZoomPosition) defines the ranges of values that need to be displayed as a result of [`ZoomFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBase2D.html#Syncfusion_UI_Xaml_Charts_ChartAxisBase2D_ZoomFactor). 

The following code example demonstrates the zooming the chart axis by setting zoom position and zoom factor.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis 

ShowGridLines="False"

ZoomFactor="0.3" ZoomPosition="0.1" />

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    ShowGridLines = false,

    ZoomFactor = 0.1,

    ZoomPosition = 0.3

};

{% endhighlight %}

{% endtabs %}

![Zooming support in WinUI Chart](Interactive-Features_images/Interactive-Features_img24.jpeg)

**Mouse** **Wheel** **Zooming**

Zooming can be performed by mouse wheel action by setting [`EnableMouseWheelZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnableMouseWheelZooming) property to true.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnableMouseWheelZooming="True" >                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    EnableMouseWheelZooming = true

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

**Pinch** **Zooming**

If you want to zoom using fingers by touch, then you have to set [`EnablePinchZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePinchZooming) property to true as shown in the below code snippet.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnablePinchZooming="True" >                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    EnablePinchZooming = true

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

**Zooming** **Relative** **to** **Cursor**

To enable the zooming relative to cursor position you can set [`ZoomRelativeToCursor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_ZoomRelativeToCursor) property to true. This support is applicable only for mouse wheel zooming.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior ZoomRelativeToCursor="True" >                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    ZoomRelativeToCursor = true

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

**SelectionZooming**

SelectionZooming helps us to zoom a particular area by selecting the region using rectangle. To enable the selection, you have to set [`EnableSelectionZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnableSelectionZooming) property to true.

The following code snippet demonstrated selection zooming.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnableSelectionZooming="True" >                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    EnableSelectionZooming = true

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Selection zooming support in WinUI Chart](Interactive-Features_images/Interactive-Features_img25.jpeg)


**Customization** **of** **Selection** **Rectangle**

Selection rectangle can be customized by setting the following properties: 

* [`Fill`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_Fill)-Represents the brush filled in selection rectangle. 
* [`Stroke`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_Stroke)- Represents the outer line color of selection rectangle.
* [`StrokeThickness`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_StrokeThickness)- Represents the selection rectangle outer line thickness. 

The following code example demonstrates the customization of selection rectangle

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnableSelectionZooming="True" 

Fill="LightBlue" Stroke="Blue" StrokeThickness="2" >                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    EnableSelectionZooming = true,

    Fill = new SolidColorBrush(Colors.LightBlue),

    Stroke = new SolidColorBrush(Colors.Blue),

    StrokeThickness = 2

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Customizing selection rectangle support in WinUI Chart](Interactive-Features_images/Interactive-Features_img26.jpeg)


**Zooming** **Mode**

The zooming can be done both horizontally and vertically. The zooming direction is defined using [`ZoomMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_ZoomMode) property.

Following code example illustrates how to restrict the chart to be zoomed only along horizontal axis,

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior ZoomMode="X">                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    ZoomMode = ZoomMode.X

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Chart](Interactive-Features_images/Interactive-Features_img27.jpeg)


Following code example illustrates how to restrict the chart to be zoomed only along vertical axis,

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior ZoomMode="Y">                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartZoomPanBehavior zooming = new ChartZoomPanBehavior()
{

    ZoomMode = ZoomMode.Y

};

chart.Behaviors.Add(zooming);

{% endhighlight %}

{% endtabs %}

![Zoom mode support in WinUI Chart](Interactive-Features_images/Interactive-Features_img28.jpeg)

**Maximum** **Zoom** **Level**

You can also limit the zooming by setting [`MaximumZoomLevel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_MaximumZoomLevel) property as shown in the following code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnableSelectionZooming="True" MaximumZoomLevel="100">                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

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

Panning feature allows moving the visible area of the chart when it is zoomed in. To enable panning, you have to set [`EnablePanning`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartZoomPanBehavior.html#Syncfusion_UI_Xaml_Charts_ChartZoomPanBehavior_EnablePanning) property to true.

{% tabs %}

{% highlight xml %}
<syncfusion:SfChart.Behaviors>

<syncfusion:ChartZoomPanBehavior EnableMouseWheelZooming="True" EnablePanning="True">                                              

</syncfusion:ChartZoomPanBehavior>

</syncfusion:SfChart.Behaviors>

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

The following image demonstrates the cursor panning in the left direction.

![Panning support in WinUI Chart](Interactive-Features_images/Interactive-Features_img33.jpeg)

## Events

The following events are available in SfChart for ChartZoomPanBehavior:

### ZoomChanging

The [`ZoomChanging`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when users start zooming the chart. This is a cancelable event. This argument contains the following information.

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_Axis) - Gets an instance of the axis whose range is changed through zooming. This event is triggered for each axis in the chart.
* [`Cancel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomChangingEventArgs_Cancel) - Gets or Sets a value that indicates whether the zooming should be canceled.
* [`CurrentFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_CurrentFactor) - Gets the current zoom factor of the axis.
* [`CurrentPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_CurrentPosition) - Gets the current zoom position of the axis.
* [`OldRange`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_OldRange) - Gets the old visible range of the axis.
* [`PreviousFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_PreviousFactor) - Gets the previous zoom factor of the axis.
* [`PreviousPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_PreviousPosition) - Gets the previous zoom position of the axis.

### ZoomChanged

The [`ZoomChanged`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs after the zooming has been completed. This argument contains the following information.

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_Axis) - Gets an instance of the axis whose range is changed through zooming. This event is triggered for each axis in the chart.
* [`CurrentFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_CurrentFactor) - Gets the current zoom factor of the axis.
* [`CurrentPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_CurrentPosition) - Gets the current zoom position of the axis.
* [`OldRange`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_OldRange) - Gets the old visible range of the axis.
* [`NewRange`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomChangedEventArgs_NewRange) - Gets the new visible range of the axis.
* [`PreviousFactor`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_PreviousFactor) - Gets the previous zoom factor of the axis.
* [`PreviousPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ZoomEventArgs_PreviousPosition) - Gets the previous zoom position of the axis.

### SelectionZoomingStart

The [`SelectionZoomingStart`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when users start selection zooming. This argument contains the following information.

* [`ZoomRect`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SelectionZoomingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionZoomingEventArgs_ZoomRect) - Gets the initial bounds of the selected region.

### SelectionZoomingEnd

The [`SelectionZoomingEnd`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs after selection zooming ends. This argument contains the following information.

* [`ZoomRect`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SelectionZoomingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionZoomingEventArgs_ZoomRect) - Gets the final bounds of the selected region.

### SelectionZoomingDelta

The [`SelectionZoomingDelta`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when selecting a region to be zoomed. This is a cancelable event. This argument contains the following information.

* [`ZoomRect`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SelectionZoomingEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionZoomingEventArgs_ZoomRect) - Gets the final bounds of the selected region.
* [`Cancel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SelectionZoomingDeltaEventArgs.html#Syncfusion_UI_Xaml_Charts_SelectionZoomingDeltaEventArgs_Cancel) - Gets or Sets a value that indicates whether the selection zooming should be canceled.

### PanChanging

The [`PanChanging`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when users start panning the chart. This is a cancelable event. This argument contains the following information:

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanningEventArgs.html#Syncfusion_UI_Xaml_Charts_PanningEventArgs_Axis) - Gets an instance of the axis whose range is changed while panning. This event is triggered for each axis in the chart.
* [`Cancel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_PanChangingEventArgs_Cancel) - Gets or Sets a value that indicates whether the panning should be canceled.
* [`NewZoomPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanningEventArgs.html#Syncfusion_UI_Xaml_Charts_PanningEventArgs_NewZoomPosition) - Gets a new zoom position of the axis.
* [`OldZoomPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_PanChangingEventArgs_OldZoomPosition) - Gets the old zoom position of the axis.

### PanChanged

The [`PanChanged`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when panning is completed. This argument contains the following information.

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanningEventArgs.html#Syncfusion_UI_Xaml_Charts_PanningEventArgs_Axis) - Gets an instance of the axis whose range is changed while panning. This event is triggered for each axis in the chart.
* [`NewZoomPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PanningEventArgs.html#Syncfusion_UI_Xaml_Charts_PanningEventArgs_NewZoomPosition) - Gets a new zoom position of the axis.
 
### ResetZooming

The [`ResetZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html) event occurs when resetting the chart on double tap. This is a cancelable event. This argument contains the following information.

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ResetZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ResetZoomEventArgs_Axis) - Gets an instance of the axis whose range is changed when panning. This event is triggered for each axis in the chart.
* [`Cancel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ResetZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ResetZoomEventArgs_Cancel) - Gets or Sets a value that indicates whether the panning should be canceled.
* [`PreviousZoomRange`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ResetZoomEventArgs.html#Syncfusion_UI_Xaml_Charts_ResetZoomEventArgs_PreviousZoomRange) - Gets the previous visible range of the axis.
