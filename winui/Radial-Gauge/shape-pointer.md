---
layout: post
title: Shape Pointer in WinUI Radial Gauge control | Syncfusion
description: Learn here all about Shape Pointer feature of Syncfusion WinUI Radial Gauge control with customization support.
platform: WinUI
control: SfRadialGauge
documentation: ug
---

# Shape Pointer in WinUI Radial Gauge

The `ShapePointer` in [`SfRadialGauge`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.SfRadialGauge.html) allows you to use any build-in shapes (`ShapeType`) as a pointer to mark a specified value. The default `ShapeType` of the ShapePointer is InvertedTriangle.

{% tabs %}

{% highlight xaml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:ShapePointer Value="60" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

ShapePointer shapePointer = new ShapePointer();
shapePointer.Value = 60;
radialAxis.Pointers.Add(shapePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![WinUI Radial Gauge Default Shape Pointer](images/marker-pointers/winui-radial-gauge-default-marker-pointer.png)

Gauge supports the following types of shapes:

* Inverted triangle
* Triangle
* Circle
* Rectangle
* Diamond

![WinUI Radial Gauge Shapes](images/marker-pointers/winui-radial-shape-pointer-shapes.png)

## Shape customization

The shape pointer can be customized using the following properties:

* `Fill` – Allows to customize the shape color.
* `ShaperHeight` – Allows to specify the shape height.
* `ShapeWidth` – Allows to specify the shape width.
* `Stroke` – Allows to specify the border color for the shape.
* `StrokeThickness` –  Allows to specify the border width of the shape.

{% tabs %}

{% highlight xaml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:ShapePointer Value="60"
                                     ShapeHeight="30"
                                     ShapeWidth="30"
                                     BorderBrush="Black"
                                     BorderWidth="3"
                                     ShapeType="Circle"
                                     Background="LightBlue"/>
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

ShapePointer shapePointer = new ShapePointer();
shapePointer.Value = 60;
shapePointer.ShapeHeight = 30;
shapePointer.ShapeWidth = 30;
shapePointer.Stroke = new SolidColorBrush(Colors.Black);
shapePointer.StrokeThickness = 3;
shapePointer.ShapeType = Syncfusion.UI.Xaml.Gauges.GaugeShapeType.Circle;
shapePointer.Fill = new SolidColorBrush(Colors.LightBlue);
radialAxis.Pointers.Add(shapePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![WinUI Radial Gauge Custom Shape Pointer](images/marker-pointers/winui-radial-gauge-custom-marker-pointer.png)

## Shape position customization

The shape pointer can be moved near or far from its actual position using the [`MarkerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_MarkerOffset) and [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_OffsetUnit) properties. 

When you set [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_OffsetUnit) to pixel, the shape pointer will be moved based on the pixel value. If you set [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_OffsetUnit) to factor, then provided factor will be multiplied with the axis radius value, and then the pointer will be moved to corresponding value. The default value of [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_OffsetUnit) is [`SizeUnit.Pixel`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.SizeUnit.html#Syncfusion_UI_Xaml_Gauges_SizeUnit_Pixel).

{% tabs %}

{% highlight xaml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:ShapePointer Value="60"
                                     MarkerOffset="-18"/>
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

ShapePointer shapePointer = new ShapePointer();
shapePointer.Value = 60;
shapePointer.MarkerOffset = -18;
radialAxis.Pointers.Add(shapePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![WinUI Radial Gauge Marker Offset](images/marker-pointers/winui-radial-gauge-marker-offset.png)

N> Provide positive value to [`MarkerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.MarkerPointer.html#Syncfusion_UI_Xaml_Gauges_MarkerPointer_MarkerOffset) to move the pointer inside of the axis and negative value to move the pointer outside of the axis.