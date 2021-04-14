---
layout: post
title: Serialization and Deserialization in WinUI DataGrid | Syncfusion
description: Learn about serialization and deserialization support in Syncfusion WinUI DataGrid (SfDataGrid) control and more.
platform: winui
control: SfDataGrid
documentation: ug
---

# Serialization and Deserialization in WinUI DataGrid (SfDataGrid)

SfDataGrid allows you to serialize and deserialize the SfDataGrid settings using [DataContractSerializer](https://msdn.microsoft.com/en-in/library/system.runtime.serialization.datacontractserializer.aspx).
 
## Serialization 
You can serialize the SfDataGrid by using [SfDataGrid.Serialize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Serialize_Windows_Storage_StorageFile_) method which exports the current DataGrid control properties to an XML file.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
this.datagrid.Serialize(storageFile);
{% endhighlight %}
{% endtabs %}

## Serialization options 

SfDataGrid serialization  operation can be customized by passing [SerializationOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html) instance as an argument to [Serialize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Serialize_System_IO_Stream_Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_) method.


### Serialize sorting

By default, SfDataGrid allows you to serialize the sorting operation. You can disable the sorting serialization by setting the [SerializationOptions.SerializeSorting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeSorting) to `false`.
 
{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeSorting = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize grouping

By default, SfDataGrid allows you to serialize the grouping operation. You can disable the grouping  serialization by setting the [SerializationOptions.SerializeGrouping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeGrouping) to `false`.
 
{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeGrouping = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize filtering

By default, SfDataGrid allows you to serialize the filtering operation. You can disable the filtering  serialization by setting the [SerializationOptions.SerializeFiltering](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeFiltering) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeFiltering = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize columns

By default, SfDataGrid allows you to serialize the columns manipulation operation. You can disable the columns serialization by setting the [SerializationOptions.SerializeColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeColumns) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeColumns = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize summaries
 
By default, SfDataGrid allows you to serialize the caption summary, group summary and table summary settings in SfDataGrid. 

You can disable the summaries serialization by setting [SerializationOptions.SerializeCaptionSummary](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeCaptionSummary) , [SerializationOptions.SerializeGroupSummaries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeGroupSummaries) , [SerializationOptions.SerializeTableSummaries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeTableSummaries) properties to `false`

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeCaptionSummary = false;
options.SerializeGroupSummaries = false;
options.SerializeTableSummaries = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize stacked headers

By default, SfDataGrid allows you to serialize the stack headers operation. You can disable the stack headers serialization by setting the [SerializationOptions.SerializeStackedHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeStackedHeaders) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeStackedHeaders = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}


### Serialize Details View

By default, SfDataGrid allows you to serialize the DetailsViewDefinition. You can disable the DetailsViewDefinition serialization by setting the [SerializationOptions.SerializeDetailsViewDefinition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeDetailsViewDefinition) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeDetailsViewDefinition = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Serialize unbound rows

By default, SfDataGrid allows you to serialize the unbound rows settings. You can disable the unbound rows serialization by setting the [SerializationOptions.SerializeUnBoundRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationOptions_SerializeUnboundRows) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.CreateFileAsync("DataGrid.xml", CreationCollisionOption.ReplaceExisting);
SerializationOptions options = new SerializationOptions();
options.SerializeUnboundRows = false;
this.datagrid.Serialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

## Deserialization

You can deserialize the SfDataGrid setting by using [SfDataGrid.Deserialize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Deserialize_Windows_Storage_StorageFile_) method which reconstructs the SfDataGrid based on the setting in the stored XML file.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
this.datagrid.Deserialize(storageFile);
{% endhighlight %}
{% endtabs %}

## Deserialization options
 
Deserialization operation can be customized by passing [DeserializationOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html) instance as an argument to [Deserialize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_Deserialize_Windows_Storage_StorageFile_) method.

### Deserialize sorting

By default, SfDataGrid allows you to deserialize the sorting operation. You can disable the sorting  deserialization by setting the [DeserializationOptions.DeserializeSorting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeSorting) to `false`.
 
{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeSorting = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize grouping

By default, SfDataGrid allows you to deserialize the grouping operation. You can disable the grouping deserialization by setting the [DeserializationOptions.DeserializeGrouping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeGrouping) to `false`.
 
{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeGrouping = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize filtering

By default, SfDataGrid allows you to deserialize the filtering. you can disable the filtering deserialization by setting [DeserializationOptions.DeserializeFiltering](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeFiltering) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeFiltering = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize columns

By default, SfDataGrid allows you to deserialize the columns manipulation operations. You can disable the columns deserialization by setting the [DeserializationOptions.DeserializeColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeColumns) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeColumns = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize summaries
 
By default, SfDataGrid allows you to deserialize the group summary, caption summary and table summary settings. 

You can disable the summaries deserialization by setting [DeserializationOptions.DeserializeCaptionSummary](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeCaptionSummary) , [DeserializationOptions.DeserializeGroupSummaries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeGroupSummaries) , [DeserializationOptions.DeserializeTableSummaries](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeTableSummaries) properties to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeCaptionSummary = false;
options.DeserializeGroupSummaries = false;
options.DeserializeTableSummaries = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize stacked headers

By default, SfDataGrid allows you to deserialize the stack headers. You can disable the stacked headers deserialization by setting the [DeserializationOptions.DeserializeStackedHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeStackedHeaders) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeStackedHeaders = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize Details View

By default, SfDataGrid allows you to deserialize the DetailsViewDefinition. You can disable the DetailsViewDefinition deserialization by setting the [DeserializationOptions.DeserializeDetailsViewDefinition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeDetailsViewDefinition) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeDetailsViewDefinition = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

### Deserialize unbound rows

By default, SfDataGrid allows you to deserialize the unbound rows settings. You can disable the unbound rows deserialization by setting the [DeserializationOptions.DeserializeUnBoundRows](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.DeserializationOptions.html#Syncfusion_UI_Xaml_DataGrid_Serialization_DeserializationOptions_DeserializeUnboundRows) to `false`.

{% tabs %}
{% highlight c# %}
var folder = ApplicationData.Current.LocalFolder;
var storageFile = await folder.GetFileAsync("DataGrid.xml");
DeserializationOptions options = new DeserializationOptions();
options.DeserializeUnboundRows = false;
this.datagrid.Deserialize(storageFile, options);
{% endhighlight %}
{% endtabs %}

## Customizing Serialization and Deserialization Operations

SfDataGrid allows you to customize the serialization and deserialization operations by deriving [SerializationController](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationController.html) class and override the necessary virtual methods.

### Serializing template column content

By default, you cannot serialize the template content in SfDataGrid. This is the default behavior during  Serialization and Deserialization operation.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <XamlControlsResources xmlns="using:Microsoft.UI.Xaml.Controls" />
            <!-- Other merged dictionaries here -->
        </ResourceDictionary.MergedDictionaries>
        <!-- Other app resources here -->
        <DataTemplate x:Key="cellTemplate">
            <Button Width="110" Content="{Binding Value}" />
        </DataTemplate>
    </ResourceDictionary>
</Application.Resources>


<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="False"
                       ItemsSource="{Binding Orders}">

    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTemplateColumn CellTemplate="{StaticResource cellTemplate}"
                                       HeaderText="Order ID"
                                       MappingName="OrderID"
                                       SetCellBoundValue="True" />        
    </syncfusion:SfDataGrid.Columns>

</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

If you want to serialize and deserialize the template content, you have to reconstruct the same template during deserialization in [RestoreColumnProperties](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.Serialization.SerializationController.html#Syncfusion_UI_Xaml_DataGrid_Serialization_SerializationController_RestoreColumnProperties_Syncfusion_UI_Xaml_DataGrid_Serialization_SerializableGridColumn_Syncfusion_UI_Xaml_DataGrid_GridColumn_) method.

{% tabs %}
{% highlight c# %}

this.dataGrid.SerializationController = new SerializationControllerExt(this.dataGrid);

public class SerializationControllerExt : SerializationController
{
    public SerializationControllerExt(SfDataGrid grid)
    : base(grid)
    {

    }

    protected override void RestoreColumnProperties(SerializableGridColumn serializableColumn, GridColumn column)
    {
        base.RestoreColumnProperties(serializableColumn, column);
        if (column is GridTemplateColumn)
        {
            if (column.MappingName == "OrderID")
            {
                column.CellTemplate = Application.Current.Resources["cellTemplate"] as DataTemplate;
            }
        }
    }
}
{% endhighlight %}
{% endtabs %}

N> View sample in [GitHub](https://github.com/SyncfusionExamples/How-to-serialize-template-column-content-in-winui-datagrid).
