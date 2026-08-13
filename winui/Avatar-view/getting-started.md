---
layout: post
title: Getting Started with WinUI AvatarView | Syncfusion®
description: Learn how to get started with the Syncfusion® WinUI AvatarView control. Explore setup, features, examples, and customization options.
platform: WinUI
control: AvatarView
documentation: ug
---

# Getting Started with WinUI AvatarView

This section explains the steps required to add the WinUI [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control and configure its basic features.

## Creating an application with WinUI AvatarView

1. Create a [WinUI 3 desktop app for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add a reference to the [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet package.
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in your XAML or C# code.
4. Initialize the [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control with the required settings.

## Initialize AvatarView

By default, the AvatarView control is displayed with the [Avatar1](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarCharacter.html#Syncfusion_UI_Xaml_Core_AvatarCharacter_Avatar1) character image, an `AvatarShape` of [Circle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarShape.html#Syncfusion_UI_Xaml_Core_AvatarShape_Circle), and an `AvatarSize` of [Small](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarSize.html#Syncfusion_UI_Xaml_Core_AvatarSize_Small).

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
    mc:Ignorable="d"
    Title="AvatarView Getting Started">
    <Grid>
      <syncfusion:SfAvatarView />
    </Grid>
</Window>

{% endhighlight %} 
{% highlight C# %}

using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Core;

namespace GettingStarted;

/// <summary>
/// A window that hosts the default WinUI AvatarView (SfAvatarView) control.
/// </summary>
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();

        // Creating an instance of the AvatarView control.
        SfAvatarView avatarView = new SfAvatarView();
        this.Content = avatarView;
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control](avatarview_images/winui_avatarview.png)

## Initialize AvatarView with ImageSource

Add a custom image as an avatar in the WinUI AvatarView control by using the [ImageSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_ImageSource) property.

> **Note:** When you add a new image to the project, select the image file in **Solution Explorer**, open the **Properties** window, and set:
> - **Build Action** = `Content`
> - **Copy to Output Directory** = `Copy if newer`

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
    mc:Ignorable="d"
    Title="AvatarView with ImageSource">
    <Grid>
        <syncfusion:SfAvatarView ContentType="CustomImage"
                                 AvatarSize="ExtraLarge"
                                 ImageSource="ms-appx:///Assets/Images/person.png">
        </syncfusion:SfAvatarView>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %}

using Microsoft.UI.Xaml;
using Microsoft.UI.Xaml.Media.Imaging;
using Syncfusion.UI.Xaml.Core;

namespace GettingStarted;

/// <summary>
/// A window that hosts the WinUI AvatarView (SfAvatarView) control with a custom image source.
/// </summary>
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();

        // Creating an instance of the AvatarView control with a custom image.
        SfAvatarView avatarView = new SfAvatarView();
        avatarView.ContentType = AvatarContentType.CustomImage;
        avatarView.AvatarSize = AvatarSize.ExtraLarge;
        avatarView.ImageSource = new BitmapImage(new Uri("ms-appx:///Assets/Images/person.png"));
        this.Content = avatarView;
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom image](avatarview_images/winui_imagesource_avatarview.png)
