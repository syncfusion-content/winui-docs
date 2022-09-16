---
layout: post
title: Export To Excel in WinUI DataGrid control | Syncfusion
description: Learn here all about Export To Excel support in Syncfusion WinUI DataGrid (SfDataGrid) control and more.
platform: winui
control: DataGrid
documentation: ug
---

# Export To Excel in WinUI DataGrid

[WinUI DataGrid](https://help.syncfusion.com/winui/datagrid/overview) provides support to export data to excel. It also provides support for grouping, filtering, sorting, unbound rows, merged cells, stacked headers and Details View while exporting.

The following assemblies needs to be added for exporting to excel.

* Syncfusion.GridExport.WinUI
* Syncfusion.XlsIO.NET

For NuGet package, have to install `Syncfusion.GridExport.WinUI` package.

You can export SfDataGrid to excel by using the `ExportToExcel` extension method present in the `Syncfusion.UI.Xaml.DataGrid.Export` namespace.

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
            //Write compressed data from memory to file
            using (Stream outstream = zipStream.AsStreamForWrite())
            {
                byte[] buffer = stream.ToArray();
                outstream.Write(buffer, 0, buffer.Length);
                outstream.Flush();
            }
        }
        //Launch the saved Excel file
        await Windows.System.Launcher.LaunchFileAsync(stFile);
    }
}
{% endhighlight %}
{% endtabs %}

N> SfDataGrid exports data to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating exported work sheets. 

## Excel exporting options

Exporting operation can be customized by passing `DataGridExcelExportOptions` instance as argument to `ExportToExcel` method. 

### Export mode

By default, actual value only will be exported to excel. If you want to export the display text, you need to set `ExportMode` property as `Text`. 

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

By default, all the groups in dataGrid will be exported in expanded state. You can enable outlines in excel based on groups by setting the `ShowOutlines` property as `true` in `DataGridExcelExportOptions`.

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

By default, all the columns (including hidden columns) in SfDataGrid will be exported to Excel. If you want to exclude some columns while exporting to Excel, you can use `ExcludedColumns` field in `DataGridExcelExportOptions`.

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

Here, the columns having `CustomerName` and `Country` as MappingName are excluded while exporting.

### Excel version

While exporting to Excel, you can specify the excel version by using `ExcelVersion` property.

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

You can export stacked headers to excel by setting `CanExportStackedHeaders` property to `true`.

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

You can export merged cells to excel by setting `CanExportMergedCells` property as `true`.

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

You can export unbound rows to excel by setting `CanExportUnboundRows` property as `true`.

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

You can export the data to specified row index and column index in worksheet, by setting `StartRowIndex` and `StartColumnIndex` properties.

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

By default, entire grid will be exported to Excel. You can export selected rows only by passing `SelectedItems` to 
`ExportToExcel` method.

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

After exporting data to excel, you can set different row height and column width for the columns based on your requirement. You can refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation#adjust-row-height-and-column-width) for more information. 

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

You can customize the cell styles based on `CellType` by using `GridExportHandler`.

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
        e.Style.Color = Color.Red;
        e.Style.Font.Color = ExcelKnownColors.White;
        e.Handled = true;
    }

    else if (e.CellType == ExportCellType.RecordCell)
    {
        e.Style.Color = Color.PaleTurquoise;
        e.Handled = true;
    }

    else if (e.CellType == ExportCellType.GroupCaptionCell)
    {
        e.Style.Color = Color.Pink;
        e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-to-Excel_images/winui-datagrid-cell-style-customization.png" alt="WinUI DataGrid displays Customized Cell Style based on CellType in Exported Excel" width="100%" Height="Auto"/>

## Cell customization in Excel while exporting

You can customize the cells by setting `CellsExportHandler` in `DataGridExcelExportOptions`.

### Customize cell value while exporting

You can customize the call values while exporting to excel by using `CellsExportHandler` in `DataGridExcelExportOptions`.

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
    // Based on the column mapping name and the cell type, we can change the cell 
    //values while exporting to excel.
    if (e.CellType == ExportCellType.RecordCell && e.ColumnName == "IsShipped")
    {

        //if the cell value is True, "Y" will be displayed else "N" will be displayed.

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

Here, cell values are changed for `Is Shipped` column based on custom condition.

### Changing row style in excel based on data

You can customize the rows based on the record values by using `CellsExportHandler`.

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

Here, records having the `Country` name as `Mexico` are customized.

### Customize the cells based on Column Name

You can customize the cells based on `DataGridCellExcelExportOptions.ColumnName` property in the `CellsExportHandler`.

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

Here, `OrderID` column cells are customized while exporting.

## Customize exported workbook and worksheet

SfDataGrid exports to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating workbook and sheet after exporting. 

### Workbook
SfDataGrid provides option to return [ExcelEngine](https://help.syncfusion.com/cr/file-formats/Syncfusion.XlsIO.ExcelEngine.html) from that you can get exported workbook. This allows you to protect, encrypt and add worksheet before saving. 

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

SfDataGrid provides support to export to already existing file or worksheet. 

In the below code snippet, worksheet is created and passed to `ExportToExcel` method. In the same way, you can open already existing excel also using `XlsIO`. 

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

Before saving workbook, you need to set the specific excel version by using `IWorkbook.Version` property. Here, you can directly manipulate the data in the worksheet. You can refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation) for more information.

#### Setting borders

You can set borders to excel cells by directly accessing worksheet after exporting data.

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

You can show filters in exported worksheet by enabling filter for the exported range in the worksheet.

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

While using `stacked headers`, you can specify the `range` based on Stacked headers count.

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

You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/worksheet-cells-manipulation#data-filtering).

#### Customize the range of cells

You can customize the range of cells after exporting to excel by directly manipulating worksheet.

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

## Exporting DetailsView

By default, [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) will be exported to Excel. You can customize its exporting operation by using `DetailsViewExportHandler`.

### Excluding DetailsViewDataGrid while exporting

You can exclude particular `DetailsViewDataGrid` while exporting, by using the `DetailsViewExportHandler` and [DataGridDetailsViewExcelExportOptions.Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) .

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

Here, `DetailsViewDataGrid` is not exported for the parent record having `OrderID` as 1002.

### Excluding DetailsViewDataGrid columns from exporting

You can exclude [DetailsViewDataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DetailsViewDataGrid.html) columns while exporting, by using `DetailsViewExportHandler` and `DataGridDetailsViewExcelExportOptions.ExcludedColumns`.

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


Here, `OrderID` column is displayed in `DetailsViewDataGrid` and it is excluded while exporting to excel.

### Customizing DetailsViewDataGrid cells

Like parent DataGrid, You can customize the `DetailsViewDataGrid` cells also by using `CellsExportHandler`. Based on `DataGridCellExcelExportOptions.GridViewDefinition` property, you can identify the particular `DetailsViewDataGrid` and customize it.

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


## Performance

Using `DataGridExcelExportOptions.CellsExportHandler` and changing settings for each cell will consume more memory and time consumption. So, avoid using `CellsExportHandler` and instead of you can do the required settings in the exported sheet.
 
### Formatting column without using CellsExportHandler

You can perform cell level customization such as row-level styling, formatting particular column in the exported worksheet. 

In the below code snippet, NumberFormat for `Unit Price` column is changed in the exported sheet after exporting without using `CellsExportHandler`. 

Reference:
[http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting)

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

In the below code snippet, the background color of rows in excel is changed based on row index using conditional formatting for better performance.

Reference:
[http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting)

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


