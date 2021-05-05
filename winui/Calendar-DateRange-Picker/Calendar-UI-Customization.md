---
layout: post
title: UI Customization in WinUI Calendar DateRange Picker | Syncfusion
description: Learn here all about how to customize the calendar in Syncfusion WinUI Calendar DateRange Picker (SfCalendarDateRangePicker) control and more.
platform: winui
control:  SfCalendarDateRangePicker
documentation: ug
---

# UI customization in WinUI Calendar DateRange Picker

This section describes how to select a date range from dropdown calendar and customization options available in `Calendar DateRange Picker` control.

## Change dropdown alignment

You can change the alignment of the dropdown calendar as full, center, left, right, top or bottom edge by using the [`DropDownPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is **Bottom**.

N> If you change the dropdown alignment by using `DropDownPlacement` property and there is not sufficient space, then `Calendar DateRange Picker` smartly shifts the dropdown calendar alignment.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDateRangePicker DropDownPlacement="Right" 
                             x:Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.DropDownPlacement = FlyoutPlacementMode.Right;

{% endhighlight %}
{% endtabs %}

![Alignment of dropdown calendar is changed to BottomEdgeAlignedLeft](Dropdown-Calendar_images/DropDownPlacement.png)

## Change dropdown size

You can change the size of dropdown calendar in `Calendar DateRange Picker` by using [`DropDownHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownHeight` property is **Auto**.

N> The dropdown size will be automatically resized based on the calendar and preset items hosted in it.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDateRangePicker DropDownHeight="500"
                               x:Name="sfCalendarDateRangePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDateRangePicker sfCalendarDateRangePicker = new SfCalendarDateRangePicker();
sfCalendarDateRangePicker.DropDownHeight = 500;

{% endhighlight %}
{% endtabs %}

![Calendar DateRange Picker with customized dropdown height](Dropdown-Calendar_images/DropDownHeight.png)

## Customize individual items in Calendar

You can change the UI of specific cells in `Calendar DateRange Picker` dropdown calendar by using the [FlyoutBase.AttachedFlyout](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) property and `DropDownFlyout` control.

1. Create a **EventDataConverter** class and set the special dates for specific events. 

{% tabs %}
{% highlight C# %}

public class EventDataConverter : IValueConverter
{
    Dictionary<DateTimeOffset, string> SpecialDates;
    public EventDataConverter()
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
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        DateTimeOffset dateTimeOffset = SpecialDates.Keys.FirstOrDefault(x => x.Date == (DateTime)value);

        if (dateTimeOffset != DateTimeOffset.MinValue)
        {
            string template = SpecialDates[dateTimeOffset];
            StackPanel stackPanel;
            switch (template)
            {
                case "SingleEvent_1":
                    return new List<Brush>() { new SolidColorBrush(Colors.DeepPink) };
                case "SingleEvent_2":
                    return new List<Brush>() { new SolidColorBrush(Colors.Cyan) };
                case "DoubleEvent_1":
                    return new List<Brush>() { new SolidColorBrush(Colors.Violet), new SolidColorBrush(Colors.Orange) };
                case "DoubleEvent_2":
                    return new List<Brush>() { new SolidColorBrush(Colors.Gold), new SolidColorBrush(Colors.Green) };
                case "DoubleEvent_3":
                    return new List<Brush>() { new SolidColorBrush(Colors.Brown), new SolidColorBrush(Colors.Blue) };
                case "TripleEvent_1":
                    return new List<Brush>() { new SolidColorBrush(Colors.Green), new SolidColorBrush(Colors.DeepSkyBlue), new SolidColorBrush(Colors.Orange) };
                case "TripleEvent_2":
                    return new List<Brush>() { new SolidColorBrush(Colors.Red), new SolidColorBrush(Colors.Green), new SolidColorBrush(Colors.Gold) };
            }
        }
        return null;
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language)
    {
        return null;
    }
}

{% endhighlight %}
{% endtabs %}

2. Create a **DataTemplate** to customize the date cells of Calendar. Now add the `Calendar` control inside the `FlyoutBase.AttachedFlyout` property and `DropDownFlyout` control.

{% tabs %}
{% highlight XAML %}

<Page.Resources>
    <local:EventDataConverter x:Key="EventDataConverterKey" />
    <DataTemplate x:Key="customTemplate">
        <ItemsControl ItemsSource="{Binding Path=Date, Converter={StaticResource EventDataConverterKey}}">
            <ItemsControl.ItemTemplate>
                <DataTemplate >
                    <Ellipse MinHeight="4" MinWidth="4" Margin="2" Fill="{Binding}"/>
                </DataTemplate>
            </ItemsControl.ItemTemplate>
            <ItemsControl.ItemsPanel>
                <ItemsPanelTemplate>
                    <StackPanel Orientation="Horizontal"/>
                </ItemsPanelTemplate>
            </ItemsControl.ItemsPanel>
        </ItemsControl>
    </DataTemplate>
</Page.Resources>
<Grid>
    <calendar:SfCalendarDateRangePicker
                        x:Name="calendarDateRangePicker"
                        MinWidth="180"
                        HorizontalAlignment="Center"
                        VerticalAlignment="Center">
        <FlyoutBase.AttachedFlyout>
            <editor:DropDownFlyout>
                <calendar:SfCalendar SelectionMode="Range"
                                         SelectedRange="{x:Bind calendarDateRangePicker.SelectedRange, Mode=TwoWay}" >
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
                                                        ContentTemplate="{StaticResource customTemplate}"
                                                       />
                                            </Grid>
                                        </DataTemplate>
                                    </Setter.Value>
                                </Setter>
                            </Style>
                        </ResourceDictionary>
                    </calendar:SfCalendar.Resources>
                </calendar:SfCalendar>
            </editor:DropDownFlyout>
        </FlyoutBase.AttachedFlyout>
    </calendar:SfCalendarDateRangePicker>
</Grid>

{% endhighlight %}
{% endtabs %}

![Custom UI of specific date cells in Calendar DateRange Picker](DropDown-Calendar_images/Customization.png)

## Customize using theme keys

You can customize the colors of day names and headers of month, year, decade and century by changing the theme keys values in a ResourceDictionary used in the `Calendar` control and by using the [`AttachedFlyout`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) and `DropDownFlyout` properties.

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
<td>SyncfusionCalendarItemBackground</td>
<td>Key to change the color of calendar date cells background color except today date cell.</td>
</tr>
<tr>
<td>SyncfusionCalendarItemBorderBrush</td>
<td>Key to change the color of calendar date cells border brush.</td>
</tr>
<tr>
<td>SyncfusionCalendarTodayItemBackground</td>
<td>Key to change the color of calendar today date cell background color</td>
</tr>
<tr>
<td>SyncfusionCalendarTodayItemBorderBrush</td>
<td>Key to change the color of calendar today date cell border brush.</td>
</tr>
<tr>
<td>SyncfusionCalendarItemOutOfScopeForeground</td>
<td>Key to change the color of calendar date cells foreground color which are out of scope.</td>
</tr>
<tr>
<td>SyncfusionCalendarItemMargin</td>
<td>Key to change the margin of calendar item.</td>
</tr>
<tr>
<td>SyncfusionSubtitleAltFontSize</td>
<td>Key to change the font size of calendar header region.</td>
</tr>
<tr>
<td>SyncfusionBodyFontSize</td>
<td>Key to change the font size of calendar items region.</td>
</tr>
</table>

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker
                        x:Name="calendarDateRangePicker"
                        MinWidth="180"
                        HorizontalAlignment="Center"
                        VerticalAlignment="Top">
    <FlyoutBase.AttachedFlyout>
        <editors:DropDownFlyout>
            <calendar:SfCalendar SelectionMode="Range" SelectedRange="{x:Bind calendarDateRangePicker.SelectedRange, Mode=TwoWay}" >
                <calendar:SfCalendar.Resources>
                    <ResourceDictionary>
                        <SolidColorBrush x:Key="SyncfusionCalendarNavigationButtonForeground"
                                                     Color="#FF248D92" />
                        <SolidColorBrush x:Key="SyncfusionCalendarWeekItemForeground"
                                                     Color="#FF248D92" />
                        <SolidColorBrush x:Key="SyncfusionCalendarTodayItemForeground"
                                                     Color="{ThemeResource SystemBaseHighColor}" />
                        <SolidColorBrush x:Key="SyncfusionCalendarItemBackground"
                                                     Color="{ThemeResource SystemListLowColor}" />
                        <SolidColorBrush x:Key="SyncfusionCalendarItemBorderBrush"
                                                     Color="{ThemeResource SystemListLowColor}"/>
                        <SolidColorBrush x:Key="SyncfusionCalendarTodayItemBackground"
                                                     Color="#FF9BC5ED" />
                        <SolidColorBrush x:Key="SyncfusionCalendarTodayItemBorderBrush"
                                                     Color="#FF9BC5ED" />
                        <SolidColorBrush x:Key="SyncfusionCalendarItemOutOfScopeForeground"
                                                     Color="SlateGray " Opacity="0.5" />
                        <Thickness x:Key="SyncfusionCalendarItemMargin">1</Thickness>
                        <x:Double x:Key="SyncfusionBodyFontSize">13</x:Double>
                        <FontFamily x:Key="SyncfusionControlThemeFontFamily">SimSun</FontFamily>
                        <x:Double x:Key="SyncfusionSubtitleAltFontSize">16</x:Double>
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
        </editors:DropDownFlyout>
    </FlyoutBase.AttachedFlyout>
</calendar:SfCalendarDateRangePicker>

{% endhighlight %}
{% endtabs %}

![Customize calendar by theme keys in WinUI Calendar DateRange Picker](Calendar-UI-Customization_images/customize-theme-keys.png)