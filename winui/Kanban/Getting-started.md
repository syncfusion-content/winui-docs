---
layout: post
title: Getting Started with WinUI Kanban control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Kanban (SfKanban) control, its elements, and more.
platform: winui
control: SfKanban
documentation: ug
---
# Getting Started with WinUI Kanban (SfKanban)

This section provides an overview of working with WinUI Kanban and a step-by-step guide to configuring and using it effectively in your application.

## Creating an application with WinUI Kanban

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/create-your-first-winui3-app).

2. Add reference to the `Syncfusion.Kanban.WinUI` NuGet.

3. Import the control namespace `Syncfusion.UI.Xaml.Kanban` in XAML or C# code.

4. Initialize the WinUI Kanban control.

{% capture codesnippet1 %}
{% tabs %}

{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="7 12" %}
<Window x:Class="GettingStarted.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:GettingStarted"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:kanban="using:Syncfusion.UI.Xaml.Kanban"
        mc:Ignorable="d"
        Title="GettingStarted">

        <Grid>
            <kanban:SfKanban x:Name="sfKanban"/>
        </Grid>
</Window>

{% endhighlight %}

{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1 13 14" %}
using Syncfusion.UI.Xaml.Kanban;

namespace GettingStarted
{
    /// <summary>
    /// An empty window that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainWindow : Window
    {
        public MainWindow()
        {
            this.InitializeComponent();
            SfKanban sfKanban = new SfKanban();
            this.Content = sfKanban;
        }
    }
}

{% endhighlight %}
{% endtabs %}
{% endcapture %}
{{ codesnippet1 | OrderList_Indent_Level_1 }}

### Create a Data Model

To populate the `SfKanban` control, you need to create a collection of `KanbanModel` objects. These objects represent the tasks or items to be displayed on the Kanban board, each containing properties such as `title`, `description`, `category`, and other relevant details.

{% highlight c# %}
   
    /// <summary>
    /// Represents a ViewModel that designed to manage a collection of kanban tasks in a software project management system, typically used in kanban boards.
    /// </summary>
    public class GettingStartedViewModel
    {
        #region Properties

        /// <summary>
        /// Gets or sets the collection of <see cref="KanbanModel"/> objects representing tasks in various stages.
        /// </summary>
        public ObservableCollection<KanbanModel> TaskDetails { get; set; }

        #endregion

        #region Constructor

        /// <summary>
        /// Initializes a new instance of the <see cref="GettingStartedViewModel"/> class.
        /// </summary>
        public GettingStartedViewModel()
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

### Bind Data to the Kanban Control

To bind a data source to the `SfKanban` control, set the `ItemsSource` property as demonstrated in the example below. This property connects the collection of `KanbanModel` objects to the Kanban board, enabling the display of tasks.

{% tabs %}

{% highlight xaml %}

<Grid>
    <kanban:SfKanban x:Name="sfKanban"
                     ItemsSource="{Binding TaskDetails}"/>
    <Grid.DataContext>
        <local:GettingStartedViewModel/>
    </Grid.DataContext>
</Grid>

{% endhighlight %}

{% highlight c# %}

this.sfKanban.ItemsSource = new GettingStartedViewModel().TaskDetails;

{% endhighlight %}

{% endtabs %}

### Define columns

To configure columns in the `SfKanban` control, you must manually define them by adding `KanbanColumn` objects to the `Columns` collection property of SfKanban.

The `ItemsSource` bound to the Kanban control will populate the respective columns based on the `Categories` property in KanbanColumn.

The following code example illustrates how this can be done.

{% tabs %}
{% highlight xaml %}

<kanban:SfKanban x:Name="sfKanban"
                 ItemsSource="{Binding TaskDetails}"
                 AutoGenerateColumns="False">
    <kanban:KanbanColumn Categories="Open" HeaderText="To Do"/>
    <kanban:KanbanColumn Categories="In Progress" HeaderText="Progress"/>
    <kanban:KanbanColumn Categories="Review,Closed" HeaderText="Done"/>
</kanban:SfKanban>

{% endhighlight %}

{% highlight c# %}

this.sfKanban.ItemsSource = new GettingStartedViewModel().TaskDetails;
this.sfKanban.AutoGenerateColumns = false;

sfKanban.Columns.Add(new KanbanColumn() { Categories = "Open", HeaderText = "To Do", });
sfKanban.Columns.Add(new KanbanColumn() { Categories = "In Progress", HeaderText = "Progress", });
sfKanban.Columns.Add(new KanbanColumn() { Categories = "Review,Closed", HeaderText = "Done", });

{% endhighlight %}
{% endtabs %}

Alternatively, you can set the `AutoGenerateColumns` property to `true` to automatically create columns without manually defining them. When enabled, the columns are generated dynamically based on the `Category` property of KanbanModel, creating a column for each distinct value in the `ItemsSource`.

## Theme

The WinUI Kanban supports light and dark themes, automatically adjusting to the system's theme settings for a consistent and visually appealing experience in any environment.

Refer to the following link for guidance on applying themes: [Themes for Syncfusion WinUI controls](https://help.syncfusion.com/winui/common/themes)

You can find the kanban keys for both themes here.
