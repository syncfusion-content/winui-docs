---
layout: post
title: Interactive Features in WinUI TreeGrid control | Syncfusion
description: Learn here all about Interactive Features support in Syncfusion WinUI TreeGrid (SfTreeGrid) control and more.
platform: winui
control: SfTreeGrid
documentation: ug
---

# Interactive Features in WinUI TreeGrid (SfTreeGrid)

## Row drag and drop 

SfTreeGrid allows drag and drop the rows within and between controls by setting the `AllowDraggingRows` and `AllowDrop` properties to true. It is also possible to drag and drop the rows between treegrid and other controls such as ListView, DataGrid and TreeView. SfTreeGrid allows dropping rows when `AllowDrop` is true and allows dragging when `AllowDraggingRows` is true.

{% tabs %}
{% highlight xml %}
<syncfusion:SfTreeGrid Name="sfTreeGrid" 
                               AllowDraggingRows="True" 
                               AllowDrop="True" 
                               ChildPropertyName="ReportsTo" 
                               AutoGenerateColumns="False"                                  
                               ItemsSource="{Binding Employees}"
                               ParentPropertyName="ID"
                               SelfRelationRootValue="-1" />
{% endhighlight %}
{% highlight c# %}
sfTreeGrid.AllowDraggingRows = true;
sfTreeGrid.AllowDrop = true;
{% endhighlight %}
{% endtabs %}

![Drag and Drop the Row in WinUI TreeGrid](Row-Drag-and-Drop_images/draganddrop_img1.jpeg)

When dropping, the dragged node(s) can be added above or below as a child node based on its drop position. For example, if you dropped node at the bottom of the targeted node, it will be added below the targeted node. If you drop over the targeted node, it will be added as a child of that targeted node.

![Drap and Drop the Row in WinUI TreeGrid](Row-Drag-and-Drop_images/draganddrop_img3)

N> Drag indicators will not be shown when drop position is set to “Drop as child”.

### Drag multiple nodes

SfTreeGrid allows users to drag multiple selected nodes. You can enable multiple selection by setting the [SfTreeGrid.SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectionMode) property to `Multiple` or `Extended`.

![Dragging Multiple Rows in WinUI TreeGrid](Row-Drag-and-Drop_images/draganddrop_img3)

### Events

SfTreeGrid triggers the following events when drag and drop:

### RowDragStarting

`RowDragStarting`: Occurs when you start to drag the node in treegrid. The `TreeGridRowDragStartingEventArgs` has the following member, which provides information for the `RowDragStarting` event.

`DraggingNodes`: Gets the TreeNode that contains the data associated when dragging the rows.

`Cancel` :  Gets and Sets a value indicating whether the event is Canceled or not. 
  
{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragStarting += SfTreeGrid_RowDragStarting;

private void SfTreeGrid_RowDragStarting(object sender, TreeGridRowDragStartingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDragOver

`RowDragOver`: Occurs continuously when tree node is dragged within the the target treegrid. The `TreeGridRowDragOverEventArgs` has the following members, which provide information for the `RowDragOver` event:

`Data`: Gets or sets a data object that contains data associated when dragging the rows.

`DraggingNodes`: Gets the TreeNode that contains the data associated when dragging the rows.

`DropPosition`: Gets a value that indicates the drop position based on the dropped location.

`ShowDragUI`: Gets or sets a value that indicates the default Dragging UI.

`TargetNode`: Gets a value that indicates the target node, which is going to be dropped.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragOver += SfTreeGrid_RowDragOver;

private void SfTreeGrid_RowDragOver(object sender, TreeGridRowDragOverEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDropping

`RowDropping`: Occurs when a record is dropped within the target treegrid. The `TreeGridRowDroppingEventArgs` has the following members, which provide information for the `RowDropping` event:

`Cancel` :  Gets and Sets a value indicating whether the event is Canceled or not. 

`Data`: Gets or sets a data object that contains data associated when dragging the rows.

`DraggingNodes`: Gets the TreeNode that contains the data associated when dragging the rows.

`DropPosition`: Gets a value that indicates the drop position based on the dropped location.

`TargetNode`: Gets a value that indicates the target node, which is going to be dropped.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDropping += SfTreeGrid_RowDropping;

private void SfTreeGrid_RowDropping(object sender, TreeGridRowDroppingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### RowDropped

`RowDropped`: Occurs when a record is dropped within the target treegrid. The `TreeGridRowDroppedEventArgs` has the following members, which provide information for the `RowDropped` event:

`Data`: Gets or sets a data object that contains data associated when dragging the rows.

`DraggingNodes`: Gets the TreeNode that contains the data associated when dragging the rows.

`DropPosition`: Gets a value that indicates the drop position based on the dropped location.

`TargetNode`: Gets a value that indicates the target node, which is going to be dropped.

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDropped += SfTreeGrid_RowDropped;

private void SfTreeGrid_RowDropped(object sender, TreeGridRowDroppedEventArgs e)
{
    
}
{% endhighlight %}
{% endtabs %}

### Disable dragging of certain nodes

You can restrict the dragging for specific nodes in SfTreeGrid by using the `SfTreeGrid.RowDragStarting` event.

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

You can restrict the dropping for specific nodes in SfTreeGrid by using the `SfTreeGrid.RowDropping` event..

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

You can disable the draggable popup by setting the `ShowDragUI` in the `RowDragOver` event of  `SfTreeGrid.RowDragOver` event..

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.RowDragOver += SfTreeGrid_RowDragOver;

private void SfTreeGrid_RowDragOver(object sender, TreeGridRowDragOverEventArgs e)
{
    e.ShowDragUI = false;
}
{% endhighlight %}
{% endtabs %}