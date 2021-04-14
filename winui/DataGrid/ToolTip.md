---
layout: post
title: ToolTip in WinUI DataGrid control | Syncfusion
description: Learn here all about ToolTip support in Syncfusion WinUI DataGrid(SfDataGrid) control and more details.
platform: winui
control: DataGrid
documentation: ug
---

# ToolTip in WinUI DataGrid

ToolTip provides the support to show the pop-up window that displays the information when the mouse hovers in cells of SfDataGrid. 

## Record cell tooltip

You can enable the ToolTip for the [GridCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridCell.html) by setting the [SfDataGrid.ShowToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_ShowToolTip) as `true`.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

<dataGrid:SfDataGrid x:Name="sfDataGrid" 
                       AutoGenerateColumns="True"
                       ShowToolTip="True"
                       ItemsSource="{Binding Orders}" >
</dataGrid:SfDataGrid>

{% endhighlight %}

{% highlight c# %}

this.sfDataGrid.ShowToolTip = true;

{% endhighlight %}
{% endtabs %}

You can enable the ToolTip for the particular column by setting the [GridColumn.ShowToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ShowToolTip) as `true`.

{% tabs %}
{% highlight xaml %}

<dataGrid:SfDataGrid.Columns>
    <dataGrid:GridTextColumn HeaderText="Order ID" ShowToolTip="True" MappingName="OrderID" TextAlignment="Right" />
    <dataGrid:GridTextColumn HeaderText="Customer ID" ShowToolTip="True" MappingName="CustomerID" />
</dataGrid:SfDataGrid.Columns>

{% endhighlight %}

{% highlight c# %}

this.sfDataGrid.Columns["OrderID"].ShowToolTip = true;
this.sfDataGrid.Columns["CustomerID"].ShowToolTip = true;

{% endhighlight %}
{% endtabs %}

N> `GridColumn.ShowToolTip` takes higher priority than `SfDataGrid.ShowToolTip`.

![Displaying tooltip for record cell in WinUI DataGrid](ToolTip_images/Displaying-tooltip-for-record-cell-in-WinUI-DataGrid.png)

## Header tooltip

You can enable the ToolTip for the header cell by setting the [GridColumn.ShowHeaderToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ShowHeaderToolTip) as `true`.

{% tabs %}
{% highlight xaml %}

<dataGrid:SfDataGrid.Columns>
    <dataGrid:GridTextColumn HeaderText="Order ID" ShowHeaderToolTip="True" MappingName="OrderID" TextAlignment="Right" />
</dataGrid:SfDataGrid.Columns>

{% endhighlight %}

{% highlight c# %}

this.sfDataGrid.Columns["OrderID"].ShowHeaderToolTip = true;

{% endhighlight %}
{% endtabs %}

![Displaying tooltip for header in WinUI DataGrid](ToolTip_images/Displaying-tooltip-for-header-in-WinUI-DataGrid.png)

## ToolTip Customization

You can customize the template of ToolTip by using the [GridColumn.ToolTipTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ToolTipTemplate) and [GridColumn.ToolTipTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ToolTipTemplateSelector) properties. 

### Customize the ToolTip using ToolTipTemplate

You can customize the appearance of the ToolTip for particular column by setting `GridColumn.ToolTipTemplate`. And you can also customize the appearance of header ToolTip for particular column by [GridColumn.HeaderToolTipTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_HeaderToolTipTemplate) property.

{% tabs %}
{% highlight xaml %}

<Page.Resources>
    <local:StringToImageConverter x:Key="imageConverter" />        
    <DataTemplate x:Key="templateToolTip">
        <Image Height="100" Width="100" Source="{Binding CustomerID,Converter={StaticResource imageConverter}}" />
    </DataTemplate>
</Page.Resources>

<dataGrid:SfDataGrid.Columns>
    <dataGrid:GridTextColumn HeaderText="Order ID"  ShowToolTip="True" MappingName="OrderID" />
    <dataGrid:GridTextColumn HeaderText="Customer ID" ToolTipTemplate="{StaticResource templateToolTip}" ShowToolTip="True" MappingName="CustomerID" />
</dataGrid:SfDataGrid.Columns>

{% endhighlight %}

{% highlight c# %}
public class StringToImageConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        string imagename = value.ToString();
        return "Assets/" + imagename + @".png";
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language)
    {
        return value;
    }
}
{% endhighlight %}
{% endtabs %}

![Displaying tooltip customization using ToolTipTemplate in WinUI DataGrid](ToolTip_images/Displaying-tooltip-customization-using-ToolTipTemplate-in-WinUI-DataGrid.png)

### Customize the ToolTip with ToolTipTemplateSelector

The different ToolTip template can be loaded in a same column conditionally based on data by setting `GridColumn.ToolTipTemplateSelector`

{% tabs %}
{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="toolTip1">
        <Grid>
            <Rectangle Fill="Transparent"/>
            <TextBlock Text="{Binding OrderID}" FontWeight="Bold" Foreground="Red" />
        </Grid>
    </DataTemplate>
    <DataTemplate x:Key="toolTip2">
        <Grid>
            <Rectangle Fill="Transparent"/>
            <TextBlock Text="{Binding OrderID}" FontStyle="Italic" Foreground="Green" />
        </Grid>
    </DataTemplate>
</Page.Resources>

<dataGrid:SfDataGrid.Columns>
    <dataGrid:GridTextColumn HeaderText="Order ID" ShowToolTip="True" MappingName="OrderID" >
        <dataGrid:GridTextColumn.ToolTipTemplateSelector>
            <local:ToolTipTemplateSelector AlternateTemplate="{StaticResource toolTip2}"  DefaultTemplate="{StaticResource toolTip1}" />
        </dataGrid:GridTextColumn.ToolTipTemplateSelector>
    </dataGrid:GridTextColumn>
</dataGrid:SfDataGrid.Columns>

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}

public class ToolTipTemplateSelector : DataTemplateSelector
{
    private DataTemplate _defaultTemplate;

    /// <summary>
    /// Gets or sets DefaultTemplate.
    /// </summary>

    public DataTemplate DefaultTemplate
    {
        get { return _defaultTemplate; }
        set { _defaultTemplate = value; }
    }

    private DataTemplate _alternateTemplate;

    /// <summary>
    /// Gets or Sets AlternateTemplate.
    /// </summary>

    public DataTemplate AlternateTemplate
    {
        get { return _alternateTemplate; }
        set { _alternateTemplate = value; }
    }

    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
        //The item that comes from ToolTipTemplate is DataContextHelper. When set SetCellBoundValue to true, it sets DataContextHelper as DataContext to DataTemplate. Refer property section of CellTemplate.
        OrderInfo orderInfo = item as OrderInfo;

        if (orderInfo == null) return this.DefaultTemplate;

        //use reflection to retrieve property
        Type type = orderInfo.GetType();
        PropertyInfo property = type.GetProperty("OrderID");

        //To see what template needs to be select according to the specified property value.
        if (property.GetValue(orderInfo, null).ToString().Contains('9') || property.GetValue(orderInfo, null).ToString().Contains('4'))
            return this.AlternateTemplate;
        else
            return this.DefaultTemplate;
    }
}

{% endhighlight %}
{% endtabs %}

The below image refers the `DefaultTemplate` which is applied through `ToolTipTemplateSelector`.

![Displaying DefaultTemplate for tooltip using ToolTipTemplateSelector in WinUI DataGrid](ToolTip_images/Displaying-DefaultTemplate-for-tooltip-using-ToolTipTemplateSelector-in-WinUI-DataGrid.png)

The below image refers the `AlternateTemplate` which is applied through `ToolTipTemplateSelector`.

![Displaying AlternateTemplate for tooltip using ToolTipTemplateSelector in WinUI DataGrid](ToolTip_images/Displaying-AlternateTemplate-for-tooltip-using-ToolTipTemplateSelector-in-WinUI-DataGrid.png)

## Events

### CellToolTipOpening event

The [CellToolTipOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CellToolTipOpening) event occurs when any tooltip of the cell is opened. The `CellToolTipOpening` event receives the [GridCellToolTipOpeningEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridCellToolTipOpeningEventArgs.html) as argument which has the following properties:

<ul>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_Column">Column :</a> Gets the hovered cell column in the SfDataGrid.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_Record">Record :</a> Gets the data context of hovered cell.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_RowColumnIndex">RowColumnIndex :</a> Gets the row and column index of the hovered cell.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_ToolTip">ToolTip :</a> Gets the tooltip of the hovered cells.</li>
</ul>

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid Name="sfDataGrid"  
                        CellToolTipOpening="SfDataGrid_CellToolTipOpening"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}" />
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.CellToolTipOpening += SfDataGrid_CellToolTipOpening;

private void SfDataGrid_CellToolTipOpening(object sender, GridCellToolTipOpeningEventArgs e)
{
    
}
{% endhighlight %}
{% endtabs %}
