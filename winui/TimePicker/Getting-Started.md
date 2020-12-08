---
layout: post
title: Getting started with WinUI SfTimePicker control | Syncfusion
description: This section describes about how to add the SfTimePicker control into WinUI application and its basic features.
platform: WinUI
control: SfBadge
documentation: ug
---

# Getting Started with WinUI TimePicker (SfTimePicker)

This section explains the steps required to add the [TimePicker]() control and its time selection options. This section covers only basic features needed to get started with Syncfusion `TimePicker` control.

## Structure of TimePicker control

![Structure of WinUI TimePicker control](Getting-Started_images/Structure.png)

## Creating an application with WinUI TimePicker

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.
2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the `SfTimePicker` control.

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
        <!--Adding TimePicker control -->
        <syncfusion:SfTimePicker Name="timePicker"/>
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
            // Creating an instance of the TimePicker control
            SfTimePicker sfTimePicker = new SfTimePicker();

            grid.Children.Add(sfTimePicker);
        }
    }
}

{% endhighlight %}
{% endtabs %}

![SfTimePicker control added in the application](Getting-Started_images/TimePicker_Added.jpg)

N> Download demo application from [GitHub]()

## Select the time programmatically

You can set or change the selected time programmatically by using [SelectedTime]() property. If you not assign any value for the `SelectedTime` property, `TimePicker` will automatically assign the current system time as `SelectedTime`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker SelectedTime=""
                         Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = new DateTimeOffset(new DateTime(2021, 10, 29));

{% endhighlight %}
{% endtabs %}

![SfTimePicker displaying the selected time](Getting-Started_images/SelectedTime.png)

N> Download demo application from [GitHub]()

## Select time interactively

You can change the selected time interactively by enter the time value using keyboard or from the drop down time spinner. You can get the selected time from the `SelectedTime` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();

{% endhighlight %}
{% endtabs %}

![SfTimePicker displaying selected value](Getting-Started_images/selectedTime.gif)

N> Download demo application from [GitHub]()

## Setting null value

If you want to set null value for the `TimePicker`, set the [AllowNullValue]() property as `true` and [SelectedTime]() property as `null`. If `AllowNullValue` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `null`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker SelectedTime="{x:Null}"
                         AllowNullValue="True"
                         Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![SfTimePicker displaying the null value](Getting-Started_images/AllowNullValue.png)

N> Download demo application from [GitHub]()

## Setting WaterMark text

You can prompt the user with some information by using the [PlaceHolderText]() property. This will dispaly only on when the `TimePicker` contains the `SelectedTime` property as `null` and `AllowNullValue` property as `true`. If `AllowNullValue` property is `false`, then the current system time is updated in `SelectedTime` property and displayed instead of `PlaceHolderText`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker PlaceHolderText="Select the Time"
                         SelectedTime="{x:Null}"
                         AllowNullValue="True"
                         Name="sfTimePicker" />

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker= new SfTimePicker();
sfTimePicker.PlaceHolderText = "Select the Time";
sfTimePicker.SelectedTime = null;
sfTimePicker.AllowNullValue = true;

{% endhighlight %}
{% endtabs %}

![SfTimePicker displaying watermark text](Getting-Started_images/PlaceHolderText.png)

N> Download demo application from [GitHub]()

## Time changed notification

You will be notified when selected time changed in `TimePicker` by using [TimeChanged]() event. The `TimeChanged` event contains the old and newly selected time in the [OldDateTime](), [NewDateTime]() properties.

* `OldDateTime` - Gets a time which is previously selected.
* `NewDateTime` - Gets a time which is currently selected.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfTimePicker TimeChanged="SfTimePicker_TimeChanged" 
                         Name="sfTimePicker"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.TimeChanged += SfTimePicker_TimeChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfTimePicker_TimeChanged(DependencyObject d, DependencyPropertyChangedEventArgs e) {          
    Console.WriteLine("The previously selected Time: " + e.OldDateTime.ToString());
    Console.WriteLine("The newly selected Time: " + e.NewDateTime.ToString());            
}

{% endhighlight %}
{% endtabs %}

## Change time display format

 You can edit and display the selected time with various formatting like hour, minutes, seconds and meridiem formats by using the [FormatString]() property. The default value of `FormatString` property is `hh tt`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker x:Name="sfTimePicker" 
                         FormatString="hh tt"/>

{% endhighlight %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.FormatString= "hh tt";

{% endhighlight %}
{% endtabs %}

![SfTimePicker selected time with hour and meridiem](Features_images/FormatString.png)

N> Download demo application from [GitHub]()

## Change time format for Spinner

You can allow the user to select the pair of hour, minutes, seconds and meridiem spinner or any single spinner cell from the drop down time spinner by using the [DropdownFormatString]() property. The default value of `DropdownFormatString` property is `hh:mm tt`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker x:Name="sfTimePicker" 
                         DropdownFormatString="hh tt"/>

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.DropdownFormatString = "hh tt";

{% endhighlight  %}
{% endtabs %}

![SfTimePicker contains only drop down hour and meridiem spinner](Features_images/DropdownFormatString.png)

Here, you can only able to select the hour and meridiem value from the drop down spinner.

N> Download demo application from [GitHub]()

## Restrict time selection

You can restrict the users from selecting a time within the particular range by specifying [MinTime]() and [MaxTime]() properties in `TimePicker` control. The default value of `MinTime` property is `1/1/0001 12:00:00 AM` and `MaxTime` property is `12/31/9999 11:59:59 PM`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker x:Name="sfTimePicker" 
                         MinTime=""
                         MaxTime=""/>

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.MinTime = new DateTimeOffset(new DateTime(2020,12,10,00,00,00));
sfTimePicker.MaxTime = new DateTimeOffset(new DateTime(2020,12,10,11,59,59));

{% endhighlight  %}
{% endtabs %}

![SfTimePicker restrict the time selection with particular range](Features_images/MinDMinTimeate.png)

## Block times using BlackoutTimes

If you want to block particular times from the time selection, add that time ranges to the [BlackoutTimes]() collection. You can add more block out time ranges to the `BlackoutTimes` collection.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker x:Name="sfTimePicker"/>

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();


{% endhighlight  %}
{% endtabs %}

![SfTimePicker blocks the particular times from selection](Features_images/BlackoutTimes.png)

## Edit time using free form editing

If you want to perform the validation after the user completely entering their time inputs, use the [EditMode]() property value as `Normal`. Then the entered time value is validated with the `FormatString` property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the selected time will be set as default format value.

By default, the user entering each input numbers are automatically validated with the `FormatString` formats and assigned the proper value for it, then it will move to next input part of the time format.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker EditMode="Normal"
                         x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.EditMode = DateTimeEditingMode.Normal;

{% endhighlight  %}
{% endtabs %}

![SfTimePicker enables free form editing to select time](Features_images/Normal.png)

## Restrict time selection by editing

You can restrict the time selection during editing by using the `EditMode` property value as `None`. Then, you can change the time only using drop down time spinner. The default value of `EditMode` property is `Mask`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker EditMode="None"
                         x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.EditMode = DateTimeEditingMode.None;

{% endhighlight  %}
{% endtabs %}

![SfTimePicker restrict time selection from editing](Features_images/None.png)

## Curved border for TimePicker

If you want to create curved borders for the `TimePicker`, use the [CornerRadius]() property. The default value of `CornerRadius` property is `0,0,0,0`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfTimePicker CornerRadius="10"
                         x:Name="sfTimePicker" />

{% endhighlight  %}
{% highlight C# %}

SfTimePicker sfTimePicker = new SfTimePicker();
sfTimePicker.CornerRadius = new CornerRadius() {
    BottomLeft=10, 
    TopLeft=10, 
    BottomRight=10, 
    TopRight=10 };

{% endhighlight  %}
{% endtabs %}

![SfTimePicker with curved border](Features_images/CornerRadius.png)
