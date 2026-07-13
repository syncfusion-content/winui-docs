---
layout: post
title: Appointments in WinUI Scheduler control | Syncfusion
description: Learn here all about to plan, configure and manage all day, recurrence and spanning appointments in Syncfusion WinUI Scheduler (SfScheduler) control and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Appointments in WinUI Scheduler (SfScheduler)

The [WinUI Scheduler](https://www.syncfusion.com/winui-controls/scheduler) control has a built-in capability to handle appointment arrangement internally based on the [ScheduleAppointmentCollection](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointmentCollection.html). The scheduler supports rendering normal appointments, all-day appointments, spanned appointments, recurring appointments, and recurrence exception date appointments.
The [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html) is a class that includes the specific scheduled appointment. It has some basic properties such as [StartTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_StartTime), [EndTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_EndTime), and [Subject](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Subject), and additional information about the appointment can be added with the [Notes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Notes), [Location](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Location), and [IsAllDay](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_IsAllDay) properties.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

{% include_relative code-snippet/weekview.xaml %}

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="14" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for the schedule appointment collection.
var scheduleAppointmentCollection = new ScheduleAppointmentCollection();
//Adding the schedule appointment in the schedule appointment collection.
scheduleAppointmentCollection.Add(new ScheduleAppointment
{
    StartTime = DateTime.Now.Date.AddHours(10),
    EndTime = DateTime.Now.Date.AddHours(12),
    Subject = "Client Meeting"
});

//Adding the schedule appointment collection to the ItemSource of SfScheduler.
this.Schedule.ItemsSource = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs %}

![schedule-appointment-in-winui-scheduler](Appointment_Images/schedule-appointment-in-winui-scheduler.png)

N> 
* The Scheduler supports the functionality to arrange appointments according to their start time and duration for normal appointments in the Day, Week, and WorkWeek views.
*  In Timeline views, all the appointments (spanned, all-day, and normal) are ordered and rendered based on the start date-time of the appointment, followed by the time duration of the appointment, `IsSpanned,` `IsAllDay,` and normal appointments.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/ScheduleAppointment)

## Scheduler item source and Mapping

The WinUI Scheduler supports binding any collection that implements the `IEnumerable` interface to populate appointments. Map the properties in the business object to [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html) by configuring the [AppointmentMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html) property. The following table shows the property mapping details for `ScheduleAppointment.`

<table>
<tr><th>Property Name</th><th>Description</th></tr>
<tr><td>{{'[StartTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_StartTime)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the StartTime of ScheduleAppointment.</td></tr>
<tr><td>{{'[EndTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_EndTime)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the EndTime of ScheduleAppointment.</td></tr>
<tr><td>{{'[StartTimeZone](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_StartTimeZone)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the StartTimeZone of ScheduleAppointment.</td></tr>
<tr><td>{{'[EndTimeZone](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_EndTimeZone)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the EndTimeZone of ScheduleAppointment.</td></tr>
<tr><td>{{'[Subject](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Subject)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the Subject of ScheduleAppointment.</td></tr>
<tr><td>{{'[Id](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Id)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the Id of ScheduleAppointment.</td></tr>
<tr><td>{{'[AppointmentBackground](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_AppointmentBackground)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the AppointmentBackground of ScheduleAppointment.</td></tr>
<tr><td>{{'[Foreground](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Foreground)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the  Foreground of ScheduleAppointment.</td></tr>
<tr><td>{{'[IsAllDay](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_IsAllDay)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the IsAllDay of ScheduleAppointment.</td></tr>
<tr><td>{{'[RecurrenceRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the RecurrenceRule of ScheduleAppointment.</td></tr>
<tr><td>{{'[RecurrenceId](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceId)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the RecurrenceId of ScheduleAppointment.</td></tr>
<tr><td>{{'[Notes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Notes)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the Notes of ScheduleAppointment.</td></tr>
<tr><td>{{'[Location](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Location)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the Location of ScheduleAppointment.</td></tr>
<tr><td>{{'[RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the RecurrenceExceptionDates of ScheduleAppointment.</td></tr>
<tr><td>{{'[ResourceIdCollection](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_ResourceIdCollection)'| markdownify }}</td>
<td>Maps the property name of a business object class, which is equivalent to the ResourceIdCollection of ScheduleAppointment.</td></tr>
</table>

N> The business object class should contain event start and end DateTime fields as mandatory.

## Creating business objects
Create a business object class `Meeting` with the mandatory fields `From`, `To`, and `EventName`.

{% tabs %}
{% highlight c# tabtitle="Meeting.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

/// <summary>   
/// Represents the business object data properties.   
/// </summary> 
public class Meeting
{
	public string EventName { get; set; }
	public DateTime From { get; set; }
	public DateTime To { get; set; }
    public Brush BackgroundColor { get; set; }
    public Brush ForegroundColor { get; set; }
}
{% endhighlight %}
{% endtabs %}

Map those properties of the `Meeting` class to the schedule appointment by using the `AppointmentMapping` properties.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6 7 8 9 10 11 12 13" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" ViewType="Week">
        <scheduler:SfScheduler.AppointmentMapping>
            <scheduler:AppointmentMapping
                Subject="EventName"
                StartTime="From"
                EndTime="To"
                AppointmentBackground="BackgroundColor"
                Foreground="ForegroundColor"/>
        </scheduler:SfScheduler.AppointmentMapping>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="4 10" %}
using Syncfusion.UI.Xaml.Scheduler;

//Schedule data mapping for business objects.
AppointmentMapping dataMapping = new AppointmentMapping();
dataMapping.Subject = "EventName";
dataMapping.StartTime = "From";
dataMapping.EndTime = "To";
dataMapping.AppointmentBackground = "BackgroundColor";
dataMapping.Foreground = "ForegroundColor";
this.Schedule.AppointmentMapping = dataMapping;
{% endhighlight %}
{% endtabs %}

Schedule meetings for a day by setting the `From` and `To` of the `Meeting` class. Create meetings of type `ObservableCollection<Meeting>` and assign the `Meetings` collection to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) property, which is of `IEnumerable` type.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="20" %}
using Syncfusion.UI.Xaml.Scheduler;

//Creating an instance for the business object class.
Meeting meeting = new Meeting();
//Setting the start time of an event.
meeting.From = new DateTime(2021, 03, 23, 10, 0, 0);
//Setting the end time of an event.
meeting.To = meeting.From.AddHours(2);
//Setting the subject for an event.
meeting.EventName = "Meeting";
//Setting the background color for an event.
meeting.BackgroundColor = new SolidColorBrush(Colors.Green);
//Setting the foreground color for an event.
meeting.ForegroundColor = new SolidColorBrush(Colors.White);
//Creating an instance for the collection of business objects.
var Meetings = new ObservableCollection<Meeting>();
//Adding a business object to the business object Collection.
Meetings.Add(meeting);
//Adding business object in the ItemsSource of SfScheduler.
Schedule.ItemsSource = Meetings;
{% endhighlight %}
{% endtabs%}

![business-objects-in-winui-scheduler](Appointment_Images/custom-appointment-in-winui-scheduler.png)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/BusinessObject)

## Spanned appointments

A spanned appointment is an appointment that lasts more than 24 hours. It does not block out time slots in the WinUI Scheduler; it is rendered in the [AllDayAppointmentPanel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AllDayAppointmentPanel.html) exclusively.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" ViewType="Week">
        <scheduler:SfScheduler.AppointmentMapping>
            <scheduler:AppointmentMapping
                Subject="EventName"
                StartTime="From"
                EndTime="To"
                AppointmentBackground="BackgroundColor"
                Foreground="ForegroundColor"/>
        </scheduler:SfScheduler.AppointmentMapping>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="8 10" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for the collection of business objects.
var Meetings = new ObservableCollection<Meeting>();
// Creating an instance for the business object class.
Meeting meeting = new Meeting();
// Setting the start time of an event.
meeting.From = new DateTime(2021, 03, 23, 10, 0, 0);
// Setting the end time of an event.
meeting.To = meeting.From.AddDays(2).AddHours(1);
// Setting the subject for an event.
meeting.EventName = "Meeting";
// Setting the background color for an event.
meeting.BackgroundColor = new SolidColorBrush(Colors.MediumPurple);
// Setting the foreground color for an event.
meeting.ForegroundColor = new SolidColorBrush(Colors.White);
// Adding a business object in the business object collection.
Meetings.Add(meeting);
//Adding schedule appointment collection to the ItemsSource of SfScheduler.
Schedule.ItemsSource = Meetings;
{% endhighlight %}
{% endtabs%}

![spanned-appointment-in-winui-scheduler](Appointment_Images/spanned-appointment-in-winui-scheduler.png)

## All day appointments

An all-day appointment is an appointment that is scheduled for a whole day. It can be set by using the [IsAllDay](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_IsAllDay) property in the [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html).

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

{% include_relative code-snippet/weekview.xaml %}

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="14" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for the schedule appointment collection.
var scheduleAppointmentCollection = new ScheduleAppointmentCollection();
//Adding schedule appointment in the schedule appointment collection. 
scheduleAppointmentCollection.Add(new ScheduleAppointment()
{
    StartTime = new DateTime(2021, 03, 23, 10, 0, 0),
    EndTime = new DateTime(2021, 03, 23, 12, 0, 0),
    Subject = "Client Meeting",
    Location = "Hutchison road",
    AppointmentBackground = new SolidColorBrush(Colors.AliceBlue),
    Foreground = new SolidColorBrush(Colors.White),
    IsAllDay = true,
});
//Adding the schedule appointment collection to the ItemsSource of SfScheduler.
Schedule.ItemsSource = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs%}

![all-day-appointment-in-winui-scheduler](Appointment_Images/all-day-appointment-in-winui-scheduler.png)

N> An appointment that lasts for an entire day (exactly 24 hours) will be considered as an all-day appointment without setting the [IsAllDay](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_IsAllDay) property. For example: From 06/29/2020 12:00 AM to 06/30/2020 12:00 AM.

## Recurrence appointment

Recurring appointments can be set on a daily, weekly, monthly, or yearly interval. Recurring appointments can be created by setting the [RecurrenceRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule) property in [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html).

### Recurrence rule

The `RecurrenceRule` is a string value (RRULE) that contains the details of the recurring appointment, such as the repeat type (daily, weekly, monthly, or yearly). It also contains details about how many times it needs to be repeated, the interval duration, the time period to render the appointment, and more. The [RecurrenceRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule) has the following properties, and based on the property values, the recurring appointments are rendered in the SfScheduler with their respective time periods.

<table>
<tr><th>PropertyName</th>
<th>Purpose</th></tr>
<tr><td>FREQ</td>
<td>Maintains the repeat type value of the appointment. (Example: Daily, Weekly, Monthly, Yearly, Every weekday) Example: FREQ=DAILY;INTERVAL=1</td></tr>
<tr><td>INTERVAL</td>
<td>Maintains the interval value of the appointments. For example, while creating a daily appointment at an interval of 2, the appointments are rendered on Monday, Wednesday, and Friday (creates the appointment on all days by leaving a gap of one day). Example: FREQ=DAILY;INTERVAL=1</td></tr>
<tr><td>COUNT</td>
<td>Holds the appointment's count value. For example, when the recurring appointment count value is 10, 10 appointments are created in the recurrence series. Example: FREQ=DAILY;INTERVAL=1;COUNT=10</td></tr>
<tr><td>UNTIL</td>
<td>This property is used to store the recurrence end date value. For example, while setting the end date of the appointment to 6/30/2020, the UNTIL property holds the end date value when the recurrence actually ends. Example: FREQ=DAILY;INTERVAL=1;UNTIL=20200725</td></tr>
<tr><td>BYDAY</td>
<td>Holds the "DAY" values of an appointment to render. For example, to create a weekly appointment, select the day(s) from the day options (Monday/Tuesday/Wednesday/Thursday/Friday/Saturday/Sunday). When Monday is selected, the first two letters of the selected day "MO" are stored in the "BYDAY" property. When selecting multiple days, the values are separated by commas. Example: FREQ=WEEKLY;INTERVAL=1;BYDAY=MO,WE;COUNT=10</td></tr>
<tr><td>BYMONTHDAY</td>
<td>This property is used to store the date value of the month while creating a monthly recurring appointment. For example, while creating a monthly recurring appointment on the date 3, BYMONTHDAY holds the value 3 and creates the appointment on the 3rd day of every month. Example: FREQ=MONTHLY;BYMONTHDAY=3;INTERVAL=1;COUNT=10</td></tr>
<tr><td>BYMONTH</td>
<td>This property is used to store the index value of the selected month while creating yearly appointments. For example, while creating a yearly appointment in June, the index value for June is 6 and is stored in the BYMONTH field. The appointment is created on every 6th month of a year. Example: FREQ=YEARLY;BYMONTHDAY=16;BYMONTH=6;INTERVAL=1;COUNT=10</td></tr>
<tr><td>BYSETPOS</td>
<td>This property is used to store the index value of the week. For example, while creating a monthly appointment in the second week of the month, the index value of the second week (2) is stored in BYSETPOS. Example: FREQ=MONTHLY;BYDAY=MO;BYSETPOS=2;UNTIL=20200725</td></tr>
</table>

### Creating the schedule recurrence appointment

The WinUI Scheduler appointment `RecurrenceRule` is used to populate the required recurring appointment collection in a specific pattern. The RRULE can be directly set to the [RecurrenceRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule) property of [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html).

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

{% include_relative code-snippet/weekview.xaml %}

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for schedule appointment collection.
var scheduleAppointmentCollection = new ScheduleAppointmentCollection();
//Adding schedule appointment in the schedule appointment collection. 
var scheduleAppointment = new ScheduleAppointment()
{
    Id = 1,
    StartTime = new DateTime(2021, 03, 28, 11, 0, 0),
    EndTime = new DateTime(2021, 03, 28, 12, 0, 0),
    Subject = "Occurs every alternate day",
    AppointmentBackground = new SolidColorBrush(Colors.RoyalBlue),
    Foreground = new SolidColorBrush(Colors.White),
};
//Creating a recurrence rule
scheduleAppointment.RecurrenceRule = "FREQ=DAILY;INTERVAL=2;COUNT=10";
//Adding the schedule appointment to the schedule appointment collection.
scheduleAppointmentCollection.Add(scheduleAppointment);
//Adding the schedule appointment collection to the ItemsSource of SfScheduler.
Schedule.ItemsSource = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs%}

![recurrence-appointment-in-winui-scheduler](Appointment_Images/recurrence-appointment-in-winui-scheduler.png)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecurringAppointment/ScheduleAppointment)

### Creating the business object recurrence appointment

To create a business object recurrence appointment, create a business object class `Meeting` with the mandatory fields `From`, `To`, and `RecurrenceRule`.

{% tabs %}
{% highlight c# tabtitle="Meeting.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

/// <summary>   
/// Represents the business object data properties.   
/// </summary> 
public class Meeting
{
	public string EventName { get; set; }
	public DateTime From { get; set; }
	public DateTime To { get; set; }
    public Brush BackgroundColor { get; set; }
    public Brush ForegroundColor { get; set; }
    public string RecurrenceRule { get; set; }
    public object Id {get; set;}
}
{% endhighlight %}
{% endtabs %}

 Map those properties of the `Meeting` class to the schedule appointments by using the `AppointmentMapping` properties.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="6 7 8 9 10 11 12 13 14 15" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" ViewType="Week">
        <scheduler:SfScheduler.AppointmentMapping>
            <scheduler:AppointmentMapping
                Subject="EventName"
                StartTime="From"
                EndTime="To"
                AppointmentBackground="BackgroundColor"
                Foreground="ForegroundColor"
                Id="Id"
                RecurrenceRule="RecurrenceRule"/>
        </scheduler:SfScheduler.AppointmentMapping>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="4 12" %}
using Syncfusion.UI.Xaml.Scheduler;

//Schedule data mapping for business objects.
AppointmentMapping dataMapping = new AppointmentMapping();
dataMapping.Subject = "EventName";
dataMapping.StartTime = "From";
dataMapping.EndTime = "To";
dataMapping.AppointmentBackground = "BackgroundColor";
dataMapping.Foreground = "ForegroundColor";
dataMapping.Id = "Id";
dataMapping.RecurrenceRule = "RecurrenceRule";
this.Schedule.AppointmentMapping = dataMapping;
{% endhighlight %}
{% endtabs %}

Schedule the recurring meetings for daily, weekly, monthly, or yearly intervals by setting the [RecurrenceRule](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule) of the `Meeting` class. Create meetings of type `ObservableCollection<Meeting>` and assign the `Meetings` collection to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) property, which is of `IEnumerable` type.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

//Creating an instance for the business object class.
Meeting meeting = new Meeting();
//Setting the start time of an event.
meeting.From = new DateTime(2021, 03, 28, 10, 0, 0);
//Setting the end time of an event.
meeting.To = meeting.From.AddHours(2);
//Setting the subject for an event.
meeting.EventName = "Meeting";
//Setting the background color for an event.
meeting.BackgroundColor = new SolidColorBrush(Colors.Green);
//Setting the foreground color for an event.
meeting.ForegroundColor = new SolidColorBrush(Colors.White);
//Creating a recurrence rule.
meeting.RecurrenceRule = "FREQ=DAILY;INTERVAL=2;COUNT=10";
// Setting the Id of an event.
meeting.Id = 1;
var Meetings = new ObservableCollection<Meeting>();
//Adding a business object in the business object collection.
Meetings.Add(meeting);
//Adding business objects in the ItemsSource of SfScheduler.
Schedule.ItemsSource = Meetings;
{% endhighlight %}
{% endtabs%}

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecurringAppointment/BusinessObject)

#### How to get the recurrence editor field values from RRULE?

Get the Recurrence properties from the [RRULE](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_CreateRRule_Syncfusion_UI_Xaml_Scheduler_RecurrenceProperties_System_DateTime_System_DateTime_) using the [RRuleParser](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_RRuleParser_System_String_System_DateTime_) method of SfScheduler.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="4" %}
using Syncfusion.UI.Xaml.Scheduler;

DateTime dateTime = new DateTime(2021, 3, 28, 10, 0, 0);
RecurrenceProperties recurrenceProperties = RecurrenceHelper.RRuleParser("FREQ=DAILY;INTERVAL=1;COUNT=3", dateTime);
{% endhighlight %}
{% endtabs%}

Recurrence properties retrieved from above method,
recurrenceProperties.RecurrenceType = RecurrenceType.Daily;
recurrenceProperties.Interval = 1;
recurrenceProperties.RecurrenceCount = 3;
recurrenceProperties.RecurrenceRange = RecurrenceRange.Count;

#### How to get the recurrence dates from RRULE?

Get the occurrence date-time list of a recurring appointment from the RRULE using the [GetRecurrenceDateTimeCollection](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetRecurrenceDateTimeCollection_System_String_System_DateTime_System_Nullable_System_DateTime__System_Nullable_System_DateTime__) method of SfScheduler.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="4" %}
using Syncfusion.UI.Xaml.Scheduler;

DateTime dateTime = new DateTime(2021, 3, 28, 9, 0, 0);
IEnumerable<DateTime> dateCollection = RecurrenceHelper.GetRecurrenceDateTimeCollection("FREQ=DAILY;INTERVAL=1;COUNT=3", dateTime);
{% endhighlight %}
{% endtabs%}

The following occurrence dates can be retrieved from the given RRULE:
var date0 = 28-03-2021 09:00:00;
var date1 = 29-03-2021 09:00:00;
var date2 = 30-03-2021 09:00:00;

#### How to get pattern appointment for the specified occurrence?

Gets the [pattern appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetPatternAppointment_Syncfusion_UI_Xaml_Scheduler_SfScheduler_System_Object_) for the specified occurrence.

To get the pattern appointment, use the following event and pass a parameter as `Scheduler` and the specified `Appointment`.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}
using Syncfusion.UI.Xaml.Scheduler;

this.Schedule.AppointmentTapped += Schedule_AppointmentTapped; 

private void Schedule_AppointmentTapped(object sender, AppointmentTappedArgs e)
{
    if (e.Appointment != null)
    {
        var patternAppointment = RecurrenceHelper.GetPatternAppointment(this.Schedule, e.Appointment);
    }
}
{% endhighlight %}
{% endtabs%}

N>
* For a business object, pass `e.Appointment.Data` as a parameter and get the business object details from the `Data` property of `ScheduleAppointment.`
* If a specified occurrence is changed, the [GetPatternAppointment()](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetPatternAppointment_Syncfusion_UI_Xaml_Scheduler_SfScheduler_System_Object_) returns the pattern appointment of the exception appointment.

#### How to get occurrence appointment at the specified date?

Get an [occurrence appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetOccurrenceAppointment_Syncfusion_UI_Xaml_Scheduler_SfScheduler_System_Object_System_DateTime_) at the specified date within a series of recurring appointments.

To get a specific appointment, use the following event and pass a parameter as `Scheduler`, the specified `Appointment`, and the specified `DateTime`.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}
using Syncfusion.UI.Xaml.Scheduler;

this.Schedule.AppointmentTapped += Schedule_AppointmentTapped; 

private void Schedule_AppointmentTapped(object sender, AppointmentTappedArgs e)
{
    if (e.Appointment != null)
    {
        var occurrenceAppointment = RecurrenceHelper.GetOccurrenceAppointment(this.Schedule, e.Appointment, new DateTime(2021, 3, 30));
    }
}
{% endhighlight %}
{% endtabs%}

N> If an occurrence at the specified date is deleted or not present, then the [GetOccurrenceAppointment()](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetOccurrenceAppointment_Syncfusion_UI_Xaml_Scheduler_SfScheduler_System_Object_System_DateTime_) returns null.

## Recurrence pattern exceptions

Delete or change any recurring pattern appointment by handling exception dates and exception appointments for that recurring appointment.

#### Recurrence exception dates

Delete any occurrence appointment that is an exception from the recurrence pattern appointment by adding exception dates to the recurring appointment.

#### Recurrence exception appointment

Change any occurrence appointment that is an exception from the recurrence pattern appointment by adding the recurrence exception appointment in the WinUI Scheduler [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource).

### Creating the recurrence exceptions for schedule appointment

Add the recurrence exception appointments and recurrence exception dates to `ScheduleAppointment` or remove them from the [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html) by using its [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates) property.

#### Delete occurrence from recurrence pattern appointment or adding exception dates to recurrence pattern for schedule appointment

Delete any occurrence that is an exception from the recurrence pattern appointment by using the [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates) property of [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html). The deleted occurrence date will be considered as a recurrence exception date.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

{% include_relative code-snippet/weekview.xaml %}

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for the schedule appointment collection.
var scheduleAppointmentCollection = new ScheduleAppointmentCollection();

// Recurrence and exception appointment.
var scheduleAppointment = new ScheduleAppointment
{
    Id = 1,
    Subject = "Daily scrum meeting",
    StartTime = new DateTime(2021, 03, 28, 11, 0, 0),
    EndTime = new DateTime(2021, 03, 28, 12, 0, 0),
    AppointmentBackground = new SolidColorBrush(Colors.LimeGreen),
    Foreground = new SolidColorBrush(Colors.White),
    RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=10"
};
//Adding the recurring or pattern appointment to the Schedule AppointmentCollection.
scheduleAppointmentCollection.Add(scheduleAppointment);

//Add the ExceptionDates to avoid occurrence on specific dates.
DateTime exceptionDate = scheduleAppointment.StartTime.AddDays(3).Date;
scheduleAppointment.RecurrenceExceptionDates = new ObservableCollection<DateTime>()
{
    exceptionDate,
};

//Setting AppointmentCollection as ItemSource of SfScheduler.
this.Schedule.ItemsSource = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs %}

![exception-dates-to-recurrence-pattern-appointment-in-winui-scheduler](Appointment_Images/exception-dates-to-recurrence-pattern-appointment-in-winui-scheduler.png)

N> Exception dates should be Universal Time Coordinates (UTC) time zone.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecursiveExceptionAppointment/ScheduleAppointment)

#### Add exception appointment to the recurrence pattern for schedule appointment

Also add an exception appointment that is a changed or modified occurrence of the recurrence pattern appointment to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) of the Scheduler. To add a changed occurrence, ensure to set the [RecurrenceId](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceId) of that occurrence and add the date of that occurrence to the [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates) of the recurrence pattern appointment. The [RecurrenceId](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceId) of the changed occurrence should hold the exact recurrence pattern appointment [Id](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Id).

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

{% include_relative code-snippet/weekview.xaml %}

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for schedule appointment collection.
var appointmentCollection = new ScheduleAppointmentCollection();
// Recurrence and exception appointment.
var scheduleAppointment = new ScheduleAppointment
{
    Id = 1,
    Subject = "Daily scrum meeting",
    StartTime = new DateTime(2021, 3, 28, 11, 0, 0),
    EndTime = new DateTime(2021, 3, 28, 12, 0, 0),
    AppointmentBackground = new SolidColorBrush(Colors.DeepSkyBlue),
    Foreground = new SolidColorBrush(Colors.White),
    RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=10"
};
//Adding the recurring or pattern appointment to the AppointmentCollection.
appointmentCollection.Add(scheduleAppointment);

//Add ExceptionDates to avoid occurrence on specific dates.
DateTime changedExceptionDate = scheduleAppointment.StartTime.AddDays(3).Date;
scheduleAppointment.RecurrenceExceptionDates = new ObservableCollection<DateTime>()
{
    changedExceptionDate,
};

//Creating an exception occurence appointment by changing the start time or end time. 
// RecurrenceId is set to 1, so it will be the changed occurence for the above-created pattern appointment. 
var exceptionAppointment = new ScheduleAppointment()
{
    Id = 2,
    Subject = "Scrum meeting - Changed Occurrence",
    StartTime = new DateTime(changedExceptionDate.Year, changedExceptionDate.Month, changedExceptionDate.Day, 13, 0, 0),
    EndTime = new DateTime(changedExceptionDate.Year, changedExceptionDate.Month, changedExceptionDate.Day, 14, 0, 0),
    AppointmentBackground = new SolidColorBrush(Colors.DeepPink),
    Foreground = new SolidColorBrush(Colors.White),
    RecurrenceId = 1
};
// Adding an exception occurence appointment to the AppointmentCollection.
appointmentCollection.Add(exceptionAppointment);
//Setting the AppointmentCollection as a ItemSource of SfScheduler.
this.Schedule.ItemsSource = appointmentCollection;
{% endhighlight %}
{% endtabs %}

![exception-appointment-to-the-recurrence-pattern-in-winui-scheduler](Appointment_Images/exception-appointment-to-the-recurrence-pattern-in-winui-scheduler.png)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecursiveExceptionAppointment/ScheduleAppointment)

N>
* The `RecurrenceId` of an exception appointment and the `Id` of its pattern appointment should have the same value.
* The exception recurrence appointment does not have the `RecurrenceRule`, so for an exception appointment, it will be reset to empty.
* The exception appointment should have a different `Id` from the original pattern appointment `Id`.
* The exception appointment should be a normal appointment and should not be created as a recurring appointment, since its occurrence is from a recurrence pattern.
* The `RecurrenceExceptionDates` should be in Universal Time Coordinated (UTC) time zone.

### Create the recurrence exceptions for business object

Add the recurrence exception appointments and recurrence exception dates to the business object, or remove them from the business object. A business object class `Meeting` can be created with the mandatory fields [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates) and [RecurrenceId](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceId).

#### Delete occurrence from the recurrence pattern appointment or adding exception dates to recurrence pattern for business object

Delete any occurrence that is an exception from the recurrence pattern appointment by using the [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html#Syncfusion_UI_Xaml_Scheduler_AppointmentMapping_RecurrenceExceptionDates) property of the [AppointmentMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html) class, which is used to map the exception dates to the schedule recurrence appointment. The deleted occurrence date will be considered as a recurrence exception date.
To add the exception dates in the recurrence series of a business object, add the `RecurrenceExceptionDates`, `EventName`, `From`, `To`, `Color`, and `RecurrenceRule` properties to the business object class `Meeting`.

{% tabs %}
{% highlight c# tabtitle="Meeting.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

public class Meeting
{
    public ObservableCollection<DateTime> RecurrenceExceptions { get; set; } = new ObservableCollection<DateTime>();
    public string EventName { get; set; }
    public DateTime From { get; set; }
    public DateTime To { get; set; }
    public object Id { get; set; }
    public Brush BackgroundColor { get; set; }
    public Brush ForegroundColor { get; set; }
    public string RecurrenceRule { get; set; }
    public object RecurrenceId { get; set; }
}
{% endhighlight %}
{% endtabs %}

Map the property `RecurrenceExceptionDates` of business object class with the `RecurrenceExceptionDates` property of `AppointmentMapping` class to map the exception dates to the scheduled appointment.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" 
                            ViewType="Week">
        <scheduler:SfScheduler.AppointmentMapping>
            <scheduler:AppointmentMapping
                Subject="EventName"
                StartTime="From"
                EndTime="To"
                Id="Id"
                AppointmentBackground="BackgroundColor"
                Foreground="ForegroundColor"
                IsAllDay="IsAllDay"
                StartTimeZone="StartTimeZone"
                RecurrenceRule="RecurrenceRule"
                RecurrenceExceptionDates="RecurrenceExceptions"
                EndTimeZone="EndTimeZone"
                RecurrenceId="RecurrenceId"/>
        </scheduler:SfScheduler.AppointmentMapping>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="19 20 21 22" %}
using Syncfusion.UI.Xaml.Scheduler;

// Creating an instance for business object collection.
ObservableCollection<Meeting> customAppointmentCollection = new ObservableCollection<Meeting>();
var exceptionDate = new DateTime(2021, 04, 01);
//Adding business object in the business object collection. 
var recurrenceAppointment = new Meeting()
{
    From = new DateTime(2021, 03, 28, 10, 0, 0),
    To = new DateTime(2021, 03, 28, 11, 0, 0),
    EventName = "Occurs Daily",
    BackgroundColor = new SolidColorBrush(Colors.LightSeaGreen),
    ForegroundColor = new SolidColorBrush(Colors.White),
    Id = 1
};
// Creating a recurrence rule.
recurrenceAppointment.RecurrenceRule = "FREQ=DAILY;COUNT=20";
// Add RecurrenceExceptionDates to appointment.
recurrenceAppointment.RecurrenceExceptions = new ObservableCollection<DateTime>()
{
    exceptionDate
};
//Adding business object in the business object collection.
customAppointmentCollection.Add(recurrenceAppointment);
//Adding business object collection to the ItemsSource of SfScheduler.
this.Schedule.ItemsSource = customAppointmentCollection;
{% endhighlight %}
{% endtabs %}

![custom-exception-dates-to-the-recurrence-pattern-in-winui-scheduler](Appointment_Images/custom-exception-dates-to-the-recurrence-pattern-in-winui-scheduler.png)

N> Exception dates should be Universal Time Coordinates (UTC) time zone.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecursiveExceptionAppointment/BusinessObject)

#### Add an exception appointment to the recurrence pattern for business object

Also add an exception appointment that is a changed or modified occurrence of the recurrence pattern appointment to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) of the Scheduler. To add the changed occurrence, ensure to set the [RecurrenceId](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceId) of that occurrence and add the date of that occurrence to [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceExceptionDates) of the recurrence pattern appointment. The `RecurrenceId` of the changed occurrence should hold the exact recurrence pattern appointment [Id](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Id). Map the equivalent properties of `Id`, `RecurrenceId`, and `RecurrenceExceptionDates` from the business object to the [Id](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html#Syncfusion_UI_Xaml_Scheduler_AppointmentMapping_Id) and [RecurrenceExceptionDates](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html#Syncfusion_UI_Xaml_Scheduler_AppointmentMapping_RecurrenceExceptionDates) properties of [AppointmentMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html).

Add the created exception recurrence appointment to the SfScheduler `ItemsSource`.

{%tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

//// Creating an instance for schedule appointment collection.
public ObservableCollection<Meeting> RecursiveAppointmentCollection
{
    get;
    set;
}
{% endhighlight %}
{% endtabs %}

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" 
                            ViewType="Week">
        <scheduler:SfScheduler.AppointmentMapping>
            <scheduler:AppointmentMapping
                Subject="EventName"
                StartTime="From"
                EndTime="To"
                Id="Id"
                AppointmentBackground="BackgroundColor"
                Foreground="ForegroundColor"
                IsAllDay="IsAllDay"
                StartTimeZone="StartTimeZone"
                RecurrenceRule="RecurrenceRule"
                RecurrenceExceptionDates="RecurrenceExceptions"
                EndTimeZone="EndTimeZone"
                RecurrenceId="RecurrenceId"/>
        </scheduler:SfScheduler.AppointmentMapping>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

this.RecursiveAppointmentCollection = new ObservableCollection<Meeting>();
//Adding business object in the business object collection. 
Meeting dailyEvent = new Meeting
{
    EventName = "Daily scrum meeting",
    From = new DateTime(2021, 03, 28, 11, 0, 0),
    To = new DateTime(2021, 03, 28, 12, 0, 0),
    BackgroundColor = new SolidColorBrush(Colors.DeepSkyBlue),
    ForegroundColor = new SolidColorBrush(Colors.White),
    RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=10",
    Id = 1
};
//Adding business object in the business object collection.
RecursiveAppointmentCollection.Add(dailyEvent);

//Add ExceptionDates to avoid occurrence on specific dates.
DateTime changedExceptionDate = DateTime.Now.AddDays(-1).Date;
dailyEvent.RecurrenceExceptions = new ObservableCollection<DateTime>()
{
    changedExceptionDate
};
//Change start time or end time of an occurrence.
Meeting changedEvent = new Meeting
{
    EventName = "Scrum meeting - Changed Occurrence",
    From = new DateTime(changedExceptionDate.Year, changedExceptionDate.Month, changedExceptionDate.Day, 13, 0, 0),
    To = new DateTime(changedExceptionDate.Year, changedExceptionDate.Month, changedExceptionDate.Day, 14, 0, 0),
    BackgroundColor = new SolidColorBrush(Colors.DeepPink),
    ForegroundColor = new SolidColorBrush(Colors.White),
    RecurrenceRule = "FREQ=DAILY;INTERVAL=1;COUNT=10",
    Id = 2,
    RecurrenceId = 1
};
RecursiveAppointmentCollection.Add(changedEvent);
//Adding business object collection to the ItemsSource of SfScheduler.
this.Schedule.ItemsSource = RecursiveAppointmentCollection;
{% endhighlight %}
{% endtabs %}

![exception-custom-appointment-to-the-recurrence-pattern-in-winui-scheduler](Appointment_Images/exception-custom-appointment-to-the-recurrence-pattern-in-winui-scheduler.png)

N>
* The `RecurrenceId` of the exception appointment and the `Id` of its pattern appointment should have the same value.
* The exception recurrence appointment does not have the `RecurrenceRule`, so for an exception appointment, it will be reset to empty.
* The exception appointment should have a different `Id` from the original pattern appointment `Id`.
* The exception appointment should be a normal appointment and should not be created as a recurring appointment, since its occurrence is from a recurrence pattern.
* The `recurrenceExceptions` should be in Universal Time Coordinated (UTC) time zone.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/RecursiveExceptionAppointment/BusinessObject)

## Appointment tooltip

An interactive tooltip provides additional details about the appointments on hovering the mouse over them.

### Enable tooltip for appointments

To enable tooltip for the scheduler appointments, use the [EnableToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_EnableToolTip) property of [SfScheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html). By default, [EnableToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_EnableToolTip) is set to `false`. To provide users with additional information or context about appointments, simply set this property to `true`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
     <scheduler:SfScheduler x:Name="Schedule"
                            EnableToolTip="True">
     </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
using Syncfusion.UI.Xaml.Scheduler;

this.Schedule.EnableToolTip = true;
{% endhighlight %}
{% endtabs %}

![appointment-tool-tip-support-in-winui-scheduler](Appointment_Images/appointment-tool-tip-support-in-winui-scheduler.gif)


### Customize tooltip appearance

You can customize the tooltip appearance by using the [ToolTipTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ToolTipTemplate) property in the [SfScheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html).

The following code example shows the usage of `DataTemplate`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule"
                           EnableToolTip="True">
     <scheduler:SfScheduler.ToolTipTemplate>
        <DataTemplate>
            <Border Background="Black"
                    CornerRadius="4"
                    Padding="5">
                <Grid>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="*" />
                    </Grid.ColumnDefinitions>
                    <Rectangle Fill="{Binding AppointmentBackground}"
                               Grid.Column="0"
                               VerticalAlignment="Stretch"
                               HorizontalAlignment="Left"
                               Width="10"
                               Margin="0,0,5,0" />
                    <StackPanel Grid.Column="1"
                                Orientation="Vertical">
                        <TextBlock Text="{Binding Subject}"
                                   TextWrapping="Wrap"
                                   FontWeight="Bold"
                                   FontSize="12"
                                   Foreground="White"
                                   TextTrimming="CharacterEllipsis"
                                   Margin="0,0,0,5" />
                        <StackPanel Orientation="Horizontal">
                            <TextBlock Text="Start Time: " Margin="0,0,2,0"
                                       FontWeight="Bold"
                                       FontSize="12"
                                       Foreground="White" />
                            <TextBlock Text="{Binding StartTime}"
                                       FontSize="12"
                                       Foreground="White" />
                        </StackPanel>
                        <StackPanel Orientation="Horizontal">
                            <TextBlock Text="End Time: " Margin="0,0,2,0"
                                       FontWeight="Bold"
                                       FontSize="12"
                                       Foreground="White" />
                            <TextBlock Text="{Binding EndTime}"
                                       FontSize="12"
                                       Foreground="White" />
                        </StackPanel>
                    </StackPanel>
                </Grid>
            </Border>
        </DataTemplate>
     </scheduler:SfScheduler.ToolTipTemplate>
    </scheduler:SfScheduler>

</Window>
{% endhighlight %}
{% endtabs %}

![appointment-tool-tip-customization-support-in-winui-scheduler](Appointment_Images/appointment-tool-tip-customization-support-in-winui-scheduler.gif)

N>
* This property is only applicable when [EnableToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_EnableToolTip) is set to `true`.

## Appearance customization

The default appearance of a schedule appointment can be customized in all views by using the [AppointmentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewSettingsBase.html#Syncfusion_UI_Xaml_Scheduler_ViewSettingsBase_AppointmentTemplate) and [AppointmentTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewSettingsBase.html#Syncfusion_UI_Xaml_Scheduler_ViewSettingsBase_AppointmentTemplateSelector) properties of [ViewSettingsBase](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ViewSettingsBase.html). Use the [AllDayAppointmentTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DaysViewSettings.html#Syncfusion_UI_Xaml_Scheduler_DaysViewSettings_AllDayAppointmentTemplate) property of [DaysViewSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DaysViewSettings.html) to customize the appearance of all-day appointments in the Day, Week, and WorkWeek views.

{%tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <scheduler:SfScheduler x:Name="Schedule" ItemsSource="{Binding Appointments}" ViewType="Week">
        <scheduler:SfScheduler.DaysViewSettings>
            <scheduler:DaysViewSettings>
                <scheduler:DaysViewSettings.AppointmentTemplate>
                    <DataTemplate>
                        <StackPanel Background="{Binding Data.BackgroundColor}"  
                            VerticalAlignment="Stretch" 
                            HorizontalAlignment="Stretch"
                            Orientation="Horizontal">
                        <TextBlock Margin="5"
                             VerticalAlignment="Center"
                            Text="Meeting" 
                            TextTrimming="CharacterEllipsis"
                            Foreground="{Binding Data.ForegroundColor}"   
                            TextWrapping="Wrap"
                            FontStyle="Italic" 
                            TextAlignment="Left"
                            FontWeight="Normal"/>
                        </StackPanel>
                    </DataTemplate>
                </scheduler:DaysViewSettings.AppointmentTemplate>
            </scheduler:DaysViewSettings>
        </scheduler:SfScheduler.DaysViewSettings>
    </scheduler:SfScheduler>
</Window>
{% endhighlight %}
{% endtabs %}

![appearance-customization-in-winui-scheduler](Appointment_Images/appearance-customization-in-winui-scheduler.png)

N>  
* By default, the `ScheduleAppointment` is set as the `DataContext` for the `AppointmentTemplate` and `AppointmentTemplateSelector` for both `ScheduleAppointment` and business object in the `ItemsSource` of SfScheduler.
* The business object can be bound in the `AppointmentTemplate` and `AppointmentTemplateSelector` by using the property of `ScheduleAppointment.Data`.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/AppointmentCustomization)

### Appointment selection border brush
You can customize the appointment selection border brush by using the [SelectionBorderBrush](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentControl.html#Syncfusion_UI_Xaml_Scheduler_AppointmentControl_SelectionBorderBrush) property in the [AppointmentControl.](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentControl.html) If the `AppointmentControl` has a default style, the appointment selection border color will be updated based on the selected appointment background color.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<Window
    ...
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler">
    <Style TargetType="scheduler:AppointmentControl">
        <Setter Property="BorderBrush" Value="Blue" />
        <Setter Property="SelectionBorderBrush" Value="Red"/>
        <Setter Property="BorderThickness" Value="2"/>
    </Style>
</Window>
{% endhighlight %}
{% endtabs %}

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/AppointmentSelectionBorderBrush)
