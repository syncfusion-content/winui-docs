---
layout: post
title: Select Solid Colors in WinUI SfColorPicker control | Syncfusion
description: This section describes about how to select the solid color brush in the SfColorPicker control and its features.
platform: WinUI
control: SfColorPicker
documentation: ug
---

# Select Solid Color Brush in WinUI ColorPicker (SfColorPicker)

This section explains how to select a solid color from different color models, how to modify their individual properties in [ColorPicker](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html).

## What is solid color?

Solid color comprises a single color with its alpha, RGB, HSV, HSL, or CMYK color channels.

## Select solid color brush programmatically

You can select the solid color brush programmatically by setting the solid color brush value to the [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrush) property. You can also choose various solid color brush from different standard color models such as `RGB`, `HSV`, `HSL`, `CMYK` formats. The default value of `SelectedBrush` property is `Blue`.

{% tabs %}
{% highlight xaml %}

 <syncfusion:SfColorPicker x:Name="colorPicker"
                           SelectedBrush="Yellow"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Solid color selected from ColorPicker](Getting-Started_images/select_Solidcolor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Select solid color brush interactively

You can select any solid color brush at runtime by clicking on the respective solid color brush area. You can enable only the solid color brush mode by setting the [BrushTypeOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_BrushTypeOptions) property value as `SolidColorBrush`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPicker Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Solid color brush selected at runtime](Getting-Started_images/Solidcolor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Change opacity of solid color brush

You can change opacity of the selected solid color brush by using the A-Alpha value editor or delicate slider in the `ColorPicker`. You can hide the A-Alpha slider by using the [AlphaInputOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_AlphaInputOptions) property value as `TextInput`. The default value of the `AlphaInputOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
                          AlphaInputOptions="TextInput"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.AlphaInputOptions = ColorInputOptions.TextInput;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Show opacity value editor](Getting-Started_images/AlphaInputOptions.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Switch between solid color channels

The `ColorPicker` contains different color channels namely `RGB`, `HSV`, `HSL` and `CMYK`. You can select any color model by setting value the [ColorChannelOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorChannelOptions) property or select it from the drop down options. The default value of `ColorChannelOptions` property is `RGB`.

{% tabs %}
{% highlight xaml %}

 <syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
                           x:Name="colorPicker"
                           ColorChannelOptions="HSV"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.ColorChannelOptions = ColorChannelOptions.HSV;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Different solid color models in ColorPicker](Select_Solid_Colors_images/ColorChannels.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Input options for solid color channel

You can change the value of selected solid color channel elements by using either text editor or delicate slider or using both. If you want to change selected solid color channel value only by using text editor or delicate slider, use the [ColorChannelInputOptions](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorChannelInputOptions) property value as `TextInput` or `SliderInput`. The default value of `ColorChannelInputOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
                          ColorChannelInputOptions="TextInput"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorChannelInputOptions = ColorInputOptions.TextInput;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Different input options for solid color channel](Select_Solid_Colors_images/ColorChannelInputOptions.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Hexadecimal solid color brush value editor

You can select a solid color brush by entering the hexadecimal color value to the hexadecimal value editor. You can also get the selected color hexadecimal value by using the hexadecimal value editor. You can hide the hexadecimal value editor by setting the [IsHexInputVisible](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_IsHexInputVisible) property value as `false`. The default value of `IsHexInputVisible` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
                          IsHexInputVisible="False"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.IsHexInputVisible = false;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Hide the hexadecimal value editor](Getting-Started_images/IsHexInputVisible.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Expand or collapse the Color Editors visibility

You can change the visibility of hexadecimal value editor and color channel elements as expandable or collapsed state by setting the [ColorEditorsVisibilityMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorEditorsVisibilityMode) property value as `Expandable` or `Collapsed`. The default value of `ColorEditorsVisibilityMode` property is `Inline`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
                          ColorEditorsVisibilityMode="Expandable"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.ColorEditorsVisibilityMode = ColorEditorsVisibilityMode.Expandable;
colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush;

{% endhighlight %}
{% endtabs %}

![Expand or collapse the Color Editors visibility](Select_Solid_Colors_images/ColorEditorsVisibilityMode.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Selected solid color brush changed notification

You will be notified when selected solid color brush changed in `ColorPicker` by  using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrushChanged) events. You can get the old and newly selected brush by using the [OldBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) and [NewBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) properties.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush"
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
