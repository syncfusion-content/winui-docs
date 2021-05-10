---
layout: post
title: Grid Lines Customization in WinUI TreeGrid control | Syncfusion
description: Learn here all about Grid Lines Customization support in Syncfusion WinUI TreeGrid(SfTreeGrid) control and more.
platform: winui
control: TreeGrid
documentation: ug
---

# Grid Lines Customization in WinUI TreeGrid

SfTreeGrid allows you to customize the grid lines visibility to vertical, horizontal, both or none. To achieve this, use the following properties.

[SfTreeGrid.GridLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_GridLinesVisibility): To set the border lines for the cells other than header and stacked header cells.
[SfTreeGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility): To set the border lines only for header and stacked header cells.

The following are the list of options available to customize grid lines visibility,

* Both
* Vertical
* Horizontal
* None

## Record rows

### Both

The [GridLinesVisibility.Both](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Both) displays the TreeGrid with both horizontal and vertical grid lines. By default GridLinesVisibility value set as Both.

{% tabs %}
{% highlight xaml %}
xmlns:treeGrid="using:Syncfusion.UI.Xaml.TreeGrid"

<treeGrid:SfTreeGrid  x:Name="sfTreeGrid"
                      AutoExpandMode="RootNodesExpanded"
                      AutoGenerateColumns="False"
                      GridLinesVisibility="Both"
                      ChildPropertyName="Children"
                      ColumnWidthMode="AutoWithLastColumnFill"
                      ExpanderColumn="FirstName"
                      ItemsSource="{Binding Persons}"/>


{% endhighlight %}
{% highlight c# %}
this.sfTreeGrid.GridLinesVisibility = GridLinesVisibility.Both;
{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid with GridLines](GridLines_images/winui-treegrid-gridlines.png)

### Horizontal

The [GridLinesVisibility.Horizontal]https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Horizontal) displays the TreeGrid with horizontal grid lines only.

{% tabs %}
{% highlight xaml %}
xmlns:treeGrid="using:Syncfusion.UI.Xaml.TreeGrid"

<treeGrid:SfTreeGrid  x:Name="sfTreeGrid"
                      AutoExpandMode="RootNodesExpanded"
                      AutoGenerateColumns="True"
                      GridLinesVisibility="Horizontal"
                      ChildPropertyName="Children"
                      ColumnWidthMode="AutoWithLastColumnFill"
                      ExpanderColumn="FirstName"
                      ItemsSource="{Binding Persons}"/>

{% endhighlight %}
{% highlight c# %}
this.sfTreeGrid.GridLinesVisibility = GridLinesVisibility.Horizontal;
{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid with Horizontal GridLines](GridLines_images/winui-treegrid-horizontal-gridlines.png)

### Vertical

The [GridLinesVisibility.Vertical](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_Vertical) displays the TreeGrid with vertical grid lines only.

{% tabs %}
{% highlight xaml %}
xmlns:treeGrid="using:Syncfusion.UI.Xaml.TreeGrid"

<treeGrid:SfTreeGrid  x:Name="sfTreeGrid"
                      AutoExpandMode="RootNodesExpanded"
                      AutoGenerateColumns="True"
                      GridLinesVisibility="Vertical"
                      ChildPropertyName="Children"
                      ColumnWidthMode="AutoWithLastColumnFill"
                      ExpanderColumn="FirstName"
                      ItemsSource="{Binding Persons}"/>

{% endhighlight %}
{% highlight c# %}
this.sfTreeGrid.GridLinesVisibility = GridLinesVisibility.Vertical;
{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid with Vertical GridLines](GridLines_images/winui-treegrid-vertical-gridlines.png)

### None
[GridLinesVisibility.None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridLinesVisibility.html#Syncfusion_UI_Xaml_Grids_GridLinesVisibility_None) displays the TreeGrid without grid lines.

{% tabs %}
{% highlight xaml %}
xmlns:treeGrid="using:Syncfusion.UI.Xaml.TreeGrid"

<treeGrid:SfTreeGrid  x:Name="sfTreeGrid"
                      Height="514"
                      Width="800"
                      Margin="5"
                      VerticalAlignment="Top"
                      AutoExpandMode="RootNodesExpanded"
                      AutoGenerateColumns="False"
                      GridLinesVisibility="None"
                      ChildPropertyName="Children"
                      ColumnWidthMode="AutoWithLastColumnFill"
                      ExpanderColumn="FirstName"
                      ItemsSource="{Binding Persons}"/>

{% endhighlight %}
{% highlight c# %}
this.sfTreeGrid.GridLinesVisibility = GridLinesVisibility.None;
{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid without GridLines](GridLines_images/winui-treegrid-without-gridlines.png)

## Header rows

You can customize the TreeGrid header lines visibility by using the [SfTreeGrid.HeaderLinesVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderLinesVisibility) property. You can also customize the header lines visibility to horizontal, vertical, none or both. By default HeaderLinesVisibility value set as Both.

{% tabs %}
{% highlight xaml %}
xmlns:treeGrid="using:Syncfusion.UI.Xaml.TreeGrid"

<treeGrid:SfTreeGrid  x:Name="sfTreeGrid"
                      AutoExpandMode="RootNodesExpanded"
                      AutoGenerateColumns="True"
                      HeaderLinesVisibility="Horizontal"
                      ChildPropertyName="Children"
                      ColumnWidthMode="AutoWithLastColumnFill"
                      ExpanderColumn="FirstName"
                      ItemsSource="{Binding Persons}"/>

{% endhighlight %}
{% highlight c# %}
this.sfTreeGrid.HeaderLinesVisibility = GridLinesVisibility.Horizontal;
{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid displays Horizontal Header Lines](GridLines_images/winui-treegrid-horizontal-header-lines.png)

## Limitations

* Grid lines customization are not supported for RowHeader.
