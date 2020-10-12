---
layout: post
title: Getting started with WinUI SfDropDownColorPalette control | Syncfusion
description: Learn here about getting started with Syncfusion WinUI SfDropDownColorPalette control and more details about the control features.
platform: WinUI
control: SfDropDownColorPalette
documentation: ug
---

# Getting started with WinUI DropDown ColorPalette

This section explains the steps required to add the [DropDownColorPalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.DropDownColorPalette.html) control and its color options such as theme, standard and more custom colors. This section covers only basic features needed to get started with Syncfusion `DropDownColorPalette` control.

## Control Structure

![Dropdown ColorPalette control structure](Getting-Started_images/Control_Structure_GS.png)

* The Selected Color represents the color that you select.

* The Automatic Color represents the color, which can be set by you as default color.

* The ToolTip with Color Details represents the toolTip, when the mouse hovers on the Color.

* The Standard Colors stores the standard colors like `Red`, `Green`, `Blue` and so on.

* The Recently User Colors stores the colors that are recently selected.

* The More Colors Option provides wide range of color in addition to colors in the palette.

* The Theme Variant Colors represents the Theme colors with variants.

### More Color Dialog

![Dropdown ColorPalette more color dialog structure](Getting-Started_images/MoreColorControl_Structure_GS.jpg)

## Creating an application with WinUI DropDownColorPalette

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.

2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 

3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.

4. Initialize the `SfDropDownColorPalette` control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid x:Name="grid">
    <syncfusion:SfDropDownColorPalette x:Name="sfDropDownColorPalette" />
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
            SfDropDownColorPalette sfDropDownColorPalette = new SfDropDownColorPalette();
            grid.Children.Add(sfDropDownColorPalette);
        }
    }
}
{% endhighlight %}
{% endtabs %}

![ColorPalette added in the winui application](Getting-Started_images/controladded.png)

## Accessing a Color programmatically

You can set or change the selected color of the `DropDownColorPalette` programmatically by setting the value to [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownColorPalette.html#Syncfusion_UI_Xaml_Editors_SfDropDownColorPalette_SelectedBrush) property. You can also get the selected color by using the `SelectedBrush` property. The default value of `SelectedBrush` property is `Black`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette SelectedBrush="Yellow"
                                   Name="sfDropDownColorPalette" />

{% endhighlight %}
{% highlight C# %}

colorPalette.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Dropdown ColorPalette programmatically picked the yellow color](Getting-Started_images/Colorprogrammatically.png)

Here, `Yellow` color is selected color in the `DropDownColorPalette`.

## Select Color from dropdown Color Palette

You can select a different colors from `Theme Colors` and `Standard Colors` panels.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette =  new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown ColorPalette control with theme and standard color items](Getting-Started_images/ThemeColorPanel.png)

## Select Automatic Color

By default automatic color brush is selected color brush. If you changed the selected color brush, then you can easily make the automatic color brush as selected color brush by clicking the automatic color panel. The automatic color brush value is `Black`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette =  new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown ColorPalette control with theme and standard color items](Getting-Started_images/automatic_color.png)

## Choosing a Color from MoreColor dialog

If you want to choose a color that is not available in theme and standard palette, click the more color button and select the color from color spectrum and click the `Ok` button. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette = new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown ColorPalette with more color dialog](Getting-Started_images/MoreColorWindow.gif)

## Recently used Color items

 If you want to choose a color brush which are recently selected from the `More Colors` dialog, use the `Recent Colors` panel. 

N> Colors selected from theme and standard colors will not be added in recent colors.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPalette sfDropDownColorPalette = new SfDropDownColorPalette();

{% endhighlight %}
{% endtabs %}

![Dropdown ColorPalette with recently used color items](Getting-Started_images/Recentcolors.png)

## Color Palette as a command button

By default, `DropDownColorPalette` acts like a dropdown. It opening a color palette when clicking anywhere on the header. By setting the [DropDownMode](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownMode) property value as `Split`, it acts like a button and dropdown as explained below.

1. When clicking on the dropdown arrow button, It acts like a dropdown.

2. When you click on the header area, it acts like a button and [Command](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownColorPalette.html#Syncfusion_UI_Xaml_Editors_SfDropDownColorPalette_Command) will be triggered. Using the `Command`, you can do some action like applying the selected color anywhere you want.

For example, if you want to apply a last selected color as a background to a TextEditor’s selected text. You can direct click the button instead of opening the dropdown and selecting an already selected color again.

{% tabs %}
{% highlight C# %}

public sealed partial class MainPage : Page
{
    private ICommand selectionChangedCommand;
    public ICommand SelectionChangedCommand {
        get {
            return selectionChangedCommand;
        }
    }
    public void SelectionChangedMethod(object param) {
        richTextBox.Document.Selection.CharacterFormat.BackgroundColor
            = (sfDropDownColorPalette.SelectedBrush as SolidColorBrush).Color;

    }
    public MainPage() {
        this.InitializeComponent();
        selectionChangedCommand = new DelegateCommand<object>(SelectionChangedMethod);
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<StackPanel Orientation="Vertical">

    <RichEditBox  Name="richTextBox" Margin="20"/>
   
    <syncfusion:SfDropDownColorPalette DropDownMode="Split"
                                       Command="{x:Bind SelectionChangedCommand}"
                                       Name="sfDropDownColorPalette" />
</StackPanel>

{% endhighlight %}
{% endtabs %}

![Dropdown color palette recent color selected in split mode](Getting-Started_images/Splitbutton.gif)

## Custom Color Palette

You can embed the [ColorPalette](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPalette.html) control inside the drop down color palette by using the [DropDownContentTemplate](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownContentTemplate) property. You can change the theme and standard colors and customize its panels, etc, based on your requirements.

N> The `DataContext` of `DropDownContentTemplate` property is [SfDropDownColorPalette.DropDownContent](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownContent).

N> You can refer the [ColorPalette](https://help.syncfusion.com/winui/color-palette/overview) documentation page to know more about all customization available for the `ColorPalette` control.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette Name="sfDropDownColorPalette">
    <syncfusion:SfDropDownColorPalette.DropDownContentTemplate>
        <DataTemplate>
            <syncfusion:SfColorPalette ShowMoreColorsButton="False"  Width="250" >
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

                <syncfusion:SfColorPalette.StandardColors>
                    <syncfusion:StandardPaletteModel ShowColors="True" 
                                 ShowColorShades="True"
                                 Header="Custom Standard Colors" >
                        <syncfusion:StandardPaletteModel.Colors>
                            <syncfusion:ColorCollection>
                                <syncfusion:ColorModel Color = "Blue" Tooltip = "Custom Blue" />
                                <syncfusion:ColorModel Color = "Orchid" Tooltip = "Custom Orchid" />
                                <syncfusion:ColorModel Color = "Gray" Tooltip = "Custom Gray" />
                                <syncfusion:ColorModel Color = "Gold" Tooltip = "Custom Gold" />
                                <syncfusion:ColorModel Color = "SandyBrown" Tooltip = "Custom SandyBrown" />
                                <syncfusion:ColorModel Color = "Pink" Tooltip = "Custom Pink" />
                                <syncfusion:ColorModel Color = "Violet" Tooltip = "Custom Violet" />
                                <syncfusion:ColorModel Color = "Yellow" Tooltip = "Custom Yellow" />
                                <syncfusion:ColorModel Color = "Orange" Tooltip = "Custom Orange" />
                                <syncfusion:ColorModel Color = "Red" Tooltip = "Custom Red" />
                            </syncfusion:ColorCollection>
                        </syncfusion:StandardPaletteModel.Colors>
                    </syncfusion:StandardPaletteModel>
                </syncfusion:SfColorPalette.StandardColors>
            </syncfusion:SfColorPalette>
        </DataTemplate>
    </syncfusion:SfDropDownColorPalette.DropDownContentTemplate>
</syncfusion:SfDropDownColorPalette>

{% endhighlight %}
{% endtabs %}

![Color palette embedded inside the dropdown color palette](Getting-Started_images/custom_colorpalette.png)

## Custom UI of Dropdown Header

You can customize the appearance of the `DropDownColorPalette` header in both split mode and dropdown mode. You can customize the selected color button using [ContentTemplate](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ContentTemplate) property and customize the dropdown button by using the [DropDownButtonTemplate](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownButtonTemplate) property.

N> The `DataContext` of `DropDownButtonTemplate` property and `ContentTemplate` property is `SfDropDownColorPalette`.

N> The `DropDownButtonTemplate` is effective only on when drop down mode is split mode.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette DropDownMode="Split"                   
                                   Name="sfDropDownColorPalette">
    
    <!--Custom UI for DropDown button-->
    <syncfusion:SfDropDownColorPalette.DropDownButtonTemplate>
        <DataTemplate>
            <Grid>
                <StackPanel Width="30">
                    <Grid VerticalAlignment="Center"
                          HorizontalAlignment="Center">
                        <Path Fill="Black" 
                              Data="M 0 0 L 5 5 L 10 0 Z"/>
                    </Grid>
                </StackPanel>
            </Grid>
        </DataTemplate>
    </syncfusion:SfDropDownColorPalette.DropDownButtonTemplate>

    <!--Custom UI for Selected color button-->
    <syncfusion:SfDropDownColorPalette.ContentTemplate>
        <DataTemplate>
            <StackPanel Height="30" 
                        Orientation="Vertical">
                <Path Data="M19.551687,9.4412649L5.7859255,23.232995 3.1009826,28.505029 8.8409869,26.226037 22.573929,12.468039 22.138519,12.03162z M27.786037,2.0999956C27.232677,2.0999961,26.679191,2.3019958,26.275703,2.7059948L22.546806,6.4419879 20.686857,4.5799915C20.483862,4.3769917 20.213869,4.264992 19.926878,4.2649922 19.638885,4.264992 19.368892,4.3769917 19.163898,4.5809914 18.74391,5.0019907 18.74391,5.6889894 19.165899,6.1109889L19.552171,6.4977872 19.552927,6.4970304 22.776479,9.726485 25.902713,12.856976C26.105709,13.060976 26.375702,13.173975 26.662693,13.173975 26.949686,13.173975 27.221677,13.060976 27.424673,12.856976 27.845661,12.435977 27.845661,11.749978 27.424673,11.328979L27.424673,11.327979 25.567722,9.4689825 29.295622,5.7349892C30.129598,4.9009908 30.129598,3.5419934 29.295622,2.7059948 28.892631,2.3019958 28.339397,2.0999961 27.786037,2.0999956z M27.785661,0C28.911632,0 29.970602,0.4399991 30.76758,1.2379975 32.409534,2.8819947 32.409534,5.5589896 30.76758,7.2049866L28.506643,9.4689825 28.896631,9.8599815C30.126598,11.09098 30.126598,13.095976 28.896631,14.327973 28.299648,14.924973 27.50667,15.253972 26.662693,15.253972L26.661693,15.253972C25.818716,15.253972,25.025737,14.924973,24.429754,14.325974L24.044054,13.939747 10.008959,28.001 1.5649682,31.352014C1.4289816,31.40603 1.2868914,31.432031 1.1458999,31.432031 0.82888244,31.432031 0.51687,31.300988 0.29689856,31.059045 -0.021095165,30.709008 -0.091041619,30.191003 0.12294829,29.770043L4.197909,21.881004 18.082576,7.9701535 17.692939,7.579986C16.464973,6.3479882 16.464973,4.3429918 17.692939,3.1109939 18.888906,1.9149966 20.965849,1.9179964 22.159816,3.1099939L22.546806,3.4989934 24.803743,1.2379975C25.600723,0.4399991,26.659692,0,27.785661,0z" 
                      Stretch="Uniform"
                      Fill="Black" 
                      Width="20" Height="20" 
                      RenderTransformOrigin="0.5,0.5"/>
                <Border Margin="5" 
                        Background="{Binding}"
                        Grid.Row="1"
                        Width="25"
                        Height="7">
                </Border>
            </StackPanel>
        </DataTemplate>
    </syncfusion:SfDropDownColorPalette.ContentTemplate> 
</syncfusion:SfDropDownColorPalette>

{% endhighlight %}
{% endtabs %}

![Displaying custom UI of drop down header in split mode](Getting-Started_images/customUI.png)

## Change Dropdown alignment

You can change alignment of the drop down palette as full, center, left, right, top or bottom with edge of the dropdown header by using the [DropDownPlacement](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is `Auto`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette DropDownPlacement="BottomEdgeAlignedRight" 
                                   Name="sfDropDownColorPalette"/>

{% endhighlight %}
{% highlight C# %}

sfDropDownColorPalette.DropDownPlacement = FlyoutPlacementMode.BottomEdgeAlignedRight;;

{% endhighlight %}
{% endtabs %}

![Dropdown color palette placement changed as BottomEdgeAlignedRight](Getting-Started_images/DropDownPlacement.png)

## Selected Color brush changed notification

The selected color brush changed in `DropDownColorPalette` can be examined using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownColorPalette.html#Syncfusion_UI_Xaml_Editors_SfDropDownColorPalette_SelectedBrushChanged) event. The `SelectedBrushChanged` event contains the old and newly selected color values in the `OldBrush`, `NewBrush` properties.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette SelectedBrushChanged="sfDropDownColorPalette_SelectedBrushChanged"
                                   Name="sfDropDownColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfDropDownColorPalette.SelectedBrushChanged += sfDropDownColorPalette_SelectedBrushChanged;

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight C# %}

//Invoked when the selected color is changed
private void sfDropDownColorPalette_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs e) {
    var oldBrush= e.OldBrush;
    var newBrush= e.NewBrush;
}

{% endhighlight %}
{% endtabs %}

## Dropdown Color Palette Open and Close notification

You can notified when drop-down opened and closed by using the `DropDownOpened` and `DropDownClosed` events.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDropDownColorPalette DropDownOpened="sfDropDownColorPalette_DropDownOpened"
                                   DropDownClosed= "sfDropDownColorPalette_DropDownClosed" 
                                   Name="sfDropDownColorPalette" />

{% endhighlight %}
{% highlight C# %}

sfDropDownColorPalette.DropDownOpened += sfDropDownColorPalette_DropDownOpened;
sfDropDownColorPalette.DropDownClosed += sfDropDownColorPalette_DropDownClosed;

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight C# %}

//Invoked when the drop down is opened
private void sfDropDownColorPalette_DropDownOpened(object sender, EventArgs e) {
}

//Invoked when the drop down is closed
private void sfDropDownColorPalette_DropDownClosed(object sender, EventArgs e) {
}

{% endhighlight %}
{% endtabs %}



