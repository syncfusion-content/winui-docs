---
layout: post
title: Basic features of Syncfusion WinUI Slider
description: This article describes about the basic featue set of the Syncfusion slider control in WinUi platform.
platform: WinUI
control: SfSlider
documentation: ug
---

# Basic Features of slider

This section explains about how to add the WinUI slider with basic features.

## Setting Minimum and Maximum value

The `Minimum` and `Maximum` properties of an slider can be used to customize the value range. The default value of `Minimum` is 0 and the default value of `Maximum` is 100.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Minimum="-20"
                 Maximum="20"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = -20;
sfSlider.Maximum = 20;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with minimum and maximum customization](images/basic-features/slider-min-max.png)

## Interval

Range slider elements like labels, ticks and divisors are rendered based on the `Interval`, `Minimum` and `Maximum` properties. The default value of `Interval` is double.NaN.

For example, if `Minimum` is 0 and `Maximum` is 10 and `Interval` is 2, the slider will render the labels, major ticks, and divisors at 0, 2, 4 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with interval customization](images/basic-features/slider-interval.png)

N> Slider having auto interval support. So, the auto interval calculated by default.

N>
* Refer the `ShowDivisors` to know about the rendering of divisors at given interval.
* Refer the `ShowTicks` to know about the rendering of major ticks at given interval.
* Refer the `ShowLabels` to know about the rendering of labels at given interval.

## Discrete Selection for Values

You can move the thumb in discrete manner for numeric values using the `StepFrequency` property in the range slider.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      StepFrequency="2"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.StepFrequency = 2;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with step frequency](images/basic-features/slider-stepFrequency.gif)

## Value

You can show value in the slider by setting double value to the `Value` properties.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Setting value to slider](images/basic-features/slider-value.png)

## Flow Direction Customization

The direction of slider can be customized by its `IsInversed` property.

When the `IsInversed` property is true, the slider can be placed in right-to-left direction. When the `IsInversed` property is set to false, the slider will be positioned in left-to-right direction.

{% tabs %}

{% highlight xml %}

<slider:SfSlider ShowTicks="True"
                 ShowLabels="True"
                 Interval="20"
                 Value="40"
                 IsInversed="True"/>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
sfSlider.Interval = 20;
sfSlider.Value = 40;
sfSlider.IsInversed = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with is inversed customization](images/basic-features/slider-isInversed.png)

## Events

**ValueChanged**

The `ValueChanged` event occurs each time a `Value` property get changed. You can get the following values in this event args:

* `OldValue` – Gets the previous value of a range value property.
* `NewValue` – Gets the new value of a range value property.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 ValueChanged="SfSlider_ValueChanged" />

{% endhighlight %}

{% highlight c# %}

private void SfSlider_ValueChanged(object sender, SliderValueChangedEventArgs e)
{
    var oldValue = e.OldValue;
    var newValue = e.NewValue;
}

{% endhighlight %}

{% endtabs %}