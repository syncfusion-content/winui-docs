---
layout: post
title: ToolTip in WinUI TreeGrid control | Syncfusion®
description: Learn here all about ToolTip support in Syncfusion® WinUI TreeGrid(SfTreeGrid) control with customization support and more.
platform: winui
control: SfTreeGrid
documentation: ug
---

# ToolTip in WinUI TreeGrid

Tooltip supports showing the pop-up window that displays the information when the mouse hovers over a cell of the SfTreeGrid.

## Record cell tooltip

You can enable tooltip for the TreeGridCell by setting the [SfTreeGrid.ShowToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_ShowToolTip) property to `true`.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid Name="treeGrid"
                       ColumnWidthMode="Star"
                       ShowToolTip="True"
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"
                       ChildPropertyName="ReportsTo"
                       ItemsSource="{Binding Employees}"
                       ParentPropertyName="ID"
                       SelfRelationRootValue="-1" />	

{% endhighlight %}
{% highlight c# %}

this.treeGrid.ShowToolTip = true;

{% endhighlight %}
{% endtabs %}

You can enable the tooltip of a particular column by setting the [TreeGridColumn.ShowToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ShowToolTip) property to `true`.

{% tabs %}
{% highlight xaml %}

<treeGrid:TreeGridTextColumn HeaderText="First Name" MappingName="FirstName" ShowToolTip="True" />
<treeGrid:TreeGridTextColumn HeaderText="Last Name" MappingName="LastName" ShowToolTip="True" />

{% endhighlight %}
{% highlight c# %}

this.treeGrid.Columns["FirstName"].ShowToolTip = true;
this.treeGrid.Columns["LastName"].ShowToolTip = true;

{% endhighlight %}
{% endtabs %}

N> It has higher priority than [SfTreeGrid.ShowToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_ShowToolTip).

<img src="Tooltip_images/Tooltip_img1.png" alt="Showing ToolTip for record cell in WinUI TreeGrid" width="100%" Height="Auto"/>

## Header tooltip

You can enable the tooltip of a header cell by setting the [TreeGridColumn.ShowHeaderToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ShowHeaderToolTip) property to `true`.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid.Columns>
    <treeGrid:TreeGridTextColumn HeaderText="First Name" MappingName="FirstName" ShowHeaderToolTip="True" />
</treeGrid:SfTreeGrid.Columns>

{% endhighlight %}
{% highlight c# %}

this.treeGrid.Columns["FirstName"].ShowHeaderToolTip = true;

{% endhighlight %}
{% endtabs %}

<img src="Tooltip_images/ToolTip_img2.png" alt="Showing ToolTip for header cell in WinUI TreeGrid" width="100%" Height="Auto"/>

## Tooltip customization

You can customize the template of ToolTip by using the [TreeGridColumn.ToolTipTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ToolTipTemplate) and [TreeGridColumn.ToolTipTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_ToolTipTemplateSelector) properties. 

#### Customize the tooltip using ToolTipTemplate

You can customize appearance of the tooltip of a particular column by setting the TreeGridColumn.ToolTipTemplate. You can also customize appearance of the header tooltip of a particular column by using the [TreeGridColumn.HeaderToolTipTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_HeaderToolTipTemplate) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid>
    <treeGrid:SfTreeGrid.Resources>
        <local:StringToImageConverter x:Key="ImageConverter" />
        <DataTemplate x:Key="TemplateToolTip">
            <Grid>
                <Grid.RowDefinitions>
                    <RowDefinition Height="*"/>
                    <RowDefinition Height="*"/>
                </Grid.RowDefinitions>
                <Image Height="100" Width="100" Source="{Binding LastName,Converter={StaticResource ImageConverter}}" />
                <TextBlock Grid.Row="1" Text="{Binding LastName}" HorizontalAlignment="Center"/>
            </Grid>
        </DataTemplate>
    </treeGrid:SfTreeGrid.Resources>
    <treeGrid:SfTreeGrid.Columns>    
        <treeGrid:TreeGridTextColumn HeaderText="Last Name" MappingName="LastName" ToolTipTemplate="{StaticResource TemplateToolTip}" ShowToolTip="True" />   
    </treeGrid:SfTreeGrid.Columns>
</treeGrid:SfTreeGrid>

{% endhighlight %}
{% highlight c# %}

public class StringToImageConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        string imagename = value.ToString();
        return @"Assets\" + imagename + @".png";
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language)
    {
        return value;
    }
}

{% endhighlight %}
{% endtabs %}

<img src="ToolTip_images/ToolTip_img3.png" alt="WinUI treeGrid with Customized ToolTip Support" width="100%" Height="Auto"/>

N> View sample in [GitHub](https://github.com/SyncfusionExamples/How-to-customize-the-tooltip-using-DataTemplate-in-winui-datagrid).

## Events

### CellToolTipOpening event

The [CellToolTipOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CellToolTipOpening) event occurs when any tooltip of the cell is opened. The `CellToolTipOpening` event receives the [TreeGridCellToolTipOpeningEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCellToolTipOpeningEventArgs.html) as argument which has the following properties:

<ul>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_Column">Column:</a> Gets the hovered cell column in the SfTreeGrid.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCellToolTipOpeningEventArgs_Node">Node:</a> Gets the hovered cell node.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_Record">Record:</a> Gets the data context of hovered cell.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_RowColumnIndex">RowColumnIndex:</a> Gets the row and column index of the hovered cell.</li>
<li> <a href="https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CellToolTipOpeningEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CellToolTipOpeningEventArgs_ToolTip">ToolTip:</a> Gets the tooltip of the hovered cells.</li>
</ul>

{% tabs %}
{% highlight xaml %}
<treeGrid:SfTreeGrid Name="treeGrid"
                       ColumnWidthMode="Star"
                       AutoExpandMode="RootNodesExpanded"
                       AutoGenerateColumns="False"
                       CellToolTipOpening="treeGrid_CellToolTipOpening"
                       ChildPropertyName="ReportsTo"
                       ItemsSource="{Binding Employees}"
                       ParentPropertyName="ID"
                       SelfRelationRootValue="-1"/>
{% endhighlight %}
{% highlight c# %}
this.treeGrid.CellToolTipOpening += TreeGrid_CellToolTipOpening;

private void TreeGrid_CellToolTipOpening(object sender, TreeGridCellToolTipOpeningEventArgs e)
{

}

{% endhighlight %}
{% endtabs %}
