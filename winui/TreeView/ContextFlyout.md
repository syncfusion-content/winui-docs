---
layout: post
title: ContextFlyout with WinUI TreeView control | Syncfusion
description: Learn about context flyout support and its customization with Syncfusion WinUI TreeView (SfTreeView) control and more details.
platform: WinUI
control: SfTreeView
documentation: ug
--

# ContextFlyout in WinUI TreeView (SfTreeView)

This section explains how to show ContextFlyout and using built-in commands in the TreeView.

## ContextFlyout for Nodes

The TreeView provides an entirely customizable context flyout to expose the functionality on user interface. You can create context flyout for nodes in an efficient manner.

You can set context flyout for the nodes by using `SfTreeView.ItemContextFlyout` property.

## Built-in Commands

The TreeView provides support for the following built-in commands

* `Edit` - Command to start the editing of the node.
* `DeleteNode` - Command to delete the node.
* `DeleteSelectedNodes` - Command to delete all the selected nodes.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeView x:Name="sfTreeView"
				ItemsSource="{Binding Folders}"
				ChildPropertyName="SubFiles"
                AllowEditing="True"
                SelectionMode="Multiple">
		<syncfusion:SfTreeView.ItemContextFlyout>
            <MenuFlyout>
                <MenuFlyoutItem x:Name="Edit" Text="Edit" Command="{x:Bind syncfusion:TreeViewCommands.Edit}" CommandParameter="{Binding }"/>
                <MenuFlyoutItem x:Name="DeleteNode" Text="Delete Node" Command="{x:Bind syncfusion:TreeViewCommands.DeleteNode}" CommandParameter="{Binding }"/>
                <MenuFlyoutItem x:Name="DeleteSelectedNodes" Text="Delete Selected Nodes" Command="{x:Bind syncfusion:TreeViewCommands.DeleteSelectedNodes}" CommandParameter="{Binding }"/>
            </MenuFlyout>
        </syncfusion:SfTreeView.ItemContextFlyout>
</syncfusion:SfTreeView>
{% endhighlight %}
{% endtabs %}

![WinUI TreeView with ContextFlyout using built-in commands](ContextFlyout_images/ContextFlyout_image1.png)

## Custom Commands

The TreeView allows to show context flyout using custom commands when built-in commands does not meet your requirement.

For an example, custom command is used to expand the nodes using context flyout in the following example

{% tabs %}
{% highlight xaml %}
<syncfusion:SfTreeView x:Name="sfTreeView"
				ItemsSource="{Binding Folders}"
				ChildPropertyName="SubFiles"
                AllowEditing="True"
                SelectionMode="Multiple">
    <syncfusion:SfTreeView.ItemContextFlyout>
        <MenuFlyout>
            <MenuFlyoutItem x:Name="Expand" Text="Expand" Command="{Binding TreeView.DataContext.ExpandCommand}" CommandParameter="{Binding }"/>
        </MenuFlyout>
    </syncfusion:SfTreeView.ItemContextFlyout>
</syncfusion:SfTreeView>
{% endhighlight %}
{% highlight c# %}
using Syncfusion.UI.Xaml.Core;

public class FileManagerViewModel
{
    public FileManagerViewModel()
    {
        ExpandCommand = new DelegateCommand<object>(ExecuteExpandCommand, CanExecuteExpandCommand);
    }
    
    public ICommand ExpandCommand { get; set; }
    
    private bool CanExecuteExpandCommand(object obj)
    {
            var itemContextFlyoutInfo = parameter as TreeViewItemContextFlyoutInfo;
            if (itemContextFlyoutInfo == null)
                return false;
            if (itemContextFlyoutInfo.Node.HasChildNodes)
                return true;
            return false;
    }

    private static void ExecuteExpandCommand(object obj)
    {
        var itemContextFlyoutInfo = parameter as TreeViewItemContextFlyoutInfo;
        if (itemContextFlyoutInfo == null)
            return;
        itemContextFlyoutInfo.TreeView.ExpandNode(itemContextFlyoutInfo.Node);
    }
}
{% endhighlight %}
{% endtabs %}

![WinUI TreeView with ContextFlyout using custom commands](ContextFlyout_images/ContextFlyout_image2.png)

## Events

### Conditionally displaying context flyout on right click

You can cancel showing of `ItemContextFlyout` for certain nodes using custom logic within this event by setting `ItemContextFlyoutOpeningEventArgs.Cancel` as true.

{% tabs %}
{% highlight c# %}
sfTreeView.ItemContextFlyoutOpening += TreeView_ItemContextFlyoutOpening;

private void TreeView_ItemContextFlyoutOpening(object sender, Syncfusion.UI.Xaml.TreeView.ItemContextFlyoutOpeningEventArgs e)
{
    if (e.FlyoutInfo.Node.Level == 2)
        e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

