---
layout: post
title: Customization in WinUI Busy Indicator | Syncfusion®
description: Customization in WinUI Busy Indicator enables configuring size factor, duration factor, color, and animation settings to create tailored loading indicators.
platform: WinUI
control: Busy Indicator
documentation: ug
---

# Customization in WinUI Busy Indicator

This section explains the customization features available in the WinUI Busy Indicator control.

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

![WinUI Busy Indicator control with SizeFactor](BusyIndicator_images/winui_busyindicator_size.gif)

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

![WinUI Busy Indicator control with DurationFactor](BusyIndicator_images/winui_busyindicator_duration.gif)

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

![WinUI Busy Indicator control with Color](BusyIndicator_images/winui_busyindicator_color.jpg)
