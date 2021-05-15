---
layout: post
title: Solid Color Selection in WinUI Color Picker control | Syncfusion
description: Learn here all about solid color selection features of Syncfusion WinUI Color Picker control with changing opacity support.
platform: WinUI
control: SfColorPicker
documentation: ug
---

# Solid Color Selection in WinUI Color Picker

This section explains how to select a solid color from different color models, how to modify their individual properties in [Color Picker](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html).

## What is solid color?

Solid color comprises a single color with its alpha value. It contains different color channels such as RGB, HSV, HSL and CMYK color channels.

## Select solid brush programmatically

You can select the solid color brush programmatically by setting the solid color brush value to the [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrush) property. You can also choose various solid color brush from different standard color models such as `RGB`, `HSV`, `HSL`, `CMYK` formats. The default value of `SelectedBrush` property is `Blue`.

{% tabs %}
{% highlight xaml %}

 <editors:SfColorPicker x:Name="colorPicker"
                        SelectedBrush="Yellow"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Select Solid Color in WinUI ColorPicker](Getting-Started_images/winui-colorpicker-select-solid-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Select solid brush interactively

You can select any solid color brush at runtime by clicking on the respective solid color brush area. You can enable only the solid color brush mode by setting the [BrushTypeOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_BrushTypeOptions) property value as `SolidColorBrush`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPicker Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Select Solid color at runtime in WinUI ColorPicker](Getting-Started_images/winui-colorpicker-solid-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Change opacity of solid brush

You can change opacity of the selected solid color brush by using the A-Alpha value editor or delicate slider in the `Color Picker`. You can hide the A-Alpha slider by using the [AlphaInputOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_AlphaInputOptions) property value as `TextInput`. The default value of the `AlphaInputOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                       AlphaInputOptions="TextInput"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.AlphaInputOptions = ColorInputOptions.TextInput;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPicker displays Opacity Value Editor](Getting-Started_images/winui-colorpicker-opacity-value-editor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Switch between color channels

The `Color Picker` contains different color channels namely `RGB`, `HSV`, `HSL` and `CMYK`. You can select any color model by setting value the [ColorChannelOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorChannelOptions) property or select it from the drop down options. The default value of `ColorChannelOptions` property is `RGB`.

{% tabs %}
{% highlight xaml %}

 <editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                        x:Name="colorPicker"
                        ColorChannelOptions="HSV"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.ColorChannelOptions = ColorChannelOptions.HSV;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPicker displays different Solid Color Modes](Select_Solid_Colors_images/winui-colorpicker-solid-color-modes.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Input options for color channel

You can change the value of selected solid color channel elements by using either text editor or delicate slider or using both. If you want to change selected solid color channel value only by using text editor or delicate slider, use the [ColorChannelInputOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorChannelInputOptions) property value as `TextInput` or `SliderInput`. The default value of `ColorChannelInputOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                       ColorChannelInputOptions="TextInput"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorChannelInputOptions = ColorInputOptions.TextInput;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPicker displays Solid Color Input Options](Select_Solid_Colors_images/winui-colorpicker-solid-color-options.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Hexadecimal editor

You can select a solid color brush by entering the hexadecimal color value to the hexadecimal value editor. You can also get the selected color hexadecimal value by using the hexadecimal value editor. You can hide the hexadecimal value editor by setting the [IsHexInputVisible](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_IsHexInputVisible) property value as `false`. The default value of `IsHexInputVisible` property is `true`.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                       IsHexInputVisible="False"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.IsHexInputVisible = false;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Hide Hexadecimal Value Editor in WinUI ColorPicker](Getting-Started_images/winui-colorpicker-hide-hexadecimal-value-editor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Expand or collapse the Color Editors visibility

You can change the visibility of hexadecimal value editor and color channel elements as expandable or collapsed state by setting the [ColorEditorsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorEditorsVisibilityMode) property value as `Expandable` or `Collapsed`. The default value of `ColorEditorsVisibilityMode` property is `Inline`.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                       ColorEditorsVisibilityMode="Expandable"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorEditorsVisibilityMode = ColorEditorsVisibilityMode.Expandable;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Expand or Collapse Color Editors Visibility in WinUI ColorPicker](Select_Solid_Colors_images/winui-colorpicker-expand-or-collpase-color-visibility.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Selected brush changed notification

You will be notified when selected solid color brush changed in `Color Picker` by  using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrushChanged) events. You can get the old and newly selected brush by using the [OldBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) and [NewBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) properties.

{% tabs %}
{% highlight XAML %}

<editors:SfColorPicker BrushTypeOptions="SolidColorBrush"
                       SelectedBrushChanged="ColorPicker_SelectedBrushChanged"
                       Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.SelectedBrushChanged += ColorPicker_SelectedBrushChanged;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# %}

private void ColorPicker_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs args) {
    var old_selectedBrush = args.OldBrush;
    var new_selectedBrush = args.NewBrush;
}

{% endhighlight %}
{% endtabs %}
