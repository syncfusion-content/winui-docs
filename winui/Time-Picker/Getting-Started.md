---
layout: post
title: Getting Started with WinUI Time Picker control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Time Picker control, its elements, and more.
platform: WinUI
control: SfTimePicker
documentation: ug
---

# Getting Started with WinUI Time Picker

This section explains the steps required to add the [WinUI Time Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html) control and its time selection options. This section covers only basic features needed to get started with Syncfusion `Time Picker` control.

## Structure of Time Picker control

![WinUI TimePicker structure](getting-started_images/winui-time-picker-structure.png)

## Creating an application with WinUI Time Picker

In this walkthrough, you will create a WinUI application that contains the `Time Picker` control.

## Adding control manually in XAML

To add `Time Picker` control manually in XAML , follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Download and refer the following NuGet in the project.
    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfTimePicker` control.

{% capture codesnippet1 %}
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="8 12" %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:editors="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d">
    <Grid Name="grid">
        <!--Adding Time Picker control -->
        <editors:SfTimePicker Name="sfTimePicker"/>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Adding control manually in C#

To add the `Time Picker` control manually in C#, follow the below steps.

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).
2. Download and refer the following NuGet in the project.
    * [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI)
3. Import the `Time Picker` namespace `Syncfusion.UI.Xaml.Editors` in C# page.
4. Initialize the `SfTimePicker` control.

{% capture codesnippet2 %}
{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1 14 15" %}

using Syncfusion.UI.Xaml.Editors;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            this.InitializeComponent();
            // Creating an instance of the Time Picker control
            SfTimePicker sfTimePicker = new SfTimePicker();
            this.Content = sfTimePicker;
        }
    }
}

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet2 | OrderList_Indent_Level_1 }}

![WinUI TimePicker control](getting-started_images/winui-time-picker-control.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/Getting_Started)

## Select time programmatically

You can set or change the selected time programmatically by using [`SelectedTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_SelectedTime) property. If you not assign any value for the `SelectedTime` property, `Time Picker` will automatically assign the current system time as `SelectedTime`.

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = new DateTimeOffset(new DateTime(2021, 10, 29, 10, 45, 10));

{% endhighlight %}
{% endtabs %}

![Programmatic selection in WinUI TimePicker](getting-started_images/winui-time-picker-programmatic-selection.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/ViewAndItemCustomization)

## Select time interactively

You can change the selected time interactively by enter the time value using keyboard or from the dropdown time spinner. You can get the selected time from the `SelectedTime` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<editors:SfTimePicker Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

SfTimePicker sfTimePicker= new SfTimePicker();

{% endhighlight %}
{% endtabs %}

![Selection in WinUI TimePicker](getting-started_images/winui-time-picker-selection.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/Getting_Started)

## Restrict selection

You can restrict users from:
* Selecting time within a specific minimum and maximum time limit using [`MinTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MinTime) and [`MaxTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_MaxTime) properties.
* Selecting a date from blocked dates using [`BlackoutTimes`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_BlackoutTimes) property.

For further reference [Time Restriction](time-restriction).

## Setting null value

If you want to set null value for the `Time Picker`, set the [`AllowNull`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_AllowNull) property as `true` and set `SelectedTime` property as `null`. If `AllowNull` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `null`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3" %}

<editors:SfTimePicker Name="sfTimePicker" 
                      SelectedTime="{x:Null}"
                      AllowNull="True"
                      />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3" %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNull = true;

{% endhighlight %}
{% endtabs %}

![Allow null value in WinUI TimePicker](getting-started_images/winui-time-picker-allow-null-value.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Header and description
This section explains about `header` and `description` properties of TimePicker.
#### Header
The `Header` property is used to display the title for the `TimePicker` Control
     
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="4" %}

<editors:SfTimePicker x:Name="TimePicker" 
                      Height="75" 
                      Width="300" 
                      Header="Select your convenient order delivery time" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfTimePicker timePicker = new SfTimePicker();
timePicker.Header = "Select your convenient order delivery time";

{% endhighlight %}
{% endtabs %}

![Customize header text in WinUI TimePicker](getting-started_images/winui-time-picker-customize-header-text.png)
#### Header customization
By using the controls `HeaderTemplate` property, you can customize the appearance of controls' header. The following code sample shows how to use a header template to customize the header.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4 5 6 7 8 9" %}

<editors:SfTimePicker  Width="250" Height="75">
    <editors:SfTimePicker.HeaderTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE8DF;"/>
                <TextBlock Text="Delivery Time" FontSize="14" Margin="5"/>
            </StackPanel>
        </DataTemplate>
    </editors:SfTimePicker.HeaderTemplate>
 </editors:SfTimePicker>


{% endhighlight %}
{% endtabs %}

![Customize header template in WinUI TimePicker](getting-started_images/winui-time-picker-customize-header-template.png)

### Description
The `Description` support is used to display the content beneath the control as well as to provide guidance on the input that the control expects.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="4" %}

<editors:SfTimePicker x:Name="TimePicker" 
                      Height="75" 
                      Width="200" 
                      Description="Your order will be delivered on time."/>


{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2 3" %}

SfTimePicker timePicker = new SfTimePicker();
timePicker.Header = "Select your convenient order delivery time";
timePicker.Description = "Your order will be delivered on time.";

{% endhighlight %}
{% endtabs %}

![Customize header description text in WinUI TimePicker](getting-started_images/winui-time-picker-customize-header-description-text.png)

## Setting watermark text

You can prompt the user with some information by using the [`PlaceholderText`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_PlaceholderText) property. This will be displayed only when the `Time Picker` contains the `SelectedTime` property as `null` and `AllowNull` property as `true`. If `AllowNull` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `PlaceholderText`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3" %}

<editors:SfTimePicker PlaceholderText="pick a travel time"
                      SelectedTime="{x:Null}"
                      AllowNull="True"
                      Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3 4" %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.PlaceholderText = "pick a travel time";
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNull = true;

{% endhighlight %}
{% endtabs %}

![Customize text with watermark in WinUI TimePicker](getting-started_images/winui-time-picker-customize-text-with-watermark.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-timepicker-examples/blob/main/Samples/TimeRestriction)

## Time changed notification

You will be notified when selected time changed in `Time Picker` by using [`SelectedTimeChanged`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfTimePicker.html#Syncfusion_UI_Xaml_Editors_SfTimePicker_TimeChanged) event. The `SelectedTimeChanged` event contains the old and newly selected time in the [`OldDateTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedDateTimeChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedDateTimeChangedEventArgs_OldDateTime) and [`NewDateTime`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedDateTimeChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_SelectedDateTimeChangedEventArgs_NewDateTime) properties.

* `OldDateTime` - Gets a time which is previously selected.
* `NewDateTime` - Gets a time which is currently selected.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<editors:SfTimePicker  
                      Name="sfTimePicker"
                      SelectedTimeChanged="SfTimePicker_TimeChanged"/>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.SelectedTimeChanged += SfTimePicker_TimeChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

private void SfTimePicker_TimeChanged(DependencyObject d, DependencyPropertyChangedEventArgs e) {          
    Console.WriteLine("The previously selected Time: " + e.OldDateTime.ToString());
    Console.WriteLine("The newly selected Time: " + e.NewDateTime.ToString());            
}

{% endhighlight %}
{% endtabs %}