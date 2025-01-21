---
layout: post
title: Quick Access Toolbar in WinUI Ribbon control | Syncfusion
description: Learn more about the Quick Access Toolbar  in the Syncfusion WinUI Ribbon (SfRibbon) control.
platform: winui
control: Ribbon
documentation: ug
---

# Quick Access Toolbar in WinUI Ribbon

The Quick Access Toolbar (QAT) is used to render a set of ribbon items that are commonly used in applications. It renders at the top-left corner of a window or ribbon to make it more accessible. Users can place it above or below the ribbon, remove commands from it, or add commands to it.

## Adding Quick Access Toolbar in Ribbon 

To add Quick Access Toolbar in Ribbon control, set the `QuickAccessToolBar` property of Ribbon. The below code shows how to add the `Quick Access Toolbar` in Ribbon.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon" >
       <ribbon:SfRibbon.QuickAccessToolBar>
             <ribbon:QuickAccessToolBar />
       </ribbon:SfRibbon.QuickAccessToolBar>
       ...
</ribbon:SfRibbon>
{% endhighlight %}
{% endtabs %}

![WinUI Ribbon Quick Access Toolbar.](Ribbon-QAT-images/winui-ribbon-qat.png)

## Adding items in Quick Access Toolbar

Ribbon items can be added in the Quick Access Toolbar (QAT) by following below ways:

 * Adding items through Code.
 * Adding items using ContextMenu.
 * Adding items using QAT MenuItems.
 * Adding items using QAT Customize dialog window

 N> Currently, Ribbon Gallery and RibbonItemHost are not supported as a QAT add-in.

### Adding items through Code

To add the ribbon items in Quick Access Toolbar (QAT) through code behind, you need to populate the QuickAccessToolbar `Items` collection. The below code shows how to add the ribbon items in `Quick Access Toolbar` of Ribbon.

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
    ...
</ribbon:SfRibbon> 
{% endhighlight %}
{% endtabs %}

![WinUI Ribbon QAT Items.](Ribbon-QAT-images/winui-ribbon-qat-items.png)

### Adding items using ContextMenu

To add the ribbon items to the Quick Access Toolbar (QAT) through context menu, right-click the required ribbon item and select `Add to Quick Access Toolbar`. The respective item will be added to the QAT. 

![WinUI RibbonItem Context Menu.](Ribbon-QAT-images/winui-ribbon-item-context-menu.png)

![WinUI Ribbon QAT Items added at run-time.](Ribbon-QAT-images/winui-ribbon-qat-items-added-at-runtime.png)

### Adding items using QAT MenuItems

The Ribbon also supports adding items to the QAT Menu items. To add items to the drop-down menu of the Quick Access Toolbar, use the `MenuItems` property of the Quick Access Toolbar. Items can be added to the Quick Access Toolbar (QAT) by making the selection.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
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
   ...
</ribbon:SfRibbon>
{% endhighlight %}
{% endtabs %}

![WinUI Ribbon QAT menu items.](Ribbon-QAT-images/winui-ribbon-qat-menu-items.png)

## Adding items using QAT Customize dialog window

To open the QAT customize dialog window, select the `MoreCommands` option from the ContextMenu of the QAT. This dialog window showcases all available commands within the Ribbon control.

Filter the command based on ribbon tabs by using the `Choose commands from` option. Then, select the desired command and click `Add` to add the command to the right Pane of the QAT dialog window. Finally, click `OK`.

![MoreCommands option in QAT drop-down context menu.](Ribbon-QAT-images/winui-ribbon-more-commands-option.png)

![Select commands in QAT dialog window.](Ribbon-QAT-images/winui-ribbon-select-command-in-qat-dialog-window.png)

![Adding command to right pane of QAT dialog window.](Ribbon-QAT-images/winui-ribbon-add-command-to-right-pane-in-qat-dialog-window.png)

Finally, the Items are displayed in the QAT.

![Add commands to WinUI Ribbon QuickAccessToolbar.](Ribbon-QAT-images/winui-ribbon-add-commands-to-qat.png)

N> To avoid adding duplicate items in QAT, set Content property for ribbon items.

## Removing QAT items

To remove an items from Quick Access Toolbar (QAT), right-click the required QAT item and select `Remove from Quick Access Toolbar` option. 

![WinUI Ribbon QAT item context menu.](Ribbon-QAT-images/winui-ribbon-qat-item-context-menu.png)

![WinUI Ribbon QAT item removed.](Ribbon-QAT-images/winui-ribbon-qat-item-removed.png)

QAT items can also be removed by using the Customize window. Select the QAT item in the right panel, then select `Remove`. 

![WinUI Ribbon Items to QAT Customize Window.](Ribbon-QAT-images/winui-ribbon-remove-qat-item.png)

![WinUI Ribbon QAT item removed.](Ribbon-QAT-images/winui-ribbon-removed-qat-item.png)

## Change Position of Quick Access Toolbar

The position of Quick Access Toolbar (QAT) can be changed by using it `Position` property.

The Position enumeration comprises of following values: .

* **Above the Ribbon** - Displays the Quick Access Toolbar above the ribbon. 
* **Below the Ribbon** - Displays the Quick Access Toolbar below the ribbon.
* **Hide** - Hide the Quick Access Toolbar in the ribbon.

The default value is **Above the Ribbon**. The below code shows how to change the position of `Quick Access Toolbar` in Ribbon.

{% tabs %}
{% highlight xaml %}
<ribbon:SfRibbon x:Name="ribbon">
   <ribbon:SfRibbon.QuickAccessToolBar>
      <ribbon:QuickAccessToolBar Position="BelowRibbon">
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
    ...
</ribbon:SfRibbon>
{% endhighlight %}
{% endtabs %}

![WinUI Ribbon QAT below ribbon.](Ribbon-QAT-images/winui-ribbon-qat-below-ribbon.png)

The position of the QAT can also be changed using its drop-down menu option.

![WinUI Ribbon QAT drop-down menu.](Ribbon-QAT-images/winui-ribbon-qat-drop-down-menu.png)

## Command Label

You can show or hide the command label in the Quick Access Toolbar using the `Show Command Labels` or `Hide Command Labels` QAT drop-down menu item.

![WinUI Ribbon QAT show command label menu item.](Ribbon-QAT-images/winui-ribbon-qat-show-command-labels.png)

![WinUI Ribbon QAT commands with label.](Ribbon-QAT-images/winui-ribbon-qat-commands-with-label.png)

N> `Show Command Labels` or `Hide Command Labels` menu item will only be shown in QAT drop-down while placing QAT below the ribbon like in Microsoft Word.