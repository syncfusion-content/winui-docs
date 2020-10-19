---
layout: post
title: Syncfusion WinUI Gauge Pointers
description: This article describes how to add and customizes the appearence of pointers of radial gauge control in WinUI platform
platform: WinUI
control: SfRadialGauge
documentation: ug
---

# Range Pointer in WinUI Radial Gauge (SfRadialGauge)

A range pointer is an accenting line or shaded background range that can be placed on a gauge to mark the current value.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="30" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 30;
radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![default range pointer](images/range-pointer/pointer_default.png)

The following properties are used to customize the range pointer:

* `Background` – Customizes the color of range pointer.

* [`PointerWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerWidth) - Specifies the width of pointer either in pixels or factor.

* [`WidthUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_WidthUnit) – Specifies whether the [`PointerWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerWidth) is defined in pixels or factor.

The [`PointerWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerWidth) of the pointer can be specified either in pixel or factor. If the [`WidthUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_WidthUnit) is specified as Pixel, then the range will be rendered based on the provided pixel value. If the [`WidthUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_WidthUnit) is set as factor, the provided factor value will be multiplied with axis radius. For example, if the pointer width is set as 0.1, then 10% of axis radius is considered as range pointer width.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="30"
                                    PointerWidth="0.1"
                                    WidthUnit="Factor"
                                    Background="Indigo" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 30;
rangePointer.PointerWidth = 0.1;
rangePointer.WidthUnit = SizeUnit.Factor;
rangePointer.Background = new SolidColorBrush(Colors.Indigo);
radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![range pointer customization](images/range-pointer/pointer_customization.png)

 The default value of [`WidthUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_WidthUnit) and [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_OffsetUnit) is [`SizeUnit.Pixel`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.SizeUnit.html#Syncfusion_UI_Xaml_Gauges_SizeUnit_Pixel).
 
 **Setting gradient brush to the pointer**

 The [`GradientStops`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_GradientStops) property of [`range pointer`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html) allows to specify the smooth color transition to pointer by specifying the different colors based on provided axis value.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis AxisLineWidth="0.1"
                          AxisLineWidthUnit="Factor">
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="40"
                                    PointerWidth="0.1"
                                    WidthUnit="Factor">
                    <gauge:RangePointer.GradientStops>
                        <gauge:GaugeGradientStop Value="10"
                                                 Color="#FFCC2B5E" />
                        <gauge:GaugeGradientStop Value="30"
                                                 Color="#FF753A88" />
                    </gauge:RangePointer.GradientStops>
                </gauge:RangePointer>
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
radialAxis.AxisLineWidth = 0.1;
radialAxis.AxisLineWidthUnit = SizeUnit.Factor;
sfRadialGauge.Axes.Add(radialAxis);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 40;
rangePointer.PointerWidth = 0.1;
rangePointer.WidthUnit = SizeUnit.Factor;
rangePointer.GradientStops.Add(new GaugeGradientStop { Value = 10, Color = Color.FromArgb(255, 204, 43, 94) });
rangePointer.GradientStops.Add(new GaugeGradientStop { Value = 30, Color = Color.FromArgb(255, 117, 58, 136) });

radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![range pointer gradient](images/range-pointer/pointer_gradient.png)

**Corner style customization**

 The [`CornerStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_CornerStyle) property of [`range pointer`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html) specifies the corner type for pointer. The corners can be customized using the [`BothFlat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.CornerStyle.html#Syncfusion_UI_Xaml_Gauges_CornerStyle_BothFlat), [`BothCurve`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.CornerStyle.html#Syncfusion_UI_Xaml_Gauges_CornerStyle_BothCurve), [`StartCurve`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.CornerStyle.html#Syncfusion_UI_Xaml_Gauges_CornerStyle_StartCurve) and [`EndCurve`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.CornerStyle.html#Syncfusion_UI_Xaml_Gauges_CornerStyle_EndCurve) options. The default value of this property is [`BothFlat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.CornerStyle.html#Syncfusion_UI_Xaml_Gauges_CornerStyle_BothFlat).

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="30"
                                    CornerStyle="BothCurve" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 30;
rangePointer.CornerStyle = CornerStyle.BothCurve;
radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![range pointer customization](images/range-pointer/pointer_corner.png)

## Position customization

The following properties are used to customize the position of range pointer:

* [`PointerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerOffset) - Specifies the position value for pointer either in pixels or factor.

* [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_OffsetUnit) – Specifies whether the [`PointerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerOffset) is defined in pixels or factor.

The range pointer can be moved far or near to the axis line using the [`PointerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerOffset) property. The [`PointerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerOffset) can be set either in pixel or factor value using its [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_OffsetUnit).

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis>
            <gauge:RadialAxis.Pointers>
                <gauge:RangePointer Value="30"
                                    PointerOffset="70" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
sfRadialGauge.Axes.Add(radialAxis);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 30;
rangePointer.PointerOffset = 70;
radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![pointer position customization](images/range-pointer/pointer_offset.png)

When you set the [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_OffsetUnit) as pixel, the pointer will be moved to the provided pixel value.

If the [`OffsetUnit`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_OffsetUnit) is specified as factor, the factor value will be multiplied with the axis radius. For example, if you set [`PointerOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Gauges.RangePointer.html#Syncfusion_UI_Xaml_Gauges_RangePointer_PointerOffset) as 0.1, then the pointer offset is considered as 10% of axis radius.