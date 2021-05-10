---
layout: post
title: Customization in WinUI Barcode control | Syncfusion
description: Learn here all about Customization feature in Syncfusion WinUI Barcode control with more background, foreground, Module custom support etc.
platform: WinUI
control: Barcode
documentation: ug
---

# Customization in WinUI Barcode

## Background
The Barcode background color can be changed using [Background](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.control.background?view=netcore-3.1#System_Windows_Controls_Control_Background) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Background="Orange" Value="1010111011" Height="150" Width="250">  
    <syncfusion:SfBarcode.Symbology>  
        <syncfusion:CodabarBarcode />  
    </syncfusion:SfBarcode.Symbology>  
</syncfusion:SfBarcode>

{% endhighlight %}
{% endtabs %} 

## Foreground
The Barcode foreground color can be changed using [Foreground](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.control.foreground?view=netcore-3.1#System_Windows_Controls_Control_Foreground) property.

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

N> In order for a barcode symbol to be recognized by a scanner, there must be an adequate contrast between the dark bars and the light spaces and not all the barcode scanners have support for colored barcodes.

## Module
The width ratio of the wide and narrow bars can be customized using [Module](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_Module) property. 

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

## AutoModule
The [QRBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html) and [DataMatrixBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html) can be rendered based on the available control size if [AutoModule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_AutoModule) is set to **True**.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Width="400" Height="400"
AutoModule="True" ShowValue="False" Value="QRBarcode">
    <syncfusion:SfBarcode.Symbology>   
        <syncfusion:QRBarcode />   
    </syncfusion:SfBarcode.Symbology>   
</syncfusion:SfBarcode>                      

{% endhighlight %}
{% endtabs %}

![WinUI Barcode Auto Module](Customization_Images/winui-barcode-auto-module.png)

### Rotation Angle
The [Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html) rotation can be changes by using [RotationAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_RotationAngle) property. The different angles can be set to [Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html) using [BarcodeRotation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html) enum values. 

The [BarcodeRotation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html) enumeration has following four angles,

<table>
<tr>
<th>
BarcodeRotation
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
{{'[Angle 0](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html#Syncfusion_UI_Xaml_Barcode_BarcodeRotation_Angle0)'| markdownify }}
</td>
<td>
Barcode can be rotated by 0 degree.
</td>
</tr>
<tr>
<td>
{{'[Angle 90](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html#Syncfusion_UI_Xaml_Barcode_BarcodeRotation_Angle90)'| markdownify }}
</td>
<td>
Barcode can be rotated by 90 degree.
</td>
</tr>
<tr>
<td>
{{'[Angle 180](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html#Syncfusion_UI_Xaml_Barcode_BarcodeRotation_Angle180)'| markdownify }}
</td>
<td>
Barcode can be rotated by 180 degree.
</td>
</tr>
<tr>
<td>
{{'[Angle 270](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.BarcodeRotation.html#Syncfusion_UI_Xaml_Barcode_BarcodeRotation_Angle270)'| markdownify }}
</td>
<td>
Barcode can be rotated by 270 degree.
</td>
</tr>
</table>

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
