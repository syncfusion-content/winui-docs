---
layout: post
title: Syncfusion Flutter Gauge Animation
description: This article describes how to add and customizes the appearence gauge annotation of radial gauge control in flutter platform
platform: flutter
control: SfRadialGauge
documentation: ug
---

# Animation in  radial gauge

## Pointer Animation
The `EnableAnimation` property of pointer allows to enable or disable animation for pointer and the `AnimationDuration` property of pointer allows to control the animation duration in milliseconds. The default value of animation duration is 1500ms.

{% tabs %}

{% highlight xml %}

<gauge:SfRadialGauge>
    <gauge:SfRadialGauge.Axes>
        <gauge:RadialAxis AxisLineWidth="30"
                          ShowTicks="False">
            <gauge:RadialAxis.Pointers>
                <gauge:NeedlePointer Value="60"
                                     EnableAnimation="True"
                                     NeedleStartWidth="0"
                                     NeedleEndWidth="15"
                                     NeedleFill="#FFDADADA"
                                     KnobFill="White"
                                     KnobStroke="#FFDADADA"
                                     KnobRadius="0.06"
                                     KnobStrokeThickness="0.04"
                                     TailFill="#FFDADADA"
                                     TailLength="0.15"
                                     TailWidth="15">
                </gauge:NeedlePointer>
                <gauge:RangePointer Value="60"
                                    PointerWidth="30"
                                    EnableAnimation="True"
                                    Background="Orange" />
            </gauge:RadialAxis.Pointers>
        </gauge:RadialAxis>
    </gauge:SfRadialGauge.Axes>
</gauge:SfRadialGauge>

{% endhighlight %}

{% highlight c# %}

SfRadialGauge sfRadialGauge = new SfRadialGauge();

RadialAxis radialAxis = new RadialAxis();
radialAxis.ShowTicks = false;
radialAxis.AxisLineWidth = 30;
sfRadialGauge.Axes.Add(radialAxis);

NeedlePointer needlePointer = new NeedlePointer();
needlePointer.Value = 60;
needlePointer.EnableAnimation = true;
needlePointer.NeedleStartWidth = 0;
needlePointer.NeedleEndWidth = 15;
needlePointer.NeedleFill = new SolidColorBrush(Color.FromArgb(255, 218, 218, 218));
needlePointer.KnobFill = new SolidColorBrush(Colors.White);
needlePointer.KnobStroke = new SolidColorBrush(Color.FromArgb(255, 218, 218, 218));
needlePointer.KnobRadius = 0.06;
needlePointer.KnobStrokeThickness = 0.04;
needlePointer.TailFill = new SolidColorBrush(Color.FromArgb(255, 218, 218, 218));
needlePointer.TailLength = 0.15;
needlePointer.TailWidth = 15;
radialAxis.Pointers.Add(needlePointer);

RangePointer rangePointer = new RangePointer();
rangePointer.Value = 60;
rangePointer.PointerWidth = 30;
rangePointer.EnableAnimation = true;
rangePointer.Background = new SolidColorBrush(Colors.Orange);
radialAxis.Pointers.Add(rangePointer);

this.Content = sfRadialGauge;

{% endhighlight %}

{% endtabs %}

![pointer animation](images/animation/animation.gif)