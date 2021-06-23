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

You can show week numbers for each week in the dropdown calendar of `Calendar Date Picker` control by setting the value of `ShowWeekNumbers` property as **true**. You can also customize the week number displayed in calendar by using the`WeekNumberRule` property and `WeekNumberFormat` property. By default, the value of `ShowWeekNumber` property is **false**, `WeekNumberRule` is **FirstDay** and `WeekNumberFormat` is **#**.

N> You can change the `WeekNumberRule` property value with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) and you can also add any prefix or suffix characters to **#** for `WeekNumberFormat` property.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True"
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker showing week number based on weeknumber rule](Week_Numbers_images/winui-calendardatepicker-show-weeknumber.png)

## Week rule

You can apply different rules for determining the first week of the year in the dropdown calendar of `Calendar Date Picker` control using the `WeekNumberRule` property. The default value of `WeekNumberRule` property is **FirstDay**.

N> You can change the `WeekNumberRule` property value with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) 

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True" WeekNumberRule="FirstFullWeek"
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;
sfCalendarDatePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker showing week number based on weeknumber rule](Week_Numbers_images/winui-calendardatepicker-week-rule.png)

## Format week numbers

You can customize the format in which week numbers are displayed in the dropdown calendar of `Calendar Date Picker` control using `WeekNumberFormat` property. The default value of `WeekNumberFormat` property is **#**.

N> You can add any prefix or suffix characters to **#** in `WeekNumberFormat` property to apply different custom formats.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True" WeekNumberRule="FirstFullWeek"
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;
sfCalendarDatePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker apply week number format](Week_Numbers_images/winui-calendardatepicker-custom-format.png)

## Customize the week number appearance

You can show week number in `Calendar Date Picker` control by setting the value of `ShowWeekNumbers` property  as **true**.
`Calendar Date Picker` control also allows you to customize the template of the week numbers using `WeekNumberTemplate` property in `CalendarItemTemplateSelector` class. The default value of `ShowWeekNumbers` property is **false**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                            HorizontalAlignment="Center" VerticalAlignment="Center" ShowWeekNumbers="True"
                            WeekNumberFormat="W #" WeekNumberRule="FirstFullWeek"
                            >
    <FlyoutBase.AttachedFlyout>
        <editors:DropDownFlyout>
            <calendar:SfCalendar >
                <calendar:SfCalendar.Resources>
                    <Style TargetType="calendar:CalendarItem">
                        <Setter Property="ContentTemplateSelector">
                            <Setter.Value>
                                <calendar:CalendarItemTemplateSelector>
                                    <calendar:CalendarItemTemplateSelector.WeekNumberTemplate>
                                        <DataTemplate>
                                            <TextBlock Text="{Binding DisplayText}" FontWeight="Bold" Foreground="Red"/>
                                        </DataTemplate>
                                    </calendar:CalendarItemTemplateSelector.WeekNumberTemplate>
                                </calendar:CalendarItemTemplateSelector>
                            </Setter.Value>
                        </Setter>
                    </Style>
                </calendar:SfCalendar.Resources>
            </calendar:SfCalendar>
        </editors:DropDownFlyout>
    </FlyoutBase.AttachedFlyout>
</calendar:SfCalendarDatePicker>

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker change week number template](UI-Customization_images/winui-calendar-datepicker-weeknumbertemplate.png)

## Customize the week day name appearance

`Calendar Date Picker` control allows you to customize the template of the week day names using `WeekNameTemplate` property in `CalendarItemTemplateSelector` class. 

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker"
                            HorizontalAlignment="Center" VerticalAlignment="Center"  
                            >
    <FlyoutBase.AttachedFlyout>
        <editors:DropDownFlyout>
            <calendar:SfCalendar >
                <calendar:SfCalendar.Resources>
                    <Style TargetType="calendar:CalendarItem">
                        <Setter Property="ContentTemplateSelector">
                            <Setter.Value>
                                <calendar:CalendarItemTemplateSelector>
                                    <calendar:CalendarItemTemplateSelector.WeekNameTemplate>
                                        <DataTemplate>
                                            <TextBlock Text="{Binding DisplayText}" FontWeight="Bold" Foreground="Red"/>
                                        </DataTemplate>
                                    </calendar:CalendarItemTemplateSelector.WeekNameTemplate>
                                </calendar:CalendarItemTemplateSelector>
                            </Setter.Value>
                        </Setter>
                    </Style>
                </calendar:SfCalendar.Resources>
            </calendar:SfCalendar>
        </editors:DropDownFlyout>
    </FlyoutBase.AttachedFlyout>
</calendar:SfCalendarDatePicker>

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker change week dayname template](UI-Customization_images/winui-calendar-datepicker-weeknametemplate.png)