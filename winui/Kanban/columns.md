---
layout: post
title: Columns in WinUI Kanban control | Syncfusion<sup>®</sup>
description: Learn here all about configuring and customizing columns in Syncfusion<sup>®</sup> WinUI Kanban (SfKanban) control.
platform: winui
control: SfKanban
documentation: ug
---

# Columns in WinUI Kanban (SfKanban) control

The WinUI Kanban control organizes its layout into columns, each representing a distinct stage of a workflow, such as to-do, in-progress, testing, validation, and completed. It supports various operations, including drag-and-drop, swim lane, and column toggling, all based on the defined columns.

## Change column width

By default, the columns are sized smartly to arrange the default UI of the cards with better readability. You can also define the minimum and maximum widths for the columns in [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html) using the [MinimumColumnWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_MinimumColumnWidth) and [MaximumColumnWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_MaximumColumnWidth) properties, respectively.

{% tabs %}
{% highlight XAML hl_lines="3 4" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 MinimumColumnWidth="200"
                 MaximumColumnWidth="250">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2 3" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.MinimumColumnWidth = 200;
this.kanban.MaximumColumnWidth = 250;

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

![minimum-maximum-column-width-in-winui-kanban](images/columns/minimum-maximum-column-width-in-winui-kanban.png)

You can also define the exact width for the columns using [ColumnWidth](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_ColumnWidth) property of [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html).

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 ColumnWidth="280">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.ColumnWidth = 280;

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

![column-width-in-winui-kanban](images/columns/column-width-in-winui-kanban.png)

## Categorizing columns

Columns are automatically generated based on the [Category](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Category) values in the [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html) from [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_ItemsSource). To manually define columns, set [AutoGenerateColumns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_AutoGenerateColumns) to `false`, add [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html) instances to the [Columns](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_Columns) property, and use the [Categories](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_Categories) property to assign categories to the columns. Cards will then be added accordingly.

The following example code generates the columns automatically based on the [Category](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Category) values.

{% tabs %}

{% highlight XAML hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="True"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="1" %}

this.kanban.AutoGenerateColumns = true;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

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

![categorizing-columns-in-winui-kanban](images/columns/categorizing-columns-in-winui-kanban.png)

### ColumnMappingPath

When the [`ItemsSource`] is a collection of KanbanModel, cards are automatically categorized and placed into the corresponding columns based on the value of the [`KanbanModel.Category`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#:~:text=System.String-,Category,-Gets%20or%20sets) property.

However, if the [`ItemsSource`] contains custom objects instead of KanbanModel, you must explicitly specify which property should be used for categorization by setting the [`ColumnMappingPath`] property. This ensures that cards are correctly assigned to their respective columns.

The properties of Kanban Model is used for the Keys of ColumnMappingPath. They are 

    * `Title` 
    * `Id`
    * `Description` 
    * `specifications`
    * `Category`
    * `IndicatorColorKey` 
    * `Tags` 


{% tabs %}

{% highlight xaml hl_lines="4" %}

<kanban:SfKanban x:Name="kanban" 
                ItemsSource="{Binding TaskDetails}"
                AutoGenerateColumns="True"
                ColumnMappingPath="IndicatorColorKey">

        <kanban:SfKanban.IndicatorColorPalette>
            <kanban:KanbanColorMapping Key="Low" Color="#0F7B0F"/>
            <kanban:KanbanColorMapping Key="Normal" Color="#FFB900"/>
            <kanban:KanbanColorMapping Key="High" Color="#C42B1C"/>
        </kanban:SfKanban.IndicatorColorPalette>

        <kanban:SfKanban.DataContext>
            <local:ViewModel />
        </kanban:SfKanban.DataContext>

</kanban:SfKanban>

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

### Populating Multi-Category Columns with Cards

The Kanban board allows user to render a single column by mapping multiple categories using [Categories](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_Categories) property of [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html) in [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html). For example, you can map the `In Progress` and `Validated` types under the `In progress` column.

{% tabs %}
{% highlight XAML hl_lines="5" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
    <kanban:KanbanColumn HeaderText="To Do" Categories="Open" />
    <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress,Validated" />
    <kanban:KanbanColumn HeaderText="Done" Categories="Done" />
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="5" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress,Validated" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done" });

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
        taskDetail.Category = "Validated";
        taskDetail.IndicatorColorKey = "Low";
        taskDetail.Tags = new List<string>() { "New control" };
        taskDetail.Image = new Image
        {
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle3.png"))
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
            Source = new BitmapImage(new Uri(path + "Assets/Kanban/People_Circle5.png"))
        };

        taskDetails.Add(taskDetail);

        taskDetail = new KanbanModel();
        taskDetail.Title = "New Feature";
        taskDetail.Id = "29574";
        taskDetail.Description = "Dragging events support for Kanban";
        taskDetail.Category = "Done";
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

![multi-category-columns-in-winui-kanban](images/columns/multi-category-columns-in-winui-kanban.png)

## Customize columns header appearance

The WinUI Kanban control allows you to customize the header text, column header template, and more.

### Customize the header text

You can use the [HeaderText](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_HeaderText) property of [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html) to customize the header text of a column in the kanban control.

{% tabs %}
{% highlight XAML hl_lines="4 5 6" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
        <kanban:KanbanColumn HeaderText="To Do" Categories="Open" />
        <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress" />
        <kanban:KanbanColumn HeaderText="Done" Categories="Done" />
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="4 5 6" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done" });

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
        taskDetail.Category = "Done";
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

### Customize column header appearance using DataTemplate

You can customize the column header appearance by using the [ColumnHeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_ColumnHeaderTemplate) property in the [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html) control. The `DataContext` for the [ColumnHeaderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_ColumnHeaderTemplate) property in [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html) is set to the [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html).

{% tabs %}
{% highlight XAML hl_lines="3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.ColumnHeaderTemplate>
        <DataTemplate>
            <Grid Height="40" Background="LightBlue" >
                <Grid.RowDefinitions>
                    <RowDefinition Height="5*"/>
                    <RowDefinition Height="5*"/>
                </Grid.RowDefinitions>
                <TextBlock Text="{Binding HeaderText}" Grid.Row="0"
                            Margin="6,2,0,0"
                            HighContrastAdjustment="None"
                            Foreground="Black"
                            FontWeight="Bold"
                            FontFamily="Lucida Handwriting"
                            FontStyle="Italic"
                            FontSize="13"></TextBlock>
                <StackPanel Orientation="Horizontal" Grid.Row="1">
                    <TextBlock Text="Items Count : "
                                HorizontalAlignment="Center" 
                                Margin="6,1,0,0"
                                HighContrastAdjustment="None"
                                Foreground="Black"
                                FontWeight="Normal"
                                FontStyle="Italic"
                                FontSize="11">                                
                    </TextBlock>
                    <TextBlock Text="{Binding CardsCount}" 
                                HorizontalAlignment="Center"
                                Margin="3,1,0,0"
                                HighContrastAdjustment="None"
                                Foreground="Black"
                                FontWeight="Normal"
                                FontStyle="Italic"
                                FontSize="11">                                
                    </TextBlock>
                </StackPanel>
            </Grid>
        </DataTemplate>
    </kanban:SfKanban.ColumnHeaderTemplate>
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;

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
        taskDetail.Category = "Done";
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

![column-header-template-in-winui-kanban](images/columns/column-header-template-in-winui-kanban.png)

## Expand/Collapse column

The Kanban allows you to programmatically expand or collapse columns using the [IsExpanded](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_IsExpanded) property of [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html) in the [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html) control. By default, columns can be expanded or collapsed by tapping the toggle button placed at the top-right corner of the kanban column header.

{% tabs %}
{% highlight XAML hl_lines="4" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
        <kanban:KanbanColumn HeaderText="To Do" Categories="Open" />
        <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress" />
        <kanban:KanbanColumn HeaderText="Done" Categories="Done" IsExpanded="False" />
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="4" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done", IsExpanded = false });

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
        taskDetail.Category = "Done";
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

![expand-collapse-column-in-winui-kanban](images/columns/expand-collapse-column-in-winui-kanban.png)

## Card drag and drop

Cards can be dragged and dropped across columns, within columns, or across swimlane rows to modify the card's status. To enable drag-and-drop functionality within the kanban, set the [AllowDrag](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_AllowDrag) property of [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html) to `true`. The default value is `true`.

![card-drag-drop-in-winui-kanban](images/columns/card-drag-drop-in-winui-kanban.gif)

To disable drag-and-drop, set [AllowDrag](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_AllowDrag) and [AllowDrop](https://learn.microsoft.com/en-us/uwp/api/windows.ui.xaml.uielement.allowdrop?view=winrt-26100#windows-ui-xaml-uielement-allowdrop) properties to `false`.

{% tabs %}
{% highlight XAML hl_lines="4" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
        <kanban:KanbanColumn HeaderText="To Do" Categories="Open" AllowDrag="False" AllowDrop="False"/>
        <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress" />
        <kanban:KanbanColumn HeaderText="Done" Categories="Done" />
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="4" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open", AllowDrag = false, AllowDrop = false });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress" });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done" });

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
        taskDetail.Category = "Done";
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

![disable-card-drag-drop-in-winui-kanban](images/columns/disable-card-drag-drop-in-winui-kanban.gif)

### Placeholder in WinUI Kanban control

The placeholders in the WinUI Kanban control visually indicate the exact position where a card is dragged and where it will be placed within a Kanban column during a drag-and-drop operation.

The appearance of drag-and-drop placeholders in the WinUI Kanban control can be customized by modifying the values of the predefined theme keys.

#### Drag placeholder theme keys

The following theme keys control the appearance of the drag placeholder:

* `SyncfusionKanbanPlaceholderBackground`
* `SyncfusionKanbanPlaceholderBorderBrush`
* `SyncfusionKanbanPlaceholderBorderThickness`

#### Drop placeholder theme keys

The following theme keys control the appearance of the drop placeholder:

* `SyncfusionKanbanPlaceholderSelectedBackground`
* `SyncfusionKanbanPlaceholderSelectedBorderBrush`
* `SyncfusionKanbanPlaceholderSelectedBorderThickness`

{% tabs %}
{% highlight XAML hl_lines="3 4 5 6 7 8" %}

<Grid>
    <Grid.Resources>
            <SolidColorBrush x:Key="SyncfusionKanbanPlaceholderBackground" Color="LightBlue" />
            <SolidColorBrush x:Key="SyncfusionKanbanPlaceholderBorderBrush" Color="DarkBlue" />
            <Thickness x:Key="SyncfusionKanbanPlaceholderBorderThickness">2</Thickness>
            <SolidColorBrush x:Key="SyncfusionKanbanPlaceholderSelectedBackground" Color="OrangeRed" />
            <SolidColorBrush x:Key="SyncfusionKanbanPlaceholderSelectedBorderBrush" Color="DarkRed" />
            <Thickness x:Key="SyncfusionKanbanPlaceholderSelectedBorderThickness">3</Thickness>
    </Grid.Resources>

    <kanban:SfKanban x:Name="kanban"
                     ItemsSource="{Binding TaskDetails}">
        <kanban:SfKanban.DataContext>
            <local:ViewModel/>
        </kanban:SfKanban.DataContext>
    </kanban:SfKanban>
</Grid>

{% endhighlight %}

{% highlight C# %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;

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

![placeholder-in-winui-kanban](images/columns/placeholder-in-winui-kanban.png)

## Work-in-Progress (WIP) limit and indications

The WinUI Kanban control allows users to set limits on the number of tasks in each column at every stage of the workflow, helping to prevent overload. The minimum and maximum number of items allowed in a column can be customized using the [MinimumCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_MinimumCount) and [MaximumCount](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html#Syncfusion_UI_Xaml_Kanban_KanbanColumn_MaximumCount) properties in [KanbanColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanColumn.html).

The Kanban control also supports built-in error bars that change color when the WIP limit is exceeded or when a task fails validation, making it easier to quickly identify bottlenecks in the process.

{% tabs %}
{% highlight XAML hl_lines="4 5 6" %}

<kanban:SfKanban x:Name="kanban"
                 AutoGenerateColumns="False" 
                 ItemsSource="{Binding TaskDetails}">
        <kanban:KanbanColumn HeaderText="To Do" Categories="Open" MaximumCount="1" />
        <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress" MinimumCount="2" />
        <kanban:KanbanColumn HeaderText="Done" Categories="Done" MinimumCount="1" MaximumCount="5" />
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="4 5 6" %}

this.kanban.AutoGenerateColumns = false;
this.kanban.ItemsSource = new ViewModel().TaskDetails;

this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "To Do", Categories = "Open", MaximumCount = 1 });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "In Progress", Categories = "In Progress", MinimumCount = 2 });
this.kanban.Columns.Add(new KanbanColumn() { HeaderText = "Done", Categories = "Done", MinimumCount = 1, MaximumCount = 5 });

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
        taskDetail.Category = "Done";
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

![work-in-progress-limit-in-winui-kanban](images/columns/work-in-progress-limit-in-winui-kanban.png)