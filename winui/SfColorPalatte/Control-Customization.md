---
layout: post
title: Control Customization of WPF SfColorPalette control | Syncfusion
description: Learn about selecting a different types of colors in Syncfusion WPF SfColorPalette control and more details about the control features.
platform: wpf
control: SfColorPalette
documentation: ug
---

# Control Customization in WPF SfColorPalette

This section explains the different types of colors available in the `SfColorPalette` and  how to choose the colors and its panel customizations.

## Accessing a Color programmatically

You can set or change the selected color of the `SfColorPalette` programmatically by setting the value to `SelectedBrush` property. You can also get the selected color by using the `SelectedBrush` property. The default value of `SelectedBrush` property is `Transparent(#00FFFFFF)`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette SelectedBrush="Yellow"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![SfColorPalette programmatically picked the yellow color](Working-with-SfColorPalette_images/Colorprogrammatically.png)

Here, `Yellow` color is selected color in the `SfColorPalette`.

## Setting null value programmatically

You can set a null color value for the selected color by setting the color code `#00000000` or `Colors.Transparent` for `SelectedBrush` property to indicate the null value.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette SelectedBrush="Transparent"
                           Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfColorPalette.SelectedBrush = new SolidColorBrush(Colors.Transparent);

{% endhighlight %}
{% endtabs %}

![SfColorPalette with selected transparent color](Working-with-SfColorPalette_images/Nullvalue.png)

## Reset the selected color

If you want to reset the selected color as `No color` or `Transparent`, click the `No Color` button. You can display the
 `No color` button only by setting the `ShowNoColorButton` property value as `true`. The default value of `ShowNoColorButton` property is `false`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ShowNoColorButton="True"
                           Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfColorPalette.ShowNoColorButton = true;

{% endhighlight %}
{% endtabs %}

![SfColorPalette resets selected color](Working-with-SfColorPalette_images/ShowNoColorButton.png)

## Setting default color

If you want to change the default selected color on application launching, set the value for `AutomaticBrush` property. If you changed the selected color, then you can easily make the default color as selected color by clicking the default color button. The default value of `AutomaticColor` property is `Black`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette AutomaticBrush="Red"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.AutomaticBrush = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![SfColorPalette with automatic color](Working-with-SfColorPalette_images/AutomaticBrush.png)

### Hide default color button

You can hide the default color button visibility by setting the `ShowDefaultColorButton` property value as `Collapsed`. The default value of `ShowDefaultColorButton` property is `true`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette AutomaticBrush="Green"
                           ShowDefaultColorButton="False"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.AutomaticBrush = new SolidColorBrush(Colors.Red);
sfColorPalette.ShowDefaultColorButton = false;

{% endhighlight %}
{% endtabs %}

![SfColorPalette with automatic color](Working-with-SfColorPalette_images/ShowDefaultColorButton.png)

## Selected color changed notification

The selected color changed in `SfColorPalette` can be examined using `SelectedBrushChanged` event. The `SelectedBrushChanged` event contains the old and newly selected color values in the `OldBrush`, `NewBrush` properties.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette SelectedBrushChanged="SfColorPalette_SelectedBrushChanged"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.SelectedBrushChanged += SfColorPalette_SelectedBrushChanged;

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight C# %}

//Invoked when the selected color is changed
private void SfColorPalette_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs e) {
    var oldBrush= e.OldBrush;
    var newBrush= e.NewBrush;

}

{% endhighlight %}
{% endtabs %}

## Tooltip support

Tooltip is used to show the information about the segment, when you mouse over on the segment. You can show information about name of the color item using tooltip when hovering the mouse on the specific color item.

![SfColorPalette with tooltip support](Working-with-SfColorPalette_images/tooltip.gif)

## Recently used color items

The recently selected color items are displayed in the `Recent Colors` panel. If you want to choose a color which are previously selected, use the `Recent Colors` panel. You can get the recently selected color list by using the `RecentColors` collection property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfColorPalette sfColorPalette = new SfColorPalette();

//Recently selected color list 
var recentColors = sfColorPalette.RecentColors;

{% endhighlight %}
{% endtabs %}

![SfColorPalette displaying the recently used color items](Getting-Started_images/RecentColors.png)

## Setting the foreground

You can change the foreground color of the `SfColorPalette` by using the `Foreground` property. The default value of `Foreground` property is `Black`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Foreground="Red"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.Foreground = new SolidColorBrush(Colors.Red);

{% endhighlight %}
{% endtabs %}

![SfColorPalette foreground color changed](Working-with-SfColorPalette_images/Foreground.png)

## Setting the background

You can change the background color of the `SfColorPalette` by using the `Background` property. The default value of `Background` property is `null`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Background="LightYellow"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.Background = new SolidColorBrush(Colors.LightYellow);

{% endhighlight %}
{% endtabs %}

![SfColorPalette background color changed](Working-with-SfColorPalette_images/Background.png)

## Change flow direction

You can change the flow direction of the `SfColorPalette` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette FlowDirection="RightToLeft"
                           Name="sfColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfColorPalette.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![SfColorPalette with right to left flow direction](Working-with-SfColorPalette_images/rtl.png)

## Change color palette size

You can change the color palette size by using the `Width` and `Height` properties. Based on the color palette size, the color items are resized. The default value of `Width` and `Height` properties is `Auto`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Width="200" 
                           Height="300"
                           Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfColorPalette.Width = 200;
sfColorPalette.Height = 300;

{% endhighlight %}
{% endtabs %}

![SfColorPalette size changed](Working-with-SfColorPalette_images/Size.png)

## Hide the SfColorPalette

You can hide the `SfColorPalette` by setting the `Visibility` property value as `Collapsed`. The default value of `SfColorPalette.Visibility` property is `Visible`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Visibility="Collapsed"
                           Name="sfColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfColorPalette.Visibility = Visibility.Collapsed;

{% endhighlight %}
{% endtabs %}
