---
layout: post
title: Shimmer Wave Directions in WinUI Shimmer Control | Syncfusion
description: Learn about the animation wave directions available in the Syncfusion WinUI Shimmer(SfShimmer) control, including Default, Left-to-right, Right-to-left, Top-to-bottom, and Bottom-to-top.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Shimmer Wave Directions in WinUI Shimmer Control

The animation wave direction is an important aspect of the Syncfusion WinUI Shimmer control's visual effects. It defines how the shimmering animation moves within the control. The SfShimmer control provides five different wave directions, allowing you to create various loading animations. Below are the available wave directions:

## Default

The default wave direction allows the animation to flow from the top-left corner to the bottom-right corner.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="Default" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.Default;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/CustomView_images/winui_shimmer_default.gif)

## Left-to-right

The default wave direction allows the animation to flow from the top-left corner to the bottom-right corner.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="LeftToRight" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.Default;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/CustomView_images/winui_shimmer_lefttoright.gif)

## Right-to-left

The right-to-left wave direction animates the shimmer effect from the right side to the left side.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="RightToLeft" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.RightToLeft;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/CustomView_images/winui_shimmer_righttoleft.gif)

## Top-to-bottom

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="TopToBottom" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.TopToBottom;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/CustomView_images/winui_shimmer_toptobottom.gif)
## Bottom-to-top

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="BottomToTop" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.BottomToTop;

![WinUI Shimmmer control with custom Fill](SfShimmer_images/CustomView_images/winui_shimmer_bottomtotop.gif)
