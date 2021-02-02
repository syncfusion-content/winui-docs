---
layout: post
title: Clipboard operations | TreeGrid | WinUI | Syncfusion
description: Learn about the clipboard operations in Syncfusion WinUI TreeGrid ( SfTreeGrid ) control and more details.
platform: winui
control: SfTreeGrid
documentation: ug
---

# Clipboard operations in Syncfusion WinUI TreeGrid

SfTreeGrid provides support to the clipboard operations such as cut, copy, and paste the data within control and between other applications such as Notepad and Excel. The clipboard operations of copy and paste are enabled by default. You can copy the selected nodes/cells from tree grid by clicking `Ctrl+C` and can paste the content from [Clipboard](https://msdn.microsoft.com/en-us/library/system.windows.clipboard.aspx) to tree grid by clicking `Ctrl+V`.

## Copy

The copy operation works based on the [CopyOption](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_CopyOption) property.

GridCopyOption provides the following options:

* [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_None): Disables copy in tree grid.

* [CopyData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_CopyData): Enables copy in tree grid.

* [CutData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_CutData): Enables cut in tree grid.

* [IncludeHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeHeaders): Copies column header along with data.

* [IncludeFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeFormat): Copies the display text with format instead of actual value.

* [IncludeHiddenColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeHiddenColumn): Copies hidden column to clipboard.

You can use the IncludeHeaders, IncludeFormat, and IncludeHiddenColumn options along with the CopyData option.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid
                Name="treeGrid"
                CopyOption="CopyData,IncludeHeaders"
                AllowFiltering="True"
                AutoExpandMode="RootNodesExpanded"
                AutoGenerateColumns="False"
                ChildPropertyName="Children"
                ColumnWidthMode="Star"                       
                ExpanderColumn="FirstName"
                ItemsSource="{Binding Persons}" />
{% endhighlight %}
{% highlight c# %}

this.treeGrid.CopyOption = GridCopyOptions.CopyData | GridCopyOptions.IncludeHeaders;

{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Copied content pasted in notepad](Clipboard-Operations-images/Clipboard-Operations-img1.png)

## Paste

The paste operation works based on the [PasteOption](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_PasteOption) property.

GridPasteOption provides the following options:

* [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridPasteOptions.html#Syncfusion_UI_Xaml_Grids_GridPasteOptions_None): Disables paste in tree grid.

* [PasteData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridPasteOptions.html#Syncfusion_UI_Xaml_Grids_GridPasteOptions_PasteData): Enables paste in tree grid. When an incompatible value is pasted into a record/cell, the pasting operation is skipped for that particular record/cell.

* [ExcludeFirstLine](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridPasteOptions.html#Syncfusion_UI_Xaml_Grids_GridPasteOptions_ExcludeFirstLine): Pastes data copied with `IncludeHeaders` copy option.

* [IncludeHiddenColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridPasteOptions.html#Syncfusion_UI_Xaml_Grids_GridPasteOptions_IncludeHiddenColumn): Pastes the values in hidden columns also.

You can use the ExcludeFirstLine and IncludeHiddenColumn options along with the PasteData option.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid
                Name="treeGrid"
                CopyOption="CopyData,IncludeHeaders"
                PasteOption="PasteData,ExcludeFirstLine"
                AllowFiltering="True"
                AutoExpandMode="RootNodesExpanded"
                AutoGenerateColumns="False"
                ChildPropertyName="Children"
                ColumnWidthMode="Star"                       
                ExpanderColumn="FirstName"
                ItemsSource="{Binding Persons}" />

{% endhighlight %}
{% highlight c# %}
this.treeGrid.CopyOption = GridCopyOptions.CopyData | GridCopyOptions.IncludeHeaders;

this.treeGrid.PasteOption = GridPasteOptions.PasteData | GridPasteOptions.ExcludeFirstLine;


{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Copied record pasted in new record](Clipboard-Operations-images/Clipboard-Operations-img2.png)

## Cut

The cut operation works based on the [CopyOption](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_CopyOption) property.

GridCopyOption provides the following options:

* [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_None): Disables copy in tree grid.

* [CutData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_CutData): Enables cut in tree grid.

* [IncludeHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeHeaders): Copies column header along with data.

* [IncludeFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeFormat): Copies the display text with format instead of actual value.

* [IncludeHiddenColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyOptions.html#Syncfusion_UI_Xaml_Grids_GridCopyOptions_IncludeHiddenColumn): Copies hidden column to clipboard.

You can use the IncludeHeaders, IncludeFormat, and IncludeHiddenColumn options along with CutData option.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid
                Name="treeGrid"
                CopyOption="CutData,IncludeHeaders" 
                AllowFiltering="True"
                AutoExpandMode="RootNodesExpanded"
                AutoGenerateColumns="False"
                ChildPropertyName="Children"
                ColumnWidthMode="Star"                       
                ExpanderColumn="FirstName"
                ItemsSource="{Binding Persons}" />

{% endhighlight %}
{% highlight c# %}
this.treeGrid.CopyOption = GridCopyOptions.CutData | GridCopyOptions.IncludeHeaders;
{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Data from the record is cut and pasted in notepad](Clipboard-Operations-images/Clipboard-Operations-img3.png)

## Events

### CopyContent

The [CopyContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CopyContent) event occurs when copy/cut the cells in tree grid. [GridCopyPasteEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyPasteEventArgs.html) provides information for to the `CopyContent` event. You can cancel copy operation by handling this event.

{% tabs %}
{% highlight c# %}
this.treeGrid.CopyContent += TreeGrid_CopyContent;

private void TreeGrid_CopyContent(object sender, GridCopyPasteEventArgs e)
{
    if (((e.OriginalSender as SfTreeGrid).SelectedItem as Person).Id == 11110)
        e.Handled = true;
}

{% endhighlight %}
{% endtabs %}

### PasteContent

The [PasteContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_PasteContent) event occurs when paste the clipboard value into tree grid. [GridCopyPasteEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridCopyPasteEventArgs.html) provides information to the PasteContent event. You can cancel the paste operation by handling this event.

{% tabs %}
{% highlight c# %}
this.treeGrid.PasteContent += TreeGrid_PasteContent;

private void TreeGrid_PasteContent(object sender, GridCopyPasteEventArgs e)
{
    if (((e.OriginalSender as SfTreeGrid).SelectedItem as Person).Id == 11110)
        e.Handled = true;
}


{% endhighlight %}
{% endtabs %}

### CopyCellContent

The [CopyCellContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CopyCellContent) event occurs when a cell is being copied/cut. [TreeGridCopyPasteCellEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html) provides information to the CopyGridCellContent event, which has the following members:

* [ClipBoardValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_ClipBoardValue): Returns cell value.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_Column): Returns corresponding GridColumn of a cell.

* [RowData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_RowData): Returns corresponding RowData of a cell.

* [OriginalSender](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_RowData): Returns SfTreeGrid.


You can change the text copied to clipboard by changing the ClipBoardValue.

{% tabs %}
{% highlight c# %}
this.treeGrid.CopyCellContent += TreeGrid_CopyCellContent;

private void TreeGrid_CopyCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
            
}

{% endhighlight %}
{% endtabs %}

The following code example changes the clipboard value to 100 instead of cell value 1005 in tree grid.

{% tabs %}
{% highlight c# %}
private void TreeGrid_CopyCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
    if (e.Column.MappingName == "OrderID" && (e.RowData as OrderDetails).OrderID == 1005)
        e.ClipBoardValue = 100;
}
{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Copied data customized through CopyCellContent event](Clipboard-Operations-images/Clipboard-Operations-img4.png)

The following code example demonstrates how to handle the copy operation when MappingName of a Column is Id.

{% tabs %}
{% highlight c# %}
private void TreeGrid_CopyCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
    if (e.Column.MappingName == "Id")
        e.Handled = true;
}
{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Copy operation for a column handled through CopyCellContent event](Clipboard-Operations-images/Clipboard-Operations-img5.png)

### PasteCellContent

The [PasteGridCellContent](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_PasteCellContent) event occurs when a cell is being pasted. [TreeGridCopyPasteCellEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_ClipBoardValue) provides information to the `PasteGridCellContent` event, which has the following members:

* [ClipBoardValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_ClipBoardValue): Returns cell value.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_Column): Returns corresponding GridColumn of a cell.

* [RowData](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_RowData): Returns corresponding RowData of a cell.

* [OriginalSender](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCopyPasteCellEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCopyPasteCellEventArgs_RowData): Returns SfTreeGrid.

You can paste the text to tree grid by changing the ClipBoardValue.

{% tabs %}
{% highlight c# %}
this.treeGrid.PasteCellContent += TreeGrid_PasteCellContent;

private void TreeGrid_PasteCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
            
}

{% endhighlight %}
{% endtabs %}

The following code example changes the clipboard value to David instead of clipboard value Warner.

{% tabs %}
{% highlight c# %}
private void TreeGrid_PasteCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
    if (e.Column.MappingName == "FirstName" && (e.RowData as Person).FirstName == "Warner")
        e.ClipBoardValue = "David";
}


{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Data of a column customized when pasting through PasteCellContent event](Clipboard-Operations-images/Clipboard-Operations-img6.png)

The following code example demonstrates how to handle the paste operation when MappingName of column is Id.

{% tabs %}
{% highlight c# %}
private void TreeGrid_PasteCellContent(object sender, TreeGridCopyPasteCellEventArgs e)
{
    if (e.Column.MappingName == "Id")
        e.Handled = true;
}


{% endhighlight %}
{% endtabs %}

![WinUI treegrid shows with Paste operation of a column is handled through PasteCellContent event](Clipboard-Operations-images/Clipboard-Operations-img7.png)

## Handle the clipboard operations programmatically

### Copy the node programmatically

Copy the selected nodes in tree grid using the [Copy](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_Copy) method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}

this.treeGrid.TreeGridCopyPaste.Copy();

{% endhighlight %}
{% endtabs %}

Copy a record by selecting the record using the [MoveCurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowSelectionController_MoveCurrentCell_Syncfusion_UI_Xaml_Grids_ScrollAxis_RowColumnIndex_System_Boolean_) method and [Copy](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_Copy) method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
RowColumnIndex rowColumnIndex = new RowColumnIndex();
rowColumnIndex.RowIndex = 2;
rowColumnIndex.ColumnIndex = 2;
this.treeGrid.SelectionController.MoveCurrentCell(rowColumnIndex);
this.treeGrid.ClipboardController.Copy();

{% endhighlight %}
{% endtabs %}

Copy multiple records by selecting a group of records using the SelectRows method and [Copy](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_Copy) method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
this.treeGrid.SelectionController.SelectRows(2, 5);
this.treeGrid.ClipboardController.Copy();

{% endhighlight %}
{% endtabs %}

### Paste to tree grid programmatically

Paste the clipboard value into tree grid using the [Paste](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_Paste) method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
this.treeGrid.ClipboardController.Paste();

{% endhighlight %}
{% endtabs %}

Paste the clipboard value into selected record by selecting the record using the MoveCurrentCell method and `Paste` method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
RowColumnIndex rowColumnIndex = new RowColumnIndex();
rowColumnIndex.RowIndex = 1;
rowColumnIndex.ColumnIndex = 1;
this.treeGrid.SelectionController.MoveCurrentCell(rowColumnIndex);
this.treeGrid.ClipboardController.Paste();

{% endhighlight %}
{% endtabs %}

### Cut from tree grid programmatically

Cut the selected records/cells in tree grid using the [Cut](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_Cut) method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
this.treeGrid.ClipboardController.Cut();
{% endhighlight %}
{% endtabs %}

Cut the entire record in tree grid by selecting whole tree grid using the [SelectAll](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridRowSelectionController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridRowSelectionController_SelectAll) method and `Cut` method in [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) of tree grid.

{% tabs %}
{% highlight c# %}
this.treeGrid.SelectionController.SelectAll();
this.treeGrid.ClipboardController.Cut();
{% endhighlight %}
{% endtabs %}

## Customize copy paste behavior

The tree grid processes the clipboard operations in the [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) class. You can customize the default copy paste behaviors by overriding the TreeGridCutCopyPaste class and set it to `SfTreeGrid.ClipboardController`.

{% tabs %}
{% highlight c# %}
public class CustomClipboardController : TreeGridClipboardController
{
    public CustomClipboardController(SfTreeGrid sfTreeGrid) : base(sfTreeGrid)
    {
    }
}

{% endhighlight %}
{% highlight c# %}
public MainPage()
{
    this.InitializeComponent();
    this.treeGrid.ClipboardController = new CustomClipboardController(this.treeGrid);
}

{% endhighlight %}
{% endtabs %}

### Paste a record into selected rows

By default, you can copy a row and paste it into another row in tree grid. The following code example shows how to copy a row and paste it into all the selected rows by overriding the [PasteRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_PasteRow_System_Object_System_Object_) method in the [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) class.

{% tabs %}
{% highlight c# %}
public class CustomClipboardController : TreeGridClipboardController
{
    SfTreeGrid treeGrid { get; set; }
    public CustomClipboardController(SfTreeGrid sfTreeGrid) : base(sfTreeGrid)
    {
        this.treeGrid = sfTreeGrid;
    }

    protected override void PasteRow(object clipboardContent, object selectedRecords)
    {
        var text = clipboardContent.ToString();
        string[] clipBoardText = Regex.Split(text, @"\r\n");

        //Get the clipBoardText and check if the clipBoardText is more than one row
        //means call the base.
        if (clipBoardText.Count() > 1)
        {
            base.PasteRow(clipboardContent, selectedRecords);
            return;
        }
        var selectedRecord = this.treeGrid.SelectedItems;
        for (int i = 0; i < selectedRecord.Count; i++)
        {
            //Get the selected records for paste the copied row.
            selectedRecords = selectedRecord[i];

            //Call the PasteRow method with clipboardContent and selectedRecords
            base.PasteRow(clipboardContent, selectedRecords);
        }
    }
}

{% endhighlight %}
{% endtabs %}

### Select pasted records

By default, after pasting the clipboard value to tree grid, the selection is maintained in previously selected records. The following code example shows how to select the pasted records by overriding the [PasteRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_PasteRow_System_Object_System_Object_) method in the [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) class.

{% tabs %}
{% highlight c# %}
public class CustomClipboardController : TreeGridClipboardController
{
    SfTreeGrid treeGrid { get; set; }
    public CustomClipboardController(SfTreeGrid sfTreeGrid) : base(sfTreeGrid)
    {
        this.treeGrid = sfTreeGrid;
    }

    protected override void PasteRow(object clipboardcontent, object selectedRecords)
    {
        base.PasteRow(clipboardcontent, selectedRecords);

        // Add the selected record to list.
        this.treeGrid.SelectedItems.Add(selectedRecords);
    }
}

{% endhighlight %}
{% endtabs %}

### Create new records when pasting

By default, when paste the clipboard value to tree grid, it changes the values of the already existing records. The following code example shows how to add the copied records as new rows in tree grid by overriding the [PasteRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_PasteRow_System_Object_System_Object_) method in the [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) class.

{% tabs %}
{% highlight c# %}
public class CustomClipboardController : TreeGridClipboardController
{
    SfTreeGrid treeGrid { get; set; }
    public CustomClipboardController(SfTreeGrid sfTreeGrid) : base(sfTreeGrid)
    {
        this.treeGrid = sfTreeGrid;
    }

    protected override void PasteRows(object clipBoardRows)
    {
        var copiedRecord = (string[])clipBoardRows;
        int copiedRecordsCount = copiedRecord.Count();

        //Based on the clipboard count added the new record for paste
        if (copiedRecordsCount > 0)
        {
            //Get the viewModel for adding the record
            var record = this.treeGrid.DataContext as ViewModel;

            for (int i = 0; i < copiedRecordsCount; i++)
            {
                //Create the new instance for Model, for adding the new record
                EmployeeInfo entity = new EmployeeInfo();

                for (int j = 0; j < this.treeGrid.Columns.Count; j++)
                {
                    string[] values = Regex.Split(copiedRecord[i], @"\t");

                    //Adding the new record by using PasteToCell method by passing the 

                    //created data, particular column, and clipboard value
                    this.PasteCell(entity, this.treeGrid.Columns[j], values[j]);
                }

                //Added the pasted record in collection
                record.Employees.Add(entity);
            }
        }
    }
}

{% endhighlight %}
{% endtabs %}

### Paste data by custom column order

The data can be pasted only from the first column, by default. However, you can paste the copied data anywhere in the grid by deriving a new class from [TreeGridClipboardController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html) and overriding the [PasteRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridClipboardController.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridClipboardController_PasteRow_System_Object_System_Object_) virtual method.

{% tabs %}
{% highlight c# %}
public class CustomClipboardController : TreeGridClipboardController
{
    SfTreeGrid treeGrid { get; set; }
    public CustomClipboardController(SfTreeGrid sfTreeGrid) : base(sfTreeGrid)
    {
        this.treeGrid = sfTreeGrid;
    }

    protected override void PasteRow(object clipboardContent, object selectedRecords)
    {
        // Splits the row into number of cells using \t.
        clipboardContent = Regex.Split(clipboardContent.ToString(), @"\t");
        var copyValue = (string[])clipboardContent;

        int columnIndex = 0;
        //Gets the currentCell column index.
        var index = this.treeGrid.SelectionController.CurrentCellManager.CurrentCell.ColumnIndex;
        foreach (var column in treeGrid.Columns)
        {
            if (index >= treeGrid.Columns.Count)
                return;
            if (copyValue.Count() <= this.treeGrid.Columns.IndexOf(column))
                break;
            // Calls the PasteToCell method and passes the copied data and pastes the column index.
            PasteCell(selectedRecords, this.treeGrid.Columns[index], copyValue[columnIndex]);
            index++;
            columnIndex++;
        }
    }
}

{% endhighlight %}
{% endtabs %}
