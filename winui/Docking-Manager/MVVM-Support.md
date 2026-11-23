---
layout: post
title: MVVM Support in WinUI DockingManager Control | Syncfusion®
description: Learn how to generate panes from a view model collection using the ItemsSource property of the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# MVVM Support in WinUI DockingManager

The DockingManager control can generate its panes from a collection bound to the `ItemsSource` property. This lets a view model add and remove panes without referencing the view.

## Bind a collection of panes

Bind an `ObservableCollection<DockPane>` to [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.SfDockingManager.html#Syncfusion_UI_Xaml_Docking_SfDockingManager_ItemsSource). Each [DockPane](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.DockPane.html) in the collection is added to the layout using its own [DockDirection](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.DockPane.html#Syncfusion_UI_Xaml_Docking_DockPane_DockDirection) and [DockState](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.DockPane.html#Syncfusion_UI_Xaml_Docking_DockPane_DockState).

{% tabs %}
{% highlight xaml %}

<Grid x:Name="grid">
    <Grid.DataContext>
        <local:DockingViewModel/>
    </Grid.DataContext>
    <docking:SfDockingManager x:Name="dockingManager"
                              Grid.Row="1"
                              ItemsSource="{Binding Panes}"/>
</Grid>

{% endhighlight %}

{% highlight c# %}

using System.Collections.ObjectModel;
using Syncfusion.UI.Xaml.Docking;

public class DockingViewModel
{
    public ObservableCollection<DockPane> Panes { get; } = new ObservableCollection<DockPane>();

    public DockingViewModel()
    {
        Panes.Add(new DockPane()
        {
            Header = "Toolbox",
            DockDirection = Dock.Left,
            DockState = DockState.Docked,
            Content = new TextBlock() { Text = "Toolbox Content" }
        });

        Panes.Add(new DockPane()
        {
            Header = "MainWindow.xaml",
            DockState = DockState.Document,
            Content = new TextBox() { AcceptsReturn = true }
        });
    }
}

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
    }
}

{% endhighlight %}
{% endtabs %}

N> [View Sample in GitHub](https://github.com/SyncfusionExamples/winui-sfdockingmanager-samples/tree/master/Samples/MVVM)
## Collection changes

When the bound collection implements `INotifyCollectionChanged`, such as `ObservableCollection<T>`, the DockingManager keeps the panes in sync:

| Collection change | Result |
|-------------------|--------|
| Add | A pane is added to the layout for each new item. |
| Remove | The pane generated for the removed item is removed from the layout. |
| Replace | The old pane is removed and a pane for the new item is added. |
| Reset (for example `Clear()`) | All generated panes are removed and regenerated from the current items. |

Setting `ItemsSource` to a different collection removes the previously generated panes and creates panes for the new collection.

## Bind items that are not panes

An item that is not a `DockPane` is also converted to a pane. The pane [Header](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Docking.DockPane.html#Syncfusion_UI_Xaml_Docking_DockPane_Header) is set to the text returned by the item's `ToString()` method, and the item itself becomes the pane `Content`. Override `ToString()` on the item type to control the header text.

{% highlight c# %}

public class NoteItem
{
    public string Title { get; set; }

    public override string ToString() => Title;
}

// The generated pane header is "Notes" and its content is the NoteItem instance.
public ObservableCollection<NoteItem> Notes { get; } = new ObservableCollection<NoteItem>();
// Bind: ItemsSource="{Binding Notes}"
Notes.Add(new NoteItem() { Title = "Notes" });

{% endhighlight %}

N> `ItemsSource` panes participate in the layout like panes defined in XAML. Pane methods such as `FloatPane`, `AutoHidePane`, and `HidePane`, and layout [serialization](https://help.syncfusion.com/winui/docking-manager/serialization), work with them in the same way.
