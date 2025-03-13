---
layout: post
title: Kanban Workflow Setup | SfKanban | WinUI | Syncfusion<sup>®</sup>Syncfusion<sup>®</sup>
description: This section provides details about configuring workflows in Syncfusion<sup>®</sup> Essential Studio<sup>®</sup> WinUI Kanban (SfKanban) control, its components, and functionality.
platform: WinUI
control: SfKanban
documentation: ug
---

# Workflow configuration

A Kanban [`Workflow`]() defines the movement of tasks through different stages in a process, ensuring efficient tracking and management.

* [`Category`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#:~:text=System.String-,Category,-Gets%20or%20sets) – Represents a specific stage in the workflow that an item is currently in.

* [`AllowedTransitions`]() – Specifies the list of categories where an item can be moved from its current category.

Workflows help in visualizing the progress of tasks, identifying bottlenecks, and ensuring smooth task transitions. By defining workflows, teams can establish clear task movement rules, improving collaboration and efficiency.
- **Improved Task Management**: Clearly defined categories and transitions help in tracking task status.
- **Better Collaboration**: Team members can understand the process and move tasks accordingly.
- **Enhanced Productivity**: Streamlined workflows reduce delays and improve overall efficiency.
- **Transparency**: A well-structured workflow allows stakeholders to track task progression easily.

{% tabs %}
{% highlight xaml %}

    <kanban:SfKanban x:Name="kanban"
                     AutoGenerateColumns="False"
                     ItemsSource="{Binding TaskDetails}">

             <kanban:SfKanban.DataContext>
                 <local:ViewModel />
             </kanban:SfKanban.DataContext>

            <kanban:SfKanban.IndicatorColorPalette>
                <kanban:KanbanColorMapping Key = "Low" Color="#0F7B0F"/>
                <kanban:KanbanColorMapping Key = "Normal" Color="#FFB900"/>
                <kanban:KanbanColorMapping Key = "High" Color="#C42B1C"/>
                </kanban:SfKanban.IndicatorColorPalette>
            <kanban:KanbanColumn HeaderText = "To Do" Categories="Open,Postponed" />
            <kanban:KanbanColumn HeaderText = "In Progress"
                            Categories="In Progress"
                            MinimumCount="2">
                    <kanban:KanbanColumn.ErrorBarSettings>
                        <kanban:KanbanErrorBarSettings MaximumValidationColor = "Red" MinimumValidationColor="Yellow" />
                    </kanban:KanbanColumn.ErrorBarSettings>
            </kanban:KanbanColumn>
            <kanban:KanbanColumn HeaderText = "For Review"
                                 Categories="Review"
                                 MaximumCount="5">
                <kanban:KanbanColumn.ErrorBarSettings>
                    <kanban:KanbanErrorBarSettings MaximumValidationColor = "Red" MinimumValidationColor="Yellow" />
                </kanban:KanbanColumn.ErrorBarSettings>
            </kanban:KanbanColumn>
            <kanban:KanbanColumn HeaderText = "Done"
                                 Categories="Closed,Closed No Changes,Won't Fix"
                                 MinimumCount="2"
                                 MaximumCount="10">
                <kanban:KanbanColumn.ErrorBarSettings>
                    <kanban:KanbanErrorBarSettings MaximumValidationColor = "Red" MinimumValidationColor="Yellow" />
                </kanban:KanbanColumn.ErrorBarSettings>
            </kanban:KanbanColumn>
    </kanban:SfKanban>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}

 this.kanban.ItemsSource = new ViewModel().TaskDetails;

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

            KanbanModel taskDetail = new KanbanModel();
            taskDetail.Title = "UWP Issue";
            taskDetail.Id = "6593";
            taskDetail.Description = "Sorting is not working properly in DateTimeAxis";
            taskDetail.Category = "Postponed";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle1.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "New Feature";
            taskDetail.Id = "6593";
            taskDetail.Description = "Need to create code base for Gantt control";
            taskDetail.Category = "Postponed";
            taskDetail.IndicatorColorKey = "Low";
            taskDetail.Tags = new List<string>() { "GanttControl UWP" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle2.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "UG";
            taskDetail.Id = "6516";
            taskDetail.Description = "Need to do post-processing work for closed incidents";
            taskDetail.Category = "Postponed";
            taskDetail.IndicatorColorKey = "Normal";
            taskDetail.Tags = new List<string>() { "Post-processing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle3.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "UWP Issue";
            taskDetail.Id = "651";
            taskDetail.Description = "Crosshair label template not visible in UWP";
            taskDetail.Category = "Open";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle4.png"))
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
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle5.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "WPF Issue";
            taskDetail.Id = "23822";
            taskDetail.Description = "Need to implement tooltip support for histogram series";
            taskDetail.Category = "Open";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle6.png"))
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
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle7.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "WF Issue";
            taskDetail.Id = "1254";
            taskDetail.Description = "HorizontalAlignment for tooltip is not working";
            taskDetail.Category = "In Progress";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "Bug fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle8.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "WPF Issue";
            taskDetail.Id = "28066";
            taskDetail.Description = "In minimized state, first and last segments have incorrect spacing";
            taskDetail.Category = "Review";
            taskDetail.IndicatorColorKey = "Normal";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle9.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "WinUI Issue";
            taskDetail.Id = "29477";
            taskDetail.Description = "Null reference exception thrown in line chart";
            taskDetail.Category = "Review";
            taskDetail.IndicatorColorKey = "Normal";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle10.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "WPF Issue";
            taskDetail.Id = "29574";
            taskDetail.Description = "Minimum and maximum properties are not working in dynamic update";
            taskDetail.Category = "Review";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "Bug Fixing" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle11.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "Kanban Feature";
            taskDetail.Id = "29574";
            taskDetail.Description = "Need to implement tooltip support for Kanban";
            taskDetail.Category = "Review";
            taskDetail.IndicatorColorKey = "High";
            taskDetail.Tags = new List<string>() { "New Control" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle12.png"))
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
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle13.png"))
            };

            taskDetails.Add(taskDetail);

            taskDetail = new KanbanModel();
            taskDetail.Title = "New Feature";
            taskDetail.Id = "29574";
            taskDetail.Description = "Swimlane support for Kanban";
            taskDetail.Category = "Open";
            taskDetail.IndicatorColorKey = "Low";
            taskDetail.Tags = new List<string>() { "New Control" };
            taskDetail.Image = new Image
            {
                Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle14.png"))
            };

            taskDetails.Add(taskDetail);
            return taskDetails;
        }
        #endregion
    }

{% endhighlight %}
{% endtabs %}

By utilizing workflows, teams can effectively manage tasks and streamline the development process. As the project evolves, workflows can be adjusted to accommodate new requirements, making them a flexible and essential tool for project management.
