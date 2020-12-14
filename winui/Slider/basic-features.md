---
layout: post
title: Basic features of Syncfusion WinUI Slider
description: This section explains about the basic featues of the WinUI slider.
platform: WinUI
control: SfSlider
documentation: ug
---

# Basic features of slider

This section explains about how to add the WinUI slider with basic features.

## Setting axis minimum and maximum value

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

## value

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

## Flow direction customization

The direction of slider can be customized by its `IsInversed` property.

When the IsInversed property is true, the slider can be placed in right-to-left direction. When the IsInversed property is set to false, the slider will be positioned in left-to-right direction.

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