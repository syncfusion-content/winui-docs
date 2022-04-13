---
layout: post
title: Week numbers in WinUI Calendar Date Picker control | Syncfusion
description: Learn here all about week number feature of the WinUI Calendar Date Picker (SfCalendarDatePicker) control and much more.
platform: WinUI
control: SfCalendarDatePicker
documentation: ug
---

# Week number of the WinUI Calendar Date Picker (SfCalendarDatePicker)

This section describes about the week number in [Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html) control.

## Enable week numbers

You can show week numbers for each week in the dropdown calendar of [Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html)  control by setting the value of [ShowWeekNumbers](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_ShowWeekNumbers) property as **true**. By default, the value of `ShowWeekNumber` property is **false**.

N> You can change the value of [WeekNumberRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_WeekNumberRule) property with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) and you can also add any prefix or suffix characters to **#** for `WeekNumberFormat` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="4" %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center" 
                               VerticalAlignment="Center"
                               ShowWeekNumbers="True" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;

{% endhighlight %}
{% endtabs %}

![show-week-number-in-winui-calendar-date-picker](Week_Numbers_images/show-week-number-in-winui-calendar-date-picker.png)

## Week rule

You can change the rule for determining the first week of the year in the dropdown calendar of the [Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html)  control using the [WeekNumberRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_WeekNumberRule) property. The default value of the `WeekNumberRule` property is **FirstDay**. You can apply any one of the below rules to the `WeekNumberRule` property.

* **FirstDay** - Indicates that the first week of the year begins on the first day of the year and ends before the following designated first day of the week.

* **FirstFourDayWeek** - Indicates that the first week of the year is the first week with four or more days before the designated first day of the week.

* **FirstFullWeek** - Indicates that the first week of the year begins on the first occurrence of the designated first day of the week on or after the first day of the year.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="4 5" %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center" 
                               VerticalAlignment="Center"
                               ShowWeekNumbers="True" 
                               WeekNumberRule="FirstFullWeek" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3 4" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;
sfCalendarDatePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![show-week-number-with-rrule-in-winui-calendar-date-picker](Week_Numbers_images/show-week-number-with-rrule-in-winui-calendar-date-picker.png)

## Format week numbers

You can customize the format in which week numbers are displayed in the dropdown calendar of [Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html)  control using [WeekNumberFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_WeekNumberFormat) property. The default value of `WeekNumberFormat` property is **#**.

N> You can add any prefix or suffix characters to **#** in `WeekNumberFormat` property to apply different custom formats.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="4 5 6" %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center"
                               VerticalAlignment="Center"
                               ShowWeekNumbers="True" 
                               WeekNumberRule="FirstFullWeek"
                               WeekNumberFormat = "W #" />

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3 4 5" %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;
sfCalendarDatePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;
sfCalendarDatePicker.WeekNumberFormat = "W #";

{% endhighlight %}
{% endtabs %}

![show-week-number-with-format-in-winui-calendar-date-picker](Week_Numbers_images/show-week-number-with-format-in-winui-calendar-date-picker.png)

## Customize the week number and name of days of the week appearance

[Calendar Date Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html)  control allows you to customize the template of the week numbers using [WeekNumberTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemTemplateSelector.html#Syncfusion_UI_Xaml_Calendar_CalendarItemTemplateSelector_WeekNumberTemplate) property and the template of name of days of the week using [WeekNameTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemTemplateSelector.html#Syncfusion_UI_Xaml_Calendar_CalendarItemTemplateSelector_WeekNameTemplate) property in the `CalendarItemTemplateSelector` class. 

In below codes we have created a `DataTemplate` for both `WeekNumberTemplate` and `WeekNameTemplate` properties in `CalendarItemTemplateSelector` class.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" %}

<Grid>
    <Grid.Resources>
        <DataTemplate x:Key="WeekNameAndNumberTemplate">
            <Viewbox >
                <Grid>
                    <Ellipse Width="30" 
                                Height="30" 
                                Fill="White"
                                HorizontalAlignment="Center" VerticalAlignment="Center"
                                Margin="1" />
                    <TextBlock Text="{Binding DisplayText}" 
                                HorizontalAlignment="Center"
                                VerticalAlignment="Center" 
                                Foreground="DeepSkyBlue"/>
                </Grid>
            </Viewbox>
        </DataTemplate>
    </Grid.Resources>
    <calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                                   HorizontalAlignment="Center" VerticalAlignment="Center" ShowWeekNumbers="True"
                                   >
        <FlyoutBase.AttachedFlyout>
            <editors:DropDownFlyout>
                <calendar:SfCalendar WeekNumberRule="FirstFourDayWeek"
                    ShowWeekNumbers="True">
                    <calendar:SfCalendar.Resources>
                        <Style TargetType="calendar:CalendarItem">
                            <Setter Property="ContentTemplateSelector">
                                <Setter.Value>
                                    <calendar:CalendarItemTemplateSelector WeekNameTemplate="{StaticResource WeekNameAndNumberTemplate}" 
                                                                WeekNumberTemplate="{StaticResource WeekNameAndNumberTemplate}" />
                                </Setter.Value>
                            </Setter>
                        </Style>
                    </calendar:SfCalendar.Resources>
                </calendar:SfCalendar>
            </editors:DropDownFlyout>
        </FlyoutBase.AttachedFlyout>
    </calendar:SfCalendarDatePicker>
</Grid>

{% endhighlight %}
{% endtabs %}