---
layout: post
title: Basic features of Syncfusion WinUI Range Slider
description: This article describes about the basic featue set of the Syncfusion range slider control in WinUi platform.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Basic features of Range slider

This section explains about how to add the WinUI slider with basic features.

## Setting minimum and maximum value

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

## values

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

## Flow direction customization

The direction of range slider can be customized by its `IsInversed` property.

When the IsInversed property is true, the range slider can be placed in right-to-left direction. When the IsInversed property is set to false, the range slider will be positioned in left-to-right direction.

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
sfRangeSlider.RangeEnd = 40;
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