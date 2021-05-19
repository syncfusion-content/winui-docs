---
layout: post
title: More Colors Dialog in WinUI DropDown Color Palette | Syncfusion
description: This section describes about how to pick a additonal colors from More Colors Dialog in the DropDown Color Palette (SfDropDownColorPalette) control.
platform: WinUI
control: SfDropDownColorPalette
documentation: ug
---

# More Colors Dialog in WinUI DropDown Color Palette

This section describes about how to pick a additional colors from More Color dialog in [WinUI DropDown Color Palette](https://www.syncfusion.com/winui-controls/dropdown-color-palette) control.

## Choosing a Color from More Colors dialog

If you want to choose a color that is not available in theme and standard palette, click the **More Colors...** button and select the color from color spectrum and click the **Ok** button. 

{% tabs %}
{% highlight xaml %}

<editors:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette = new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown Color Palette with more color dialog](Getting-Started_images/MoreColorWindow.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/DropDown_ColorPalette)

## Recently used Colors

 If you want to choose a color brush which are recently selected from the `More Colors` dialog, use the `Recent Colors` panel. 

N> Colors selected from theme and standard colors will not be added in recent colors.

{% tabs %}
{% highlight xaml %}

<editors:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette = new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown Color Palette with recently used color items](Getting-Started_images/Recentcolors.png)
