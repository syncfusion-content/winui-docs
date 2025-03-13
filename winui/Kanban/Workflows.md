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
{% highlight c# tabtitle="ViewModel.cs" % }

public class ViewModel
         {
             public ViewModel()
             {
                 TaskDetails = new ObservableCollection<KanbanModel>();
                 TaskDetails.Add(new KanbanModel()
                    {
                        Title = "Universal App",
                        Id = "6593",
                        Description = "Draft preliminary software specifications",
                        Category = "Review",
                        IndicatorColorKey = "High",
                        Tags = new List<string> { "Analysis" },
                        Image = new Image { Source = new BitmapImage(new Uri("ms-appx:///Images/People_Circle0.png", UriKind.RelativeOrAbsolute)) },
                    });
             }
             public ObservableCollection<KanbanModel> TaskDetails { get; set; }
         }
         
{% endhighlight %}
{% endtabs %}

By utilizing workflows, teams can effectively manage tasks and streamline the development process. As the project evolves, workflows can be adjusted to accommodate new requirements, making them a flexible and essential tool for project management.
