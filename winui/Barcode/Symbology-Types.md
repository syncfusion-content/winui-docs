---
layout: post
title: Symbology Types in WinUI Barcode control | Syncfusion
description: Learn here all about Symbology Types feature in Syncfusion WinUI Barcode control and it supports many variants of one and two-dimensional barcodes.
platform: WinUI
control: Barcode
documentation: ug
---

# Symbology Types in WinUI Barcode
Barcode Symbology supports 12 variants of one-dimensional and 3 variants of two-dimensional barcodes.

## One-Dimensional Barcodes
One-Dimensional barcode is also called as linear barcode. The bars and spaces for each symbol in one-dimensional barcodes are grouped in such a way to represent a specific ASCII character.

The following table represents supported one-dimensional barcode symbologies.

<table>
<tr>
<th>Symbology</th>
<th>Supported characters</th>
</tr>
<tr>
<td>
{{'[Codabar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.CodabarBarcode.html)'| markdownify }}
</td>
<td>
[0-9]; [- $ : / . +]
</td>
</tr>
<tr>
<td>
{{'[Code 11](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code11Barcode.html)'| markdownify }}
</td>
<td>
[0-9]; [-]
</td>
</tr>
<tr>
<td>
{{'[Code 32](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code32Barcode.html)'| markdownify }}
</td>
<td>
[0-9]
</td>
</tr>
<tr>
<td>
{{'[Code 39](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39Barcode.html)'| markdownify }}
</td>
<td>
[0-9]; [A-Z]; [- . $ / + % SPACE]
</td>
</tr>
<tr>
<td>
{{'[Code 39 Extended](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39ExtendedBarcode.html)'| markdownify }}
</td>
<td>
[0-9]; [A-Z]; [a-z]
</td>
</tr>
<tr>
<td>
{{'[Code 93](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code93Barcode.html)'| markdownify }}
</td>
<td>
[0-9]; [A-Z]; [- . $ / + % SPACE]
</td>
</tr>
<tr>
<td>
{{'[Code 93 Extended](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code93ExtendedBarcode.html)'| markdownify }}
</td>
<td>
All 128 ASCII characters
</td>
</tr>
<tr>
<td>
{{'[Code128A](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128ABarcode.html)'| markdownify }}
</td>
<td>
[0-9]; [A-Z]; [NUL (0x00) SOH (0x01) STX (0x02) ETX (0x03) EOT(0x04) ENQ (0x05) ACK (0x06) BEL (0x07) BS (0x08) HT (0x09) LF (0x0A) VT(0x0B) FF (0x0C) CR (0x0D) SO (0x0E) SI (0x0F) DLE (0x10) DC1 (0x11) DC2(0x12) DC3 (0x13) DC4 (0x14) NAK (0x15) SYN (0x16) ETB (0x17) CAN(0x18) EM (0x19) SUB (0x1A) ESC (0x1B) FS (0x1C) GS (0x1D) RS (0x1E) US(0x1F) SPACE (0x20)]; [" ! # $ % & ' ( ) * + , - . / ; &lt; = &gt; ? @ [ / ]^ _ ]
</td>
</tr>
<tr>
<td>
{{'[Code 128B](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128BBarcode.html)'| markdownify }}
</td>
<td>
[0-9]; [A-Z]; [a-z]; [SPACE (0x20) ! " # $ % & ' ( ) * + , - . / :; &lt; = &gt; ? @ [ / ]^ _ `  { | } ~ DEL (•) ]
</td>
</tr>
<tr>
<td>
{{'[Code 128C](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128CBarcode.html)'| markdownify }}
</td>
<td>
ASCII 00-99(encodes each two digit with one code)
</td>
</tr>
<tr>
<td>
{{'[UPCBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.UpcBarcode.html)'| markdownify }}
</td>
<td>
[0-9]
</td>
</tr>
<tr>
<td>
{{'[GS1Code128Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.GS1Code128Barcode.html)'| markdownify }}
</td>
<td>
ASCII 00-99(encodes each two digit with one code)
</td>
</tr>
</table>

N> [One dimensional Symbology Customization](https://help.syncfusion.com/winui/barcode/symbology-customization#one-dimensional-barcode-settings)

### Codabar
The [CodabarBarcode] (https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.CodabarBarcode.html) is a discrete numerical symbology used in libraries, blood banks, and other information processing applications.

* Encodes only numeric characters and some special characters like dash (-), colon (:), slash (/), plus (+).
* Each character has three bars and four spaces.
* Uses A, B, C, D as start and stop characters.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:CodabarBarcode />    
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![CodabarBarcode](Symbology_Images/CodaBar.png)

### Code 11
The [Code11Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code11Barcode.html) Symbology is used primarily for labeling telecommunications equipment and it has the following structure:

* Allows character set of digits (0-9) and dash (-).
* Each character is encoded with 3 bars and 2 spaces.
* There may be two wide and three narrow elements or one wide and four narrow elements among these five elements.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code11Barcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code11Barcode](Symbology_Images/Code11.png)

### Code 32
The [Code32Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code32Barcode.html) is primarily used for coding pharmaceuticals, cosmetics, and dietetics, and it has the following structure:

* Starts with ‘A’ character (ASCII 65) that is not really encoded.
* Encodes only the character set of length 8.
* Checksum module 10 has one digit that is automatically calculated.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code32Barcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code32Barcode](Symbology_Images/Code32.png)

### Code 39
The [Code39Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39Barcode.html) is a type of Barcode Symbology that encodes alphanumeric characters into a series of bars. It can be any length, though more than 25 characters begin to push the bounds. This is the only type of Barcode symbology that does not require a checksum.

* Allows character set of digits (0-9), upper case alphabets (A-Z), and symbols like space, minus (-), plus (+), period (.), dollar sign ($), slash (/), and percent (%).
* Always starts and ends with an asterisk (*) symbol, termed as start and stop character.
* Each character is encoded with five bars and four spaces where three are wide and six are narrow.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code39Barcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code39Barcode](Symbology_Images/Code39.png)

### Code 39 Extended
The [Code39ExtendedBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39ExtendedBarcode.html) Symbology is an extended version of [Code39Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39Barcode.html) that supports the full ASCII character set. It encodes lower case alphabets (a-z) as well as special characters in the keyboard.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code39ExtendedBarcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code39ExtendedBarcode](Symbology_Images/Code39Extended.png)

### Code 93
The [Code93Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code93Barcode.html) is designed to complement and improve upon [Code39Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code39Barcode.html). It represents the full ASCII character set by using the combination of 2 characters. It is a continuous, variable-length symbology that produces a denser code.

* Encodes character set of uppercase alphabets (A-Z), digits (0-9), and special characters like asterisk (*), dash (-), dollar ($), percent (%), Space, dot (.), slash (/), and plus (+).
* The asterisk (*) is not a true encoding character, but it is the start and stop symbol for [Code93Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code93Barcode.html) [Symbology](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.SfBarcode.html#Syncfusion_UI_Xaml_Barcode_SfBarcode_Symbology).

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code93Barcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code93Barcode](Symbology_Images/Code93.png)

### Code 93 Extended
The [Code93ExtendedBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code93ExtendedBarcode.html) is designed to complement and improve upon Code 39. It represents the full ASCII character set by using the combination of 2 characters. It is a continuous, variable-length Symbology that produces a denser code.

* Encodes character set of uppercase alphabets (A-Z), digits (0-9), and special characters like asterisk (*), dash (-), dollar ($), percent (%), Space, dot (.), slash (/), and plus (+).
* The asterisk (*) is not a true encoding character, but it is the start and stop symbol for Code 93 symbology.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Code93ExtendedBarcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code93ExtendedBarcode](Symbology_Images/Code93Extended.png)

#### Code 128A
The [Code128ABarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128ABarcode.html) (or Chars Set A) includes all the standard upper case U.S. alphanumeric keyboard characters and punctuation characters together with the control characters, (characters with ASCII values from 0 to 95 inclusive), and seven special characters.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:Code128ABarcode />  
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code128ABarcode](Symbology_Images/Code128A.png)

#### Code128B
The [Code128BBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128BBarcode.html) (or Chars Set B) includes all the standard upper case alphanumeric keyboard characters and punctuation characters together with the lower case alphabetic characters (characters with ASCII values from 32 to 127 inclusive), and seven special characters.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:Code128BBarcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code128BBarcode](Symbology_Images/Code128B.png)

#### Code128C
The [Code128CBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Code128CBarcode.html) (or Chars Set C) includes a set of 100 digit pairs from 00 to 99 inclusive, as well as three special characters. This allows numeric data to be encoded as two data digits per symbol character effectively twice the density of standard data.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:Code128CBarcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Code128CBarcode](Symbology_Images/Code128C.png)

### UPC
The [UPCBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.UpcBarcode.html)(Universal Product Code), also known as UPC-A. It encodes 12 numeric digits. UPC barcode symbology mostly used in trade items.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:UpcBarcode />  
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![UPCBarcode](Symbology_Images/UPC_Barcode.png)

### GS1Code128Barcode
The [GS1Code128Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.GS1Code128Barcode.html) also known as EAN-128 barcode. It is commonly used in shipping and supply chain entities.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:GS1Code128Barcode />  
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![GS1Code128Barcode](Symbology_Images/GS1Code128Barcode.png)

## Two Dimensional Barcodes
Two Dimensional Barcode is a way to represent information via two-dimensional approach. It is similar to One Dimensional Barcode, but can represent more data per unit area.

The following table represents the supported two dimensional barcode symbologies

<table>
<tr>
<th>Symbology</th>
<th>Supported characters</th>
</tr>
<tr>
<td>
{{'[QR Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html)'| markdownify }}
</td>
<td>
[0–9]; [A–Z (upper-case only)]; [space $ % * + - . / , :]; [Shift JIS characters]
</td>
</tr>
<tr>
<td>
{{'[DataMatrixBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html)'| markdownify }}
</td>
<td>
All ASCII characters
</td>
</tr>
<tr>
<td>
{{'[Pdf417Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Pdf417Barcode.html)'| markdownify }}
</td>
<td>
All ASCII characters
</td>
</tr>
</table>

N> [Two dimensional Symbology Customization](https://help.syncfusion.com/winui/barcode/symbology-customization#two-dimensional-barcode-settings)

### QR Code
The [QRBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.QRBarcode.html) is a two dimensional barcode symbology that is popularly used in automotive industry. It is known for fast readability and greater storage capacity.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:QRBarcode />   
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![QRBarcode](Symbology_Images/QRBarCode.png)

### Data Matrix
The [DataMatrixBarcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.DataMatrixBarcode.html) is widely used in printed media such as labels and letters. It can be read easily by a Barcode reader and also by mobile phones. It consists of a grid of dark and light dots or blocks forming square or rectangular symbol. The data encoded in the Barcode can be either number or alphanumeric.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>  
    <syncfusion:DataMatrixBarcode />  
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![DataMatrixBarcode](Symbology_Images/DataMatrix.png)

### Pdf417Barcode
The [Pdf417Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Barcode.Pdf417Barcode.html) is a two dimensional barcode and it can encode text, numbers, files, and actual data bytes. It is mainly used in a variety of applications such as transport, identification cards, and inventory management.
 
{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode.Symbology>   
    <syncfusion:Pdf417Barcode />  
</syncfusion:SfBarcode.Symbology>

{% endhighlight %}
{% endtabs %}

![Pdf417Barcode](Symbology_Images/Pdf417Barcode.png)
