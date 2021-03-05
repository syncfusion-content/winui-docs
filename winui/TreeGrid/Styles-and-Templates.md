---
layout: post
title: Styles and Templates in SfTreeGrid.
description: Learn How to apply styles and templates in Syncfusion WinUI TreeGrid (SfTreeGrid) control and more details.| Syncfusion | SfTreeGrid 
platform: winui
control: SfTreeGrid
documentation: ug
---

# Styles and Templates in WinUI TreeGrid (SfTreeGrid)

## Styling Column Header

The header cell can be customized by writing style of TargetType [TreeGridHeaderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridHeaderCell.html). You can set to particular SfTreeGrid by setting [SfTreeGrid.HeaderStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_HeaderStyle) property and the particular column can be styled by setting [TreeGridColumn.HeaderStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_HeaderStyle) property.

N> `TreeGridColumn.HeaderStyle` takes higher priority than `SfTreeGrid.HeaderStyle` property.

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <Style TargetType="syncfusion:TreeGridHeaderCell" x:Key="headerStyle">
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Background" Value="LightPink"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Page.Resources>


<syncfusion:SfTreeGrid  Name="treeGrid"               
                        HeaderStyle="{StaticResource headerStyle}"
                        ChildPropertyName="ReportsTo"
                        ItemsSource="{Binding Employees}"
                        ParentPropertyName="ID"
                        SelfRelationRootValue="-1">
    <syncfusion:SfTreeGrid.Columns>
        <syncfusion:TreeGridTextColumn HeaderText="First Name" MappingName="FirstName" />
        <syncfusion:TreeGridTextColumn HeaderText="Employee ID" MappingName="ID" TextAlignment="Right" />
        <syncfusion:TreeGridTextColumn HeaderText="Last Name" MappingName="LastName" />
        <syncfusion:TreeGridTextColumn HeaderText="Salary" MappingName="Salary" />
        <syncfusion:TreeGridTextColumn HeaderText="Title" MappingName="Title" />
        <syncfusion:TreeGridTextColumn HeaderText="Reports To" MappingName="ReportsTo" TextAlignment="Right" />
    </syncfusion:SfTreeGrid.Columns>
</syncfusion:SfTreeGrid>

{% endhighlight %}
{% endtabs %}

![Style applied for WinUI Treagrid Headers](Styles-and-Templates_images/Styles-and-Templates_img1.png)

### Styling Stacked Headers

The appearance of stacked header can be customized by writing style of TargetType [TreeGridStackedHeaderCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridStackedHeaderCell.html).

{% tabs %}
{% highlight xaml %}
<Page.Resources>
    <Style TargetType="syncfusion:TreeGridStackedHeaderCell">
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Page.Resources>

{% endhighlight %}
{% endtabs %}

![Style applied for WinUI TreeGrid StackedHeader](Styles-and-Templates_images/Styles-and-Templates_img2.png)

### Setting Different Style for Each Stacked Header

You can apply the different style to stacked header by overriding the [default renderer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.Renderers.TreeGridCellRendererBase.html) of StackedHeader.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <Style x:Key="style1" TargetType="syncfusion:TreeGridStackedHeaderCell">
        <Setter Property="Background" Value="LightBlue" />
        <Setter Property="FontFamily" Value="Segoe UI" />
        <Setter Property="FontStyle" Value="Italic" />
        <Setter Property="FontWeight" Value="Bold"/>
    </Style>
    <Style x:Key="style2" TargetType="syncfusion:TreeGridStackedHeaderCell">
        <Setter Property="Background" Value="Bisque" />
        <Setter Property="FontFamily" Value="Courier New" />
        <Setter Property="FontStyle" Value="Oblique" />
        <Setter Property="FontWeight" Value="Bold"/>
    </Style>
</Application.Resources>

{% endhighlight %}
{% highlight c# %}
//Default TreeGridStackedCellRenderer is removed.
this.treeGrid.CellRenderers.Remove("StackedHeader");
//Customized TreeGridStackedCellRenderer is added.
this.treeGrid.CellRenderers.Add("StackedHeader", new TreeGridCustomStackedRenderer());

public class TreeGridCustomStackedRenderer : TreeGridStackedHeaderCellRenderer
{
    public TreeGridCustomStackedRenderer()
    {
    }
    public override void OnInitializeEditElement(TreeDataColumnBase dataColumn, TreeGridStackedHeaderCell uiElement, object dataContext)
    {
        if (dataColumn.ColumnIndex == 0)
            uiElement.Style = App.Current.Resources["style1"] as Style;
        else 
            uiElement.Style = App.Current.Resources["style2"] as Style;
        base.OnInitializeEditElement(dataColumn, uiElement, dataContext);
    }
}

{% endhighlight %}
{% endtabs %}

![Different style applied for WinUI TreeGrid stackedHeader](Styles-and-Templates_images/Styles-and-Templates_img3.png)