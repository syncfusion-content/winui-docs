---
layout: post
title: DropDown Calendar in CalendarDatePicker control | Syncfusion
description: This page explain about how to Customization the Drop Down of the WinUI SfCalendarDatePicker control and items features.
platform: winui
control:  SfCalendarDatePicker
documentation: ug
---

# Dropdown Calendar in WPF SfCalendarDatePicker (SfCalendarDatePicker)

This section describes how to select a date from dropdown Calendar and its customization options in [SfCalendarDatePicker](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html) control.

## Change dropdown alignment

You can change the alignment of the dropdown calendar as full, center, left, right, top or bottom with edge of the `CalendarDatePicker` by using the [DropDownPlacement](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownPlacement) property. The default value of `DropDownPlacement` property is `Auto`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker DropDownPlacement="Right" 
                             x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.DropDownPlacement = FlyoutPlacementMode.Right;

{% endhighlight %}
{% endtabs %}

![Alignment of dropdown calendar is changed to BottomEdgeAlignedLeft](Dropdown-Calendar_images/DropDownPlacement.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown)

## Hide the dropdown button

You can hide the dropdown button in `CalendarDatePicker` by setting the [ShowDropDownButton](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowDropDownButton) property value as `false`. The default value of `ShowDropDownButton` property is `true`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker ShowDropDownButton="False" 
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowDropDownButton = false;

{% endhighlight %}
{% endtabs %}

![CalendarDatePicker hides the dropdown button](Dropdown-Calendar_images/ShowDropDownButton.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown)

## Custom UI for specific cell in dropdown Calendar

You can change the UI of specific cells in `CalendarDatePicker` by using the [DropDownContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownContentTemplate)[CalendarItem.ContentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.CalendarItem.html) property. The `DataContext` of `CalendarItem.ContentTemplate` and `DropDownContentTemplate` is `CalendarDatePicker`. 

{% tabs %}
{% highlight C# %}

public class CustomCalendarItemTemplateSelector : DataTemplateSelector
{
    public CustomCalendarItemTemplateSelector()
    {
        SpecialDates = new Dictionary<DateTimeOffset, string>();
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(1), "BirthDay");
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(5), "Gift");
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(-1).AddDays(-2), "Award");
        SpecialDates.Add(DateTimeOffset.Now.AddDays(1), "Gift");
        SpecialDates.Add(DateTimeOffset.Now.AddDays(9), "BirthDay");
        SpecialDates.Add(DateTimeOffset.Now.AddDays(-4), "Award");
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(1), "Award");
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(3), "BirthDay");
        SpecialDates.Add(DateTimeOffset.Now.AddMonths(1).AddDays(-5), "Gift");
    }

    private Dictionary<DateTimeOffset, string> SpecialDates { get; set; }

    public DataTemplate DefaultTemplate { get; set; }
    public DataTemplate BirthdayTemplate { get; set; }
    public DataTemplate GiftTemplate { get; set; }
    public DataTemplate AwardTemplate { get; set; }

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
                    case "BirthDay":
                        return BirthdayTemplate;
                    case "Gift":
                        return GiftTemplate;
                    case "Award":
                        return AwardTemplate;
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
        <x:String x:Key="birthday">M24.188005,24.530994C24.999008,24.530994 25.657011,25.188997 25.657011,26 25.657011,26.811003 24.999008,27.469006 24.188005,27.469006 23.377003,27.469006 22.719,26.811003 22.719,26 22.719,25.188997 23.377003,24.530994 24.188005,24.530994z M16.000006,24.530994C16.811008,24.530994 17.469011,25.188997 17.469011,26 17.469011,26.811003 16.811008,27.469006 16.000006,27.469006 15.189002,27.469006 14.530999,26.811003 14.530999,26 14.530999,25.188997 15.189002,24.530994 16.000006,24.530994z M7.813005,24.405994C8.6240082,24.405994 9.282011,25.063997 9.282011,25.875 9.282011,26.686003 8.6240082,27.344006 7.813005,27.344006 7.0020018,27.344006 6.3439994,26.686003 6.3439994,25.875 6.3439994,25.063997 7.0020018,24.405994 7.813005,24.405994z M3,22.5C2.4490051,22.5,2,22.949005,2,23.5L2,29.5 30,29.5 30,23.5C30,22.949005,29.550995,22.5,29,22.5z M5,14.5C4.4489999,14.5,4,14.949,4,15.5L4,20.5 28,20.5 28,15.5C28,14.949,27.551001,14.5,27,14.5L16,14.5z M16,8.5C16.552,8.5,17,8.948,17,9.5L17,12.5 27,12.5C28.653999,12.5,30,13.846,30,15.5L30,20.672067 30.030354,20.68236C31.178461,21.103616,32,22.207819,32,23.5L32,30.5C32,31.052002,31.552002,31.5,31,31.5L1,31.5C0.44799805,31.5,0,31.052002,0,30.5L0,23.5C0,22.207819,0.82153827,21.103616,1.969646,20.68236L2,20.672067 2,15.5C2,13.846,3.346,12.5,5,12.5L15,12.5 15,9.5C15,8.948,15.448,8.5,16,8.5z M16.019098,0C16.450115,1.7290001 18.144182,3.5890007 18.144182,4.7290001 18.219185,6.1879997 17.684164,7 16.019098,7 14.354033,7 13.856012,6.0419998 13.856012,4.7290001 13.856012,3.323 14.56604,1.3330002 16.019098,0z</x:String>
        <x:String x:Key="gift">M14.072999,21.71989L14.173005,21.71989 23.954012,21.71989 23.954012,30.402982C23.954012,31.300994,23.255007,31.999997,22.356997,31.999997L14.072999,31.999997z M1.2980041,21.71989L11.178987,21.71989 11.178987,31.999997 2.8949892,31.999997C1.9960022,31.999997,1.2980041,31.300994,1.2980041,30.402982z M19.661989,3.2556945C19.06299,3.2556945,14.072999,7.3477336,12.975007,8.545744L12.975007,8.8447515C13.674012,8.6447526 15.670015,7.1477343 17.267,6.1497227 19.162996,5.0517112 19.962008,3.7546926 19.661989,3.2556945z M5.5889899,3.2556945C5.3899848,3.7546926 6.1879889,5.0517112 7.984986,6.2497221 9.4819957,7.2477342 11.578004,8.6447526 12.277009,8.9447509L12.277009,8.6447526C11.178987,7.3477336,6.287995,3.2556945,5.5889899,3.2556945z M17.864281,0.00017286225C18.476668,-0.0068490629 19.175909,0.19928326 19.962008,0.76066515 22.756014,2.6566814 22.656008,4.2536984 22.656008,5.2517105 22.157015,7.447733 19.463015,8.4457446 16.868014,8.9447509L23.355013,8.9447509C24.252993,8.9447509,24.951998,9.6427566,24.951998,10.541768L24.951998,13.235797C24.951998,13.834803,24.553011,14.433808,24.053988,14.633815L24.053988,19.723867 14.173005,19.723867 14.173005,9.3437568 13.574006,9.3437568 13.075013,9.3437568 12.675996,9.3437568 12.277009,9.3437568 11.578004,9.3437568 11.477998,9.3437568 11.178987,9.3437568 11.178987,19.723867 1.2980041,19.723867 1.2980041,14.732815C0.59899889,14.533815,-2.3291432E-07,13.934802,0,13.136797L0,10.441769C-2.3291432E-07,9.5437566,0.69900499,8.8447515,1.5969848,8.8447515L8.4840099,8.8447515C5.8890082,8.545744 3.0939943,7.447733 2.6950075,5.2517105 2.6950075,4.353706 2.5950014,2.7566885 5.3899848,0.76066515 6.0889899,0.261659 6.7869879,0.061659901 7.385987,0.061660053 8.9830028,0.061659901 10.080995,1.4586705 10.480012,1.8586761 10.878999,2.2576827 12.076997,4.452706 12.675996,6.6487285 13.274995,4.452706 14.471986,2.2576827 14.871003,1.8586761 15.301535,1.4281411 16.29929,0.018116923 17.864281,0.00017286225z</x:String>
        <x:String x:Key="award">M6.4050484,19.617198L3.7509956,25.34103 6.5209923,24.451031 7.7069907,27.094029 10.305956,21.486943 10.209199,21.463142C8.8243089,21.103976,7.5456314,20.475896,6.431808,19.637838z M20.198464,18.975471L19.810075,19.313839C18.872342,20.092266,17.802781,20.71557,16.640677,21.144267L16.418594,21.22308 18.634039,27.072047 19.967047,24.487023 22.674016,25.519068z M12.916001,5.5320349C9.9759998,5.5320349 7.5829983,7.9410334 7.5829983,10.903033 7.5829983,13.865032 9.9759998,16.274031 12.916001,16.274031 15.857003,16.274031 18.250004,13.865032 18.250004,10.903033 18.250004,7.9410334 15.857003,5.5320349 12.916001,5.5320349z M12.916001,3.5320349C16.960003,3.5320349 20.250005,6.8390341 20.250005,10.903033 20.250005,14.968032 16.960003,18.274031 12.916001,18.274031 8.8729992,18.274031 5.5829973,14.968032 5.5829973,10.903033 5.5829973,6.8390341 8.8729992,3.5320349 12.916001,3.5320349z M12.91602,2.0000057C8.0390205,2.0000057 4.0710211,5.9940157 4.0710211,10.903028 4.0710211,15.81304 8.0390205,19.80705 12.91602,19.80705 17.79302,19.80705 21.761019,15.81304 21.761019,10.903028 21.761019,5.9940157 17.79302,2.0000057 12.91602,2.0000057z M12.91602,0C18.89502,0 23.761019,4.8920126 23.761019,10.903028 23.761019,13.251471 23.018526,15.429016 21.757237,17.210832L21.674238,17.325164 21.711064,17.311053 26.135013,28.99606 20.926031,27.007045 18.356024,31.999053 14.455157,21.696701 14.295179,21.719278C13.843446,21.777196 13.383129,21.807055 12.91602,21.807055 12.822598,21.807055 12.729448,21.805861 12.636584,21.803486L12.375046,21.793458 7.6759906,31.926026 5.4279938,26.921029 0,28.665028 4.8565531,18.189458 4.5508928,17.834802C3.0024042,15.949165 2.0710211,13.533284 2.0710211,10.903028 2.0710211,4.8920126 6.9370208,0 12.91602,0z</x:String>
        <DataTemplate x:Key="defaultTemplate"/>
        <DataTemplate x:Key="birthdayTemplate">
            <Grid>
                <Path 
                    Data="{StaticResource birthday}"
                    Stretch="Uniform"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Width="18"
                    Height="18"
                    Margin="3"
                    VerticalAlignment="Top"
                    HorizontalAlignment="Right"/>
            </Grid>
        </DataTemplate>
        <DataTemplate x:Key="giftTemplate">
            <Grid>
                <Path 
                    Data="{StaticResource gift}"
                    Stretch="Uniform"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Width="18"
                    Height="18"
                    Margin="3"
                    VerticalAlignment="Top"
                    HorizontalAlignment="Right"/>
            </Grid>
        </DataTemplate>
        <DataTemplate x:Key="awardTemplate">
            <Grid>
                <Path 
                    Data="{StaticResource award}"
                    Stretch="Uniform"
                    Fill="{ThemeResource SystemBaseHighColor}"
                    Width="18"
                    Height="18"
                    Margin="3"
                    VerticalAlignment="Top"
                    HorizontalAlignment="Right"/>
            </Grid>
        </DataTemplate>
    </Page.Resources>
    <Grid>
        <calendar:SfCalendarDatePicker>
            <calendar:SfCalendarDatePicker.DropDownContentTemplate>
                <DataTemplate>
                    <Grid>
                        <calendar:SfCalendar>
                            <calendar:SfCalendar.Resources>
                                <local:CustomCalendarItemTemplateSelector
                                                x:Key="selector"
                                                AwardTemplate="{StaticResource awardTemplate}"
                                                BirthdayTemplate="{StaticResource birthdayTemplate}"
                                                DefaultTemplate="{StaticResource defaultTemplate}"
                                                GiftTemplate="{StaticResource giftTemplate}" />
                                <Style TargetType="calendar:CalendarItem">
                                    <Setter Property="CornerRadius" Value="5" />
                                    <Setter Property="Margin" Value="3" />
                                    <Setter Property="BorderThickness" Value="1" />
                                    <Setter Property="BorderBrush" Value="LightGray" />
                                    <Setter Property="HorizontalContentAlignment" Value="Stretch" />
                                    <Setter Property="VerticalContentAlignment" Value="Stretch" />
                                    <Setter Property="ContentTemplate">
                                        <Setter.Value>
                                            <DataTemplate>
                                                <Grid MinWidth="50" MinHeight="40">
                                                    <ContentControl
                                                                    Margin="3"
                                                                    HorizontalAlignment="Left"
                                                                    VerticalAlignment="Top"
                                                                    Content="{Binding DisplayText}"
                                                                    FontSize="10" />
                                                    <ContentControl
                                                                    Margin="10"
                                                                    HorizontalAlignment="Right"
                                                                    VerticalAlignment="Bottom"
                                                                    Content="{Binding Date}"
                                                                    ContentTemplateSelector="{StaticResource selector}" />
                                                </Grid>
                                            </DataTemplate>
                                        </Setter.Value>
                                    </Setter>
                                </Style>
                            </calendar:SfCalendar.Resources>
                        </calendar:SfCalendar>
                    </Grid>
                </DataTemplate>
            </calendar:SfCalendarDatePicker.DropDownContentTemplate>
        </calendar:SfCalendarDatePicker>
    </Grid>

{% endhighlight %}
{% endtabs %}

![Custom UI of specific date cells in CalendarDatePicker](Getting-Started_images/ItemTemplateSelector.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/CustomUI)

## First day of week

By default, Sunday is shown as the first day of the week in a drop-down spinner. If you want to change the first day of week, use the [FirstDayOfWeek](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_FirstDayOfWeek) property value. The default value of `FirstDayOfWeek` property is `Sunday`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker x:Name="sfCalendarDatePicker" 
                               FirstDayOfWeek="Monday"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.FirstDayOfWeek = DayOfWeek.Monday;

{% endhighlight %}
{% endtabs %}

![WinUI CalendarDatePicker weekdays start from Monday](Getting-Started_images/first-day-of-week.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection)

## Number of weeks in a view

If you want to increase or decrease the number of weeks shown in a month view in drop-down spinner, use the [NumberOfWeeksInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_NumberOfWeeksInView) property. The default value of `NumberOfWeeksInView` property is `6`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker NumberOfWeeksInView="4"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.NumberOfWeeksInView = 4;

{% endhighlight %}
{% endtabs %}

![Show particular weeks in WinUI CalendarDatePicker.](Getting-Started_images/weeks-in-view.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection)

## Hide days that is out of scope

By default, out of scope view days are disabled in drop-down spinner. If you want to hide the days that are out of the scope of current view, use the [OutOfScopeVisibility](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_OutOfScopeVisibility) property value as `Hidden`. The default value of `OutOfScopeVisibility` property is `Disabled`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendarDatePicker OutOfScopeVisibility="Hidden"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.OutOfScopeVisibility = OutOfScopeVisibility.Hidden;

{% endhighlight %}
{% endtabs %}

![Display only the current month dates in WinUI CalendarDatePicker.](Getting-Started_images/disableoutofscope.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Restriction)

## Show submit button

If you want to select the date from drop down calendar only by clicking the `Ok` button, use the [ShowSubmitButtons](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_ShowSubmitButtons) property value as `true`. The default value of `ShowSubmitButtons` property is `false`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker ShowSubmitButtons="true"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.ShowSubmitButtons = true;

{% endhighlight %}
{% endtabs %}

![SfCalendarDatePicker hides the drop down calendar submit and cancel buttons](Dropdown-Calendar_images/ShowSubmitButtons.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown)

## Today and selected date highlighting

You can highlight the today and selected date as rectangle, filled rectangle, circle and filled circle. You can use the [TodayHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_TodayHighlightMode) property to highlight the today date and use the [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_SelectionHighlightMode) property to highlight the selected date. The default value of `TodayHighlightMode` property is `FilledRectangle` and `SelectionHighlightMode` property is `Rectangle`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker SelectionHighlightMode="FilledCircle"
                     TodayHighlightMode="Circle"
                     x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.SelectionHighlightMode = CalendarItemHighlightMode.FilledCircle;
sfCalendarDatePicker.TodayHighlightMode = CalendarItemHighlightMode.Circle;

{% endhighlight %}
{% endtabs %}

![CalendarDatePicker highlights the today and selected date](Getting-Started_images/TodayHighlightMode.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Selection)

## Change dropdown size

You can change the size of dropdown calendar by using [DropDownWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendarDatePicker.html#Syncfusion_UI_Xaml_Calendar_SfCalendarDatePicker_DropDownWidth) [DropDownHeight](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownBase_DropDownHeight) property. The default value of `DropDownHeight`  properties is `NaN`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker DropDownWidth="400"
                               DropDownHeight="500"
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.DropDownWidth = 400;
sfCalendarDatePicker.DropDownHeight = 500;

{% endhighlight %}
{% endtabs %}

![CalendarDatePicker with customized dropdown height and width](Dropdown-Calendar_images/DropDownHeight.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/DropDown)

## Change flow direction

You can change the flow direction of the `Calendar` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendarDatePicker FlowDirection="RightToLeft" 
                               x:Name="sfCalendarDatePicker"/>

{% endhighlight %}
{% highlight c# %}

SfCalendarDatePicker sfCalendarDatePicker = new SfCalendarDatePicker();
sfCalendarDatePicker.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![CalendarDatePicker flow direction changed to right to left](Getting-Started_images/FlowDirection.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendardatepicker-examples/blob/main/Samples/Formatting)
