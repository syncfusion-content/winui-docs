---
layout: post
title: Quick Access ToolBar | WinUI | Ribbon | Syncfusion
description: Learn more about the Quick Access ToolBar  in the Syncfusion WinUI Ribbon (SfRibbon) control.
platform: winui
control: Ribbon
documentation: ug
---

# QuickAccessToolBar in WinUI Ribbon

`QuickAccessToolBar`(QAT) is a customizable bar that provides one click access to the most important and frequently used items.

## Add items in QAT

### Add items through code

QAT items can be added as follows,

{% tabs %}
{% highlight xaml %}

 <ribbon:SfRibbon x:Name="ribbon" >
            <ribbon:SfRibbon.QuickAccessToolBar>
                <ribbon:QuickAccessToolBar Positions="AboveRibbon">
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

![Default QAT item in Ribbon control](Ribbon-QAT-images/default-qat.png)

### Add items through context menu

QAT item can be add with right click on item in QAT and select `Add to Quick Access Toolbar`.

![Add items through context menu in QAT](Ribbon-QAT-images/add-items-in-qat.png)

### Removing QAT items

QAT item can be removed with right click on item in QAT and select `Remove from Quick Access Toolbar`.

![Remove QAT items from QAT](Ribbon-QAT-images/remove-items-from-qat.png)

## QAT items positions

QAT's position can be dynamically adjusted above or below the ribbon. Above the ribbon is the default value.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon x:Name="ribbon" >
            <ribbon:SfRibbon.QuickAccessToolBar>
                <ribbon:QuickAccessToolBar Positions="AboveRibbon">
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

![QAT position in above ribbon](Ribbon-QAT-images/above-ribbon.png)

![QAT position in below ribbon](Ribbon-QAT-images/below-ribbon.png)

## QAT Menu items

Ribbon also supports to add the items to QAT Menu items. To add the items to the Drop Down Menu of the QuickAccessToolBar, use the attached property, QATMenuItems of the Quick Access ToolBar . `QATMenuItems` can be added to the QAT by making the Selection.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon.QuickAccessToolBar>
                    <ribbon:QuickAccessToolBar Positions="AboveRibbon">
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
                            <ribbon:RibbonButton  x:Name="openButton1"    
                                              Icon="Bold"
                                              Content="Open"/>
                            <ribbon:RibbonToggleButton x:Name="Italic1"
                                                   Content="Italic"
                                                   Icon="Italic"/>
                            <ribbon:RibbonSplitButton x:Name="Underline"                                                 
                                                  Content="Underline"
                                                  Icon="Underline">
                                <ribbon:RibbonSplitButton.Flyout>
                                    <MenuFlyout>
                                        <MenuFlyoutItem Text="Underline" />
                                        <MenuFlyoutItem Text="Double underline" />
                                        <MenuFlyoutItem Text="Thick underline" />
                                        <MenuFlyoutItem Text="Dotted underline" />
                                    </MenuFlyout>
                                </ribbon:RibbonSplitButton.Flyout>
                            </ribbon:RibbonSplitButton>
                            <ribbon:RibbonDropDownButton  Content="Select"
                                                      Icon="SelectAll" >
                                <ribbon:RibbonDropDownButton.Flyout>
                                    <MenuFlyout>
                                        <MenuFlyoutItem  Icon="SelectAll"
                                                     Text="Select All" />
                                        <MenuFlyoutItem  Icon="SelectAll"
                                                     Text="Select Objects" />
                                        <MenuFlyoutItem  Icon="ClearSelection"
                                                     Text="Selection Pane" />
                                    </MenuFlyout>
                                </ribbon:RibbonDropDownButton.Flyout>
                            </ribbon:RibbonDropDownButton>
                            <ribbon:RibbonDropDownButton Content="New File"
                                                     AllowedSizeModes="Large">
                                <ribbon:RibbonDropDownButton.Icon>
                                    <FontIcon Glyph="&#xE7C3;" />
                                </ribbon:RibbonDropDownButton.Icon>
                                <ribbon:RibbonDropDownButton.Flyout>
                                    <MenuFlyout>
                                        <MenuFlyoutItem  Text="Empty File" />
                                        <MenuFlyoutItem  Text="Template File" />
                                    </MenuFlyout>
                                </ribbon:RibbonDropDownButton.Flyout>
                            </ribbon:RibbonDropDownButton>
                        </ribbon:QuickAccessToolBar.MenuItems>
                    </ribbon:QuickAccessToolBar>
</ribbon:SfRibbon.QuickAccessToolBar>

{% endhighlight %}
{% endtabs %}

![QAT menu items](Ribbon-QAT-images/qat-menu-items.png)

## Overflow button in QAT

When the Quick Access Toolbar (QAT) panel contains an excessive number of items, it may exceed the available space within the QAT panel's size. In such cases, these additional items will be displayed within an Overflow button.

![QAT overflow menu items in Ribbon control](Ribbon-QAT-images/qat-overflow-items.png)