---
layout: post
title: Export To Excel in WinUI DataGrid control | Syncfusion
description: Learn here all about Export To Excel support in Syncfusion WinUI DataGrid (SfDataGrid) control and more.
platform: winui
control: DataGrid
documentation: ug
---

# Export To Excel in WinUI DataGrid

The [WinUI DataGrid](https://help.syncfusion.com/winui/datagrid/overview) supports exporting data to excel. Export unbound rows, unbound columns, merged cells, stacked headers, and Details View while exporting.

The following assemblies needs to be added for exporting to excel.

* Syncfusion.GridExport.WinUI
* Syncfusion.XlsIO.NET

For NuGet package, install the [Syncfusion.GridExport.WinUI](https://www.nuget.org/packages/Syncfusion.GridExport.WinUI) package.

Export the SfDataGrid to excel by using the [ExportToExcel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportExtensions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportExtensions_ExportToExcel_Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Syncfusion_UI_Xaml_Data_ICollectionViewAdv_Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_) extension method in the [Syncfusion.UI.Xaml.DataGrid.Export](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.html) namespace.

{% tabs %}
{% highlight c# %}
using Syncfusion.UI.Xaml.DataGrid.Export;
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

async void Save(MemoryStream stream, string filename)
{
    StorageFile stFile;

    if (!(Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.Phone.UI.Input.HardwareButtons")))
    {
        FileSavePicker savePicker = new FileSavePicker();
        savePicker.DefaultFileExtension = ".xlsx";
        savePicker.SuggestedFileName = filename;
        savePicker.FileTypeChoices.Add("Excel Documents", new List<string>() { ".xlsx" });
        var hwnd = System.Diagnostics.Process.GetCurrentProcess().MainWindowHandle;
        WinRT.Interop.InitializeWithWindow.Initialize(savePicker, hwnd);
        stFile = await savePicker.PickSaveFileAsync();
    }
    else
    {
        StorageFolder local = Windows.Storage.ApplicationData.Current.LocalFolder;
        stFile = await local.CreateFileAsync(filename, CreationCollisionOption.ReplaceExisting);
    }
    if (stFile != null)
    {
        using (IRandomAccessStream zipStream = await stFile.OpenAsync(FileAccessMode.ReadWrite))
        {
            //Write the compressed data from the memory to the file
            using (Stream outstream = zipStream.AsStreamForWrite())
            {
                byte[] buffer = stream.ToArray();
                outstream.Write(buffer, 0, buffer.Length);
                outstream.Flush();
            }
        }
        //Launch the saved Excel file.
        await Windows.System.Launcher.LaunchFileAsync(stFile);
    }
}
{% endhighlight %}
{% endtabs %}

N> The SfDataGrid exports data to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). Refer to the [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating the exported worksheets. 

## Excel exporting options

The exporting operation can be customized by passing [DataGridExcelExportOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html) instance as an argument to the [ExportToExcel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportExtensions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportExtensions_ExportToExcel_Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Syncfusion_UI_Xaml_Data_ICollectionViewAdv_Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_) method. 

### Export mode

By default, only the actual value will be exported to excel. To export the display text, set the [ExportMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_ExportMode) property as [Text](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.ExportMode.html#Syncfusion_UI_Xaml_DataGrid_Export_ExportMode_Text). 

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.ExportMode = ExportMode.Text;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Export groups with outlines

By default, all the groups in the DataGrid will be exported in an expanded state. Enable outlines in excel based on the group expanded state by setting the [ShowOutlines](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_ShowOutlines) property as `true` in the [DataGridExcelExportOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.ShowOutlines = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-to-excel.png" alt="Exporting to Excel with Outlines for Groups in WinUI DataGrid" width="100%" Height="Auto"/>

### Exclude columns while exporting

By default, all the columns (including hidden columns) in the SfDataGrid will be exported to Excel. To exclude some columns while exporting to Excel, use the [ExcludedColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_ExcludedColumns) field in the [DataGridExcelExportOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.ExcludedColumns.Add("CustomerName");
options.ExcludedColumns.Add("Country");
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

Here, the columns having the `CustomerName` and `Country` as MappingName are excluded while exporting.

### Excel version

While exporting to Excel, specify the excel version by using the [ExcelVersion](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_ExcelVersion) property.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Exporting stacked headers

Export the stacked headers to excel by setting the [CanExportStackedHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CanExportStackedHeaders) property to `true`.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CanExportStackedHeaders = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Exporting merged cells

Export the merged cells to excel by setting the [CanExportMergedCells](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CanExportMergedCells) property as `true`.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CanExportMergedCells = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Exporting unbound rows

Export the unbound rows to excel by setting the [CanExportUnboundRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CanExportUnboundRows) property as `true`.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CanExportUnboundRows = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Changing start row and column index while exporting

Export the data to the specified row index and column index in the worksheet, by setting the [StartRowIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_StartRowIndex) and [StartColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_StartColumnIndex) properties.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.StartColumnIndex = 3;
options.StartRowIndex = 3;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-with-row-column-index.png" alt="Exporting to Excel with Custom Row and Column Index in WinUI DataGrid" width="100%" Height="Auto"/>

## Export DataGrid SelectedItems to Excel

By default, the entire grid will be exported to Excel. Export selected rows only by passing the [SelectedItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_SelectedItems) to the [ExportToExcel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportExtensions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportExtensions_ExportToExcel_Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Syncfusion_UI_Xaml_Data_ICollectionViewAdv_Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_) method.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.SelectedItems, options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-selected-item.png" alt="Exporting Selected Items only to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

## Row Height and Column Width customization 

After exporting data to excel, set the different row heights and column widths for the columns based on your requirement. Please refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation#adjust-row-height-and-column-width) for more information. 

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].SetRowHeight(2, 50);
workBook.Worksheets[0].SetColumnWidth(2, 50);
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

## Styling cells based on CellType in Excel

Customize the cell styles based on the [CellType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportStartOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportStartOptions_CellType) by using the [GridExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_GridExportHandler).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.GridExportHandler = GridExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void GridExportHandler(object sender, DataGridExcelExportStartOptions e)
{
    if (e.CellType == ExportCellType.HeaderCell)
    {
        e.Style.Color = Color.FromArgb(100, 228, 234);
        e.Style.Font.Color = ExcelKnownColors.White;
        e.Handled = true;
    }

    else if (e.CellType == ExportCellType.RecordCell)
    {
        e.Style.Color = Color.FromArgb(240, 224, 144);
        e.Handled = true;
    }

    else if (e.CellType == ExportCellType.GroupCaptionCell)
    {
        e.Style.Color = Color.FromArgb(252, 159, 161);
        e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-cell-style-customization.png" alt="WinUI DataGrid displays Customized Cell Style based on CellType in Exported Excel" width="100%" Height="Auto"/>

## Cell customization in Excel while exporting

Customize the cells by setting the [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler) in the [DataGridExcelExportOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html).

### Customize cell value while exporting

Customize the cell values while exporting to excel by using the [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler) in the [DataGridExcelExportOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CellsExportHandler = CellsExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void CellsExportHandler(object sender, DataGridCellExcelExportOptions e)
{
    // Based on the column mapping name and the cell type, change the cell 
    //values while exporting to excel.
    if (e.CellType == ExportCellType.RecordCell && e.ColumnName == "IsShipped")
    {

        //if the cell value is True, "Y" will be displayed. Else "N" will be displayed.

        if (e.CellValue.Equals(true))
            e.Range.Cells[0].Value = "Y";

        else
            e.Range.Cells[0].Value = "N";
        e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-cell-value-customization.png" alt="Customizing Cell Values while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

Here, the cell values are changed for the `Is Shipped` column based on custom condition.

### Changing row style in excel based on data

Customize the rows based on the record values by using the [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CellsExportHandler = CellsExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void CellsExportHandler(object sender, DataGridCellExcelExportOptions e)
{
    var record = e.NodeEntry;

    if (record != null && (record as OrderInfo).Country == "Mexico")
    {
        e.Range.CellStyle.ColorIndex = ExcelKnownColors.Green;
        e.Range.CellStyle.Font.Color = ExcelKnownColors.White;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-row-style-customization.png" alt="Customizing Row Style based on Data while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

Here, the records having the `Country` name as `Mexico` are customized.

### Customize the cells based on Column Name

Customize the cells based on the [DataGridCellExcelExportOptions.ColumnName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridCellExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridCellExcelExportOptions_ColumnName) property in the [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CellsExportHandler = CellsExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void CellsExportHandler(object sender, DataGridCellExcelExportOptions e)
{

    if (e.ColumnName != "OrderID")
        return;

    e.Range.CellStyle.Font.Size = 12;
    e.Range.CellStyle.Font.Color = ExcelKnownColors.Pink;
    e.Range.CellStyle.Font.FontName = "Segoe UI";
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-cell-value-based-on-column.png" alt="Customizing Cell Values based on Column name while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

Here, the `OrderID` column cells are customized while exporting.

## Exporting DetailsView

By default, the [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) will be exported to Excel. Customize its exporting operation by using the [DetailsViewExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_DetailsViewExportHandler).

### Excluding DetailsViewDataGrid while exporting

Exclude the particular [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) while exporting by using the [DetailsViewExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_DetailsViewExportHandler) and [DataGridDetailsViewExcelExportOptions.Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) .

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.DetailsViewExportHandler = DetailsViewExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void DetailsViewExportHandler(object sender, DataGridDetailsViewExcelExportOptions e)
{
    var recordEntry = e.NodeEntry as RecordEntry;
    var record = (recordEntry.Data as Model);

    if (record != null && record.OrderID == 1002)
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-data-in-detailsview.png" alt="Excluding Specific DetailsView while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

Here, the [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) is not exported for the parent record having the `OrderID` as 1002.

### Excluding DetailsViewDataGrid columns from exporting

Exclude the [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) columns while exporting by using the [DetailsViewExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_DetailsViewExportHandler) and [DataGridDetailsViewExcelExportOptions.ExcludedColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridDetailsViewExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridDetailsViewExcelExportOptions_ExcludedColumns).

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.DetailsViewExportHandler = DetailsViewExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void DetailsViewExportHandler(object sender, DataGridDetailsViewExcelExportOptions e)
{
    e.ExcludedColumns.Add("OrderID");
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-export-without-column.png" alt="Excluding Columns in DetailsViewDataGrid while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>


Here, the `OrderID` column is displayed in the `DetailsViewDataGrid` and is excluded while exporting to excel.

### Customizing DetailsViewDataGrid cells

Like the parent DataGrid, customize the [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) cells by using [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler). Based on the [DataGridCellExcelExportOptions.GridViewDefinition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridCellExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridCellExcelExportOptions_GridViewDefinition) property, identify the particular `DetailsViewDataGrid` and customize it.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CellsExportHandler = CellsExportHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private static void CellsExportHandler(object sender, DataGridCellExcelExportOptions e)
{
    if (e.GridViewDefinition == null)
        return;

    if (e.ColumnName == "OrderID")
    {
        e.Range.CellStyle.Font.Size = 12;
        e.Range.CellStyle.Font.Color = ExcelKnownColors.Blue;
        e.Range.CellStyle.Font.FontName = "Segoe UI";
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-exported-cell-customization.png" alt="Customizing DetailsViewDataGrid Cells while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

## Customize exported workbook and worksheet

SfDataGrid exports to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating workbook and sheet after exporting. 

### Workbook
The SfDataGrid provides an option to return the [ExcelEngine](https://help.syncfusion.com/cr/file-formats/Syncfusion.XlsIO.ExcelEngine.html). From that, get the exported workbook. This allows you to protect, encrypt and add worksheets before saving. 

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Worksheet customization

The SfDataGrid provides support to export to an already existing file or worksheet. 

In the following code sample, the worksheet is created and passed to the [ExportToExcel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportExtensions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportExtensions_ExportToExcel_Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Syncfusion_UI_Xaml_Data_ICollectionViewAdv_Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_) method. In the same way, open an already existing excel using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). 

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
ExcelEngine excelEngine = new ExcelEngine();
IWorkbook workBook = excelEngine.Excel.Workbooks.Create();
dataGrid.ExportToExcel(dataGrid.View, options, workBook.Worksheets[0]);
workBook.Version = ExcelVersion.Excel2013;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

Before saving the workbook, set the specific excel version by using the [IWorkbook.Version](https://help.syncfusion.com/cr/wpf/Syncfusion.XlsIO.IWorkbook.html#Syncfusion_XlsIO_IWorkbook_Version) property. Here, directly manipulate the data in the worksheet. Please refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation) for more information.

#### Setting borders

Set borders to excel cells by directly accessing the worksheet after exporting data.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].UsedRange.BorderInside(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
workBook.Worksheets[0].UsedRange.BorderAround(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-change-border-style.png" alt="Changing Border Style in Exported Excel for WinUI DataGrid" width="100%" Height="Auto"/>

#### Enabling Filters

Show filters in the exported worksheet by enabling a filter for the exported range in the worksheet.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].UsedRange;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-filter-on-exported-excel.png" alt="Filters on Exported Excel in WinUI DataGrid" width="100%" Height="Auto"/>

While using the [stacked headers](https://help.syncfusion.com/winui/datagrid/stacked-headers), the filter option enables for the stacked header cell. To avoid this, specify the `range` based on the Stacked headers count to show the filter icon in the header cell.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
options.CanExportStackedHeaders = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
var range = "A" + (dataGrid.StackedHeaderRows.Count + 1).ToString() + ":" + workBook.Worksheets[0].UsedRange.End.AddressLocal;
excelEngine.Excel.Workbooks[0].Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].Range[range];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

Please refer to the [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/worksheet-cells-manipulation#data-filtering).

#### Customize the range of cells

Customize the range of cells after exporting to excel by directly manipulating worksheet.

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Color = Syncfusion.Drawing.Color.LightSlateGray;
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Font.Color = ExcelKnownColors.White;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-range-of-cells-customization.png" alt="Customizing Range of Cells in Exported Excel for WinUI DataGrid" width="100%" Height="Auto"/>

## Performance

Using the [DataGridExcelExportOptions.CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler) and changing settings for each cell will consume more memory and time. So, avoid using [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler) instead, do the required settings in the exported sheet.
 
### Formatting column without using CellsExportHandler

Perform cell-level customization such as row-level styling and formatting particular columns in the exported worksheet. 

In the following code sample, the NumberFormat for the `Unit Price` column is changed in the exported sheet after exporting without using the [CellsExportHandler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Export.DataGridExcelExportOptions.html#Syncfusion_UI_Xaml_DataGrid_Export_DataGridExcelExportOptions_CellsExportHandler). 

Reference:
[CellRange Formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting)

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];
workBook.ActiveSheet.Columns[1].NumberFormat = "0.0";
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-column-formatting.png" alt="Formatting the Column while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>

### Alternate row styling without using CellsExportHandler

In the following code sample, the background color of rows in excel is changed based on the row index using conditional formatting for better performance.

Reference:
[Conditional Formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting)

{% tabs %}
{% highlight c# %}
var options = new DataGridExcelExportOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];

IConditionalFormats condition = workBook.ActiveSheet.Range[2, 1, this.dataGrid.View.Records.Count + 1, this.dataGrid.Columns.Count].ConditionalFormats;
IConditionalFormat condition1 = condition.AddCondition();
condition1.FormatType = ExcelCFType.Formula;
condition1.FirstFormula = "MOD(ROW(),2)=0";
condition1.BackColorRGB = Syncfusion.Drawing.Color.Pink;
IConditionalFormat condition2 = condition.AddCondition();
condition2.FormatType = ExcelCFType.Formula;
condition2.FirstFormula = "MOD(ROW(),2)=1";
condition2.BackColorRGB = Syncfusion.Drawing.Color.LightGray;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-row-style.png" alt="Displaying Row Style while Exporting to Excel in WinUI DataGrid" width="100%" Height="Auto"/>


