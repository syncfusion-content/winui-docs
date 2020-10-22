---
layout: post
title: Expand and Collapse in WinUI TreeView | Syncfusion
description: Learn here about expanding and collapsing treeview nodes in WinUI and also explains about events associated with expanding and collapsing.
platform: WinUI
control: TreeView
documentation: ug
---

# Expand and Collapse in WinUI TreeView

The [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) allows you to expand and collapse the nodes either by user interaction on the nodes or by programmatically. 

## Expand Action Trigger

 Expanding and collapsing of nodes can be performed either by tapping the expander view or in both expander view and content view by setting the [ExpandActionTrigger](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ExpandActionTrigger) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTreeView x:Name="treeView"  ExpandActionTrigger="Node" />

{% endhighlight %}
{% highlight c# %}

// Expands by tapping both expander view and content view.
treeView.ExpandActionTrigger = ExpandActionTrigger.Node;

{% endhighlight %}
{% endtabs %}

## Auto Expand Mode

By default, the Treeview items will be in collapsed state. You can define how the nodes to be expanded while loading the TreeView by using [AutoExpandMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_AutoExpandMode) property.

The `AutoExpandMode` property is only applicable for bound mode. For Unbound mode, you need to set `IsExpanded` property to `true` while creating the nodes, to be in expanded state while loading the TreeView.

* None : All items are collapsed when loaded.
* RootNodes : Expands only the root item when loaded.
* AllNodes : Expands all the items when loaded.

## Programmatic Expand and Collapse

The TreeView allows programmatic expand and collapse based on the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) and level by using following methods.

* [ExpandNode(TreeViewNode item)](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ExpandNode_Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_) - Method to expand the particular `TreeViewNode` passed to it.
* [CollapseNode(TreeViewNode item)](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_CollapseNode_Syncfusion_UI_Xaml_TreeView_Engine_TreeViewNode_) - Method to collapse the particular `TreeViewNode` passed to it.
* [ExpandNodes(int level)](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ExpandNodes_System_Int32_) - Method to expand all the items in specific level passed to it.
* [CollapseNodes(int level)](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_CollapseNodes_System_Int32_) - Method to expand all the items in specific level passed to it.

{% tabs %}
{% highlight c# %}
// Expands all the nodes of root level '0'
treeView.ExpandNodes(0);

// Collapses all the nodes of root level '0'
treeView.CollapseNodes(0);

// Expand a particular node.
treeView.ExpandNode(node);

// Collapse a particular node.
treeView.CollapseNode(node);

{% endhighlight %}
{% endtabs %}

### Expand and Collapse all the nodes

Expand and collapse all the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) programmatically at runtime by using the `TreeView.ExpandAll` method and `TreeView.CollapseAll` method.

{% tabs %}
{% highlight c# %}

//Expands all the nodes
treeView.ExpandAll();

//Collapses all the nodes
treeView.CollapseAll();

{% endhighlight %}
{% endtabs %}

## Expand and Collapse using Keyboard

TreeView allows to expand and collapse the nodes by using right and left arrows keys. To expand a node, press the right arrow key and to collapse a node, press the left arrow key on the focused item.

## Events

TreeView exposes following events to handle expanding and collapsing of items.

* [NodeCollapsing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_NodeCollapsing) - It occurs when a node is being collapsed.
* [NodeExpanding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_NodeExpanding) - It occurs when a node is being expanded.
* [NodeCollapsed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_NodeCollapsed) - It occurs when a node is collapsed.
* [NodeExpanded](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_NodeExpanded) - It occurs when a node is expanded.

The expanding and collapsing interactions can be handled with the help of `NodeCollapsing` and `NodeExpanding` events and expanded and collapsed interactions can be handled with help of `NodeCollapsed` and `NodeExpanded` events.

                                                                                                                                                                                                                              