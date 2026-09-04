---
layout: post
title: Getting Started with WinUI Busy Indicator | Syncfusion®
description: Learn how to get started with the Syncfusion® WinUI Busy Indicator control. Explore setup, features, examples, and customization options.
platform: WinUI
control: Busy Indicator
documentation: ug
---

# Getting Started with WinUI Busy Indicator

This section explains how to add and configure the [Busy Indicator](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html) control in a WinUI application and demonstrates the basic features required to get started.

## Creating an application with WinUI Busy Indicator control

1. Create a [WinUI 3 desktop app for C#](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Install the [Syncfusion.Notifications.WinUI](https://www.nuget.org/packages/Syncfusion.Notifications.WinUI) NuGet package.
3. Import the `Syncfusion.UI.Xaml.Notifications` namespace in XAML or C#.
4. Create and initialize the [Busy Indicator](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html) control and add it to the window. Set [`IsActive`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_IsActive) to `true` to display the indicator.

{% capture codesnippet1 %}
{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:notification="using:Syncfusion.UI.Xaml.Notifications"
    mc:Ignorable="d">
    <Grid>
      <notification:SfBusyIndicator IsActive="True"/>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %}

using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Notifications;

namespace GettingStarted;

/// <summary>
/// An empty window that can be used on its own or navigated to within a Frame.
/// </summary>
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfBusyIndicator busyIndicator = new SfBusyIndicator();
        busyIndicator.IsActive = true;
        this.Content = busyIndicator;
    }
}

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Setting the animation type in Busy Indicator

The Busy Indicator control provides eight predefined animation types, such as `DottedCircle`, `DottedCircularFluent`, `DottedLinear`, `LinearIndicator`, `Pulse`, `Ripple`, `SingleCircle`, and `Slices`. You can choose any of the predefined animation types by setting the [AnimationType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_AnimationType) property. The default value is `DottedCircle`.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:notification="using:Syncfusion.UI.Xaml.Notifications"
    mc:Ignorable="d">
    <Grid>
      <notification:SfBusyIndicator IsActive="True"
           AnimationType="DottedLinear">
      </notification:SfBusyIndicator>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %}

using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Notifications;

namespace GettingStarted;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfBusyIndicator busyIndicator = new SfBusyIndicator();
        busyIndicator.IsActive = true;
        busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedLinear;
        this.Content = busyIndicator;
    }
}

{% endhighlight %}
{% endtabs %}

## Displaying content in Busy Indicator

The Busy Indicator control provides an option to set the content that indicates the busy status of the control to the user, by using the [BusyContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBusyIndicator.html#Syncfusion_UI_Xaml_Notifications_SfBusyIndicator_BusyContent) property. The content is rendered alongside the animation while `IsActive` is `true`, and is hidden when `IsActive` is `false`.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:notification="using:Syncfusion.UI.Xaml.Notifications"
    mc:Ignorable="d">
    <Grid>
      <notification:SfBusyIndicator IsActive="True"
           AnimationType="DottedCircularFluent"
           BusyContent="Loading">
      </notification:SfBusyIndicator>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %}
using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Notifications;

namespace GettingStarted;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfBusyIndicator busyIndicator = new SfBusyIndicator();
        busyIndicator.IsActive = true;
        busyIndicator.AnimationType = BusyIndicatorAnimationType.DottedCircularFluent;
        busyIndicator.BusyContent = "Loading";
        this.Content = busyIndicator;
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI Busy Indicator control getting started](BusyIndicator_images/winui_busyindicator_getting_started.gif)
