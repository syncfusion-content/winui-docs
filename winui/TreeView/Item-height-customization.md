---
layout: post
title: Item Height Customization in WinUI TreeView | Syncfusion
description: Learn here about customize the height of the items in WinUI TreeView and autofit the items based on node content.
platform: WinUI
control: TreeView
documentation: ug
---

# Item Height Customization in WinUI TreeView

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) provides various options to customize the height of items. To achieve this customization, please walkthrough the below sections:

## Customize Item Height

The TreeView allows customizing the height of items by setting the [ItemHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemHeight) property. The default value of this property is `40`. This property can be customized at runtime.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeView x:Name="treeView" ItemHeight="50" />
{% endhighlight %}
{% highlight c# %}
treeView.ItemHeight = 50;
{% endhighlight %}
{% endtabs %}

## Customize Item height using `QueryNodeSize` event
 The TreeView allows customizing the height of the items using [QueryNodeSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_QueryNodeSize) event. This event is raised whenever the item comes into view and triggered with [QueryNodeSizeEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html).

The `TreeView.QueryNodeSize` event provides the following arguments:
 
 * [Node](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html#Syncfusion_UI_Xaml_TreeView_QueryNodeSizeEventArgs_Node): This argument contains the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) and data associated with it.
 * [Height](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html#Syncfusion_UI_Xaml_TreeView_QueryNodeSizeEventArgs_Height): This argument contains the default item height of the queried item and can be set with desired size.
 * [Handled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html#Syncfusion_UI_Xaml_TreeView_QueryNodeSizeEventArgs_Handled): Decides whether the specified or measured height can be set to the item or not. The default value is `false`. When this property is not set, the decided height will not set to the item.

### Customize specific item height using custom value

The TreeView allows customizing the height of the specific item by setting the custom value directly to the [Height](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html#Syncfusion_UI_Xaml_TreeView_QueryNodeSizeEventArgs_Height) argument which is available in [QueryNodeSizeEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs.html).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeView x:Name="treeView"
                       QueryNodeSize="treeView_QueryNodeSize"    />
{% endhighlight %}
{% highlight c# %}
treeView.QueryNodeSize += treeView_QueryNodeSize;

private void treeView_QueryNodeSize(object sender, Syncfusion.UI.Xaml.TreeView.QueryNodeSizeEventArgs e)
{
    if (e.Node.Level == 0)
    {
        //Returns speified item height for items.
        e.Height = 50;
        e.Handled = true;
    }
}

{% endhighlight %}
{% endtabs %}
