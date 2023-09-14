---
layout: post
title: Getting started with WinUI Shimmer control | Syncfusion
description: Learn about getting started with the Syncfusion WinUI Shimmer(SfShimmer) control and its basic features here.
platform: WinUI
control: Shimmer
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

![WinUI Shimmer control overview](Shimmer_images/winui_shimmer_getting_started.gif)

## Loading shimmer content

By disabling the `IsActive` property of `SfShimmer` , shimmer content is loaded.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer x:Name="shimmer"  IsActive ="false">
    <syncfusion:SfShimmer.Content>
            <TextBlock Text="Content is loaded!"/>
    </syncfusion:SfShimmer.Content>
</syncfusion:SfShimmer>

{% endhighlight %} 
{% highlight C# %}

SfShimmer Shimmer= new SfShimmer()
{
    IsActive = false,
    Content = new TextBlock
    {
        Text = "Content is loaded!"
    }
};
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}