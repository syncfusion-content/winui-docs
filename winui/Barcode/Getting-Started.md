---
layout: post
title: Getting Started with WinUI Barcode control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Barcode(SfBarCode) control, its elements, and more.
platform: WinUI
control: Barcode
documentation: ug
---

# Getting Started with WinUI Barcode

This section provides a quick overview for getting started with the [WinUI Barcode](https://www.syncfusion.com/winui-controls/barcode) . Walk through the entire process of creating a real world of this control.

## Creating an application with WinUI Barcode

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Barcode.WinUI](https://www.nuget.org/packages/Syncfusion.Barcode.WinUI) NuGet. 
3. Import the control namespace `using Syncfusion.UI.Xaml.Barcode` in XAML or C# code.
4. Initialize the SfBarCode control.

{% tabs %}
{% highlight xaml %}

<Page x:Class="syncfusion.barcodedemos.winui.GettingStartedPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.Barcode"
      xmlns:local="using:syncfusion.barcodedemos.winui"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">
    <Grid>
        <syncfusion:SfBarcode x:Name="barcode" Value="48625310">
            <syncfusion:SfBarcode.Symbology>
                <syncfusion:CodabarBarcode />
            </syncfusion:SfBarcode.Symbology>
        </syncfusion:SfBarcode>
    </Grid>
</Page>

{% endhighlight %}

{% highlight C# %} 

using Microsoft.UI.Xaml.Controls;
using Syncfusion.UI.Xaml.Barcode;

public sealed partial class GettingStartedPage : Page
{
    /// <summary>
    /// Interaction logic for GettingStartedPage.xaml
    /// </summary>
    public GettingStartedPage()
    {
        this.InitializeComponent();
        SfBarcode barcode = new SfBarcode();
        CodabarBarcode codabarBarcode = new CodabarBarcode();
        barcode.Symbology = codabarBarcode;
        barcode.Value = "48625310";
        Root_Grid.Children.Add(barcode);
    }
}

{% endhighlight %}
{% endtabs %} 

![WinUI Codabar Barcode](Getting_Started_Images/winui-codabar-barcode.png)

## Symbology

You can set the required symbology to the barcode based on input value by initializing the respective symbology instance using [Symbology](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_Symbology) property. In the following code snippet, the QR code has been set as the barcode symbology.

N> [Supported Symbology types in SfBarcode](https://help.syncfusion.com/winui/barcode/symbology-types)

{% tabs %}
{% highlight xaml %}

<Page xmlns:syncfusion="using:Syncfusion.UI.Xaml.Barcode">
    <Grid>
        <syncfusion:SfBarcode x:Name="barcode" Value="http://www.syncfusion.com">
            <syncfusion:SfBarcode.Symbology>
                <syncfusion:QRBarcode />
            </syncfusion:SfBarcode.Symbology>
        </syncfusion:SfBarcode>
    </Grid>
</Page>

{% endhighlight %}
{% endtabs %}

![WinUI QR Barcode](Getting_Started_Images/winui-QR-barcode.png)

## Text customization

The Barcode text can be customized by using below properties,

### Value

The text to be encoded can be set using the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_Value) property. By default, this original text will be displayed at the bottom of the bar code. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="48625310" Height="150">
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode with Value](Getting_Started_Images/winui-codabar-barcode.png)

### Text spacing

The space between barcode and text can be increased/decreased by using [TextSpacing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_TextSpacing) property. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" TextSpacing="7">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode with Text Spacing](Getting_Started_Images/winui-barcode-text-spacing.png)

### Display value

The visibility of the Barcode text can be changed using [ShowValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_ShowValue) property in Barcode. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" ShowValue="False">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode with Display Value](Getting_Started_Images/winui-barcode-display-value.png)

### HorizontalTextAlignment

The horizontal alignment of the Barcode text can be changed using [HorizontalTextAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_HorizontalTextAlignment) property in Barcode.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" HorizontalTextAlignment="Right">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Horizontal Text Alignment](Getting_Started_Images/winui-barcode-horizontal-text-alignment.png)

### VerticalTextAlignment

The vertical alignment of the Barcode text can be changed using [VerticalTextAlignment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_VerticalTextAlignment) property in Barcode.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" VerticalTextAlignment="Top">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Vertical Text Alignment](Getting_Started_Images/winui-barcode-vertical-text-alignment.png)

## Customization

The Barcode can be customized using below properties,

### Background
The Barcode background can be changed using [Background](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.control.background?view=netcore-3.1#System_Windows_Controls_Control_Background) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Background="Orange" Value="1010111011" Height="150" Width="250">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %} 

### Foreground
The Barcode foreground can be changed using [Foreground](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.control.foreground?view=netcore-3.1#System_Windows_Controls_Control_Foreground) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Foreground="White" Value="1010111011" Height="150" Width="250">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %} 

![WinUI Barcode Customization](Customization_Images/winui-barcode-customization.png)

### Module
The width ratio of the wide and narrow bars can be changed using [Module](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_Module) property. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Module="1" Value="48625310" ShowValue="False" Height="150">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Module](Customization_Images/winui-barcode-module.png)

### AutoModule
The size of [QRBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html) and [DataMatrixBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html) can be changed using [AutoModule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_AutoModule) Property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Width="400" Height="400" AutoModule="True" ShowValue="False" Value="QRBarcode">
    <syncfusion:SfBarcode.Symbology>   
        <syncfusion:QRBarcode />   
    </syncfusion:SfBarcode.Symbology>   
</syncfusion:SfBarcode>                      

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Auto Module](Customization_Images/winui-barcode-auto-module.png)

### Rotation Angle
The Barcode can be rotated in different angles by using [RotationAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_RotationAngle) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" RotationAngle="Angle90" Value="1010111011" Height="150" Width="250">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Rotation Angle](Customization_Images/winui-barcode-rotation-angle.png)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-barcode-examples)
