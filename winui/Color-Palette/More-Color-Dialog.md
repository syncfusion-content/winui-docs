---
layout: post
title: More Colors in WinUI Color Palette control | Syncfusion&reg;
description: Learn here all about More Colors features of Syncfusion&reg; WinUI Color Palette(SfColorPalette) control and more.
platform: WinUI
control: SfColorPalette
documentation: ug
---

# More Colors in WinUI Color Palette control

This section explains the different more colors available in the [Color Palette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html) and  how to choose the colors and its panel customizations.

## Choosing a color from MoreColors dialog in WinUI Color Palette

In addition to colors in `Theme colors` and `Standard colors`, `MoreColor` feature allows you to select wide range of color options from the WinUI [Color Palette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html). You can select any custom color with various opacity level based on requirement.

## Select a color from MoreColor dialog

If you wants any custom colors to select with various opacity level, click the more color button and select the color from color spectrum and then click the `Ok` button. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ShowMoreColorsButton="true"
                        Name="colorPalette"/>

{% endhighlight %}
{% highlight C# %}

colorPalette.ShowMoreColorsButton = true;

{% endhighlight %}
{% endtabs %}

![WinUI Color Palette with More Color Window](Getting-Started_images/winui-colorpalette-more-color-window.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Hide more color option

If you want to restrict the user to select the color from `MoreColor` dialog, hide the `MoreColor` button by using [ShowMoreColorsButton](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ShowMoreColorsButton) property value as `false`. The default value of `ShowMoreColorsButton` property is `true`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ShowMoreColorsButton="False"
                        Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.ShowMoreColorsButton = false;

{% endhighlight %}
{% endtabs %}

![Hide More Color Option in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-hide-more-color-option.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)
