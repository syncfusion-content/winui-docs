---
layout: post
title: Customization of Color Palette in DropDown Color Palette | Syncfusion
description: This section describes about how to customize the Color Palette in the DropDown Color Palette (SfDropDownColorPalette) control and its additional features.
platform: WinUI
control: SfDropDownColorPalette
documentation: ug
---

# Customization of Color Palette in WinUI DropDown Color Palette

This section describes about how to customization Color Palette in [WinUI DropDown Color Palette](https://www.syncfusion.com/winui-controls/dropdown-color-palette) control.

## Customizing control in drop down

You can customize the control displayed in drop down of `DropDown Color Palette` by using [AttachedFlyout](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) and [DropDownFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownFlyout.html#properties) properties. 

N> You can refer the [Color Palette](https://help.syncfusion.com/winui/color-palette/getting-started) documentation page to know more about all customization available in the `Color Palette` control.

{% tabs %}
{% highlight xaml %}

<editors:SfDropDownColorPalette Name="sfDropDownColorPalette">
    <FlyoutBase.AttachedFlyout>
        <editors:DropDownFlyout>
            <editors:SfColorPalette ShowMoreColorsButton="False" Width="250" >
                <editors:SfColorPalette.PaletteColors>
                    <editors:ColorPaletteModel ShowColors="True" 
                                               ShowColorShades="True"
                                               Header="Custom Theme Colors" >
                        <editors:ColorPaletteModel.Colors>
                            <editors:ColorCollection>
                                <editors:ColorModel Color="#FF11EBF8" Tooltip="Custom Aqua" />
                                <editors:ColorModel Color="#FFF80FA6" Tooltip="Custom Deep Pink" />
                                <editors:ColorModel Color="#FF8BA7C2" Tooltip="Custom Dark Gray" />
                                <editors:ColorModel Color="#F53CDF07" Tooltip="Custom Lime Green" />
                                <editors:ColorModel Color="#C2929545" Tooltip="Custom Olive Drab" />
                                <editors:ColorModel Color="#2E956145" Tooltip="Custom Sienna" />
                                <editors:ColorModel Color="#78458E95" Tooltip="Custom Steel Blue" />
                                <editors:ColorModel Color="#8B8220E4" Tooltip="Custom Blue Violet" />
                                <editors:ColorModel Color="#FF352722" Tooltip="Custom Dark Slate Gray" />
                                <editors:ColorModel Color="#FF318B86" Tooltip="Custom Sea Green" />
                            </editors:ColorCollection>
                        </editors:ColorPaletteModel.Colors>
                    </editors:ColorPaletteModel>
                </editors:SfColorPalette.PaletteColors>

                <editors:SfColorPalette.StandardColors>
                    <editors:StandardPaletteModel ShowColors="True" 
                                 ShowColorShades="True"
                                 Header="Custom Standard Colors" >
                        <editors:StandardPaletteModel.Colors>
                            <editors:ColorCollection>
                                <editors:ColorModel Color = "Blue" Tooltip = "Custom Blue" />
                                <editors:ColorModel Color = "Orchid" Tooltip = "Custom Orchid" />
                                <editors:ColorModel Color = "Gray" Tooltip = "Custom Gray" />
                                <editors:ColorModel Color = "Gold" Tooltip = "Custom Gold" />
                                <editors:ColorModel Color = "SandyBrown" Tooltip = "Custom SandyBrown" />
                                <editors:ColorModel Color = "Pink" Tooltip = "Custom Pink" />
                                <editors:ColorModel Color = "Violet" Tooltip = "Custom Violet" />
                                <editors:ColorModel Color = "Yellow" Tooltip = "Custom Yellow" />
                                <editors:ColorModel Color = "Orange" Tooltip = "Custom Orange" />
                                <editors:ColorModel Color = "Red" Tooltip = "Custom Red" />
                            </editors:ColorCollection>
                        </editors:StandardPaletteModel.Colors>
                    </editors:StandardPaletteModel>
                </editors:SfColorPalette.StandardColors>
            </editors:SfColorPalette>
        </editors:DropDownFlyout>
    </FlyoutBase.AttachedFlyout>
</editors:SfDropDownColorPalette>

{% endhighlight %}
{% endtabs %}

![Color palette embedded inside the dropdown color palette](Getting-Started_images/custom_colorpalette.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/DropDownColorPalette_as_command)
