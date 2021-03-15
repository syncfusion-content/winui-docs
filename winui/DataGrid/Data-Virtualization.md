---
layout: post
title: Data Virtualization | DataGrid | WinUI | Syncfusion
description: Learn about data virtualization support in Syncfusion WinUI DataGrid (SfDataGrid) control and more details.
platform: winui
control: DataGrid
documentation: ug
---

# Data Virtualization in WinUI DataGrid (SfDataGrid)

SfDataGrid provides support to handle the large amount of data through built-in virtualization features. With Data virtualization, [SfDataGrid.View](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_View) process the data in on-demand for better performance while loading large amount of data. Below are the different virtualization concepts available,

<table>
<tr>
<th>
Concept
</th>
<th>
Usage
</th>
</tr>
<tr>
<td>
<code>Data Virtualization</code>
</td>
<td>
Use to load large amount of data in less time.
</td>
</tr>
<tr>
<td>
<code>Incremental Loading</code>
</td>
<td>
Use to load subset of data from the services or servers in less time while loading and scrolling. On-demand request also supported.
</td>
</tr>
</table>

## Data Virtualization

You can load large amount of data in less time by setting [SfDataGrid.EnableDataVirtualization](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_EnableDataVirtualization) property to `true`.

{% tabs %}
{% highlight xaml %}
xmlns:dataGrid="using:Syncfusion.UI.Xaml.DataGrid"

<dataGrid:SfDataGrid x:Name="sfDataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding EmployeeDetails}"
                       EnableDataVirtualization="True">
{% endhighlight %}
{% highlight c# %}
this.sfDataGrid.EnableDataVirtualization = true;
{% endhighlight %}
{% endtabs %}

## Working with GridVirtualizingCollectionView

You can load the large amount of data in less time in another way using [GridVirtualizingCollectionView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.GridVirtualizingCollectionView.html) which is derived from [VirtualizingCollectionView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.VirtualizingCollectionView.html) to [SfDataGrid.ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_ItemsSource). 

In the below code, `ViewModel` defined with `GridVirtualizingCollectionView` by passing complete records collection and bound to SfDataGrid.

{% tabs %}
{% highlight c# %}
public class ViewModel
{
    private GridVirtualizingCollectionView _gridVirtualizingItemsSource;

    public GridVirtualizingCollectionView GridVirtualizingItemsSource
    {
        get { return _gridVirtualizingItemsSource; }
        set { _gridVirtualizingItemsSource = value; }
    }

    public ViewModel()
    {
        var _orders = this.GenerateOrders();                        
        GridVirtualizingItemsSource = new GridVirtualizingCollectionView(_orders);
    }
}
{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}
<dataGrid:SfDataGrid x:Name="sfDataGrid" 
                       ColumnSizer="Star"
                       ItemsSource="{Binding GridVirtualizingItemsSource}" />
{% endhighlight %}
{% endtabs %}

### Limitations 

1. Data update using [LiveDataUpdateMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_LiveDataUpdateMode) is not supported.
2. Details view is not supported.
3. [AllowFrozenGroupHeaders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_AllowFrozenGroupHeaders) is not supported.

## Incremental Loading
 
DataGrid supports to load the data incrementally using [ISupportIncrementalLoading](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.data.isupportincrementalloading) interface.
`ISupportIncrementalLoading` interface has [LoadMoreItemsAsync](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.IncrementalList-1.html#Syncfusion_UI_Xaml_DataGrid_IncrementalList_1_LoadMoreItemsAsync_System_UInt32_) method which helps to load the data incrementally. `LoadMoreItemsAsync` called in on-demand while scrolling based on [HasMoreItems](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.IncrementalList-1.html#Syncfusion_UI_Xaml_DataGrid_IncrementalList_1_HasMoreItems) property.

If `HasMoreItems` is `false`, SfDataGrid stops calling `LoadMoreItemsAsync`.  SfDataGrid have [IncrementalList](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.IncrementalList-1.html) which is derived from `ISupportIncrementalLoading`. You can use `IncrementalList` or create collection derived from `ISupportIncrementalLoading` and bind it `SfDataGrid.ItemsSource`.

In the below code, `IncrementalList` is initialized by passing Action to its constructor for loading items incrementally.

{% tabs %}
{% highlight xaml %}
<Page.DataContext>
    <local:ViewModel />
</Page.DataContext>

<dataGrid:SfDataGrid x:Name="sfDataGrid" 
                       AllowFiltering="True"
                       AutoGenerateColumns="True"    
                       ItemsSource="{Binding IncrementalItemsSource}"/>  
{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}
Public class ViewModel
{

    public ViewModel()
    {
        IncrementalItemsSource = new IncrementalList<OrderInfo>(LoadMoreItems) { MaxItemCount = 1000 };
    }

    private IncrementalList<OrderInfo> _incrementalItemsSource;

    public IncrementalList<OrderInfo> IncrementalItemsSource
    {
        get { return _incrementalItemsSource; }
        set { _incrementalItemsSource = value; }
    }

    async Task<IList<OrderInfo>> LoadMoreItems(CancellationToken c, uint count, int baseIndex)
    {
        IList<OrderInfo> list = null;

        await Task.Run(new Action(() =>
        {
            this.GenerateOrders();
            list = _orders.Skip(baseIndex).Take(10).ToList();
        }));
        return list;
    }
}
{% endhighlight %}
{% endtabs %}

### Load data using ISupportIncrementalLoading

You can fetch the data in some user action instead of scrolling using [IncrementalList.LoadItems](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.IncrementalList-1.html#Syncfusion_UI_Xaml_Grid_IncrementalList_1_LoadItems_System_Collections_Generic_IEnumerable__0__) method.

In the below code, data fetched when you click the `Load Items` button.

{% tabs %}
{% highlight xaml %}
<Page.DataContext>
    <local:ViewModel />
</Page.DataContext>

<Grid>

    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="90" />
    </Grid.ColumnDefinitions>

    <dataGrid:SfDataGrid x:Name="sfDataGrid"
                           Grid.Column="0"
                           DataFetchSize="5"                             
                           ItemsSource="{Binding IncrementalItemsSource}" />
    <Button x:Name="LoadItems"
            Grid.Column="1"
            Command="{Binding DataContext.LoadItems,
                              ElementName=sfDataGrid}"
            Content="Load Items" />

</Grid>
{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}
public class ViewModel : INotifyPropertyChanged
{
    #region Members

    NorthwindEntities northwindEntity;

    #endregion

    #region Properties

    private IncrementalList<Order> incrementalItemsSource;

    public IncrementalList<Order> IncrementalItemsSource
    {
        get { return incrementalItemsSource; }
        set { incrementalItemsSource = value; RaisePropertyChanged("IncrementalItemsSource"); }
    }

    private DelegateCommand loadItems;
    public DelegateCommand LoadItems
    {
        get
        {
            if (loadItems == null)
                loadItems = new DelegateCommand(OnLoadItemsClicked, OnCanLoad);
            return loadItems;
        }
    }

    #endregion

    #region Ctor

    public ViewModel()
    {
        string uri = "http://services.odata.org/Northwind/Northwind.svc/";

        incrementalItemsSource = new IncrementalList<Order>(LoadMoreItems) { MaxItemCount = 20 };

        northwindEntity = new NorthwindEntities(new Uri(uri));
    }

    #endregion

    #region Methods

    async Task<IList<Order>> LoadMoreItems(CancellationToken c, uint count, int baseIndex)
    {
        IList<Order> list = null;

        await Task.Run(new Action(() =>
        {
            DataServiceQuery<Order> query = (northwindEntity.Orders as 

            query = query.Skip<Order>(baseIndex).Take<Order>((int)count) as DataServiceQuery<Order>;

            IAsyncResult ar = query.BeginExecute(null, null);

            var items = query.EndExecute(ar);

            list = items.ToList();

        }));

        return list;
    }

    private static bool OnCanLoad(object obj)
    {
        return true;
    }

    private void OnLoadItemsClicked(object obj)
    {
        LoadMoreItems(CancellationToken.None, 10, incrementalItemsSource.Count);
        incrementalItemsSource.LoadMoreItemsAsync(10);
    }
    #endregion

    #region INotifyPropertyChanged Member

    public event PropertyChangedEventHandler PropertyChanged;

    void RaisePropertyChanged(string propertyName)
    {
        if (PropertyChanged != null)
        {
            PropertyChanged(this, new PropertyChangedEventArgs(propertyName));
        }
    }

    #endregion

    public void Dispose()
    {
        if (incrementalItemsSource != null)
            incrementalItemsSource.Clear();
    }
}

{% endhighlight %}
{% endtabs %}

### Limitations

1. Deleting is not supported. You can code to delete row in application level.
2. Summary is not calculated based on [LiveDataUpdateMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_LiveDataUpdateMode).
