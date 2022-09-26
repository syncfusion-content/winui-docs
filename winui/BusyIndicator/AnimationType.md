---
layout: post
title: AnimationType in WinUI BusyIndicator control | Syncfusion
description: Learn here all about different animation types available in the Syncfusion WinUI BusyIndicator control.
platform: WinUI
control: SfBusyIndicator
documentation: ug
---

# AnimationType in WinUI BusyIndicator

The `AnimationType` property for the SfBusyIndicator control allows the users to set one of the animations from the built-in animations. The different types of animations are `DottedCircularFluent`, `DottedCircle`, `DottedLinear`, `DoubleCircle`, `LinearBox`, `LinearOscillatingBox`, `SingleCircle`.

{% tabs %}
{% highlight XAML %}

<notification:SfBusyIndicator IsActive="True"
    AnimationType="DottedCircle"
    BusyContent="Loading">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();
busyIndicator.IsActive = true;
busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircle;
busyIndicator.Content = "Loading";

{% endhighlight %}
{% endtabs %}

The following gif image contains the types of animation in BusyIndicator.

![WinUI BusyIndicator control with AnimationTypes](BusyIndicator_videos/winui_busyindicator_animationtypes.gif)

