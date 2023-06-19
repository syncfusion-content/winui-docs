---
layout: post
title: Getting Started with WinUI Scheduler control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Scheduler(SfScheduler) control, its elements, and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Getting Started with WinUI Scheduler (SfScheduler)

This section provides an overview of working with [WinUI Scheduler](https://www.syncfusion.com/winui-controls/Scheduler) and also provides a walk-through to configure the WinUI Scheduler control in a real-time scenario.

## Creating an application with WinUI Scheduler

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).

2. Add reference to the [Syncfusion.Scheduler.WinUI](https://www.nuget.org/packages/Syncfusion.Scheduler.WinUI) NuGet. 

3. Import the control namespace `Syncfusion.UI.Xaml.Scheduler` in XAML or C# code.

4. Initialize the WinUI Scheduler control.

{% capture codesnippet1 %}
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="8 12" %}
<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:scheduler="using:Syncfusion.UI.Xaml.Scheduler"
    mc:Ignorable="d">

    <Grid>
        <scheduler:SfScheduler x:Name="Schedule" ViewType="Month" />
    </Grid>
</Window>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1 13 14" %}
using Syncfusion.UI.Xaml.Scheduler;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            this.InitializeComponent();
            SfScheduler scheduler = new SfScheduler();
            this.Content = scheduler;
        }
    }
}
{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Change different Scheduler Views

The [WinUI Scheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.html) control provides eight different types of views to display dates and it can be assigned to the control by using the [ViewType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ViewType) property. By default, the control is assigned with the `Month` view. The current date will be displayed initially for all the Schedule views.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}
 <scheduler:SfScheduler x:Name="Schedule" 
                        ViewType="Month">
 </scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
this.Schedule.ViewType = SchedulerViewType.Month;
{% endhighlight %}
{% endtabs %}

![Show month view in WinUI Scheduler](gettingstarted_images/winui-scheduler-show-month-view.png)

## Appointments

The [WinUI Scheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.html) has a built-in capability to handle the appointment arrangement internally based on the [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html) collections. Allocate the collection generated to the Appointments property.

### Creating the schedule appointments

The [ScheduleAppointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html) is a class that includes the specific scheduled appointment. It has some basic properties such as [StartTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_StartTime), [EndTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_EndTime), [Subject](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Subject), and some additional information about the appointment can be added with [Notes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Notes), [Location](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_Location), and [IsAllDay](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_IsAllDay) properties.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="14" %}
// Creating an instance for the schedule appointment collection.
var scheduleAppointmentCollection = new ScheduleAppointmentCollection();

//Adding schedule appointment in the schedule appointment collection. 
scheduleAppointmentCollection.Add(new ScheduleAppointment()
{
    StartTime = new DateTime(2021, 03, 16, 10, 0, 0),
    EndTime = new DateTime(2021, 03, 16, 12, 0, 0),
    Subject = "Client Meeting",
    Location = "Hutchison road",
});

//Adding the schedule appointment collection to the ItemSource of WinUI Scheduler.
this.Schedule.ItemsSource = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs %}

N> [View sample in GitHub](https://github.com/SyncfusionExamples/WinUI-Scheduler-Examples/tree/main/GettingStarted)

### Creating the custom Events/Appointments with data mapping

Map the custom appointments data to our scheduler.

N> The CustomAppointment class should contain two DateTime fields and a string field as mandatory.

Here are the steps to render meetings using the [WinUI Scheduler](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html) control with respective custom data properties created in a class `Meeting.`

* [Creating custom class to map that objects with ScheduleAppointment](#creating-custom-class-to-map-that-objects-with-ScheduleAppointment)
* [Create view model](#create-view-model)
* [Mapping the data object to ScheduleAppointment](#mapping-the-data-object-to-ScheduleAppointment)
* [Bind item source for Scheduler](#binding-item-source-for-Scheduler-control)

#### Creating custom class to map that object with appointment
Create a custom class `Meeting` with mandatory fields `From,` `To,` and `EventName`.

{% tabs %}
{% highlight c# tabtitle="Meeting.cs" %}  
    /// <summary>    
    /// Represents the custom data properties.    
    /// </summary>    
    public class Meeting 
    { 
        public string EventName { get; set; } 
        public DateTime From { get; set; } 
        public DateTime To { get; set; } 
        public bool IsAllDay { get; set; } 
        public Brush Color { get; set; } 
        public Brush ForegroundColor { get; set; } 
        public string StartTimeZone { get; set; } 
        public string EndTimeZone { get; set; } 
    }
{% endhighlight %}
{% endtabs %}

N> Inherit this class from the `INotifyPropertyChanged` for dynamic changes in custom data.

#### Create view model

By setting `From` and `To` of Meeting class, schedule meetings for a specific day. Change the `Subject` and `color` of the appointment using the `EventName` and `Color` properties. Define the list of custom appointments in a separate class of `ViewModel`.

{% tabs %}
{% highlight c# tabtitle="SchedulerViewModel.cs" %}
public class SchedulerViewModel
{
    /// <summary>
    /// current day meetings 
    /// </summary>
    private List<string> currentDayMeetings;

    /// <summary>
    /// minimum time meetings
    /// </summary>
    private List<string> minTimeMeetings;
    
    /// <summary>
    /// color collection
    /// </summary>
    private List<Brush> colorCollection;

    /// <summary>
    /// Initializes a new instance of the <see cref="ScheduleViewModel" /> class.
    /// </summary>
     
    public SchedulerViewModel()
    {
        this.Appointments = new ObservableCollection<SchedulerModel>();
        this.InitializeDataForBookings();
        this.IntializeAppoitments();
    }

    /// <summary>
    /// Gets or sets appointments.
    /// </summary>
    public ObservableCollection<SchedulerModel> Appointments
    {
        get;
        set;
    }

    /// <summary>
    /// Method for get timing range.
    /// </summary>
    /// <returns>return time collection</returns>
    private List<Point> GettingTimeRanges()
    {
        List<Point> randomTimeCollection = new List<Point>();
        randomTimeCollection.Add(new Point(9, 11));
        randomTimeCollection.Add(new Point(12, 14));
        randomTimeCollection.Add(new Point(15, 17));

        return randomTimeCollection;
    }

    /// <summary>
    /// Method for initialize data bookings.
    /// </summary>
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

        // MinimumHeight Appointment Subjects
        this.minTimeMeetings = new List<string>();
        this.minTimeMeetings.Add("Client Metting");
        this.minTimeMeetings.Add("Birthday wish alert");

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
    /// Initialize appointments.
    /// </summary>
    /// <param name="count">count value</param>
    private void IntializeAppoitments()
    {
        Random randomTime = new Random();
        List<Point> randomTimeCollection = this.GettingTimeRanges();

        DateTime date;
        DateTime dateFrom = DateTime.Now.AddDays(-100);
        DateTime dateTo = DateTime.Now.AddDays(100);
        var random = new Random();
        var dateCount = random.Next(4);
        DateTime dateRangeStart = DateTime.Now.AddDays(0);
        DateTime dateRangeEnd = DateTime.Now.AddDays(1);

        for (date = dateFrom; date < dateTo; date = date.AddDays(1))
        {
            if (date.Day % 7 != 0)
            {
                for (int additionalAppointmentIndex = 0; additionalAppointmentIndex < 1; additionalAppointmentIndex++)
                {
                    SchedulerModel meeting = new SchedulerModel();
                    int hour = randomTime.Next((int)randomTimeCollection[additionalAppointmentIndex].X, (int)randomTimeCollection[additionalAppointmentIndex].Y);
                    meeting.From = new DateTime(date.Year, date.Month, date.Day, hour, 0, 0);
                    meeting.To = meeting.From.AddHours(1);
                    meeting.EventName = this.currentDayMeetings[randomTime.Next(9)];
                    meeting.Color = this.colorCollection[randomTime.Next(9)];
                    meeting.ForegroundColor = GetAppointmentForeground(meeting.Color);
                    meeting.IsAllDay = false;
                    meeting.StartTimeZone = string.Empty;
                    meeting.EndTimeZone = string.Empty;
                    this.Appointments.Add(meeting);
                }
            }
            else
            {
                SchedulerModel meeting = new SchedulerModel();
                meeting.From = new DateTime(date.Year, date.Month, date.Day, randomTime.Next(9, 11), 0, 0);
                meeting.To = meeting.From.AddDays(2).AddHours(1);
                meeting.EventName = this.currentDayMeetings[randomTime.Next(9)];
                meeting.Color = this.colorCollection[randomTime.Next(9)];
                meeting.ForegroundColor = GetAppointmentForeground(meeting.Color);
                meeting.IsAllDay = true;
                meeting.StartTimeZone = string.Empty;
                meeting.EndTimeZone = string.Empty;
                this.Appointments.Add(meeting);
                }
            }

        // Minimum Height Meetings.
        DateTime minDate;
        DateTime minDateFrom = DateTime.Now.AddDays(-2);
        DateTime minDateTo = DateTime.Now.AddDays(2);

        for (minDate = minDateFrom; minDate < minDateTo; minDate = minDate.AddDays(1))
        {
            SchedulerModel meeting = new SchedulerModel();
            meeting.From = new DateTime(minDate.Year, minDate.Month, minDate.Day, randomTime.Next(9, 18), 30, 0);
            meeting.To = meeting.From;
            meeting.EventName = this.minTimeMeetings[randomTime.Next(0, 1)];
            meeting.Color = this.colorCollection[randomTime.Next(0, 2)];
            meeting.ForegroundColor = GetAppointmentForeground(meeting.Color);
            meeting.StartTimeZone = string.Empty;
            meeting.EndTimeZone = string.Empty;

            this.Appointments.Add(meeting);
        }
    }

    /// <summary>
    /// Method to get the foreground color based on background.
    /// </summary>
    /// <param name="backgroundColor"></param>
    /// <returns></returns>
    private Brush GetAppointmentForeground(Brush backgroundColor)
    {
        if ((backgroundColor as SolidColorBrush).Color.ToString().Equals("#FF8551F2") || (backgroundColor as SolidColorBrush).ToString().Equals("#FF5363FA") || (backgroundColor as SolidColorBrush).ToString().Equals("#FF2D99FF"))
            return new SolidColorBrush(Microsoft.UI.Colors.White);
        else
            return new SolidColorBrush(Color.FromArgb(255, 51, 51, 51));
    }
}
{% endhighlight %}
{% endtabs %}

#### Mapping the data object to ScheduleAppointment
Map those properties of the `Meeting` class with our `WinUI Scheduler` control by using the [AppointmentMapping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentMapping.html) property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2 3 4 5 6 7 8 9 10 11 12" %}
<scheduler:SfScheduler x:Name="Schedule">
    <scheduler:SfScheduler.AppointmentMapping>
        <scheduler:AppointmentMapping
            Subject="EventName"
            StartTime="From"
            EndTime="To"
            AppointmentBackground="Color"
            Foreground="ForegroundColor"    
            IsAllDay="IsAllDay"
            StartTimeZone="StartTimeZone"
            EndTimeZone="EndTimeZone"/>
    </scheduler:SfScheduler.AppointmentMapping>
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1 3 12" %} 
using Syncfusion.UI.Xaml.Scheduler;

AppointmentMapping appointmentMapping = new AppointmentMapping();
appointmentMapping.Subject = "EventName";
appointmentMapping.StartTime = "From";
appointmentMapping.EndTime = "To";
appointmentMapping.AppointmentBackground = "Color";
appointmentMapping.Foreground = "ForegroundColor";
appointmentMapping.IsAllDay = "IsAllDay";
appointmentMapping.StartTimeZone = "StartTimeZone";
appointmentMapping.EndTimeZone = "EndTimeZone";
Schedule.AppointmentMapping = appointmentMapping;
{% endhighlight %}
{% endtabs %}

#### Bind item source for Scheduler
Create meetings of type `ObservableCollection<Appointments>` and assign those appointments collection `Appointments` to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) property of `SfScheduler`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 6" %}

<Grid>
    <Grid.DataContext>
        <local:SchedulerViewModel/>
    </Grid.DataContext>
    <scheduler:SfScheduler x:Name="Schedule" 
                           ItemsSource="{Binding Appointments}" 
                           ViewType="Month"/>
</Grid>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}
SchedulerViewModel schedulerViewModel = new SchedulerViewModel();
this.Schedule.ItemsSource = schedulerViewModel.Appointments;
{% endhighlight %}
{% endtabs %}

N> [View sample in GitHub]()

## Change first day of week

The WinUI Scheduler control will be rendered with `Sunday` as the first day of the week but customize it to any day by using the [FirstDayOfWeek](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_FirstDayOfWeek) property of `SfScheduler`.

{% tabs %}  
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}
<scheduler:SfScheduler x:Name="Schedule"  
                       FirstDayOfWeek="Monday">
</scheduler:SfScheduler>    
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}
//setting first day of the week.    
Schedule.FirstDayOfWeek = DayOfWeek.Monday;   
{% endhighlight %}  
{% endtabs %}  

![Change first day of week in WinUI Scheduler](gettingstarted_images/winui-scheduler-change-first-day-of-week.png)