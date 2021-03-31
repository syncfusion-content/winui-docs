---
layout: post
title: Data binding in WinUI DataGrid control | Syncfusion
description: Learn about data binding (List, ObservableCollection) support in Syncfusion WinUI DataGrid (SfDataGrid) control and more details. 
platform: winui
control: SfDataGrid
documentation: ug
---

# Data Binding in WinUI DataGrid (SfDataGrid)

SfDataGrid control is designed to display the bounded data in a tabular format. The data binding can be achieved by assigning the data sources to [SfDataGrid.ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_ItemsSource) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}" />
{% endhighlight %}
{% endtabs %}

If the data source implements [INotifyCollectionChanged](https://msdn.microsoft.com/en-us/library/System.Collections.Specialized.INotifyCollectionChanged) interface, then SfDataGrid control will automatically refresh the UI when item is added, removed or while list cleared. When you add, remove item in [ObservableCollection](https://msdn.microsoft.com/library/ms668604), SfDataGrid automatically refresh the UI as `ObservableCollection` implements `INotifyCollectionChanged`. But when you do the same in [List](https://msdn.microsoft.com/en-us/library/6sh2ey19), SfDataGrid will not refresh the UI automatically.

## Binding with IEnumerable

SfDataGrid control supports to bind any collection that implements the [IEnumerable](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable) interface. All the data operations such as sorting, grouping, filtering, summaries are supported when you are binding collection derived from IEnumerable.

## Binding with dynamic data object

SfDataGrid control supports to bind [dynamic data object](https://msdn.microsoft.com/en-us/library/system.dynamic). Below are the limitations when you are binding dynamic data object,

1. SfDataGrid doesn’t support [LiveDataUpdateMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_LiveDataUpdateMode) - `AllowDataShaping` and `AllowSummaryUpdate`.

2. In WinRT, UI won’t get refreshed when you are changing the property value. This is limitation in WinRT platform.
All the data operations (sorting, grouping, filtering and etc.) are supported when you are binding dynamic data object. If the data operations are not working as expected, set [SfDataGrid.IsDynamicItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_IsDynamicItemsSource) property as `true` . 
 
## Binding Complex properties

SfDataGrid control provides support to bind complex property to its columns. To bind the complex property to [GridColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridColumn.html), set the complex property path to [MappingName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_MappingName).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid AutoGenerateColumns="False" ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" />
        <syncfusion:GridTextColumn MappingName="Customer.CustomerID" />
        <syncfusion:GridTextColumn MappingName="ShipCity" />
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

All the data operations (sorting, grouping, filtering and etc.) are supported when you are binding complex property. If the data operations are not working as expected, set [GridColumn.UseBindingValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridColumn.html#Syncfusion_UI_Xaml_DataGrid_GridColumn_UseBindingValue) as `true` to make it work. 

### Limitations when binding complex property 

* SfDataGrid doesn’t support [LiveDataUpdateMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_LiveDataUpdateMode) - `AllowDataShaping` and `AllowSummaryUpdate`.

## Binding Indexer properties

SfDataGrid control provides support to bind an indexer property to its columns. To bind an indexer property to [GridColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridColumn.html), set the indexer property path to [MappingName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_MappingName)

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid" ItemsSource="{Binding Students}" AutoGenerateColumns="False">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="RollNo"/>
        <syncfusion:GridTextColumn MappingName="Name"/>
        <syncfusion:GridTextColumn MappingName="Marks[0]"/>
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.Columns.Add(new GridTextColumn() {MappingName="Marks[0]"});
{% endhighlight %}
{% endtabs %}

All the data operations (sorting, grouping, filtering and etc.) are supported when you are binding indexer property. If the data operations are not working as expected, set [GridColumn.UseBindingValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridColumn.html#Syncfusion_UI_Xaml_DataGrid_GridColumn_UseBindingValue) as `true` to make it work.
 
### Limitations when binding indexer property 

* SfDataGrid doesn’t support [LiveDataUpdateMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_LiveDataUpdateMode) - `AllowDataShaping` and `AllowSummaryUpdate`.

## Defining source data type

Based on type of data item bound to SfDataGrid, the data operations and column auto generation are carried out. You can specify the type of underlying data item explicitly for doing data operation by setting [SfDataGrid.SourceType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_SourceType) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid" ItemsSource="{Binding Orders}" SourceType="{x:Type local:OrderInfo}"/>
{% endhighlight %}
{% highlight c# %}
dataGrid.SourceType = typeof(OrderInfo);
{% endhighlight %}
{% endtabs %}

For example, when you set [SourceType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_SourceType) property, the columns are generated based on members of SourceType regardless of data items actual type. When your `ItemsSource` have different types derived from same type, you can set SourceType as base type for all different types.


## Events

### ItemsSourceChanged

[SfDataGrid.ItemsSourceChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_ItemsSourceChanged) event occurs when the data source is changed by using ItemsSource property.
This event receives two arguments namely `sender` that handles `SfDataGrid` and [GridItemsSourceChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridItemsSourceChangedEventArgs.html) as objects.

The [GridItemsSourceChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridItemsSourceChangedEventArgs.html) object contains the following properties

* [OldItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridItemsSourceChangedEventArgs.html#Syncfusion_UI_Xaml_DataGrid_GridItemsSourceChangedEventArgs_OldItemsSource) - Gets the value of old data source
* [NewItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridItemsSourceChangedEventArgs.html#Syncfusion_UI_Xaml_DataGrid_GridItemsSourceChangedEventArgs_NewItemsSource) - Get the value of new data source


## View 

DataGrid has the View property of type `ICollectionViewAdv` interface that implements ICollectionView interface. View is responsible for maintain and manipulation data and other advanced operations like Sorting, Grouping, Filtering and etc. When you bind Collection to `ItemsSource` property of SfDataGrid, then View will be created and maintains the operations on Data such as Grouping, Filtering, Sorting, Insert, Delete, and Modification. Following are some important properties that can be used for various purposes.

N> DataGrid creates different types of views derived from [ICollectionViewAdv](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.ICollectionViewAdv.html) interface based on ItemsSource.

<table>
<tr>
<th>Property</th>
<th>Type</th>
<th>Description</th>
</tr>
<tr>
<td>Records</td>
<td>IRecordsList</td>
<td>Maintains the Records that are displayed in View when DataGrid is not Grouped.</td></tr>
<tr>
<td>TopLevelGroup</td>
<td>TopLevelGroup</td>
<td>Maintains the Group information when DataGrid is Grouped.</td>
</tr>
<tr>
<td>TopLevelGroup.DisplayElements</td>
<td>GroupDisplayElements</td>
<td>Maintains the Records and Group information that are displayed in View when DataGrid is Grouped.</td>
</tr>
<tr>
<td>Filter</td>
<td>Predicate&lt;object&gt;</td>
<td>Get or sets the method that determines the data is suitable to be displayed in View. </td>
</tr>
<tr>
<td>FilterPredicates</td>
<td>ObservableCollection&lt;IFilterDefinition&gt;</td>
<td>Maintains the FilterPredicates that are created while filtering using Filtering UI. </td>
</tr>
<tr>
<td>Groups</td>
<td>ReadOnlyObservableCollection&lt;object&gt;</td>
<td>Maintains the top-level group information. It returns null value when there are no groups. </td>
</tr>
<tr>
<td>GroupDescriptions</td>
<td>ObservableCollection&lt;GroupDescription&gt;</td>
<td>Maintains the GroupDescription collection information. It describes how the items in the collection are grouped in the view.</td>
</tr>
<tr>
<td>SortDescriptions</td>
<td>SortDescriptionCollection</td>
<td>Maintains the SortDescription collection information. It describes how the items in the collection are sort in the view.</td>
</tr>
<tr>
<td>SourceCollection</td>
<td>IEnumerable</td>
<td>Maintains the underlying source collection.</td>
</tr>
<tr>
<td>TableSummaryRows</td>
<td>ObservableCollection&lt;ISummaryRow&gt;</td>
<td>Maintains the TableSummaryRows collection information. To know more about TableSummaries {{ '[click here](https://help.syncfusion.com/winui/datagrid/summaries)' | markdownify }} </td>
</tr>
<tr>
<td>SummaryRows</td>
<td>ObservableCollection&lt;ISummaryRow&gt;</td>
<td>Maintains the SummaryRows collection information. To know more about summaries {{ '[click here](https://help.syncfusion.com/winui/datagrid/summaries)' | markdownify }} </td>
</tr>
<tr>
<td>CaptionSummaryRows</td>
<td>ISummaryRow</td>
<td>Maintains the CaptionSummaryRow information. To know more about CaptionSummaries {{ '[click here](https://help.syncfusion.com/winui/datagrid/summaries)' | markdownify }} </td>
</tr>
</table>


The following events are associated with View.

### RecordPropertyChanged

[RecordPropertyChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.ICollectionViewAdv.html#Syncfusion_UI_Xaml_Data_ICollectionViewAdv_RecordPropertyChanged) event is raised when the DataModel property value is changed, if the DataModel implements the `INotifyPropertyChanged` interface. The event receives with two arguments namely sender that handles the DataModel and [PropertyChangedEventArgs](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.PropertyChangedEventArgs)&rd=true) as object.

`PropertyChangedEventArgs` has below property,

[PropertyName](https://msdn.microsoft.com/en-us/library/system.componentmodel.propertychangedeventargs.propertyname) – It denotes the PropertyName of the changed value.

### CollectionChanged

[CollectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.CollectionViewAdv.html#Syncfusion_UI_Xaml_Data_CollectionViewAdv_CollectionChanged) event is raised whenever that is some change in Records / DisplayElements collection. The event receives two arguments namely sender that handles View object and [NotifyCollectionChangedEventArgs](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs)&rd=true) as object.

[NotifyCollectionChangedEventArgs](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs)&rd=true) has below properties,

[Action](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.Action)&rd=true) - It contains the current action. (i.e) Add, Remove, Move, Replace, Reset.

[NewItems](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.NewItems)&rd=true) - It contains the list of new items involved in the change.

[OldItems](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldItems)&rd=true) - It contains the list of old items affected by the Action.

[NewStartingIndex](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.NewStartingIndex)&rd=true) - It contains the index at which the change occurred.

[OldStartingIndex](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex)&rd=true)-It contains the index at which the Action occurred.

### SourceCollectionChanged

[SourceCollectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.CollectionViewAdv.html#Syncfusion_UI_Xaml_Data_CollectionViewAdv_SourceCollectionChanged) event is raised when you make changes in SourceCollection for example add or remove the collection. The event receives two arguments namely sender that handles GridQueryableCollectionViewWrapper object and `NotifyCollectionChangedEventArgs` as object.

`NotifyCollectionChangedEventArgs` has below properties,

[Action](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.Action)&rd=true) - It contains the current action. (i.e) Add, Remove, Move, Replace, Reset.

[NewItems](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.NewItems)&rd=true) - It contains the list of new items involved in the change.

[OldItems](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldItems)&rd=true) - It contains the list of old items affected by the Action.

[NewStartingIndex](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.NewStartingIndex)&rd=true) - It contains the index at which the change occurred.

[OldStartingIndex](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex)&rd=true) - It contains the index at which the Action occurred.

The following is the methods that are associated with View which can be used to defer refresh the view.

<table>
<tr>
<th>Method Name</th>
<th>Description</th>
</tr>
<tr>
<td>DeferRefresh</td>
<td>
Enter the defer cycle so that you can perform all data operations in view and update once. </td>
</tr>
<tr>
<td>BeginInit & EndInit</td>
<td>
When BeginInit method is called it suspends all the updates until EndInit method is called. You can perform all the updation with in these methods and update the view at once.</td>
</tr>
</table>


N> View has properties that already defined in SfDataGrid. It recommended setting those properties via SfDataGrid.

## Maintain scroll position when changing the ItemsSource for SfDataGrid

By default, the scrollbar position is not maintained and gets reset when changing the ItemsSource of the SfDataGrid. But, you can maintain the scrollbar position of the SfDataGrid by setting the [SfDataGrid.CanMaintainScrollPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_CanMaintainScrollPosition) value to `true`.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        CanMaintainScrollPosition="True"
                        ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% highlight c# %}
dataGrid.CanMaintainScrollPosition = true;
{% endhighlight %}
{% endtabs %}