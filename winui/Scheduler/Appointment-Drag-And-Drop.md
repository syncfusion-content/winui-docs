---
layout: post
title: Appointment Drag and Drop in WinUI Scheduler control | Syncfusion
description: Learn here all about appointment drag and drop support in Syncfusion WinUI Scheduler (SfScheduler) control, and more.
platform: winui
control: SfScheduler
documentation: ug
---

# Appointment Drag and Drop in WinUI Scheduler (SfScheduler)

The Scheduler supports rescheduling appointments by performing drag and drop operations.

N> The Syncfusion WinUI controls have been upgraded to Windows App SDK 1.1 [release note](https://help.syncfusion.com/winui/release-notes/v20.2.0.36), and there is a framework break with drag and drop functionality and the following framework issue in this report [link](https://github.com/microsoft/microsoft-ui-xaml/issues/7231), so appointment drag and drop will not work until the framework resolves this issue.

## Disable drag and drop

The Scheduler supports disabling appointment drag and drop by setting the [AppointmentEditFlag](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentEditFlag.html) property except [DragDrop](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentEditFlag.html#Syncfusion_UI_Xaml_Scheduler_AppointmentEditFlag_DragDrop). In this case, appointment drag and drop cannot be performed.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="2" %}
<scheduler:SfScheduler x:Name="Schedule" 
                       AppointmentEditFlag="Add,Edit,Resize">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
this.Schedule.AppointmentEditFlag = AppointmentEditFlag.Add | AppointmentEditFlag.Edit | AppointmentEditFlag.Resize;
{% endhighlight %}
{% endtabs %}

## Show/Hide the time indicator on appointment dragging

Show or hide the time indicator at a specific time to drag the appointment, by using the [ShowTimeIndicator](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DragDropSettings.html#Syncfusion_UI_Xaml_Scheduler_DragDropSettings_ShowTimeIndicator) property of [DragDropSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DragDropSettings.html) and setting it to `true`. 

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}
this.Schedule.ViewType = SchedulerViewType.Week;
this.Schedule.DragDropSettings.ShowTimeIndicator = true;
{% endhighlight %}
{% endtabs %}

![show-appointment-dragging-time-indicator-in-winui-scheduler](Appointment-Drag-And-Drop_Images/appointment-dragging-time-indicator-in-winui-scheduler.png)

N>
* Not applicable for the `Month` and `Timeline Month` views. 
* If the [TimeRulerSize](https://help.syncfusion.com/winui/scheduler/day-week-views#change-time-ruler-size) property value is set to zero to collapse the time ruler labels, the time indicator will not be shown while dragging.

## Appointment dragging time indicator text formatting

Customize the format of the appointment dragging time indicator by setting the [TimeIndicatorFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DragDropSettings.html#Syncfusion_UI_Xaml_Scheduler_DragDropSettings_TimeIndicatorFormat) property of [DragDropSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.DragDropSettings.html) in the Scheduler.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="2" %}
this.Schedule.ViewType = SchedulerViewType.Week;
this.Schedule.DragDropSettings.TimeIndicatorFormat = "HH mm tt";
{% endhighlight %}
{% endtabs %}

![customize-appointment-dragging-time-indicator-format-in-winui-scheduler](Appointment-Drag-And-Drop_Images/customize-appointment-dragging-time-indicator-format-in-winui-scheduler.png)

## AppointmentDragOver event

The Scheduler notifies with [AppointmentDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentDragOver) when the appointment is being dragged. The [AppointmentDragOverEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html) has the following members that provide the information for the [AppointmentDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentDragOver) event.

[Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragOverEventArgs_Appointment): Gets the appointment that is being dragged.

[DraggingPoint](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragOverEventArgs_DraggingPoint): Gets the dragging point of the schedule appointment UI.

[DraggingTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragOverEventArgs_DraggingTime): Gets the dragging time of the dragged appointment object.

[SourceResource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragOverEventArgs_SourceResource): Gets the SchedulerResource where the appointment was located before the drag started.

[TargetResource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragOverEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragOverEventArgs_TargetResource): Gets the SchedulerResource where the appointment is currently being dragged over.


{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.AppointmentDragOver += Schedule_AppointmentDragOver;

private void Schedule_AppointmentDragOver(object sender, AppointmentDragOverEventArgs e)
{
    //To notify when dragging the appointment.
}
{% endhighlight %}
{% endtabs %}

## AppointmentDragStarting event

The Scheduler is notified by the [AppointmentDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentDragStarting) event when starting to drag the appointment. The [AppointmentDragStartingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragStartingEventArgs.html) has the following members that provide the information for the [AppointmentDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentDragStarting) event.

[Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragStartingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragStartingEventArgs_Appointment): Gets the selected appointment.

`Cancel`: Cancels the appointment dragging by setting this property to `true`.

[Resource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDragStartingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDragStartingEventArgs_Resource): Gets the resource of an appointment under which the appointment is located.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.AppointmentDragStarting += Schedule_AppointmentDragStarting;

private void Schedule_AppointmentDragStarting(object sender, AppointmentDragStartingEventArgs e)
{
    //To notify when start to drag the appointment.
}
{% endhighlight %}
{% endtabs %}

## AppointmentDropping event

The Scheduler is notified by `AppointmentDropping` when the appointment is dropped. The [AppointmentDroppingEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDroppingEventArgs.html) has the following members that provide information for the [AppointmentDropping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_AppointmentDropping) event.

[Appointment](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDroppingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDroppingEventArgs_Appointment): Gets the selected appointment that is being dragged and dropped.

`Cancel`: Cancels the appointment dropping by setting this property to `true`.

[DropTime](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDroppingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDroppingEventArgs_DropTime): Gets the drop time of the dragged appointment.

[SourceResource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDroppingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDroppingEventArgs_SourceResource): Gets the SchedulerResource where the appointment was located before the drag started.

[TargetResource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Scheduler.AppointmentDroppingEventArgs.html#Syncfusion_UI_Xaml_Scheduler_AppointmentDroppingEventArgs_TargetResource): Gets the SchedulerResource where the appointment is currently being dragged over.

{% tabs %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}
this.Schedule.AppointmentDropping += Schedule_AppointmentDropping;

private void Schedule_AppointmentDropping(object sender, AppointmentDroppingEventArgs e)
{
    //To notify when the appointment is dropping.
}
{% endhighlight %}
{% endtabs %}
