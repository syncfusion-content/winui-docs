---
layout: post
title: Week numbers in WinUI Calendar control | Syncfusion
description: Learn here all about the week number features of the WinUI Calendar (SfCalendar) control and much more.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Week number of the WinUI Calendar (SfCalendar)

This section describes about the various customization options available in [Calendar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html) control.

## Enable week numbers

You can show the week numbers for each week in `Calendar` control by setting the value of `ShowWeekNumbers` property as **true**. You can also customize the week number displayed in calendar by using the `WeekNumberRule` property and `WeekNumberFormat` property. By default, the value of `ShowWeekNumber` property is **false**, `WeekNumberRule` is **FirstDay** and `WeekNumberFormat` is **#**.

N> You can change the `WeekNumberRule` property value with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) and you can also add any prefix or suffix characters to **#** for `WeekNumberFormat` property.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True"
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.ShowWeekNumbers = true;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar showing week number based on weeknumber rule](Week_Numbers_images/winui-calendar-show-weeknumbers.png)

## Week rule

You can change the rule for determining the first week of the year in `Calendar` control using the `WeekNumberRule` property. The default value of the `WeekNumberRule` property is **FirstDay**. You can apply any one of the below rules to `WeekNumberRule` property.

* **FirstDay** - Indicates that the first week of the year begins on the first day of the year and ends before the following designated first day of the week.

* **FirstFourDayWeek** - Indicates that the first week of the year is the first week with four or more days before the designated first day of the week.

* **FirstFullWeek** - Indicates that the first week of the year begins on the first occurrence of the designated first day of the week on or after the first day of the year.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True" WeekNumberRule="FirstFullWeek"
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.ShowWeekNumbers = true;
sfCalendar.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar showing week number based on week number rule](Week_Numbers_images/winui-calendar-week-numberrule.png)

## Format week numbers

You can customize the format in which week numbers are displayed in `Calendar` control using `WeekNumberFormat` property. The default value of `WeekNumberFormat` property is **#**.

N> You can add any prefix or suffix characters to **#** in `WeekNumberFormat` property to apply different custom formats.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar HorizontalAlignment="Center" VerticalAlignment="Center"
                     ShowWeekNumbers="True" WeekNumberRule="FirstFullWeek"
                     WeekNumberFormat = "W #" />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.ShowWeekNumbers = true;
sfCalendar.WeekNumberRule = CalendarWeekRule.FirstFullWeek;
sfCalendar.WeekNumberFormat = "W #";

{% endhighlight %}
{% endtabs %}

![WinUI Calendar apply week number format](Week_Numbers_images/winui-calendar-weeknumber-format.png)

## Customize the week number and name of days of the week appearance

`Calendar` control also allows you to customize the template of the week numbers using `WeekNumberTemplate` property and the template of name of days of the week using `WeekNameTemplate` property in the `CalendarItemTemplateSelector` class. 

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
                                Fill="WhiteSmoke"
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
</Grid>

{% endhighlight %}
{% endtabs %}

![WinUI Calendar change week number template](Week_Numbers_images/winui-calendar-weeknumber-weekname-template.png)
