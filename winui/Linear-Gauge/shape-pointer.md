---
layout: post
title: Shape Pointer in WinUI Linear Gauge control | Syncfusion
description: Learn here all about Shape Pointer feature of Syncfusion WinUI Linear Gauge control with custom support.
platform: WinUI
control: SfLinearGauge
documentation: ug
---

# Shape Pointer in WinUI Linear Gauge

Indicate current values by using the different types of shape pointers. You can change the shape type using the [`ShapeType`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.GaugeShapeType.html) property.

{% tabs %}

{% highlight xaml %}

<gauge:SfLinearGauge>
    <gauge:SfLinearGauge.Axis>
        <gauge:LinearAxis>
            <gauge:LinearAxis.MarkerPointers>
                <gauge:LinearShapePointer Value="60" />
            </gauge:LinearAxis.MarkerPointers>
        </gauge:LinearAxis>
    </gauge:SfLinearGauge.Axis>
</gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

SfLinearGauge sfLinearGauge = new SfLinearGauge();

LinearShapePointer linearShapePointer = new LinearShapePointer();
linearShapePointer.Value = 60;
sfLinearGauge.Axis.MarkerPointers.Add(linearShapePointer);

this.Content = sfLinearGauge;

{% endhighlight %}

{% endtabs %}

![default shape pointer](images/shape-pointer/pointer_default.png)

Gauge supports the following types of shape pointer:

* Circle
* Diamond
* Inverted triangle
* Triangle
* Rectangle

![all default shape pointers](images/shape-pointer/pointer_shapes.png)

## Custom shape pointer

You can add customized shapes to denote the current pointer value instead of in-built shape. It can be achieved by providing required shape in [`ShapeTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_ShapeTemplate) property.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="CustomShapePointer">
        <Grid>
            <Rectangle Fill="{Binding Fill}"
                       Stroke="{Binding Stroke}"
                       StrokeThickness="{Binding SrokeThickness}"
                       Width="{Binding ShapeHeight}"
                       Height="{Binding ShapeHeight}"
                       RadiusX="3"
                       RadiusY="3" />
        </Grid>
    </DataTemplate>
</Page.Resources>

<gauge:SfLinearGauge>
    <gauge:SfLinearGauge.Axis>
        <gauge:LinearAxis>
            <gauge:LinearAxis.MarkerPointers>
                <gauge:LinearShapePointer Value="60" 
                                    ShapeTemplate="{StaticResource CustomShapePointer}"/>
            </gauge:LinearAxis.MarkerPointers>
        </gauge:LinearAxis>
    </gauge:SfLinearGauge.Axis>
</gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

SfLinearGauge sfLinearGauge = new SfLinearGauge();

LinearShapePointer linearShapePointer = new LinearShapePointer();
linearShapePointer.Value = 60;
linearShapePointer.ShapeTemplate = this.Resources["CustomShapePointer"] as DataTemplate;
sfLinearGauge.Axis.MarkerPointers.Add(linearShapePointer);

this.Content = sfLinearGauge;

{% endhighlight %}

{% endtabs %}

![custom shape pointer](images/shape-pointer/pointer_template.png)

## Shape customization

The shape pointer can be customized using the following properties:

* [`Fill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_Fill) – Allows to customize the shape color.
* [`Stroke`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_Stroke) – Allows to specify the border color for the shape.
* [`StrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_StrokeThickness) –  Allows to specify the border width of the shape.
* [`ShapeHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_ShapeHeight) – Allows to specify the shape height.
* [`ShapeWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearShapePointer.html#Syncfusion_UI_Xaml_Gauges_LinearShapePointer_ShapeWidth) – Allows to specify the shape width.

{% tabs %}

{% highlight xaml %}

<gauge:SfLinearGauge>
    <gauge:SfLinearGauge.Axis>
        <gauge:LinearAxis>
            <gauge:LinearAxis.MarkerPointers>
                <gauge:LinearShapePointer Value="60"
                                    ShapeHeight="30"
                                    ShapeWidth="30"
                                    Fill="LightBlue"
                                    Stroke="Black"
                                    StrokeThickness="3"
                                    ShapeType="Circle" />
            </gauge:LinearAxis.MarkerPointers>
        </gauge:LinearAxis>
    </gauge:SfLinearGauge.Axis>
</gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

SfLinearGauge sfLinearGauge = new SfLinearGauge();

LinearShapePointer linearShapePointer = new LinearShapePointer();
linearShapePointer.Value = 60;
linearShapePointer.ShapeHeight = 30;
linearShapePointer.ShapeWidth = 30;
linearShapePointer.Fill = new SolidColorBrush(Colors.LightBlue);
linearShapePointer.Stroke = new SolidColorBrush(Colors.Black);
linearShapePointer.StrokeThickness = 3;
linearShapePointer.ShapeType = GaugeShapeType.Circle;
sfLinearGauge.Axis.MarkerPointers.Add(linearShapePointer);

this.Content = sfLinearGauge;

{% endhighlight %}

{% endtabs %}

![shape pointer customization](images/shape-pointer/shape_customization.png)

## Shape position customization

The shape pointer can be moved near or far from its actual position in X or Y direction using the [`OffsetPoint`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearMarkerPointer.html#Syncfusion_UI_Xaml_Gauges_LinearMarkerPointer_OffsetPoint) property. 

To move the pointer inside of the axis, provide positive values.

To move the pointer outside of the axis, provide negative values.

{% tabs %}

{% highlight xaml %}

<gauge:SfLinearGauge>
    <gauge:SfLinearGauge.Axis>
        <gauge:LinearAxis>
            <gauge:LinearAxis.MarkerPointers>
                <gauge:LinearShapePointer Value="60"
                                    OffsetPoint="0,-25"/>
            </gauge:LinearAxis.MarkerPointers>
        </gauge:LinearAxis>
    </gauge:SfLinearGauge.Axis>
</gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

SfLinearGauge sfLinearGauge = new SfLinearGauge();

LinearShapePointer linearShapePointer = new LinearShapePointer();
linearShapePointer.Value = 60;
linearShapePointer.OffsetPoint = new Point(0, -25);
sfLinearGauge.Axis.MarkerPointers.Add(linearShapePointer);

this.Content = sfLinearGauge;

{% endhighlight %}

{% endtabs %}

![pointer offset](images/shape-pointer/pointer_offset.png)

### Shape pointer alignment

You can change the horizontal or vertical position of the shape pointer either start, end or center by using the [`HorizontalAnchor`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearMarkerPointer.html#Syncfusion_UI_Xaml_Gauges_LinearMarkerPointer_HorizontalAnchor) and [`VerticalAnchor`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearMarkerPointer.html#Syncfusion_UI_Xaml_Gauges_LinearMarkerPointer_VerticalAnchor) properties. The default value of [`HorizontalAnchor`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearMarkerPointer.html#Syncfusion_UI_Xaml_Gauges_LinearMarkerPointer_HorizontalAnchor) and [`VerticalAnchor`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.LinearMarkerPointer.html#Syncfusion_UI_Xaml_Gauges_LinearMarkerPointer_VerticalAnchor) properties are center.

{% tabs %}

{% highlight xaml %}

<gauge:SfLinearGauge>
    <gauge:SfLinearGauge.Axis>
        <gauge:LinearAxis>
            <gauge:LinearAxis.MarkerPointers>
                <gauge:LinearShapePointer Value="60"
                                    VerticalAnchor="End"
                                    OffsetPoint="0,-5" />
            </gauge:LinearAxis.MarkerPointers>
        </gauge:LinearAxis>
    </gauge:SfLinearGauge.Axis>
</gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

SfLinearGauge sfLinearGauge = new SfLinearGauge();

LinearShapePointer linearShapePointer = new LinearShapePointer();
linearShapePointer.Value = 60;
linearShapePointer.VerticalAnchor = GaugeAnchor.End;
linearShapePointer.OffsetPoint = new Point(0, -5);
sfLinearGauge.Axis.MarkerPointers.Add(linearShapePointer);

this.Content = sfLinearGauge;

{% endhighlight %}

{% endtabs %}

![pointer anchor placement customization](images/shape-pointer/pointer_anchor.png)
