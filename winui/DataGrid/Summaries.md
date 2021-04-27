---
layout: post
title: Summaries in WinUI DataGrid control | Syncfusion
description: Learn here all about Summaries support in Syncfusion WinUI DataGrid(SfDataGrid) control with displaying summary and more.
platform: winui
control: DataGrid
documentation: ug
---


# Summaries in WinUI DataGrid

SfDataGrid provides support to display the concise information about the data objects using summaries. SfDataGrid provides below three different types of summary rows.

* **Table Summary** – Used to display summary information of table either at top or bottom of SfDataGrid. 

* **Group Summary** – used to display summary information of data objects in each group.

* **Caption Summary** – used to display summary information in the caption of the group.
 
![WinUI DataGrid with table and summaries](Summaries_images/winui-datagrid-summaries.png)

Summary rows are represented by using [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html) and  each `GridSummaryRow` hold summary information of columns in [SummaryColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_SummaryColumns) property. The `SummaryColumns` contains the collection of [GridSummaryColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html) which carries the name of column, format and its summary aggregate type.

## Table Summary

The table summary calculates the summary value over all the records. SfDataGrid allows you to add any number of table summary rows in top and bottom of SfDataGrid.

You can add table summary row in SfDataGrid by adding [GridTableSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridTableSummaryRow.html) to [SfDataGrid.TableSummaryRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_TableSummaryRows) collection.

### Defining summary for column

You can display summary information in the column by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `false` and defining summary columns. To calculate summary based on column you have to specify the below properties,

1. [GridSummaryColumn.MappingName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_MappingName) – MappingName of the column (Property name of data object) that you want calculate summary.

2. [GridSummaryColumn.SummaryType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_SummaryType) – SfDataGrid provides different built-in summary calculation functions for various types.

3. [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format) – Used to define format string for summary based on support function name’s in specified SummaryType.

Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary and [Aggregate Types](#aggregate-types) section to know about different Summary Types.

In the below code snippet, summary is defined for `UnitPrice` and `ProductName` columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"                               
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">

    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'Total UnitPrice : {Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format="'Total Product Count : {Count:d}'"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>

</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.TableSummaryRows.Add(new GridTableSummaryRow()
{
    ShowSummaryInRow = false,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "Total UnitPrice : {Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "Total Product Count : {Count:d}"
        },
    }
});
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays Table Summary on column basics](Summaries_images/winui-datagrid-table-summary-with-column.png)

### Displaying summary for Row

You can display summary information in row by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `true` and defining summary columns. You have to set [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title) based on [GridSummaryColumn.Name](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Name) property to format summary columns values in row. 

Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary.
 
{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">
                       
    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow Title=" Total Price : {PriceAmount} for {ProductCount} products " ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                                Format="'{Sum:c}'"
                                                MappingName="UnitPrice"
                                                SummaryType="DoubleAggregate" />
    
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                                Format="'{Count:d}'"
                                                MappingName="ProductName"
                                                SummaryType="CountAggregate" />
    
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
    
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.TableSummaryRows.Add(new GridTableSummaryRow()
{
    ShowSummaryInRow = true,
    Title = "Total Price: {PriceAmount} for {ProductCount} Products",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "{Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        },
    }
});
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays Table Summary on a row](Summaries_images/winui-datagrid-table-summary-with-row.png)


### Displaying column summary with title

SfDataGrid supports to show column summary and title summary at the same time. You can show column summary along with title by defining the [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title)  and [GridSummaryRow.TitleColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_TitleColumnCount) property along with defining summary columns. Showing column summary along with title can be only supported if [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) is disabled.

Refer [Defining summary for column](#defining-summary-for-column) section to know more about how to define summary columns.

In the below code snippet, `GridSummaryRow.TitleColumnCount` is set as 2 and `GridSummaryRow.Title` is defined along with summary columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">
    <dataGrid:SfDataGrid.TableSummaryRows>
       <dataGrid:GridTableSummaryRow ShowSummaryInRow="False" TitleColumnCount="2" Position="Top"
                                       Title="Total Price : {PriceAmount} for {ProductCount} products">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="CustomerName" 
                                              Format=" {Count:d}"
                                              MappingName="CustomerName" 
                                              SummaryType="CountAggregate" />
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format=" {Sum:c}"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format=" {Count:d}"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />                        
            </dataGrid:GridSummaryRow.SummaryColumns>
       </dataGrid:GridTableSummaryRow>     
	   
       <dataGrid:GridTableSummaryRow ShowSummaryInRow="False" TitleColumnCount="2" Position="Bottom"
                                       Title="Total Price : {PriceAmount} for {ProductCount} products">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="CustomerName" 
                                              Format=" {Count:d}"
                                              MappingName="CustomerName" 
                                              SummaryType="CountAggregate" />
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format=" {Sum:c}"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format=" {Count:d}"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />                        
            </dataGrid:GridSummaryRow.SummaryColumns>
       </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>  
	
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.TableSummaryRows.Add(new GridTableSummaryRow()
{
    ShowSummaryInRow = false,
    Position = TableSummaryRowPosition.Top,
    Title = "Total Price : {PriceAmount} for {ProductCount} products",
    TitleColumnCount = 2,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
            Name = "CustomerName",
            Format = "{Count:d}",
            MappingName = "CustomerName",
            SummaryType = SummaryType.CountAggregate
        },
		
        new GridSummaryColumn()
        {
            Name = "PriceAmount",
            MappingName = "UnitPrice",
            SummaryType = SummaryType.DoubleAggregate,
            Format = "{Sum:c}"
        },
		
        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        }        
    }
});

this.sfDataGrid.TableSummaryRows.Add(new GridTableSummaryRow()
{
    ShowSummaryInRow = false,
    Position = TableSummaryRowPosition.Bottom,
    Title = "Total Price : {PriceAmount} for {ProductCount} products",
    TitleColumnCount = 2,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
            Name="CustomerName",
            Format="{Count:d}",
            MappingName="CustomerName",
            SummaryType=SummaryType.CountAggregate
        },
		
        new GridSummaryColumn()
        {
            Name = "PriceAmount",
            MappingName="UnitPrice",
            SummaryType= SummaryType.DoubleAggregate,
            Format="{Sum:c}"
        },
		
        new GridSummaryColumn()
        {
            Name="ProductCount",
            MappingName="ProductName",
            SummaryType=SummaryType.CountAggregate,
            Format="{Count:d}"
        }        
    }
});

{% endhighlight %}
{% endtabs %}

The following screenshot illustrates displaying summary columns with title at same time for `TableSummaryRow`.

![Table summary columns with title in WinUI DataGrid](Summaries_images/winui-datagrid-table-summary-with-title.png)

#### Limitations

The following are the limitations of displaying column summary along with title at same time for `TableSummaryRow`:

* If [FrozenColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_FrozenColumnCount) is defined lesser than `GridSummaryRow.TitleColumnCount`, the title summary will be spanned to `FrozenColumnCount` range, since spanned range and frozen range cannot be vary.
* Summary columns defined in the `GridSummaryRow.TitleColumnCount` range will not be shown.


### Positioning TableSummaryRow

You can position the table summary either at top or bottom of SfDataGrid by setting [GridTableSummaryRow.Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridTableSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridTableSummaryRow_Position) property.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}">

    <dataGrid:SfDataGrid.TableSummaryRows>

        <dataGrid:GridTableSummaryRow Position="Top" ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>

        <dataGrid:GridTableSummaryRow Title=" Total Product count: {ProductCount}"
                                        Position="Bottom"
                                        ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                                Format="'{Count:d}'"
                                                MappingName="ProductName"
                                                SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>

    </dataGrid:SfDataGrid.TableSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
GridTableSummaryRow tablesummaryrow1 = new GridTableSummaryRow() 
{ 
    ShowSummaryInRow = false, 
    Position = TableSummaryRowPosition.Top,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {

        new GridSummaryColumn()
        {
            Name = "PriceAmount",
            Format = "{Sum:c}",
            MappingName = "UnitPrice",
            SummaryType = SummaryType.DoubleAggregate 

        }
    }
};

GridTableSummaryRow tablesummaryrow2 = new GridTableSummaryRow()
{
    ShowSummaryInRow = true,
    Position = TableSummaryRowPosition.Bottom,
    Title = "Total Product count: {ProductCount}",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            Format = "{Count:d}",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate 
        }
    }
};

this.sfDataGrid.TableSummaryRows.Add(tablesummaryrow1);
this.sfDataGrid.TableSummaryRows.Add(tablesummaryrow2);
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid Table Summary Position](Summaries_images/winui-datagrid-table-summary-position.png)

## Group Summary

Group summary values calculated based on the records in the group and the summary information will be displayed at the bottom of each group. You can view the group summary row by expanding the corresponding group header. SfDataGrid allows you to add any number of group summary rows.

You can add the group summary rows in SfDataGrid by adding the [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html) to [SfDataGrid.GroupSummaryRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_GroupSummaryRows) collection.

### Defining summary for column

You can display summary information in the column by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `false` and defining summary columns. To calculate summary based on column you have to specify the below properties,

1. [GridSummaryColumn.MappingName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_MappingName) – MappingName of the column (Property name of data object) that you want calculate summary.

2. [GridSummaryColumn.SummaryType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_SummaryType) – SfDataGrid provides different built-in summary calculation functions for various types.

3. [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format) – Used to define format string for summary based on support function name’s in specified SummaryType.

Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary and [Aggregate Types](#aggregate-types) section to know about different Summary Type’s.

In the below code snippet, summary is defined for `UnitPrice` and `ProductName` columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"                             
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">

    <dataGrid:SfDataGrid.GroupSummaryRows>
        <dataGrid:GridSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'Amount - {Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />

                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format="'Count - {Count:d}'"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.GroupSummaryRows>
    
</dataGrid:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.GroupSummaryRows.Add(new GridSummaryRow()
{
    ShowSummaryInRow = false,    
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {

        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "Amount - {Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "Count - {Count:d}"
        },
    }
});
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays Group Summary on column basics](Summaries_images/winui-datagrid-group-summary-with-column.png)

### Displaying summary for Row

You can display summary information in row by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `true` and defining summary columns. You have to define [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title) based on [GridSummaryColumn.Name](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Name) property to format summary columns values in row.
 
Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary. 

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">

    <dataGrid:SfDataGrid.GroupSummaryRows>
        <dataGrid:GridSummaryRow Title="Total Price : {PriceAmount} for {ProductCount} products" ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />

                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format="'{Count:d}'"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.GroupSummaryRows>

</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.GroupSummaryRows.Add(new GridSummaryRow()
{
    Title = "Total Price : {PriceAmount} for {ProductCount} products",
    ShowSummaryInRow = true,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "{Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        },
    }
});

{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays Group Summary on a row](Summaries_images/winui-datagrid-group-summary-with-row.png)


### Displaying column summary with title

SfDataGrid supports to show column summary and title summary at the same time. You can show column summary along with title by defining the [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title)  and [GridSummaryRow.TitleColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_TitleColumnCount) property along with defining summary columns. Showing column summary along with title can be only supported if [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) is disabled.

Refer [Defining summary for column](#defining-summary-for-column-1) section to know more about how to define summary columns.

In the below code snippet, `GridSummaryRow.TitleColumnCount` is set as 2 and `GridSummaryRow.Title` is defined along with summary columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"                             
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">
    <dataGrid:SfDataGrid.GroupSummaryRows>
        <dataGrid:GridSummaryRow ShowSummaryInRow="False" TitleColumnCount="2" 
                                   Title="Total Price: {PriceAmount} for {ProductCount} Products" >
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="CustomerName" 
                                              Format=" {Count:d}"
                                              MappingName="CustomerName" 
                                              SummaryType="CountAggregate" />
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format=" {Sum:c}"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format=" {Count:d}"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />                        
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.GroupSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.GroupSummaryRows.Add(new GridSummaryRow()
{
    ShowSummaryInRow = false,
    Title = "Total Price: {PriceAmount} for {ProductCount} Products",
    TitleColumnCount = 2,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
            Name = "CustomerName",
            Format = "{Count:d}",
            MappingName = "CustomerName",
            SummaryType = SummaryType.CountAggregate
        },
		
        new GridSummaryColumn()
        {
            Name = "PriceAmount",
            MappingName = "UnitPrice",
            SummaryType = SummaryType.DoubleAggregate,
            Format = "{Sum:c}"
        },
		
        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        }        
    }
});

{% endhighlight %}
{% endtabs %}

The following screenshot illustrates displaying summary columns with title at same time for `GroupSummaryRow`.

![Group Summary with title in WinUI DataGrid](Summaries_images/winui-datagrid-group-summary-with-title.png)

#### Limitations

The following are the limitations of displaying column summary along with title at same time for `GroupSummaryRow`:

* If [FrozenColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_FrozenColumnCount) is defined lesser than `GridSummaryRow.TitleColumnCount`, the title summary will be spanned to `FrozenColumnCount` range, since spanned range and frozen range cannot be vary.
* Summary columns defined in the `GridSummaryRow.TitleColumnCount` range will not be shown.


## Caption Summaries

SfDataGrid provides built-in support for caption summaries. The caption summary value calculated based on the records in a group and the summary information will be displayed in the caption of group.

Below screen shot shows the built-in caption summary of Group.


![Caption summary in WinUI DataGrid](Summaries_images/winui-datagrid-caption-summary.png)

### Formatting built-in caption summary

By default, the summary value displayed in [CaptionSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CaptionSummaryRowControl.html)  based on [SfDataGrid.GroupCaptionTextFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_GroupCaptionTextFormat) property. 

The default group caption format is `{ColumnName}: {Key} - {ItemsCount} Items`.

* **ColumnName** -   Displays the name of the column currently grouped.
* **Key**   -   Displays the key value of group.
* **ItemsCount** -   Displays the number of items in group.

You can change group caption format to display column name and count alone by setting `GroupCaptionTextFormat` as below,

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid  x:Name="sfDataGrid"
                        AllowGrouping="True"
                        AutoGenerateColumns="True"
                        GroupCaptionTextFormat=" {ColumnName} : {ItemsCount} Items "
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True"/>
{% endhighlight %}
{% endtabs %}


![Caption summary shows with group caption text format in WinUI DataGrid](Summaries_images/winui-datagrid-group-caption-text-format.png)

### Defining summary for column

You can display summary information in the column by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `false` and defining summary columns. To calculate summary based on column you have to specify the below properties,

1. [GridSummaryColumn.MappingName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_MappingName) – MappingName of the column (Property name of data object) that you want calculate summary.

2. [GridSummaryColumn.SummaryType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_SummaryType) – SfDataGrid provides different built-in summary calculation functions for various types.

3. [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format) – Used to define format string for summary based on support function name’s in specified SummaryType.

Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary and [Aggregate Types](#aggregate-types) section to know about different Summary Type’s.

In the below code snippet, summary is defined for `UnitPrice` and `ProductName` columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True">
            
    <dataGrid:SfDataGrid.CaptionSummaryRow>
        <dataGrid:GridSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                                Format="'{Sum:c}'"
                                                MappingName="UnitPrice"
                                                SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                                Format="'{Count:d}'"
                                                MappingName="ProductName"
                                                SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.CaptionSummaryRow>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.CaptionSummaryRow = new GridSummaryRow()
{
    ShowSummaryInRow = false,                
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {

        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "{Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        },
    }
};
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays caption Summary on column basics](Summaries_images/winui-datagrid-caption-summary-with-column.png)

### Displaying summary for Row

You can display summary information in row by setting [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) to `true` and defining summary columns. You have to define [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title) based on [GridSummaryColumn.Name](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Name) property to format summary columns values in row.
 
Refer [Formatting Summary](#formatting-summary) section to know more about how to format summary. 


{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">

    <dataGrid:SfDataGrid.CaptionSummaryRow>
        <dataGrid:GridSummaryRow Title="Total Price : {PriceAmount} for {ProductCount} Products" ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format="'{Count:d}'"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.CaptionSummaryRow>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.CaptionSummaryRow = new GridSummaryRow()
{
    ShowSummaryInRow = true,
    Title = "Total Price: {PriceAmount} for {ProductCount} Products",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {

        new GridSummaryColumn()
        { 
            Name = "PriceAmount", 
            MappingName = "UnitPrice", 
            SummaryType = SummaryType.DoubleAggregate, 
            Format = "{Sum:c}"
        }, 

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        },
    }
};

{% endhighlight %}
{% endtabs %}


![WinUI DataGrid displays caption Summary on a row](Summaries_images/winui-datagrid-caption-summary-with-row.png)


### Displaying column summary with title

SfDataGrid supports to show column summary and title summary at the same time. You can show column summary along with title by defining the [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title) and [GridSummaryRow.TitleColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_TitleColumnCount) property along with defining summary columns. Showing column summary along with title can be only supported if [GridSummaryRow.ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) is disabled.

Refer [Defining summary for column](#defining-summary-for-column-2) section to know more about how to define summary columns.

In the below code snippet, `GridSummaryRow.TitleColumnCount` is set as 2 and `GridSummaryRow.Title` is defined along with summary columns.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">
    <dataGrid:SfDataGrid.CaptionSummaryRow>
        <dataGrid:GridSummaryRow  ShowSummaryInRow="False" TitleColumnCount="2" 
		                            Title=" {ColumnName} : {Key} - {ItemsCount} Items ">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="CustomerName" 
                                              Format=" {Count:d}"
                                              MappingName="CustomerName" 
                                              SummaryType="CountAggregate" />
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format=" {Sum:c}"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
                <dataGrid:GridSummaryColumn Name="ProductCount"
                                              Format=" {Count:d}"
                                              MappingName="ProductName"
                                              SummaryType="CountAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridSummaryRow>
    </dataGrid:SfDataGrid.CaptionSummaryRow>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.CaptionSummaryRow = new GridSummaryRow()
{
    ShowSummaryInRow = false,
    Title = "{ColumnName} : {Key} - {ItemsCount} Items",
    TitleColumnCount = 2,
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
            Name = "CustomerName",
            Format = "{Count:d}",
            MappingName = "CustomerName",
            SummaryType = SummaryType.CountAggregate
        },

        new GridSummaryColumn()
        {
            Name = "PriceAmount",
            MappingName = "UnitPrice",
            SummaryType = SummaryType.DoubleAggregate,
            Format = "{Sum:c}"
        },

        new GridSummaryColumn()
        {
            Name = "ProductCount",
            MappingName = "ProductName",
            SummaryType = SummaryType.CountAggregate,
            Format = "{Count:d}"
        }
    }
};

{% endhighlight %}
{% endtabs %}

The following screenshot illustrates displaying summary columns with title at same time for `CaptionSummaryRow`.

![Caption summary columns with title in WinUI DataGrid](Summaries_images/winui-datagrid-caption-summary-with-title.png)

#### Limitations

The following are the limitations of displaying column summary along with title at same time for `CaptionSummaryRow`:

* If [FrozenColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_FrozenColumnCount) is defined lesser than `GridSummaryRow.TitleColumnCount`, the title summary will be spanned to `FrozenColumnCount` range, since spanned range and frozen range cannot be vary.
* Summary columns defined in the `GridSummaryRow.TitleColumnCount` range will not be shown.


## Formatting summary

In the below sections formatting is explained using TableSummary. In the same way, you can format group and caption summaries also.

### Defining Summary Function

In the below code snippet [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format) property is defined to display sum of `UnitPrice` by specifying the function name inside curly braces.
  
N> [DoubleAggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_DoubleAggregate) is used as SummaryType which has Count, Max, Min, Average and Sum functions.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">

    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid shows with sum function](Summaries_images/winui-datagrid-with-sum-function.png)

### Formatting Summary Value

You can format the summary value by setting the appropriate format after the aggregate function followed by colon(:) in  `GridSummaryColumn.Format` property.

In the below code snippet `UnitPrice` column summary is formatted using `c` format specifier. Refer [here](https://msdn.microsoft.com/en-us/library/dwhawy9k.aspx?f=255&MSPPError=-2147217396) to know about how to set different format.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True">
    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![Formatting summary value in WinUI DataGrid](Summaries_images/winui-datagrid-summary-value-formatting.png)

### Displaying additional Content in Summary

You can append additional content with summary value using  `GridSummaryColumn.Format` property.

In the below code snippet `Total UnitPrice: ` text is appended before summary value.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"                               
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">
                       
    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow ShowSummaryInRow="False">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'Total UnitPrice : {Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
    
</dataGrid:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![WinUI DataGrid shows with additional summary content](Summaries_images/winui-datagrid-additional-summary-content.png)

### Formatting Summary for Row using Title Property

You can format the summary value for row using [GridSummaryRow.Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_Title) when `ShowSummaryInRow` set to `true`.

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">
    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow Title=" Total Price : {PriceAmount} "  
                                        ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>
                <dataGrid:GridSummaryColumn Name="PriceAmount"
                                              Format="'{Sum:c}'"
                                              MappingName="UnitPrice"
                                              SummaryType="DoubleAggregate" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![Formatting summary value with title in WinUI DataGrid](Summaries_images/winui-datagrid-format-summary-using-title.png)

## Aggregate Types

You can specify the different summary aggregate types by using [GridSummaryColumn.SummaryType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_SummaryType) property and use the built-in function in [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format).

The following are the list of predefined aggregate types and its built-in functions.

<table>
<tr>
<th>
Aggregate Type
</th>
<th>
Built-in function
</th>
</tr>
<tr>
<td>
{{'[CountAggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_CountAggregate)'| markdownify }}
</td>
<td>
Count
</td>
</tr>
<tr>
<td>
{{'[Int32Aggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_Int32Aggregate)'| markdownify }}
</td>
<td>
Count, Max, Min, Average and Sum
</td>
</tr>
<tr>
<td>
{{'[DoubleAggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_DoubleAggregate)'| markdownify }}
</td>
<td>
Count, Max, Min, Average and Sum
</td>
</tr>
<tr>
<td>
{{'[Custom](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_Custom)'| markdownify }}
</td>
<td>
Used for custom summaries
</td>
</tr>
</table>

## Calculate summary for selected rows

SfDataGrid calculates the summaries for all records by default. You can calculate the summaries for selected records by using the [SfDataGrid.SummaryCalculationUnit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_SummaryCalculationUnit) or [GridSummaryRow.CalculationUnit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_CalculationUnit) property.
This is applicable for all type of summary rows such as table, caption and group summary.

In the below code snippet, the summaries for selected records are calculated for the top positioned `TableSummaryRow` and the summaries for all records are calculated for the bottom positioned `TableSummaryRow`.

{% tabs %}
{% highlight xaml %}
  <dataGrid:SfDataGrid x:Name="sfDataGrid" 
                        ItemsSource="{Binding Orders}"
                        SelectionMode="Multiple"
                        AutoGenerateColumns="True">
     <dataGrid:SfDataGrid.TableSummaryRows>
         <dataGrid:GridTableSummaryRow ShowSummaryInRow="True" Title="Total Price for all records: {UnitPrice}">
             <dataGrid:GridSummaryRow.SummaryColumns>
                 <dataGrid:GridSummaryColumn Name="UnitPrice"
                                       Format="'{Sum:c}'"
                                       MappingName="UnitPrice"
                                       SummaryType="DoubleAggregate" />
             </dataGrid:GridSummaryRow.SummaryColumns>
         </dataGrid:GridTableSummaryRow>
		 
         <dataGrid:GridTableSummaryRow ShowSummaryInRow="True" Title="Total Price for selected records: {UnitPrice}" CalculationUnit="SelectedRows" Position="Top">
             <dataGrid:GridSummaryRow.SummaryColumns>
                 <dataGrid:GridSummaryColumn Name="UnitPrice"
                                       Format="'{Sum:c}'"
                                       MappingName="UnitPrice"
                                       SummaryType="DoubleAggregate" />
             </dataGrid:GridSummaryRow.SummaryColumns>
         </dataGrid:GridTableSummaryRow>
     </dataGrid:SfDataGrid.TableSummaryRows>
 </dataGrid:SfDataGrid>

{% endhighlight %}
{% highlight c# %}

GridTableSummaryRow tableSummaryRow1 = new GridTableSummaryRow()
{
    ShowSummaryInRow = true,
    Position = TableSummaryRowPosition.Top,
    CalculationUnit = SummaryCalculationUnit.SelectedRows,
    Title = "Total Price for selected records: {UnitPrice}",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
           Name = "UnitPrice",
           Format = "{Sum:c}",
           MappingName = "UnitPrice",
           SummaryType = SummaryType.DoubleAggregate
        }
    }
};

GridTableSummaryRow tableSummaryRow2 = new GridTableSummaryRow()
{
    ShowSummaryInRow = true,
    Position = TableSummaryRowPosition.Bottom,
    Title = "Total Price for all records: {UnitPrice}",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        {
            Name = "UnitPrice",
            Format= "{Sum:c}",
            MappingName = "UnitPrice",
            SummaryType = SummaryType.DoubleAggregate
        }
    }
};

this.sfDataGrid.TableSummaryRows.Add(tableSummaryRow1);
this.sfDataGrid.TableSummaryRows.Add(tableSummaryRow2);

{% endhighlight %}
{% endtabs %}

![Calculate selected records summary in WinUI DataGrid](Summaries_images/winui-datagrid-calculate-records.png)

N> The `GridSummaryRow.CalculationUnit` takes higher priority than the `SfDataGrid.SummaryCalculationUnit`.

### Limitation

[SummaryCalculationUnit.SelectedRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryCalculationUnit.html#Syncfusion_UI_Xaml_Data_SummaryCalculationUnit_SelectedRows) or [SummaryCalculationUnit.Mixed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryCalculationUnit.html#Syncfusion_UI_Xaml_Data_SummaryCalculationUnit_Mixed) will not be considered for cell selection.

## Custom summaries


SfDataGrid allows you to implement your own aggregate functions, when the built-in aggregate functions don’t meet your requirement.

You can calculate the summary values based on custom logic using [GridSummaryColumn.CustomAggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_CustomAggregate) property.

### Implementing custom aggregate

1. Create custom aggregate class by deriving from [ISummaryAggregate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.ISummaryAggregate.html) interface.

2. In the `CalculateAggregateFunc` method, you have to calculate the summary and assign it to the property.
 
In the below code snippet, the Standard Deviation is calculated for quantity of products.

{% tabs %}
{% highlight c# %}
public class CustomAggregate : ISummaryAggregate
{
 
    public CustomAggregate()
    {
    }
 
    public double StdDev { get; set; }
 
    public Action<System.Collections.IEnumerable, string, System.Reflection.PropertyInfo> CalculateAggregateFunc()
    {
        return (items, property, pd) =>
        {
            var enumerableItems = items as IEnumerable<OrderInfo>;
 
            if (pd.Name == "StdDev")
            {
                this.StdDev = enumerableItems.StdDev<OrderInfo>(q => q.UnitPrice);
            }
        };
    }
}

public static class LinqExtensions
{
    public static double StdDev<T>(this IEnumerable<T> values, Func<T, double?> selector)
    {
        double ret = 0;
        var count = values.Count();

        if (count > 0)
        {                
            double? avg = values.Average(selector);       
            double sum = values.Select(selector).Sum(d =>
            {
                if (d.HasValue)
                {
                    return Math.Pow(d.Value - avg.Value, 2);
                }
                return 0.0;
            });                
            ret = Math.Sqrt((sum) / (count - 1));
        }
        return ret;
    }
}

{% endhighlight %}
{% endtabs %}

3.Assign the custom aggregate to `GridSummaryColumn.CustomAggregate` property and set the [SummaryType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_SummaryType) as [Custom](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryType.html#Syncfusion_UI_Xaml_Data_SummaryType_Custom). [GridSummaryColumn.Format](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryColumn.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryColumn_Format) property is defined based on property name in custom aggregate `StdDev`.

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <local:CustomAggregate x:Key="customAggregate" />
</Page.Resources>

<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">
					   
    <dataGrid:SfDataGrid.TableSummaryRows>
        <dataGrid:GridTableSummaryRow Name="Total Products"
                                        Title="Standard Deviation: {UnitPrice}"
                                        Position="Top"
                                        ShowSummaryInRow="True">
            <dataGrid:GridSummaryRow.SummaryColumns>

                <dataGrid:GridSummaryColumn   Name="UnitPrice"
                                                CustomAggregate="{StaticResource customAggregate}"
                                                Format="'{StdDev:##.###}'"
                                                MappingName="UnitPrice"
                                                SummaryType="Custom" />
            </dataGrid:GridSummaryRow.SummaryColumns>
        </dataGrid:GridTableSummaryRow>
    </dataGrid:SfDataGrid.TableSummaryRows>
</dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.TableSummaryRows.Add(new GridTableSummaryRow()
{
    ShowSummaryInRow = true,
    Position = TableSummaryRowPosition.Top,
    Title = "Standard Deviation: {UnitPrice}",
    SummaryColumns = new ObservableCollection<ISummaryColumn>()
    {
        new GridSummaryColumn()
        { 
            Name = "UnitPrice", 
            MappingName = "UnitPrice", 
            CustomAggregate = new CustomAggregate(),
            SummaryType = SummaryType.Custom, 
            Format = "{StdDev:##.###}"
        },      
    }
});
{% endhighlight %}
{% endtabs %}

![Custom aggregate summaries in WinUI SfDataGrid](Summaries_images/winui-datagrid-custom-aggregate-summaries.png)

## Overriding Summary Renderer

Each summary cell is associated with its own renderer and you can customize it by overriding the available virtual methods in the renderer. 

There will be specific key for each summary row. You can remove and add the key from [SfDataGrid.CellRenderers](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CellRenderers) collection, when the renderer is need to be customized.

<table>
<tr>
<th>
Types of summary
</th>
<th>
Renderer
</th>
<th>
Key
</th>
</tr>
<tr>
<td>
Table summary
</td>
<td>
{{'[GridTableSummaryCellRenderer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Renderers.GridTableSummaryCellRenderer.html)'| markdownify }}
</td>
<td>
TableSummary
</td>
</tr>
<tr>
<td>
Caption summary
</td>
<td>
{{'[GridCaptionSummaryCellRenderer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Renderers.GridCaptionSummaryCellRenderer.html)'| markdownify }}
</td>
<td>
CaptionSummary
</td>
</tr>
<tr>
<td>
Group summary
</td>
<td>
{{'[GridSummaryCellRenderer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Renderers.GridSummaryCellRenderer.html)'| markdownify }}
</td>
<td>
GroupSummary
</td>
</tr>
</table>


### Formatting Table Summary

You can apply number format for numeric values displayed on `GridTableSummaryRow` by overriding the [OnUpdateEditBinding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Renderers.GridTableSummaryCellRenderer.html#Syncfusion_UI_Xaml_DataGrid_Renderers_GridTableSummaryCellRenderer_OnUpdateEditBinding_Syncfusion_UI_Xaml_DataGrid_DataColumnBase_Syncfusion_UI_Xaml_DataGrid_GridTableSummaryCell_System_Object_) method in `GridTableSummaryCellRenderer` class.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.CellRenderers.Remove("TableSummary");
this.sfDataGrid.CellRenderers.Add("TableSummary", new GridTableSummaryCellRendererExt());

public class GridTableSummaryCellRendererExt : GridTableSummaryCellRenderer
{

    public override void OnUpdateEditBinding(Syncfusion.UI.Xaml.DataGrid.DataColumnBase dataColumn, Syncfusion.UI.Xaml.DataGrid.GridTableSummaryCell element, object dataContext)
    {

        //Check whether the dataContext is SummaryRecordEntry
        var record = dataContext as SummaryRecordEntry;

        if (!(dataContext is SummaryRecordEntry))
            return;

        //Process each SummaryColumn and get the display text of corresponding summary

        foreach (ISummaryColumn summaryColumn in record.SummaryRow.SummaryColumns)
        {

            if (!summaryColumn.MappingName.Contains(dataColumn.GridColumn.MappingName))
                continue;
            string summaryText = string.Empty;

            if (record.SummaryRow.ShowSummaryInRow)
                summaryText = SummaryCreator.GetSummaryDisplayTextForRow(record, this.DataGrid.View);

            else
                summaryText = SummaryCreator.GetSummaryDisplayText(record, dataColumn.GridColumn.MappingName, this.DataGrid.View);

            if (!string.IsNullOrEmpty(summaryText))
            {

                //Create new number format and apply it to summary columns 
                NumberFormatInfo format = new NumberFormatInfo();
                format.NumberDecimalDigits = 3;
                format.NumberDecimalSeparator = "*";
                format.NumberGroupSeparator = ",";

                //Number format is applied to summary columns                    
                element.Content = Convert.ToDouble(double.Parse(summaryText, NumberStyles.Currency)).ToString("N", format);
            }
        }
    }
}
{% endhighlight %}
{% endtabs %}


![Table summary formatting using renderer in WinUI DataGrid](Summaries_images/winui-datagrid-summary-format.png)


### Customizing GroupCaptionText

You can apply different group caption text format for available groups based on certain conditions by deriving the `GridCaptionSummaryCellRenderer` class .

For example, the group caption text is customized based on the group name and items count of the column.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.CellRenderers.Remove("CaptionSummary");
this.sfDataGrid.CellRenderers.Add("CaptionSummary", new GridCaptionSummaryCellRendererExt());

public class GridCaptionSummaryCellRendererExt : GridCaptionSummaryCellRenderer
{    
    public override void OnUpdateEditBinding(Syncfusion.UI.Xaml.DataGrid.DataColumnBase dataColumn, Syncfusion.UI.Xaml.DataGrid.GridCaptionSummaryCell element, object dataContext)
    {

        if (element.DataContext is Group && this.DataGrid.View.GroupDescriptions.Count > 0)
        {
            var groupRecord = element.DataContext as Group;                
            var groupedColumn = this.GetGroupedColumn(groupRecord);

            if (this.DataGrid.CaptionSummaryRow == null)
            {

                if (this.DataGrid.View.GroupDescriptions.Count < groupRecord.Level)
                    return;

                //Set the CaptionSummaryCell text as customized.
                element.Content = GetCustomizedCaptionText(groupedColumn.HeaderText, groupRecord.Key, groupRecord.ItemsCount);
            }

            else if (this.DataGrid.CaptionSummaryRow.ShowSummaryInRow)
            {
                element.Content = SummaryCreator.GetSummaryDisplayTextForRow(groupRecord.SummaryDetails, this.DataGrid.View, groupedColumn.HeaderText);
            }

            else
                element.Content = SummaryCreator.GetSummaryDisplayText(groupRecord.SummaryDetails, dataColumn.GridColumn.MappingName, this.DataGrid.View);
        }
    }

    private GridColumn GetGroupedColumn(Group group)
    {
        var groupDesc = this.DataGrid.View.GroupDescriptions[group.Level - 1];

        foreach (var column in this.DataGrid.Columns)
        {

            if (column.MappingName == groupDesc.PropertyName)
            {
                return column;
            }
        }
        return null;
    }

    private string GetCustomizedCaptionText(string columnName, object groupName, int itemsCount)
    {

        //entryText - instead of "Items", the entryText is assigned to Customize the CaptionSummaryCell Text.
        string entryText = string.Empty;

        if (itemsCount < 20)
            entryText = "entries in the Group";

        else if (itemsCount < 40)
            entryText = "elements in the Group";

        else if (itemsCount < 60)
            entryText = "list in the Group";

        else
            entryText = "items in the Group";

        if (groupName.ToString().Equals("1001"))
            groupName = "Thousand and One";

        else if (groupName.ToString().Equals("1002"))
            groupName = "Thousand and Two";

        else if (groupName.ToString().Equals("1004"))
            groupName = "Thousand and Four";
        return string.Format("{0}: {1} - {2} {3}", columnName, groupName, itemsCount, entryText);
    }
}

{% endhighlight %}
{% endtabs %}

![Customized group caption text format in WinUI DataGrid](Summaries_images/winui-datagrid-group-caption-text.png)
