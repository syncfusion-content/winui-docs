---
layout: post
title: Interacting with TreeView in WinUI | Syncfusion
description: Learn here about the different interactions supported on Syncfusion WinUI TreeView control and also explains the events associated with the TreeView
platform: WinUI
control: TreeView
documentation: ug
---

# Interactivity in WinUI TreeView

 This section explains about how to interact with [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) and its items.

## Interacting with TreeView items

### ItemTapped event

The [ItemTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemTapped) event will be triggered whenever tapping the item. The [ItemTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemTappedEventArgs.html) has the following members which provides the information for `ItemTapped` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) and data associated with the tapped item as its arguments.
 * `Position`: Gets the touch position in the tapped item.
 * `Handled`: Gets or sets whether the event is handled or not.

{% tabs %}
{% highlight c# %}

treeView.ItemTapped += treeView_ItemTapped;

private async void treeView_ItemTapped(object sender, ItemTappedEventArgs e)
{
    var dialog = new MessageDialog("Tapped Item: " + (e.Node.Content as Folder).FileName);
    await dialog.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

### ItemDoubleTapped event

The [ItemDoubleTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDoubleTapped) event will be triggered whenever double tapping the item. The [ItemDoubleTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemDoubleTappedEventArgs.html) has the following members providing information for the `ItemDoubleTapped` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) and data associated with the double tapped item as its arguments.
 * `Position`: Gets the touch position in the double tapped item.
 * `Handled`: Gets or sets whether the event is handled or not.

{% tabs %}
{% highlight c# %}

treeView.ItemDoubleTapped += treeView_ItemDoubleTapped;

private async void treeView_ItemDoubleTapped(object sender, ItemDoubleTappedEventArgs e)
{
    var dialog = new MessageDialog("DoubleTapped Item: " + (e.Node.Content as Folder).FileName);
    await dialog.ShowAsync();
}

{% endhighlight %}
{% endtabs %}

### ItemHolding event

The [ItemHolding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemHolding) event will be triggered whenever the item is long pressed. The 
 [ItemHoldingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemHoldingEventArgs.html) has the following members which provides the information for `ItemHolding` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) and data associated with the hold item as its arguments.
 * `Position`: Gets the touch position in the hold item.
 
{% tabs %}
{% highlight c# %}

treeView.ItemHolding += treeView_ItemHolding;

private async void treeView_ItemHolding(object sender, ItemHoldingEventArgs e)
{
    var dialog = new MessageDialog("HoldItem: " + (e.Node.Content as Folder).FileName);
    await dialog.ShowAsync();
}

{% endhighlight %}
{% endtabs %}