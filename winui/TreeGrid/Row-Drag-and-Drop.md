---
layout: post
title: Row drag and drop in WinUI TreeGrid control | Syncfusion
description: Learn here all about row drag and drop support in Syncfusion WinUI TreeGrid (SfTreeGrid) control and more.
platform: winui
control: SfTreeGrid
documentation: ug
---

# Row drag and drop in WinUI TreeGrid (SfTreeGrid)

`SfTreeGrid` allows you to drag and drop the rows by setting the [AllowDraggingRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_AllowDraggingRows) and [AllowDrop](https://docs.microsoft.com/en-us/dotnet/api/system.windows.uielement.allowdrop) properties to true. You can also drag and drop the rows between treegrid and other controls such as [ListView](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.controls.listview?view=winui-3.0), [DataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html) and [SfTreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html). 

{% tabs %}
{% highlight xml %}
<syncfusion:SfTreeGrid Name="sfTreeGrid" 
                               AllowDraggingRows="True" 
                               AllowDrop="True" 
                               ChildPropertyName="ReportsTo" 
                               ItemsSource="{Binding Employees}"
                               ParentPropertyName="ID"
                               SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
sfTreeGrid.AllowDraggingRows = true;
sfTreeGrid.AllowDrop = true;
{% endhighlight %}
{% endtabs %}

<img src="Row-Drag-and-Drop-images/draganddrop-img1.png" alt="Drag and Drop the Row in WinUI TreeGrid" width="100%" Height="Auto"/>

While dropping, the dragging nodes can be added above or below or as a child node based on their [DropPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDropPosition.html). For example, if you drop a node at the bottom of the target node, it will be added below the target node. If you drop over the target node, it will be added as a child of that target node.

<img src="Row-Drag-and-Drop-images/draganddrop-img2.png" alt="Drap and Drop the Row in WinUI TreeGrid" width="100%" Height="Auto"/>

N> Drag indicators will not be shown when [DropPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDropPosition.html) is set to [AsChild](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDropPosition.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowDropPosition_AsChild).

## Drag multiple nodes

SfTreeGrid allows users to select and drag multiple nodes. You can enable multiple selection by setting the [SfTreeGrid.SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectionMode) property to `Multiple` or `Extended`.

<img src="Row-Drag-and-Drop-images/draganddrop-img3.png" alt="Dragging Multiple Rows in WinUI TreeGrid" width="100%" Height="Auto"/>

## Drag and drop events

When dragging and dropping the nodes `SfTreeGrid` triggers the following events:

### RowDragStarting event

[RowDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDragStarting) event occurs when you start to drag the node in the SfTreeGrid. The [TreeGridRowDragStartingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDragStartingEventArgs.html) has the following member, which provides information for the `RowDragStarting` event.

`DraggingNodes`: Gets the TreeNode that contains the data associated when dragging the rows.

`Cancel` :  Gets or sets a value indicating whether the event is canceled or not. 

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragStarting += SfTreeGrid_RowDragStarting;

private void SfTreeGrid_RowDragStarting(object sender, TreeGridRowDragStartingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDragOver event

[RowDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDragOver) event occurs continuously when dragging the tree node in the SfTreeGrid. The [TreeGridRowDragOverEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDragOverEventArgs.html) has the following members, which provide information for the `RowDragOver` event:

`Data`: Gets a data object that contains the data associated with dragging the nodes.

`DraggingNodes`: Gets the tree node that contains the data associated with dragging the nodes.

`DropPosition`: Gets a value indicating the drop position based on the dropped location.

`ShowDragUI`: Gets or sets the visibility of Dragging UI.

`TargetNode`: Gets a value that indicates the target node where the record is going to be drop.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragOver += SfTreeGrid_RowDragOver;

private void SfTreeGrid_RowDragOver(object sender, TreeGridRowDragOverEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDropping event

[RowDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDropping) event occurs when a tree node is dropping in the SfTreeGrid. The [TreeGridRowDroppingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDroppingEventArgs.html) has the following members, which provide information for the `RowDropping` event:

`Cancel` :  Gets and sets a value indicating whether the event is canceled or not. 

`Data`: Gets a data object that contains the data associated with dragging the nodes.

`DraggingNodes`: Gets the tree node that contains the data associated with dragging the nodes.

`DropPosition`: Gets a value indicating the drop position based on the dropped location.

`TargetNode`: Gets a value that indicates the target node where the record is going to be drop.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDropping += SfTreeGrid_RowDropping;

private void SfTreeGrid_RowDropping(object sender, TreeGridRowDroppingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDropped event

[RowDropped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDropped) event occurs after dropped the tree nodes in the SfTreeGrid. The [TreeGridRowDroppedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDroppedEventArgs.html) has the following members, which provide information for the `RowDropped` event:

`Data`: Gets a data object that contains the data associated with dragging the nodes.

`DraggingNodes`: Gets the tree node that contains the data associated with dragging the nodes.

`DropPosition`: Gets a value indicating the drop position based on the dropped location.

`TargetNode`: Gets a value that indicates the target node where the record is going to be drop.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDropped += SfTreeGrid_RowDropped;

private void SfTreeGrid_RowDropped(object sender, TreeGridRowDroppedEventArgs e)
{
    
}
{% endhighlight %}
{% endtabs %}

## Customizing row drag and drop operation

### Disable dragging of certain nodes

You can restrict the dragging for specific nodes in SfTreeGrid by using the [SfTreeGrid.RowDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDragStarting) event.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragStarting += SfTreeGrid_RowDragStarting;

private void SfTreeGrid_RowDragStarting(object sender, TreeGridRowDragStartingEventArgs e)
{
    var nodes = e.DraggingNodes;
    var item = nodes[0].Item as Employee;
    if (item.FirstName == "Richard")
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

### Disable dropping of certain nodes

You can restrict the dropping for specific nodes in SfTreeGrid by using the [SfTreeGrid.RowDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDropping) event.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDropping += SfTreeGrid_RowDropping;

private void SfTreeGrid_RowDropping(object sender, TreeGridRowDroppingEventArgs e)
{
    // Disable drop on leaf nodes.
    if (!e.TargetNode.HasChildNodes)
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

### Disable default Drag UI

You can disable the draggable pop-up by setting the [ShowDragUI](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowDragOverEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowDragOverEventArgs_ShowDragUI) in [SfTreeGrid.RowDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_RowDragOver) event.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragOver += SfTreeGrid_RowDragOver;

private void SfTreeGrid_RowDragOver(object sender, TreeGridRowDragOverEventArgs e)
{
    e.ShowDragUI = false;
}
{% endhighlight %}
{% endtabs %}