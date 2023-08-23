---
layout: post
title: Customization in WinUI Shimmer control | Syncfusion
description: Learn how to customize the appearance of the Syncfusion WinUI Shimmer(SfShimmer) control using various properties like Fill, Wave Color, Wave Width, Repeat Count, Wave Duration, and Wave Angle.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Customization in WinUI AvatarView

This section explains how to customize the appearance of the Syncfusion WinUI Shimmer (SfShimmer) control using various properties. You can modify the following aspects of the Shimmer effect:

## Fill

The `Fill` property allows you to set the background color of the Shimmer view.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer Fill="Red" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.Fill = new SolidColorBrush(Colors.Red);

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Gettting_Started/winui_shimmer_fill.gif)


## Wave Color

The `WaveColor` property lets you define the color of the shimmer wave.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveColor ="Blue" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.Fill = new SolidColorBrush(Colors.Blue);

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Gettting_Started/winui_shimmer_wavecolor.gif)

## Wave Width
The `WaveWidth` property specifies the width of the shimmer wave.


<syncfusion:SfShimmer WaveWidth="200" />

## Repeat Count
The `RepeatCount` property sets the number of times the built-in view should be repeated.


<syncfusion:SfShimmer RepeatCount="2" />

## Wave Duration
The `WaveDuration`` property determines the duration of the wave animation in milliseconds.


<syncfusion:SfShimmer WaveDuration="1500" />

## Wave Angle
The `WaveAngle` property allows you to adjust the angle of the shimmer wave.

<syncfusion:SfShimmer WaveAngle="15" />

## Applying Customization
To apply these customization properties and achieve the desired visual effects, use the following syntax:

```markdown
<syncfusion:SfShimmer
    Fill="LightGray"
    WaveColor="White"
    WaveWidth="200"
    RepeatCount="2"
    WaveDuration="1500"
    WaveAngle="15" />
For more detailed information about customizing the Syncfusion Shimmer control, refer to the Syncfusion Shimmer documentation.