---
layout: post
title: Select Theme colors in WinUI SfColorPalette control | Syncfusion
description: Learn about selecting a different theme colors in Syncfusion WinUI SfColorPalette control and more details about the control features.
platform: WinUI
control: SfColorPalette
documentation: ug
---

# Select Theme colors in WinUI ColorPalette (SfColorPalette)

This section explains the different types of theme colors available in the [ColorPalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html) and  how to choose the colors and its panel customizations.

## Select a color from built-in theme colors

You can select a various theme colors by setting the value to the [ActivePalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ActivePalette) property. Based on the `ActivePalette` value, the respective base theme color items are displayed with its variants. The default value of `ActivePalette` property is `Office`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette ActivePalette="Yellow"
                           Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.ActivePalette = ColorPaletteNames.Yellow;

{% endhighlight %}
{% endtabs %}

![SfColorPalette with yellow theme colors](Working-with-SfColorPalette_images/ActivePalatte.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Add your own custom colors in theme palette

If you want to allow the user to select a color from own theme colors, add that color with its name and tooltip text into the `PaletteColors.Colors` collection using the [ColorModel](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.ColorModel.html). It will generates color variants automatically. You can also customize the header text, show or hide its variants by using the [ColorPaletteModel](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.ColorPaletteModel.html). 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ShowColors="True" 
                                      ShowColorShades="True"
                                      Header="Custom Theme Colors" >
            <syncfusion:ColorPaletteModel.Colors>
                <syncfusion:ColorCollection>
                    <syncfusion:ColorModel Color="#FF11EBF8" Tooltip="Custom Aqua" />
                    <syncfusion:ColorModel Color="#FFF80FA6" Tooltip="Custom Deep Pink" />
                    <syncfusion:ColorModel Color="#FF8BA7C2" Tooltip="Custom Dark Gray" />
                    <syncfusion:ColorModel Color="#F53CDF07" Tooltip="Custom Lime Green" />
                    <syncfusion:ColorModel Color="#C2929545" Tooltip="Custom Olive Drab" />
                    <syncfusion:ColorModel Color="#2E956145" Tooltip="Custom Sienna" />
                    <syncfusion:ColorModel Color="#78458E95" Tooltip="Custom Steel Blue" />
                    <syncfusion:ColorModel Color="#8B8220E4" Tooltip="Custom Blue Violet" />
                    <syncfusion:ColorModel Color="#FF352722" Tooltip="Custom Dark Slate Gray" />
                    <syncfusion:ColorModel Color="#FF318B86" Tooltip="Custom Sea Green" />
                </syncfusion:ColorCollection>
            </syncfusion:ColorPaletteModel.Colors>                        
        </syncfusion:ColorPaletteModel>
    </syncfusion:SfColorPalette.PaletteColors>    
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.Header = "Custom Theme Colors";
colorPalette.PaletteColors.ShowColors = true;
colorPalette.PaletteColors.ShowColorShades = true;

{% endhighlight %}
{% endtabs %}

![Own colors added in the theme color palette](Working-with-SfColorPalette_images/CustomThemeColors.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Hide base theme colors

If you want allow the user to select only the variants of theme color without its base theme colors, use the `PaletteColors.ShowColors` property value as `false`. The default value of `PaletteColors.ShowColors` property is `true`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ShowColors="False"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColors = false;

{% endhighlight %}
{% endtabs %}

![ColorPalette hides the base theme color variants](Working-with-SfColorPalette_images/PalatteColors_ShowColors.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Hide theme color variants

If you want allow the user to select only the base theme colors without its variant colors, use the `PaletteColors.ShowColorShades` property value as `false`. The default value of `PaletteColors.ShowColorShades` property is `true`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ShowColorShades="False"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColorShades = false;

{% endhighlight %}
{% endtabs %}

![ColorPalette hides the theme color variants](Working-with-SfColorPalette_images/PaletteColors_ShowColorShades.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Change theme palette header text

If you want to change header text of the theme color palette, use the `PaletteColors.Header` property. The default value of `PaletteColors.Header` property is `Theme Colors`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel Header="My theme colors"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.Header = "My theme colors";

{% endhighlight %}
{% endtabs %}

![Header text of theme color palette is changed](Working-with-SfColorPalette_images/PaletteColors_Header.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Hide theme color palette header

If you want to hide header of the theme color palette, use the `PaletteColors.ShowHeader` property. The default value of `PaletteColors.ShowHeader` property is `true`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ShowHeader="False"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowHeader = false;

{% endhighlight %}
{% endtabs %}

![Header of theme color palette is collapsed](Working-with-SfColorPalette_images/PaletteColors_ShowHeader.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Custom UI for theme palette header 

You can change the appearance of theme color palette header by using the `PaletteColors.HeaderTemplate` property. 

N> The DataContext of `PaletteColors.HeaderTemplate` is `PaletteColors.Header`

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel >
            <syncfusion:ColorPaletteModel.HeaderTemplate>
                <DataTemplate>
                    <Grid Background="LightBlue">
                        <TextBlock HorizontalAlignment="Center"
                                   VerticalAlignment="Center"
                                   Text="{Binding}"
                                   FontWeight="Bold" 
                                   Foreground="Red"/>
                    </Grid>
                </DataTemplate>
            </syncfusion:ColorPaletteModel.HeaderTemplate>
        </syncfusion:ColorPaletteModel>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% endtabs %}

![Customized UI for theme color palette header](Working-with-SfColorPalette_images/PaletteColors_HeaderTemplate.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Differentiate base theme color from its variants

If you wants to differentiate base theme color from its variants, change the spacing of theme variant colors from base theme color by using the `PaletteColors.ColorShadesSpacing` property. The default value of `PaletteColors.ColorShadesSpacing` property is `10`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="ColorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ColorShadesSpacing="20"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ColorShadesSpacing = 20;

{% endhighlight %}
{% endtabs %}

![Changed the spacing between base theme color and its variants](Working-with-SfColorPalette_images/ColorShadesSpacing.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Hide theme palette

If you want to hide the theme color palette from the view, use the `PaletteColors.ShowColors` and `PaletteColors.ShowColorShades` properties values as `false`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPalette Name="colorPalette">
    <syncfusion:SfColorPalette.PaletteColors>
        <syncfusion:ColorPaletteModel ShowColors="False" 
                                      ShowColorShades="False"/>
    </syncfusion:SfColorPalette.PaletteColors>
</syncfusion:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColors = false;
colorPalette.PaletteColors.ShowColorShades = false;

{% endhighlight %}
{% endtabs %}

![Theme color palette is hidden from the ColorPalette](Working-with-SfColorPalette_images/HideThemeColor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

