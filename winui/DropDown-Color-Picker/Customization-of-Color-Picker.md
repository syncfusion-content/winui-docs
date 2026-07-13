---
layout: post
title: Customization of Color Picker in WinUI DropDown Color Picker | Syncfusion
description: This section describes how to customize the Color Picker embedded in the WinUI DropDown Color Picker (SfDropDownColorPicker) control.
platform: WinUI
control: SfDropDownColorPicker
documentation: ug
---

# Customization of Color Picker in WinUI DropDown Color Picker

This section describes how to customize the Color Picker embedded in the [WinUI DropDown Color Picker](https://www.syncfusion.com/winui-controls/dropdown-color-picker) control.

## Prerequisites

Before applying the customization in this section, make sure the following are in place:

- Install the [Syncfusion WinUI controls](https://www.nuget.org/packages/Syncfusion.Editors.WinUI/) NuGet package in your WinUI project.
- Reference the `Syncfusion.UI.Xaml.Editors` namespace in your XAML page:

{% tabs %}
{% highlight xaml %}

xmlns:editors="using:Syncfusion.UI.Xaml.Editors"

{% endhighlight %}
{% endtabs %}

## Customizing the Color Picker inside the DropDown

You can customize the control displayed in the drop-down of the DropDown Color Picker by using the [AttachedFlyout](https://learn.microsoft.com/en-us/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml.controls.primitives.flyoutbase.attachedflyout) and [DropDownFlyout](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.DropDownFlyout.html#properties) properties. `AttachedFlyout` lets you attach any flyout to the control, while `DropDownFlyout` is the default flyout used by the DropDown Color Picker.

N> You can refer to the [Color Picker](https://help.syncfusion.com/winui/color-picker/getting-started) documentation page to learn about all the customization options available in the `SfColorPicker` control.

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

The `BrushTypeOptions` property accepts a bitwise combination of `SolidColorBrush` and `LinearGradientBrush` values; the default is `SolidColorBrush | LinearGradientBrush`.

![Color picker embedded inside the DropDown Color Picker](Getting-Started_images/custom_colorpicker.jpg)

## Troubleshooting

| Issue | Possible cause | Suggested fix |
|---|---|---|
| The embedded Color Picker does not appear when the drop-down is opened. | The `AttachedFlyout` is not assigned or the namespace is missing. | Verify the `xmlns:editors` namespace is declared and the `SfColorPicker` is placed inside the `DropDownFlyout`. |
| Build error: `SfColorPicker` or `SfDropDownColorPicker` cannot be found. | The Syncfusion WinUI Editors NuGet package is not referenced. | Install `Syncfusion.Editors.WinUI` and rebuild the project. |

N> Download the demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDownColorPicker_as_command) and run it to explore the customization shown in this section.
