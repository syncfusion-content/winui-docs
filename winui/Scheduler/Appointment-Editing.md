---
layout: post
title: Appointment editing | WinUI | Scheduler | Syncfusion
description: This section explains how to handle appointment editing and appointment resizing operations in WinUI scheduler.
platform: winui
control: Scheduler
documentation: ug
---

# Appointment Editing in WinUI Scheduler (SfScheduler)

This section explains how to handle appointment editing in WinUI scheduler and also explains about the appointment resizing.

## Adding appointments

The Scheduler supports to add new appointment by using `Appointment Editor` UI dialog. You can open this editor dialog by double clicking on a time cell.

## Editing appointment

The Scheduler supports to edit the appointment by using `Appointment Editor` UI dialog. You can open this dialog by double clicking on the appointment.

You can edit the appointments in appointment editor dialog. This changes will be saved back in appointment and mapped data object when using data binding.

### Edit recurring appointment

The Scheduler supports to edit the recurrence appointment. The following editor dialog will appear when you edit the recurrence appointment to select whether to edit only the particular occurrence or appointment series.

You can also handle the opening of recurrence popup editor dialog using `RecurringAppointmentEditMode` property in `AppointmentEditorOpeningEventArgs` by handling `AppointmentEditorOpening` event.

### AppointmentEditorOpening event

When you opens the appointment editor UI dialog to add or update appointment, then Scheduler notifies by `AppointmentEditorOpening` event.

The `AppointmentEditorOpeningEventArgs` has following members which provides the information for `AppointmentEditorOpening` event.

`Appointment` : Gets the selected appointment details which is being updated. It will be null when adding new appointment through appointment editor.

`DateTime` : Get the DateTime of time slot or month cell where user double clicked.

`Cancel` : To avoid the default appointment editor showing by enabling this property.

`RecurrenceEditMode` : Get or Sets the edit mode to perform the edit option to edit the occurrence or series for recurrence appointment. The default value of `RecurrenceEditMode` is `User.`

* User - Default editor content dialog will appear when editing a recurrence appointment to select the edit option from the end-user itself.
* Occurrence - Edit the particular occurrence alone in recurrence appointment. Default editor content dialog will not appear.
* Series - Edit the entire series in recurrence appointment. Default editor content dialog will not appear.

For example, To use custom appointment editor dialog instead of default appointment editor content dialog you can handle `AppointmentEditorOpening` event.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentEditorOpening += Schedule_AppointmentEditorOpening;

private void Schedule_AppointmentEditorOpening(object sender, AppointmentEditorOpeningEventArgs e)
{
    //To handle the default appointment editor content dialog by setting the e.Cancel value as true.
    e.Cancel = true;

    if (e.Appointment != null)
    {
        //Display the custom appointment editor content dialog to edit the appointment.
    }
    else
    {
        //Display the custom appointment editor content dialog to add new appointment.
    }
}
{% endhighlight %}
{% endtabs%}

* `Resource` : Gets the resource of an appointment under which the appointment is located.

## Visible/Collapse the built-in editors in appointment editor dialog

You can programmatically visible or collapse the editors by setting the `AppointmentEditorOptions` property in `SchedulerAppointmentEditorView`. By default, the value of `AppointmentEditorOptions` is set to `AppointmentEditorOptions.All` in the `SchedulerAppointmentEditorView` that displays all the appointment editors. The following code shows how to collapse the `Recurrence` editor by handling the `AppointmentEditorOpening` event.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentEditorOpening += Schedule_AppointmentEditorOpening;

private void Schedule_AppointmentEditorOpening(object sender, AppointmentEditorOpeningEventArgs e)
{
    e.AppointmentEditorOptions = AppointmentEditorOptions.All |  ~AppointmentEditorOptions.Recurrence;
}
{% endhighlight %}
{% endtabs%}

N>
* The basic editors such that `Subject`, `Location`, `Start Hour` and `End Hour` of the scheduler appointment editor will not be collapsed.

### AppointmentEditorClosing event

When you close the appointment editor content dialog after added or edited the schedule appointment, Scheduler notifies by `AppointmentEditorClosing` event.

The `AppointmentEditorClosingEventArgs` has following members which provides the information for `AppointmentEditorClosing` event.

`Handled` : Gets or sets a value that indicates whether the scheduler can update the underlying appointments collection or appointment based on the action performed in appointment editor. If the value is true, scheduler does not perform the action and you have to write the code in the handler and perform the action. The default value of Handled is `false.`

`Appointment` : Gets the details of updated or newly added appointment.

`Cancel` : To avoid the default appointment editor closing by enabling this property.

`Action` : Gets the action of appointment which is Add, Edit, Delete or Cancel.

* Add - Specifies that appointment is newly added through appointment editor.
* Edit - Specifies that appointment is edited through appointment editor.
* Delete - Specifies that appointment is deleted through appointment editor.
* Cancel - Specifies that appointment editing is canceled through appointment editor.

For example, to handle the appointment adding for today’s date, user can handle the `AppointmentEditorClosing` event.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentEditorClosing += Schedule_AppointmentEditorClosing;

private void Schedule_AppointmentEditorClosing(object sender, AppointmentEditorClosingEventArgs e)
{
    var appointment = e.Appointment as ScheduleAppointment;
    if (appointment != null)
    {
        if (appointment.StartTime.Day == DateTime.Now.Day)
            e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs%}

* Resource - gets the resource collection of edited appointment.

## Disable appointment editing

To disable appointment editing functionality, Set `AppointmentEditFlag` property to `None.` In this case, you will not be able to perform add, edit, resize and drag & drop the appointments.

{% tabs %}
{% highlight XAML %}
<scheduler:SfScheduler x:Name="Schedule"  
                       ViewType="Week"
                       AppointmentEditFlag="None">
</scheduler:SfScheduler> 
{% endhighlight %}
{% endtabs %}

## Delete appointments

The Scheduler supports two ways to remove the selected appointment.

1. Pressing <kbd>delete</kbd> key.
2. Using appointment editor dialog.

### Delete recurring appointment

The Scheduler supports to delete the recurrence appointment. The following editor dialog will appear when user deletes the recurrence appointment. You can select the delete option to make the changes for occurrence or appointment series.

### AppointmentDeleting event

The Scheduler notifies by `AppointmentDeleting` event, when user delete the appointment.

The `AppointmentDeletingEventArgs` has following members which provides information for `AppointmentDeleting` event.

`Appointment` : Gets the selected appointment to delete.

`Cancel` : To avoid appointment deleting by enabling this property.

`RecurrenceEditMode` : Gets or sets whether to delete series or occurrence when delete a recurrence appointment. The default value of `RecurrenceEditMode` is `User`

* User - Default editor dialog will appear when deleting a recurrence appointment to select the edit option from the end-user itself.
* Occurrence - Delete the particular occurrence alone in recurrence appointment. Default editor dialog will not appear.
* Series - Delete the entire series in recurrence appointment. Default editor dialog will not appear.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentDeleting += Schedule_AppointmentDeleting;

private void Schedule_AppointmentDeleting(object sender, AppointmentDeletingEventArgs e)
{
    //To notify when restrict appointment delete.
    e.Cancel = true;
}
{% endhighlight %}
{% endtabs%}

## Appointment Resizing

The Scheduler has support to resize the selected appointment. This support is available for all views except `Month` view.

N>  Applicable only for WinUI UWP.

### Disable appointment resize

The Scheduler supports to disable the appointment resizing by setting `AppointmentEditFlag` property except `Resize.` In this case, you will not be able to perform appointment resizing.

{% tabs %}
{% highlight xaml %}
<scheduler:SfScheduler x:Name="Schedule"  
                       ViewType="Week"
                       AppointmentEditFlag="Add,DragDrop,Edit">
</scheduler:SfScheduler>
{% endhighlight %}
{% highlight c# %}
this.Schedule.AppointmentEditFlag = AppointmentEditFlag.Add | AppointmentEditFlag.DragDrop | AppointmentEditFlag.Edit;
{% endhighlight %}
{% endtabs %}

### AppointmentResizing event

The Scheduler notifies by `AppointmentResizing` event when user resize an appointment.

The `AppointmentResizingEventArgs` has following members which provides information for `AppointmentResizing` event.

`Appointment`: Gets the appointment being resized.

`Action`: Gets the current action being performed while resizing an appointment.

* Starting - Denotes event occurred when user mouse over the appointment to resize an appointment (before showing resize cursor).
* Progressing - Denotes event occurred when user resizing an appointment.
* Committing - Denotes event occurred when user ends the resizing by releasing pointer to commit the changed to underlying appointment.
* Canceling - Denotes the event occurred before canceling the resize operation when user press <kbd>Esc</kbd> key when resizing operation in progress.

`StartTime`: Gets the updated start time of appointment in resizing operation.

`EndTime`: Gets the updated end time of appointment in resizing operation.

`CanContinueResize`: Gets or sets a value indicating whether resizing operation should be continued or canceled. You can set this property when Action is Starting, Progressing, Canceling.This property won’t have any effect for when Action is Committing.

`CanCommit`: Gets or sets a value indicating whether to update underlying appointment when resizing operation is completed. You can set this property when Action is Canceling and Committing. This property won’t have any effect for when Action is Starting and Progressing.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentResizing += Schedule_AppointmentResizing;

private void Schedule_AppointmentResizing(object sender, AppointmentResizingEventArgs e)
{
    //To notify when resizing the appointment. 
}
{% endhighlight %}
{% endtabs%}

* `Resource`: Gets the resource of an appointment under which the appointment is located.