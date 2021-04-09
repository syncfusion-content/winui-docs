---
layout: post
title: Events | WinUI | Scheduler | Syncfusion
description: This section explains about events in the Syncfusion WinUI Scheduler (SfScheduler) control and more details.
platform: winui
control: Scheduler
documentation: ug
---

# Events in WinUI Scheduler (SfScheduler)

## CellTapped

The `CellTapped` event occurs when the user clicks or touches the cell in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `CellTappedEventArgs` as objects.

The `CellTappedEventArgs` object contains the following properties:

* `Appointment`: Returns the Tapped appointment values.

    1. If `ItemsSource` added with the custom business object then tapped custom Appointment details can get by using the Appointment `Data` property in the Cell tapped arguments.
    2. The tapped appointment is a Recurrence appointment it will return the parent recurrence appointment values.
    3. The appointment details get for month view if `AppointmentDisplaymode `as `Appointment,` or else it will be null for month view.

* `Appointments`: Returns the Tapped Month cell appointments values if the `AppointmentDisplayMode` as `indicator.` The Tapped Month Cell has a Recurrence appointment it will return the parent recurrence appointment values. It will be null for Day or Week or Workweek views.   
* `IsMoreAppointments`: Specifies whether more appointments are tapped or not in month view. It will be applicable only for Month view has AppointmentDisplaymode as Appointment. 
* `CancelNavigation`: Specifies whether the day view navigation should be disabled when clicking more appointments in the month view. It will be applicable for month view has AppointmentDisplaymode as Appointment and click the More appointments in month cell.
* `DateTime`: Gets the date-time of the tapped cell.
* `PointerDeviceType`: Gets the pointer device type of the tapped cell.
* `Resource`: Gets the resource associated with the timeslot cell where the user tapped.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellTapped="Schedule_CellTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.CellTapped += Schedule_CellTapped;

private void Schedule_CellTapped(object sender, CellTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## CellDoubleTapped

The `CellDoubleTapped` event occurs when the user double clicks the cell in Scheduler. This event receives two arguments namely this that handles SfScheduler and `CellDoubleTappedEventArgs` as objects. The base class of the `CellDoubleTappedEventArgs` is `CellTappedEventArgs.`

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellDoubleTapped="Schedule_CellDoubleTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.CellDoubleTapped += Schedule_CellDoubleTapped;

private void Schedule_CellDoubleTapped(object sender, CellDoubleTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## CellLongPressed

The `CellLongPressed` event occurs when the user long presses the cell in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `CellLongPressedEventArgs` as objects. The base class of the `CellLongPressedEventArgs` is `CellTappedEventArgs.`

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       CellLongPressed="Schedule_CellLongPressed">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.CellLongPressed += Schedule_CellLongPressed;

private void Schedule_CellLongPressed(object sender, CellLongPressedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## SelectionChanged

The `SelectionChanged` event occurs after the selection is changed in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `SelectionChangedEventArgs` as objects.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       SelectionChanged="Schedule_SelectionChanged">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.SelectionChanged += Schedule_SelectionChanged;

private void Schedule_SelectionChanged(object sender, Syncfusion.UI.Xaml.Scheduler.SelectionChangedEventArgs e)
{
    var newDate = e.NewValue.ToString();
    var oldDate = e.OldValue.ToString();
}
{% endhighlight %}
{% endtabs %}

The `SelectionChangedEventArgs` object contains the following properties:

* OldValue: Gets an old selected date.
* NewValue: Gets a new selected date.

## SelectionChanging

The `SelectionChanging` event occurs when the selection gets changing in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `SelectionChangingEventArgs` as objects.

The `SelectionChanging` object contains the following properties:

* OldValue: Gets an old selected date.
* NewValue: Gets a new selected date.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       SelectionChanging="Schedule_SelectionChanging">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.SelectionChanging += Schedule_SelectionChanging;

private void Schedule_SelectionChanging(object sender, SelectionChangingEventArgs e)
{
    var newDate = e.NewValue.ToString();
    var oldDate = e.OldValue.ToString();
}
{% endhighlight %}
{% endtabs %}

## ViewHeaderCellTapped

The `ViewHeaderCellTapped` event occurs when the user clicks or touches the view header in Scheduler. This event receives two arguments namely `this` that handles SfScheduler and `ViewHeaderCellTappedEventArgs` as objects.

The `ViewHeaderCellTappedEventArgs` object contains the following properties:

* `DateTime`: Gets the corresponding date time.
* `Resource`: Gets the resource when tapped on view header in a day, week, workweek, and timeline views.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Month"
                       ViewHeaderCellTapped="Schedule_ViewHeaderCellTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.ViewHeaderCellTapped += Schedule_ViewHeaderCellTapped;

private void Schedule_ViewHeaderCellTapped(object sender, ViewHeaderCellTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## HeaderTapped

The `HeaderTapped` event occurs when the user clicks or touches the Scheduler header. This event receives two arguments namely `this` that handles SfScheduler and `HeaderTappedEventArgs` as objects.

The `HeaderTappedEventArgs` object contains the following property:

* `DateTime`: Gets the corresponding date time.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                       ViewType="Week"
                       HeaderTapped="Schedule_HeaderTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.HeaderTapped += Schedule_HeaderTapped;

private void Schedule_HeaderTapped(object sender, HeaderTappedEventArgs e)
{
    var dateTime = e.DateTime.ToString();
}
{% endhighlight %}
{% endtabs %}

## AppointmentTapped

The `AppointmentTapped` event occurs when the schedule appointments get tapped in all views. This event receives two arguments namely this that handles SfScheduler and `AppointmentTappedArgs` as objects.

The `AppointmentTappedArgs` object contains the following properties:

* `Appointment`: Gets the custom appointment details.
* `SelectedDate`: Gets the SelectedDate details.
* `Resource`: Gets the resource details under which the appointment is located.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule" 
                       ViewType="Month"
                       AppointmentTapped="Schedule_AppointmentTapped">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c#%}
this.Schedule.AppointmentTapped += Schedule_AppointmentTapped;

private void Schedule_AppointmentTapped(object sender, AppointmentTappedArgs e)
{
    var appointment = e.Appointment.ToString();
}
{% endhighlight %}
{% endtabs %}