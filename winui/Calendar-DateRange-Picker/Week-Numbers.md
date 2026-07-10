---
layout: post
title: Week numbers in WinUI Calendar DateRange Picker control | Syncfusion
description: Learn here all about week numbers feature of the WinUI Calendar DateRange Picker (SfCalendarDateRangePicker) control and much more.
platform: WinUI
control: SfCalendarDateRangePicker
documentation: ug
---

# Week numbers of the WinUI Calendar DateRange Picker

This section describes about the week numbers in the [Calendar DateRange Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html) control.

## Enable week numbers

You can show week numbers for each week in the drop-down calendar of the [Calendar DateRange Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html) control by setting the value of the [ShowWeekNumbers](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_ShowWeekNumbers) property to **true**. By default, the value of the `ShowWeekNumbers` property is **false**.

N> You can change the value of the [WeekNumberRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_WeekNumberRule) property with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) and you can also add any prefix or suffix characters to **#** for the `WeekNumberFormat` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar">
    <calendar:SfCalendarDateRangePicker HorizontalAlignment="Center"
                                        VerticalAlignment="Center"
                                        ShowWeekNumbers="True"
                                        />
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="4" %}

using Syncfusion.UI.Xaml.Calendar;

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.ShowWeekNumbers = true;

{% endhighlight %}
{% endtabs %}

![show-week-number-in-winui-calendar-date-range-picker](Images/week_numbers/show-week-number-in-winui-calendar-date-range-picker.png)

## Week rule

You can change the rule for determining the first week of the year in the drop-down calendar of the [Calendar DateRange Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html) control using the [WeekNumberRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_WeekNumberRule) property. The default value of the `WeekNumberRule` property is **FirstDay** and you can also apply any one of the following rules to the `WeekNumberRule` property:

* **FirstDay** - Indicates that the first week of the year begins on the first day of the year and ends before the following designated first day of the week.

* **FirstFourDayWeek** - Indicates that the first week of the year is the first week with four or more days before the designated first day of the week.

* **FirstFullWeek** - Indicates that the first week of the year begins on the first occurrence of the designated first day of the week on or after the first day of the year.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6 7" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar">
    <calendar:SfCalendarDateRangePicker HorizontalAlignment="Center"
                                        VerticalAlignment="Center"
                                        ShowWeekNumbers="True"
                                        WeekNumberRule="FirstFullWeek" />
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="4 5" %}

using Syncfusion.UI.Xaml.Calendar;

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.ShowWeekNumbers = true;
sfCalendarDateRangePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![show-week-number-with-rrule-in-winui-calendar-date-range-picker](Images/week_numbers/show-week-number-with-rrule-in-winui-calendar-date-range-picker.png)

## Format week numbers

You can customize the format in which week numbers are displayed in the drop-down calendar of the [Calendar DateRange Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html) control using the [WeekNumberFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDateRangePicker_WeekNumberFormat) property. The default value of the `WeekNumberFormat` property is **#**.

N> You can add any prefix or suffix characters to **#** in the `WeekNumberFormat` property to apply different custom formats.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6 7 8" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar">
    <calendar:SfCalendarDateRangePicker HorizontalAlignment="Center"
                                        VerticalAlignment="Center"
                                        ShowWeekNumbers="True"
                                        WeekNumberRule="FirstFullWeek"
                                        WeekNumberFormat = "W #" />
</Window>

{% endhighlight %}
{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="4 5 6" %}

using Syncfusion.UI.Xaml.Calendar;

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.ShowWeekNumbers = true;
sfCalendarDateRangePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;
sfCalendarDateRangePicker.WeekNumberFormat = "W #";

{% endhighlight %}
{% endtabs %}

![show-week-number-with-format-in-winui-calendar-date-range-picker](Images/week_numbers/show-week-number-with-format-in-winui-calendar-date-range-picker.png)

## Customize the week numbers and name of days of the week appearance

The [Calendar DateRange Picker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDateRangePicker.html) control allows you to customize the template of the week numbers using the [WeekNumberTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemTemplateSelector.html#Syncfusion_UI_Xaml_Calendar_CalendarItemTemplateSelector_WeekNumberTemplate) property and the template of the name of days of the week using the [WeekNameTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItemTemplateSelector.html#Syncfusion_UI_Xaml_Calendar_CalendarItemTemplateSelector_WeekNameTemplate) property in the `CalendarItemTemplateSelector` class. 

In the following code, a `DataTemplate` is created for both the `WeekNumberTemplate` and `WeekNameTemplate` properties in the `CalendarItemTemplateSelector` class.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="3" %}

<Window
    ...
     xmlns:calendar="using:Syncfusion.UI.Xaml.Calendar"
     xmlns:editors="using:Syncfusion.UI.Xaml.Editors">
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
    <calendar:SfCalendarDateRangePicker x:Name="sfCalendarDateRangePicker"
                                        HorizontalAlignment="Center" VerticalAlignment="Center" ShowWeekNumbers="True"
                                        WeekNumberRule="FirstFullWeek"
                                        >
        <FlyoutBase.AttachedFlyout>
            <editors:DropDownFlyout>
                <calendar:SfCalendar ShowWeekNumbers="{x:Bind sfCalendarDateRangePicker.ShowWeekNumbers,Mode=TwoWay}" >
                    <calendar:SfCalendar.Resources>
                        <Style TargetType="calendar:CalendarItem">
                            <Setter Property="ContentTemplateSelector">
                                <Setter.Value>
                                    <calendar:CalendarItemTemplateSelector WeekNameTemplate="{StaticResource WeekNameAndNumberTemplate}"
                                                                           WeekNumberTemplate="{StaticResource WeekNameAndNumberTemplate}"
                                                                           />
                                </Setter.Value>
                            </Setter>
                        </Style>
                    </calendar:SfCalendar.Resources>
                </calendar:SfCalendar>
            </editors:DropDownFlyout>
        </FlyoutBase.AttachedFlyout>
    </calendar:SfCalendarDateRangePicker>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %}