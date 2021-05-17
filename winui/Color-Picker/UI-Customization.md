---
layout: post
title: UI Customization in WinUI Color Picker control | Syncfusion
description: Learn here all about UI customization features of Syncfusion WinUI Color Picker(SfColorPicker) control and more.
platform: WinUI
control: SfColorPicker
documentation: ug
---

# UI Customization in WinUI Color Picker

This section explains how to customize the color spectrum and switch to different modes in [Color Picker](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html).

## Switch between solid, linear and gradient brush mode interactively

You can change the color selection mode directly at runtime by clicking on the corresponding `Solid`, `Linear` or `Radial` gradient brush mode drop down options which is placed in the top of the `Color Picker` control.

![Switch between Solid, Linear and Gradient Color in WinUI Color Picker](Getting-Started_images/winui-colorpicker-switch-color-option.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Enable specific brush mode

You can enable the user to choose either `Solid`, `Linear` or `Radial` gradient brush or any combination of brush mode by using the `BrushTypeOptions` property. 

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush,RadialGradientBrush"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush | BrushTypeOptions.RadialGradientBrush;

{% endhighlight %}
{% endtabs %}

![Enable Solid and Radial Gradient Color in WinUI Color Picker](Getting-Started_images/winui-colorpicker-solid-and-radial-gradient-color.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Change shape of Color Spectrum

By default, color spectrum is in box shapes. If you want to change the color spectrum shapes as circle, use the [ColorSpectrumShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorSpectrumShape) property value as `Ring` . The default value of `ColorSpectrumShape` property is `Box`.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker ColorSpectrumShape="Ring" 
                       BrushTypeOptions="LinearGradientBrush"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorSpectrumShape = ColorSpectrumShape.Ring;
colorPicker.BrushTypeOptions = BrushTypeOptions.LinearGradientBrush;

{% endhighlight %}
{% endtabs %}

![Changing Color Spectrum Shape as Ring in WinUI Color Picker](Getting-Started_images/winui-colorpicker-spectrum-shape.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Change Color spectrum's color components

You can changes the color spectrum components as any combination of hue, saturation or value by using the [ColorSpectrumComponents](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorSpectrumComponents) property. The default value of `ColorSpectrumComponents` property is `SaturationValue`.

![WinUI ColorPicker displays different Color Spectrum Combination](Getting-Started_images/winui-colorpicker-color-spectrum-components.jpg)

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker ColorSpectrumComponents = "HueSaturation"
                       BrushTypeOptions="LinearGradientBrush"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorSpectrumComponents = ColorSpectrumComponents.HueSaturation;
colorPicker.BrushTypeOptions = BrushTypeOptions.LinearGradientBrush;

{% endhighlight %}
{% endtabs %}

![Changing Color Spectrum Combination as HueSaturation in WinUI Color Picker](Getting-Started_images/winui-colorpicker-color-spectrum-component.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)
