---
layout: post
title: Customization in WinUI Shimmer control | Syncfusion
description: Learn how to customize the appearance of the Syncfusion WinUI Shimmer(SfShimmer) control using various properties like Fill, Wave Color, Wave Width, Repeat Count and Wave Duration.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Customization in WinUI Shimmer

This section explains how to customize the appearance of the Syncfusion WinUI Shimmer (SfShimmer) control using various properties. You can modify the following aspects of the Shimmer effect:

## Fill

The `Fill` property allows you to set the background color of the Shimmer view.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer Fill="Blue" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.Fill = new SolidColorBrush(Colors.Blue);

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Customization_images/winui_shimmer_fill.gif)

## Wave Color

The `WaveColor` property lets you define the color of the shimmer wave.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveColor ="Blue" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveColor = new SolidColorBrush(Colors.Blue);

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Customization_images/winui_shimmer_wavecolor.gif)

## Wave Width

The `WaveWidth` property specifies the width of the shimmer wave.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveWidth="10" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveWidthy = 10;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Customization_images/winui_shimmer_wavewidth.gif)

## Repeat Count

The `RepeatCount` property sets the number of times the built-in view should be repeated.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer RepeatCount ="2" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.RepeatCount = 2;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Customization_images/winui_shimmer_repeatcount.gif)

<syncfusion:SfShimmer RepeatCount="2" />

## Wave Duration

The `WaveDuration` property determines the duration of the wave animation in milliseconds.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDuration="5000" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDuration =5000;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/Customization_images/winui_shimmer_waveduration.gif)



