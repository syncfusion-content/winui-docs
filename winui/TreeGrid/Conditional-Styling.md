---
layout: post
title: Conditional Styling | TreeGrid | WinUI | Syncfusion
description: Learn here all about conditional styling support in Syncfusion WinUI TreeGrid(SfTreeGrid) control and more.
platform: winUI
control: SfTreeGrid
documentation: ug
---

# Conditional styling in WinUI TreeGrid

You can style the treegrid and its inner elements conditionally based on data Using StyleSelector.

## Cells

### Style cells using style selector

The record cells ([TreeGridCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCell.html)) can be customized conditionally based on data by setting [SfTreeGrid.CellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CellStyleSelector) property and the particular column record cells can be customized by setting [GridColumn.CellStyleSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_CellStyleSelector) property and you can get the container as TreeGridCell in the StyleSelector.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <local:SelectorClass x:Key="styleSelector" />
    <Style x:Key="redCellStyle" TargetType="syncfusion:TreeGridCell">
        <Setter Property="Foreground" Value="Red" />
    </Style>
    <Style x:Key="blueCellStyle" TargetType="syncfusion:TreeGridCell">
        <Setter Property="Foreground" Value="DarkBlue" />
    </Style>
</Application.Resources>

<syncfusion:SfTreeGrid Margin="5" Name="treeGrid"
                               ChildPropertyName="Children"
                               AutoGenerateColumns="False"
                               ColumnWidthMode="Star"         
                               CellStyleSelector="{StaticResource styleSelector}"
                               ItemsSource="{Binding PersonDetails}" />
{% endhighlight %}
{% highlight c# %}
public class SelectorClass : StyleSelector
{
    protected override Style SelectStyleCore(object item, DependencyObject container)
    {
        var data = item as PersonInfo;
        if (data != null && ((container as TreeGridCell).ColumnBase.TreeGridColumn.MappingName == "Id"))
        {
            //custom condition is checked based on data.
            if (data.Id < 10)
                return App.Current.Resources["redCellStyle"] as Style;
            return App.Current.Resources["blueCellStyle"] as Style;
        }
        return base.SelectStyleCore(item, container);
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid Conditional Cell Styling based on Data using Style Selector](Conditional-Styling_images/winui-treegrid-cell-style-customization.png)

### Add image to cell

You can add the image to tree gird cell by using TreeGridTemplateColumn,

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeGrid Margin="5" Name="treeGrid"
                    Grid.Row="0"                   
                    AutoGenerateColumns="False"
                    CheckBoxSelectionMode="Default"
                    AutoExpandMode="RootNodesExpanded"
                    ChildPropertyName="ReportsTo"
                    ExpanderColumn="ID" 
                    AllowResizingColumns="True"
                    NavigationMode="Cell" AllowEditing="True"
                    ParentPropertyName="ID"
                    SelfRelationRootValue="-1"
                    SelectionMode="Single" 
                    ItemsSource="{Binding EmployeeDetails}" >
    <syncfusion:SfTreeGrid.Columns>
        <syncfusion:TreeGridTextColumn MappingName="FirstName"/>
        <syncfusion:TreeGridTextColumn MappingName="LastName"/>
        <syncfusion:TreeGridTextColumn MappingName="Department"/>
        <syncfusion:TreeGridTextColumn MappingName="Title"/>
        <syncfusion:TreeGridTemplateColumn HeaderText="Country" MappingName="ImageLink">
            <syncfusion:TreeGridTemplateColumn.CellTemplate>
                <DataTemplate>
                    <Grid>
                        <Image Width="30"
                               Height="20"
                               Source="{Binding ImageLink,
                                                Converter={StaticResource converter}}" />
                    </Grid>
                </DataTemplate>
            </syncfusion:TreeGridTemplateColumn.CellTemplate>
        </syncfusion:TreeGridTemplateColumn>
    </syncfusion:SfTreeGrid.Columns>
</syncfusion:SfTreeGrid>

{% endhighlight %}
{% highlight c# %}
class StringToImageConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        string imageName = value.ToString();
        if (imageName == "US.jpg")
        {
            Uri uri = new Uri("ms-appx:///Images/US.jpg");
            BitmapImage image = new BitmapImage(uri);
            return image;
        }

        else if (imageName == "UK.jpg")
        {
            Uri uri1 = new Uri("ms-appx:///Images/UK.jpg");
            BitmapImage image = new BitmapImage(uri1);
            return image;
        }

        else
        {
            Uri uri1 = new Uri("ms-appx:///Images/Japan.jpg");
            BitmapImage image = new BitmapImage(uri1);
            return image;
        }
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language)
    {
        throw new NotImplementedException();
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI TreeGrid Column with Image](Conditional-Styling_images/winui-treegrid-column-with-image.png)

N> View sample in [GitHub](https://github.com/SyncfusionExamples/How-to-load-images-in-a-cell-in-winui-treegrid).
