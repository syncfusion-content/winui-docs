---
layout: post
title: Select colors from more color dialog in WPF SfColorPalette control | Syncfusion
description: Learn about selecting a different colors from more color dialog in Syncfusion WPF SfColorPalette control and more details about the control features.
platform: wpf
control: SfColorPalette
documentation: ug
---

## Choosing a color from MoreColor dialog

In addition to colors in `Theme colors` and `Standard colors`, `MoreColor` feature allows you to select wide range of color options from the WinUI [ColorPalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html). You can select any custom color with various opacity level based on requirement.

## Select a color from MoreColor dialog

If you wants any custom colors to select with various opacity level, click the more color button and select the color from color spectrums and click the `Ok` button. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ShowMoreColorsButton="true"
                           Name="ColorPalette"/>

{% endhighlight %}
{% highlight C# %}

ColorPalette.ShowMoreColorsButton = true;

{% endhighlight %}
{% endtabs %}

![ColorPalette with more color dialog](Getting-Started_images/MoreColorWindow.gif)

## Hide more color option

If you want to restrict the user to select the color from `MoreColor` dialog, hide the `MoreColor` button by using [ShowMoreColorsButton](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ShowMoreColorsButton) property value as `false`. The default value of `ShowMoreColorsButton` property is `true`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ShowMoreColorsButton="False"
                           Name="ColorPalette" />

{% endhighlight %}
{% highlight C# %}

ColorPalette.ShowMoreColorsButton = false;

{% endhighlight %}
{% endtabs %}

![ColorPalette hides the more color option](Working-with-SfColorPalette_images/ShowDefaultColorButton.png)
