---
layout: post
title: Getting Started with WinUI SfDatePicker control | Syncfusion
description: This section describes about how to add the SfDatePicker control into WinUI application and its basic features.
platform: WinUI
control: SfDatePicker
documentation: ug
---

# Getting Started with WinUI DatePicker (SfDatePicker)

This section explains the steps required to add the [DatePicker]() control and its date selection options. This section covers only basic features needed to get started with Syncfusion `DatePicker` control.

## Structure of DatePicker control

![Structure of WinUI DatePicker control](Getting-Started_images/Structure.png)

## Creating an application with WinUI DatePicker

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfDatePicker` control.

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
    <Grid Name="grid">
        <!--Adding DatePicker control -->
        <syncfusion:SfDatePicker Name="datePicker"/>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

using Syncfusion.UI.Xaml.Editors;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the DatePicker control
            SfDatePicker datePicker = new SfDatePicker();

            grid.Children.Add(datePicker);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![DatePicker control added in the application](Getting-Started_images/DatePicker_Added.jpg)

N> Download demo application from [GitHub]()

## Select the date programmatically

You can set or change the selected date by using [SelectedDate]() property. If you not assign any value for the `SelectedDate` property, `DatePicker` will automatically assign the current system date as `SelectedDate`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker SelectedDate="10/29/2021"
                         Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.SelectedDate = new DateTimeOffset(new DateTime(2021, 10, 29));

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying selected value](Getting-Started_images/selectedDate.png)

N> Download demo application from [GitHub]()

## Select date interactively

You can change the selected date interactively by enter the date value using keyboard or from the drop down date selector. You can get the selected date from the `SelectedDate` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying selected value](Getting-Started_images/selectedDate.png)

N> Download demo application from [GitHub]()

## Setting null value

If you want to set null value for the `DatePicker`, set the [AllowNullValue]() property as `true` and [SelectedDate]() property as `null`. If `AllowNullValue` property is `false`, then the current system date is updated in `SelectedDate` property and displayed instead of `null`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker SelectedDate="{x:Null}"
                         AllowNullValue="True"
                         Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.SelectedDate = null;
sfDatePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying null value](Getting-Started_images/AllowNullValue.png)

N> Download demo application from [GitHub]()

## Setting WaterMark text

You can prompt the user with some information by using the [PlaceHolderText]() property. This will dispaly only on when the `TimePicker` contains the `SelectedDate` property as `null` and `AllowNullValue` property as `true`. If `AllowNullValue` property is `false`, then the current system time is updated in `SelectedDate` property and displayed instead of `PlaceHolderText`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker PlaceHolderText="Select the Time"
                         SelectedDate="{x:Null}"
                         AllowNullValue="True"
                         Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.PlaceHolderText = "Select the Time";
sfDatePicker.SelectedDate = null;
sfDatePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying watermark text](Getting-Started_images/PlaceHolderText.png)

N> Download demo application from [GitHub]()

## Date changed notification

You will be notified when selected date changed in `SfDatePicker` by using [DateChanged]() event. The `DateChanged` event contains the old and newly selected date in the [OldDateTime](), [NewDateTime]() properties.

* OldDateTime - Gets a date which is previously selected.
* NewDateTime - Gets a date which is currently selected.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker DateChanged="SfDatePicker_DateChanged" 
                         Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DateChanged += SfDatePicker_DateChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfDatePicker_DateChanged(DependencyObject d, DependencyPropertyChangedEventArgs e) {          
    Console.WriteLine("The previously selected Date: " + e.OldDateTime.ToString());
    Console.WriteLine("The newly selected Date: " + e.NewDateTime.ToString());            
}

{% endhighlight %}
{% endtabs %}

## Change date display format

 You can edit and display the selected date with various formatting like date, month and year formats by using the [FormatString]() property. The default value of `FormatString` property is `d`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker x:Name="sfDatePicker" 
                         FormatString="MM/yyyy"/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.FormatString= "MM/yyyy";

{% endhighlight  %}
{% endtabs %}

![SfDatePicker selected date with month format](Features_images/Features_img1.png)

N> Download demo application from [GitHub]()

## Change date format for Spinner

You can allow the user to select the pair of date, month and year selector or any single selector cell from the drop down date selector by using the [DropdownFormatString]() property. The default value of `DropdownFormatString` property is `d`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker x:Name="sfDatePicker" 
                         DropdownFormatString="dd/MM"/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.DropdownFormatString = "dd/MM";

{% endhighlight  %}
{% endtabs %}

![SfDatePicker contains only date and month selector](Features_images/Features_img2.png)

Here, you can only able to select the date and month value from the drop down selector.

N> Download demo application from [GitHub]()

## Restrict date selection

You can restrict the users from selecting a date within the particular range by specifying [MinDate]() and [MaxDate]() properties in `DatePicker` control. The default value of `MinDate` property is `1/1/0001` and `MaxDate` property is `12/31/9999`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker x:Name="sfDatePicker" 
                         MinDate=""
                         MaxDate=""/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.MaxDate = new DateTimeOffset(new DateTime(2020,12,10));
sfDatePicker.MinDate = new DateTimeOffset(new DateTime(2020,12,14));

{% endhighlight  %}
{% endtabs %}

![SfDatePicker restrict the date selection with particular range](Features_images/MinDate.png)

## Block dates using BlackoutDates

If you want to block particular dates from the date selection, add that date ranges to the [BlackoutDates]() collection. You can add more block out date ranges to the `BlackoutDates` collection.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker x:Name="sfDatePicker" 
                         MinDate=""
                         MaxDate=""/>

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.MaxDate = new DateTimeOffset(new DateTime(2020,12,10));
sfDatePicker.MinDate = new DateTimeOffset(new DateTime(2020,12,14));

{% endhighlight  %}
{% endtabs %}

![SfDatePicker blocks the particular dates from selection](Features_images/BlackoutDates.png)

## Edit date using free form editing

If you want to perform the validation after the user completely entering their date inputs, use the [EditMode]() property value as `Normal`. Then the entered date value is validated with the `FormatString` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the selected date will be set as default format value.

By default, the user entering each input numbers are automatically validated with the `FormatString` formats and assigned the proper value for it, then it will move to next input part of the time format.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker EditMode="Normal"
                         x:Name="sfDatePicker" />

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditingMode.Normal;

{% endhighlight  %}
{% endtabs %}

![SfDatePicker enables free form editing to select date](Features_images/Normal.png)

## Restrict date selection by editing

You can restrict the date selection during editing by using the `EditMode` property value is `None`. Then, you can change the date only using drop down date selector. The default value of `EditMode` property is `Mask`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker EditMode="None"
                         x:Name="sfDatePicker" />

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.EditMode = DateTimeEditingMode.None;

{% endhighlight  %}
{% endtabs %}

![SfDatePicker restrict date selection from editing](Features_images/Normal.png)

## Curved border for DatePicker

If you want to create curved borders for the `DatePicker`, use the [CornerRadius]() property. The default value of `CornerRadius` property is `0,0,0,0`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker CornerRadius="10"
                         x:Name="sfDatePicker" />

{% endhighlight  %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.CornerRadius = new CornerRadius() {
    BottomLeft=10, 
    TopLeft=10, 
    BottomRight=10, 
    TopRight=10 };

{% endhighlight  %}
{% endtabs %}

![SfDatePicker with curved border](Features_images/CornerRadius.png)
