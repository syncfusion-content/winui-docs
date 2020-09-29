---
layout: post
title: Syncfusion WinUI Gauge Pointers
description: This article describes how to add and customizes the appearence of pointers of radial gauge control in winui platform
platform: winui
control: SfRadialGauge
documentation: ug
---

# Pointers in radial gauge

 Pointer is used to indicate values on an axis. The radial gauge control has three types of pointers: 

`Marker pointer`
`Needle pointer`
`Range pointer`

All the pointers can be customized as needed. You can add multiple pointers to the gauge to point multiple values on the same scale. The value of the pointer is set using the `Value` property.

![multiple pointers](images/pointers/pointers.png)

## Multiple pointers

In addition to the default pointer, you can add n number of pointers to an axis by adding in the `Pointers` property.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="30" />
                <gauge:MarkerPointer Value="70" />
                <gauge:NeedlePointer Value="60" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
RangePointer rangePointer = new RangePointer { Value = 30 };
radialAxis.Pointers.Add(rangePointer);
MarkerPointer markerPointer = new MarkerPointer { Value = 70 };
radialAxis.Pointers.Add(markerPointer);
NeedlePointer needlePointer = new NeedlePointer { Value = 60 };
radialAxis.Pointers.Add(needlePointer);

sfRadialGauge.Axes.Add(radialAxis);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![multiple pointers](images/pointers/multiple_pointer.png)

## Pointer dragging

Pointers can be dragged over the scale value. It can be achieved by clicking and dragging the pointer. To enable or disable the pointer drag, use the `IsInteractive` property.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis ShowTicks="False"
                          AxisLineFill="CornflowerBlue"
                          AxisLineWidth="30">
            <gauge:RadialAxis.Pointers>
                <gauge:MarkerPointer Value="30"
                                     IsInteractive="True"
                                     MarkerOffset="-30"
                                     Background="Indigo" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
radialAxis.ShowTicks = false;
radialAxis.AxisLineFill = new SolidColorBrush(Colors.CornflowerBlue);
radialAxis.AxisLineWidth = 30;
sfRadialGauge.Axes.Add(radialAxis);

MarkerPointer markerPointer = new MarkerPointer();
markerPointer.Value = 30;
markerPointer.IsInteractive = true;
markerPointer.Background = new SolidColorBrush(Colors.Indigo);
markerPointer.MarkerOffset = -30;
radialAxis.Pointers.Add(markerPointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![pointer dragging](images/pointers/pointer-interaction.gif)

## Event

`ValueChangeStarted` - Occurs whenever the pointer starts to drag.

`ValueChanging` - Occurs before the current drag value gets updated as pointer value. The `Cancel` argument of `ValueChangingEventArgs` allows to restrict the update of current drag value as pointer value.

`ValueChanged` - Occurs whenever the pointer value is changed while dragging.

`ValueChangeCompleted` - Occurs once the dragging of the pointer gets completed.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis ShowTicks="False"
                          AxisLineFill="CornflowerBlue"
                          AxisLineWidth="30">
            <gauge:RadialAxis.Pointers>
                <gauge:MarkerPointer Value="30"
                                     IsInteractive="True"
                                     MarkerOffset="-30"
                                     Background="Indigo" 
                                     ValueChanging="MarkerPointer_ValueChanging"
                                     ValueChanged="MarkerPointer_ValueChanged"/>
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

private void MarkerPointer_ValueChanging(object sender, ValueChangingEventArgs e)
{
    if (e.NewValue > 60)
    {
        e.Cancel = true;
    }
}

private void MarkerPointer_ValueChanged(object sender, ValueChangedEventArgs e)
{

}

{% endhighlight %}

{% endtabs %}