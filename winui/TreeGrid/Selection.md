---
layout: post
title: Selection | TreeGrid | WinUI | Syncfusion
description: This section explains about the selection of the rows and its customization in Syncfusion WinUI TreeGrid (SfTreeGrid) control and more details
platform: winui
control: TreeGrid
documentation: ug
---

# Selection in WinUI TreeGrid (SfTreeGrid)

SfTreeGrid allows you select one or more rows. 

## Current cell navigation

Keyboard navigation through the rows is determined based on the [NavigationMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_NavigationMode) property. [NavigationMode.Cell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.NavigationMode.html#Syncfusion_UI_Xaml_Grids_NavigationMode_Cell) allows you navigate between the cells in a row and navigate between rows. [NavigationMode.Row](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.NavigationMode.html#Syncfusion_UI_Xaml_Grids_NavigationMode_Row) allows you navigate only between rows.

## Selection modes

The [SelectionMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectionMode) property defines the behavior of selection in tree grid. If `SelectionMode` is [Single](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionMode.html#Syncfusion_UI_Xaml_Grids_GridSelectionMode_Single), you can select a single row, and if the `SelectionMode` is [Extended](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionMode.html#Syncfusion_UI_Xaml_Grids_GridSelectionMode_Extended) or [Multiple](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionMode.html#Syncfusion_UI_Xaml_Grids_GridSelectionMode_Multiple), you can select multiple rows. If you want to disable the selection, set `SelectionMode` to [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionMode.html#Syncfusion_UI_Xaml_Grids_GridSelectionMode_None).

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"
                                       AutoExpandMode="RootNodesExpanded"
                                       AutoGenerateColumns="False" 
                                       NavigationMode="Row"
                                       ChildPropertyName="Children"
                                       SelectionMode="Single"
                                       ColumnSizer="Star" 
                                       ExpanderColumn="FirstName"
                                       ItemsSource="{Binding PersonDetails}"
                                       >
{% endhighlight %}
{% endtabs %}

![Row selected in WinUI treegrid](Selection_images/Selection_img1.jpeg)

## Disable selection for rows and columns

You can disable selection and navigation on particular column by setting the [GridColumn.AllowFocus](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_AllowFocus) property. You can disable selection on particular row or column by handling the [CurrentCellActivating](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html) event.

## Multiple row selection

The tree grid allows you select multiple rows by setting the `SelectionMode` property to `Extended` or `Multiple`, where you can select multiple rows by mouse click and also using the key modifiers.

When using `Extended`, you can select multiple rows by pressing the key modifiers `Ctrl` and `Shift`.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"
                                       AutoExpandMode="RootNodesExpanded"
                                       AutoGenerateColumns="False" 
                                       NavigationMode="Row"
                                       ChildPropertyName="Children"
                                       SelectionMode="Extended"
                                       ColumnSizer="Star" 
                                       ExpanderColumn="FirstName"
                                       ItemsSource="{Binding PersonDetails}"
                                       >
{% endhighlight %}
{% endtabs %}

![Multiple rows selected in WinUI treegrid](Selection_images/Selection_img2.jpeg)

N> When `SelectionMode` is `Multiple`, you can select or deselect multiple rows by clicking the respective row. In multiple selection, pressing the navigation keys moves only the current cell, and you can select or deselect by pressing the `Space` key.

## Get selected rows

The [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedItem) property returns the data object of the selected row, and the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedIndex) property returns the index of the `SelectedItem` in tree grid. The `SelectedItem` denotes the first selected row in multiple selection.

The [CurrentItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentItem) returns the data object that currently has focus, and the [CurrentColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentColumn) denotes the [TreeGridColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridColumn.html) that currently has focus.

### Row selection

You can get all the selected records using the [SelectedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedItems) property, and you can also get all the selected rows information using [SfTreeGrid.SelectionController.SelectedRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridBaseSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridBaseSelectionController_SelectedRows), which is a collection of [TreeGridRowInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowInfo.html).

### CurrentItem vs SelectedItem

Both [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedItem) and `CurrentItem` return the same data object when a single row is selected in tree grid. When you select more than one rows or cells, the record that had been selected initially is maintained in `SelectedItem`, and the record that currently has focus is maintained in `CurrentItem`.

## Programmatic selection

### Process selection using properties

You can select a single row by setting the `SelectedItem` property or [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedIndex) property.

{% tabs %}
{% highlight c# %}

var recordIndex = this.sfTreeGrid.ResolveToNodeIndex(6);
this.sfTreeGrid.SelectedIndex = recordIndex;

{% endhighlight %}
{% highlight c# %}

var node = this.sfTreeGrid.GetNodeAtRowIndex(6);
this.sfTreeGrid.SelectedItem = node.Item;

{% endhighlight %}
{% endtabs %}

In row selection, you can select multiple rows by adding data objects to the `SelectedItems` property.

{% tabs %}
{% highlight c# %}
var viewModel = this.sfTreeGrid.DataContext as ViewModel;

foreach (var order in viewModel.PersonDetails)
{
    if (order.LastName == "Buchanan")
        this.sfTreeGrid.SelectedItems.Add(order);
}
{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows row with LastName as Buchanan added to SelectedItems collection](Selection_images/Selection_img3.jpeg)

### Process selection using methods

You can select a range of rows using the [SelectRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectRows_System_Int32_System_Int32_) method in row selection.

{% tabs %}
{% highlight c# %}

this.sfTreeGrid.SelectRows(3, 7);

{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with rows from 3 to 7 are selected](Selection_images/Selection_img4.jpeg)

### Process current cell

When you set [CurrentItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentItem) to a particular record, the [CurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_CurrentCell) will be moved to the corresponding record. When `SelectionMode` is `Multiple` or `Extended`, the selection will added to a particular record item. When `SelectionMode` is `Single`, the selection will added to a single cell.

You can move the `CurrentCell` to a particular rowColumnIndex using the [MoveCurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowSelectionController_MoveCurrentCell_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_System_Boolean_) method.

{% tabs %}
{% highlight c# %}

this.sfTreeGrid.SelectionController.MoveCurrentCell(new RowColumnIndex(3, 2), false);

{% endhighlight %}
{% endtabs %}

### Clear selection

You can clear the selection using the [ClearSelections](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfDataGrid.html#Syncfusion_UI_Xaml_Grid_SfDataGrid_ClearSelections_System_Boolean_) method. In row selection, you can remove the selection by setting null to the `SelectedItem` or clearing the `SelectedItems` property.

{% tabs %}
{% highlight c# %}

this.sfTreeGrid.SelectionController.ClearSelections(true);

{% endhighlight %}
{% endtabs %}

## Scrolling rows and columns

### Automatic scrolling on drag selection

SfTreeGrid scrolls rows and columns automatically when you try to perform the drag selection like in Excel. You can enable or disable AutoScrolling by setting the [AutoScroller.AutoScrolling](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridAutoScroller.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridAutoScroller_AutoScrolling) property.

{% tabs %}
{% highlight c# %}

this.sfTreeGrid.AutoScroller.AutoScrolling = AutoScrollOrientation.Both;

{% endhighlight %}
{% endtabs %}

### Scroll to a particular row or column index

You can scroll programmatically to particular cell using the [ScrollInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_ScrollInView_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_) method by passing row and column index.

{% tabs %}
{% highlight c# %}

this.sfTreeGrid.ScrollInView(new RowColumnIndex(10, 5));

{% endhighlight %}
{% endtabs %}

### Scroll to selected item

You can scroll programmatically to the `SelectedItem` using the `ScrollInView` method.

{% tabs %}
{% highlight c# %}

var rowIndex = this.sfTreeGrid.ResolveToRowIndex(this.sfTreeGrid.SelectedItem);
var columnIndex = this.sfTreeGrid.ResolveToStartColumnIndex();
this.sfTreeGrid.ScrollInView(new RowColumnIndex(rowIndex, columnIndex));

{% endhighlight %}
{% endtabs %}

## Mouse and keyboard behaviors

### Keyboard behavior

<table>
<tr>
<td>
{{'**Key or Key combinations**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
<kbd>DownArrow</kbd>

</td>
<td>
Moves CurrentCell directly below the active current cell. If the CurrentCell is in the last row, pressing the <kbd>DownArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>UpArrow</kbd>

</td>
<td>
Moves the CurrentCell directly above the active current cell. If the CurrentCell is in the first row, pressing the <kbd>UpArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>LeftArrow</kbd>

</td>
<td>
Moves the current cell to previous to the active current cell. If the CurrentCell is in the first cell, pressing the <kbd>LeftArrow</kbd> does nothing. If the focused row is group header, the group will be collapsed when it is in expanded state.
</td>
</tr>
<tr>
<td>
<kbd>RightArrow</kbd>

</td>
<td>
Moves the current cell to next to the active current cell. If the CurrentCell is in the last cell, pressing the <kbd>RightArrow</kbd> does nothing. If the focused row is group header, the group will be expanded when it is in collapsed state.
</td>
</tr>
<tr>
<td>
<kbd>Home</kbd> / <kbd>Ctrl</kbd> + <kbd>LeftArrow</kbd>

</td>
<td>
Moves the current cell to the first cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>End</kbd> / <kbd>Ctrl</kbd> + <kbd>RightArrow</kbd>

</td>
<td>
Moves the current cell to the last cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>PageDown</kbd>

</td>
<td>
The tree grid will be scrolled to the next set of rows that is not displayed in view, including the row that is partially displayed, and the current cell is set to the last row.
</td>
</tr>
<tr>
<td>
<kbd>PageUp</kbd>

</td>
<td>
The tree grid will be scrolled to the previous set of rows that is not displayed in view, including the row that is partially displayed, and the current cell is set to the first row.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>

</td>
<td>
Moves the current cell to next to the active current cell. If the active current cell is the last cell of the current row, the focus will be moved to the first cell of the row next to the current row. If the active current cell is the last cell of the last row, the focus will be moved to next control in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Tab</kbd>

</td>
<td>
Moves the current cell to previous cell to the active current cell. If the active current cell is the first cell of the current row, the current cell will be moved to the last cell of the row previous to the current row. If the active current cell is the first cell of the first row, the focus will be moved to the previous control in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>DownArrow</kbd>

</td>
<td>
Moves the current cell to the current column of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>UpArrow</kbd>

</td>
<td>
Moves the current cell to the current column of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>Home</kbd>

</td>
<td>
Moves the current cell to the first cell of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>End</kbd>

</td>
<td>
Moves the current cell to the last cell of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>

</td>
<td>
If the active current cell is in edit mode, the changes will be committed, and moves the current cell to below the active current cell. If the active current cell is in the last row, commits changes only and retains the same cell.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>Enter</kbd>

</td>
<td>
Commits only the changes when the current cell is in edit mode and retains the focus in same cell.
</td>
</tr>
<tr>
<td>
<kbd>F2</kbd>

</td>
<td>
If the {{'[TreeGrid.AllowEditing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_AllowEditing)'| markdownify }} property is <kbd>true</kbd>, and the 
{{'[GridColumn.AllowEditing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_AllowEditing)'| markdownify }} property is <kbd>true</kbd> for the current column, the current cell enters into edit mode.
</td>
</tr>
<tr>
<td>
<kbd>Esc</kbd>
</td>
<td>
If the current cell is in edit mode, reverts the changes that had been done in the current cell. If the underlying source implements {{'[IEditableObject](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject#%22%22"")'| markdownify }}, clicking the <kbd>Esc</kbd> key for the second time cancels the edit mode for entire row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>A</kbd>
</td>
<td>
All rows or cells will be selected.
</td>
</tr>
</table>

### Shift key combinations

When `SelectionMode` is set to `Extended`, you can select multiple rows using the navigation keys along with the <kbd>Shift</kbd> key. Before starting navigation, the current cell will be marked as a pressed cell, and the selection will be done in all rows between the pressed cell and current cell.

<table>
<tr>
<td>
{{'**Key combinations**'| markdownify }}
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>DownArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>UpArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>LeftArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Home</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>End</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>PageDown</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>PageUp</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>DownArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>UpArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>RightArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>LeftArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>Home</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>End</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>PageDown</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>PageUp</kbd>
</td>
</tr>
</table>

### Mouse behavior

You can enable or disable the selection when the mouse button is in the pressed state by setting the [AllowSelectionOnPointerPressed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_AllowSelectionOnPointerPressed) property.

When `SelectionMode` is set to `Extended`, you can select multiple rows by clicking any cell along with `Ctrl` and `Shift` keys. When you click a cell along with `Ctrl` key, you can select or deselect a particular row. When you click a cell along with `Shift` key, you can select the range rows from the pressed cell to the current cell.

### Customize mouse and keyboard behaviors

You can customize the mouse and keyboard behaviors by overriding the selection controller. Refer to the [Customizing Selection Behaviors](https://help.syncfusion.com/winui/treegrid/selection#customize-selection-behaviors) section to learn about override the selection controller.

## Events

### CurrentCellActivating

The [CurrentCellActivating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellActivating) event will occurs before moving the current cell to particular cell. [CurrentCellActivatingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs.html) has following members which provides information for `CurrentCellActivating` event.

* [ActivationTrigger](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatingEventArgs_ActivationTrigger) - Returns the reason for moving the current cell.

* [CurrentRowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatingEventArgs_ActivationTrigger) - [RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.ScrollAxis.RowColumnIndex.html) of the cell where the current cell need to move.

*  [PreviousRowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatingEventArgs_PreviousRowColumnIndex) - `RowColumnIndex` of the cell from where the current cell moved.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"                       
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"      
                       ChildPropertyName="Children"		
                       ColumnSizer="Star" 
                       ExpanderColumn="FirstName"					   
                       CurrentCellActivating="sfTreeGrid_CurrentCellActivating"                        
                       ItemsSource="{Binding PersonDetails}"
                       LiveNodeUpdateMode="AllowDataShaping">
                                                                                                          
{% endhighlight %}
{% highlight c# %}

this.sfTreeGrid.CurrentCellActivating += sfTreeGrid_CurrentCellActivating;

private void sfTreeGrid_CurrentCellActivating(object sender, Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs e)
{
           
}
{% endhighlight %}
{% endtabs %}

You can cancel the current cell moving process within this event by setting [GridCurrentCellActivatingEventArgs.Cancel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs.html) to true.

{% tabs %}
{% highlight c# %}
private void sfTreeGrid_CurrentCellActivating(object sender, Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatingEventArgs e)
{
    var provider = this.sfTreeGrid.View.GetPropertyAccessProvider();
    var record = this.sfTreeGrid.GetNodeAtRowIndex(e.CurrentRowColumnIndex.RowIndex).Item;

    if (record == null)
        return;

    var column = this.sfTreeGrid.Columns[this.sfTreeGrid.ResolveToGridVisibleColumnIndex(e.CurrentRowColumnIndex.ColumnIndex)];
    var cellValue = provider.GetValue(record, column.MappingName);

    if (cellValue.ToString() == "1001")
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

### CurrentCellActivated

The [CurrentCellActivated](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellActivated) event occurs after the current cell moves to the corresponding cell. [CurrentCellActivatedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatedEventArgs.html) has the following members, which provide information to the `CurrentCellActivated` event:


* [ActivationTrigger ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatedEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatedEventArgs_ActivationTrigger) - Returns the reason of the current cell movement.

* [CurrentRowColumnIndex ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatedEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatedEventArgs_CurrentRowColumnIndex) - `RowColumnIndex` of the cell where the current cell move.

* [PreviousRowColumnIndex ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatedEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellActivatedEventArgs_PreviousRowColumnIndex) - `RowColumnIndex` of the cell where the current cell moved.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"                       
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"                       
                       ChildPropertyName="Children"
                       ColumnSizer="Star" 
                       ExpanderColumn="FirstName"			           
                       CurrentCellActivated="sfTreeGrid_CurrentCellActivated"                                              
                       ItemsSource="{Binding PersonDetails}"
                       LiveNodeUpdateMode="AllowDataShaping">

{% endhighlight %}
{% highlight c# %}

this.sfTreeGrid.CurrentCellActivated += sfTreeGrid_CurrentCellActivated;

private void sfTreeGrid_CurrentCellActivated(object sender, Syncfusion.UI.Xaml.DataGrid.CurrentCellActivatedEventArgs e)
{

}
{% endhighlight %}
{% endtabs %}

### SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectionChanging) event occurs before processing the selection to a particular row or cell. This event is triggered only to the keyboard and mouse interactions. [GridSelectionChangingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangingEventArgs.html) has the following members, which provide information to the `SelectionChanging` event.

* [AddedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Grids_GridSelectionChangingEventArgs_AddedItems) - Collection of [GridRowInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowInfo.html) where the selection is going to be processed.

* [RemovedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Grids_GridSelectionChangingEventArgs_RemovedItems) - Collection of `GridRowInfo` where the selection is going to be removed.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"                       
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"                     
                       ChildPropertyName="Children"
                       ColumnSizer="Star" 
                       ExpanderColumn="FirstName"			           				  
                       SelectionChanging="sfTreeGrid_SelectionChanging"                       
                       ItemsSource="{Binding PersonDetails}"	
                       LiveNodeUpdateMode="AllowDataShaping">

{% endhighlight %}
{% highlight c# %}

this.sfTreeGrid.SelectionChanging += sfTreeGrid_SelectionChanging;

private void sfTreeGrid_SelectionChanging(object sender, Syncfusion.UI.Xaml.Grids.GridSelectionChangingEventArgs e)
{
            
}
{% endhighlight %}
{% endtabs %}

### SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectionChanged) event occurs after the selection process is completed for a particular row or cell in tree grid. [GridSelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangedEventArgs.html) has the following members, which provide information to the SelectionChanged event:

* [AddedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Grids_GridSelectionChangedEventArgs_AddedItems) - Collection of `GridRowInfo` where the selection has been processed.

* [RemovedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Grids_GridSelectionChangedEventArgs_RemovedItems) - Collection of `GridRowInfo` where the selection has been removed.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"
                       Grid.Row="0"
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"                   
                       ChildPropertyName="Children"
                       ColumnSizer="Star" 
                       ExpanderColumn="FirstName"			           
                       SelectionChanged="sfTreeGrid_SelectionChanged"                       
                       ItemsSource="{Binding PersonDetails}"					   
                       LiveNodeUpdateMode="AllowDataShaping">

{% endhighlight %}
{% highlight c# %}

this.sfTreeGrid.SelectionChanged += sfTreeGrid_SelectionChanged;

private void sfTreeGrid_SelectionChanged(object sender, Syncfusion.UI.Xaml.Grids.GridSelectionChangedEventArgs e)
{
           
}
{% endhighlight %}
{% endtabs %}

## Appearance

### Change selection background and foreground

You can change the selection background and foreground using the [SelectionBackGround](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectionBackground) and [SelectionForeGround](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectionForeground) properties.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"                                           
                                           AutoExpandMode="RootNodesExpanded"
                                           AutoGenerateColumns="False"
                                           SelectionMode="Multiple"
                                           ChildPropertyName="Children"
                                           ColumnSizer="Star" 
                                           ExpanderColumn="FirstName"
                                           ItemsSource="{Binding PersonDetails}"
                                           SelectionBackground="SkyBlue"                                                    
                                           SelectionForeground="DarkBlue"
                                         >
{% endhighlight %}
{% endtabs %}

![Background and foreground of the selected rows are changed in WinUI treegrid](Selection_images/Selection_img5.jpeg)

### Change current cell border style

You can change the current cell border thickness and border color using the [CurrentCellBorderThickness](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_CurrentCellBorderThickness) and [CurrentCellBorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_CurrentCellBorderBrush) properties.

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="sfTreeGrid"                                           
                                           AutoExpandMode="RootNodesExpanded"
                                           AutoGenerateColumns="False"
                                           SelectionMode="Multiple"
                                           ChildPropertyName="Children"
                                           ColumnSizer="Star" 
                                           ExpanderColumn="FirstName"
                                           ItemsSource="{Binding PersonDetails}"
                                           LiveNodeUpdateMode="AllowDataShaping"                                           
                                           CurrentCellBorderBrush="Red"
                                           CurrentCellBorderThickness="1.6"
                                         >
{% endhighlight %}
{% endtabs %}

![Style of current cell border is customized in WinUI treegrid](Selection_images/Selection_img6.jpeg)

### Customize row selection border

You can customize the row selection by editing the control template of [TreeGridRowControl](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowControl.html).

{% tabs %}
{% highlight xaml %}
<Style TargetType="syncfusion:TreeGridRowControl">
            <Setter Property="Background" Value="Transparent" />
            <Setter Property="BorderBrush" Value="#33000000" />
            <Setter Property="Foreground" Value="#FF000000"/>
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="treeGrid:TreeGridRowControl">
                        <Grid BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
                            <VisualStateManager.VisualStateGroups>
                                <VisualStateGroup x:Name="SelectionStates">
                                    <VisualState x:Name="Unselected" />
                                    <VisualState x:Name="Selected">
                                        <VisualState.Setters>
                                            <Setter Target="PART_SelectionBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                    <VisualState x:Name="SelectedPointerOver">
                                        <VisualState.Setters>
                                            <Setter Target="PART_SelectionBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                    <VisualState x:Name="SelectedPressed">
                                        <VisualState.Setters>
                                            <Setter Target="PART_SelectionBorder.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>

                                    <VisualState x:Name="UnselectedPointerOver" />
                                    <VisualState x:Name="UnselectedPressed" />
                                    <VisualState x:Name="Focused">
                                        <VisualState.Setters>
                                            <Setter Target="PART_FocusRect.Visibility" Value="Visible" />
                                        </VisualState.Setters>
                                    </VisualState>
                                </VisualStateGroup>
                            </VisualStateManager.VisualStateGroups>
                            <Border x:Name="PART_BackgroundBorder"
                                Margin="{TemplateBinding IndentMargin}"
                                Background="Transparent"
                                Visibility="Visible">
                                <Rectangle x:Name="PART_FocusRect"
                                       Margin="1,2,2,2"
                                       Fill="Transparent"
                                       Stroke="DarkGray"
                                       StrokeDashArray="2,2"
                                       StrokeThickness="1"
                                       Visibility="Collapsed" />
                            </Border>
                             <!--Adding new border to show border for whole selected row--> 
                            <Border x:Name="PART_SelectionBorder"
                                Margin="{TemplateBinding IndentMargin}"
                                Background="{TemplateBinding SelectionBackground}"
                                Visibility="Collapsed"                                     
                                BorderBrush="Red"
                                BorderThickness="1.5,1.5,1.5,2.5"
                                Opacity="0.75"/>
                            <ContentPresenter />
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
{% endhighlight %}
{% endtabs %}

![Customization of row selection border in WinUI treegrid](Selection_images/Selection_img7.jpeg)

## Customize selection behaviors

The tree grid processes the selection operations in selection controller. [TreeGridRowSelectionController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html) processes selection operations when selection unit is row.
You can customize the default row selection behaviors by overriding the `TreeGridRowSelectionController` class and set it to [SfTreeGrid.SelectionController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_SelectionController).

{% tabs %}
{% highlight c# %}
this.sfTreeGrid.SelectionController = new GridSelectionControllerExt(this.sfTreeGrid);
public class GridSelectionControllerExt : TreeGridRowSelectionController
{
    public GridSelectionControllerExt(SfTreeGrid treeGrid) : base(treeGrid)
    {
    }
}
{% endhighlight %}
{% endtabs %}

### Scroll and select the record programmatically

You can scroll to the record programmatically using the [ScrollInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_ScrollInView_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_) method by passing the row index of the record. You can get the row index of the record using the [ResolveToRowIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridIndexResolver.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridIndexResolver_ResolveToRowIndex_Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_Syncfusion_UI_Xaml_TreeGrid_TreeNode_) extension method present in `Syncfusion.UI.Xaml.TreeGrid.Helpers`.

You can select the record programmatically by setting the `SelectedItem` property in tree grid.

{% tabs %}
{% highlight c# %}
private void sfTreegrid_Loaded(object sender, System.Windows.RoutedEventArgs e)
{
    var selectedItem = (this.sfTreeGrid.DataContext as ViewModel).SelectedItem;
    var rowindex = this.sfTreeGrid.ResolveToRowIndex(selectedItem);
    var columnindex = this.sfTreeGrid.ResolveToStartColumnIndex();
    //Make the row in to available on the view. 
    this.sfTreeGrid.ScrollInView(new RowColumnIndex(rowindex, columnindex));
    //Set the SelectedItem in SfTreeGrid.
    this.sfTreeGrid.SelectedItem = selectedItem;
}
{% endhighlight %}
{% endtabs %}

### Prevent the selection when right-click

You can prevent the selection when right-clicking in tree grid by customizing the `TreeGridRowSelectionController` and overriding the [ProcessPointerPressed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowSelectionController_ProcessPointerPressed_Microsoft_UI_Xaml_Input_PointerRoutedEventArgs_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_).

{% tabs %}
{% highlight c# %}
protected override void ProcessPointerPressed(PointerRoutedEventArgs args, RowColumnIndex rowColumnIndex)
{
    var properties = args.GetCurrentPoint(TreeGrid).Properties;
    if (properties.IsRightButtonPressed)
    {
        args.Handled = false;
    }
    else
        base.ProcessPointerPressed(args, rowColumnIndex);
}
{% endhighlight %}
{% endtabs %}

### Select the rows based on cell value

In tree grid, you can select the rows based on cell value by adding the corresponding records to `SelectedItems`. You can get the cell value of a particular cell using the [View.GetPropertyAccessProvider](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridView.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridView_GetPropertyAccessProvider) method.

{% tabs %}
{% highlight c# %}
private void Button_Click(object sender, RoutedEventArgs e)
{    
    var reflector = sfTreeGrid.View.GetPropertyAccessProvider();

    var totalRowIndex = sfTreeGrid.View.Nodes.Count;
    var totalColumnIndex = sfTreeGrid.Columns.Count;

    for (int recordIndex = 0; recordIndex < totalRowIndex; recordIndex++)
    {
        for (int colindex = 0; colindex < totalColumnIndex; colindex++)
        {
            var record = this.sfTreeGrid.View.Nodes[recordIndex];
            var mappingName = sfTreeGrid.Columns[colindex].MappingName;
            //Get the cell value based on mappingName.
            var currentCellValue = reflector.GetValue(record.Item, mappingName);
            if (currentCellValue == "Steven")
            {
                object node = sfTreeGrid.View.Nodes[recordIndex];
                //selected rows should be added here.
                sfTreeGrid.SelectedItems.Add((node as TreeNode).Item);
            }
        }
    }
}
{% endhighlight %}
{% endtabs %}

### Search and select the record

You can search and select a record in tree grid based on the searched text using the TextChanged event of TextBox.

{% tabs %}
{% highlight c# %}
private void TextBox_TextChanged(object sender, System.Windows.Controls.TextChangedEventArgs e)
{
    var textBox = sender as TextBox;
    var treeGrid = this.sfTreeGrid;
    if (textBox.Text == "")
        treeGrid.SelectedItems.Clear();

    for (int i = 0; i < treeGrid.View.Nodes.Count; i++)
    {
        if (Provider == null)
            Provider = treeGrid.View.GetPropertyAccessProvider();

        if (treeGrid.View.Nodes[i].HasChildNodes && treeGrid.View.Nodes[i].ChildNodes.Count == 0)
        {            
            treeGrid.ExpandNode(treeGrid.View.Nodes[i]);
            treeGrid.CollapseNode(treeGrid.View.Nodes[i]);         
        }
        else if (treeGrid.View.Nodes[i].HasChildNodes)
        {                    
            dataRow = (treeGrid.View.Nodes[i].Item as EmployeeInfo);
            FindMatchText(dataRow);
            GetChildNodes(treeGrid.View.Nodes[i]);
        }
        else
        {
            dataRow=(treeGrid.View.Nodes[i].Item as EmployeeInfo);
            FindMatchText(dataRow);
        }
    }
}
{% endhighlight %}
{% endtabs %}

N> View sample in [GitHub](https://github.com/SyncfusionExamples/How-to-search-and-select-the-record-in-winui-treegrid)

### Read cell values from selected items

You can get the cell values of `SelectedItems` using `SfTreeGrid.SelectedItems` and internal reflector, which reflects the field value from data object based on field name.

{% tabs %}
{% highlight c# %}
private void Button_Click(object sender, RoutedEventArgs e)
{
    listBox.Items.Clear();
    // Get the selected items of SfTreeGrid
    var reflector = this.sfTreeGrid.View.GetPropertyAccessProvider();
    foreach (var row in this.sfTreeGrid.SelectedItems)
    {
        foreach (var column in sfTreeGrid.Columns)
        {
            //Get the value from data object based on MappingName 
            var cellvalue = reflector.GetValue(row, column.MappingName);
            //Returns the display value of the cell from data object based on MappingName             
            listBox.Items.Add(cellvalue.ToString());
        }
    }
}
{% endhighlight %}
{% endtabs %}

### Show the selection of row/cell when setting the background

The `Row`/`Cell` selection border is behind the grid cell content. So, when you apply the background for a row, the selection is not displayed in `UI`. You can overcome this by setting opacity in [TreeGridCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCell.html).

{% tabs %}
{% highlight xaml %}
<Style TargetType="treeGrid:TreeGridCell">
    <Setter Property="Background">
        <Setter.Value>
            <SolidColorBrush Color="Blue" Opacity="0.5"/>
        </Setter.Value>
    </Setter>
</Style>
{% endhighlight %}
{% endtabs %}

### Set the current cell on a particular row when tree grid is loaded

You can set the current cell in tree grid using the [treeGrid.SelectionController.MoveCurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowSelectionController_MoveCurrentCell_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_System_Boolean_) method.

{% tabs %}
{% highlight c# %}
private void sfTreeGrid_Loaded(object sender, RoutedEventArgs e)
{
    var viewModel = this.sfTreeGrid.DataContext as ViewModel;
    //find the RowIndex for particular record
    var RowIndex = this.sfTreeGrid.ResolveToRowIndex(viewModel.EmployeeInfo[2]);
    // find the ColumnIndex for that row.
    var ColumnIndex = this.sfTreeGrid.ResolveToScrollColumnIndex(1);
    // CurrentCell is set if MappingName is EmployeeID
    if (this.sfTreeGrid.Columns[ColumnIndex].MappingName == "EmployeeID")
        this.sfTreeGrid.SelectionController.MoveCurrentCell(new RowColumnIndex(RowIndex, ColumnIndex));
}
{% endhighlight %}
{% endtabs %}
