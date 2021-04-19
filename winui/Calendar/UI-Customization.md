---
layout: post
title: Customize the WinUI Calendar control | Syncfusion
description: This section describes about how to customize the Calendar (SfCalendar) control into WinUI application and its basic features.
platform: WinUI
control: SfCalendar
documentation: ug
---

# Customize the WinUI Calendar

This section describes about the various customization options available in [Calendar](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html) control.

## Custom UI for specific cell in Calendar

You can change the UI of specific cells in `Calendar` by using the [CalendarItem.ContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItem.html) property. The `DataContext` of `CalendarItem.ContentTemplate` is `Calendar`. 

{% tabs %}
{% highlight C# %}

public class CustomCalendarItemTemplateSelector : DataTemplateSelector
{
     public CustomCalendarItemTemplateSelector()
    {
            SpecialDates = new Dictionary<DateTimeOffset, string>();
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(1), "SingleEvent_1");
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(5), "DoubleEvent_1");
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(-2), "TripleEvent_2");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(1), "TripleEvent_1");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(5), "SingleEvent_2");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(7), "DoubleEvent_2");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(9), "SingleEvent_1");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(12), "TripleEvent_2");
            SpecialDates.Add(DateTimeOffset.Now.AddDays(-4), "DoubleEvent_1");
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(1), "DoubleEvent_3");
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(3), "SingleEvent_2");
            SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(-5), "DoubleEvent_2");
    }

    private Dictionary<DateTimeOffset, string> SpecialDates { get; set; }

    public DataTemplate DefaultTemplate { get; set; }
    public DataTemplate SingleEventTemplate_1 { get; set; }
    public DataTemplate SingleEventTemplate_2 { get; set; }
    public DataTemplate DoubleEventTemplate_1 { get; set; }
    public DataTemplate DoubleEventTemplate_2 { get; set; }
    public DataTemplate DoubleEventTemplate_3 { get; set; }
    public DataTemplate TripleEventTemplate_1 { get; set; }
    public DataTemplate TripleEventTemplate_2 { get; set; }

    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
        if (item != null)
        {
            DateTimeOffset calendarItem = (DateTimeOffset)item;
            DateTimeOffset dateTimeOffset = SpecialDates.Keys.FirstOrDefault(x => x.Date == calendarItem.Date);

            if (dateTimeOffset != DateTimeOffset.MinValue)
            {
                string template = this.SpecialDates[dateTimeOffset];

                switch (template)
                {
                    case "SingleEvent_1":
                        return SingleEventTemplate_1;
                    case "SingleEvent_2":
                        return SingleEventTemplate_2;
                    case "DoubleEvent_1":
                        return DoubleEventTemplate_1;
                    case "DoubleEvent_2":
                        return DoubleEventTemplate_2;
                    case "DoubleEvent_3":
                        return DoubleEventTemplate_3;
                    case "TripleEvent_1":
                        return TripleEventTemplate_1;
                    case "TripleEvent_2":
                        return TripleEventTemplate_2;
                }
            }

            return DefaultTemplate;
        }

        return base.SelectTemplateCore(item, container);
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Page.Resources>
    <DataTemplate x:Key="defaultTemplate">
    </DataTemplate>
    <DataTemplate x:Key="singleEventTemplate_1">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="DeepPink" Margin="2"/>
        </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="singleEventTemplate_2">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Cyan" Margin="2"/>
        </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="doubleEventTemplate_1">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Violet" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Orange" Margin="2"/>
        </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="doubleEventTemplate_2">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Gold" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Green" Margin="2"/>
        </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="doubleEventTemplate_3">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Brown" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Blue" Margin="2"/>
        </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="tripleEventTemplate_1">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Green" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="DeepSkyBlue" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Orange" Margin="2"/>
        </StackPanel>
    </DataTemplate>
     <DataTemplate x:Key="tripleEventTemplate_2">
        <StackPanel Orientation="Horizontal">
            <Ellipse MinWidth="4" MinHeight="4" Fill="Red" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Green" Margin="2"/>
            <Ellipse MinWidth="4" MinHeight="4" Fill="Gold" Margin="2"/>
        </StackPanel>
    </DataTemplate>
</Page.Resources>
 <Grid>
    <calendar:SfCalendar
                    CornerRadius="14"
                    DayOfWeekFormat="{}{dayofweek.abbreviated(3)}">
            <calendar:SfCalendar.Resources>
                <ResourceDictionary>
                    <!--  Resources and color keys for Calendar Control  -->
                    <SolidColorBrush x:Key="SyncfusionCalendarItemOutOfScopeForeground"
                                                 Color="SlateGray" Opacity="0.5" />
                    <SolidColorBrush x:Key="SyncfusionCalendarWeekItemForeground"
                                                 Color="{ThemeResource SystemBaseMediumLowColor}" />
                    <x:Double x:Key="SyncfusionSubtitleAltFontSize">16</x:Double>
                    <Thickness x:Key="SyncfusionCalendarItemMargin">1</Thickness>
                    <x:Double x:Key="SyncfusionBodyFontSize">13</x:Double>
                    <local:CustomCalendarItemTemplateSelector x:Key="selector"
                                    SingleEventTemplate_1="{StaticResource singleEventTemplate_1}"
                                    SingleEventTemplate_2="{StaticResource singleEventTemplate_2}"
                                    DoubleEventTemplate_1="{StaticResource doubleEventTemplate_1}"
                                    DoubleEventTemplate_2="{StaticResource doubleEventTemplate_2}"                                                                     
                                    DoubleEventTemplate_3="{StaticResource doubleEventTemplate_3}"
                                    TripleEventTemplate_1="{StaticResource tripleEventTemplate_1}"
                                    TripleEventTemplate_2="{StaticResource tripleEventTemplate_2}"
                                    DefaultTemplate="{StaticResource defaultTemplate}"/>
                    <Style TargetType="calendar:CalendarItem">
                        <Setter Property="CornerRadius" Value="14"/>
                        <Setter Property="HorizontalContentAlignment" Value="Stretch"/>
                        <Setter Property="VerticalContentAlignment" Value="Stretch"/>
                        <Setter Property="ContentTemplate">
                            <Setter.Value>
                                <DataTemplate>
                                    <Grid MinWidth="40" MinHeight="40">
                                        <ContentControl
                                                        HorizontalAlignment="Center"
                                                        VerticalAlignment="Center"
                                                        Margin="2"
                                                        Content="{Binding DisplayText}"/>
                                        <ContentControl
                                                        Margin="3"
                                                        HorizontalAlignment="Center"
                                                        VerticalAlignment="Bottom"
                                                        Content="{Binding Date}"
                                                        ContentTemplateSelector="{StaticResource selector}"/>
                                    </Grid>
                                </DataTemplate>
                            </Setter.Value>
                        </Setter>
                    </Style>
                </ResourceDictionary>
            </calendar:SfCalendar.Resources>
    </calendar:SfCalendar>
</Grid>

{% endhighlight %}
{% endtabs %}

![Custom UI of specific date cells in Calendar](Getting-Started_images/ItemTemplateSelector.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/CustomUI)

## Customize using theme keys

You can customize the colors of day names and headers of month, year, decade and century by changing the theme keys values in a `ResourceDictionary` used in the `Calendar` control.

<table>
<tr>
<th> Name of the key</th>
<th> Description </th>
</tr>
<tr>
<td>SyncfusionCalendarNavigationButtonForeground</td>
<td>Key to change the color of calendar navigation button foreground color.</td>
</tr>
<tr>
<td>SyncfusionCalendarWeekItemForeground</td>
<td>Key to change the color of calendar week days name foreground color.</td>
</tr>
<tr>
<td>SyncfusionCalendarTodayItemForeground</td>
<td>Key to change the color of calendar today date foreground color.</td>
</tr>
<tr>
<td>SyncfusionCalendarItemBackground<br/><br/></td>
<td>Key to change the color of calendar date cells background color except today date cell.</td>
</tr>
<tr>
<td>SyncfusionCalendarItemBorderBrush<br/><br/></td>
<td>Key to change the color of calendar date cells border brush.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionCalendarTodayItemBackground<br/><br/></td>
<td>Key to change the color of calendar today date cell background color.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionCalendarTodayItemBorderBrush<br/><br/></td>
<td>Key to change the color of calendar today date cell border brush.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionCalendarItemOutOfScopeForeground<br/><br/></td>
<td>Key to change the color of calendar date cells foreground color which are out of scope.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionCalendarItemMargin<br/><br/></td>
<td>Key to change the margin of calendar item.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionSubtitleAltFontSize<br/><br/></td>
<td>Key to change the font size of calendar header region.<br/><br/></td>
</tr>
<tr>
<td>SyncfusionBodyFontSize<br/><br/></td>
<td>Key to change the font size of calendar items region.<br/><br/></td>
</tr>
</tr>
<table/>

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar CornerRadius="6">
     <calendar:SfCalendar.Resources>
        <ResourceDictionary>
                    <!--Theme Key customization-->
            <SolidColorBrush x:Key="SyncfusionCalendarNavigationButtonForeground"
                                         Color="#FF248D92" />
            <SolidColorBrush x:Key="SyncfusionCalendarWeekItemForeground"
                                         Color="#FF248D92" />
            <SolidColorBrush x:Key="SyncfusionCalendarTodayItemForeground"
                                         Color="{ThemeResource SystemBaseHighColor}" />
            <SolidColorBrush x:Key="SyncfusionCalendarItemBackground"
                                         Color="{ThemeResource SystemChromeMediumLowColor}" />
            <SolidColorBrush x:Key="SyncfusionCalendarItemBorderBrush"
                                         Color="{ThemeResource SystemChromeMediumLowColor}"/>
            <SolidColorBrush x:Key="SyncfusionCalendarTodayItemBackground"
                                         Color="#FF9BC5ED" />
            <SolidColorBrush x:Key="SyncfusionCalendarTodayItemBorderBrush"
                                         Color="#FF9BC5ED" />
            <SolidColorBrush x:Key="SyncfusionCalendarItemOutOfScopeForeground"
                                         Color="SlateGray" Opacity="0.5" />
            <Thickness x:Key="SyncfusionCalendarItemMargin">1</Thickness>
            <x:Double x:Key="SyncfusionSubtitleAltFontSize">16</x:Double>
            <x:Double x:Key="SyncfusionBodyFontSize">13</x:Double>
            <FontFamily x:Key="SyncfusionControlThemeFontFamily">SimSun</FontFamily>
            <Style TargetType="calendar:CalendarItem">
                <Setter Property="CornerRadius" Value="5"/>
                <Setter Property="HorizontalContentAlignment" Value="Stretch"/>
                <Setter Property="VerticalContentAlignment" Value="Stretch"/>
                <Setter Property="ContentTemplate">
                    <Setter.Value>
                        <DataTemplate>
                            <Grid MinWidth="40" MinHeight="40">
                                <ContentControl
                                                HorizontalAlignment="Center"
                                                VerticalAlignment="Center"
                                                Margin="3"
                                                Content="{Binding DisplayText}"/>
                            </Grid>
                        </DataTemplate>
                    </Setter.Value>
                </Setter>
            </Style>
        </ResourceDictionary>
    </calendar:SfCalendar.Resources>
</calendar:SfCalendar>

{% endhighlight %}
{% endtabs %}

![Customize calendar using theme keys](UI-Customization_images/customize-theme-keys.png)

## Hide days that is out of scope

You can hide the days that are out of the scope of current view by setting the [OutOfScopeVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_OutOfScopeVisibility) property value as **Hidden**. The default value of `OutOfScopeVisibility` property is **Disabled**.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar OutOfScopeVisibility="Hidden"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.OutOfScopeVisibility = OutOfScopeVisibility.Hidden;

{% endhighlight %}
{% endtabs %}

![Display only the current month dates in WinUI Calendar.](Getting-Started_images/disableoutofscope.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Restriction)

