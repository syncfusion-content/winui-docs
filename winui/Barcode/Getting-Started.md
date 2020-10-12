---
layout: post
title: Getting Started | Barcode | WinUI | Syncfusion
description: This section explains how to add Syncfusion Barcode control and how it can be customized in WinUI platform.
platform: WinUI
control: Barcode
documentation: ug
---

# Getting Started with WinUI Barcode

This section provides a quick overview for getting started with the [Barcode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Controls.Barcode.SfBarcode.html) for WinUI. Walk through the entire process of creating a real world of this control.

## Creating simple application with Barcode

* Creating the project
* Add `Barcode` to Project
* Set the required Barcode using `Symbology` property.

## Creating an application with WinUI Barcode

### Create a new WinUI Project

Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.

### Add Barcode to Project

The `Barcode` control can be added to project by the following ways.

#### Adding Barcode by XAML

1. Add `Syncfusion.Barcode.WinUI` NuGet.
2. Import `Syncfusion.UI.Xaml.Controls.Barcode` in XAML Page.
3. Declare `Barcode` control in XAML page.

The following code example shows how to create the Barcode control from XAML:

{% tabs %}
{% highlight xaml %}

<Page x:Class="syncfusion.barcodedemos.winui.GettingStartedPage "
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                xmlns:syncfusion="using:Syncfusion.UI.Xaml.Controls.Barcode"
                xmlns:local="using:syncfusion.barcodedemos.winui"
                Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
                NavigationCacheMode="Disabled">
                <Grid>
                        <syncfusion:SfBarcode x:Name="barcode" Value="48625310"/>
                </Grid>

</Page>

{% endhighlight %}
{% endtabs %} 

#### Adding Barcode by C#

In order to add control manually in C#, do the below steps,

1. Add the below required assembly references to the project,
    * Syncfusion.Barcode.WinUI
2. Import Barcode namespace `using Syncfusion.UI.Xaml.Controls.Barcode`.
3. Create `Barcode` control instance and add it to the Page.

{% tabs %} 
{% highlight C# %} 

using Microsoft.UI.Xaml.Controls;
using Syncfusion.UI.Xaml.Controls.Barcode;

public sealed partial class GettingStartedPage : Page
{
    /// <summary>
    /// Interaction logic for GettingStartedPage.xaml
    /// </summary>
    public GettingStartedPage()
    {
        this.InitializeComponent();
        SfBarcode barcode = new SfBarcode();
        Root_Grid.Children.Add(barcode);
    }
}

{% endhighlight %}
{% endtabs %} 

![CodaBar Barcode](Getting_Started_Images/CodaBar.png)

## Symbology

You can set the required symbology to the barcode based on input value by initializing the respective Symbology instance in `Symbology` property. In the following code snippet, the QR code has been set as the barcode symbology.

{% tabs %}
{% highlight xaml %}

<Page xmlns:syncfusion="using:Syncfusion.UI.Xaml.Controls.Barcode">

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

![OR Barcode](Getting_Started_Images/QRBarcode.png)

## Text Customization

The Barcode text can be customized by using below properties,

### Value

The text to be encoded can be set using the `Value` property. By default, this original text will be displayed at the bottom of the bar code. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="48625310" Height="150"/>
               
{% endhighlight %}
{% endtabs %}

![CodaBar Barcode with Value](Getting_Started_Images/CodaBar.png)

### TextSpacing

The space between barcode and text can be increased/decreased by using `TextSpacing` property. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" TextSpacing="7"/>

{% endhighlight %}
{% endtabs %}

![CodaBar Barcode with Text spacing](Getting_Started_Images/textspacing.png)

### ShowValue

The visibility of the Barcode text can be changed using `ShowValue` property in Barcode. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" ShowValue="False"/>

{% endhighlight %}
{% endtabs %}

![CodaBar Barcode with ShowValue set to false](Getting_Started_Images/showvalue.png)

### HorizontalTextAlignment

The alignment of the Barcode text can be changed using `HorizontalTextAlignment' property in Barcode.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" HorizontalTextAlignment="Right" />

{% endhighlight %}
{% endtabs %}

![HorizontalTextAlignment set to Right](Getting_Started_Images/HorizontalTextAlignment.png)

### VerticalTextAlignment

The alignment of the Barcode text can be changed using `VerticalTextAlignment' property in Barcode.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfBarcode x:Name="barcode" Value="10110111" Height="150" VerticalTextAlignment="Top" />

{% endhighlight %}
{% endtabs %}

![VerticalTextAlignment set to Top](Getting_Started_Images/VerticalTextAlignment.png)
