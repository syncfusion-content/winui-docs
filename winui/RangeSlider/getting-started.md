---
layout: post
title: Getting Started for Syncfusion WinUI Range Slider
description: A quick tour to initial users about Syncfusion Range Slider control for the WinUI platform. It provide overview on SfRangeSlider. 
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Getting Started with WinUI Range Slider (SfRangeSlider)

This section explains the steps required to add the range slider control and its elements such as values, ticks, divisors, labels and tooltip. This section covers only basic features needed to know to get started with Syncfusion range slider.

## Creating an application with WinUI Range Slider

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.

2. Add reference to [Syncfusion.Sliders.WinUI](https://www.nuget.org/packages/Syncfusion.Sliders.WinUI) NuGet.

3. Import the control namespace `Syncfusion.UI.Xaml.Sliders` in XAML or C# code.

4. Initialize the SfRangeSlider control

The default value of the `Minimum` and `Maximum` properties of the `SfRangeSlider` is 0 and 100 respectively. So, the `RangeStart` and `RangeEnd` properties must be given within the range.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

## Set value

You can show values in the range slider by setting double value to the `RangeStart` and `RangeEnd` properties.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Setting values to range slider](images/getting-started/slider-value.png)

## Enable ticks

You can enable ticks in the range slider using the `ShowTicks` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowTicks="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowTicks = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/getting-started/slider-ticks.png)

## Enable labels

You can enable ticks in the range slider using the `ShowLabels` property.

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
SfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with labels](images/getting-started/slider-labels.png)

## Enable divisors

You can enable divisors in the range slider using the `ShowDivisors` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowDivisors="True"
                      DivisorHeight="4"
                      DivisorWidth="4"
                      ActiveTrackHeight="4"
                      InactiveTrackHeight="4" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 4;
sfRangeSlider.DivisorWidth = 4;
sfRangeSlider.ActiveTrackHeight = 4;
sfRangeSlider.InactiveTrackHeight = 4;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisors](images/getting-started/slider-divisors.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/WinUI_Radial_Gauge_Getting_Started)