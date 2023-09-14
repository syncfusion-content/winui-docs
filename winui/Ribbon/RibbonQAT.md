---
layout: post
title: Quick Access Toolbar | WinUI | Ribbon | Syncfusion
description: Learn more about the Quick Access Toolbar  in the Syncfusion WinUI Ribbon (SfRibbon) control.
platform: winui
control: Ribbon
documentation: ug
---

# Quick Access Toolbar in WinUI Ribbon

The Quick Access Toolbar (QAT) is used to render a set of ribbon items that are commonly used in applications. It renders at the top-left corner of a window or ribbon to make it more accessible. Users can place it above or below the ribbon, remove commands from it, or add commands to it.

## Adding Quick Access Toolbar in Ribbon 

To add Quick Access Toolbar in Ribbon control, set the QuickAccessToolBar property of Ribbon. The below code shows how to add the `Quick Access Toolbar` in Ribbon.

{% tabs %}
{% highlight xaml %}

 <ribbon:SfRibbon x:Name="ribbon" >
            <ribbon:SfRibbon.QuickAccessToolBar>
                <ribbon:QuickAccessToolBar />
            </ribbon:SfRibbon.QuickAccessToolBar>
</ribbon:SfRibbon>

{% endhighlight %}
{% endtabs %}

![Add items through context menu in QAT](Ribbon-QAT-images/default-qat.png)

## Adding items in Quick Access Toolbar

Ribbon items can be added in the Quick Access Toolbar (QAT) by following below ways:

 * Adding items through Code.
 * Customizing items at runtime.
 * Adding items using QAT MenuItems.

 N> Currently, Ribbon Gallery and RibbonItemHost is not supported as a QAT add-in.

 ### Adding items through Code

To add the ribbon items in Ribbon Quick Access Toolbar through code behind, you need to populate the QuickAccessToolbar `Items` collection. The below code shows how to add the ribbon items in `Quick Access Toolbar` of Ribbon.

{% tabs %}
{% highlight xaml %}

 <ribbon:SfRibbon x:Name="ribbon" >
            <ribbon:SfRibbon.QuickAccessToolBar>
                <ribbon:QuickAccessToolBar>
                    <ribbon:RibbonButton x:Name="SaveButton"
                                         Content="Save"
                                         Icon="Save"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Save"/>
                    <ribbon:RibbonButton x:Name="undoButton"
                                         Content="Undo"
                                         Icon="Undo"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Undo"/>
                    <ribbon:RibbonButton x:Name="printButton"
                                         Content="Print"
                                         Icon="Print"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Print"/>                       
                </ribbon:QuickAccessToolBar>
            </ribbon:SfRibbon.QuickAccessToolBar>
</ribbon:SfRibbon>

{% endhighlight %}
{% endtabs %}

![Default QAT item in Ribbon control](Ribbon-QAT-images/above-ribbon.png)


### Customizing items at runtime

To add an item at runtime to the Quick Access Toolbar (QAT) through context menu, right-click the required ribbon item and select `Add to Quick Access Toolbar`. The respective item will then be added to the QAT. 

![Add items through context menu in QAT](Ribbon-QAT-images/add-items-in-qat.png)

After clicking the context menu, the respective item will be added to the Quick Access Toolbar (QAT).

![Added item through context menu in QAT](Ribbon-QAT-images/added-item-in-qat.png)


### Adding items using QAT MenuItems

The Ribbon also supports adding items to the QAT Menu items. To add items to the drop-down menu of the Quick Access Toolbar, use the `MenuItems` property of the Quick Access Toolbar. Items can be added to the QAT by making the selection.

In `MenuItems`, define the ribbon items that are either already contain in the Ribbon Tabs or not in the Ribbon Tabs. If the item is not in the Ribbon Tab, specify all the required properties. Otherwise, providing the 'Content' is sufficient.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon.QuickAccessToolBar>
       <ribbon:QuickAccessToolBar>
               <ribbon:RibbonButton x:Name="SaveButton"
                                    Content="Save"
                                    Icon="Save"
                                    Command="{Binding ButtonCommand}"
                                    CommandParameter="Save"/>
               <ribbon:RibbonButton x:Name="undoButton"
                                    Content="Undo"
                                    Icon="Undo"
                                    Command="{Binding ButtonCommand}"
                                    CommandParameter="Undo"/>
               <ribbon:RibbonButton x:Name="printButton"
                                    Content="Print"
                                    Icon="Print"
                                    Command="{Binding ButtonCommand}"
                                    CommandParameter="Print"/>
               <ribbon:QuickAccessToolBar.MenuItems>
                       <ribbon:RibbonButton  x:Name="Share"     
                                             Icon="Share"
                                            Content="Share"/>
                       <ribbon:RibbonToggleButton Content="Italic"/>
                       <ribbon:RibbonSplitButton Content="Underline"/>
                       <ribbon:RibbonDropDownButton  Content="Select"/>
                       <ribbon:RibbonDropDownButton Content="New File"/>
               </ribbon:QuickAccessToolBar.MenuItems>
        </ribbon:QuickAccessToolBar>
</ribbon:SfRibbon.QuickAccessToolBar>

{% endhighlight %}
{% endtabs %}

![QAT menu items](Ribbon-QAT-images/selection-after-adding.png)

N> QAT items are unique, so when adding them through MenuItems or through code, it's important to provide Content to avoid duplicates.

## Removing QAT items

To remove a QAT item, right-click on the item in the QAT and select `Remove from Quick Access Toolbar`. 

![Remove QAT items from QAT](Ribbon-QAT-images/remove-items.png)

After clicking the context menu, the respective item will be removed from the Quick Access Toolbar (QAT).

![Removed QAT items from QAT](Ribbon-QAT-images/item-removed.png)


## Position of Quick Access Toolbar

The Quick Access Toolbar supports the following position:
* Above the Ribbon
* Below the Ribbon
* Hide

The position of the QAT can be dynamically adjusted either above or below the ribbon throughh context menu.

![Context menu for QAT Position](Ribbon-QAT-images/position-of-qat.png)

The default position is above the ribbon. To hide Quick Access Toolbar, set the Position as "Hide".

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon x:Name="ribbon" >
            <ribbon:SfRibbon.QuickAccessToolBar>
                <ribbon:QuickAccessToolBar Position="AboveRibbon">
                    <ribbon:RibbonButton x:Name="SaveButton"
                                         Content="Save"
                                         Icon="Save"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Save"/>
                    <ribbon:RibbonButton x:Name="undoButton"
                                         Content="Undo"
                                         Icon="Undo"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Undo"/>
                    <ribbon:RibbonButton x:Name="printButton"
                                         Content="Print"
                                         Icon="Print"
                                         Command="{Binding ButtonCommand}"
                                         CommandParameter="Print"/>                       
                </ribbon:QuickAccessToolBar>
            </ribbon:SfRibbon.QuickAccessToolBar>
</ribbon:SfRibbon>

{% endhighlight %}
{% endtabs %}

**QAT in above Ribbon**

![QAT position in above ribbon](Ribbon-QAT-images/above-ribbon.png)

**QAT in below Ribbon**

![QAT position in below ribbon](Ribbon-QAT-images/below-ribbon.png)

## Command Label

When the QAT is positioned below the Ribbon, it supports command labels at runtime. To show or hide the command label for QAT items, click `Show Command Labels` or `Hide Command Labels` in the Context menu.


**Show Command Labels**

![Show Command Label](Ribbon-QAT-images/show-command-label.png)

**Hide Command Labels**

![Hide Command Label](Ribbon-QAT-images/below-ribbon.png)

## Overflow in QAT

When the Quick Access Toolbar (QAT) panel contains an excessive number of items, it may exceed the available space within the QAT panel's size. In such cases, these additional items will be displayed within an Overflow button.

![QAT overflow menu items in Ribbon control](Ribbon-QAT-images/qat-overflow-items.png)