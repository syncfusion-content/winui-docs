---
layout: post
title: Customization in WinUI BusyIndicator control | Syncfusion
description: Learn all about the customization features such as size factor, duration factor, and color in Syncfusion WinUI BusyIndicator (SfBusyIndicator) control here.
platform: WinUI
control: SfBusyIndicator
documentation: ug
---

# Customization in WinUI BusyIndicator

This section explains the customization features available in the WinUI `BusyIndicator` control.

## Size

The indicator size can be customized by using the [SizeFactor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_SizeFactor) property. Its default value is 0.5 and ranges from 0 to 1.

{% tabs %}
{% highlight XAML %}

<notification:SfBusyIndicator IsActive="True"
    AnimationType="DottedCircularFluent"
    SizeFactor="0.2">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircularFluent;
busyIndicator.SizeFactor = 0.2;

{% endhighlight %}
{% endtabs %}

![WinUI BusyIndicator control with SizeFactor](BusyIndicator_images/winui_busyindicator_size.gif)

## Duration

The indicator animation speed can be customized by using the [DurationFactor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_DurationFactor) property. Its default value is 0.5 and ranges from 0 to 1.

{% tabs %}
{% highlight XAML %}

<notification:SfBusyIndicator IsActive="True"
    AnimationType="DottedCircularFluent"
    DurationFactor="0.9">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircularFluent;
busyIndicator.DurationFactor = 0.9;

{% endhighlight %}
{% endtabs %}

![WinUI BusyIndicator control with DurationFactor](BusyIndicator_images/winui_busyindicator_duration.gif)

## Color

The indicator color can be customized by using the [Color](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_Color) property.

{% tabs %}
{% highlight XAML %}

<notification:SfBusyIndicator IsActive="True"
    AnimationType="DottedCircle"
    Color="Red">
</notification:SfBusyIndicator>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.Color = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![WinUI BusyIndicator control with Color](BusyIndicator_images/winui_busyindicator_color.jpg)
