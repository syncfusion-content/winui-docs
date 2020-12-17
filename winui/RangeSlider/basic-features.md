---
layout: post
title: Basic features of Syncfusion WinUI Range Slider
description: This article describes about the basic featue set of the Syncfusion range slider control in WinUi platform.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Basic Features of Range Slider

This section explains about how to add the WinUI slider with basic features.

## Setting Minimum and Maximum value

The `Minimum` and `Maximum` properties of a range slider can be used to customize the range. The default value of `Minimum` is 0 and the default value of `Maximum` is 100.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="-20"
                      Maximum="20"
                      RangeStart="-10"
                      RangeEnd="10"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = -20;
sfRangeSlider.Maximum = 20;
sfRangeSlider.RangeStart = -10;
sfRangeSlider.RangeEnd = 10;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with minimum and maximum customization](images/basic-features/slider-min-max.png)

## Interval

Slider elements like labels, ticks and divisors are rendered based on the `Interval`, `Minimum` and `Maximum` properties. The default value of `Interval` is double.NaN.

For example, if `Minimum` is 0 and `Maximum` is 10 and `Interval` is 2, the slider will render the labels, major ticks, and divisors at 0, 2, 4 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.Value = 4;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with interval customization](images/basic-features/slider-interval.png)

N> Slider having auto interval support. So, the auto interval calculated by default.

N>
* Refer the `ShowDivisors` to know about the rendering of divisors at given interval.
* Refer the `ShowTicks` to know about the rendering of major ticks at given interval.
* Refer the `ShowLabels` to know about the rendering of labels at given interval.

## Discrete Selection for Values

You can move the thumb in discrete manner for numeric values using the `StepFrequency` property in the slider.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 StepFrequency="2"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.Value = 4;
sfSlider.StepFrequency = 2;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with step frequency](images/basic-features/slider-stepFrequency.gif)

## Values

You can show values in the range slider by setting double values to the `RangeStart` and `RangeEnd` properties.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Setting value to range slider](images/basic-features/slider-value.png)

## Dragging Active Range

You can drag the active range in the range slider by setting `CanDragActiveRange` property as true. The default value of `CanDragActiveRange` is false.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="40"
                      RangeEnd="60"
                      CanDragActiveRange="True"
                      ShowLabels="True"
                      LabelOffset="10"  />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 40;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.CanDragActiveRange = true;
sfRangeSlider.ShowLabels = true;
sfRangeSlider.LabelOffset = 10;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with range dragging](images/basic-features/slider-canDragActiveRange.gif)

## Flow Direction Customization

The direction of range slider can be customized by its `IsInversed` property.

When the `IsInversed` property is true, the range slider can be placed in right-to-left direction. When the `IsInversed` property is set to false, the range slider will be positioned in left-to-right direction.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider ShowTicks="True"
                      ShowLabels="True"
                      Interval="20"
                      RangeStart="40"
                      RangeEnd="60"
                      IsInversed="True"/>

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
sfRangeSlider.Interval = 20;
sfRangeSlider.RangeStart = 40;
sfRangeSlider.RangeEnd = 60;
sfRangeSlider.IsInversed = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with is inversed customization](images/basic-features/slider-isInversed.png)

## Events

**RangeValueChanged**

The `RangeValueChanged` event occurs each time a `RangeStart` or `RangeEnd` get changed. You can get the following values in this event args:

* `RangeStartOldValue` – Gets the previous value of a range start.
* `RangeStartNewValue` – Gets the new value of a range start.
* `RangeEndOldValue` – Gets the previous value of a range end.
* `RangeEndNewValue` – Gets the new value of a range end.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      RangeValueChanged="SfRangeSlider_RangeValueChanged"/>

{% endhighlight %}

{% highlight c# %}

private void SfRangeSlider_RangeValueChanged(object sender, RangeValueChangedEventArgs e)
{
    var rangeStartOldValue = e.RangeStartOldValue;
    var rangeStartNewValue = e.RangeStartNewValue;
    var rangeEndOldValue = e.RangeEndOldValue;
    var rangeEndNewValue = e.RangeEndNewValue;
}

{% endhighlight %}

{% endtabs %}