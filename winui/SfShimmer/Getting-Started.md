---
layout: post
title: Getting started with WinUI Shimmer control | Syncfusion
description: Learn about getting started with the Syncfusion WinUI Shimmer(SfShimmer) control and its basic features here.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Getting Started with WinUI Shimmer

This section explains the steps required to add the WinUI Shimmer control and covers only the basic features needed to get started with the Syncfusion Shimmer control.

## Creating an application with WinUI Shimmer control

1. Create a [WinUI 3 desktop app for C# and .NET 6](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in XAML or C# code.
4. Initialize the [SfShimmer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfShimmer.html) control.

## Initializing Shimmer control 

To initialize the Shimmer control, you can simply add the `SfShimmer` control in your XAML or C# code.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Core"
    mc:Ignorable="d">
    <Grid>
        <syncfusion:SfShimmer />
    </Grid>
</Window>

{% endhighlight %} 
{% highlight C# %}

// Creating an instance of the Shimmer control.
SfShimmer Shimmer = new SfShimmer();
           
{% endhighlight %}
{% endtabs %}

![WinUI Shimmer control overview](SfShimmer_images/GettingStarted_images/winui_shimmer_getting_started.gif)

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

![WinUI Shimmmer control with DefaultView](SfShimmer_images/GettingStarted_images/winui_shimmer_default.gif)

## Left-to-right

The default wave direction allows the animation to flow from the top-left corner to the bottom-right corner.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="LeftToRight" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.LeftToRight;

![WinUI Shimmmer control with LeftToRight View](SfShimmer_images/GettingStarted_images/winui_shimmer_lefttoright.gif)

## Right-to-left

The right-to-left wave direction animates the shimmer effect from the right side to the left side.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="RightToLeft" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.RightToLeft;

![WinUI Shimmmer control with RightToLeftView](SfShimmer_images/GettingStarted_images/winui_shimmer_righttoleft.gif)

## Top-to-bottom

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="TopToBottom" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.TopToBottom;

![WinUI Shimmmer control with TopToBottomView](SfShimmer_images/GettingStarted_images/winui_shimmer_toptobottom.gif)
## Bottom-to-top

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer WaveDirection="BottomToTop" />

{% endhighlight %}
{% highlight c# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.WaveDirection = ShimmerWaveDirection.BottomToTop;

![WinUI Shimmmer control with TopToBottomView](SfShimmer_images/GettingStarted_images/winui_shimmer_bottomtotop.gif)
