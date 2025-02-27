---
layout: post
title: CRUD Operations in WinUI TreeView control | Syncfusion®
description: Learn here all about CRUD Operations support in Syncfusion® WinUI TreeView(SfTreeView) control and more.
platform: WinUI
control: SfTreeView
documentation: ug
---

# CRUD Operations in WinUI TreeView

TreeView listens and responds to the CRUD operations such as add, delete and data update (property change) at runtime. Also, it supports `editing`, `delete` by pressing <kbd>Delete</kbd> key.

## Add nodes

TreeView allows user to add new node directly by adding new data object to underlying collection in bound mode and by adding [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) to [Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_Nodes) collection in unbound mode.

{% tabs %}
{% highlight c# %}
// For bound mode
(sfTreeView.DataContext as ViewModel).Countries.Add(new Country() { Name = "Germany"});

// For Unbound mode
sfTreeView.Nodes.Add(new TreeViewNode(){ Content = "Germany" });
{% endhighlight %}
{% endtabs %}

## Delete nodes

TreeView provides built-in support to delete the selected nodes in user interface (UI) by pressing <kbd>Delete</kbd> key. You can enable the deleting support by setting the [SfTreeView.AllowDeleting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_AllowDeleting) property to `true`.

{% tabs %}
{% highlight xaml %}
<treeView:SfTreeView  
                x:Name="sfTreeView" 
				AllowDeleting="True"
				ChildPropertyName="Files"
                ItemsSource="{Binding Countries}"/>
{% endhighlight %}
{% highlight c# %}
sfTreeView.AllowDeleting = true;
{% endhighlight %}
{% endtabs %}

You can delete node directly in underlying collection also using Remove () or RemoveAt (int index).

{% tabs %}
{% highlight c# %}

//For Bound mode
(sfTreeView.DataContext as ViewModel).Countries.Remove(sfTreeView.SelectedItem as Country);

// OR
(sfTreeView.DataContext as ViewModel).Orders.RemoveAt(2);

// For Unbound mode
sfTreeView.Nodes.Remove(sfTreeView.Nodes[0]);

//OR
sfTreeView.Nodes.RemoveAt(2);
{% endhighlight %}
{% endtabs %}

### Event customization

#### Delete selected nodes conditionally

You can cancel the node deletion by using the `ItemDeletingEventArgs.Cancel` of [ItemDeleting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDeleting) event. This event occurs when the node is being deleted using <kbd>Delete</kbd> key. You can skip certain nodes when deleting more than one node by removing items from [ItemDeletingEventArgs.Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemDeletingEventArgs.html#Syncfusion_UI_Xaml_TreeView_ItemDeletingEventArgs_Nodes).

{% tabs %}
{% highlight c# %}
sfTreeView.ItemDeleting += TreeView_ItemDeleting;

private void TreeView_ItemDeleting (object sender, ItemDeletingEventArgs e)
{
    var nodeCollection = e.Nodes.ToList();
    foreach (var node in nodeCollection)
    {
        var country = node.Content as Country;
        if (country != null)
        {
            if (country.Name == "Brazil")
                e.Cancel = true;
            else if (country.Name == "India")
                e.Nodes.Remove(node);
        }        
    }
}
{% endhighlight %}
{% endtabs %}


#### Reset selection after deleting the selected node

You can handle the selection after remove the nodes through [SfTreeView.SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_SelectedItem) property in [ItemDeleted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDeleted) event. This event occurs after the node is deleted using <kbd>Delete</kbd> key.

{% tabs %}
{% highlight c# %}
sfTreeView.ItemDeleted += TreeView_ItemDeleted;

private void TreeView_ItemDeleted (object sender, ItemDeletedEventArgs e)
{
    if(sfTreeView.Nodes.Count > 0)
    {
        sfTreeView.SelectedItem = sfTreeView.Nodes[0].Content;
    }
}
{% endhighlight %}
{% endtabs %}

## Modify nodes

Treeview allows user to modify the data in a node by `editing`.
