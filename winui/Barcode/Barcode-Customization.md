---
layout: post
title: Customization | Barcode | WinUI | Syncfusion
description: Shows how the Barcode can be customized in Barcode control
platform: WinUI
control: Barcode
documentation: ug
---

# Customization

## Barcode Customization

The color of the Barcode can be customized by using the properties of `Background` and `Foreground` in `SfBarcode` control.

The Background represents the Color of the dark bar (Black color by default) and the Foreground represents the color of the gap between two adjacent black bars (White color by default).

{% highlight xaml %}

    <syncfusion:SfBarcode x:Name="barcode" Background="Orange" Foreground="White" Value="48625310" Height="150">
        <syncfusion:SfBarcode.Symbology>
           <syncfusion:CodabarBarcode />
         </syncfusion:SfBarcode.Symbology>
    </syncfusion:SfBarcode>
    
{% endhighlight %}

![Barcode_Customization](Symbology_Images/Barcode_Customization.png)


## Module

 The width ratio of the wide and narrow bars can be customized using `Module` property. The following code snippet explains that how the `Module` property is used,

{% highlight xaml %}

    <syncfusion:SfBarcode x:Name="barcode" Module="1" Value="48625310" Height="150">
        <syncfusion:SfBarcode.Symbology>
           <syncfusion:CodabarBarcode />
         </syncfusion:SfBarcode.Symbology>
    </syncfusion:SfBarcode>
   
{% endhighlight %}

![Module](Symbology_Images/BarWidth.png)
