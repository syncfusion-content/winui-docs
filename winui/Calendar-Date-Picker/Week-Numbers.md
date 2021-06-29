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

You can show week numbers for each week in the dropdown calendar of `Calendar Date Picker` control by setting the value of `ShowWeekNumbers` property as **true**. You can also customize the week number displayed in calendar by using the `WeekNumberRule` property and `WeekNumberFormat` property. By default, the value of `ShowWeekNumber` property is **false**, `WeekNumberRule` is **FirstDay** and `WeekNumberFormat` is **#**.

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

You can change the rule for determining the first week of the year in the dropdown calendar of the `Calendar Date Picker` control using the `WeekNumberRule` property. The default value of the `WeekNumberRule` property is **FirstDay**. You can apply any one of the below rules to the `WeekNumberRule` property.

* **FirstDay** - Indicates that the first week of the year begins on the first day of the year and ends before the following designated first day of the week.

* **FirstFourDayWeek** - Indicates that the first week of the year is the first week with four or more days before the designated first day of the week.

* **FirstFullWeek** - Indicates that the first week of the year begins on the first occurrence of the designated first day of the week on or after the first day of the year.

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
                               WeekNumberFormat = "W #" />

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowWeekNumbers = true;
sfCalendarDatePicker.WeekNumberRule = CalendarWeekRule.FirstFullWeek;
sfCalendarDatePicker.WeekNumberFormat = "W #";

{% endhighlight %}
{% endtabs %}

![WinUI Calendar Date Picker apply week number format](Week_Numbers_images/winui-calendardatepicker-custom-format.png)

## Customize the week number and name of days of the week appearance

`Calendar Date Picker` control also allows you to customize the template of the week numbers using `WeekNumberTemplate` property and the template of name of days of the week using `WeekNameTemplate` property in the `CalendarItemTemplateSelector` class. 

In below codes we have created a `DataTemplate` for both `WeekNumberTemplate` and `WeekNameTemplate` properties in `CalendarItemTemplateSelector` class.

{% tabs %}
{% highlight XAML %}

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

![WinUI Calendar Date Picker change week number template](Week_Numbers_images/winui-calendardatepicker-weeknumber-weekname-template.png)

