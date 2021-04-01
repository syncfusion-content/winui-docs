---
layout: post
title: Load appointments on demand | WinUI | Scheduler | Syncfusion
description: This section explains how to load appointments on demand from visible date ranges in the Syncfusion WinUI Scheduler (SfScheduler)
platform: winui
control: Scheduler
documentation: ug
---

# Load On Demand in WinUI Scheduler (SfScheduler)

The scheduler supports to loading appointment on demand with loading indicator and it improves the loading performance when you have appointments range for multiple years.

![load-on-demand-from-visible-date-ranges-in-winui-scheduler](LoadOnDemand_Image/load-on-demand-from-visible-date-ranges-in-winui-scheduler.gif)

## QueryAppointments event

The `QueryAppointments` event is used to load appointments in on-demand for the visible date range. You might start and stop the loading indicator animation before and after the appointments loaded using the `ShowBusyIndicator`.
The `QueryAppointmentsEventArgs` has the following members which provide information for the `QueryAppointments` event.

`VisibleDateRange` : Gets the current visible date range of scheduler that is used to load the appointments.

{%tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"
                        ViewType="Month" QueryAppointments="Schedule_QueryAppointments" >
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# %}
this.Schedule.QueryAppointments += Schedule_QueryAppointments;

/// <summary>
///  current day meetings
/// </summary>
private List<string> currentDayMeetings;

/// <summary>
/// color collection
/// </summary>
private List<Brush> colorCollection;

private void Schedule_QueryAppointments(object sender, QueryAppointmentsEventArgs e)
{
    this.Schedule.ShowBusyIndicator = true;
    this.InitializeDataForBookings();
    this.Schedule.ItemsSource = this.GenerateSchedulerAppointments(e.VisibleDateRange);
    this.Schedule.ShowBusyIndicator = false;
}

private void InitializeDataForBookings()
{
    this.currentDayMeetings = new List<string>();
    this.currentDayMeetings.Add("General Meeting");
    this.currentDayMeetings.Add("Plan Execution");
    this.currentDayMeetings.Add("Project Plan");
    this.currentDayMeetings.Add("Consulting");
    this.currentDayMeetings.Add("Performance Check");
    this.currentDayMeetings.Add("Yoga Therapy");
    this.currentDayMeetings.Add("Plan Execution");
    this.currentDayMeetings.Add("Project Plan");
    this.currentDayMeetings.Add("Consulting");
    this.currentDayMeetings.Add("Performance Check");

    this.colorCollection = new List<Brush>();
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 133, 81, 242)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 140, 245, 219)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 83, 99, 250)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 255, 222, 133)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 45, 153, 255)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 253, 183, 165)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 198, 237, 115)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 253, 185, 222)));
    this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 83, 99, 250)));
}

    /// <summary>
    /// Method to generate the schedule appointments.
    /// </summary>
    /// <param name="dateRange"></param>
    /// <returns></returns>
    private IEnumerable GenerateSchedulerAppointments(DateRange dateRange)
    {
        Random ran = new Random();
        int daysCount = (dateRange.ActualEndDate - dateRange.ActualStartDate).Days;
        var appointments = new ScheduleAppointmentCollection();

        for (int i = 0; i < 50; i++)
        {
            var startTime = dateRange.ActualStartDate.AddDays(ran.Next(0, daysCount + 1)).AddHours(ran.Next(0, 24));
            appointments.Add(new ScheduleAppointment
            {
                StartTime = startTime,
                EndTime = startTime.AddHours(1),
                Subject = currentDayMeetings[ran.Next(0, currentDayMeetings.Count)],
                AppointmentBackground = colorCollection[ran.Next(0, colorCollection.Count)],
            });
        }
         return appointments;
}
{% endhighlight %}
{% endtabs %}

The `QueryAppointments` will be raised once any one of the following action will be taken.

Once the `ViewChanged` event is raised, the `QueryAppointments` will be raised.

If the appointment has been added, removed, or changed (Resize,drag, and drop) in the current time visible date range, then the `QueryAppointments` event will not be triggered. Since the appointments for that visible date range have been loaded already.

The `QueryAppointments` event is triggered when the Schedule `ResourceCollection` is updated to load appointments based on the changed resource collection.

The `QueryAppointments` event will be triggered when the `ResourceGroupType` is changed.

## Load On Demand command

The Scheduler notifies by `LoadOnDemandCommand` when the user changes the visible date range. You can get a visible date range from the `QueryAppointmentsEventArgs`. The default value for this `ICommand` is null. The `QueryAppointmentsEventArgs` passed as a command parameter.

You can define a ViewModel class that implements command and handle it by the `CanExecute` and `Execute` methods to check and execute on-demand loading. In execute method, you can perform the following operations,

* You can start and stop the loading indicator animation before and after the appointments loaded using the `ShowBusyIndicator`.
* Once got appointment collection, you can load into the scheduler `ItemsSource`.

{%tabs %}
{% highlight xaml %}
 <scheduler:SfScheduler x:Name="Schedule"  
                        ViewType="Month"
                        ShowBusyIndicator="{Binding ShowBusyIndicator}"
                        LoadOnDemandCommand="{Binding LoadOnDemandCommand}"
                        ItemsSource="{Binding Events}">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# %}
public class LoadOnDemandViewModel : NotificationObject
{
    public DelegateCommand LoadOnDemandCommand { get; set; }
    private IEnumerable events;
    public IEnumerable Events
    {
        get { return events; }
        set
        {
            events = value;
            this.RaisePropertyChanged("Events");
        }
    }

    private bool showBusyIndicator;
    public bool ShowBusyIndicator
    {
        get { return showBusyIndicator; }
        set
        {
            showBusyIndicator = value;
            this.RaisePropertyChanged("ShowBusyIndicator");
        }
    }

    public LoadOnDemandViewModel()
    {
        this.InitializeDataForBookings();
        this.LoadOnDemandCommand = new DelegateCommand(ExecuteOnDemandLoading, CanExecuteOnDemandLoading);
    }

    public event PropertyChangedEventHandler PropertyChanged;
    public async void ExecuteOnDemandLoading(object parameter)
    {
        this.ShowBusyIndicator = true;
        await Task.Delay(1000);
        Application.Current.Resources.DispatcherQueue.TryEnqueue(() =>
        {
            this.Events = this.GenerateSchedulerAppointments((parameter as QueryAppointmentsEventArgs).VisibleDateRange);
            });
            this.ShowBusyIndicator = false;
        }

        private bool CanExecuteOnDemandLoading(object sender)
        {
            return true;
        }

    /// <summary>
    ///  current day meetings
    /// </summary>
    private List<string> currentDayMeetings;

    /// <summary>
    /// color collection
    /// </summary>
    private List<Brush> colorCollection;

    private void InitializeDataForBookings()
    {
        this.currentDayMeetings = new List<string>();
        this.currentDayMeetings.Add("General Meeting");
        this.currentDayMeetings.Add("Plan Execution");
        this.currentDayMeetings.Add("Project Plan");
        this.currentDayMeetings.Add("Consulting");
        this.currentDayMeetings.Add("Performance Check");
        this.currentDayMeetings.Add("Yoga Therapy");
        this.currentDayMeetings.Add("Plan Execution");
        this.currentDayMeetings.Add("Project Plan");
        this.currentDayMeetings.Add("Consulting");
        this.currentDayMeetings.Add("Performance Check");

        this.colorCollection = new List<Brush>();
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 133, 81, 242)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 140, 245, 219)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 83, 99, 250)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 255, 222, 133)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 45, 153, 255)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 253, 183, 165)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 198, 237, 115)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 253, 185, 222)));
        this.colorCollection.Add(new SolidColorBrush(Color.FromArgb(255, 83, 99, 250)));
    }

    private IEnumerable GenerateSchedulerAppointments(DateRange dateRange)
    {
        Random ran = new Random();
        int daysCount = (dateRange.ActualEndDate - dateRange.ActualStartDate).Days;
        var appointments = new ScheduleAppointmentCollection();
        for (int i = 0; i < 50; i++)
        {
            var startTime = dateRange.ActualStartDate.AddDays(ran.Next(0, daysCount + 1)).AddHours(ran.Next(0, 24)); appointments.Add(new ScheduleAppointment
            {
                StartTime = startTime,
                EndTime = startTime.AddHours(1),
                Subject = currentDayMeetings[ran.Next(0, currentDayMeetings.Count)],
                AppointmentBackground = colorCollection[ran.Next(0, colorCollection.Count)],
            });
        }
        return appointments;
    }
}
{% endhighlight %}
{% endtabs %}

The `LoadOnDemandCommand` will be invoked once any one of the following actions will be taken.

* Once the ViewChanged event is raised, the `LoadOnDemandCommand` will also be raised.

* If the appointment has been added, removed, or changed (Resize, drag, and drop) in the current time visible date range, then the `LoadOnDemandCommand` will not be triggered. Since the appointments for that visible date range have been loaded already.

* The `LoadOnDemandCommand` is triggered when the Schedule `ResourceCollection` is updated to load the appointments based on the changed resource collection.

* The `LoadOnDemandCommand` will be triggered when the `ResourceGroupType` is changed.

## Load On Demand for recurring appointment

The scheduler will add the occurrences of recurrence series based on the visible date range, you can use the `RecurrenceHelper.GetRecurrenceDateTimeCollection` to compare and load the recurrence appointment on demand in the `ItemsSource`.

The recurrence appointment should be added to the Scheduler `ItemsSource` until the date of recurrence ends.

If `RecurrenceRule` added with count or end date, you can use the `RecurrenceHelper.GetRecurrenceDateTimeCollection` method to get the recurrence date collection and compare recursive dates in the current visible date range. Then add the recurrence appointment in the scheduler `ItemsSource`.  If the recursive dates are in the current visible date range.

If the `RecurrenceRule` is added without an end date, then the recurrence appointment should be added in the scheduler `ItemsSource` when all the visible dates changed from the recurrence start date.