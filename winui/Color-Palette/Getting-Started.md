---
layout: post
title: Getting Started with WinUI Color Palette control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Color Palette(SfColorPalette) control and more.
platform: WinUI
control: SfColorPalette
documentation: ug
---

# Getting Started with WinUI Color Palette

This section explains the steps required to add the [WinUI ColorPalette](https://www.syncfusion.com/winui-controls/color-palette) control and its various color options. This section covers only basic features needed to get started with Syncfusion `ColorPalette` control.

## Control Structure

![WinUI ColorPalette Control](Getting-Started_images/winui-colorpalette-control.png)

* The Selected Color represents the color that you select.
* The Automatic Color represents the Color, which can be set by you as default color.
* The ToolTip with Color Details represents the ToolTip, when the mouse hovers on the Color.
* The Standard Colors stores the standard colors like `Red`, `Green`, `Blue` and so on.
* The Recently User Colors stores the Colors that are recently selected.
* The No Color represents the `Transparent` color that applied as the selected color. 
* The More Colors Option provides wide range of color in addition to colors in the palette.
* The Theme Variant Colors represents the Theme colors with variants.

### More Color Dialog

![WinUI ColorPalette displays More Color Options](Getting-Started_images/winui-colorpalette-more-color-options.jpg)

## Creating an application with WinUI ColorPalette

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfColorPalette` control.

{% tabs %}
{% highlight xaml %}
<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
        <!--Adding ColorPalette control -->
        <editors:SfColorPalette Name="colorPalette"/>
    </Grid>
</Page>

{% endhighlight %}
{% highlight c# %}

using Syncfusion.UI.Xaml.Editors;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the ColorPalette control
            SfColorPalette colorPalette = new SfColorPalette();
            grid.Children.Add(colorPalette);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![Overview of WinUI ColorPalette](Getting-Started_images/winui-colorpalette-overview.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Accessing a Color programmatically

You can set or change the selected color of the `ColorPalette` programmatically by setting the value to [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_SelectedBrush) property. You can also get the selected color by using the `SelectedBrush` property. The default value of `SelectedBrush` property is `Transparent(#00FFFFFF)`.

{% tabs %}
{% highlight xaml %}

<Button Background="{Binding ElementName=colorPalette, Path=SelectedBrush}"></Button>

<editors:SfColorPalette SelectedBrush="Yellow"
                        Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Selecting Color Programmatically in WinUI ColorPalette](Working-with-SfColorPalette_images/winui-colorpalette-color-selection.png)

Here, `Yellow` color is selected color in the `ColorPalette`.

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Select color from color palette

You can select a different colors from Theme Color and Standard Color panels. You can show or hide the variant colors of the base Theme Colors and Standard Colors by using the `PaletteColors.ShowColorShades`  and `StandardColors.ShowColorShades` properties value as `true` or `false`.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette">
    <editors:SfColorPalette.PaletteColors>
        <editors:ColorPaletteModel ShowColorShades="True"/>
    </editors:SfColorPalette.PaletteColors>
    <editors:SfColorPalette.StandardColors>
        <editors:StandardPaletteModel ShowColorShades="True"/>
    </editors:SfColorPalette.StandardColors>
</editors:SfColorPalette>

{% endhighlight %}
{% highlight C# %}

colorPalette.PaletteColors.ShowColorShades = true;
colorPalette.StandardColors.ShowColorShades = true;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPalette with Theme and Standard Color Palettes](Getting-Started_images/winui-colorpalette-theme-and-standard-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Select a color from built-in theme colors

You can select a various theme colors by setting the value to the [ActivePalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ActivePalette) property. Based on the `ActivePalette` value, the respective base theme color items are displayed with its variants. The default value of `ActivePalette` property is `Office`.

![WinUI ColorPalette displays Various Theme Palettes](Working-with-SfColorPalette_images/winui-colorpalette-theme-palette.jpg)

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ActivePalette="Yellow"
                        Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.ActivePalette = ColorPaletteNames.Yellow;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPalette with Yellow Theme Color](Working-with-SfColorPalette_images/winui-colorpalette-theme-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Add your own colors in the Theme and Standard color palette

If you want to add own custom colors in base Theme Colors and Standard Colors palette, add the colors into the `PaletteColors.Colors` and `StandardColors.Colors` collections. The variant colors will be automatically created for the own Theme and Standard Colors.

{% tabs %}
{% highlight XAML %}

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

    <editors:SfColorPalette.StandardColors>
        <editors:StandardPaletteModel ShowColors="True" 
                                      ShowColorShades="True"
                                      Header="Custom Standard Colors" >
            <editors:StandardPaletteModel.Colors>
                <editors:ColorCollection>
                    <editors:ColorModel Color = "Blue" Tooltip = "Custom Blue" />
                    <editors:ColorModel Color = "Orchid" Tooltip = "Custom Orchid" />
                    <editors:ColorModel Color = "Gray" Tooltip = "Custom Gray" />
                    <editors:ColorModel Color = "Gold" Tooltip = "Custom Gold" />
                    <editors:ColorModel Color = "SandyBrown" Tooltip = "Custom SandyBrown" />
                    <editors:ColorModel Color = "Pink" Tooltip = "Custom Pink" />
                    <editors:ColorModel Color = "Violet" Tooltip = "Custom Violet" />
                    <editors:ColorModel Color = "Yellow" Tooltip = "Custom Yellow" />
                    <editors:ColorModel Color = "Orange" Tooltip = "Custom Orange" />
                    <editors:ColorModel Color = "Red" Tooltip = "Custom Red" />
                </editors:ColorCollection>
            </editors:StandardPaletteModel.Colors>                        
        </editors:StandardPaletteModel>
    </editors:SfColorPalette.StandardColors>    
</editors:SfColorPalette>

{% endhighlight %}
{% highlight c# %}

colorPalette.PaletteColors.Header = "Custom Theme Colors";
colorPalette.PaletteColors.ShowColors = true;
colorPalette.PaletteColors.ShowColorShades = true;

colorPalette.StandardColors.Header = "Custom Standard Colors";
colorPalette.StandardColors.ShowColors = true;
colorPalette.StandardColors.ShowColorShades = true;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPalette with Custom Colors](Working-with-SfColorPalette_images/winui-colorpalette-custom-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/Custom-Colors)

## Choosing a color from MoreColor dialog

If you want to choose a color that is not available in palette, click the more color button and select the color from color spectrum and click the `Ok` button. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ShowMoreColorsButton="true"
                        Name="colorPalette"/>

{% endhighlight %}
{% highlight C# %}

colorPalette.ShowMoreColorsButton = true;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPalette with More Color Window](Getting-Started_images/winui-colorpalette-more-color-window.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Recently used colors

 If you want to choose a color brush which are recently selected from the `More Colors` dialog, use the `Recent Colors` panel. You can get the recently used color list from the [RecentColors](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_RecentColors) collection.

N> Colors selected from theme and standard colors will not be added in recent colors.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette Name="colorPalette"/>

{% endhighlight %}
{% highlight C# %}


//Getting the recently used color list
var recentColors = colorPalette.RecentColors;

{% endhighlight %}
{% endtabs %}

![WinUI ColorPalette with Recent Color Items](Getting-Started_images/winui-colorpalette-recent-colors.png)

## Select transparent color 

If you want to select the `Transparent` color, click the `No Color` button. You can display the
 `No color` button only by setting the [ShowNoColorButton](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_ShowNoColorButton) property value as `true`. The default value of `ShowNoColorButton` property is `false`. 

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette ShowNoColorButton="True"
                        Name="colorPalette"/>

{% endhighlight %}
{% highlight C# %}

colorPalette.ShowNoColorButton = true;

{% endhighlight %}
{% endtabs %}

![Selecting Transparent Color in WinUI ColorPalette](Working-with-SfColorPalette_images/winui-colorpalette-transparent-color.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpalette-examples/blob/master/Samples/ColorPalette_features)

## Selected color changed notification

You will be notified when selected color changed in `ColorPalette` by using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html#Syncfusion_UI_Xaml_Editors_SfColorPalette_SelectedBrushChanged) event. The `SelectedBrushChanged` event contains the old and newly selected color values in the [OldBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedBrushChangedEventArgs_OldBrush) and [NewBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedBrushChangedEventArgs_NewBrush) properties.

{% tabs %}
{% highlight xaml %}

<editors:SfColorPalette SelectedBrushChanged="ColorPalette_SelectedBrushChanged"
                        Name="colorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.SelectedBrushChanged += ColorPalette_SelectedBrushChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# %}

//Invoked when the selected color is changed
private void ColorPalette_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs e) {
    var oldBrush= e.OldBrush;
    var newBrush= e.NewBrush;
}

{% endhighlight %}
{% endtabs %}
