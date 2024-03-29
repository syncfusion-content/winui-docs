---
layout: post
title: Getting Started with WinUI AvatarView control | Syncfusion
description: Learn about getting started with the Syncfusion WinUI AvatarView (SfAvatarView) control with its basic features.
platform: WinUI
control: AvatarView
documentation: ug
---

# Getting Started with WinUI AvatarView

This section explains the steps required to add the WinUI [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control with its basic features.

## Creating an application with WinUI AvatarView

1. Create a [WinUI 3 desktop app for C# and .NET 6](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in XAML or C# code.
4. Initialize the [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control.

## Initialize AvatarView 

By default, AvatarView control is displayed with the [Avatar1](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarCharacter.html#Syncfusion_UI_Xaml_Core_AvatarCharacter_Avatar1) character image, AvatarShape of [Circle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarShape.html#Syncfusion_UI_Xaml_Core_AvatarShape_Circle), and AvatarSize of [Small](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarSize.html#Syncfusion_UI_Xaml_Core_AvatarSize_Small).

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
      <syncfusion:SfAvatarView />
    </Grid>
</Page>

{% endhighlight %} 
{% highlight C# %}

// Creating an instance of the AvatarView control.
SfAvatarView avatarView = new SfAvatarView();
           
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control](avatarview_images/winui_avatarview.png)

## Initialize AvatarView with ImageSource

Add any custom image as an avatar in WinUI AvatarView control using the [ImageSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_ImageSource) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="CustomImage"
                         AvatarSize="ExtraLarge"
                         ImageSource="Images\person.png">
</syncfusion:SfAvatarView>

{% endhighlight %} 
{% highlight C# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.CustomImage;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.ImageSource = new BitmapImage(new Uri("ms-appx:///Images\\person.png"));
           
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom image](avatarview_images/winui_imagesource_avatarview.png)
