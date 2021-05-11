---
layout: post
title: Divisors in WinUI Slider control | Syncfusion
description: Learn here all about Divisors feature of Syncfusion WinUI Slider(SfSlider) control with height, width support and more.
platform: WinUI
control: SfSlider
documentation: ug
---

# Divisors in WinUI Slider

This section explains about how to show the divisors in the slider.

## Show Divisors

The [`ShowDivisors`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDivisors) property is used to render the divisors on the track. The default value of the [`ShowDivisors`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowDivisors) property is false. It is a shape, which is used to represent the major interval points of the track.

For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 100, and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 10, the slider will render the divisors at 0, 10, 20 and so on.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider with Divisors](images/divisors/winui-slider-divisors.png)

## Divisors Height and Width

You can change the divisor height and width of the RangeSlider using the [`DivisorHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorHeight) and [`DivisorWidth`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorWidth) properties respectively.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="4"
                 DivisorWidth="4" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 4;
sfSlider.DivisorWidth = 4;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Changing Divisor Height and Width of WinUI Slider](images/divisors/winui-slider-divisor-height-width.png)

## Divisor Stroke Thickness and Stroke

You can change the divisor stroke thickness of the slider using the [`DivisorStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStrokeThickness) property. The default value of [`DivisorStrokeThickness`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStrokeThickness) is 0. Also, you can change the divisor stroke of the slider using the [`DivisorStroke`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorStroke) property.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorStrokeThickness="2"
                 DivisorStroke="Red" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorStrokeThickness = 2;
sfSlider.DivisorStroke = new SolidColorBrush(Colors.Red);
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Divisor Stroke Thickness of WinUI Slider](images/divisors/winui-slider-divisor-stroke-thickness.png)

## Divisor Fill

You can change the divisor fill of the slider using the [`DivisorFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_DivisorFill) property.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorFill="#ff7979" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorFill = new SolidColorBrush(ColorHelper.FromArgb(255,255, 121, 121));
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Changing Divisor Color of WinUI Slider](images/divisors/winui-slider-divisor-color.png)

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

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorStrokeThickness="2"
                 DivisorTemplate="{StaticResource DivisorTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorStrokeThickness = 2;
sfSlider.DivisorTemplate = this.Resources["DivisorTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider with Divisor Template](images/divisors/winui-slider-divisor-template.png)

N> Its DataContext is [`SliderBase`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html?tabs=tabid-1).

**SSetting a Active Template for Divisors**

The [`ActiveDivisorTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveDivisorTemplate) property allows you to define the data template for the divisor's as shown in the following code sample.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Key="ActiveDivisorTemplate">
    <Rectangle Height="6"
               Width="6"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColor}"
               StrokeThickness="2" />
</DataTemplate>

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="5"
                 DivisorWidth="5"
                 ActiveDivisorTemplate="{StaticResource ActiveDivisorTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 5;
sfSlider.DivisorWidth = 5;
sfSlider.ActiveDivisorTemplate = this.Resources["ActiveDivisorTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Active Divisor Template of WinUI Slider](images/divisors/winui-slider-active-divisor-template.png)
