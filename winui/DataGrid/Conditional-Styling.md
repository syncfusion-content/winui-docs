---
layout: post
title: Conditional styling in WinUI DataGrid control | Syncfusion
description: Learn here all about conditional styling support in Syncfusion WinUI DataGrid(SfDataGrid) control and more.
platform: winui
control: SfDataGrid
documentation: ug
---

# Conditional styling in WinUIF DataGrid (SfDataGrid)

You can style the DataGrid and its inner elements (cells, rows and columns) conditionally based on data Using StyleSelector.

## Cell style

### Conditional styling of cells using style selector

The record cells ([GridCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridCell.html)) can be customized conditionally based on data by setting [SfDataGrid.CellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CellStyleSelector) property and the particular column record cells can be customized by setting [GridColumn.CellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_CellStyleSelector) property and you can get the container as `GridCell` in the StyleSelector.

N> `GridColumn.CellStyleSelector` takes higher priority than `SfDataGrid.CellStyleSelector` property.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style x:Key="redCellStyle" TargetType="syncfusion:GridCell">
        <Setter Property="Foreground" Value="Red" />
    </Style>
    <Style x:Key="blueCellStyle" TargetType="syncfusion:GridCell">
        <Setter Property="Foreground" Value="DarkBlue" />
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="False"
                       CellStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" HeaderText="Order ID" />
        <syncfusion:GridTextColumn MappingName="CustomerID" HeaderText="Customer ID" />
        <syncfusion:GridTextColumn MappingName="CustomerName" HeaderText="Customer Name" />
        <syncfusion:GridTextColumn MappingName="ShipCity" HeaderText="Ship City" />
        <syncfusion:GridTextColumn MappingName="Country" />
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{

    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var data = item as OrderInfo;

        if (data != null && ((container as GridCell).ColumnBase.GridColumn.MappingName == "OrderID"))
        {

            //custom condition is checked based on data.

            if (data.OrderID < 1005)
                return App.Current.Resources["redCellStyle"] as Style;
            return App.Current.Resources["blueCellStyle"] as Style;
        }
        return base.SelectStyleCore(item, container);
    }
}
{% endhighlight %}
{% endtabs %}

Here, GridCell’s are customized based on `OrderID` property of underlying record.

![Conditional styling of WinUI datagrid cells using style selector](Conditional-Styling_images/Conditional-Styling_img1.png)

## Row style

### Conditional styling of rows using style selector

The record rows ([DataGridRowControl](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DataGridRowControl.html) ) can be customized conditionally based on data by setting [SfDataGrid.RowStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_RowStyleSelector) property and you can get the container as `DataGridRowControl` in StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:CustomRowStyleSelector x:Key="rowStyleSelector" />
    <Style x:Key="rowStyle1" TargetType="syncfusion:DataGridRowControl">
        <Setter Property="Background" Value="Bisque" />
    </Style>
    <Style x:Key="rowStyle2" TargetType="syncfusion:DataGridRowControl">
        <Setter Property="Background" Value="Aqua" />
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="False"
                       RowStyleSelector="{StaticResource rowStyleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" HeaderText="Order ID" />
        <syncfusion:GridTextColumn MappingName="CustomerID" HeaderText="Customer ID" />
        <syncfusion:GridTextColumn MappingName="CustomerName" HeaderText="Customer Name" />
        <syncfusion:GridTextColumn MappingName="ShipCity" HeaderText="Ship City" />
        <syncfusion:GridTextColumn MappingName="Country" />
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class CustomRowStyleSelector : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var row = (item as DataRowBase).RowData;
        var data = row as OrderInfo;

        if (data.OrderID < 1004)
            return App.Current.Resources["rowStyle1"] as Style;
        return App.Current.Resources["rowStyle2"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, rows are customized based on `OrderID` property of underlying record.

![Conditional styling of WinUI datagrid rows using style selector](Conditional-Styling_images/Conditional-Styling_img2.png)

## Alternate row style

The appearance of alternating rows can be customized conditionally based on data by setting [SfDataGrid.AlternatingRowStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_AlternatingRowStyleSelector) property.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:StyleSelector x:Key="alternatingRowStyleSelector" />
    <Style x:Key="rowStyle1" TargetType="syncfusion:DataGridRowControl">
        <Setter Property="Background" Value="Bisque" />
    </Style>
    <Style x:Key="rowStyle2" TargetType="syncfusion:DataGridRowControl">
        <Setter Property="Background" Value="Aqua" />
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="False"
                       ItemsSource="{Binding Orders}"
                       AlternatingRowStyleSelector="{StaticResource alternatingRowStyleSelector}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" HeaderText="Order ID" />
        <syncfusion:GridTextColumn MappingName="CustomerID" HeaderText="Customer ID" />
        <syncfusion:GridTextColumn MappingName="CustomerName" HeaderText="Customer Name" />
        <syncfusion:GridTextColumn MappingName="ShipCity" HeaderText="Ship City" />
        <syncfusion:GridTextColumn MappingName="Country" />
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{

    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var row = (item as DataRowBase).RowData;
        var data = row as OrderInfo;

        if (data.OrderID < 1006)
            return App.Current.Resources["rowStyle1"] as Style;
        return App.Current.Resources["rowStyle2"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, alternating rows are customized based on `OrderID` property of underlying record.

![WinUI datagrid alternate row style](Conditional-Styling_images/Conditional-Styling_img3.png)

## Caption summary cell style

### Conditional styling of caption summary cells using style selector

The appearance of caption summary cell can be customized conditionally based on summary value by setting [SfDataGrid.CaptionSummaryCellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CaptionSummaryCellStyleSelector) and you can get the container as `GridCaptionSummaryCell` using StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="selector"/>
    <Style TargetType="syncfusion:GridCaptionSummaryCell" x:Key="captionSummaryStyle">
        <Setter Property="Foreground" Value="Red"/>
    </Style>
</Application.Resources>


<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       CaptionSummaryCellStyleSelector="{StaticResource selector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.CaptionSummaryRow>
        <syncfusion:GridSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomertCount"
                                        Format="'{Count:c}'"
                                        MappingName="CustomerName"
                                        SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.CaptionSummaryRow>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{

    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var summaryValue = (item as Group).SummaryDetails.SummaryValues[0];
        var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
        var calculatedValue = aggregateValue.Value;

        //custom condition is checked.
        if ((double)calculatedValue > 1005)
            return App.Current.Resources["captionSummaryStyle"] as Style;
        return base.SelectStyleCore(item, container);
    }
}
{% endhighlight %}
{% endtabs %}

Here, caption summary cells are customized based on `OrderID` summary value.

![Conditional styling of datagrid caption summary cells using style selector](Conditional-Styling_images/Conditional-Styling_img4.png)

### Conditional styling of caption summary cell based on column

The caption summary cells can be conditionally customized summary column. 

Here, caption summary cells are customized based on `OrderID` summary column.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="selector"/>
    <Style TargetType="syncfusion:GridCaptionSummaryCell" x:Key="captionSummaryStyle">
        <Setter Property="Foreground" Value="Red"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       CaptionSummaryCellStyleSelector="{StaticResource selector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.CaptionSummaryRow>
        <syncfusion:GridSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomertCount"
                                        Format="'{Count:c}'"
                                        MappingName="CustomerName"
                                        SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.CaptionSummaryRow>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{

    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var cell = container as GridCaptionSummaryCell;

        if (cell.ColumnBase.GridColumn.MappingName == "OrderID")
        {
            var groupKey = (int)(item as Group).Key;

            //custom condition is checked.
            if (groupKey < 1005)
                return App.Current.Resources["captionSummaryStyle"] as Style;
        }
        return null;
    }
}
{% endhighlight %}
{% endtabs %}

![Conditional styling of datagrid caption summary cell based on column](Conditional-Styling_images/Conditional-Styling_img5.png)

## Group summary cell style

Group summary cells can be customized conditionally by getting particular summary value from [SummaryValues](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryRecordEntry.html#Syncfusion_UI_Xaml_Data_SummaryRecordEntry_SummaryValues) through converter or style selector. Likewise, you can also customize the group summary cell based on various properties exposed in [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html) (example: [ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) property).

### Conditional styling of group summary cell using style selector

The appearance of group summary cell can be customized conditionally based on summary value by setting [SfDataGrid.GroupSummaryCellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CaptionSummaryRowStyleSelector) and you can get the container as `GridGroupSummaryCell` in StyleSelector.

Here, group summary cells are customized based on summary values whether it’s positive or negative.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GridGroupSummaryCell" x:Key="customGroupSummary">
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
    <Style TargetType="syncfusion:GridGroupSummaryCell" x:Key="customGroupSummary1">
        <Setter Property="Background" Value="Red"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       GroupSummaryCellStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.GroupSummaryRows>
        <syncfusion:GridSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                      Format="'Amount - {Sum:c}'"
                                      MappingName="OrderID"
                                      SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomerCount"
                                      Format="'Count - {Count:d}'"
                                      MappingName="CustomerName"
                                      SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
        <syncfusion:GridSummaryRow Title="TotalPrice:  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.GroupSummaryRows>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{

    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var summaryValue = (item as SummaryRecordEntry).SummaryValues[0];
        var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
        var calculatedValue = aggregateValue.Value;

        //custom condition is checked.
        if ((double)calculatedValue < 1005)
            return App.Current.Resources["customGroupSummary1"] as Style;
        return App.Current.Resources["customGroupSummary"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, group summary cells are customized based on `TotalPrice` summary value.

![Conditional styling of datagrid group summary cell using style selector](Conditional-Styling_images/Conditional-Styling_img8.png)

### Conditional styling of group summary cell based on column

The group summary cells can be conditionally customized based on summary column. 

Here, group summary cells are customized based on `TotalPrice` summary column.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GridGroupSummaryCell" x:Key="customGroupSummary">
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
    <Style TargetType="syncfusion:GridGroupSummaryCell" x:Key="customGroupSummary1">
        <Setter Property="Background" Value="Red"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       GroupSummaryCellStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.GroupSummaryRows>
        <syncfusion:GridSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                      Format="'Amount - {Sum:c}'"
                                      MappingName="OrderID"
                                      SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomerCount"
                                      Format="'Count - {Count:d}'"
                                      MappingName="CustomerName"
                                      SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
        <syncfusion:GridSummaryRow Title="TotalPrice:  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.GroupSummaryRows>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var cell = container as GridGroupSummaryCell;

        if (cell.ColumnBase.GridColumn.MappingName == "OrderID")
        {
            var summaryValue = (item as SummaryRecordEntry).SummaryValues[0];
            var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
            var calculatedValue = aggregateValue.Value;

            //custom condition is checked.
            if (aggregateValue.Key != "Count" && (double)calculatedValue < 1005)
                return App.Current.Resources["customGroupSummary1"] as Style;
        }
        return App.Current.Resources["customGroupSummary"] as Style;
    }
}
{% endhighlight %}
{% endtabs %}

![Conditional styling of datagrid group summary cell based on column](Conditional-Styling_images/Conditional-Styling_img9.png)

## Group summary row style

Group summary row can be customized conditionally by getting particular summary value from [SummaryValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryValue.html#Syncfusion_UI_Xaml_Data_SummaryValue__ctor) through `converter` or `style selector`. Likewise, you can also customize the group summary row based on various properties exposed in [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html) (example: [ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) property).

### Conditional styling of group summary row using style selector

The appearance of group summary row can be customized conditionally based on summary value by setting [SfDataGrid.GroupSummaryRowStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_GroupSummaryRowStyleSelector) and you can get the container as `GridGroupSummaryRowControl` in StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GroupSummaryRowControl" x:Key="customGroupSummary">
        <Setter Property="Background" Value="LightBlue"/>
    </Style>
    <Style TargetType="syncfusion:GroupSummaryRowControl" x:Key="customGroupSummary1">
        <Setter Property="Background" Value="Yellow"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowEditing="True"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       GroupSummaryRowStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.GroupSummaryRows>
        <syncfusion:GridSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                      Format="'Amount - {Sum:c}'"
                                      MappingName="OrderID"
                                      SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomerCount"
                                      Format="'Count - {Count:d}'"
                                      MappingName="CustomerName"
                                      SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
        <syncfusion:GridSummaryRow Title="TotalPrice:  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.GroupSummaryRows>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var summaryRecordEntry = (item as SpannedDataRow).RowData;
        var summaryValue = (summaryRecordEntry as SummaryRecordEntry).SummaryValues[0];
        var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
        var calculatedValue = aggregateValue.Value;

        //custom condition is checked.
        if ((double)calculatedValue % 2 == 0)
            return App.Current.Resources["customGroupSummary1"] as Style;
        return App.Current.Resources["customGroupSummary"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, group summary rows are customized based on `TotalPrice` summary value whether it’s positive or negative.

![Conditional styling of datagrid group summary row using style selector](Conditional-Styling_images/Conditional-Styling_img10.png)

## Table summary cell

Table summary cells can be customized conditionally by getting particular summary value from [SummaryValues](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryRecordEntry.html#Syncfusion_UI_Xaml_Data_SummaryRecordEntry_SummaryValues) through `converter` or `style selector`. Likewise, you can also customize the table summary cell based on various properties exposed in [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.htm) (example: [ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) property).

### Conditional styling of table summary cell using style selector

The appearance of table summary cell can be customized conditionally based on summary value by setting [SfDataGrid.TableSummaryCellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_TableSummaryCellStyleSelector) and you can get the container as `GridTableSummaryCell` in StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary">
        <Setter Property="Foreground" Value="Red"/>
    </Style>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary1">
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Application.Resources>


<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowEditing="True"
                       AllowGrouping="True"
                       AutoGeneratingColumn="dataGrid_AutoGeneratingColumn"
                       ShowGroupDropArea="True"
                       TableSummaryCellStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.TableSummaryRows>
        <syncfusion:GridTableSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                      Format="'Total UnitPrice : {Sum:c}'"
                                      MappingName="OrderID"
                                      SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomerCount"
                                      Format="'Total Customer Count : {Count:d}'"
                                      MappingName="CustomerID"
                                      SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridTableSummaryRow>
        <syncfusion:GridSummaryRow Title="Total Price :  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                              Format="'{Sum:c}'"
                                              MappingName="OrderID"
                                              SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.TableSummaryRows>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var summaryValue = (item as SummaryRecordEntry).SummaryValues[0];
        var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
        var calculatedValue = aggregateValue.Value;
        var cell = container as GridTableSummaryCell;

        //custom condition is checked.
        if ((double)calculatedValue > 8500 && cell.ColumnBase.GridColumn.MappingName == "OrderID")
            return App.Current.Resources["customTableSummary"] as Style;
        return App.Current.Resources["customTableSummary1"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, table summary cells are customized based on `TotalPrice` summary value.

![Conditional styling of datagrid table summary cell using style selector](Conditional-Styling_images/Conditional-Styling_img11.png)

### Conditional styling of table summary cell based on column

The table summary cells can be conditionally customized based on summary column.

Here, table summary cells are customized based on `TotalPrice` summary column.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary">
        <Setter Property="Foreground" Value="Red"/>
    </Style>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary1">
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Application.Resources>


<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       AllowEditing="True"
                       AllowGrouping="True"
                       AutoGeneratingColumn="dataGrid_AutoGeneratingColumn"
                       ShowGroupDropArea="True"
                       TableSummaryCellStyleSelector="{StaticResource styleSelector}"
                       ItemsSource="{Binding Orders}"
                       ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.TableSummaryRows>
        <syncfusion:GridTableSummaryRow ShowSummaryInRow="False">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="PriceAmount"
                                      Format="'Total UnitPrice : {Sum:c}'"
                                      MappingName="OrderID"
                                      SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="CustomerCount"
                                      Format="'Total Customer Count : {Count:d}'"
                                      MappingName="CustomerID"
                                      SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridTableSummaryRow>
        <syncfusion:GridSummaryRow Title="Total Price :  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                              Format="'{Sum:c}'"
                                              MappingName="OrderID"
                                              SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.TableSummaryRows>
</syncfusion:SfDataGrid>{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var cell = container as GridTableSummaryCell;

        // column name is checked.
        if (cell.ColumnBase.GridColumn.MappingName == "OrderID")
            return App.Current.Resources["customTableSummary"] as Style;
        return App.Current.Resources["customTableSummary1"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

![Conditional styling of datagrid table summary cell based on column](Conditional-Styling_images/Conditional-Styling_img12.png)

## Table summary row style

Table summary rows can be customized conditionally by getting particular summary value from [SummaryValues](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.SummaryRecordEntry.html#Syncfusion_UI_Xaml_Data_SummaryRecordEntry_SummaryValues) through converter or style selector. Likewise, you can also customize the table summary row based on various properties exposed in [GridSummaryRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html) (example: [ShowSummaryInRow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridSummaryRow.html#Syncfusion_UI_Xaml_DataGrid_GridSummaryRow_ShowSummaryInRow) property).

### Conditional styling of table summary row using style selector

The appearance of table summary row can be customized conditionally based on summary value by setting [SfDataGrid.TableSummaryRowStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_TableSummaryRowStyleSelector) and you can get the container as `GridTableSummaryRowControl` in StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:TableSummaryRowControl" x:Key="tableSummaryRowStyle">
        <Setter Property="Background" Value="Bisque"/>
    </Style>
    <Style TargetType="syncfusion:TableSummaryRowControl" x:Key="tableSummaryRowStyle1">
        <Setter Property="Background" Value="LightBlue"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                        AutoGenerateColumns="True"
                        AllowEditing="True"
                        AllowGrouping="True"
                        ShowGroupDropArea="True"
                        TableSummaryRowStyleSelector="{StaticResource styleSelector}"
                        ItemsSource="{Binding Orders}"
                        ColumnWidthMode="Star">
    <syncfusion:SfDataGrid.TableSummaryRows>
        <syncfusion:GridTableSummaryRow Position="Top" ShowSummaryInRow="False">
            <syncfusion:GridTableSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="price"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="customerID"
                                        Format="'{Count:n0}'"
                                        MappingName="CustomerID"
                                        SummaryType="CountAggregate" />
            </syncfusion:GridTableSummaryRow.SummaryColumns>
        </syncfusion:GridTableSummaryRow>
        <syncfusion:GridSummaryRow Title="Count : {count}, Total Price :  {totalPrice}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="count"
                                                Format="'{Count:n0}'"
                                                MappingName="CustomerID"
                                                SummaryType="DoubleAggregate" />
                <syncfusion:GridSummaryColumn Name="totalPrice"
                                        Format="'{Sum:c}'"
                                        MappingName="OrderID"
                                        SummaryType="DoubleAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.TableSummaryRows>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var summaryRecordEntry = (item as SpannedDataRow).RowData;
        var summaryValue = (summaryRecordEntry as SummaryRecordEntry).SummaryValues[0];
        var aggregateValue = summaryValue.AggregateValues.ElementAt(0);
        var calculatedValue = aggregateValue.Value;

        //custom condition is checked.
        if (aggregateValue.Key != "Count" && (double)calculatedValue < 0)
            return App.Current.Resources["tableSummaryRowStyle"] as Style;
        return App.Current.Resources["tableSummaryRowStyle1"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, table summary rows are customized based on `TotalPrice` summary value.

![Conditional styling of datagrid table summary row using style selector](Conditional-Styling_images/Conditional-Styling_img13.png)

## Table summary cell alignment based on column

The alignment of summary cells can be customized conditionally based on summary column. 

Here, horizontal alignment of table summary cells are changed based on column name. Likewise, you can change the horizontal alignment of group, caption summary cells.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector"/>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary">
        <Setter Property="HorizontalContentAlignment" Value="Center"/>
    </Style>
    <Style TargetType="syncfusion:GridTableSummaryCell" x:Key="customTableSummary1">
        <Setter Property="HorizontalContentAlignment" Value="Right"/>
    </Style>
</Application.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                               AutoGenerateColumns="True"
                               AllowEditing="True"
                               AllowGrouping="True"
                               ShowGroupDropArea="True"
                               TableSummaryCellStyleSelector="{StaticResource styleSelector}"
                               ItemsSource="{Binding Orders}"
                               ColumnWidthMode="Star">
            <syncfusion:SfDataGrid.TableSummaryRows>
                <syncfusion:GridTableSummaryRow Position="Top" ShowSummaryInRow="False">
                    <syncfusion:GridTableSummaryRow.SummaryColumns>
                        <syncfusion:GridSummaryColumn Name="price"
                                                Format="'{Sum:c}'"
                                                MappingName="OrderID"
                                                SummaryType="DoubleAggregate" />
                        <syncfusion:GridSummaryColumn Name="customerID"
                                                Format="'{Count:n0}'"
                                                MappingName="CustomerID"
                                                SummaryType="CountAggregate" />
                    </syncfusion:GridTableSummaryRow.SummaryColumns>
                </syncfusion:GridTableSummaryRow>
                <syncfusion:GridSummaryRow Title="Count : {count}, Total Price :  {totalPrice}" ShowSummaryInRow="True">
                    <syncfusion:GridSummaryRow.SummaryColumns>
                        <syncfusion:GridSummaryColumn Name="count"
                                                Format="'{Count:n0}'"
                                                MappingName="CustomerID"
                                                SummaryType="DoubleAggregate" />
                        <syncfusion:GridSummaryColumn Name="totalPrice"
                                                Format="'{Sum:c}'"
                                                MappingName="OrderID"
                                                SummaryType="DoubleAggregate" />
                    </syncfusion:GridSummaryRow.SummaryColumns>
                </syncfusion:GridSummaryRow>
            </syncfusion:SfDataGrid.TableSummaryRows>
        </syncfusion:SfDataGrid>

{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var cell = container as GridTableSummaryCell;

        // column name is checked.
        if (cell.ColumnBase.GridColumn.MappingName == "OrderID")
            return App.Current.Resources["customTableSummary"] as Style;
        return App.Current.Resources["customTableSummary1"] as Style;
    }
}

{% endhighlight %}
{% endtabs %}

Here, horizontal alignment of `OrderID` column alone left, other column horizontal alignment are changed into right.

![WinUI datagrid summary column alignment](Conditional-Styling_images/Conditional-Styling_img14.png)

