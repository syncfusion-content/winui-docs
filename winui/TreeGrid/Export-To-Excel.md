---
layout: post
title: Export To Excel in WinUI TreeGrid control | Syncfusion
description: Learn here all about Export To Excel support in Syncfusion WinUI TreeGrid (SfTreeGrid) control and more.
platform: winui
control: TreeGrid
documentation: ug
---

# Export To Excel in WinUI TreeGrid (SfTreeGrid)

The [WinUI TreeGrid](https://help.syncfusion.com/winui/treegrid/overview) supports exporting data to excel. Export merged cells, stacked headers while exporting.

The following assemblies needs to be added for exporting to excel.

* Syncfusion.GridExport.WinUI
* Syncfusion.XlsIO.NET

For NuGet package, install the [Syncfusion.GridExport.WinUI](https://www.nuget.org/packages/Syncfusion.GridExport.WinUI) package.

Export the SfTreeGrid to excel by using the `ExportToExcel` extension method in the `Syncfusion.UI.Xaml.TreeGrid.Export` namespace.

{% tabs %}
{% highlight c# %}
using Syncfusion.UI.Xaml.TreeGrid.Export;
var options = new TreeGridExcelExportOptions();
var excelEngine = treeGrid.ExportToExcel(options);
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

N> The SfTreeGrid exports data to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). Refer to the [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating the exported worksheets.

## Excel exporting options

The exporting operation can be customized by passing `TreeGridExcelExportOptions` instance as an argument to the `ExportToExcel` method. 

### Export mode

By default, only the actual value will be exported to excel. To export the display text, set the `ExportMode` property as `Text`. 

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExportMode = ExportMode.Text;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Export without outlines	

By default, all the children in the TreeGrid will be exported based on the state in TreeGrid. You can disable the outlines in Excel by setting the `ShowOutlines` property to false in `TreeGridExcelExportOptions` class.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.ShowOutlines = false;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-export-to-excel.png" alt="WinUI TreeGrid Data Exporting to Excel without Outlines" width="100%" Height="Auto"/>

### Exclude columns while exporting

By default, all the columns (including hidden columns) in the TreeGrid will be exported to Excel. To exclude some columns, use `ExcludedColumns` field in `TreeGridExcelExportOptions` class.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.ExcludedColumns.Add("FirstName");
options.ExcludedColumns.Add("LastName");
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

Here, the columns having FirstName and LastName as MappingName are excluded when exporting.

### Excel version

While exporting to Excel, specify the excel version by using the `ExcelVersion` property.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Exporting stacked headers

Export the stacked headers to excel by setting the `CanExportStackedHeaders` property to `true`.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.CanExportStackedHeaders = true;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Exporting merged cells

Export the merged cells to excel by setting the `CanExportMergedCells` property as `true`.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.CanExportMergedCells = true;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Export column width to Excel

You can export the columns with its actual width by setting the `CanExportColumnWidth` property to `true`. 

{% tabs %}
{% highlight c# %}
var options =new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.CanExportColumnWidth = true;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

The default value of the `CanExportColumnWidth` property is `true`.

### Export with customized row height

You can export the TreeGrid to Excel with customized row height by using the `DefaultRowHeight` property.

{% tabs %}
{% highlight c# %}
var options =new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.DefaultRowHeight = 60;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample"); 
{% endhighlight %}
{% endtabs %}

### Change the node expand state in Excel

You can change the node expanding state in Excel by using the `NodeExpandMode` property.

{% tabs %}
{% highlight c# %}
var options =new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.NodeExpandMode = NodeExpandMode.CollapseAll;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Changing start row and column index while exporting

Export the data to the specified row index and column index in the worksheet, by setting the `StartRowIndex` and `StartColumnIndex` properties.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.StartRowIndex = 3;
options.StartColumnIndex = 3;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-change-row-column-index.png" alt="Changing Row and Column Index while Exporting from WinUI TreeGrid to Excel" width="100%" Height="Auto"/>

## Row Height and Column Width customization  

After exporting the data to Excel, you can set different row heights and column widths for the columns. You can refer to [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation#adjust-row-height-and-column-width) for more information.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].SetRowHeight(2, 50);
workBook.Worksheets[0].SetColumnWidth(2, 50);
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

## Styling cells based on CellType in Excel

Customize the cell styles based on the `CellType` by using the `GridExportHandler`.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.GridExportHandler = GridExportHandler;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private void GridExportHandler(object sender, TreeGridExcelExportStartOptions e)
{
    if (e.CellType == ExportCellType.HeaderCell)
    {
        e.Style.Color = Color.Red;
        e.Style.Font.Color = ExcelKnownColors.White;
        e.Handled = true;
    }
    else if(e.CellType == ExportCellType.RecordCell)
    {
        e.Style.Color = Color.LightPink;
        e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-cell-style-customization.png" alt="WinUI TreeGrid displays Customized Cell Style based on CellType in Exported Excel" width="100%" Height="Auto"/>

## Cell customization in Excel while exporting

Customize the cells by setting the `CellsExportHandler` in the `TreeGridExcelExportOptions`.

### Customize cell value while exporting

Customize the cell values while exporting to excel by using the `CellsExportHandler` in the `TreeGridExcelExportOptions`.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.CellsExportHandler = CellsExportHandler;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private void CellsExportHandler(object sender, TreeGridCellExcelExportOptions e)
{
    // Based on the column mapping name and the cell type, we can change the cell values while exporting to excel.
    if (e.CellType == ExportCellType.RecordCell && e.ColumnName == "Availability")
    {
        if (e.CellValue.Equals(true))
            e.Range.Cells[0].Value = "Y";

        else
            e.Range.Cells[0].Value = "N";
        e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-export-customization.png" alt="Customizing Cell Values while Exporting to Excel in WinUI TreeGrid" width="100%" Height="Auto"/>

Here, the cell values changed for the Availability column are based on the custom condition.

### Changing row style in Excel based on data

You can customize the rows based on the record values by using the `CellsExportHandler`.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.CellsExportHandler = CellsExportHandler;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private void CellsExportHandler(object sender, TreeGridCellExcelExportOptions e)
{
    if ((e.Node == null))
        return;
    var record = e.Node as EmployeeInfo;

    if (record.City == "US")
    {
        e.Range.CellStyle.Color = Color.LightYellow;
        e.Range.CellStyle.Font.Color = ExcelKnownColors.Pink;
    }
}
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-row-style.png" alt="Customizing Row Style based on Data while Exporting to Excel in WinUI TreeGrid" width="100%" Height="Auto"/>

Here, the records having the `City` name as `US` are customized.

### Customize the cells based on column name

You can customize the cells based on the [GridCellExcelExportingEventArgs.ColumnName](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.Converter.GridCellExcelExportingEventArgs.html#Syncfusion_UI_Xaml_Grid_Converter_GridCellExcelExportingEventArgs_ColumnName) property in [CellsExportingEventHandler](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeGrid.Converter.TreeGridExcelExportingOptions.html#Syncfusion_UI_Xaml_TreeGrid_Converter_TreeGridExcelExportingOptions_CellsExportingEventHandler).

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.CellsExportHandler = CellsExportHandler;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");

private void CellsExportHandler(object sender, TreeGridCellExcelExportOptions e)
{
    if (e.ColumnName != "ID")
        return;

    e.Range.CellStyle.Font.Size = 12;
    e.Range.CellStyle.Font.Color = ExcelKnownColors.Pink;
    e.Range.CellStyle.Font.FontName = "Segoe UI";
}
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-column-cell-customization.png" alt="Customizing Cell Values based on Column name while Exporting to Excel in WinUI TreeGrid" width="100%" Height="Auto"/>

Here, the `ID` column cells are customized while exporting.

## Customize exported workbook and worksheet

The TreeGrid can be exported to Excel using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer to the [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating the workbooks and sheets after exporting.

### Set borders

You can set the borders to Excel cells by directly accessing worksheet after exporting the data.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].UsedRange.BorderInside(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
workBook.Worksheets[0].UsedRange.BorderAround(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-cell-border-style.png" alt="Changing Border Style in Exported Excel for WinUI TreeGrid" width="100%" Height="Auto"/>

#### Enabling Filters

Show filters in the exported worksheet by enabling a filter for the exported range in the worksheet.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].UsedRange;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-filter.png" alt="Filters on Exported Excel in WinUI TreeGrid" width="100%" Height="Auto"/>


While using the `stacked headers`, the filter option enables for the stacked header cell. To avoid this, specify the `range` based on the Stacked headers count to show the filter icon in the header cell.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
var range = "A" + (treeGrid.StackedHeaderRows.Count + 1).ToString() + ":" + workBook.Worksheets[0].UsedRange.End.AddressLocal;
excelEngine.Excel.Workbooks[0].Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].Range[range];
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

Please refer to the [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/worksheet-cells-manipulation#data-filtering).

### Customize the range of cells

Customize the range of cells after exporting to excel by directly manipulating worksheet.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Color = Syncfusion.Drawing.Color.LightSlateGray;
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Font.Color = ExcelKnownColors.White;
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-range-of-cells.png" alt="Customizing Range of Cells in Exported Excel for WinUI TreeGrid" width="100%" Height="Auto"/>

## Performance

Using the `TreeGridExcelExportOptions.CellsExportHandler` and changing the settings for each cell will consume more memory and time. So, avoid using the `CellsExportHandler` and instead of this, you can do the required settings in the exported sheet.

### Formatting column without using CellsExportHandler

Perform cell-level customization such as row-level styling and formatting particular columns in the exported worksheet. 

In the following code sample, the NumberFormat for the `Salary` column is changed in the exported sheet after exporting without using the `CellsExportHandler`. 

Reference:
[CellRange Formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting)

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExportMode = ExportMode.Value;
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];
workBook.ActiveSheet.Columns[2].NumberFormat = "$0.0";
MemoryStream stream = new MemoryStream();
workBook.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

<img src="Export-To-Excel_images/winui-treegrid-column-formatting.png" alt="Formatting the Column while Exporting to Excel in WinUI TreeGrid" width="100%" Height="Auto"/>

### Alternate row styling without using CellsExportHandler

In the following code sample, the background color of rows in excel is changed based on the row index using conditional formatting for better performance.

Reference:
[Conditional Formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting)

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExportMode = ExportMode.Value;
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = treeGrid.ExportToExcel(options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];
IConditionalFormats condition = workBook.ActiveSheet.Range[2, 1, this.treeGrid.View.Nodes.Count + 1, this.treeGrid.Columns.Count].ConditionalFormats;
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

<img src="Export-To-Excel_images/winui-treegrid-changing-row-style.png" alt="Displaying Row Style while Exporting to Excel in WinUI TreeGrid" width="100%" Height="Auto"/>

## How to

### Export multiple TreeGrids to single Excel sheet

You can export multiple TreeGrids to single Excel sheet by merging one TreeGrid worksheet into another using the `Worksheet.UsedRange.CopyTo` method.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;

var excelEngine = treeGrid.ExportToExcel(options);
var workBook1 = excelEngine.Excel.Workbooks[0];
var worksheet1 = workBook1.Worksheets[0];
            
excelEngine = treeGrid1.ExportToExcel(options);
var workBook2 = excelEngine.Excel.Workbooks[0];
var worksheet2 = workBook2.Worksheets[0];

var columnCount = this.treeGrid1.Columns.Count;
//Merge the One TreeGrid WorkSheet into the other TreeGrid WorkSheet
worksheet2.UsedRange.CopyTo(worksheet1[1, columnCount + 1]);
MemoryStream stream = new MemoryStream();
workBook1.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

### Export the TreeGrid that is not loaded in view

You can export the TreeGrid that is not loaded in view by calling the ApplyTemplate() method before exporting.

{% tabs %}
{% highlight c# %}
var options = new TreeGridExcelExportOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
treeGrid1.ApplyTemplate();
var excelEngine = treeGrid1.ExportToExcel(options);
var workBook1 = excelEngine.Excel.Workbooks[0];
MemoryStream stream = new MemoryStream();
workBook1.SaveAs(stream);
Save(stream, "Sample");
{% endhighlight %}
{% endtabs %}

