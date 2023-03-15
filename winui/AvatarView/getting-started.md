---
layout: post
title: Getting Started with WinUI AvatarView control | Syncfusion
description: Learn here all about getting started with the Syncfusion WinUI AvatarView (SfAvatarView) control with its basic features.
platform: WinUI
control: AvatarView
documentation: ug
---

# Getting Started with WinUI AvatarView

This section explains the steps required to add the WinUI AvatarView control with its basic features.

## Creating an application with WinUI AvatarView

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in XAML or C# code.
4. Initialize the `SfAvatarView` control.

## Initialize AvatarView 

When AvatarView is initialized without the initials, custom image and group view, the default avatar character is displayed.

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

You can add a custom image to display in WinUI AvatarView using the `ImageSource` property.

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

![WinUI AvatarView control with image](avatarview_images/winui_imagesource_avatarview.png)