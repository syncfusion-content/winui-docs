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

## Event arguments

| Event argument | Properties |
|----------------|------------|
| `PaneEventArgs` | `Pane` - the affected pane. |
| `PaneCancelEventArgs` | `Pane` - the affected pane. `Cancel` - set to `true` to cancel the operation. |
| `ActivePaneChangedEventArgs` | `OldPane` - the previously active pane. `NewPane` - the newly active pane. Either value can be `null`. |
| `DockStateChangedEventArgs` | `Pane` - the affected pane. `OldState` - the previous `DockState`. `NewState` - the new `DockState`. |
| `LayoutChangedEventArgs` | `Reason` - the `LayoutChangeReason` that caused the update. `Pane` - the pane involved, if any. |
| `DragStartedEventArgs` | `Pane` - the dragged pane. `InitialPosition` - the pointer position where the drag started. |
| `DragDeltaEventArgs` | `Pane` - the dragged pane. `Position` - the pointer position. `OldTarget` and `NewTarget` - the previous and current `Dock` targets, if any. |
| `DockOperationCompletedEventArgs` | `Pane` - the docked pane. `Operation` - the `Dock` target that was applied. |

## Cancel adding or closing a pane

The `PaneAdding` and `PaneClosing` events can be cancelled. The following example keeps the **Output** pane from being closed.

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

dockingManager.DockStateChanged += (s, e) =>
{
    Debug.WriteLine($"{e.Pane?.Header}: {e.OldState} -> {e.NewState}");
};

dockingManager.ActivePaneChanged += (s, e) =>
{
    Debug.WriteLine($"Active pane: {e.OldPane?.Header} -> {e.NewPane?.Header}");
};

dockingManager.LayoutChanged += (s, e) =>
{
    Debug.WriteLine($"Layout changed: {e.Reason}");
};

{% endhighlight %}

## Drag-and-drop events

{% highlight c# %}

dockingManager.DragStarted += (s, e) =>
{
    Debug.WriteLine($"Drag started: {e.Pane.Header}");
};

dockingManager.DragCompleted += (s, e) =>
{
    Debug.WriteLine($"Dropped {e.Pane.Header} on {e.NewTarget}");
};

dockingManager.DragCancelled += (s, e) =>
{
    Debug.WriteLine($"Drag cancelled: {e.Pane.Header}");
};

dockingManager.DockOperationCompleted += (s, e) =>
{
    Debug.WriteLine($"{e.Pane.Header} docked: {e.Operation}");
};

{% endhighlight %}
