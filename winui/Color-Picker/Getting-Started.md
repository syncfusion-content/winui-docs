---
layout: post
title: Getting Started with WinUI SfColorPicker control | Syncfusion
description: This section describes about how to add the SfColorPicker control into WinUI application and its basic features.
platform: WinUI
control: SfColorPicker
documentation: ug
---

# Getting Started with WinUI ColorPicker (SfColorPicker)

This section describes how to create a [ColorPicker](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html) control in a WinUI application and overview of its basic functionalities.

## Structure of ColorPicker control

![Structure of WinUI ColorPicker control](Getting-Started_images/Structure.png)

## Creating an application with WinUI ColorPalette

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.

2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 

3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.

4. Initialize the `SfColorPicker` control.

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
    <Grid Name="grid">
        <!--Adding ColorPicker control -->
        <syncfusion:SfColorPicker Name="colorPicker"/>
    </Grid>
</Page>

{% endhighlight %}
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
            // Creating an instance of the ColorPicker control
            SfColorPicker colorPicker = new SfColorPicker();

            // Setting height and width to ColorPicker control
            colorPicker.Height = 300;
            colorPicker.Width = 300;

            grid.Children.Add(colorPicker);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![ColorPicker control added in the application](Getting-Started_images/ColorPicker_Added.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Select solid color brush

You can select the solid color brush programmatically by setting the solid color brush value to the [SelectedBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrush) property. You can also choose various solid color brush from different standard color models such as `RGB`, `HSV`, `HSL`, `CMYK` formats. The default value of `SelectedBrush` property is `Blue`.

{% tabs %}
{% highlight xaml %}

 <syncfusion:SfColorPicker x:Name="colorPicker"
                           SelectedBrush="Yellow"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.SelectedBrush = new SolidColorBrush(Colors.Yellow);

{% endhighlight %}
{% endtabs %}

![Solid color selected from ColorPicker](Getting-Started_images/select_Solidcolor.png)

You can select any solid color brush at runtime by clicking on the respective solid color brush area.

![Solid color brush selected at runtime](Getting-Started_images/Solidcolor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

### Switch between solid color channels

 You can select the color model by setting the required color brush model to the [ColorChannelOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_ColorChannelOptions) property or select it from the drop down options. The default value of `ColorChannelOptions` property is `RGB`.

{% tabs %}
{% highlight xaml %}

 <syncfusion:SfColorPicker x:Name="colorPicker"
                           ColorChannelOptions="HSV"/>

{% endhighlight %}
{% highlight c# %}

SfColorPicker colorPicker = new SfColorPicker();
colorPicker.ColorChannelOptions = ColorChannelOptions.HSV;

{% endhighlight %}
{% endtabs %}

![Different solid color models in ColorPicker](Getting-Started_images/RGB.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

### Change opacity of solid color brush

You can change opacity of the selected solid color brush by using the A-Alpha value editor or delicate slider in the `ColorPicker`. You can hide the A-Alpha slider by using the [AlphaInputOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_AlphaInputOptions) property value as `TextInput`. The default value of the `AlphaInputOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker AlphaInputOptions="TextInput"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.AlphaInputOptions = ColorInputOptions.TextInput;

{% endhighlight %}
{% endtabs %}

![Show opacity value editor](Getting-Started_images/AlphaInputOptions.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

### Hexadecimal solid color brush value editor

You can select a solid color brush by entering the hexadecimal color value to the hexadecimal value editor. You can also get the selected color hexadecimal value by using the hexadecimal value editor. You can hide the hexadecimal value editor by setting the [IsHexInputVisible](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_IsHexInputVisible) property value as `false`. The default value of `IsHexInputVisible` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker IsHexInputVisible="False"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.IsHexInputVisible = false;

{% endhighlight %}
{% endtabs %}

![Hide the hexadecimal value editor](Getting-Started_images/IsHexInputVisible.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectSolidColors)

## Select linear gradient color brush

Linear Gradient color brush can be selected by the multiple colors and their location along the gradient axis using the `GradientStop` objects and `StartPoint` and `EndPoint` properties. Based on the `StartPoint` and `EndPoint`, the selected color brush will be combined in linear manner.

{% tabs %}
{% highlight xaml %}

 <syncfusion:SfColorPicker x:Name="colorPicker">
    <syncfusion:SfColorPicker.SelectedBrush>
        <LinearGradientBrush StartPoint="0,0" EndPoint="1,1">
            <GradientStop Color="Yellow" Offset="0.0" />
            <GradientStop Color="Red" Offset="0.25" />
            <GradientStop Color="Blue" Offset="0.75" />
            <GradientStop Color="LimeGreen" Offset="1.0" />
        </LinearGradientBrush>
    </syncfusion:SfColorPicker.SelectedBrush>
</syncfusion:SfColorPicker>

{% endhighlight %}
{% highlight c# %}

//Creating the linear gradient brush
LinearGradientBrush linearGradient = new LinearGradientBrush();
linearGradient.StartPoint = new Point(0, 0);
linearGradient.EndPoint = new Point(1, 1);
linearGradient.GradientStops.Add(
    new GradientStop() { Color = Colors.Yellow, Offset = 0.0 });
linearGradient.GradientStops.Add(
    new GradientStop() { Color = Colors.Red, Offset = 0.25 });
linearGradient.GradientStops.Add(
    new GradientStop() { Color = Colors.Blue, Offset = 0.75 });
linearGradient.GradientStops.Add(
    new GradientStop() { Color = Colors.LimeGreen, Offset = 1.0 });

//Assigning a linear gradient brush to ColorPicker
colorPicker.SelectedBrush = linearGradient;

{% endhighlight %}
{% endtabs %}

![Assigning a Linear Gradient brush to ColorPicker](Getting-Started_images/ColorPicker_select-a-LinearGradient.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectLinearGradientColors)

You can directly select a required linear gradient color brush at runtime by setting the [BrushTypeOptions](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_BrushTypeOptions) property value as `LinearGradientBrush`. The default value of `BrushTypeOptions` property is `All`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="LinearGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.BrushTypeOptions = BrushTypeOptions.LinearGradientBrush;

{% endhighlight %}
{% endtabs %}

![Selecting a linear gradient color brush](Getting-Started_images/lineargradient.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Select radial gradient color brush

Radial Gradient color brush is similar to Linear Gradient color brush, except for the axis defined by the circle. Based on the `GradientOrigin`, `Center` and radius point values, the selected gradient color brush are combined in a circle manner.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfColorPicker x:Name="colorPicker">
    <syncfusion:SfColorPicker.SelectedBrush>
        <RadialGradientBrush GradientOrigin="0.5,0.5" 
                             Center="0.5,0.5"
                             RadiusX="0.5" RadiusY="0.5">
            <GradientStop Color="Yellow" Offset="0" />
            <GradientStop Color="Red" Offset="0.25" />
            <GradientStop Color="Blue" Offset="0.75" />
            <GradientStop Color="LimeGreen" Offset="1" />
        </RadialGradientBrush>
    </syncfusion:SfColorPicker.SelectedBrush>
</syncfusion:SfColorPicker>

{% endhighlight %}
{% highlight c# %}

//Creating a radial gradient brush
RadialGradientBrush radialGradient = new RadialGradientBrush();
radialGradient.GradientOrigin = new Point(0.5, 0.5);
radialGradient.Center = new Point(0.5, 0.5);
radialGradient.RadiusX = 0.5;
radialGradient.RadiusY = 0.5;
radialGradient.GradientStops.Add(
    new GradientStop() {Color=Colors.Yellow, Offset= 0.0 });
radialGradient.GradientStops.Add(
    new GradientStop() {Color=Colors.Red, Offset = 0.25 });
radialGradient.GradientStops.Add(
    new GradientStop() {Color=Colors.Blue, Offset = 0.75 });
radialGradient.GradientStops.Add(
    new GradientStop() {Color=Colors.LimeGreen, Offset = 1.0 });

//Assigning a radial gradient brush to ColorPicker
colorPicker.SelectedBrush = radialGradient;

{% endhighlight %}
{% endtabs %}

![Assigning a Raidial Gradient brush to ColorPicker](Getting-Started_images/ColorPicker_select-a-RadialGradient.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectRadialGradientColors)

You can directly select a required radial gradient color brush at runtime by setting the `BrushTypeOptions` property value as `RadialGradientBrush`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="RadialGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.BrushTypeOptions = BrushTypeOptions.RadialGradientBrush;

{% endhighlight %}
{% endtabs %}

![Selecting a radial gradient color brush](Getting-Started_images/radialgradient.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Switch between solid, linear and gradient brush mode

You can allow the user to choose either `Solid`, `Linear` or `Radial` gradient brush or any combination of brush mode by using the `BrushTypeOptions` property. 

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker BrushTypeOptions="SolidColorBrush,RadialGradientBrush"
                          Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.BrushTypeOptions = BrushTypeOptions.SolidColorBrush | BrushTypeOptions.RadialGradientBrush;

{% endhighlight %}
{% endtabs %}

![Allow only the solid and radial gradient brush mode](Getting-Started_images/BrushTypeOptions.jpg)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

You can change the color selection mode directly at runtime by clicking on the corresponding `Solid`, `Linear` or `Radial` gradient brush mode drop down options which is placed in the top of the `ColorPicker` control.

![Switch between solid, linear and gradient brush mode](Getting-Started_images/ColorPicker_Switch_brushes.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-colorpicker-examples/tree/master/Samples/SelectGradientColors)

## Selected brush changed notification

You will be notified when selected brush changed in `ColorPicker` by using [SelectedBrushChanged](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SfColorPicker.html#Syncfusion_UI_Xaml_Editors_SfColorPicker_SelectedBrushChanged) events. You can get the old and newly selected brush by using the [OldBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) and [NewBrush](https://help.syncfusion.com/cr/winUI/Syncfusion.UI.Xaml.Editors.SelectedBrushChangedEventArgs.html) properties.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfColorPicker SelectedBrushChanged="ColorPicker_SelectedBrushChanged"
                      Name="colorPicker">

{% endhighlight %}
{% highlight C# %}

colorPicker.SelectedBrushChanged += ColorPicker_SelectedBrushChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows,

{% tabs %}
{% highlight C# %}

private void ColorPicker_SelectedBrushChanged(object sender, SelectedBrushChangedEventArgs args) {
    var old_selectedBrush = args.OldBrush;
    var new_selectedBrush = args.NewBrush;
}

{% endhighlight %}
{% endtabs %}
