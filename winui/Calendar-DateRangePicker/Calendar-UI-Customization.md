---
layout: post
title: UI Customization in Calendar DateRangePicker control | Syncfusion
description: This page explain how to customize the dropdown calendar of the WinUI Calendar DateRangePicker (SfCalendarDateRangePicker) control.
platform: winui
control:  SfCalendarDateRangePicker
documentation: ug
---

# Calendar UI Customization in WinI Calendar DateRangePicker

This section describes how to select a date range from dropdown calendar and customization options available in `Calendar DateRangePicker` control.

## Change dropdown alignment

You can change the alignment of the dropdown calendar as full, center, left, right, top or bottom edge by using the [`DropDownPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is `Bottom`.

N> If you change the dropdown alignment by using `DropDownPlacement` property and there is not sufficient space, then `Calendar DateRangePicker` smartly shifts the dropdown calendar alignment.

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

You can change the size of dropdown calendar in `Calendar DateRangePicker` by using [`DropDownHeight`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownHeight` property is `Auto`.

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

![Calendar DateRangePicker with customized dropdown height](Dropdown-Calendar_images/DropDownHeight.png)

## Customize individual items in Calendar

You can change the UI of specific cells in `Calendar DateRangePicker` dropdown calendar by using the [AttachedFlyout](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) and `DropDownFlyout` properties.

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
            </editor:DropDownFlyout>
        </FlyoutBase.AttachedFlyout>
    </calendar:SfCalendarDateRangePicker>
</Grid>

{% endhighlight %}
{% endtabs %}

![Custom UI of specific date cells in Calendar DateRangePicker](DropDown-Calendar_images/Customization.png)

## Customize using theme keys

You can customize the colors of day names and headers of month, year, decade and century by changing the theme keys values in a ResourceDictionary used in the `Calendar` control and by using the [`AttachedFlyout`](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout?view=winrt-19041) and `DropDownFlyout` properties.

<table>
<tr>
<td>
Name of the key<br/><br/></td><td>
Description<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarNavigationButtonForeground<br/><br/></td><td>
Key to change the color of calendar navigation button foreground color.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarWeekItemForeground<br/><br/></td><td>
Key to change the color of calendar week days name foreground color.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarTodayItemForeground<br/><br/></td><td>
Key to change the color of calendar today date foreground color.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarItemBackground<br/><br/></td><td>
Key to change the color of calendar date cells background color except today date cell.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarItemBorderBrush<br/><br/></td><td>
Key to change the color of calendar date cells border brush.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarTodayItemBackground<br/><br/></td><td>
Key to change the color of calendar today date cell background color.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarTodayItemBorderBrush<br/><br/></td><td>
Key to change the color of calendar today date cell border brush.<br/><br/></td></tr>
<tr>
<td>
SyncfusionCalendarItemOutOfScopeForeground<br/><br/></td><td>
Key to change the color of calendar date cells foreground color which are out of scope.<br/><br/></td></tr>
<td>
SyncfusionCalendarItemMargin<br/><br/></td><td>
Key to change the margin of calendar item.<br/><br/></td></tr>
<td>
SyncfusionSubtitleAltFontSize<br/><br/></td><td>
Key to change the font size of calendar header region.<br/><br/></td></tr>
<td>
SyncfusionBodyFontSize<br/><br/></td><td>
Key to change the font size of calendar items region.<br/><br/></td></tr>
<table/>

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDateRangePicker
                    x:Name="calendarDateRangePicker"
                    MinWidth="180"
                    SelectedRange="{x:Bind calendar.SelectedRange, Mode=TwoWay}"
                    HorizontalAlignment="Center"
                    VerticalAlignment="Top">
    <FlyoutBase.AttachedFlyout>
        <editor:DropDownFlyout>
            <calendar:SfCalendar
                            x:Name="calendar"
                            SelectionMode="Range"
                            >
                <calendar:SfCalendar.Resources>
                    <ResourceDictionary
                        <!--Theme Key customization-->
                        <SolidColorBrusx:Key="SyncfusionCalendarNavigationButtonForeground"
                                                     Color="#FF248D92" />
                        <SolidColorBrusx:Key="SyncfusionCalendarWeekItemForeground"
                                                     Color="#FF248D92" />
                        <SolidColorBrusx:Key="SyncfusionCalendarTodayItemForeground"
                                                     Color="{ThemeResourcSystemBaseHighColor}" />
                        <SolidColorBrusx:Key="SyncfusionCalendarItemBackground"
                                                     Color="{ThemeResourcSystemListLowColor}" />
                        <SolidColorBrusx:Key="SyncfusionCalendarItemBorderBrush"
                                                     Color="{ThemeResourcSystemListLowColor}"/>
                        <SolidColorBrusx:Key="SyncfusionCalendarTodayItemBackground"
                                                     Color="#FF9BC5ED" />
                        <SolidColorBrusx:Key="SyncfusionCalendarTodayItemBorderBrush"
                                                     Color="#FF9BC5ED" />
                        <SolidColorBrusx:Key="SyncfusionCalendarItemOutOfScopeForeground"
                                                     Color="SlateGrayOpacity="0.5" />
                        <Thickness x:Key="SyncfusionCalendarItemMargin">1Thickness>
                        <x:Double x:Key="SyncfusionBodyFontSize">13</x:Double>
                        <FontFamilx:Key="SyncfusionControlThemeFontFamily">SimSunFontFamily>
                        <x:Double x:Key="SyncfusionSubtitleAltFontSize">16x:Double
                        <Style TargetType="calendar:CalendarItem">
                            <Setter Property="CornerRadius" Value="5"/>
                            <Setter Property="HorizontalContentAlignmentValue="Stretch"/>
                            <Setter Property="VerticalContentAlignmentValue="Stretch"/>
                            <Setter Property="ContentTemplate">
                                <Setter.Value>
                                    <DataTemplate>
                                        <Grid MinWidth="40" MinHeight="40">
                                            <ContentControl
                                                            HorizontalAlignmt="Center"
                                                            VerticalAlignmen"Center"
                                                            Margin="3"
                                                            Content="{BindinDisplayText}"/>
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

{% endhighlight %}
{% endtabs %}

![Customize calendar by theme keys in WinUI Calendar DateRangePicker](Calendar-UI-Customization_images/customize-theme-keys.png)