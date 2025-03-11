---
layout: post
title: Context Flyout in WinUI TreeGrid control | Syncfusion®
description: Learn here all about Context Flyout support in Syncfusion® WinUI TreeGrid(SfTreeGrid) control and more.
platform: winUI
control: SfTreeGrid
documentation: ug
---

# Context Flyout in WinUI TreeGrid

SfTreeGrid provides an entirely customizable ContextFlyout to expose the functionalities on user interface. You can create ContextFlyout for different rows in an efficient manner.

## Context flyout for record rows

You can set the context menu to data rows using the [SfTreeGrid.ContextFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_RecordContextFlyout) property.
  
{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid.ContextFlyout>
    <MenuFlyout>
        <MenuFlyoutItem  x:Name="Cut" Text="Cut" />
        <MenuFlyoutItem  x:Name="Copy" Text="Copy"  />
        <MenuFlyoutItem  x:Name="Paste" Text="Paste" />
        <MenuFlyoutItem  x:Name="Delete" Text="Delete" />
    </MenuFlyout>
</treeGrid:SfTreeGrid.ContextFlyout>

{% endhighlight %}
{% endtabs %}

<img src="Context-flyout_images/ContextFlyout_image1.png" alt="ContextFlyout added for record rows in WinUI TreeGrid" width="100%" Height="Auto"/>

## Context flyout for header row

You can set the context menu to header using the [SfTreeGrid.HeaderContextFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_HeaderContextFlyout) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid.HeaderContextFlyout>
    <MenuFlyout>
        <MenuFlyoutItem  x:Name="SortAscending" Text="Sort Ascending" />
        <MenuFlyoutItem  x:Name="SortDescending" Text="Sort Descending"  />
        <MenuFlyoutItem  x:Name="ClearSorting" Text="Clear Sorting" />
        <MenuFlyoutItem  x:Name="ClearFiltering" Text="Clear Filtering" />
    </MenuFlyout>
</treeGrid:SfTreeGrid.HeaderContextFlyout>


{% endhighlight %}
{% endtabs %}

<img src="Context-flyout_images/ContextFlyout_image2.png" alt="ContextFlyout for header in treegrid WinUI" width="100%" Height="Auto"/>


## Context flyout for expander

You can set the context menu to expander using the [SfTreeGrid.ExpanderContextFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_ExpanderContextFlyout) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid.ExpanderContextFlyout>
    <MenuFlyout>
        <MenuFlyoutItem x:Name="Expand" Text="Expand" />
        <MenuFlyoutItem x:Name="Collapse" Text="Collapse" />
    </MenuFlyout>
</treeGrid:SfTreeGrid.ExpanderContextFlyout>

{% endhighlight %}
{% endtabs %}

## Events

The [TreeGridContextFlyoutOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_TreeGridContextFlyoutOpening) event occurs when opening the context flyout in SfTreeGrid. [TreeGridContextFlyoutEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridContextFlyoutEventArgs.html) has the following members, which provide information about the TreeGridContextFlyoutOpening event:
  
[ContextFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridContextFlyoutEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridContextFlyoutEventArgs_ContextFlyout) – Gets the corresponding context flyout. 
[ContextFlyoutInfo](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridContextFlyoutEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridContextFlyoutEventArgs_ContextFlyoutInfo) – Returns the context menu info based on the row that opens the context menu.
[ContextFlyoutType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridContextFlyoutEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridContextFlyoutEventArgs_ContextFlyoutType) – Returns the type of context menu.
[RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridContextFlyoutEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridContextFlyoutEventArgs_RowColumnIndex) – RowColumnIndex of the context menu, which is currently going to be opened. The RowColumnIndex is updated only for the RecordContextFlyout and remains empty.
[Handled](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridHandledEventArgs.html#Syncfusion_UI_Xaml_Grids_GridHandledEventArgs_Handled) - Indicates whether the TreeGridContextFlyoutOpening event is handled or not.

## Changing the menu item while context flyout opening

You can use the [TreeGridContextFlyoutOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_TreeGridContextFlyoutOpening) event to change the menu item when the context flyout opens.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid.RecordContextFlyout>
    <MenuFlyout>
        <MenuFlyoutItem  x:Name="Cut" Text="Cut" />
        <MenuFlyoutItem  x:Name="Copy" Text="Copy"  />
        <MenuFlyoutItem  x:Name="Paste" Text="Paste" />
    </MenuFlyout>
</treeGrid:SfTreeGrid.RecordContextFlyout>

{% endhighlight %}
{% highlight c# %}

treeGrid.TreeGridContextFlyoutOpening += TreeGrid_TreeGridContextFlyoutOpening;

private void TreeGrid_TreeGridContextFlyoutOpening(object sender, TreeGridContextFlyoutEventArgs e)
{
    e.ContextFlyout.Items.Clear();

    if (e.ContextFlyoutType == Syncfusion.UI.Xaml.TreeGrid.ContextFlyoutType.RecordCell)
    {
        e.ContextFlyout.Items.Add(new MenuFlyoutItem() { Text = "Record" });
        e.ContextFlyout.Items.Add(new MenuFlyoutItem() { Text = "Data" });
    }
}

{% endhighlight %}
{% endtabs %}

<img src="Context-flyout_images/ContextFlyout_image3.png" alt="ContextFlyout for opening the menu items in WinUI treegrid" width="100%" Height="Auto"/>
