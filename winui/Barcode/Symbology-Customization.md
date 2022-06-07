---
layout: post
title: Symbology Customization in WinUI Barcode control | Syncfusion
description: Learn here all about the Symbology Customization feature in Syncfusion WinUI Barcode control with one, two-dimensional support, and more.
platform: WinUI
control: Barcode
documentation: ug
---

# Symbology Customization in WinUI Barcode
Each Barcode symbology can be associated with optional settings that may affect the specific bar code. 

## One-Dimensional Barcode settings

### EnableCheckSum
The [EnableCheckSum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.UnidimensionalBarcode.html#Syncfusion_UI_Xaml_Barcode_UnidimensionalBarcode_EnableCheckSum) property enables the redundancy check using a check digit, the decimal equivalent of a binary parity bit. It consists of a single digit, computed from the other digits in the message.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:CodabarBarcode EnableCheckSum="True" ShowCheckSum="False" />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}
 
### ShowCheckSum
The check digit can be shown in the Barcode or kept hidden by using the [ShowCheckSum](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.UnidimensionalBarcode.html#Syncfusion_UI_Xaml_Barcode_UnidimensionalBarcode_ShowCheckSum) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:CodabarBarcode EnableCheckSum="True" ShowCheckSum="True" />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

### EncodeStartStopSymbols
The [EncodeStartStopSymbols](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.UnidimensionalBarcode.html#Syncfusion_UI_Xaml_Barcode_UnidimensionalBarcode_EncodeStartStopSymbols) property adds Start and Stop symbols to signal a bar code reader that a bar code has been scanned.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:CodabarBarcode EncodeStartStopSymbols="True" />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

## Two-Dimensional Barcode settings

### DataMatrix Barcode settings
The [DataMatrix](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html) Barcode can be customized using the [Encoding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html#Syncfusion_UI_Xaml_Barcode_DataMatrixBarcode_Encoding) and [MatrixSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html#Syncfusion_UI_Xaml_Barcode_DataMatrixBarcode_MatrixSize) properties.

#### Encoding
The encoding format of the DataMatrix Barcode can be modified using the [Encoding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html#Syncfusion_UI_Xaml_Barcode_DataMatrixBarcode_Encoding) property to decide the Barcode value to be set.

The [DataMatrixEncoding](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixEncoding.html) enumeration has the following four encoding:

* ASCII         - Supports character values between U+0000 and U+007F.
* ASCIINumeric  - Supports only single digit numeric characters [0-9].
* Auto          - Supports symbols and all kind of characters [^A-Za-z0-9].
* Base256       - Supports all characters and symbols [^A-Za-z0-9].

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:DataMatrixBarcode Encoding="ASCIINumeric" />
</syncfusion:SfBarcode.Symbology>

{% endhighlight  %}
{% endtabs %}

#### MatrixSize
The [MatrixSize](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html#Syncfusion_UI_Xaml_Barcode_DataMatrixBarcode_MatrixSize) property allows user to specify the size of the Barcode from a set of predefined sizes available in the [DataMatrixSize]https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixSize.html) enumeration.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:DataMatrixBarcode MatrixSize="Size104x104" />
</syncfusion:SfBarcode.Symbology>

{% endhighlight  %}
{% endtabs %}

**Data Matrix Size Table**

<table>
<tr>
<th>
Data Matrix Size</th><th>
Description</th></tr>
<tr>
<td>
Auto</td><td>
Size is chosen based on the input data</td></tr>
<tr>
<td>
Size10x10</td><td>
Square matrix with 10 rows and 10 columns.</td></tr>
<tr>
<td>
Size12x12</td><td>
Square matrix with 12 rows and 12 columns.</td></tr>
<tr>
<td>
Size14x14</td><td>
Square matrix with 14 rows and 14 columns.</td></tr>
<tr>
<td>
Size16x16</td><td>
Square matrix with 16 rows and 16 columns.</td></tr>
<tr>
<td>
Size18x18</td><td>
Square matrix with 18 rows and 18 columns.</td></tr>
<tr>
<td>
Size20x20</td><td>
Square matrix with 20 rows and 20 columns.</td></tr>
<tr>
<td>
Size22x22</td><td>
Square matrix with 22 rows and 22 columns.</td></tr>
<tr>
<td>
Size24x24</td><td>
Square matrix with 24 rows and 24 columns.</td></tr>
<tr>
<td>
Size26x26</td><td>
Square matrix with 26 rows and 26 columns.</td></tr>
<tr>
<td>
Size32x32</td><td>
Square matrix with 32 rows and 32 columns.</td></tr>
<tr>
<td>
Size36x36</td><td>
Square matrix with 36 rows and 36 columns.</td></tr>
<tr>
<td>
Size40x40</td><td>
Square matrix with 40 rows and 40 columns.</td></tr>
<tr>
<td>
Size44x44</td><td>
Square matrix with 44 rows and 44 columns.</td></tr>
<tr>
<td>
Size48x48</td><td>
Square matrix with 48 rows and 48 columns.</td></tr>
<tr>
<td>
Size52x52</td><td>
Square matrix with 52 rows and 52 columns.</td></tr>
<tr>
<td>
Size64x64</td><td>
Square matrix with 64 rows and 64 columns.</td></tr>
<tr>
<td>
Size72x72</td><td>
Square matrix with 72 rows and 72 columns.</td></tr>
<tr>
<td>
Size80x80</td><td>
Square matrix with 80 rows and 80 columns.</td></tr>
<tr>
<td>
Size88x88</td><td>
Square matrix with 88 rows and 88 columns.</td></tr>
<tr>
<td>
Size96x96</td><td>
Square matrix with 96 rows and 96 columns.</td></tr>
<tr>
<td>
Size104x104</td><td>
Square matrix with 104 rows and 104 columns.</td></tr>
<tr>
<td>
Size120x120</td><td>
Square matrix with 120 rows and 120 columns.</td></tr>
<tr>
<td>
Size132x132</td><td>
Square matrix with 132 rows and 132 columns.</td></tr>
<tr>
<td>
Size144x144</td><td>
Square matrix with 144 rows and 144 columns.</td></tr>
<tr>
<td>
Size8x18</td><td>
Rectangular matrix with 8 rows and 18 columns.</td></tr>
<tr>
<td>
Size8x32</td><td>
Rectangular matrix with 8 rows and 32 columns.</td></tr>
<tr>
<td>
Size12x26</td><td>
Rectangular matrix with 12 rows and 26 columns.</td></tr>
<tr>
<td>
Size12x36</td><td>
Rectangular matrix with 12 rows and 36 columns.</td></tr>
<tr>
<td>
Size16x36</td><td>
Rectangular matrix with 16 rows and 36 columns.</td></tr>
<tr>
<td>
Size16x48</td><td>
Rectangular matrix with 16 rows and 48 columns.</td></tr>
</table>

### QRBarcode settings
The [QRBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html) settings allows users to modify the version, error correction level, and input mode of the QRBarcode.

#### QRVersion
The QR Barcode uses [QRVersion](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html#Syncfusion_UI_Xaml_Barcode_QRBarcode_QRVersion) property to decide the version from 1 to 40 using [QRBarcodeVersion](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcodeVersion.html) enumeration where Version 1 measures 21 modules x 21 modules, Version 2 measures 25 modules x 25 modules, and so on, increasing in steps of 4 modules per side up to Version 40 which measures 177 modules x 177 modules. By default, the QR version is set to [Auto](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcodeVersion.html#Syncfusion_UI_Xaml_Barcode_QRBarcodeVersion_Auto), which means that it will be set based on the length of the input text.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:QRBarcode QRVersion="Version01" />
</syncfusion:SfBarcode.Symbology>

{% endhighlight  %}
{% endtabs %}

#### ErrorCorrectionLevel
The QR Barcode uses [ErrorCorrectionLevel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html#Syncfusion_UI_Xaml_Barcode_QRBarcode_ErrorCorrectionLevel) property to generate a series of error correction codewords that are added to the data code word sequence in order to enable the symbol to withstand damage without data loss. There are four user–selectable levels of error correction. By default, the property value is [Low](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.ErrorCorrectionLevel.html#Syncfusion_UI_Xaml_Barcode_ErrorCorrectionLevel_Low).

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:QRBarcode ErrorCorrectionLevel="Quartile" />
</syncfusion:SfBarcode.Symbology>

{% endhighlight  %}
{% endtabs %}

**Error Correction Level Table**

<table>
<tr>
<th>
Error Correction Level</th><th>
Recovery Capacity % (approx.)</th></tr>
<tr>
<td>
Low</td><td>
7</td></tr>
<tr>
<td>
Medium</td><td>
15</td></tr>
<tr>
<td>
Quartile</td><td>
25</td></tr>
<tr>
<td>
High</td><td>
30</td></tr>
</table>

#### InputMode
The QR Barcode uses [InputMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html#Syncfusion_UI_Xaml_Barcode_QRBarcode_InputMode) property to decide the supported character set for value. The default value is [BinaryMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRInputMode.html#Syncfusion_UI_Xaml_Barcode_QRInputMode_BinaryMode).

The [QRInputMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRInputMode.html) enumeration has following values:

* NumericMode
* AlphaNumericMode
* BinaryMode

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:QRBarcode InputMode="AlphaNumericMode" />
</syncfusion:SfBarcode.Symbology>

{% endhighlight  %}
{% endtabs %}

**Input Mode Table**

<table>
<tr>
<th>
Input Mode</th><th>
Possible characters</th></tr>
<tr>
<td>
Numeric Mode</td><td>
0,1,2,3,4,5,6,7,8,9</td></tr>
<tr>
<td>
Alphanumeric Mode</td><td>
0–9, A–Z (upper-case only), space, $, %, *, +, -,., /, :</td></tr>
<tr>
<td>
Binary Mode</td><td>
Shift JIS characters</td></tr>
</table>
