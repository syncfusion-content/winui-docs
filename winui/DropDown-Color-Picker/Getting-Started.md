---
layout: post
title: Getting Started with WinUI DropDown Color Picker control | Syncfusion
description: Learn here about getting started with Syncfusion WinUI DropDown Color Picker(SfColorPicker) control and more.
platform: WinUI
control: SfDropDownColorPicker
documentation: ug
---

# Getting Started with WinUI DropDown Color Picker

This section explains the steps required to add the [WinUI DropDown Color Picker](https://www.syncfusion.com/winui-controls/dropdown-color-picker) control and its color options such as gradient colors and RGB, HSV , HSL, CMYK and Hexadecimal solid color editors.

## Control Structure

![Structure of WinUI DropDown ColorPicker control](Getting-Started_images/Structure1.jpg)

## Creating an application with WinUI DropDown Color Picker

In this walkthrough, you will create a WinUI application that contains the `DropDown Color Picker` control.

## Adding control manually in XAML

To add `DropDown Color Picker` control manually in XAML , follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Download and refer the following NuGet in the project.
    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfDropDownColorPicker` control.

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
    <Grid x:Name="grid">
    <editors:SfDropDownColorPicker x:Name="sfDropDownColorPicker" />
    </Grid>
</Page>

{% endhighlight %}
{% endtabs %}

## Adding control manually in C#

To add the `DropDown Color Picker` control manually in C#, follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Download and refer the following NuGet in the project.
    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)
3. Import the `DropDown Color Picker` namespace `Syncfusion.UI.Xaml.Editors` in C# page.
4. Initialize the `SfDropDownColorPicker` control.

{% tabs %}
{% highlight C# %}

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
            SfDropDownColorPicker sfDropDownColorPicker = new SfDropDownColorPicker();
            grid.Children.Add(sfDropDownColorPicker);
        }
    }
}
{% endhighlight %}
{% endtabs %}

![DropDown ColorPicker added in the winui application](Getting-Started_images/ColorPicker_Added.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Select solid brush programmatically

You can select the solid color brush programmatically by setting the solid color brush value to the [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownColorPicker.html#Syncfusion_UI_Xaml_Editors_SfDropDownColorPicker_SelectedBrush) property. The default value of `SelectedBrush` property is `Blue`.

{% tabs %}
{% highlight xaml %}

 <editors:SfDropDownColorPicker x:Name="sfDropDownColorPicker"
                                SelectedBrush="Yellow"/>

{% endhighlight %}
{% highlight c# %}

SfDropDownColorPicker sfDropDownColorPicker = new SfDropDownColorPicker();
colorPicker.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Solid color programmatically selected from DropDown ColorPicker](Getting-Started_images/select_Solidcolor.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Select solid brush interactively

You can select various solid color brush at runtime by selecting the color brush from the color spectrum and clicking `OK` button.

{% tabs %}
{% highlight xaml %}

<editors:SfDropDownColorPicker Name="sfDropDownColorPicker"/>

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPicker sfDropDownColorPicker =  new SfDropDownColorPicker();

{% endhighlight %}
{% endtabs %}

![Selecting a color brush from Dropdown ColorPicker at runtime](Getting-Started_images/colorselecting.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Switch between solid color channels

You can switch between required RGB, HSV, HSL or CMYK color brush channels by choosing it from the `Combobox` options.

{% tabs %}
{% highlight xaml %}

 <editors:SfDropDownColorPicker x:Name="sfDropDownColorPicker"/>

{% endhighlight %}
{% highlight c# %}

SfDropDownColorPicker sfDropDownColorPicker = new SfDropDownColorPicker();

{% endhighlight %}
{% endtabs %}

![Switch between different solid color channels in Dropdown ColorPicker](Getting-Started_images/RGBSwitch.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Change opacity of solid brush

You can change opacity of the selected solid color brush by using the A-Alpha value editor or delicate slider in the `DropDown Color Picker`.

{% tabs %}
{% highlight XAML %}

<editors:SfDropDownColorPicker Name="SfDropDownColorPicker">

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPicker sfDropDownColorPicker  new SfDropDownColorPicker();

{% endhighlight %}
{% endtabs %}

![Opacity value editor and slider in DropDown ColorPicker](Getting-Started_images/AlphaInputOptions.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Hexadecimal editor

You can select a solid color brush by entering the hexadecimal color value to the hexadecimal value editor. You can also get the selected color hexadecimal value by using the hexadecimal value editor.

{% tabs %}
{% highlight XAML %}

<editors:SfDropDownColorPicker Name="sfDropDownColorPicker">

{% endhighlight %}
{% highlight C# %}

SfDropDownColorPicker sfDropDownColorPicker  new SfDropDownColorPicker();

{% endhighlight %}
{% endtabs %}

![Selecting a color from hexadecimal value editor](Getting-Started_images/IsHexInputVisible.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/DropDown_ColorPicker)

## Selected brush changed notification

The selected brush changed in `DropDown Color Picker` can be examined by using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfDropDownColorPicker.html#Syncfusion_UI_Xaml_Editors_SfDropDownColorPicker_SelectedBrushChanged) events. You can get the old and newly selected brush by using the [OldBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) and [NewBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) properties.

{% tabs %}
{% highlight XAML %}

<editors:SfDropDownColorPicker SelectedBrushChanged="SfDropDownColorPicker_SelectedBrushChanged"
                               Name="sfDropDownColorPicker">

{% endhighlight %}
{% highlight C# %}

sfDropDownColorPicker.SelectedBrushChanged += SfDropDownColorPicker_SelectedBrushChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# %}

private void SfDropDownColorPicker_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs args) {
    var old_selectedBrush = args.OldBrush;
    var new_selectedBrush = args.NewBrush;
}

{% endhighlight %}
{% endtabs %}
