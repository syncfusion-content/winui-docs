---
layout: post
title: Interval in Syncfusion WinUI Slider
description: This section explains about how to add intervals for Syncfusion WinUI Slider.
platform: WinUI
control: SfSlider
documentation: ug
---

## Interval

Slider elements like labels, ticks and divisors are rendered based on the `Interval`, `Minimum` and `Maximum` properties. The default value of `Interval` is 0.

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

![Slider with interval customization](images/interval/slider-interval.png)

N> Slider having auto interval support. So, the auto interval calculated by default.

N>
* Refer the `ShowDivisors` to know about the rendering of divisors at given interval.
* Refer the `ShowTicks` to know about the rendering of major ticks at given interval.
* Refer the `ShowLabels` to know about the rendering of labels at given interval.

## Discrete selection for values

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

![Slider with step frequency](images/interval/slider-stepFrequency.gif)