---
layout: post
title: Select colors from more color dialog in WPF SfColorPalette control | Syncfusion
description: Learn about selecting a different colors from more color dialog in Syncfusion WPF SfColorPalette control and more details about the control features.
platform: wpf
control: SfColorPalette
documentation: ug
---

## Choosing a color from MoreColor dialog

In addition to colors in `Theme colors` and `Standard colors`, `MoreColor` feature allows you to select wide range of color options. You can select any custom color with various opacity level based on requirement.

## Select a color from MoreColor dialog

If you wants any custom colors to select with various opacity level, click the more color button and select the color from color spectrums and click the `Ok` button. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ShowMoreColorsButton="true"
                           Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfColorPalette.ShowMoreColorsButton = true;

{% endhighlight %}
{% endtabs %}

![SfColorPalette with more color dialog](Getting-Started_images/MoreColorWindow.gif)

## Hide more color option

If you want to restrict the user to select the color from `MoreColor` dialog, hide the `MoreColor` button by using `ShowMoreColorsButton` property value as `false`. The default value of `ShowMoreColorsButton` property is `true`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ShowMoreColorsButton="False"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.ShowMoreColorsButton = false;

{% endhighlight %}
{% endtabs %}

![SfColorPalette hides the more color option](Working-with-SfColorPalette_images/ShowDefaultColorButton.png)
