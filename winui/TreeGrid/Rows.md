---
layout: post
title: Rows in WinUI TreeGrid control | Syncfusion
description: Learn here all about Rows support in Syncfusion WinUI TreeGrid(SfTreeGrid) control with header width support and more.
platform: winui
control: SfTreeGrid
documentation: ug
---

# Rows in WinUI TreeGrid

This section explains about various row types in treegrid and its customization.

## Row header

RowHeader is a special column used to indicate the status of row (current row, editing status, errors in row, etc.) which is placed as first cell of each row. You can show or hide the row header by setting [SfTreeGrid.ShowRowHeader](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_ShowRowHeader) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       ColumnWidthMode="Star"
                       AutoExpandMode="AllNodesExpanded"
                       ShowRowHeader="True" 
                       AutoGenerateColumns="False"
                       ChildPropertyName="Children"
                       ItemsSource="{Binding EmployeeDetails}" >
{% endhighlight %}
{% endtabs %}

### Row indicators and its description

<table>
<tr>
<th>
Row Indicator
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img1.jpeg"/>
</td>
<td>
Denotes the row which has current cell or selected item.
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img2.jpeg"/>
</td>
<td>
Denotes row is being edited. 
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img3.jpeg"/>
</td>
<td>
Denotes the row has errors. 
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img4.jpeg"/>
</td>
<td>
Denotes that the current row which has errors.
</td>
</tr>
</table>

### Show row index in row header

You can display the row index value in row header by customizing the `TreeGridRowHeaderCell` style with the binding of `RowIndex` to `TextBlock.Text` property.

{% tabs %}
{% highlight xaml %}
<Style TargetType="syncfusion:TreeGridRowHeaderCell">
    <Setter Property="Background" Value="Transparent" />
    <Setter Property="BorderBrush" Value="#FFE5E5E5" />
    <Setter Property="BorderThickness" Value="0,0,1,1" />
    <Setter Property="Padding" Value="0" />
    <Setter Property="IsTabStop" Value="False" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:TreeGridRowHeaderCell">
                <Border x:Name="PART_RowHeaderCellBorder"
            Background="{TemplateBinding Background}"
            BorderBrush="{TemplateBinding BorderBrush}"
            BorderThickness="{TemplateBinding BorderThickness}">
                    <Grid>
                        <!--RowIndex is displayed here -->
                        <TextBlock HorizontalAlignment="Center"
                        VerticalAlignment="Center"
                        Text="{Binding RowIndex,
                                          RelativeSource={RelativeSource TemplatedParent}}"
                        TextAlignment="Center" />
                    </Grid>
                </Border>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

{% endhighlight %}
{% endtabs %}
![WinUI TreeGrid displays Row Header Cells with Row Index](Rows_images/winui-treegrid-row-header-with-index.png)

## Header row

Header row is present in top of the treegrid which has column headers in it. Column header describes the caption to identify the column content.

![WinUI TreeGrid displays Column Header in Header Row](Rows_images/winui-treegrid-column-header-in-header-row.png)

### Hiding header row

You can hide the header row by setting [SfTreeGrid.HeaderRowHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderRowHeight) as 0 (zero).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Name="treeGrid"
                       ColumnWidthMode="Star"
                       AutoExpandMode="AllNodesExpanded"
                       ShowRowHeader="True" 
                       HeaderRowHeight="0"
                       AutoGenerateColumns="False"
                       ChildPropertyName="Children"
                       ItemsSource="{Binding EmployeeDetails}" >

{% endhighlight %}
{% endtabs %}

### Customize style of header row

You can change the header cell background and foreground for specific column or an entire grid by using [HeaderStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_HeaderStyle) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:Window.Resources>
        <Style TargetType="syncfusion:TreeGridHeaderCell" x:Key="headerStyle">
            <Setter Property="Background" Value="#FF7AA732"/>
            <Setter Property="Foreground" Value="Red"/>
        </Style>
</syncfusion:Window.Resources>

<syncfusion:SfTreeGrid Name="treeGrid"
                       ColumnWidthMode="Star"
                       AutoExpandMode="AllNodesExpanded"
                       HeaderStyle="{StaticResource headerStyle}"
                       AutoGenerateColumns="False"
                       ChildPropertyName="Children"
                       ItemsSource="{Binding EmployeeDetails}" > 
{% endhighlight %}
{% endtabs %}

![Customizing Row Header in WinUI TreeGrid](Rows_images/winui-treegrid-row-header-customization.png)

You can change the style of the particular column header by using the [HeaderStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_HeaderStyle) property in column,

{% tabs %}
{% highlight xaml %}
<syncfusion:TreeGridTextColumn HeaderText="First Name" HeaderStyle="{StaticResource headerStyle}" MappingName="FirstName" />
{% endhighlight %}
{% endtabs %}

![Customizing Column Header in WinUI TreeGrid](Rows_images/winui-treegrid-column-header-customization.png)

