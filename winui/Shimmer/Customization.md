---
layout: post
title: Customization in WinUI Shimmer control | Syncfusion
description: Learn how to customize the appearance of the Syncfusion WinUI Shimmer(SfShimmer) control using various properties like Fill, Wave Color, Wave Width, Repeat Count and Wave Duration.
platform: WinUI
control: Shimmer
documentation: ug
---

# Customization in WinUI Shimmer

This section explains how to customize the appearance of the Syncfusion WinUI Shimmer (SfShimmer) control using various properties. You can modify the following aspects of the Shimmer effect:

## Fill

The `Fill` property allows you to set the background color of the Shimmer view.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer Fill="#89CFF0" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.Fill = Color.FromRgba("#89CFF0");
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}

![Fill customization in WinUI Shimmer](Shimmer_images/winui_shimmer_fill.gif)

## Wave Color

The `WaveColor` property lets you define the color of the shimmer wave.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveColor ="#89CFF0" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveColor = Color.FromRgba("#89CFF0");
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}

![WaveColor customization in WinUI Shimmer](Shimmer_images/winui_shimmer_wavecolor.gif)

## Wave Duration

The `WaveDuration` property determines the duration of the wave animation in milliseconds.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDuration="3000" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDuration =3000;
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}

![WaveDuration customization in WinUI Shimmer](Shimmer_images/winui_shimmer_waveduration.gif)

## Wave Width

The `WaveWidth` property specifies the width of the shimmer wave.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveWidth="70" 
                      WaveColor="#89CFF0"/>

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveWidth = 70;
Shimmer.WaveColor = Color.FromRgba("#89CFF0");
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}

![WaveWidth customization in WinUI Shimmer](Shimmer_images/winui_shimmer_wavewidth.gif)

## Repeat Count

The `RepeatCount` property sets the number of times the built-in view should be repeated.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer RepeatCount ="3" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.RepeatCount = 3;
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}

![RepeatCount customization in WinUI Shimmer](Shimmer_images/winui_shimmer_repeatcount.gif)