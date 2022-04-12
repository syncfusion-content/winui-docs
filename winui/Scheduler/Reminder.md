---
layout: post
title: Reminder in WinUI Scheduler control | Syncfusion
description: Learn here all about the Reminder support in the Syncfusion WinUI Scheduler (SfScheduler) control, its elements and more.
platform: winui
control: SfScheduler
documentation: ug
---
# Reminder in WinUI Scheduler (SfScheduler)
The WinUI scheduler notify an appointment reminder by using the [ReminderAlertOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ReminderAlertOpening) event. An appointment can have one or more reminders. 

## Enable reminder
Reminder can be enable by setting the [EnableReminder](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_EnableReminder) property to `true` which is used to trigger the `ReminderAlertOpening` event to notify appointment reminder. The reminder can be set by using the [Reminders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Reminders) property of [ScheduleAppointment.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html)

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}
<syncfusion:SfScheduler x:Name="Scheduler"
                        ViewType="Week"
                        EnableReminder="True" >
</syncfusion:SfScheduler>
{% endhighlight %}
{% endtabs %}

## Adding reminders
Configure the appointment reminders with [SchedulerReminder.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html) The `SchedulerReminder` has the following properties.

<table>
<tr>
<th>Properties</th>
<th>Description</th>
</tr>
<tr>
<td>{{'[ReminderTimeInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_ReminderTimeInterval)'| markdownify }}</td>
<td>Gets or sets the time interval that decides to notify the reminder before the appointment’s start time.
</td>
</tr>
<tr>
<td>{{'[ReminderAlertTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_ReminderAlertTime)'| markdownify }}</td>
<td>Gets the reminder time that decides when to enable `ReminderAlertOpening` event to the reminder of the appointment.</td>
</tr>
<tr>
<td>{{'[Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_Appointment)'| markdownify }}</td>
<td>Gets the appointment details for which the reminder is created.</td>
</tr>
<tr>
<td>{{'[Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_Data)'| markdownify }}</td>
<td>Gets the reminder data object associated with the `SchedulerReminder.`</td>
</tr>
<tr>
<td>{{'[IsDismissed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_IsDismissed)' | markdownify }}</td>
<td> Gets or sets whether the reminder is dismissed. </td>
</tr>
</table>

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6" %}
 <Grid.DataContext>
    <local:ReminderViewModel/>
 </Grid.DataContext>
 <syncfusion:SfScheduler x:Name="Schedule" 
                ItemsSource="{Binding Events}"
                EnableReminder="True">
  </syncfusion:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="ReminderViewModel.cs" %}
 public class ReminderViewModel 
 {
    ...
    public ScheduleAppointmentCollection Events { get; set; } = new ScheduleAppointmentCollection();
    this.Events.Add(new ScheduleAppointment()
    {
        StartTime = DateTime.Now,
        EndTime = DateTime.Now.AddHours(1),
        AppointmentBackground = new SolidColorBrush(Color.FromArgb(255, 83, 99, 250)),
        Subject = "Conference",
        Reminders = new ObservableCollection<SchedulerReminder>
        {
            new SchedulerReminder { ReminderTimeInterval = new TimeSpan(0)},
        }
    });
 }
{% endhighlight %}
{% endtabs %}

## Creating business object for reminder  
[Reminders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html#Syncfusion_UI_Xaml_Scheduler_AppointmentMapping_Reminders) supports to map the custom object with the [ScheduleAppointment.Reminders.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Reminders)

{% tabs %}
{% highlight c# tabtitle="Event.xaml.cs" %}
/// <summary>
/// Represents custom data properties.
/// </summary>
 public class Event
    {
        public Event()
        {
        }

        public DateTime From { get; set; }
        public DateTime To { get; set; }
        public bool IsAllDay { get; set; }
        public string EventName { get; set; }
        public string Notes { get; set; }
        public string StartTimeZone { get; set; }
        public string EndTimeZone { get; set; }
        public Brush Color { get; set; }
        public object RecurrenceId { get; set; }
        public object Id { get; set; }
        public string RecurrenceRule { get; set; }
        public ObservableCollection<DateTime> RecurrenceExceptions { get; set; }
        public ObservableCollection<Reminder> Reminders { get; set; }
    }
{% endhighlight %}
{% endtabs %}

The [ReminderMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ResourceMapping.html) provides the mapping information about the [SchedulerReminder](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html) properties to the [Data](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_Data) object. `ReminderMapping` has the following properties,

* [ReminderTimeInterval](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderMapping.html#Syncfusion_UI_Xaml_Scheduler_ReminderMapping_ReminderTimeInterval): Maps the property name of a custom class, which is equivalent for the [SchedulerReminder.ReminderTimeInterval.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_ReminderTimeInterval)
* [IsDismissed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderMapping.html#Syncfusion_UI_Xaml_Scheduler_ReminderMapping_IsDismissed): Maps the property name of a custom class, which is equivalent for the [SchedulerReminder.IsDismissed.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_IsDismissed)
* [ReminderAlertTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderMapping.html#Syncfusion_UI_Xaml_Scheduler_ReminderMapping_ReminderAlertTime): Maps the property name of a custom class, which is equivalent for the [SchedulerReminder.ReminderAlertTime.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html#Syncfusion_UI_Xaml_Scheduler_SchedulerReminder_ReminderAlertTime)

{% tabs %}
{% highlight c# tabtitle="Reminder.cs" %}
/// <summary>
/// Represents custom data properties.
/// </summary>
public class Reminder
{
    /// <summary>
    /// Gets or sets the value indicating whether the reminder is dismissed or not. 
    /// </summary>
    public bool Dismissed { get; set; }

    /// <summary>
    /// Gets or sets a value that decides to notify the reminder before the appointment’s start time.
    /// </summary>
    public TimeSpan TimeInterval { get; set; }

}

{% endhighlight %}
{% endtabs %}

Map those properties of the `Meeting` class with the [SfScheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html) control by using the [AppointmentMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html) and map `CustomReminder` properties with the [SchedulerReminder](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SchedulerReminder.html) by using the [ReminderMapping.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderMapping.html)

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 17 18 19 20" %}
 <syncfusion:SfScheduler x:Name="Schedule" 
                ItemsSource="{Binding Events}"
                EnableReminder="True">
            <syncfusion:SfScheduler.AppointmentMapping>
                <syncfusion:AppointmentMapping
                    Subject="EventName"
                    StartTime="From"
                    EndTime="To"
                    AppointmentBackground="Color"
                    IsAllDay="IsAllDay"
                    StartTimeZone="StartTimeZone"
                    EndTimeZone="EndTimeZone"
                    RecurrenceExceptionDates="RecurrenceExceptions"
                    RecurrenceRule="RecurrenceRule"
                    RecurrenceId="RecurrenceId"
                    Reminders="Reminders">
                    <syncfusion:AppointmentMapping.ReminderMapping>
                        <syncfusion:ReminderMapping IsDismissed="Dismissed"
                                                    ReminderTimeInterval="TimeInterval"/>
                    </syncfusion:AppointmentMapping.ReminderMapping>
                </syncfusion:AppointmentMapping>
            </syncfusion:SfScheduler.AppointmentMapping>
        </syncfusion:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="ReminderViewModel.cs" %}
public class ReminderViewModel 
{
  ...
  public ObservableCollection<Event> Events { get; set; } = new ObservableCollection<Event>();
  this.Events.Add(new Event()
  {
    From = DateTime.Now,
    To = DateTime.Now.AddHours(1),
    Color = new SolidColorBrush((Color)ColorConverter.ConvertFromString("#FF339933")),
    EventName = "Conference",
    Reminders = new ObservableCollection<Reminder>
    {
        new Reminder { TimeInterval = new TimeSpan(0)},
    }
    });
}
{% endhighlight %}
{% endtabs %}

## ReminderAlertOpening event
Scheduler notify the appointment's reminder by the [ReminderAlertOpening](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ReminderAlertOpening) event before the appointment's start time. The [ReminderAlertOpeningEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderAlertOpeningEventArgs.html) has the following properties,
* [Reminders](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ReminderAlertOpeningEventArgs.html#Syncfusion_UI_Xaml_Scheduler_ReminderAlertOpeningEventArgs_Reminders): Gets a list of reminders that are used to notify the appointment reminders.
* `Cancel`: To avoid the reminder notify by enabling this property.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}
scheduler.ReminderAlertOpening += Scheduler_ReminderAlertOpening;

private void Scheduler_ReminderAlertOpening(object sender, ReminderAlertOpeningEventArgs e)
{
    var reminders = e.Reminders;
    var appointment = e.Reminders[0].Appointment;
}
{% endhighlight %}
{% endtabs %}