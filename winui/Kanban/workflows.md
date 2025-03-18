---
layout: post
title: Workflows in .NET WinUI Kanban Board control | Syncfusion<sup>®</sup>
description: Learn here all about Workflows support in Syncfusion<sup>®</sup> .NET WinUI Kanban Board (SfKanban) control and more.
platform: WinUI
control: SfKanban
documentation: ug
---

# Workflows in WinUI Kanban (SfKanban) control

The `WinUI Kanban` workflow allows to set the flow of cards between the columns. It provides restriction on columns when the card is moved from one column to another column. It provides support to prevent the drag and drop action on the column.

To define the flow of card transitions between different states, create an instance of the `KanbanWorkflow` class and add it to the `Workflows` property of the `SfKanban` to define the workflow for each column. The `KanbanWorkflow` class contains the following properties to specify the source and target categories.

* `Category` – Used to define the source category/state..
* `AllowedTransitions` – Used to define the list of categories/states to which a card can be moved from the current category.
 
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38" %}
     
<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
    <kanban:SfKanban.Workflows>
        <kanban:KanbanWorkflow Category="Open">
            <kanban:KanbanWorkflow.AllowedTransitions>
                <x:String>In Progress</x:String>
                <x:String>Closed</x:String>
                <x:String>Closed No Changes</x:String>
                <x:String>Won't Fix</x:String>
            </kanban:KanbanWorkflow.AllowedTransitions>
        </kanban:KanbanWorkflow>
        <kanban:KanbanWorkflow Category="Postponed">
            <kanban:KanbanWorkflow.AllowedTransitions>
                <x:String>Open</x:String>
                <x:String>In Progress</x:String>
                <x:String>Closed</x:String>
                <x:String>Closed No Changes</x:String>
                <x:String>Won't Fix</x:String>
            </kanban:KanbanWorkflow.AllowedTransitions>
        </kanban:KanbanWorkflow>
        <kanban:KanbanWorkflow Category="Review">
            <kanban:KanbanWorkflow.AllowedTransitions>
                <x:String>In Progress</x:String>
                <x:String>Closed</x:String>
                <x:String>Postponed</x:String>
            </kanban:KanbanWorkflow.AllowedTransitions>
        </kanban:KanbanWorkflow>
        <kanban:KanbanWorkflow Category="In Progress">
            <kanban:KanbanWorkflow.AllowedTransitions>
                <x:String>Review</x:String>
                <x:String>Postponed</x:String>
            </kanban:KanbanWorkflow.AllowedTransitions>
        </kanban:KanbanWorkflow>
    </kanban:SfKanban.Workflows>
    <kanban:SfKanban.IndicatorColorPalette>
        <kanban:KanbanColorMapping Key="Low" Color="#0F7B0F"/>
        <kanban:KanbanColorMapping Key="Normal" Color="#FFB900"/>
        <kanban:KanbanColorMapping Key="High" Color="#C42B1C"/>
    </kanban:SfKanban.IndicatorColorPalette>
    <kanban:KanbanColumn HeaderText="To Do" Categories="Open,Postponed" />
    <kanban:KanbanColumn HeaderText="In Progress"
                         Categories="In Progress"/>
    <kanban:KanbanColumn HeaderText="For Review"
                         Categories="Review"/>
    <kanban:KanbanColumn HeaderText="Done"
                         Categories="Closed,Closed No Changes,Won't Fix"/>
 </kanban:SfKanban>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1 2 3 4 5 6 7" %}
           
this.kanban.Workflows = new List<KanbanWorkflow>()
{
    new KanbanWorkflow() { Category = "Open", AllowedTransitions ={ "In Progress", "Closed", "Closed No Changes", "Won't Fix"} },
    new KanbanWorkflow() { Category = "Postponed", AllowedTransitions ={ "Open", "In Progress", "Closed", "Closed No Changes", "Won't Fix"} },
    new KanbanWorkflow() { Category = "Review", AllowedTransitions ={ "In Progress", "Closed", "Postponed" } },
    new KanbanWorkflow() { Category = "In Progress", AllowedTransitions ={ "Review", "Postponed"} },
};

{% endhighlight %}
{% highlight C# tabtitle="ViewModel.cs" %} 

public class ViewModel
{
    #region Properties

    /// <summary>
    /// Gets or sets the collection of <see cref="KanbanModel"/> objects representing tasks in various stages.
    /// </summary>
    public ObservableCollection<KanbanModel> TaskDetails { get; set; }

    #endregion

    #region Constructor

    /// <summary>
    /// Initializes a new instance of the <see cref="ViewModel"/> class.
    /// </summary>
    public ViewModel()
    {
        this.TaskDetails = this.GetTaskDetails();
    }

    #endregion

    #region Private methods

    /// <summary>
    /// Method to get the kanban model collections.
    /// </summary>
    /// <returns>The kanban model collections.</returns>
    private ObservableCollection<KanbanModel> GetTaskDetails()
    {
        var taskDetails = new ObservableCollection<KanbanModel>();
        string path = @"ms-appx:///";

        KanbanModel taskDetail = new KanbanModel();
        taskDetail.Title = "UWP Issue";
        taskDetail.Id = "651";
        taskDetail.Description = "Crosshair label template not visible in UWP";
        taskDetail.Category = "Open";
        taskDetail.IndicatorColorKey = "High";
        taskDetail.Tags = new List<string>() { "Bug Fixing" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri("ms-appx:///Assets/Kanban/People_Circle1.png"))
        };

        taskDetails.Add(taskDetail);

        taskDetail = new KanbanModel();
        taskDetail.Title = "WinUI Issue";
        taskDetail.Id = "646";
        taskDetail.Description = "AxisLabel cropped when rotating the axis label";
        taskDetail.Category = "Open";
        taskDetail.IndicatorColorKey = "Low";
        taskDetail.Tags = new List<string>() { "Bug Fixing" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle2.png"))
        };

        taskDetails.Add(taskDetail);

        taskDetail = new KanbanModel();
        taskDetail.Title = "Kanban Feature";
        taskDetail.Id = "25678";
        taskDetail.Description = "Provide drag and drop support";
        taskDetail.Category = "In Progress";
        taskDetail.IndicatorColorKey = "Low";
        taskDetail.Tags = new List<string>() { "New control" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle3.png"))
        };

        taskDetails.Add(taskDetail);

        taskDetail = new KanbanModel();
        taskDetail.Title = "New Feature";
        taskDetail.Id = "29574";
        taskDetail.Description = "Dragging events support for Kanban";
        taskDetail.Category = "Closed";
        taskDetail.IndicatorColorKey = "Normal";
        taskDetail.Tags = new List<string>() { "New Control" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle4.png"))
        };

        taskDetails.Add(taskDetail);
        return taskDetails;
    }

    #endregion
}     

{% endhighlight %}
{% endtabs %}

By following the code snippet, you will notice that a card picked from the `Open` state cannot be dropped into the `Review` state. This is because we have defined that the card can only transition from the `Open` state to the `In Progress`, `Closed`, `Closed No Changes`, and `Won't Fix` states, and not to any other states.