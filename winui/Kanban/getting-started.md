---
layout: post
title: Getting Started with WinUI Kanban control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Kanban (SfKanban) control, its elements, and more.
platform: winui
control: SfKanban
documentation: ug
---

# Getting Started with WinUI Kanban Control

This section provides a quick overview of how to get started with the WinUI Kanban control (SfKanban) for WinUI and a walk-through to configure the WinUI Kanban control in a real-time scenario. Follow the steps below to add WinUI Kanban control to your project.

## Creating an application with WinUI Kanban

1. Create a [WinUI 3 desktop app for C# and .NET 6](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).

2. Add reference to the `Syncfusion.Kanban.WinUI` NuGet.

3. Import the control namespace `Syncfusion.UI.Xaml.Kanban` in XAML or C# code.

4. Initialize the WinUI Kanban control.

{% capture codesnippet1 %}
{% tabs %}

{% highlight XAML hl_lines="3 5" %}

<Window
    ...
    xmlns:kanban="using:Syncfusion.UI.Xaml.Kanban">

    <kanban:SfKanban x:Name="kanban"/>
</Window>

{% endhighlight %}

{% highlight C# hl_lines="1 9 10" %}

using Syncfusion.UI.Xaml.Kanban;
. . .

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfKanban kanban = new SfKanban();
        this.Content = kanban;
    }
}

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

## Populate WinUI Kanban item source

Here are the steps to render kanban card items using the WinUI Kanban control with the respective `KanbanModel` class.

* Create view model.
* Bind the item source for Kanban.

### Create view model

Create a view model class to set values for the properties listed in the `KanbanModel` class as shown in the following example code. Each `KanbanModel` instance represents a card in the Kanban control.

{% highlight c# tabtitle="ViewModel.cs" %}
   
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

        taskDetail = new KanbanModel();
        taskDetail.Title = "WF Issue";
        taskDetail.Id = "1254";
        taskDetail.Description = "HorizontalAlignment for tooltip is not working";
        taskDetail.Category = "Review";
        taskDetail.IndicatorColorKey = "High";
        taskDetail.Tags = new List<string>() { "Bug fixing" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle5.png"))
        };

        taskDetails.Add(taskDetail);
        return taskDetails;
    }

    #endregion
}

{% endhighlight %}

### Bind item source for Kanban

To populate the kanban card items, utilize the `ItemsSource` property of `SfKanban`.

{% tabs %}

{% highlight XAML hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;

{% endhighlight %}

{% endtabs %}

### Defining columns

The columns are generated automatically based on the different values of the `Category` in the `KanbanModel` class from the `ItemsSource`. However, you can manually define the columns by setting the `AutoGenerateColumns` property to `false` and adding `KanbanColumn` instances to the `Columns` property of `SfKanban`. You can define the column categories using the `Categories` property of `KanbanColumn`, and the cards will be added to their respective columns.

{% tabs %}
{% highlight XAML hl_lines="2 4 5 6 7" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
        <kanban:KanbanColumn HeaderText="To Do" Categories="Open" />
        <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress" />
        <kanban:KanbanColumn HeaderText="Code Review" Categories="Code Review" />
        <kanban:KanbanColumn HeaderText="Done" Categories="Done" />
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="1 4 5 6 7" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Code Review", Categories = "Code Review" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done" });

{% endhighlight %}
{% endtabs %}

N> When manually defining columns, ensure the `AutoGenerateColumns` property of `SfKanban` is set to `false`.

## Theme

The WinUI Kanban supports light and dark themes, automatically adjusting to the system's theme settings for a consistent and visually appealing experience in any environment.

Refer to the following link for guidance on applying themes: [Themes for Syncfusion WinUI controls](https://help.syncfusion.com/winui/common/themes)

N> You can refer to our `WinUI Kanban` feature tour page for its groundbreaking feature representations. You can also explore our `WinUI Kanban Examples` that shows you how to render the Kanban in WinUI.