---
layout: post
title: Pane Management in WinUI DockingManager Control | Syncfusion®
description: Learn how to add, remove, float, auto-hide, hide, restore, and activate panes programmatically in the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Pane Management in WinUI DockingManager

The DockingManager control provides properties and methods to manage panes at runtime. This page describes the active pane, the selected document, and the methods used to add, remove, and change the state of panes.

## Active pane and selected document

| Member | Description |
|--------|-------------|
| `ActivePane` | Gets the pane that currently has focus. This property is read-only. Use `ActivatePane` to change it. |
| `SelectedDocument` | Gets or sets the content displayed in the central document area. |

The `ActivePane` changes when the user clicks or focuses a pane, or when `ActivatePane` is called. The [ActivePaneChanged](Events.md) event is raised after every change.

{% tabs %}
{% highlight xaml %}

<docking:SfDockingManager x:Name="dockingManager">
    <docking:DockPane x:Name="ToolboxPane"
                      Header="Toolbox"
                      DockDirection="Left"
                      DockState="Docked">
        <TextBlock Text="Toolbox Content"/>
    </docking:DockPane>
</docking:SfDockingManager>

{% endhighlight %}

{% highlight c# %}

dockingManager.ActivatePane(ToolboxPane);

DockPane active = dockingManager.ActivePane;

dockingManager.SelectedDocument = new TextBox() { Text = "Document content" };

{% endhighlight %}
{% endtabs %}

## Add and remove panes

Use `AddPane` to add a pane to the DockingManager at runtime. The second parameter specifies the edge to dock the pane to. Passing `Dock.Center` adds the pane as a document.

Use `RemovePane` to remove a pane from the DockingManager. Nothing happens if the pane is not part of the DockingManager.

{% highlight c# %}

DockPane propertiesPane = new DockPane()
{
    Header = "Properties",
    Content = new TextBlock() { Text = "Properties Content" }
};

// Add the pane docked to the right edge.
dockingManager.AddPane(propertiesPane, Dock.Right);

// Remove the pane.
dockingManager.RemovePane(propertiesPane);

{% endhighlight %}

N> `AddPane` raises `PaneAdding` and `PaneAdded`. `RemovePane` raises `PaneClosing` and `PaneClosed`. Cancel `PaneAdding` or `PaneClosing` to prevent the operation. See [Events](Events.md).

## Change the state of a pane

The following methods change the `DockState` of a pane at runtime.

| Method | Description |
|--------|-------------|
| `FloatPane(DockPane)` | Moves the pane to a floating window. Not applied when `AllowFloat` is `false`. |
| `AutoHidePane(DockPane)` | Collapses the pane to the edge as an auto-hidden tab. Not applied when `AllowAutoHide` is `false`. |
| `HidePane(DockPane)` | Hides the pane. The pane is kept so that it can be restored later. Raises `PaneClosing` and `PaneClosed`. |
| `RestorePane(DockPane)` | Returns a hidden, floating, auto-hidden, or document pane to the `Docked` state. |
| `SetPaneState(DockPane, DockState)` | Moves the pane to the specified state. The `AllowFloat` and `AllowAutoHide` restrictions apply. |
| `ActivatePane(DockPane)` | Makes the pane the active pane. |

{% tabs %}
{% highlight xaml %}

<StackPanel Orientation="Horizontal" Spacing="8">
    <Button Content="Float" Click="OnFloat"/>
    <Button Content="Auto-Hide" Click="OnAutoHide"/>
    <Button Content="Hide" Click="OnHide"/>
    <Button Content="Restore" Click="OnRestore"/>
</StackPanel>

<docking:SfDockingManager x:Name="dockingManager">
    <docking:DockPane x:Name="ToolboxPane"
                      Header="Toolbox"
                      DockDirection="Left"
                      DockState="Docked">
        <TextBlock Text="Toolbox Content"/>
    </docking:DockPane>
</docking:SfDockingManager>

{% endhighlight %}

{% highlight c# %}

private void OnFloat(object sender, RoutedEventArgs e) => dockingManager.FloatPane(ToolboxPane);

private void OnAutoHide(object sender, RoutedEventArgs e) => dockingManager.AutoHidePane(ToolboxPane);

private void OnHide(object sender, RoutedEventArgs e) => dockingManager.HidePane(ToolboxPane);

private void OnRestore(object sender, RoutedEventArgs e) => dockingManager.RestorePane(ToolboxPane);

{% endhighlight %}
{% endtabs %}

The `SetPaneState` method can be used instead of the individual methods.

{% highlight c# %}

dockingManager.SetPaneState(ToolboxPane, DockState.Floating);
dockingManager.SetPaneState(ToolboxPane, DockState.Document);
dockingManager.SetPaneState(ToolboxPane, DockState.Docked);

{% endhighlight %}

N> These methods do nothing when the pane is `null`, is not part of the DockingManager, or is already in the requested state.

## Pane sizes

Use the following `DockPane` properties to control the size of a docked pane along its docked edge. Left and right panes use the value as their width. Top and bottom panes use it as their height.

| Property | Description |
|----------|-------------|
| `DesiredDockSize` | The preferred size of the pane. The default value is `NaN`, which uses the default pane size. |
| `MinDockSize` | The minimum size of the pane. The default value is `NaN`, which uses the default minimum. |
| `MaxDockSize` | The maximum size of the pane. The default value is `NaN`, which applies no maximum. A negative, infinite, or not-greater-than-minimum value also applies no maximum. |

{% tabs %}
{% highlight xaml %}

<docking:DockPane Header="Toolbox"
                  DockDirection="Left"
                  DockState="Docked"
                  DesiredDockSize="250"
                  MinDockSize="150"
                  MaxDockSize="400">
    <TextBlock Text="Toolbox Content"/>
</docking:DockPane>

<docking:DockPane Header="Output"
                  DockDirection="Bottom"
                  DockState="Docked"
                  DesiredDockSize="180">
    <TextBlock Text="Build Output Window"/>
</docking:DockPane>

{% endhighlight %}

{% highlight c# %}

DockPane toolboxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = Dock.Left,
    DockState = DockState.Docked,
    DesiredDockSize = 250,
    MinDockSize = 150,
    MaxDockSize = 400
};

DockPane outputPane = new DockPane()
{
    Header = "Output",
    DockDirection = Dock.Bottom,
    DockState = DockState.Docked,
    DesiredDockSize = 180
};

{% endhighlight %}
{% endtabs %}

To read or restore the size of a docked pane as a ratio, use `GetDockSizeRatio` and `SetPaneSizeRatio`. The ratio is the pane size relative to the pane plus the document area along the same axis. `GetDockSizeRatio` returns `NaN` when the pane is not docked.

{% highlight c# %}

double ratio = dockingManager.GetDockSizeRatio(toolboxPane);

dockingManager.SetPaneSizeRatio(toolboxPane, 0.25);

{% endhighlight %}
