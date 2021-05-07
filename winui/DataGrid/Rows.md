---
layout: post
title: Rows in WinUI DataGrid control | Syncfusion
description: Learn here all about Rows support in Syncfusion WinUI DataGrid(SfDataGrid) control with header width and more.
platform: winui
control: DataGrid
documentation: ug
---

# Rows in WinUI DataGrid

This section explains about various row types in SfDataGrid.

[StackedHeaderRow](https://help.syncfusion.com/winui/datagrid/stacked-headers)

[AddNewRow](https://help.syncfusion.com/winui/datagrid/data-manipulation#add-new-rows)

[SummaryRow](https://help.syncfusion.com/winui/datagrid/summaries)

[UnboundRow](https://help.syncfusion.com/winui/datagrid/unbound-rows)

## Row Header

RowHeader is a special column used to indicate the status of row (current row, editing status, errors in row, etc.) which is placed as first cell of each row. You can show or hide the row header by setting [SfDataGrid.ShowRowHeader](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_ShowRowHeader) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid"
                       AddNewRowPosition="Top"
                       ItemsSource="{Binding Orders}"
                       ShowRowHeader="True" />
{% endhighlight %}
{% highlight c# %}
sfDataGrid.ShowRowHeader = true;
{% endhighlight %}
{% endtabs %}

![WinUI DataGrid Row Header](Rows_images/winui-datagrid-row-header.png)

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
<img src="Rows_images/Rows_img2.png" alt="RowHeader in WinUI DataGrid Image2"/>
</td>
<td>
Denotes the row which has current cell or selected item.
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img3.png" alt="RowHeader in WinUI DataGrid Image3"/>
</td>
<td>
Denotes row is being edited. 
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img4.png" alt="RowHeader in WinUI DataGrid Image4"/>
</td>
<td>
Denotes row is AddNewRow.
</td>
</tr>
<tr>
<td>
<img src="Rows_images/Rows_img5.png" alt="RowHeader in WinUI DataGrid Image5"/>
</td>
<td>
Denotes the row has errors or current row which has errors. 
</td>
</tr>
</table>

### Row header width

You can change the width of the row header by setting [SfDataGrid.RowHeaderWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_RowHeaderWidth) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid"
                       ShowRowHeader="True"
                       RowHeaderWidth="50"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}

{% highlight c# %}
sfDataGrid.RowHeaderWidth = 50;
{% endhighlight %}
{% endtabs %}

### Display the row index in row header

You can display the corresponding row index in each row header, by customizing the `ControlTemplate` of [GridRowHeaderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridRowHeaderCell.html). You have to bind the `RowIndex` property to `TextBlock.Text` like the below code example.

{% tabs %}
{% highlight xaml %}

<Style TargetType="syncfusion:GridRowHeaderCell">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:GridRowHeaderCell">
                <Border x:Name="PART_RowHeaderCellBorder"
                        Background="{TemplateBinding Background}"
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                    <Grid>
                        <TextBlock HorizontalAlignment="Center"
                                   VerticalAlignment="Center"
                                   Text="{Binding RowIndex,RelativeSource={RelativeSource TemplatedParent}}"
                                   TextAlignment="Center" />
                    </Grid>
                </Border>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

{% endhighlight %}
{% endtabs %}

![WinUI DatGrid displays Row Header Cells with Row Index](Rows_images/winui-datagrid-row-header-with-index.png)


### Change the current row indicator

You can change the current row indicator in the row header by customizing the control template of `GridRowHeaderCell`.

{% tabs %}
{% highlight xaml %}

<Style TargetType="syncfusion:GridRowHeaderCell">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:GridRowHeaderCell">
                <Border x:Name="PART_RowHeaderCellBorder"
                        Background="{TemplateBinding Background}"
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="IndicationStates">
                            <VisualState x:Name="Normal">
                            </VisualState>
                            <VisualState x:Name="CurrentRow">
                                <Storyboard>
                                    <ObjectAnimationUsingKeyFrames Storyboard.TargetName="PART_RowHeaderIndicator" Storyboard.TargetProperty="Data">
                                        <DiscreteObjectKeyFrame KeyTime="0">
                                            <DiscreteObjectKeyFrame.Value>
                                                <Geometry>F1M-218.342,2910.79L-234.066,2926.52 -233.954,2926.63 -225.428,2926.63 -210.87,2912.07 -206.495,2907.7 -225.313,2888.88 -234.066,2888.88 -218.342,2904.6 -259.829,2904.6 -259.829,2910.79 -218.342,2910.79z</Geometry>
                                            </DiscreteObjectKeyFrame.Value>
                                        </DiscreteObjectKeyFrame>
                                    </ObjectAnimationUsingKeyFrames>                                            
                                </Storyboard>
                            </VisualState>
                        </VisualStateGroup>
                    </VisualStateManager.VisualStateGroups>
                    <Path x:Name="PART_RowHeaderIndicator"
                          Width="8.146"
                          Height="8.146"
                          HorizontalAlignment="Center"
                          VerticalAlignment="Center"
                          Fill="#FF303030"
                          Stretch="Fill">
                    </Path>
                </Border>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

{% endhighlight %}
{% endtabs %}

![Customizing Current Row Indicator in WinUI DataGrid](Rows_images/winui-datagrid-current-row-indicator.png)


## Header Row

Header row is present in top of the DataGrid which has column headers in it. Column header describes the caption to identify the column content.

![WinUI DataGrid Header Row with Column Header](Rows_images/winui-datagrid-header-row-with-column-header.png)

You can change the header row height by setting [SfDataGrid.HeaderRowHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderRowHeight) property.

### Hiding header row

You can hide the header row by setting `SfDataGrid.HeaderRowHeight` as `0` (zero).


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid"
                       HeaderRowHeight="0"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}
{% endtabs %}

![Hide Row Header in WinUI DataGrid](Rows_images/winui-datagrid-hide-row-header.png)

You can also hide the header row of DetailsViewDataGrid by setting `HeaderRowHeight` as `0` (zero) to [ViewDefinition.DataGrid](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridViewDefinition.html#Syncfusion_UI_Xaml_DataGrid_GridViewDefinition_DataGrid).


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid" ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="OrderDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="firstLevelNestedGrid" HeaderRowHeight="0" />
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

![Hide Row Header of Details View in WinUI DataGrid](Rows_images/winui-datagrid-details-view-without-header.png)

## Freeze panes

DataGrid provides support to freeze the rows and columns at top and bottom similar to excel. You can freeze the rows and columns by setting following properties,

<table>
<tr>
<th>
Property Name
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
{{'[FrozenRowsCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_FrozenRowsCount)'| markdownify }}
</td>
<td>
Set the frozen rows count at <kbd>top</kbd> of the SfDataGrid.
</td>
</tr>
<tr>
<td>
{{'[FrozenFooterRowsCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_FrozenFooterRowsCount)'| markdownify }}
</td>
<td>
Set the footer rows count at <kbd>bottom</kbd> of the SfDataGrid.
</td>
</tr>
<tr>
<td>
{{'[FrozenColumnCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_FrozenColumnCount)'| markdownify }}
</td>
<td>
Set the frozen columns count in <kbd>left side</kbd> of the SfDataGrid. 
</td>
</tr>
<tr>
<td>
{{'[FrozenFooterColumnCount ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_FrozenFooterColumnCount)'| markdownify }}
</td>
<td>
Set the frozen columns in <kbd>right side</kbd> of the SfDataGrid.
</td>
</tr>
</table>


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="sfDataGrid"
                       FrozenFooterColumnCount="1"
                       FrozenColumnCount="1"
                       FrozenRowsCount="2"
                       FrozenFooterRowsCount="3"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}
{% highlight c# %}
sfDataGrid.FrozenFooterColumnCount = 1;
sfDataGrid.FrozenColumnCount = 1;
sfDataGrid.FrozenRowsCount = 2;
sfDataGrid.FrozenFooterRowsCount = 3;
{% endhighlight %}
{% endtabs %}

![WinUI DataGrid displays Frozen Rows and columns at top and bottom](Rows_images/winui-datagrid-frozen-rows-columns-position.png)

### Differentiate frozen rows from normal rows

You can differentiate the frozen rows and footer rows from normal rows by writing style for [DataGridRowControl](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.DataGridRowControl.html) and by customizing the `FrozenRow` and `FooterRow` visual states.


{% tabs %}
{% highlight xaml %}
<Style TargetType="syncfusion:DataGridRowControl">
    <Setter Property="Background" Value="Transparent" />
    <Setter Property="BorderBrush" Value="Gray" />
    <Setter Property="BorderThickness" Value="0" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:DataGridRowControl">
                <Grid>
                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="BorderStates">
                            <VisualState x:Name="NormalRow" />
                            <VisualState x:Name="FrozenRow">
                                <Storyboard BeginTime="0">
                                    <ObjectAnimationUsingKeyFrames BeginTime="0"
                                                           Duration="1"
                                                           Storyboard.TargetName="PART_RowBorder"
                                                           Storyboard.TargetProperty="BorderThickness">

                                        <!--  Border Thickness for Frozen rows  -->
                                        <DiscreteObjectKeyFrame KeyTime="0" Value="0, 0, 0, 4" />
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="FooterRow">
                                <Storyboard BeginTime="0">
                                    <ObjectAnimationUsingKeyFrames BeginTime="0"
                                                           Duration="1"
                                                           Storyboard.TargetName="PART_RowBorder"
                                                           Storyboard.TargetProperty="BorderThickness">

                                        <!--  Border Thickness for Footer rows  -->
                                        <DiscreteObjectKeyFrame KeyTime="0" Value="0, 4, 0, 0" />
                                    </ObjectAnimationUsingKeyFrames>

                                    <ObjectAnimationUsingKeyFrames BeginTime="0"
                                                           Duration="1"
                                                           Storyboard.TargetName="PART_RowBorder"
                                                           Storyboard.TargetProperty="Margin">

                                        <DiscreteObjectKeyFrame KeyTime="0" Value="0, -1, 0, 0" />
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                        </VisualStateGroup>
                    </VisualStateManager.VisualStateGroups>

                    <Border x:Name="PART_RowBorder"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}" />

                    <Rectangle x:Name="PART_CurrentFocusRow"
                               Margin="{TemplateBinding CurrentFocusBorderMargin}"
                               Stroke="DarkGray"
                               StrokeDashArray="3,3"
                               StrokeThickness="1"
                               Visibility="{TemplateBinding CurrentFocusRowVisibility}" />

                    <Rectangle x:Name="PART_RowBackgroundClipRect" Fill="{TemplateBinding Background}" />

                    <Border x:Name="PART_RowSelectionBorder"
                            Background="{TemplateBinding SelectionBackground}"
                            Visibility="{TemplateBinding SelectionBorderVisibility}" />

                    <Border x:Name="PART_RowHighlightBorder"
                            Margin="1"
                            Background="{TemplateBinding RowHoverBackground}"
                            BorderBrush="{TemplateBinding RowHoverBackground}"
                            BorderThickness="{TemplateBinding BorderThickness}"
                            Visibility="{TemplateBinding HighlightSelectionBorderVisibility}" />

                    <Border BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
                        <ContentPresenter />
                    </Border>
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
{% endhighlight %}
{% endtabs %}

![Differentiating Frozen Rows and Footer Rows from Normal rows in WinUI DataGrid](Rows_images/winui-datagrid-difference-of-frozen-and-normal-rows.png)

### Disable drag and drop between frozen and non-frozen columns

You can disable the drag and drop between frozen and non-frozen columns by handling [ColumnDragging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_ColumnDragging) event.
Using [Reason](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.QueryColumnDraggingEventArgs.html#Syncfusion_UI_Xaml_DataGrid_QueryColumnDraggingEventArgs_Reason) property in [QueryColumnDraggingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.QueryColumnDraggingEventArgs.html), you can cancel the column dropping operation. 

In the below code, if the Reason is [QueryColumnDraggingReason.Dropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.QueryColumnDraggingReason.html#Syncfusion_UI_Xaml_Grids_QueryColumnDraggingReason_Dropping) and the column is dragged from frozen region to non-frozen region or vice versa, you can cancel the dropping action by setting `e.Cancel` as `true` in the event.

{% tabs %}
{% highlight c# %}
this.sfDataGrid.ColumnDragging += SfDataGrid_ColumnDragging;

void SfDataGrid_ColumnDragging(object sender, QueryColumnDraggingEventArgs e)
{
    if (e.Reason == QueryColumnDraggingReason.Dropping)
    {
        //used to get frozen column index from the  frozen column count.
        var frozenColIndex = sfDataGrid.FrozenColumnCount +
                                              this.sfDataGrid.ResolveToStartColumnIndex();
        //cancels dragging from frozen column to non-frozen column.

        if (e.From < frozenColIndex && e.To > frozenColIndex - 1)
            e.Cancel = true;

        // cancels dragging from non-frozen column to frozen column.

        if (e.From > frozenColIndex && e.To < frozenColIndex ||
             (e.From == frozenColIndex && e.To < frozenColIndex))
            e.Cancel = true;
    }
}
{% endhighlight %}
{% endtabs %}


### Limitations

1. When using `DetailsView` with freeze panes, exception will be raised like **DetailsView is not supported with Freeze panes support**.

2. When [AllowFrozenGroupHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_AllowFrozenGroupHeaders) is `true`, frozen rows will not be considered.

3. SfDataGrid has support to freeze the number of rows from top or bottom. There is no support to freeze a specific row.

N>
1. Header rows, table summary rows and row header are frozen regardless of `FrozenRowsCount` and `FrozenFooterRowsCount`.
2. `FrozenRowsCount` and `FrozenFooterRowsCount` values should be less than the number of rows and column visible.
