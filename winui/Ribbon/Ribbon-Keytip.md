---
layout: post
title: Ribbon keytip feature in WinUI Ribbon control | Syncfusion
description: Learn more about the keytip feature in the Syncfusion WinUI Ribbon (SfRibbon) control.
platform: winui
control: Ribbon
documentation: ug
---

# Ribbon Keytip

The Syncfusion WinUI SfRibbon supports the keyboard navigation to activate the Ribbon elements using keytip and it can be enabled by setting the `KeyTipService.EnableKeyTip` attached property as True to the Ribbon control. 

The ribbon keytip can be activated through the keyboard by pressing the Alt or F10 keys, and the keytip for the ribbon elements will be displayed.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon 
        ribbon:KeyTipService.EnableKeyTip="True" />

{% endhighlight %}
{% endtabs %}

When a control's keytip is activated, the following control action is executed:

* A ribbon tab’s keytip will select the tab.
* A ribbon gallery control's keytip will open the gallery.
* A backstage menu button keytip will open the ribbon backstage.
* Using a ribbon button and launcher button keytips will execute the button's command or Click event.
* Using the keytip of a RibbonDropDownButton and RibbonSplitButton will open the button's drop-down content.


## Creating keytip for ribbon

The `KeyTipService` in a Ribbon represents the service that provides the attached properties to enable and manage the keytips to the ribbon control.

The keytip can be attached to the ribbon elements by using the `KeyTipService.AccessText` attached property. 

### Launcher button keytip

The Keytip for the launcher button can be attached by using the `KeyTipService.LauncherButtonAccessText` attached property in a ribbon group.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon ribbon:KeyTipService.EnableKeyTip="True">
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home" ribbon:KeyTipService.AccessText="H">
            <ribbon:RibbonGroup Header="Clipboard"
                                ribbon:KeyTipService.LauncherButtonAccessText="CB"
                                LauncherButtonClick="RibbonGroup_LauncherButtonClick">
                <ribbon:RibbonSplitButton Command="{Binding ButtonCommand}"
                                          CommandParameter="Paste"
                                          Content="Paste"
                                          DisplayOptions="Normal,Simplified"
                                          Icon="Paste"
                                          ribbon:KeyTipService.AccessText ="V"
                                          SizeMode="Large">
                    <ribbon:RibbonSplitButton.Flyout>
                        <MenuFlyout>
                            <MenuFlyoutItem Command="{Binding ButtonCommand}"
                                            CommandParameter="Paste -&gt;Paste Special"
                                            Text="Paste Special" 
                                            ribbon:KeyTipService.AccessText="S"/>
                            <MenuFlyoutItem Command="{Binding ButtonCommand}"
                                            CommandParameter="Paste -&gt; Set Default Paste"
                                            Text="Set Default Paste" 
                                            ribbon:KeyTipService.AccessText="A"/>
                        </MenuFlyout>
                    </ribbon:RibbonSplitButton.Flyout>
                </ribbon:RibbonSplitButton>
                <ribbon:RibbonButton Click="RibbonButton_Click"
                                         Content="Cut"
                                         DisplayOptions="Normal,Overflow"
                                         Icon="Cut"
                                         SizeMode="Normal"                                                             
                                         ribbon:KeyTipService.AccessText="X"/>
                <ribbon:RibbonButton Command="{Binding ButtonCommand}"
                                         CommandParameter="Copy"
                                         Content="Copy"
                                         DisplayOptions="Normal,Overflow"
                                         Icon="Copy"
                                         SizeMode="Normal" 
                                         ribbon:KeyTipService.AccessText="C"/>
                <ribbon:RibbonButton Command="{Binding ButtonCommand}"
                                         CommandParameter="Format Painter"
                                         Content="Format Painter"
                                         DisplayOptions="Normal,Simplified"
                                         SizeMode="Normal"
                                         ribbon:KeyTipService.AccessText="FP">
                        <ribbon:RibbonButton.Icon>
                            <FontIcon Glyph="&#xF0E3;" />
                        </ribbon:RibbonButton.Icon>
                </ribbon:RibbonButton>
            </ribbon:RibbonGroup>                
        </ribbon:RibbonTab>
        <ribbon:RibbonTab Header="Insert" 
                              ribbon:KeyTipService.AccessText="N"/>
        <ribbon:RibbonTab Header="View" 
                              ribbon:KeyTipService.AccessText="W"/>
    </ribbon:SfRibbon.Tabs>
    <ribbon:SfRibbon.RightPane>
        <StackPanel Orientation="Horizontal">
            <ribbon:RibbonButton Command="{Binding ButtonCommand}"
                                 CommandParameter="Undo"
                                 Content="Undo"
                                 Icon="Undo" 
                                 ribbon:KeyTipService.AccessText="UD"/>
            <ribbon:RibbonButton Command="{Binding ButtonCommand}"
                                 CommandParameter="Redo"
                                 Content="Redo"
                                 Icon="Redo" 
                                 ribbon:KeyTipService.AccessText="DO"/>
        </StackPanel>
    </ribbon:SfRibbon.RightPane>
</ribbon:SfRibbon>
{% endhighlight %}
{% highlight C# %}
using Syncfusion.UI.Xaml.Ribbon;

RibbonButton copyButton = new RibbonButton();
copyButton.Content = "Copy";
copyButton.SizeMode = SizeMode.Normal;
copyButton.Icon = new SymbolIcon(Symbol.Copy);
KeyTipService.SetAccessText(copyButton, "C");

{% endhighlight %}
{% endtabs %}

![Ribbon tab ketip](Ribbon-keytip-images/Ribbon-tab-keytip.png)

![Displaying keytips for ribbon items associated with ribbon tab](Ribbon-keytip-images/Ribbon-items-keytip.png)

![Displaying keytips for drop-down items associated with buttons](Ribbon-keytip-images/Ribbon-dropdown-items-keytip.png)


## Backstage keytip

The keytip for the backstage menu button can be set in RibbonBackstage using the `KeyTipService.AccessText` attached property. The same property can be used to set the keytips of backstage items such as backstage button items and tab items.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon.Backstage>
    <ribbon:RibbonBackstage ribbon:KeyTipService.AccessText="F" 
                            Target="{Binding ElementName=rootGrid}">
        <ribbon:BackstageView>
            <ribbon:BackstageView.Items>
                <ribbon:BackstageViewTabItem Header="New"
                                              Icon="NewFolder"
                                              ribbon:KeyTipService.AccessText="N"/>
                <ribbon:BackstageViewTabItem Header="Open"
                                             Icon="OpenWith"
                                             ribbon:KeyTipService.AccessText="OW"/>
                <ribbon:BackstageViewItemSeparator />
                <ribbon:BackstageViewTabItem Header="Info"
                                             ribbon:KeyTipService.AccessText="I"/>
                <ribbon:BackstageViewButtonItem Command="{Binding SaveCommand}"
                                                CommandParameter="{Binding ElementName=simplifiedRibbon}"
                                                Header="Save" 
                                                ribbon:KeyTipService.AccessText="S"/>
                <ribbon:BackstageViewButtonItem Command="{Binding CloseButtonCommand}"
                                                CommandParameter="{Binding ElementName=simplifiedRibbon}"
                                                Header="Close" 
                                                ribbon:KeyTipService.AccessText="C"/>
                </ribbon:BackstageView.Items>
                <ribbon:BackstageView.FooterItems>
                    <ribbon:BackstageViewItemSeparator />
                    <ribbon:BackstageViewTabItem Header="Account"
                                                 ribbon:KeyTipService.AccessText="A"/>
                    <ribbon:BackstageViewTabItem Header="FeedBack"
                                                 ribbon:KeyTipService.AccessText="F"/> 
                    <ribbon:BackstageViewButtonItem Command="{Binding OptionCommand}"
                                                    CommandParameter="{Binding ElementName=simplifiedRibbon}"
                                                    Header="Option" 
                                                    ribbon:KeyTipService.AccessText="ON"/>
                    </ribbon:BackstageView.FooterItems>
                </ribbon:BackstageView>
    </ribbon:RibbonBackstage>
</ribbon:SfRibbon.Backstage>

{% endhighlight %}
{% highlight C# %}
using Syncfusion.UI.Xaml.Ribbon;

 BackstageViewButtonItem closeButton = new BackstageViewButtonItem();
 closeButton.Content = "Close";
 closeButton.Icon = new SymbolIcon(Symbol.Clear);
 KeyTipService.SetAccessText(closeButton, "C");
 
{% endhighlight %}
{% endtabs %}


## Rules for defining keytips

*	The keytip access text to the ribbon elements can have a maximum of three letters. A deviation from the text count (>3)        results in an exception.

*	Avoid using the same keytip access text setting on multiple elements. 

    For example, when you attach the access text H, H or HF, HF in the same layer, the first H keytip associated element in the layer is activated while the other H or HF associated element is ignored.

*	Furthermore, do not use the same first letter for the single and double access text elements.

    For example, if you attach the access text F, FP and FPF to the two elements and then press the F key, only the F keytip associated element will be activated, while the FP, FPF associated elements will be ignored.


N> The keytip action cannot be activated for ribbon disabled elements, but we can set access text to the disabled elements and have the keytip appear disabled.

![Keytip for backsteage buttons and tab items](Ribbon-keytip-images/backstage-keytip.png)


