---
layout: post
title: Floating Windows in WinUI DockingManager Control | Syncfusion®
description: Learn how to create, reposition, and manage floating windows within the Syncfusion® WinUI DockingManager control layout.
platform: winui
control: DockingManager
documentation: ug
---

# Floating Windows in WinUI DockingManager

The DockingManager control allows panes to be displayed as floating windows. Floating windows can be moved independently within the DockingManager layout, providing greater flexibility for organizing content and customizing the workspace.

## Create a Floating Window

A pane can be displayed as a floating window by setting its `DockState` property to `Floating`.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane floatingPane = new DockPane()
{
    Header = "Solution Explorer",
    DockState = DockState.Floating,
    Content = new TextBlock()
    {
        Text = "Solution Explorer Content"
    }
};

dockingManager.Panes.Add(documentPane);
dockingManager.Panes.Add(floatingPane);

{% endhighlight %}
{% endtabs %}

## Floating Multiple Windows

The DockingManager control supports multiple floating windows within the same layout. Floating windows can be positioned independently and rearranged to suit different workspace requirements.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

        <docking:DockPane Header="Properties"
                          DockState="Floating">
            <TextBlock Text="Properties Window"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane solutionExplorerPane = new DockPane()
{
    Header = "Solution Explorer",
    DockState = DockState.Floating
};

DockPane propertiesPane = new DockPane()
{
    Header = "Properties",
    DockState = DockState.Floating
};

dockingManager.Panes.Add(documentPane);
dockingManager.Panes.Add(solutionExplorerPane);
dockingManager.Panes.Add(propertiesPane);

{% endhighlight %}
{% endtabs %}

## Reposition a Floating Window

Floating windows can be repositioned using drag-and-drop interactions. Users can move floating windows anywhere on the desktop and place them according to their workflow requirements.

When a floating window is dragged over the docking layout, docking targets are displayed, allowing the window to be docked back into the layout.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}
{% endtabs %}

