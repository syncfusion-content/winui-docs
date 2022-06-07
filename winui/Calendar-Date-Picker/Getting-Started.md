---
layout: post
title: Getting Started | WinUI Calendar Date Picker | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Calendar Date Picker (SfCalendarDatePicker) control, its elements, and more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# Getting Started with WinUI Calendar Date Picker

This section explains the steps required to add the [WinUI Calendar Date Picker](https://www.syncfusion.com/winui-controls/calendar-date-picker) control and its date selection options. This section covers only basic features needed to get started with Syncfusion `Calendar Date Picker` control.

## Structure of Calendar Date Picker control

![date-picker-control-view-winui-calendar-date-picker](Getting-Started_images/date-picker-control-view-winui-calendar-date-picker.png)

## Creating an application with WinUI Calendar Date Picker

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Calendar.WinUI](https://www.nuget.org/packages/Syncfusion.Calendar.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Calendar` in XAML or C# code.
4. Initialize the `SfCalendarDatePicker` control.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="8 12" %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar"
    mc:Ignorable="d">
    <Grid Name="grid">
        <!--Adding Calendar Date Picker control -->
        <calendar:SfCalendarDatePicker Name="sfCalendarDatePicker"/>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1 14 15" %}

using Syncfusion.UI.Xaml.Calendar;

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
            // Creating an instance of the Calendar control
            SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
            this.Content = sfCalendarDatePicker;
        }
    }
}

{% endhighlight %}
{% endtabs %}

![date-picker-with-normal-view-winui-calendar-date-picker](Getting-Started_images/date-picker-with-normal-view-in-winui-calendar-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/tree/main/Samples/GettingStarted).

## Select the date programmatically

You can set or change the selected date programmatically by using the [SelectedDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectedDate) property. If no value is assigned to the `SelectedDate` property, `Calendar Date Picker` will automatically assign the current system date as the `SelectedDate`.

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker= new SfCalendarDatePicker();
sfCalendarDatePicker.SelectedDate = new DateTimeOffset(new DateTime(2021, 01, 06));

{% endhighlight %}
{% endtabs %}

![programatic-date-selection-in-winui-calendar-date-picker](Getting-Started_images/programatic-date-selection-in-winui-calendar-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction).

## Select date interactively

You can change the selected date interactively by entering the date value using keyboard or selecting from the drop-down calendar menu. You can also get the selected date from the `SelectedDate` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<calendar:SfCalendarDatePicker Name="sfCalendarDatePicker" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

SfCalendarDatePicker sfCalendarDatePicker= new SfCalendarDatePicker();

{% endhighlight %}
{% endtabs %}

![date-selection-in-winui-calendar-date-picker](Getting-Started_images/date-selection-in-winui-calendar-date-picker.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/tree/main/Samples/GettingStarted).

## Setting null value

If you want to set null value for the `Calendar Date Picker`, set the [AllowNull](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_AllowNull) property as `true` and set `SelectedDate` property as `null`. If `AllowNull` property is `false`, then the current system date is updated in `SelectedDate` property and displayed instead of `null`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3" %}

<calendar:SfCalendarDatePicker Name="sfCalendarDatePicker"
                               SelectedDate="{x:Null}"
                               AllowNull="True"
                                />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3" %}

SfCalendarDatePicker sfCalendarDatePicker= new SfCalendarDatePicker();
sfCalendarDatePicker.SelectedDate = null;
sfCalendarDatePicker.AllowNull = true;

{% endhighlight %}
{% endtabs %}

![datepicker-with-null-value-in-winui-calendar-date-picker](Getting-Started_images/datepicker-with-null-value-in-winui-calendar-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection).

## Header and description
This section explains about `header` and `description` properties of CalendarDatePicker.
#### Header
The `Header` property is used to display the title for the `CalendarDatePicker` Control.
     
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4" %}

<editors:SfCalendarDatePicker x:Name="CalendarDatePicker" 
                              Header="Enter your date of birth"
                              Width="180" 
                              Height="60" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker calendarDatePicker = new SfCalendarDatePicker();
calendarDatePicker.Header = "Enter your date of birth";

{% endhighlight %}
{% endtabs %}

![date-picker-with-header-description-in-winui-calendar-date-picker](Getting-Started_images/date-picker-with-header-description-in-winui-calendar-date-picker.png)

#### Header customization
By using the controls `HeaderTemplate` property, you can customize the appearance of controls' header. The following code sample shows how to use a header template to customize the header.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4 5 6 7 8 9" %}

<editors:SfCalendarDatePicker  Width="180" Height="75" >
            <editors:SfCalendarDatePicker.HeaderTemplate>
                <DataTemplate>
                    <StackPanel Orientation="Horizontal">
                       <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xED55;"/>
                        <TextBlock Text="Birthday Date" FontSize="14" Margin="5"/>
                    </StackPanel>
                </DataTemplate>
            </editors:SfCalendarDatePicker.HeaderTemplate>
</editors:SfCalendarDatePicker>

{% endhighlight %}
{% endtabs %}

![date-picker-with-header-template-in-winui-calendar-date-picker](Getting-Started_images/date-picker-with-header-template-in-winui-calendar-date-picker.png)

#### Description
The `Description` support is used to display the content beneath the control as well as to provide guidance on the input that the control expects.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 5" %}

<editors:SfCalendarDatePicker x:Name="CalendarDatePicker" 
                              Header="Enter your date of birth" 
                              Width="300" 
                              Height="80" 
                              Description="Candidate should born between 1990 to 2010." 
                              />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker calendarDatePicker = new SfCalendarDatePicker();
calendarDatePicker.Description = "Candidate should born between 1990 to 2010.";


{% endhighlight %}
{% endtabs %}

![date-picker-with-description-in-winui-calendar-date-picker](Getting-Started_images/date-picker-with-description-in-winui-calendar-date-picker.png)


## Setting watermark text

You can prompt the user with some information by using the [PlaceholderText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_PlaceholderText) property. This will be displayed only when the `Calendar Date Picker` contains the `SelectedDate` property as `null` and `AllowNull` property as `true`. If `AllowNull` property is `false`, then the current system date is updated in `SelectedDate` property and displayed instead of `PlaceholderText`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4" %}

<calendar:SfCalendarDatePicker Name="sfCalendarDatePicker" 
                               PlaceholderText="Select the Date"
                               SelectedDate="{x:Null}"
                               AllowNull="True"
                                />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2 3 4" %}

SfCalendarDatePicker sfCalendarDatePicker= new SfCalendarDatePicker();
sfCalendarDatePicker.PlaceholderText = "Select the Date";
sfCalendarDatePicker.SelectedDate = null;
sfCalendarDatePicker.AllowNull = true;

{% endhighlight %}
{% endtabs %}

![date-range-picker-with-water-mark-text-in-winui-calendar-date-range-picker](Getting-Started_images/date-range-picker-with-water-mark-text-in-winui-calendar-date-range-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection)

## Selection changed notification

You will be notified when selected date is changed in `Calendar Date Picker` by using the [SelectedDateChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectedDateChanged) event. The `SelectedDateChanged` event contains the old and newly selected date in the [OldDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SelectedDateChangedEventArgs.html#Syncfusion_UI_Xaml_Calendar_SelectedDateChangedEventArgs_OldDate) and [NewDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SelectedDateChangedEventArgs.html#Syncfusion_UI_Xaml_Calendar_SelectedDateChangedEventArgs_NewDate) properties.

* `OldDate` - Gets a date, which is previously selected.
* `NewDate` - Gets a date, which is currently selected.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendarDatePicker Name="sfCalendarDatePicker" 
                               SelectedDateChanged="SfCalendarDatePicker_SelectedDateChanged" 
                               />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.SelectedDateChanged += SfCalendarDatePicker_SelectedDateChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

private void SfCalendarDatePicker_SelectedDateChanged(object sender, SelectedDateChangedEventArgs e)
{
    var oldDate = e.OldDate;
    var newDate = e.NewDate;
}

{% endhighlight %}
{% endtabs %}

## Edit date using free form editing

Since, the default value of `EditMode` property is **Mask**, each input numbers entered in editor are automatically validated with the `DisplayDateFormat`'s formats and the proper value is assigned in current field. Then, focus will move to next input field of the date format.

If you want to perform the validation after the user completely entered their date inputs, set the [EditMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_EditMode) property value as **Normal**. Then, the entered date value is validated with the `DisplayDateFormat` property value by pressing the `Enter` key or lost focus. If the entered value does not suit the `DisplayDateFormat` property, the previously selected date value is set to the `SelectedDate` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker" 
                               EditMode="Normal"
                               />

{% endhighlight  %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.EditMode = DateTimeEditMode.Normal;

{% endhighlight  %}
{% endtabs %}

![date-picker-with-editing-in-winui-calendar-date-picker](Getting-Started_images/date-picker-with-editing-in-winui-calendar-date-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection).

## Cancel a date that is being changed

The `SelectedDateChanging` event will be triggered as soon as a date is selected but before the `SelectedDate` property is updated. If the change is considered invalid, it can be canceled. The `SelectedDateChanging` event contains the following properties:

* `OldDate` - Gets a date, which is previously selected.
* `NewDate` - Gets a date, which is currently selected.
* `Cancel` - Gets or sets whether to cancel the selected date value update.

Users are restricted to select a blackout date from a drop-down menu, but you can provide text input by the editor. Because selecting a blackout date leads to crash, you can cancel the change using the `SelectedDateChanging` event.

N> `SelectedDateChanging` event is called before the `SelectedDateChanged` event, when a date is selected.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<calendar:SfCalendarDatePicker Height="30" Width="250" 
                               x:Name="SfCalendarDatePicker"
                               SelectedDateChanging="SfCalendarDatePicker_DateChanging" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.SelectedDateChanging += SfCalendarDatePicker_DateChanging;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# tabtitle="MainWindow.xaml.cs" %}

 private void SfCalendarDatePicker_DateChanging(object sender, Syncfusion.UI.Xaml.Editors.DateChangingEventArgs e)
{
    var OldDate = e.OldDate;
    var NewDate = e.NewDate;

    //Cancel Selected date update
    e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

## Hide the drop-down button

You can hide the drop-down button in `Calendar Date Picker` by setting the [ShowDropDownButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowDropDownButton) property value as **false**. The default value of `ShowDropDownButton` property is **true**.

N> When the drop-down button is hidden, you can still open the drop-down calendar using **ALT + DownArrow** keyboard shortcut.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<calendar:SfCalendarDatePicker 
                               x:Name="sfCalendarDatePicker"
                               ShowDropDownButton="False"  />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowDropDownButton = false;

{% endhighlight %}
{% endtabs %}

![show-or-hide-drop-down-button-in-winui-calendar-date-range-picker](Dropdown-Calendar_images/show-or-hide-drop-down-button-in-winui-calendar-date-range-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown).

## Show submit button

If you want to select the date from drop-down calendar only by clicking the **Ok** button, use the [ShowSubmitButtons](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowSubmitButtons) property value as **true**. The default value of `ShowSubmitButtons` property is **false**.

N> When the submit buttons are hidden, `SelectedDate` property will be updated as soon you choose start and end date from the drop-down.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<calendar:SfCalendarDatePicker 
                               x:Name="sfCalendarDatePicker"
                               ShowSubmitButtons="true" />

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowSubmitButtons = true;

{% endhighlight %}
{% endtabs %}

![show-or-hide-submit-buttons-in-winui-calendar-date-range-picker](Dropdown-Calendar_images/show-or-hide-submit-buttons-in-winui-calendar-date-range-picker.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown).

## Restrict selection

You can restrict users from:
* Selecting a date within a specific minimum and maximum range using [`MinDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MinDate) and [`MaxDate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MaxDate) properties.
* Selecting a date from blocked dates using [`BlackoutDates`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_BlackoutDates) property.
* Selecting a date from specifically blocked set of dates (example : blocking weekend dates) using [`ItemPrepared`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_ItemPrepared) event. 

For further details, refer [Date Selection and Restriction](date-selection-and-restriction).

## Navigation between views

* You can navigate between month, year, decade, and century views in `Calendar Date Picker` control.
* You can also restrict the users to navigate between specific views only (month and year selection for credit card) using [`MinDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MinDisplayMode) and [`MaxDisplayMode`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_MaxDisplayMode) properties.

![view-navigation-in-winui-calendar-date-range-picker](Getting-Started_images/view-navigation-in-winui-calendar-date-range-picker.gif)

For further details, refer [Navigation](navigation).