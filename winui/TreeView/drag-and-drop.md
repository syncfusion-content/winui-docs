---
layout: post
title: Drag and Drop in WinUI TreeView control | Syncfusion
description: Learn here all about Drag and Drop support in Syncfusion WinUI TreeView control and more details.
platform: winui
control: SfTreeView
documentation: ug
---

# Drag and Drop in WinUI TreeView

TreeView allows drag and drop the items within the treeview control by setting the [CanDrag](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.candrag?view=winrt-19041) property as `true`. It is also possible to drag and drop the items between treeview and other controls such as `ListView` and `SfDataGrid`. 

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView x:Name="treeView"
                        Width="400"
                        Height="500"
                        CanDrag="True"
                        AutoExpandMode="AllNodes"
                        BorderBrush="LightGray"
                        BorderThickness="1"
                        IsAnimationEnabled="True"
                        ChildPropertyName="Files"
                        ItemsSource="{Binding Folders}">
    <treeView:SfTreeView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <ContentPresenter Width="20"
                                    Height="20"
                                    HorizontalAlignment="Stretch"
                                    VerticalAlignment="Center"
                                    ContentTemplate="{Binding ImageTemplate}" />
                <TextBlock Margin="5"
                            VerticalAlignment="Center"
                            Text="{Binding FileName}" />
            </StackPanel>
        </DataTemplate>
    </treeView:SfTreeView.ItemTemplate>
</treeView:SfTreeView>
{% endhighlight %}
{% highlight c# %}
treeView.CanDrag = true;
{% endhighlight %}
{% endtabs %}

While dropping, the dragged items can be added above or below to the target item based on drag indicator position.

![Drag and drop items in WinUI treeview](DragDrop_images/DragDrop_image1.png)

## Dragging multiple items

SfTreeView allows to drag multiple selected items. To enable multiple selection, set the [SfTreeView.SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_SelectionMode) as `Multiple` or `Extended`. 

![Drag and drop items in WinUI treeview](DragDrop_images/DragDrop_image2.png)
## Drag and drop events

SfTreeView triggers the following events when drag and drop:

### ItemDragStarting event

[ItemDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDragStarting) event occurs when you starting to drag the items in treeview. The [TreeViewItemDragStartingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs.html)  has the following member, which provides information for the `ItemDragStarting` event.

* [Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDragStartingEventArgs_Data) : Gets or Sets a data object that contains the data associated while dragging the items. 
* [DraggingNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDragStartingEventArgs_DraggingNodes) : Gets the collection of [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) which are dragged.If you set the Data property, the value of DraggingNodes property will be `null`.
* [Cancel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDragStartingEventArgs_Cancel) : Gets or sets a value indicating whether dragging should be canceled.

{% tabs %}
{% highlight c# %}
treeView.ItemDragStarting += TreeView_ItemDragStarting;

private void TreeView_ItemDragStarting(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### ItemDragStarted event

[ItemDragStarted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDragStarted)  event occurs after started the dragging, in treeview. The [TreeViewItemDragStartedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartedEventArgs.html)  has the following member, which provides information for the `ItemDragStarted` event.

* [Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDragStartedEventArgs_Data) : Gets a data object that contains the data associated while dragging the items. 
* [DraggingNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDragStartedEventArgs_DraggingNodes) : Gets the collection of [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) which are dragged.

{% tabs %}
{% highlight c# %}
treeView.ItemDragStarted += TreeView_ItemDragStarted;

private void TreeView_ItemDragStarted(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartedEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}


### ItemDropping event

[ItemDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropping) event occurs when item is dropping within the targeted SfTreeView. The [TreeViewItemDroppingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html) has the following members, which provide information for the `ItemDropping` event.

* [Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_Data) : Gets a data object that contains the data associated while dragging the items. 
* [DraggingNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_DraggingNodes) : Gets the collection of [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) which are dragged.
* [DragSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_DragSource) : Gets the source of the transferred data.
* [DropPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_DropPosition) : Gets or sets the position where dragged nodes are going to be dropped.
* [Handled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_Handled) : Gets or sets a value indicating whether the event is handled. If this event is handled, dragged nodes will not be dropped to TreeView.
* [TargetNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppingEventArgs_TargetNode) : Gets the node where the dragged nodes are going to be dropped.

{% tabs %}
{% highlight c# %}
treeView.ItemDropping += TreeView_ItemDropping;

private void TreeView_ItemDropping(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### ItemDropped event

[ItemDropped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropped) event occurs when item is dropped within the targeted SfTreeView. The [TreeViewItemDroppedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html) has the following members, which provide information for the `Drop` event.
* [Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppedEventArgs_Data) : Gets a data object that contains the data associated while dragging the items. 
* [DraggingNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppedEventArgs_DraggingNodes) : Gets the collection of [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) which are dragged.
* [DragSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppedEventArgs_DragSource) : Gets the source of the transferred data.
* [DropPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppedEventArgs_DropPosition) : Gets the position where dragged nodes are dropped.
* [TargetNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs.html#Syncfusion_UI_Xaml_TreeView_TreeViewItemDroppedEventArgs_TargetNode) : Gets the node where the dragged nodes are dropped.

{% tabs %}
{% highlight c# %}
treeView.ItemDropped += TreeView_ItemDropped

private void TreeView_ItemDropped(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs e)
{

}

{% endhighlight %}
{% endtabs %}

## Customizing the drag and drop operation

### Disable dragging of certain items in WinUI TreeView

You can restrict the dragging of certain nodes in SfTreeView by using the  [SfTreeView.ItemDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDragStarting) event.

{% tabs %}
{% highlight c# %}
treeView.ItemDragStarting += TreeView_ItemDragStarting;

private void TreeView_ItemDragStarting(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs e)
{
    var record = e.DraggingNodes[0].Content as Folder;
    if (record.FileName == "Sanitation.docx")
        e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

### Disable dropping on certain items in WinUI TreeView

You can restrict the dropping the items on certain nodes in SfTreeView by using the [SfTreeView.ItemDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropping) event.

{% tabs %}
{% highlight c# %}
treeView.ItemDropping += TreeView_ItemDropping;

private void TreeView_ItemDropping(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs e)
{
    var record = e.DraggingNodes[0].Content as Folder;
    if (record.FileName == "Downloads")
        e.Handled = true;
}
{% endhighlight %}
{% endtabs %}

### Customize the drop position

You can customize the drop position of dragging nodes in SfTreeView by using the [SfTreeView.ItemDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropping) event.

{% tabs %}
{% highlight c# %}
treeView.ItemDropping += TreeView_ItemDropping;

private void TreeView_ItemDropping(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs e)
{
    var record = e.DraggingNodes[0].Content as Folder;
    if (record.FileName == "Downloads")
        e.DropPosition = Syncfusion.UI.Xaml.TreeView.DropPosition.DropAsChild;
}

{% endhighlight %}
{% endtabs %}

## Drag and drop between two TreeView's

You can customize the dragging operation between two treeview by using the [SfTreeView.ItemDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDragStarting) , [SfTreeView.ItemDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropping) and [SfTreeView.ItemDropped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDropped) events.

{% tabs %}
{% highlight c# %}

AssociatedObject.sfTreeView1.ItemDragStarting += SfTreeView1_ItemDragStarting;    
AssociatedObject.sfTreeView1.ItemDropping += SfTreeView1_ItemDropping;
AssociatedObject.sfTreeView2.ItemDropping += SfTreeView2_ItemDropping;
AssociatedObject.sfTreeView2.ItemDropped += SfTreeView1_ItemDropped;
    
 /// <summary>
 /// Customizing the ItemStarting event
 /// </summary>
 /// <param name="sender"></param>
 /// <param name="e"></param>
 private void SfTreeView1_ItemDragStarting(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDragStartingEventArgs e)
 {
     //Restrict the dragging for certain node
     var record = e.DraggingNodes[0].Content as Model;
     if (record.Header == "Feature Schedule")
         e.Cancel = true;
 }

 /// <summary>
 /// Customizing the ItemDropping event
 /// </summary>
 /// <param name="sender"></param>
 /// <param name="e"></param>
 private void SfTreeView1_ItemDropping(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs e)
 {
     //Restrict the dropping in first treeview
     e.Handled = true;
 }

 /// <summary>
 /// Customizing the ItemDropping event
 /// </summary>
 /// <param name="sender"></param>
 /// <param name="e"></param>
 private void SfTreeView2_ItemDropping(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppingEventArgs e)
 {
     //Restrict the dropping for drop position as above
     if (e.DropPosition == Syncfusion.UI.Xaml.TreeView.DropPosition.DropAbove)
         e.Handled = true;

     //Restrict the dropping on certain nodes
     var record = e.TargetNode.Content as Model;
     if (record.Header == "My Folders")
         e.Handled = true;
 }

 /// <summary>
 /// Customize the ItemDropped event
 /// </summary>
 /// <param name="sender"></param>
 /// <param name="e"></param>
 private void SfTreeView1_ItemDropped(object sender, Syncfusion.UI.Xaml.TreeView.TreeViewItemDroppedEventArgs e)
 {
     var parentNode = e.TargetNode.ParentNode;
     var collection = parentNode.ChildNodes;
     var record = e.DraggingNodes[0].Content as Model;
     int count = 0;
     foreach (var child in parentNode.ChildNodes)
     {
         var childNode = child.Content as Model;
         if (childNode.Header == record.Header)
         {
             count++;
             if (count > 1)
             {
                // Remove dropped node if the parent has the same node in it
                 collection.Remove(child);
                 return;
             }

         }
     }
 }

{% endhighlight %}
{% endtabs %}

![Drag and drop items in WinUI treeview](DragDrop_images/DragDrop_image3.png)

N> View sample in [GitHub](https://github.com/SyncfusionExamples/How-to-drag-and-drop-between-two-winui-treeview)
