---
layout: post
title: Getting Started with WinUI NumberBox | Syncfusion
description: Learn how to get started with Syncfusion WinUI NumberBox (SfNumberBox) control, its elements, and more in here.
platform: WinUI
control: SfNumberBox
documentation: ug
---

# Getting Started with WinUI NumberBox

This section explains the steps required to add the [WinUI NumberBox](https://www.syncfusion.com/winui-controls/NumberBox) control in the WinUI application and utilize the various functions provided.

## Structure of NumberBox control

![WinUI NumberBox Structure](Overview_images/overview_img.png)

## Creating an application with WinUI NumberBox

In this walkthrough, you will create a WinUI application that contains the [NumberBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html) control.

## Adding control manually in XAML

To add `NumberBox` control manually in XAML, follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2.  Download and refer the following NuGet package in the project.

    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)

3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML page.
4. Initialize the `NumberBox` control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid Name="grid">
        <!--Adding NumberBox control -->
        <editors:SfNumberBox HorizontalAlignment="Center"
                             VerticalAlignment="Center" 
                             Value="15.35" />
    </Grid>
</Page>

{% endhighlight %}
{% endtabs %}

## Adding control manually in C#

To add `NumberBox` control manually in C# , follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2.  Download and refer the following NuGet in the project.

    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)

3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in C# page.
4. Initialize the `NumberBox` control.

{% tabs %}
{% highlight c# %}

namespace GettingStarted
{
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the NumberBox control
            SfNumberBox sfNumberBox = new SfNumberBox();
            sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
            sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
            sfNumberBox.Value = 15.35;

            grid.Children.Add(sfNumberBox);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox Application](GettingStarted_images/gettingStarted_img.png)

## Editing the value

By default, the [NumberBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html) control allows you to enter numeric input and restricts the alphabetic input. Once `Enter` key is pressed or control focus is lost, the value of the `NumberBox` control is validated and updated based on the format applied.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center" 
                     VerticalAlignment="Center" 
                     CustomFormat="0.000" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.CustomFormat = "0.000";

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox value editing](GettingStarted_images/editing_value.gif)

## Change number format

You can change the format in which the value should be displayed using the [CustomFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_CustomFormat) property and [NumberFormatter](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_NumberFormatter) property. By default, value of the `CustomFormat` property and `NumberFormatter` property is **null**. You can apply various custom formats available in [this link](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings) to the `NumberBox` control  using `CustomFormat` property.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center"
                     Value="12.5" 
                     CustomFormat="C2" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.Value = 12.5;
sfNumberBox.CustomFormat = "C2";

{% endhighlight %}
{% endtabs %}

You can also change the format of the value of `NumberBox` control using `NumberFormatter` property with [different formatters](https://docs.microsoft.com/en-us/uwp/api/windows.globalization.numberformatting?view=winrt-20348) available.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox Name="sfNumberBox" 
                     HorizontalAlignment="Center" 
                     VerticalAlignment="Center" 
                     Value="12.5" />

{% endhighlight %}
{% highlight C# %}

CultureInfo ci = new CultureInfo("en-US");
string currencyCode = new RegionInfo(ci.LCID).ISOCurrencySymbol;
sfNumberBox.NumberFormatter = new CurrencyFormatter(currencyCode, new string[] { ci.Name }, "ZZ")
{
    IntegerDigits = 1,
    FractionDigits = 2,
    Mode = CurrencyFormatterMode.UseCurrencyCode
};

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox value editing](GettingStarted_images/custom_format.png)

## Accept null value

By default, `NumberBox` control allows **null** value. A null value is assigned when the user clicks the clear button or clears the input. You can disable this by setting the value of [AllowNull](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_AllowNull) property as **false**. When value of the `AllowNull` property is set to **false** and the input is cleared, the `NumberBox` control returns it to **0**. 

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center"
                     AllowNull="False" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.AllowNull = false;

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox prevent empty textbox](GettingStarted_images/allowNull.gif)

## Header and description
This section explains about header and description property of NumberBox.
### Header
The `Header` property is used to displays the title for the NumberBox Control.
     
{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox x:Name="numberBox" 
                     Height="75" 
                     Width="300" 
                     Header="Amount to withdraw" 
                     Value="100" />

 
{% endhighlight %}
{% highlight c# %}

SfNumberBox SfNumberBox = new SfNumberBox();
SfNumberBox.Header = "Amount to withdraw";

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox with Header](GettingStarted_images/header_text.png)

#### Header Customization
Customize the header appearance of control by using the `HeaderTemplate` property of control. The following code shows how to use a header template to customize the header.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox Value="100" CustomFormat="#,0.00" Width="250" Height="75">
            <editors:SfNumberBox.HeaderTemplate>
                <DataTemplate>
                    <StackPanel Orientation="Horizontal">
                       <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xEF40;"/>
                       <TextBlock Text="Amount" FontSize="14" Margin="5"/>
                    </StackPanel>
                </DataTemplate>
            </editors:SfNumberBox.HeaderTemplate>
  </editors:SfNumberBox>

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox with Header Template](GettingStarted_images/header_template.png)

### Description
The `Description` support is used to display the content beneath the control and to provide guidance on the input that the control expects.

{% tabs %}
{% highlight xaml %}
   
<editors:SfNumberBox x:Name="numberBox" 
                      Height="75"
                      Width="300" 
                      Value="10"  
                      Description="Please enter only positive digits."/>

{% endhighlight %}
{% highlight c# %}

SfNumberBox SfNumberBox = new SfNumberBox();
SfNumberBox.Description = “Please enter only positive digits.”;


{% endhighlight %}
{% endtabs %}

![WinUI NumberBox with Description](GettingStarted_images/description_text.png)


## Setting watermark text

You can prompt the user with any information by using the [PlaceholderText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_PlaceholderText) property. Watermark text will be displayed only when the value of the [AllowNull](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_AllowNull) property is **true** and the value of `NumberBox` control is **null**. The default value of `PlaceholderText` property is **string.Empty** (No string will be displayed).

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center" 
                     VerticalAlignment="Center" 
                     PlaceholderText="Enter input here..." />

{% endhighlight %}
{% highlight C# %}

SfNumberBox SfNumberBox= new SfNumberBox();
SfNumberBox.PlaceholderText = "Enter input here...";
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox Watermark Text](GettingStarted_images/watermark_text.png)

## Clear button visibility 

The `ShowClearButton` Property is used to show or hide the clear button in `NumberBox`. By default, visibility of the clear button is enabled.

N> The clear button appears only when the text box is focused and the `IsEditable` property value is set to **true**.
{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox x:Name="numberBox" 
            Height="75" 
            Width="300"                   
            ShowClearButton="True" 
            IsEditable="True" 
            Value="10"/>


{% endhighlight %}
{% highlight C# %}

SfNumberBox SfNumberBox = new SfNumberBox();
SfNumberBox.ShowClearButton = true;
SfNumberBox.IsEditable = true; 


{% endhighlight %}
{% endtabs %}

If IsEditable is true

![WinUI NumberBox with Clear Button](GettingStarted_images/clearbutton_visible.png)

If IsEditable is false

![WinUI NumberBox without Clear Button](GettingStarted_images/clearbutton_collapsed.png)


## Value changed notification

The [ValueChanged]( [AllowNull](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_AllowNull)) event is triggered, when the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_Value) property of `NumberBox` control is changed. The value will not be changed when the user enters the input. The value of the `NumberBox` control will be changed after validation is performed on the `Enter` keypress or when the focus is lost in the control. The `ValueChanged` contains the following properties.

 * `NewValue` - Contains the new input value.
 * `OldValue` - Contains the previous input value.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center" 
                     x:Name="sfNumberBox"
                     ValueChanged="sfNumberBox_ValueChanged" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.ValueChanged += sfNumberBox_ValueChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows.

{% tabs %}
{% highlight C# %}

private void sfNumberBox_ValueChanged(object sender, ValueChangedEventArgs e)
{
    var oldValue = e.OldValue;
    var newValue = e.NewValue;
}

{% endhighlight %}
{% endtabs %}