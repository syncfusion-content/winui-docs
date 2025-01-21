---
layout: post
title: Theme Colors in WinUI Color Palette control | Syncfusion
description: Learn here all about Theme Colors support in Syncfusion WinUI Color Palette(SfColorPalette) control and more.
platform: WinUI
control: SfColorPalette
documentation: ug
---

# Theme Colors in WinUI Color Palette

This section explains the different types of theme colors available in the [Color Palette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html) and  how to choose the colors and its panel customizations.

## Select a color from built-in theme colors

You can select a various theme colors by setting the value to the [ActivePalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ActivePalette) property. Based on the `ActivePalette` value, the respective base theme color items are displayed with its variants. The default value of `ActivePalette` property is `Office`.

![WinUI Color Palette displays Various Theme Palettes](Working-with-SfColorPalette_images/winui-colorpalette-theme-palette.jpg)

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ActivePalette="Yellow"
                        Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.ActivePalette = ColorPaletteNames.Yellow;

{% endhighlight %}
{% endtabs %}

![WinUI Color Palette with Yellow Theme Color](Working-with-SfColorPalette_images/winui-colorpalette-theme-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Add your own custom colors in theme palette

If you want to allow the user to select a color from own theme colors, add that color with its name and tooltip text into the `PaletteColors.Colors` collection using the [ColorModel](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.ColorModel.html). It will generates color variants automatically. You can also customize the header text and show or hide its variants by using the [ColorPaletteModel](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.ColorPaletteModel.html). 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowColors="True" 
                                   ShowColorShades="True"
                                   Header="Custom Theme Colors" >
            <editors:ColorPaletteModel.Colors>
                <editors:ColorCollection>
                    <editors:ColorModel Color="#FF11EBF8" Tooltip="Custom Aqua" />
                    <editors:ColorModel Color="#FFF80FA6" Tooltip="Custom Deep Pink" />
                    <editors:ColorModel Color="#FF8BA7C2" Tooltip="Custom Dark Gray" />
                    <editors:ColorModel Color="#F53CDF07" Tooltip="Custom Lime Green" />
                    <editors:ColorModel Color="#C2929545" Tooltip="Custom Olive Drab" />
                    <editors:ColorModel Color="#2E956145" Tooltip="Custom Sienna" />
                    <editors:ColorModel Color="#78458E95" Tooltip="Custom Steel Blue" />
                    <editors:ColorModel Color="#8B8220E4" Tooltip="Custom Blue Violet" />
                    <editors:ColorModel Color="#FF352722" Tooltip="Custom Dark Slate Gray" />
                    <editors:ColorModel Color="#FF318B86" Tooltip="Custom Sea Green" />
                </editors:ColorCollection>
            </editors:ColorPaletteModel.Colors>                        
        </editors:ColorPaletteModel>
    </editors:SfColorPalette.PaletteColors>    
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.Header = "Custom Theme Colors";
colorPalette.PaletteColors.ShowColors = true;
colorPalette.PaletteColors.ShowColorShades = true;

{% endhighlight %}
{% endtabs %}

![WinUI Color Palette with Custom Theme Colors](Working-with-SfColorPalette_images/winui-colorpalette-custom-theme-colors.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Hide base theme colors

If you want allow the user to select only the variants of theme color without its base theme colors, use the `PaletteColors.ShowColors` property value as `false`. The default value of `PaletteColors.ShowColors` property is `true`. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowColors="False"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColors = false;

{% endhighlight %}
{% endtabs %}

![Hide Base Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-hide-base-theme-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Hide theme color variants

If you want allow the user to select only the base theme colors without its variant colors, use the `PaletteColors.ShowColorShades` property value as `false`. The default value of `PaletteColors.ShowColorShades` property is `true`. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowColorShades="False"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColorShades = false;

{% endhighlight %}
{% endtabs %}

![Hide Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-hide-theme-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Change theme palette header text

If you want to change header text of the theme color palette, use the `PaletteColors.Header` property. The default value of `PaletteColors.Header` property is `Theme Colors`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel Header="My theme colors"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.Header = "My theme colors";

{% endhighlight %}
{% endtabs %}

![Changing Header Text of Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-header-text.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Hide theme palette header

If you want to hide the header of theme color palette, use the `PaletteColors.ShowHeader` property. The default value of `PaletteColors.ShowHeader` property is `true`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowHeader="False"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowHeader = false;

{% endhighlight %}
{% endtabs %}

![Hide Header of Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-hide-header.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Custom UI for theme palette header 

You can change the appearance of theme palette header by using the `PaletteColors.HeaderTemplate` property. 

N> The DataContext of `PaletteColors.HeaderTemplate` is `PaletteColors.Header`

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel >
            <editors:ColorPaletteModel.HeaderTemplate>
                <DataTemplate>
                    <Grid Background="LightBlue">
                        <TextBlock HorizontalAlignment="Center"
                                   VerticalAlignment="Center"
                                   Text="{Binding}"
                                   FontWeight="Bold" 
                                   Foreground="Red"/>
                    </Grid>
                </DataTemplate>
            </editors:ColorPaletteModel.HeaderTemplate>
        </editors:ColorPaletteModel>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% endtabs %}

![Customizing Header of Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-header-customization.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Adjust space between base theme color and its variants

If you wants to adjust the space between base theme color and its variants, use the `PaletteColors.ColorShadesSpacing` property. The default value of `PaletteColors.ColorShadesSpacing` property is `10`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ColorShadesSpacing="20"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ColorShadesSpacing = 20;

{% endhighlight %}
{% endtabs %}

![WinUI Color Palette displays Spacing between Base Theme Color and its Variants](Working-with-SfColorPalette_images/winui-colorpalette-color-shades-spacing.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Hide theme palette

If you want to hide the theme palette from the view, use the `PaletteColors.ShowColors` and `PaletteColors.ShowColorShades` properties values as `false`. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowColors="False" 
                                   ShowColorShades="False"/>
    </editors:SfColorPalette.PaletteColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColors = false;
colorPalette.PaletteColors.ShowColorShades = false;

{% endhighlight %}
{% endtabs %}

![Hide Theme Color in WinUI Color Palette](Working-with-SfColorPalette_images/winui-colorpalette-hide-theme-colors.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

