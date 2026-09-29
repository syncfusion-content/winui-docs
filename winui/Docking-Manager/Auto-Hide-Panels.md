---
layout: post
title: Auto-Hide Panels in WinUI DockingManager Control | Syncfusion®
description: Learn how to configure auto-hide panels and maximize workspace utilization in the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Auto-Hide Panels in WinUI DockingManager

The DockingManager control allows panes to be automatically hidden when they are not in use. Auto-hidden panes remain accessible through edge tabs and can be displayed temporarily when selected.

This behavior helps maximize the available workspace while keeping important tool windows easily accessible.

## Auto-Hide a Pane

A pane can be displayed as an auto-hidden window by setting its `DockState` property to `AutoHidden`.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="AutoHidden">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane toolBoxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.AutoHidden,
    Content = new TextBlock()
    {
        Text = "Toolbox Content"
    }
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

dockingManager.Panes.Add(toolBoxPane);
dockingManager.Panes.Add(documentPane);

{% endhighlight %}
{% endtabs %}

## Display an Auto-Hidden Pane

When a pane is auto-hidden, it is displayed as a tab along the edge of the docking layout. Selecting the tab temporarily expands the pane and displays its content. When the pane loses focus, it automatically collapses back to its hidden state.

