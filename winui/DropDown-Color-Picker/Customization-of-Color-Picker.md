---
layout: post
title: Customization of Color Picker in DropDown Color Picker | Syncfusion
description: This section describes about how to customize the Color Picker in the DropDown Color Picker (SfDropDownColorPicker) control and its additional features.
platform: WinUI
control: SfDropDownColorPicker
documentation: ug
---

# Customization of Color Picker in WinUI DropDown Color Picker

This section describes about how to customization Color Picker in [WinUI DropDown Color Picker](https://www.syncfusion.com/winui-controls/dropdown-color-picker) control.

## Customizing control in drop down

You can customize the control displayed in drop down of `DropDown Color Picker` by using [AttachedFlyout](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) and [DropDownFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownFlyout.html#properties) properties.

N> You can refer the [Color Picker](https://help.syncfusion.com/winui/color-picker/getting-started) documentation page to know more about all customization available in the `Color Picker` control.

{% tabs %}
{% highlight xaml %}

<editors:SfDropDownColorPicker Name="sfDropDownColorPicker">
    <FlyoutBase.AttachedFlyout>
        <editors:DropDownFlyout>
            <editors:SfColorPicker BrushTypeOptions="LinearGradientBrush"
                                   Width="250" />
        </editors:DropDownFlyout>
    </FlyoutBase.AttachedFlyout>        
</editors:SfDropDownColorPicker>

{% endhighlight %}
{% endtabs %}

![Color picker embedded inside the dropdown color picker](Getting-Started_images/custom_colorpicker.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDownColorPicker_as_command)
