---
layout: post
title: Customization in WinUI SfColorPicker control | Syncfusion
description: This section describes about how to customize the elements in the SfColorPicker control and its features.
platform: WinUI
control: SfColorPicker
documentation: ug
---

# Customization of WinUI ColorPicker (SfColorPicker)

This section explains how to customize the color spectrum and switch to different modes in [ColorPicker](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html).

## Switch between solid, linear and gradient brush mode interactively

You can change the color selection mode directly at runtime by clicking on the corresponding `Solid`, `Linear` or `Radial` gradient brush mode drop down options which is placed in the top of the `ColorPicker` control.

![Switch between solid, linear and gradient brush mode](Getting-Started_images/ColorPicker_Switch_brushes.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Enable specific brush modes

You can enable the user to choose either `Solid`, `Linear` or `Radial` gradient brush or any combination of brush mode by using the `BrushTypeOptions` property. 

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush,RadialGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush | BrushTypeOptions.RadialGradientBrush;

{% endhighlight %}
{% endtabs %}

![Allow only the solid and radial gradient brush mode](Getting-Started_images/BrushTypeOptions.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Change shape of Color Spectrum

By default, color spectrum is in box shapes. If you want to change the color spectrum shapes as circle, use the [ColorSpectrumShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorSpectrumShape) property value as `Ring` . The default value of `ColorSpectrumShape` property is `Box`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker ColorSpectrumShape="Ring" 
                          BrushTypeOptions="LinearGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorSpectrumShape = ColorSpectrumShape.Ring;
colorPicker.BrushTypeOptions = BrushTypeOptions.LinearGradientBrush;

{% endhighlight %}
{% endtabs %}

![Color spectrum shapes changed as ring](Getting-Started_images/ColorSpectrumShape.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Change Color spectrum's color components

You can changes the color spectrum components as any combination of hue, saturation or value by using the [ColorSpectrumComponents](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorSpectrumComponents) property. The default value of `ColorSpectrumComponents` property is `SaturationValue`.

![Different Color spectrum combination](Getting-Started_images/ColorSpectrumComponents1.jpg)

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker ColorSpectrumComponents = "HueSaturation"
                          BrushTypeOptions="LinearGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorSpectrumComponents = ColorSpectrumComponents.HueSaturation;
colorPicker.BrushTypeOptions = BrushTypeOptions.LinearGradientBrush;

{% endhighlight %}
{% endtabs %}

![Color spectrum combination changed as HueSaturation](Getting-Started_images/ColorSpectrumComponents.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)