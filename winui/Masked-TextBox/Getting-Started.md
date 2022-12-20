---
layout: post
title: Getting started with WinUI MaskedTextBox control | Syncfusion
description: Learn all about getting started with the Syncfusion WinUI MaskedTextBox (SfMaskedTextBox) control and its basic features here.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Getting Started with WinUI MaskedTextBox

This section explains the steps required to add the WinUI MaskedTextBox control to get started with Syncfusion `MaskedTextBox` control.

## Creating an application with WinUI MaskedTextBox control

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `MaskedTextBox` control.

## Initialize MaskedTextBox control using simple mask

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
    <Grid>
        <!--Adding SfMaskedTextBox control for date mask.-->
        <syncfusion:SfMaskedTextBox Width="200"
                                    MaskType="Simple"
                                    Mask="00/00/0000" />
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

// Creating an instance of the MaskedTextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "00/00/0000";

{% endhighlight %}
{% endtabs %}

![Simple mask in WinUI MaskedTextBox](MaskedTextBox_Images/winui_simple_mask.png)

## Initialize MaskedTextBox control using RegEx mask

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
    <Grid>
        <!--Adding SfMaskedTextBox control for email mask.-->
        <syncfusion:SfMaskedTextBox Width="200"
                                    MaskType="RegEx"
                                    Mask="[A-Za-z0-9._%-]+@[A-Za-z0-9]+\.[A-Za-z]{2,3}" />
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

// Creating an instance of the MaskedTextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[A-Za-z0-9._%-]+@[A-Za-z0-9]+\\.[A-Za-z]{2,3}";

{% endhighlight %}
{% endtabs %}

![RegEx mask in WinUI MaskedTextBox](MaskedTextBox_Images/winui_regex_mask.png)

## Setting the prompt character

Displays prompt character for the absence of your input in the mask and its default value is ‘_’. You can set the custom prompt character using `PromptChar` property.

{% tabs %}
{% highlight C# %}

// Creating an instance of the MaskedTextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "00/00/0000";
maskedTextBox.PromptChar = '#';

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox prompt character](MaskedTextBox_Images/winui_masked_textbox_prompt_char.png)

## Setting the value

The MaskedTextBox control displays the value that can be set using the `Value` property.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox Width="200"
                            MaskType="Simple"
                            Mask="00/00/0000"
                            Value="12/02/2022" />

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "00/00/0000";
maskedTextBox.Value = "12/02/2022";

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox value](MaskedTextBox_Images/winui_masked_textbox_value.png)