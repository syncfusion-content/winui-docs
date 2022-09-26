---
layout: post
title: Customization in WinUI BusyIndicator control | Syncfusion
description: Learn here all about the customization features such as size factor, duration factor, and color in Syncfusion WinUI BusyIndicator (SfBusyIndicator) control.
platform: WinUI
control: SfBusyIndicator
documentation: ug
---

# Customization in WinUI BusyIndicator

This section explains the customization features available in the WinUI `BusyIndicator` control.

## Size

The BusyIndicator size can be customized using the factor values 0 to 1.

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

![WinUI BusyIndicator control with SizeFactor](BusyIndicator_videos/winui_busyindicator_size.gif)

## Duration

The WinUI BusyIndicator animation speed can be customized using factor values 0 to 1.

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
busyIndicator.SizeFactor = 0.9;

{% endhighlight %}
{% endtabs %}

![WinUI BusyIndicator control with DurationFactor](BusyIndicator_videos/winui_busyindicator_duration.gif)

## Color

The BusyIndicator color can be customized based on the requirement.

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

![WinUI BusyIndicator control with Color](BusyIndicator_videos/winui_busyindicator_color.jpg)