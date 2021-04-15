---
layout: post
title: Getting Started with Syncfusion WinUI Range Slider
description: A guide to initial users about Syncfusion RangeSlider control in the WinUI platform. It provide an overview of SfRangeSlider. 
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Getting Started with WinUI Range Slider (SfRangeSlider)

This section explains the steps required to add the [WinUI RangeSlider](https://www.syncfusion.com/winui-controls/range-slider) control and its elements such as values, ticks, divisors, labels, and tooltip. This section covers only basic features needed to get started with Syncfusion RangeSlider.

## Creating an application with WinUI Range Slider

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).

2. Add reference to [Syncfusion.Sliders.WinUI](https://www.nuget.org/packages/Syncfusion.Sliders.WinUI) NuGet.

3. Import the control namespace `Syncfusion.UI.Xaml.Sliders` in XAML or C# code.

4. Initialize the [`SfRangeSlider`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html?tabs=tabid-1) control

The default value of the [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) and [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) properties of the [`SfRangeSlider`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html?tabs=tabid-1) is 0 and 100 respectively. So, the [`RangeStart`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_RangeStart) and [`RangeEnd`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_RangeEnd) properties must be given within the range.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

## Set Values

You can show values in the range slider by setting double values to the [`RangeStart`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_RangeStart) and [`RangeEnd`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_RangeEnd) properties.

{% tabs %}

{% highlight xaml %}

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

## Enable Ticks

You can enable ticks in the range slider using the [`ShowTicks`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowTicks) property.

{% tabs %}

{% highlight xaml %}

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

## Enable Labels

You can enable labels in the range slider using the [`ShowLabels`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowLabels) property.

{% tabs %}

{% highlight xaml %}

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

## Enable Divisors

You can enable divisors in the range slider using the [`ShowDivisors`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDivisors) property.

{% tabs %}

{% highlight xaml %}

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

N> Download demo application from the [GitHub](https://github.com/SyncfusionExamples/WinUI_Sliders_Getting_Started/tree/main/RangeSlider)