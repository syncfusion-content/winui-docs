---
layout: post
title: Grid Lines Customization in WinUI Data Grid | Syncfusion®
description: Grid lines customization in Data Grid lets you control the visibility and appearance of horizontal and vertical lines for records, headers, and details views.
platform: winui
control: Data Grid
documentation: ug
---

# Grid Lines Customization in WinUI Data Grid

WinUI Data Grid allows you to customize the grid lines visibility to vertical, horizontal, both or none. To achieve this, use the following properties.

[SfDataGrid.GridLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_GridLinesVisibility): To set the border lines for the cells other than header and stacked header cells.
[SfDataGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility): To set the border lines only for header and stacked header cells.

The following are the list of options available to customize grid lines visibility,

* Both
* Vertical
* Horizontal
* None

## Record rows

### Both

The [GridLinesVisibility.Both](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Both) displays the Data Grid with both horizontal and vertical grid lines.
{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

 <dataGrid:SfDataGrid   x:Name="sfDataGrid"
                        AutoGenerateColumns="True"                       
                        GridLinesVisibility="Both"                          
                        ItemsSource="{Binding OrdersDetails}">
 </dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
 this.sfDataGrid.GridLinesVisibility = GridLinesVisibility.Both;
{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-datagrid-gridlines.png" alt="GridLines" width="100%" Height="Auto"/>

### Horizontal

The [GridLinesVisibility.Horizontal](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Horizontal) displays the Data Grid with horizontal grid lines only.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

 <dataGrid:SfDataGrid   x:Name="sfDataGrid"
                        AutoGenerateColumns="True"                       
                        GridLinesVisibility="Horizontal"                          
                        ItemsSource="{Binding OrdersDetails}">
 </dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
 this.sfDataGrid.GridLinesVisibility = GridLinesVisibility.Horizontal;
{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-datagrid-horizontal-gridlines.png" alt="Horizontal GridLines" width="100%" Height="Auto"/>

### Vertical

The [GridLinesVisibility.Vertical](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Vertical) displays the Data Grid with vertical grid lines only.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

 <dataGrid:SfDataGrid   x:Name="sfDataGrid"
                        AutoGenerateColumns="True"                       
                        GridLinesVisibility="Vertical"                          
                        ItemsSource="{Binding OrdersDetails}">
 </dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
 this.sfDataGrid.GridLinesVisibility = GridLinesVisibility.Vertical;
{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-datagrid-vertical-gridlines.png" alt="Vertical GridLines" width="100%" Height="Auto"/>

### None
[GridLinesVisibility.None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_None) displays the Data Grid without grid lines. By default GridLinesVisibility value set as None.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

 <dataGrid:SfDataGrid   x:Name="sfDataGrid"
                        AutoGenerateColumns="True" 
                        GridLinesVisibility="None"                     
                        ItemsSource="{Binding OrdersDetails}">
 </dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
 this.sfDataGrid.GridLinesVisibility = GridLinesVisibility.None;
{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-datagrid-without-gridlines.png" alt="Without GridLines" width="100%" Height="Auto"/>

## Header rows

You can customize the Data Grid header lines visibility by using the [SfDataGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility) property. You can also customize the header lines visibility to horizontal, vertical, none or both. By default HeaderLinesVisibility value set as Both.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

 <dataGrid:SfDataGrid   x:Name="sfDataGrid"
                        AutoGenerateColumns="True" 
                        HeaderLinesVisibility="Horizontal"                            
                        ItemsSource="{Binding OrdersDetails}">
 </dataGrid:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
 this.sfDataGrid.HeaderLinesVisibility = GridLinesVisibility.Horizontal;
{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-datagrid-horizontal-header-lines.png" alt="Displays Horizontal Header Lines" width="100%" Height="Auto"/>

## Grid lines for Master-Details view

Data Grid allows you to customize the grid lines for Master-Details view also like parent Data Grid by changing the grid lines properties in GridViewDefinition.DataGrid. 

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

<dataGrid:SfDataGrid  x:Name="sfDataGrid"
                      AutoGenerateColumns="True"
                      ItemsSource="{Binding OrdersDetails}"
                      GridLinesVisibility="Horizontal"
                      HeaderLinesVisibility="Horizontal">
        <dataGrid:SfDataGrid.DetailsViewDefinition>
            <dataGrid:GridViewDefinition RelationalColumn="OrderDetails">
                <dataGrid:GridViewDefinition.DataGrid>
                    <dataGrid:SfDataGrid  x:Name="FirstDetailsViewGrid" 
                                          GridLinesVisibility="Horizontal"
                                          HeaderLinesVisibility="Horizontal"
                                          AutoGenerateColumns="True">
                    </dataGrid:SfDataGrid>
                </dataGrid:GridViewDefinition.DataGrid>
            </dataGrid:GridViewDefinition>
        </dataGrid:SfDataGrid.DetailsViewDefinition>
</dataGrid:SfDataGrid>


{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.GridLinesVisibility = GridLinesVisibility.Horizontal;
this.sfDataGrid.HeaderLinesVisibility = GridLinesVisibility.Horizontal;
this.FirstLevelNestedGrid.GridLinesVisibility = GridLinesVisibility.Horizontal;
this.FirstLevelNestedGrid.HeaderLinesVisibility = GridLinesVisibility.Horizontal;

{% endhighlight %}
{% endtabs %}

<img src="GridLines_images/winui-detailsviewdatagrid-horizontal-lines.png" alt="DetailsViewDataGrid GridLinesVisibility customization" width="100%" Height="Auto"/>

## Limitations

* Grid lines customization are not supported for RowHeader.
