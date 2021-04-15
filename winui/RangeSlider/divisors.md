---
layout: post
title: Divisors in WinUI RangeSlider control | Syncfusion
description: Learn here all about Divisors support in Syncfusion WinUI RangeSlider(SfRangeSlider) control and more.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Divisors in WinUI RangeSlider (Range Slider)

This section explains about how to show the divisors in the range slider.

## Show Divisors

The [`ShowDivisors`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDivisors) property is used to render the divisors on the track. The default value of the [`ShowDivisors`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDivisors) property is false. It is a shape, which is used to represent the major interval points of the track.

For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 100, and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 10, the slider will render the divisors at 0, 10, 20 and so on.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisors](images/divisors/slider-showDivisors.png)

## Divisors Height and Width

You can change the divisor height and width of the RangeSlider using the [`DivisorHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorHeight) and [`DivisorWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorWidth) properties respectively.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="4"
                      DivisorWidth="4" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 4;
sfRangeSlider.DivisorWidth = 4;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor height and width customization](images/divisors/slider-divisorHeightWidth.png)

## Divisor Stroke Thickness and Stroke

You can change the divisor stroke thickness of the range slider using the [`DivisorStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStrokeThickness) property. The default value of [`DivisorStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStrokeThickness) is 0. Also, you can change the divisor stroke of the range slider using the [`DivisorStroke`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStroke) property.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorStrokeThickness="2"
                      DivisorStroke="Red" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorStrokeThickness = 2;
sfRangeSlider.DivisorStroke = new SolidColorBrush(Colors.Red);
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor stroke customization](images/divisors/slider-divisorstroke.png)

## Divisor Fill

You can change the divisor fill of the range slider using the [`DivisorFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorFill) property.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorFill="#ff7979" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorFill = new SolidColorBrush(ColorHelper.FromArgb(255,255, 121, 121));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor fill customization](images/divisors/slider-divisorfill.png)

## Divisor Template

**Setting a Template for Divisors**

The [`DivisorTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorTemplate) property allows you to define the data template for the divisor's as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="DivisorTemplate">
    <Rectangle Height="{Binding DivisorHeight}"
               Width="{Binding DivisorWidth}"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColor}"
               StrokeThickness="{Binding DivisorStrokeThickness}" />
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorStrokeThickness="2"
                      DivisorTemplate="{StaticResource DivisorTemplate}">
</slider:SfRangeSlider>

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorStrokeThickness = 2;
sfRangeSlider.DivisorTemplate = this.Resources["DivisorTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor template customization](images/divisors/slider-divisorTemplate.png)

N> Its DataContext is [`SliderBase`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html?tabs=tabid-1).

**Setting a Active Template for Divisors**

The [`DivisorTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorTemplate) property allows you to define the data template for the divisor's as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="ActiveDivisorTemplate">
    <Rectangle Height="6"
               Width="6"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColor}"
               StrokeThickness="2" />
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="5"
                      DivisorWidth="5"
                      ActiveDivisorTemplate="{StaticResource ActiveDivisorTemplate}">
</slider:SfRangeSlider>

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 5;
sfRangeSlider.DivisorWidth = 5;
sfRangeSlider.ActiveDivisorTemplate = this.Resources["ActiveDivisorTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Slider with active divisor template customization](images/divisors/slider-activeDivisorTemplate.png)
