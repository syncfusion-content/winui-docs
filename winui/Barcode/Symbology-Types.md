---
layout: post
title: Types of Symbology in Syncfusion Barcode control for Winui
description: Different types of Symbology in one-dimensional and two-dimensional barcodes are explained.
platform: WinUI
control: Barcode
documentation: ug
---

# Types of Symbology

Barcode Symbology supports 11 variants of one dimension and 2 variants of two dimensional barcodes that are shown as follows.

## One Dimensional Barcodes

One dimensional barcode is also called as linear barcode. The bars and spaces for each symbol in one dimensional barcodes are grouped in such a way to represent a specific ASCII character.

* Codabar
* Code 11
* Code 32
* Code 39
* Code 39 Extended
* Code 93
* Code 93 Extended
* Code 128A
* Code 128B
* Code 128C
* UPC

### Codabar

`CodabarBarcode` is a discrete numerical symbology that is used in libraries, blood banks and a variety of other information processing applications.

* Encodes only numeric characters and some special characters like dash (-), colon (:), slash (/), plus (+).
* Each character has three bars and four spaces.
* Uses characters of A, B, C, D as start and stop characters.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:CodabarBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![CodabarBarcode](Symbology_Images/CodaBar.png)

Codabar Barcode

{:.caption}

### Code 11

`Code11Barcode` Symbology is used primarily for labeling the telecommunications equipment and it has the following structure.

* Allows character set of digits (0-9), dash (-).
* Each character is encoded with 3 bars and 2 spaces.
* Of these five elements, there may be two wide and three narrow elements or one wide and four narrow elements.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code11Barcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code11Barcode](Symbology_Images/Code11.png)

Code 11 Barcode

{:.caption}

### Code 32

`Code32Barcode` is primarily used for coding pharmaceuticals, cosmetics, dietetics and it has the following structure:

* Starts with ‘A’ character (ASCII 65) that is not really encoded.
* Encodes only the character set of length 8.
* One digit for Checksum module 10 that is automatically calculated.


{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code32Barcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code32Barcode](Symbology_Images/Code32.png)

Code32 Barcode

{:.caption}

### Code 39

`Code39Barcode` is a Symbology of Barcode that encodes alphanumeric characters into a series of bars. It may be of any length, although more than 25 characters begin to push the bounds. This Symbology is the only type of the Barcode in common use that does not require a checksum.

* Allows character set of digits (0-9), upper case alphabets (A-Z), and symbols like space, minus (-), plus (+), period (.), dollar sign ($), slash (/), and percent (%).
* Always starts and ends with an asterisk (*) symbol, termed as start and stop character.
* Each character is encoded with 5 bars and 4 spaces where 3 are wide and 6 are narrow.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code39Barcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code39Barcode](Symbology_Images/Code39.png)

Code 39 Barcode

{:.caption}

### Code 39 Extended

`Code39ExtendedBarcode` Symbology is an extended version of `Code39Barcode` which supports the full ASCII character set. It encodes lower case alphabets (a-z) as well as special characters in the keyboard.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code39ExtendedBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code39ExtendedBarcode](Symbology_Images/Code39Extended.png)

Code 39 Extended Barcode

{:.caption}

### Code 93

`Code93Barcode` is designed to complement and improve upon `Code39Barcode`. It represents the full ASCII character set by using the combination of 2 characters. It is a continuous, variable-length symbology that produces a denser code.

* Encodes character set of uppercase alphabets (A-Z), digits (0-9), and special characters like asterisk (*), dash (-), dollar ($), percent (%), Space, dot (.), slash (/), and plus (+).
* The asterisk (*) is not a true encoding character, but it is the start and stop symbol for `Code93Barcode` `Symbology`.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>        
         <syncfusion:Code93Barcode />          
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code93Barcode](Symbology_Images/Code93.png)

Code93 Barcode 

{:.caption}

### Code 93 Extended

`Code93ExtendedBarcode` is designed to complement and improve upon Code 39. It represents the full ASCII character set by using the combination of 2 characters. It is a continuous, variable-length Symbology that produces a denser code.

* Encodes character set of uppercase alphabets (A-Z), digits (0-9), and special characters like asterisk (*), dash (-), dollar ($), percent (%), Space, dot (.), slash (/), and plus (+).
* The asterisk (*) is not a true encoding character, but it is the start and stop symbol for Code 93 symbology.


{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code93ExtendedBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code93ExtendedBarcode](Symbology_Images/Code93Extended.png)

Code93 Extended Barcode

{:.caption}

#### Code 128A

`Code128ABarcode` (or Chars Set A) includes all the standard upper case U.S. alphanumeric keyboard characters and punctuation characters together with the control characters, (characters with ASCII values from 0 to 95 inclusive), and seven special characters.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code128ABarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code128ABarcode](Symbology_Images/Code128A.png)

Code128A Barcode

{:.caption}

#### Code128B

`Code128BBarcode` (or Chars Set B) includes all the standard upper case alphanumeric keyboard characters and punctuation characters together with the lower case alphabetic characters (characters with ASCII values from 32 to 127 inclusive), and seven special characters.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code128BBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code128BBarcode](Symbology_Images/Code128B.png)

Code128B Barcode

{:.caption}

#### Code128C

`Code128CBarcode` (or Chars Set C) includes a set of 100 digit pairs from 00 to 99 inclusive, as well as three special characters. This allows numeric data to be encoded as two data digits per symbol character effectively twice the density of standard data.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:Code128CBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![Code128CBarcode](Symbology_Images/Code128C.png)

Code128C Barcode

{:.caption}

### UPC

The `UPCBarcode`(Universal Product Code), also known as UPC-A. It encodes 12 numeric digits. UPC barcode symbology mostly used in trade items.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:UpcBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![UPCBarcode](Symbology_Images/UPC_Barcode.png)

UPC Barcode

## Two Dimensional Barcodes

Two dimensional Barcode is a way to represent information via two-dimensional approach. It is similar to one dimensional Barcode, but can represent more data per unit area.

* QR Code
* Data Matrix

### QR Code

`QRBarcode` is a two dimensional symbology that is popularly used in automotive industry. It is known for fast readability and greater storage capacity.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:QRBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![QRBarcode](Symbology_Images/QRBarCode.png)

QR Barcode

{:.caption}

### Data Matrix

`DataMatrixBarcode` Symbology is widely used in printed media such as labels and letters. It can be read easily by a Barcode reader and also by mobile phones. It consists of a Grid of dark and light dots or blocks forming square or rectangular symbol. The data encoded in the Barcode can be either number or alphanumeric.

{% highlight xaml %}

     <syncfusion:SfBarcode.Symbology>
         <syncfusion:DataMatrixBarcode />
     </syncfusion:SfBarcode.Symbology>

{% endhighlight %}

![DataMatrixBarcode](Symbology_Images/DataMatrix.png)

Data Matrix Barcode

{:.caption}