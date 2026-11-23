---
layout: post
title: Events in WinUI DockingManager Control | Syncfusion®
description: Learn about the pane, state, layout, and drag-and-drop events of the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Events in WinUI DockingManager

The DockingManager control raises events when panes are added or closed, when the active pane or the dock state changes, when the layout is updated, and during drag-and-drop operations.

| Event | Event argument | Description |
|-------|----------------|-------------|
| `PaneAdding` | `PaneCancelEventArgs` | Occurs before a pane is added. Set `Cancel` to `true` to prevent the pane from being added. |
| `PaneAdded` | `PaneEventArgs` | Occurs after a pane is added. |
| `PaneClosing` | `PaneCancelEventArgs` | Occurs before a pane is removed or hidden. Set `Cancel` to `true` to keep the pane. |
| `PaneClosed` | `PaneEventArgs` | Occurs after a pane is removed or hidden. |
| `ActivePaneChanged` | `ActivePaneChangedEventArgs` | Occurs after the active pane changes. |
| `DockStateChanged` | `DockStateChangedEventArgs` | Occurs after the dock state of a pane changes. |
| `LayoutChanged` | `LayoutChangedEventArgs` | Occurs after the layout is recalculated. |
| `DragStarted` | `DragStartedEventArgs` | Occurs when a pane drag operation starts. |
| `DragCompleted` | `DragDeltaEventArgs` | Occurs when a pane is dropped on a dock target. |
| `DragCancelled` | `DragDeltaEventArgs` | Occurs when a pane drag operation is cancelled. |
| `DockOperationCompleted` | `DockOperationCompletedEventArgs` | Occurs after the dock operation caused by a drop is applied. |

## Cancel adding or closing a pane

The [PaneAdding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.SfDockingManager.html#Syncfusion_UI_Xaml_Docking_SfDockingManager_PaneAdding) and [PaneClosing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.SfDockingManager.html#Syncfusion_UI_Xaml_Docking_SfDockingManager_PaneClosing) events can be cancelled. The following example keeps the **Output** pane from being closed.

{% tabs %}
{% highlight xaml %}

<docking:SfDockingManager x:Name="dockingManager"
                          PaneClosing="OnPaneClosing"/>

{% endhighlight %}

{% highlight c# %}

private void OnPaneClosing(object sender, PaneCancelEventArgs e)
{
    if (e.Pane?.Header?.ToString() == "Output")
    {
        e.Cancel = true;
    }
}

{% endhighlight %}
{% endtabs %}

## Track state and active pane changes

{% highlight c# %}

dockingManager.DockStateChanged += OnDockStateChanged;
dockingManager.ActivePaneChanged += OnActivePaneChanged;
dockingManager.LayoutChanged += OnLayoutChanged;

private void OnDockStateChanged(object sender, DockStateChangedEventArgs e)
{
    Debug.WriteLine($"{e.Pane?.Header}: {e.OldState} -> {e.NewState}");
}

private void OnActivePaneChanged(object sender, ActivePaneChangedEventArgs e)
{
    Debug.WriteLine($"Active pane: {e.OldPane?.Header} -> {e.NewPane?.Header}");
}

private void OnLayoutChanged(object sender, LayoutChangedEventArgs e)
{
    Debug.WriteLine($"Layout changed: {e.Reason}");
}

{% endhighlight %}

## Drag-and-drop events

{% highlight c# %}

dockingManager.DragStarted += OnDragStarted;
dockingManager.DragCompleted += OnDragCompleted;
dockingManager.DragCancelled += OnDragCancelled;
dockingManager.DockOperationCompleted += OnDockOperationCompleted;

private void OnDragStarted(object sender, DragStartedEventArgs e)
{
    Debug.WriteLine($"Drag started: {e.Pane.Header}");
}

private void OnDragCompleted(object sender, DragDeltaEventArgs e)
{
    Debug.WriteLine($"Dropped {e.Pane.Header} on {e.NewTarget}");
}

private void OnDragCancelled(object sender, DragDeltaEventArgs e)
{
    Debug.WriteLine($"Drag cancelled: {e.Pane.Header}");
}

private void OnDockOperationCompleted(object sender, DockOperationCompletedEventArgs e)
{
    Debug.WriteLine($"{e.Pane.Header} docked: {e.Operation}");
}

{% endhighlight %}
