---
layout: post
title: Getting Started with WinUI Dock Layout Control | Syncfusion®
description: Learn how to get started with the Syncfusion® WinUI Dock Layout control and create Visual Studio-style docking interfaces in WinUI applications.
platform: winui
control: DockLayout
documentation: ug
---

# Getting Started with WinUI Dock Layout Control

This section explains how to create a WinUI application with the Dock Layout control and add docked and document windows.

## Creating an application with WinUI Dock Layout

1. Create a WinUI 3 desktop application using C# and .NET 8 or later.

2. Add a reference to the `Syncfusion.DockingManager.WinUI` NuGet package.

3. Import the control namespace `Syncfusion.UI.Xaml.Docking` in XAML or C# code.

4. Initialize the `SfDockingManager` control.

{% capture codesnippet1 %}
{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:docking="using:Syncfusion.UI.Xaml.Docking">

    <Grid>
        <docking:SfDockingManager x:Name="dockingManager"/>
    </Grid>

</Window>

{% endhighlight %}
{% highlight c# %}

using Syncfusion.UI.Xaml.Docking;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();

        SfDockingManager dockingManager = new SfDockingManager();
        Content = dockingManager;
    }
}

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Add dock panes

The `DockPane` is the basic element of the Dock Layout control. It hosts content and can be displayed in different docking states.

The following example demonstrates how to add docked and document panes.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="Docked">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockDirection="Right"
                          DockState="Docked">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox AcceptsReturn="True"
                     Text="Main document editor..."/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}
{% endtabs %}



## Dock states

The Dock Layout control supports the following docking states:

* **Docked** - Displays a pane in one of the dock regions.
* **Document** - Displays a pane in the document area.
* **Floating** - Displays a pane in a separate floating window.
* **AutoHidden** - Hides a pane until it is activated.
* **Tabbed** - Groups panes within a tabbed layout.

## Add a floating window

A pane can be displayed in a floating window by setting its `DockState` to `Floating`.

{% tabs %}
{% highlight xaml %}

<docking:DockPane Header="Properties"
                  DockState="Floating">
    <TextBlock Text="Properties Window"/>
</docking:DockPane>

{% endhighlight %}
{% endtabs %}



## Create tab groups and documents

The Dock Layout control allows multiple document and tool windows to be grouped as tabs.

{% tabs %}
{% highlight xaml %}

<docking:DockPane x:Name="OutputPane"
                  Header="Output"
                  DockDirection="Bottom"
                  DockState="Docked">
    <TextBlock Text="Output Content"/>
</docking:DockPane>

<docking:DockPane Header="Error List"
                  DockDirection="Bottom"
                  DockState="Tabbed"
                  TargetNameInTabbedState="OutputPane">
    <TextBlock Text="Error List Content"/>
</docking:DockPane>

{% endhighlight %}
{% endtabs %}