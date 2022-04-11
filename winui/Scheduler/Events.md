---
layout: post
title: Events in WinUI Scheduler control | Syncfusion
description: Learn here all about the Events support in Syncfusion WinUI Scheduler (SfScheduler) control and more details.
platform: winui
control: SfScheduler
documentation: ug
---

# Events in WinUI Scheduler (SfScheduler)

## CellTapped

The [CellTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_CellTapped) event occurs when the user clicks or touches the cell in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and [CellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html) as objects.

The [CellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html) object contains the following properties:

* [Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_Appointment): Returns the Tapped appointment values.

    1. If `ItemsSource` is added with the custom business object then tapped, custom Appointment details could be got by using the Appointment `Data` property in the Cell tapped arguments.
    2. The tapped appointment is a Recurrence appointment, it will return the parent recurrence appointment values.
    3. The appointment details is got for the month view if `AppointmentDisplaymode `as `Appointment,` or else it will be null for month view.

* [Appointments](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_Appointments): Returns the Tapped Month cell appointments values if the `AppointmentDisplayMode` as `indicator.` The Tapped Month Cell has a Recurrence appointment it will return the parent recurrence appointment values. It will be null for Day or Week or Workweek views.   
* [IsMoreAppointments](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_IsMoreAppointments): Specifies whether more appointments are tapped or not in month view. It will be applicable only for Month view which has AppointmentDisplaymode as Appointment. 
* [CancelNavigation](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_CancelNavigation): Specifies whether the day view navigation should be disabled when clicking more appointments in the month view. It will be applicable for month view which has AppointmentDisplaymode as Appointment and click the More appointments in the month cell.
* [DateTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_DateTime): Gets the date-time of the tapped cell.
* [PointerDeviceType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_PointerDeviceType): Gets the pointer device type of the tapped cell.
* [Resource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_CellTappedEventArgs_Resource): Gets the resource associated with the timeslot cell where the user tapped.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellTapped="Schedule_CellTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.CellTapped += Schedule_CellTapped;

private void Schedule_CellTapped(object sender, CellTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## CellDoubleTapped

The [CellDoubleTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_CellDoubleTapped) event occurs when the user double clicks the cell in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `CellDoubleTappedEventArgs` as objects. The base class of the [CellDoubleTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellDoubleTappedEventArgs.html) is [CellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html).

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellDoubleTapped="Schedule_CellDoubleTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.CellDoubleTapped += Schedule_CellDoubleTapped;

private void Schedule_CellDoubleTapped(object sender, CellDoubleTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## CellLongPressed

The [CellLongPressed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_CellLongPressed) event occurs when the user long presses the cell in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `CellLongPressedEventArgs` as objects. The base class of the [CellLongPressedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellLongPressedEventArgs.html) is [CellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.CellTappedEventArgs.html).

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellLongPressed="Schedule_CellLongPressed">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.CellLongPressed += Schedule_CellLongPressed;

private void Schedule_CellLongPressed(object sender, CellLongPressedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## SelectionChanged

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_SelectionChanged) event occurs after the selection is changed in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and [SelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs.html) as objects.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       SelectionChanged="Schedule_SelectionChanged">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.SelectionChanged += Schedule_SelectionChanged;

private void Schedule_SelectionChanged(object sender, Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs e)
{
    var newDate = e.NewValue.ToString();
    var oldDate = e.OldValue.ToString();
}
{% endhighlight %}
{% endtabs %}

The [SelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs.html) object contains the following properties:

* [OldValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_SelectionChangedEventArgs_OldValue): Gets an old selected date.
* [NewValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_SelectionChangedEventArgs_NewValue): Gets a new selected date.

## SelectionChanging

The [SelectionChanging](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_SelectionChanging) event occurs when the selection gets changing in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and [SelectionChangingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangingEventArgs.html) as objects.

The [SelectionChangingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangingEventArgs.html) object contains the following properties:

* [OldValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_SelectionChangingEventArgs_OldValue): Gets an old selected date.
* [NewValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SelectionChangingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_SelectionChangingEventArgs_NewValue): Gets a new selected date.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       SelectionChanging="Schedule_SelectionChanging">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.SelectionChanging += Schedule_SelectionChanging;

private void Schedule_SelectionChanging(object sender, SelectionChangingEventArgs e)
{
    var newDate = e.NewValue.ToString();
    var oldDate = e.OldValue.ToString();
}
{% endhighlight %}
{% endtabs %}

## ViewHeaderCellTapped

The [ViewHeaderCellTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ViewHeaderCellTapped) event occurs when the user clicks or touches the view header in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and [ViewHeaderCellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewHeaderCellTappedEventArgs.html) as objects.

The [ViewHeaderCellTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewHeaderCellTappedEventArgs.html) object contains the following properties:

* [DateTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewHeaderCellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_ViewHeaderCellTappedEventArgs_DateTime): Gets the corresponding date time.
* [Resource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewHeaderCellTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_ViewHeaderCellTappedEventArgs_Resource): Gets the resource when tapped on view header in a day, week, workweek, and timeline views.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       ViewHeaderCellTapped="Schedule_ViewHeaderCellTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.ViewHeaderCellTapped += Schedule_ViewHeaderCellTapped;

private void Schedule_ViewHeaderCellTapped(object sender, ViewHeaderCellTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## HeaderTapped

The [HeaderTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_HeaderTapped) event occurs when the user clicks or touches the Scheduler header. This event receives two arguments namely `this` that handles SfScheduler and `HeaderTappedEventArgs` as objects.

The [HeaderTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.HeaderTappedEventArgs.html) object contains the following property:

* [DateTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.HeaderTappedEventArgs.html#Syncfusion_UI_Xaml_Scheduler_HeaderTappedEventArgs_DateTime): Gets the corresponding date time.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Week"
                       HeaderTapped="Schedule_HeaderTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.HeaderTapped += Schedule_HeaderTapped;

private void Schedule_HeaderTapped(object sender, HeaderTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## AppointmentTapped

The [AppointmentTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentTapped) event occurs when the schedule appointments get tapped in all views. This event receives two arguments namely `this` that handles SfScheduler and `AppointmentTappedArgs` as objects.

The [AppointmentTappedArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentTappedArgs.html) object contains the following properties:

* [Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentTappedArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentTappedArgs_Appointment): Gets the custom appointment details.
* [SelectedDate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentTappedArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentTappedArgs_SelectedDate): Gets the SelectedDate details.
* [Resource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentTappedArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentTappedArgs_Resource): Gets the resource details under which the appointment is located.

{% tabs %}
{% highlight xaml tabtitle ="MainWindow.xaml" hl_lines="3" %}
<scheduler:SfScheduler x:Name="Schedule" 
                       ViewType="Month"
                       AppointmentTapped="Schedule_AppointmentTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle= "MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.AppointmentTapped += Schedule_AppointmentTapped;

private void Schedule_AppointmentTapped(object sender, AppointmentTappedArgs e)
{
    var appointment = e.Appointment.ToString();
}
{% endhighlight %}
{% endtabs %}
