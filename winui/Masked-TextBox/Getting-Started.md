---
layout: post
title: Getting started with WinUI Masked TextBox control | Syncfusion
description: Learn all about getting started with the Syncfusion WinUI Masked TextBox (SfMaskedTextBox) control and its basic features here.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Getting Started with WinUI Masked TextBox

This section explains the steps required to add the [WinUI Masked TextBox](https://www.syncfusion.com/winui-controls/masked-textbox) control to get started with [SfMaskedTextBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html) control.

## Creating an application with WinUI Masked TextBox control

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the [SfMaskedTextBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html) control.

## Initialize Masked TextBox control using simple mask

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

// Creating an instance of the Masked TextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "00/00/0000";

{% endhighlight %}
{% endtabs %}

![Simple mask in WinUI Masked TextBox](MaskedTextBox_Images/winui_simple_mask.png)

## Initialize Masked TextBox control using RegEx mask

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

// Creating an instance of the Masked TextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[A-Za-z0-9._%-]+@[A-Za-z0-9]+\\.[A-Za-z]{2,3}";

{% endhighlight %}
{% endtabs %}

![RegEx mask in WinUI Masked TextBox](MaskedTextBox_Images/winui_regex_mask.png)

## Setting the prompt character

Every single mask displays a prompt character ('_') in the absence of your input. You can customize this prompt character by using the [PromptChar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_PromptChar) property.

{% tabs %}
{% highlight C# %}

// Creating an instance of the Masked TextBox control.
SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "00/00/0000";
maskedTextBox.PromptChar = '#';

{% endhighlight %}
{% endtabs %}

![WinUI Masked TextBox prompt character](MaskedTextBox_Images/winui_masked_textbox_prompt_char.png)

## Setting the value

The [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property is used to set the input value for Masked TextBox control.

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

![WinUI Masked TextBox value](MaskedTextBox_Images/winui_masked_textbox_value.png)
