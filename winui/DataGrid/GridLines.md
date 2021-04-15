---
layout: post
title: Grid Lines Customization in WinUI DataGrid control | Syncfusion
description: Learn here all about Grid Lines Customization support in Syncfusion WinUI DataGrid(SfDataGrid) control and more.
platform: winui
control: DataGrid
documentation: ug
---

# Grid Lines Customization in WinUI DataGrid

SfDataGrid allows you to customize the grid lines visibility to vertical, horizontal, both or none. To achieve this, use the following properties.

[SfDataGrid.GridLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_GridLinesVisibility): To set the border lines for the cells other than header and stacked header cells.
[SfDataGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility): To set the border lines only for header and stacked header cells.

The following are the list of options available to customize grid lines visibility,

* Both
* Vertical
* Horizontal
* None

## Record rows

### Both

The [GridLinesVisibility.Both](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Both) displays the DataGrid with both horizontal and vertical grid lines. By default GridLinesVisibility value set as Both.

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

![GridLinesVisibility in WinUI DataGrid](GridLines_images/GridLines_image1.png)

### Horizontal

The [GridLinesVisibility.Horizontal]https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Horizontal) displays the DataGrid with horizontal grid lines only.

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

![Horizontal GridLinesVisibility in WinUI DataGrid](GridLines_images/GridLines_image2.png)

### Vertical

The [GridLinesVisibility.Vertical](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Vertical) displays the DataGrid with vertical grid lines only.

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

![Vertical GridLinesVisibility in WinUI DataGrid](GridLines_images/GridLines_image3.png)

### None
[GridLinesVisibility.None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_None) displays the DataGrid without grid lines.

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

![None GridLinesVisibility in WinUI DataGrid](GridLines_images/GridLines_image4.png)

## Header rows

You can customize the DataGrid header lines visibility by using the [SfDataGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility) property. You can also customize the header lines visibility to horizontal, vertical, none or both. By default HeaderLinesVisibility value set as Both.

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

![Horizontal HeaderLinesVisibility in WinUI DataGrid](GridLines_images/GridLines_image5.png)

## Limitations

* Grid lines customization are not supported for RowHeader.
