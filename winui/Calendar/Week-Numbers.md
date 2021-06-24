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

You can show week numbers for each week in `Calendar` control by setting the value of `ShowWeekNumbers` property as **true**. You can also customize the week number displayed in calendar by using the`WeekNumberRule` property and `WeekNumberFormat` property. By default, the value of `ShowWeekNumber` property is **false**, `WeekNumberRule` is **FirstDay** and `WeekNumberFormat` is **#**.

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

You can apply different rules for determining the first week of the year in `Calendar` control using the `WeekNumberRule` property. The default value of `WeekNumberRule` property is **FirstDay**.

N> You can change the `WeekNumberRule` property value with the [CalendarWeekRule](https://docs.microsoft.com/en-us/dotnet/api/system.globalization.calendarweekrule?view=net-5.0) 

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
                     />

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.ShowWeekNumbers = true;
sfCalendar.WeekNumberRule = CalendarWeekRule.FirstFullWeek;

{% endhighlight %}
{% endtabs %}

![WinUI Calendar apply week number format](Week_Numbers_images/winui-calendar-weeknumber-format.png)

## Customize the week number and name of days of the week appearance

You can show week number in `Calendar` control by setting the value of `ShowWeekNumbers` property  as **true**.
`Calendar` control also allows you to customize the template of the week numbers using `WeekNumberTemplate` property and template of name of days of the week using `WeekNameTemplate` property in the `CalendarItemTemplateSelector` class. The default value of `ShowWeekNumbers` property is **false**.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar WeekNumberRule="FirstFourDayWeek"
                     ShowWeekNumbers="True">
                    <calendar:SfCalendar.Resources>
                        <Style TargetType="calendar:CalendarItem">
                            <Setter Property="ContentTemplateSelector">
                                <Setter.Value>
                                    <calendar:CalendarItemTemplateSelector>
                                        <calendar:CalendarItemTemplateSelector.WeekNumberTemplate>
                                            <DataTemplate>
                                            <Viewbox >
                                                <Grid>
                                                <Ellipse MinWidth="30" MinHeight="30" Fill="WhiteSmoke"
                                                            HorizontalAlignment="Center" VerticalAlignment="Center"
                                                            Margin="1"/>
                                                <TextBlock Text="{Binding DisplayText}" HorizontalAlignment="Center"
                                                            VerticalAlignment="Center" Foreground="DeepSkyBlue"/>
                                                </Grid>
                                            </Viewbox>
                                            </DataTemplate>
                                            </calendar:CalendarItemTemplateSelector.WeekNumberTemplate>
                                        <calendar:CalendarItemTemplateSelector.WeekNameTemplate>
                                            <DataTemplate>
                                                <Viewbox>
                                                    <Grid>
                                                        <Ellipse MinWidth="30" MinHeight="30" Fill="WhiteSmoke"
                                                                HorizontalAlignment="Center" VerticalAlignment="Center"
                                                                Margin="1"/>
                                                        <TextBlock Text="{Binding DisplayText}"  HorizontalAlignment="Center"
                                                                VerticalAlignment="Center" Foreground="DeepSkyBlue"/>
                                                    </Grid>
                                                </Viewbox>
                                            </DataTemplate>
                                        </calendar:CalendarItemTemplateSelector.WeekNameTemplate>
                                </calendar:CalendarItemTemplateSelector>
                            </Setter.Value>
                        </Setter>
                    </Style>
                    </calendar:SfCalendar.Resources>
</calendar:SfCalendar>

{% endhighlight %}
{% endtabs %}

![WinUI Calendar change week number template](Week_Numbers_images/winui-calendar-weeknumber-weekname-template.png)
