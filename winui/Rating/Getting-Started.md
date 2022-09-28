---
layout: post
title: Getting started with WinUI Rating control | Syncfusion
description: Learn here all about getting started with the Syncfusion WinUI Rating(SfRating) control and its basic features.
platform: WinUI
control: SfRating
documentation: ug
---

# Getting Started with WinUI Rating

This section explains the steps required to add the WinUI Rating control and covers only the basic features needed to get started with Syncfusion `Rating` control.

## Creating an application with WinUI Rating control

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the SfRating control.

## Initialize Rating control using Items

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid>
     <syncfusion:SfRating Value="3">
         <syncfusion:SfRating.Items>
            <syncfusion:SfRatingItem Content="1"/>
            <syncfusion:SfRatingItem Content="2"/>
            <syncfusion:SfRatingItem Content="3"/>
            <syncfusion:SfRatingItem Content="4"/>
            <syncfusion:SfRatingItem Content="5"/>
         </syncfusion:SfRating.Items>
     </syncfusion:SfRating>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

// Creating an instance of the Rating control.
SfRating rating = new SfRating();

//Adding items to the Rating control.
rating.Items.Add(new SfRatingItem() { Content = "1"});
rating.Items.Add(new SfRatingItem() { Content = "2"});
rating.Items.Add(new SfRatingItem() { Content = "3"});
rating.Items.Add(new SfRatingItem() { Content = "4"});
rating.Items.Add(new SfRatingItem() { Content = "5"});

//Setting rating value.
rating.Value = 3;
           
{% endhighlight %}
{% endtabs %}

![Rating control using items in WinUI](Rating_images/winui_rating_items.png)

## Initialize Rating control using ItemsCount

{% tabs %}
{% highlight xaml %}

<syncfusion:SfRating Value="3" ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![Rating control using itemscount in WinUI](Rating_images/winui_rating_itemscount.png)

