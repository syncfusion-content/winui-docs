---
layout: post
title: CRUD Operations in WinUI TreeView control | Syncfusion®
description: Learn here all about CRUD Operations support in Syncfusion® WinUI TreeView(SfTreeView) control and more.
platform: WinUI
control: SfTreeView
documentation: ug
---

# CRUD Operations in WinUI TreeView

The `TreeView` listens and responds to the CRUD operations such as add, delete, and data update (property change) at runtime. It also supports `editing` and `delete` by pressing the <kbd>Delete</kbd> key.

## Add nodes

The TreeView allows the user to add a new node directly by adding a new data object to the underlying collection in bound mode and by adding a [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) to the [Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_Nodes) collection in unbound mode.

{% tabs %}
{% highlight c# %}
// For bound mode
(sfTreeView.DataContext as ViewModel).Countries.Add(new Country() { Name = "Germany"});

// For Unbound mode
sfTreeView.Nodes.Add(new TreeViewNode(){ Content = "Germany" });
{% endhighlight %}
{% endtabs %}

## Delete nodes

The TreeView provides built-in support to delete the selected nodes in the user interface (UI) by pressing the <kbd>Delete</kbd> key. You can enable the deleting support by setting the [SfTreeView.AllowDeleting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_AllowDeleting) property to `true`.

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

You can delete a node directly in the underlying collection also using `Remove()` or `RemoveAt(int index)`.

{% tabs %}
{% highlight c# %}

//For Bound mode
(sfTreeView.DataContext as ViewModel).Countries.Remove(sfTreeView.SelectedItem as Country);

// OR
(sfTreeView.DataContext as ViewModel).Countries.RemoveAt(2);

// For Unbound mode
sfTreeView.Nodes.Remove(sfTreeView.Nodes[0]);

//OR
sfTreeView.Nodes.RemoveAt(2);
{% endhighlight %}
{% endtabs %}

### Event customization

#### Delete selected nodes conditionally

You can cancel the node deletion by using the `ItemDeletingEventArgs.Cancel` property of the [ItemDeleting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDeleting) event. This event occurs when the node is being deleted using the <kbd>Delete</kbd> key. You can skip certain nodes when deleting more than one node by removing items from [ItemDeletingEventArgs.Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemDeletingEventArgs.html#Syncfusion_UI_Xaml_TreeView_ItemDeletingEventArgs_Nodes).

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

You can handle the selection after removing the nodes through the [SfTreeView.SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_SelectedItem) property in the [ItemDeleted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDeleted) event. This event occurs after the node is deleted using the <kbd>Delete</kbd> key.

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

The TreeView allows the user to modify the data in a node by using [editing](https://help.syncfusion.com/winui/treeview/editing). For more information, see the [Editing](https://help.syncfusion.com/winui/treeview/editing) documentation.
