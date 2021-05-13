---
layout: post
title: Track in WinUI RangeSlider control | Syncfusion
description: Learn here all about Track feature of Syncfusion WinUI RangeSlider(sfRangeSlider) control with color, hover and more.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Track in WinUI RangeSlider (Range Slider)

This section explains how to customize the track in the slider.

## Track Color

You can change the active and inactive track color of the range slider using the [`ActiveTrackFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveTrackFill) and [`InactiveTrackFill`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_InactiveTrackFill) properties respectively.

The active side of the range slider is between start and end thumbs.

The InactiveTrack of the RangeSlider visible between the [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) value and StartThumb, also between the EndThumb and [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) value.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ActiveTrackFill="#009688"
                      InactiveTrackFill="#C2E6E3" />
      
{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 0, 150, 136));
sfRangeSlider.InactiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 194, 230, 227));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Active and Inactive Track Color of WinUI RangeSlider](images/track/winui-range-slider-active-inactive-color.png)

## Track Hover Color

You can change the active and inactive track hover color of the range slider using the `SyncfusionSliderActiveTrackFillPointerOver` and `SyncfusionSliderInactiveTrackFillPointerOver` resource keys respectively. This color will be applied when hovering the cursor on the RangeSlider control.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <SolidColorBrush x:Key="SyncfusionSliderActiveTrackFillPointerOver">#009688</SolidColorBrush>
    <SolidColorBrush x:Key="SyncfusionSliderInactiveTrackFillPointerOver">#C2E6E3</SolidColorBrush>
</Page.Resources>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ActiveTrackFill="#009688"
                      InactiveTrackFill="#C2E6E3" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 0, 150, 136));
sfRangeSlider.InactiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 194, 230, 227));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Active and Inactive Track Hover Color of WinUI RangeSlider](images/track/winui-slider-active-inactive-hover-color.png)

## Track Pressed Color

You can change the active and inactive track pressed color of the range slider using the`SyncfusionSliderActiveTrackFillPressed` and `SyncfusionSliderInactiveTrackFillPressed` resource keys respectively. This color will be applied when pressed the cursor on the range slider control.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <SolidColorBrush x:Key="SyncfusionSliderActiveTrackFillPointerOver">#009688</SolidColorBrush>
    <SolidColorBrush x:Key="SyncfusionSliderInactiveTrackFillPointerOver">#C2E6E3</SolidColorBrush>
    
    <SolidColorBrush x:Key="SyncfusionSliderActiveTrackFillPressed">#018A7D</SolidColorBrush>
    <SolidColorBrush x:Key="SyncfusionSliderInactiveTrackFillPressed">#98B8B5</SolidColorBrush>
</Page.Resources>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ActiveTrackFill="#009688"
                      InactiveTrackFill="#C2E6E3"  />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 0, 150, 136));
sfRangeSlider.InactiveTrackFill = new SolidColorBrush(ColorHelper.FromArgb(255, 194, 230, 227));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Active and Inactive Track Pressed Color of WinUI RangeSlider](images/track/winui-range-slider-active-inactive-pressed-color.png)

## Track Height

You can change the track height of the range slider using the [`ActiveTrackHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveTrackHeight) and [`InactiveTrackHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_InactiveTrackHeight) properties. The default value of the both properties are 2.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ActiveTrackHeight="8"
                      InactiveTrackHeight="8"  />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveTrackHeight = 8;
sfRangeSlider.InactiveTrackHeight = 8;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Active and Inactive Track Height of WinUI RangeSlider](images/track/winui-range-slider-active-inactive-track-height.png)

## Track Style

You can change the track style of the range slider using the [`ActiveTrackStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveTrackStyle) and [`InactiveTrackStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_InactiveTrackStyle) properties. The default value of the both properties are null.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <Style x:Key="ActiveTrackStyle"
            TargetType="Rectangle">
        <Setter Property="RadiusX"
                Value="4" />
        <Setter Property="RadiusY"
                Value="4" />
    </Style>

    <Style x:Key="InactiveTrackStyle"
            TargetType="Rectangle">
        <Setter Property="RadiusX"
                Value="3" />
        <Setter Property="RadiusY"
                Value="3" />
    </Style>
</Page.Resources>
    
<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ActiveTrackHeight="8"
                      InactiveTrackHeight="6"
                      ActiveTrackStyle="{StaticResource ActiveTrackStyle}"
                      InactiveTrackStyle="{StaticResource InactiveTrackStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveTrackHeight = 8;
sfRangeSlider.InactiveTrackHeight = 6;
sfRangeSlider.ActiveTrackStyle = this.Resources["ActiveTrackStyle"] as Style;
sfRangeSlider.InactiveTrackStyle = this.Resources["InactiveTrackStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Active and Inactive Track Style of WinUI RangeSlider](images/track/winui-range-slider-active-inactive-track-style.png)
