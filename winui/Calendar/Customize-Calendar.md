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

## Today and selected date highlighting

You can highlight the today and selected date with rectangle and circle shapes. You can customize the selected date cell shape using [SelectionShape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionShape) property and use the [SelectionHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_SelectionHighlightMode) property to update the background of the selected date. The default value of `SelectionShape` property is `Rectangle` and `SelectionHighlightMode` property is `Outline`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar SelectionHighlightMode="Filled"
                     SelectionShape="Circle"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight c# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.SelectionHighlightMode = SelectionHighlightMode.FilledCircle;
sfCalendar.SelectionShape = SelectionShape.Circle;

{% endhighlight %}
{% endtabs %}

![Calendar highlights the today and selected date](Getting-Started_images/TodayHighlightMode.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection)

## Change flow direction

You can change the flow direction of the `Calendar` layout from right to left by setting the `FlowDirection` property value as `RightToLeft`. The default value of `FlowDirection` property is `LeftToRight`.

{% tabs %}
{% highlight XAML %}

<calendar:SfCalendar FlowDirection="RightToLeft" 
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight c# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.FlowDirection = FlowDirection.RightToLeft;

{% endhighlight %}
{% endtabs %}

![Calendar flow direction changed to right to left](Getting-Started_images/FlowDirection.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Formatting)

## Number of weeks in a view

If you want to increase or decrease the number of weeks shown in a month view, use the [NumberOfWeeksInView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Calendar.SfCalendar.html#Syncfusion_UI_Xaml_Calendar_SfCalendar_NumberOfWeeksInView) property. The default value of `NumberOfWeeksInView` property is `6`.

{% tabs %}
{% highlight xaml %}

<calendar:SfCalendar NumberOfWeeksInView="3"
                     x:Name="sfCalendar"/>

{% endhighlight %}
{% highlight C# %}

SfCalendar sfCalendar = new SfCalendar();
sfCalendar.NumberOfWeeksInView = 3;

{% endhighlight %}
{% endtabs %}

![Show particular weeks in WinUI Calendar](Getting-Started_images/weeks-in-view.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-tools-calendar-examples/blob/main/Samples/Selection)

