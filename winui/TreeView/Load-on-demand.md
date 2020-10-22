---
layout: post
title: Load On-demand in WinUI TreeView | Syncfusion
description: Learn here about loading nodes on demand on Syncfusion WinUI TreeView control and also explains about the handling expander visibility in TreeView.
platform: WinUI
control: TreeView
documentation: ug
---

# Load on demand in WinUI TreeView

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) allows you to load child items only when they are requested using Load on-demand(Lazy load). It helps to load the child items from services when end-user expands the node. Initially populate the root [Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_Nodes) by assigning [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemsSource) and then when any node is expanded, child items can be loaded using [LoadOnDemandCommand](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LoadOnDemandCommand). The Load on-demand is applicable for bound mode only.

{% tabs %}
{% highlight xaml %}

<Page x:Class="syncfusion.treeviewdemos.winui.LoadOnDemandPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.TreeView"
      xmlns:local="using:syncfusion.treeviewdemos.winui"
      mc:Ignorable="d"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">

<Page.DataContext>
    <local:LoadOnDemandViewModel />
</Page.DataContext>

<Grid>
    <syncfusion:SfTreeView x:Name="treeView"
                           BorderBrush="LightGray"
                           BorderThickness="1"
                           SelectionMode="Multiple"
                           ExpandActionTrigger="Node"
                           IsAnimationEnabled="True"
                           LoadOnDemandCommand="{Binding TreeViewOnDemandCommand}"
                           ItemsSource="{Binding Menu}">
                    <syncfusion:SfTreeView.ItemTemplate>
                        <DataTemplate>
                            <TextBlock VerticalAlignment="Center"
                                       Text="{Binding ItemName}" />
                        </DataTemplate>
                    </syncfusion:SfTreeView.ItemTemplate>
    </syncfusion:SfTreeView>
</Grid>
</Page>

{% endhighlight %}
{% highlight c# %}
 
public class LoadOnDemandViewModel
{
    private ObservableCollection<LoadOnDemandModel> menu;
   
    private DelegateCommand treeViewOnDemandCommand;

    public LoadOnDemandViewModel()
    {
        this.Menu = GetMenuItems();
        TreeViewOnDemandCommand = new DelegateCommand(ExecuteOnDemandLoading, CanExecuteOnDemandLoading);
    }

    public ObservableCollection<LoadOnDemandModel> Menu
    {
        get { return menu; }
        internal set { menu = value; }
    }

    public DelegateCommand TreeViewOnDemandCommand
    {
        get { return treeViewOnDemandCommand; }
        set { treeViewOnDemandCommand = value; }
    }

    public static IEnumerable<LoadOnDemandModel> GetSubMenu(int iD)
    {
        ObservableCollection<LoadOnDemandModel> menuItems = new ObservableCollection<LoadOnDemandModel>();
        if (iD == 1)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Hot Singles", HasChildNodes = false, ID = 11 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Rising Artists", HasChildNodes = false, ID = 12 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Live Music", HasChildNodes = false, ID = 13 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "More in Music", HasChildNodes = true, ID = 14 });
        }
        else if (iD == 2)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "100 Albums - $10 Each", HasChildNodes = false, ID = 21 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Hip-Hop and R&B Sale", HasChildNodes = false, ID = 22 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "CD Deals", HasChildNodes = false, ID = 23 });
        }
        else if (iD == 3)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Songs", HasChildNodes = false, ID = 31 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Bestselling Albums", HasChildNodes = false, ID = 32 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "New Releases", HasChildNodes = false, ID = 33 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "MP3 Albums", HasChildNodes = false, ID = 34 });
        }
        else if (iD == 4)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Rock Music", HasChildNodes = false, ID = 41 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Gospel", HasChildNodes = false, ID = 42 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Latin Music", HasChildNodes = false, ID = 43 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Jazz", HasChildNodes = false, ID = 44 });
        }
        else if (iD == 5)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Hunger Games", HasChildNodes = false, ID = 51 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Pride and Prejudice", HasChildNodes = false, ID = 52 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Harry Potter", HasChildNodes = false, ID = 53 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Game of Thrones", HasChildNodes = false, ID = 54 });
        }
        else if (iD == 14)
        {
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Music Trade-In", HasChildNodes = false, ID = 141 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Redeem a Gift Card", HasChildNodes = false, ID = 142 });
            menuItems.Add(new LoadOnDemandModel() { ItemName = "Band T-Shirts", HasChildNodes = false, ID = 143 });
        }
        return menuItems;
    }

    private bool CanExecuteOnDemandLoading(object sender)
    {
        var haschildnodes = ((sender as TreeViewNode).Content as LoadOnDemandModel).HasChildNodes;
        if (haschildnodes)
        {
            if ((sender as TreeViewNode).ChildNodes.Count > 0)
                return false;
            else
                return true;
        }
        else
            return false;
    }

    private async void ExecuteOnDemandLoading(object obj)
    {
        var node = obj as TreeViewNode;
        node.ShowExpanderAnimation = true;
        LoadOnDemandModel loadOnDemandModel = node.Content as LoadOnDemandModel;
        await Application.Current.Resources.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, async () => 
        {
            await Task.Delay(2000).ConfigureAwait(true);
            var items = GetSubMenu(loadOnDemandModel.ID);
            node.PopulateChildNodes(items);
            if (items.Any())
                node.IsExpanded = true;
            node.ShowExpanderAnimation = false;
        });
    }

    private static ObservableCollection<LoadOnDemandModel> GetMenuItems()
    {
        ObservableCollection<LoadOnDemandModel> menuItems = new ObservableCollection<LoadOnDemandModel>();
        menuItems.Add(new LoadOnDemandModel() { ItemName = "Discover Music", HasChildNodes = true, ID = 1 });
        menuItems.Add(new LoadOnDemandModel() { ItemName = "Sales and Events", HasChildNodes = true, ID = 2 });
        menuItems.Add(new LoadOnDemandModel() { ItemName = "Categories", HasChildNodes = true, ID = 3 });
        menuItems.Add(new LoadOnDemandModel() { ItemName = "MP3 Albums", HasChildNodes = true, ID = 4 });
        menuItems.Add(new LoadOnDemandModel() { ItemName = "Fiction Book Lists", HasChildNodes = true, ID = 5 });
        return menuItems;
    }
}

{% endhighlight %}
{% highlight c# %}

public class LoadOnDemandModel : NotificationObject
{
    private string itemName;

    private int id;

    private bool hasChildNodes;

    public string ItemName
    {
        get { return itemName; }
        set
        {
            itemName = value;
            RaisePropertyChanged(nameof(ItemName));
        }
    }

    public int ID
    {
        get { return id; }
        set
        {
            id = value;
            RaisePropertyChanged(nameof(ID));
        }
    }

    public bool HasChildNodes
    {
        get { return hasChildNodes; }
        set
        {
            hasChildNodes = value;
            RaisePropertyChanged(nameof(HasChildNodes));
        }
    }
}

{% endhighlight %}
{% endtabs %}

N> The `LoadOnDemandCommand` receives [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) as command parameter by default. 

## Handling expander visibility

The `TreeView` shows the expander for a particular node based on return value of [CanExecute](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.icommand.canexecute?view=winrt-19041) method of [LoadOnDemandCommand](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_LoadOnDemandCommand). If `CanExecute` returns `true`, then expander icon is displayed for that node. If `CanExecute` returns `false`, then expander icon will not be displayed for that node. The `CanExecute` method gets called to decide the visibility of expander icon and before executing `LoadOnDemandCommand`. 

{% tabs %}
{% highlight c# %}

private bool CanExecuteOnDemandLoading(object sender)
{
    var haschildnodes = ((sender as TreeViewNode).Content as LoadOnDemandModel).HasChildNodes;
    if (haschildnodes)
    {
        if ((sender as TreeViewNode).ChildNodes.Count > 0)
            return false;
        else
            return true;
    }
    else
        return false;
}

{% endhighlight %}
{% endtabs %}

## On-demand loading of child items

You can load child items for the node in [Execute](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.input.icommand.execute?view=winrt-19041) method of `LoadOnDemandCommand`. The Execute method will get called when user expands the tree node. In `LoadOnDemand.Execute` method, you can perform following operations,

* Show or hide busy indicator in the place of expander by setting [TreeViewNode.ShowExpanderAnimation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html#Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_ShowExpanderAnimation) until the data fetched.
* Once data fetched, you can populate the child nodes by calling [TreeViewNode.PopulateChildNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html#Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_PopulateChildNodes_System_Collections_IEnumerable_) method by passing the child items collection. 
* When load on-demand command executes expanding operation will not be handled by `TreeView`. So, you have to set [TreeViewNode.IsExpanded](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html#Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_IsExpanded) property to `true` to expand the tree node after populating child nodes.
* You can skip population of child items again and again when every time the node expands, based on [TreeViewNode.ChildNodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html#Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_ChildNodes) count. 

{% tabs %}
{% highlight c# %}

private async void ExecuteOnDemandLoading(object obj)
{
    var node = obj as TreeViewNode;
    node.ShowExpanderAnimation = true;
    LoadOnDemandModel loadOnDemandModel = node.Content as LoadOnDemandModel;
    await Application.Current.Resources.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, async () => 
    {
        await Task.Delay(2000).ConfigureAwait(true);
        var items = GetSubMenu(loadOnDemandModel.ID);
        node.PopulateChildNodes(items);
        if (items.Any())
            node.IsExpanded = true;
        node.ShowExpanderAnimation = false;
    });
}

{% endhighlight %}
{% endtabs %}

![WinUI TreeView with Load On-Demand](LoadOnDemand_images/load-on-demand.gif)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-treeview-examples/tree/main/Samples/Load-On-Demand)
