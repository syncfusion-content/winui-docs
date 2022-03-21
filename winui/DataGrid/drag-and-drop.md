---
layout: post
title: Row drag and drop in WinUI DataGrid control | Syncfusion
description: Learn here all about row drag and drop support in Syncfusion WinUI DataGrid (SfDataGrid) control and more.
platform: winui
control: SfDataGrid
documentation: ug
---

# Row drag and drop in WinUI DataGrid (SfDataGrid)

[WinUI DataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html) allows drag and drop the rows by setting the `AllowDraggingRows` and [AllowDrop](https://docs.microsoft.com/en-us/dotnet/api/system.windows.uielement.allowdrop) property as `true`. You can also drag and drop the rows between datagrid and other controls such as `ListView` , `SfTreeView` and `SfTreeGrid`. 

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid"
                     AllowDraggingRows="True"
                     AllowDrop="True"               
                     AutoGenerateColumns="True"
                     ItemsSource="{Binding Orders}" />
{% endhighlight %}

{% highlight c# %}
this.sfDataGrid.AllowDraggingRows = true;
this.sfDataGrid.AllowDrop = true;
{% endhighlight %}
{% endtabs %}

While dropping, the dragged rows can be added above or below to the target record based on its drop position

For example, if you drop record at the bottom of the target record, it will be added below the target record.

<img src="Row_Drag_Drop_Images/RowDragDrop_Img1.png" alt="Drag and Drop Rows in WinUI DataGrid" width="Auto"/>

If you drop above the target record, it will be added above the target record

<img src="Row_Drag_Drop_Images/RowDragDrop_Img2.png" alt="Drag and Drop Rows in WinUI DataGrid" width="Auto"/>

## Dragging multiple rows

WinUI DataGrid (SfDataGrid) allows to select and drag multiple rows. To enable multiple selection, set the [SfDataGrid.SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectionMode) as `Multiple` or `Extended`. 

N> The drag selection cannot be performed while the `AllowDraggingRows` enabled as `true` in the SfDataGrid.

<img src="Row_Drag_Drop_Images/RowDragDrop_Img3.png" alt="Dragging Multiple Rows in WinUI DataGrid" width="Auto"/>

## Drag and drop events

SfDataGrid triggers the following events when drag and drop:

### Row Drag starting event

`RowDragStarting` event occurs when you start to drag the records in datagrid. The `DataGridRowDragStartingEventArgs` has the following member, which provides information for the `RowDragStarting` event.
* `DraggingRows` : Gets the records which contains the data associated while dragging the rows.
* `Cancel` : Gets and sets a value indicating whether the event is Canceled or not. 

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDragStarting += SfDataGrid_RowDragStarting;

private void SfDataGrid_RowDragStarting(object sender, DataGridRowDragStartingEventArgs e)
{
    
}
{% endhighlight %}
{% endtabs %}

### Row Drag over event

`RowDragOver` event occurs continuously while record is dragged within the target SfDataGrid. The `DataGridRowDragOverEventArgs` has the following members, which provide information for the `RowDragOver` event.
* `Data` : Gets a data object that contains the data associated while dragging the rows. 
* `DraggingRows` : Gets the records which contains the data associated while dragging the rows.
* `DropPosition` : Gets a value indicating the drop position which is based on dropped location 
* `ShowDragUI` : Gets or sets the visibility of Dragging UI.  
* `TargetIndex` : Gets a value indicating the target index which is going to drop.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDragOver += SfDataGrid_RowDragOver;

private void SfDataGrid_RowDragOver(object sender, DataGridRowDragOverEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### Row Dropping event

`RowDropping` event occurs when a record is dropping within the target SfDataGrid. The `DataGridRowDroppingEventArgs` has the following members, which provide information for the `RowDropping` event.
* `Cancel` : Gets and sets a value indicating whether the event is Canceled or not. 
* `Data` : Gets a data object that contains the data associated while dragging the rows. 
* `DraggingRows` : Gets the records which contains the data associated while dragging the rows. 
* `DropPosition` : Gets a value indicating the drop position which is based on dropped location 
* `TargetIndex` : Gets a value indicating the target record which is going to drop.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDropping += SfDataGrid_RowDropping;

private void SfDataGrid_RowDropping(object sender, DataGridRowDroppingEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### Row Dropped event

`RowDropped` event occurs when a record is dropping within the target SfDataGrid. The `DataGridRowDroppedEventArgs` has the following members, which provide information for the `Dropping` event.
* `Data` : Gets a data object that contains the data associated while dragging the rows. 
* `DraggingRows` : Gets the records which contains the data associated while dragging the rows.
* `DropPosition` : Gets a value indicating the drop position which is based on dropped location 
* `TargetIndex` : Gets a value indicating the target record which is going to drop.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDropped += SfDataGrid_RowDropped;

private void SfDataGrid_RowDropped(object sender, DataGridRowDroppedEventArgs e)
{
    
}
{% endhighlight %}
{% endtabs %}

## Customizing row drag and drop operation

### Disable dragging of certain rows in WinUI DataGrid

You can restrict the dragging of certain rows in SfDataGrid by using the  `SfDataGrid.RowDragStarting` event.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDragStarting += SfDataGrid_RowDragStarting;

private void SfDataGrid_RowDragStarting(object sender, DataGridRowDragStartingEventArgs e)
{
    var records = e.DraggingRows;
    var orders = records[0] as OrderInfo;
    if (orders.OrderID > 1005)
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

### Disable dropping over certain rows in WinUI DataGrid

You can restrict the dropping the records in certain rows in SfDataGrid by using the [SfDataGrid.RowDropping] event.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDropping += SfDataGrid_RowDropping;

private void SfDataGrid_RowDropping(object sender, DataGridRowDroppingEventArgs e)
{
    if(e.TargetIndex > 6)
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

### Disable the drag UI

You can disable the draggable popup by setting the `ShowDragUI` as `false` in `SfDataGrid.RowDragOver` event.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDragOver += SfDataGrid_RowDragOver;

private void SfDataGrid_RowDragOver(object sender, DataGridRowDragOverEventArgs e)
{
    e.ShowDragUI = false;
}
{% endhighlight %}
{% endtabs %}

### Reorder the source collection while drag and drop the rows

You can reorder the source collection after drag and drop the row by handling `SfDataGrid.RowDropped` event.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.RowDropped += SfDataGrid_RowDropped;

private void SfDataGrid_RowDropped(object sender, DataGridRowDroppedEventArgs e)
{
    if (e.DropPosition != DataGridRowDropPosition.None)
    {
        // Get Dragging records
        ObservableCollection<object> draggingRecords = e.DraggingRows as ObservableCollection<object>;

        // Gets the TargetRecord from the underlying collection using record index of the TargetRecord (e.TargetIndex)
        ViewModel viewmodel = sfDataGrid.DataContext as ViewModel;
        OrderInfo targetRecord = viewmodel.Orders[e.TargetIndex];

        // Removes the dragging records from the underlying collection
        foreach (OrderInfo item in draggingRecords)
        {
            viewmodel.Orders.Remove(item);
        }

        // Find the target record index after removing the records
        int targetIndex = viewmodel.Orders.IndexOf(targetRecord);
        int insertionIndex = e.DropPosition == DataGridRowDropPosition.Above ? targetIndex : targetIndex + 1;
        insertionIndex = insertionIndex < 0 ? 0 : insertionIndex;

        // Insert dragging records to the target position
        for (int i = draggingRecords.Count - 1; i >= 0; i--)
        {
            viewmodel.Orders.Insert(insertionIndex, draggingRecords[i] as OrderInfo);
        }
    }
}
{% endhighlight %}
{% endtabs %}
