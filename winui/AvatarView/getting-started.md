---
layout: post
title: Getting Started with WinUI AvatarView control | Syncfusion
description: Learn all about getting started with the Syncfusion WinUI AvatarView (SfAvatarView) control, its elements, and more here.
platform: WinUI
control: AvatarView
documentation: ug
---

# Getting Started with WinUI AvatarView

This section explains the steps required to add the WinUI AvatarView control and covers only the basic features needed to get started with Syncfusion `AvatarView` control.

## Creating an application with WinUI AvatarView

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in XAML or C# code.
4. Initialize the `SfAvatarView` control.

## Initialize AvatarView 

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Core"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid>
      <syncfusion:SfAvatarView AvatarSize="ExtraLarge" />
    </Grid>
</Page>

{% endhighlight %} 
{% highlight C# %}

// Creating an instance of the AvatarView control.
SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarSize = AvatarSize.ExtraLarge;

//Setting page content.
page.Content = avatarView;
           
{% endhighlight %}
{% endtabs %}

![AvatarView control](avatarview_images/winui_avatarview_initialise.png)

## Initialize AvatarView with ImageSource

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="CustomImage"
                         AvatarSize="ExtraLarge"
                         ImageSource="ellanaa.png"
                         BorderBrush="Black">
</syncfusion:SfAvatarView>

{% endhighlight %} 
{% highlight C# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.CustomImage;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.ImageSource = new BitmapImage(new Uri("ms-appx:///ellanaa.png"));
avatarView.BorderBrush = new SolidColorBrush(Colors.Black);
page.Content = avatarView;
           
{% endhighlight %}
{% endtabs %}

![AvatarView control with custom image](avatarview_images/winui_avatarview_initialiseimage.png)