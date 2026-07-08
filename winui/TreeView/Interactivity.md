---
layout: post
title: Interactivity in WinUI TreeView control | Syncfusion®
description: Learn here all about Interactivity support in Syncfusion® WinUI TreeView(SfTreeView) control and more.
platform: WinUI
control: TreeView
documentation: ug
---

# Interactivity in WinUI TreeView

This section explains how to interact with the [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) and its items using the following gesture events:

* `ItemTapped` - Triggered when an item is tapped.
* `ItemDoubleTapped` - Triggered when an item is double-tapped.
* `ItemHolding` - Triggered when an item is long pressed.

## Interacting with TreeView items

### ItemTapped event

The [ItemTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemTapped) event is triggered whenever an item is tapped. The [ItemTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemTappedEventArgs.html) has the following members which provide the information for the `ItemTapped` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) and the data associated with the tapped item as its arguments.
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

The [ItemDoubleTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemDoubleTapped) event is triggered whenever an item is double-tapped. The [ItemDoubleTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemDoubleTappedEventArgs.html) has the following members providing information for the `ItemDoubleTapped` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) and the data associated with the double-tapped item as its arguments.
 * `Position`: Gets the touch position in the double-tapped item.
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

The [ItemHolding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemHolding) event is triggered whenever an item is long pressed. The
 [ItemHoldingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.ItemHoldingEventArgs.html) has the following members which provide the information for the `ItemHolding` event:

 * `Node`: Gets the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.TreeViewNode.html) and the data associated with the held item as its arguments.
 * `Position`: Gets the touch position in the held item.

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
