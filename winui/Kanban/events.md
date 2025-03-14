---
layout: post
title: Events in WinUI Kanban control | Syncfusion<sup>®</sup>
description: Learn here all about the interaction-related events support in Syncfusion<sup>®</sup> WinUI Kanban (SfKanban) control.
platform: winui
control: SfKanban
documentation: ug
---

# Events in WinUI Kanban (SfKanban)

## DragStarting

The [CardDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDragStarting) event occurs when a card begins to be dragged. We can get the following details from the [CardDragStarting](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDragStarting) event.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragStartingEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragStartingEventArgs_Column) -  Returns the source column from which the card is being dragged.

* [Card](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragStartingEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragStartingEventArgs_Card) - Returns the dragging card in the kanban.
* [IsDraggingCardRetained]() - This allows repeated drag-and-drop actions on the same card without moving it from the source column.

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 CardDragStarting="OnKanbanCardDragStarting">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}
{% highlight C# hl_lines="2 7 11" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.CardDragStarting += this.OnKanbanCardDragStarting;

private void OnKanbanCardDragStarting(object sender, KanbanCardDragStartingEventArgs e)
{
        var draggingCard = e.Card;
        var draggingColumn = e.Column;
        e.IsDraggingCardRetained = true;

        /*e.IsDraggingCardRetained is also use for specific columns with the column name
        if (e.Column.HeaderText.ToString() == "Menu")
        {
            e.IsDraggingCardRetained = true;
        }*/
            
}

{% endhighlight %}
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
        return taskDetails;
    }

    #endregion
}

{% endhighlight %}

{% endtabs %}

## DragOver

The [CardDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDragOver) event occurs when a card is being dragged over a column. We can get the following details from the [CardDragOver](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDragOver) event.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragOverEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragOverEventArgs_Column) - Returns the column in which the card is currently being dragged.
* [CurrentIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragOverEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragOverEventArgs_CurrentIndex) - Returns the current index position of the card within its column.
* [CurrentColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragOverEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragOverEventArgs_CurrentColumnIndex) - Returns the current index of the column that contains the card.
* [CurrentRowIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDragOverEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDragOverEventArgs_CurrentRowIndex) - Returns the current row index of the swimlane that contains the card. The current row index is applicable only for the swimlane column and is used to get the swimlane's index.

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 CardDragOver="OnKanbanCardDragOver">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.CardDragOver += this.OnKanbanCardDragOver;

private void OnKanbanCardDragOver(object sender, KanbanCardDragOverEventArgs e)
{
    var currentColumn = e.Column;
    var currentIndex = e.CurrentIndex;
    var currentColumnIndex = e.CurrentColumnIndex;
    var currentRowIndex = e.CurrentRowIndex;
}

{% endhighlight %}

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
        return taskDetails;
    }

    #endregion
}

{% endhighlight %}

{% endtabs %}

## Drop

The [CardDrop](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDrop) event occurs when a dragged card is dropped into a column. We can get the following details from the [CardDrop](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardDrop) event.

* [SourceColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_SourceColumn) - Returns the column from which the user drags the card.
* [PreviousCardIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_PreviousCardIndex) - Returns the integer value that indicates the previous card index while dragging into the next column.
* [PreviousColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_PreviousColumnIndex) - Returns the integer value indicating the previous card's column index while drag enters next column.
* [PreviousRowIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_PreviousRowIndex) - Returns the integer value indicating the previous card's swimlane index while drag enters next swimlane. It is applicable only for the swimlane column.
* [TargetColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_TargetColumn) - Returns the target column upon which the card is dropped.
* [TargetSwimlane](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_TargetSwimlane) - Returns the target swimlane on which the card is dropped.
* [TargetCardIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_TargetCardIndex) - Returns the index in the target column where the card is going to be inserted.
* [TargetColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_TargetColumnIndex) - Returns the target column index where the card is going to be inserted.
* [TargetRowIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardDropEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardDropEventArgs_TargetRowIndex) - Returns the integer value indicating the target row index of the swimlane where the card is going to be inserted. It is applicable only for the swimlane column.

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 CardDrop="OnKanbanCardDrop">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.CardDrop += this.OnKanbanCardDrop;

private void OnKanbanCardDrop(object sender, KanbanCardDropEventArgs e)
{
    var sourceColumn = e.SourceColumn;
    var previousCardIndex = e.PreviousCardIndex;
    var previousColumnIndex = e.PreviousColumnIndex;
    var previousRowIndex = e.PreviousRowIndex;
    var targetColumn = e.TargetColumn;
    var targetCardIndex = e.TargetCardIndex;
    var targetColumnIndex = e.TargetColumnIndex;
    var targetRowIndex = e.TargetRowIndex;
    var targetSwimlane = e.TargetSwimlane;
}

{% endhighlight %}

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
        return taskDetails;
    }

    #endregion
}

{% endhighlight %}

{% endtabs %}

## CardTapped

The [CardTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTapped) event occurs when the card is tapped. We can get the following details from the [CardTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTapped) event.

* [SelectedCard](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardTappedEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardTappedEventArgs_SelectedCard) - Returns the instance of the card that was tapped.
* [SelectedColumn](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardTappedEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardTappedEventArgs_SelectedColumn) - Returns the instance of the column containing the tapped card.
* [SelectedCardIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardTappedEventArgs.html#Syncfusion_UI_Xaml_Kanban_KanbanCardTappedEventArgs_SelectedCardIndex) - Returns the index position of the tapped card within its column.

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 CardTapped="OnKanbanCardTapped">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
this.kanban.CardTapped += this.OnKanbanCardTapped;

private void OnKanbanCardTapped(object sender, KanbanCardTappedEventArgs e)
{
    var selectedCard = e.SelectedCard;
    var selectedColumn = e.SelectedColumn;
    var selectedCardIndex = e.SelectedCardIndex;
}

{% endhighlight %}

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
        return taskDetails;
    }

    #endregion
}

{% endhighlight %}

{% endtabs %}

## Command

Kanban commands allow to map [CardTapped](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTapped) event to command which supports the MVVM (Model-View-ViewModel) pattern.

### CardTappedCommand

The [CardTappedCommand](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTappedCommand) is triggered when a card is tapped, passing the [KanbanCardTappedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanCardTappedEventArgs.html) as a parameter.

{% tabs %}
{% highlight XAML hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 CardTappedCommand="KanbanCardTappedCommand">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="ViewModel.cs" hl_lines="25 122 123 125 126 127 128 129 130 131 132 134 135 136 137 138 139 140 141 142 143" %}

    public class ViewModel
    {
        #region Properties

        /// <summary>
        /// Gets or sets the collection of <see cref="KanbanModel"/> objects representing tasks in various stages.
        /// </summary>
        public ObservableCollection<KanbanModel> TaskDetails { get; set; }

        /// <summary>
        /// Gets or sets the command that is executed when a Kanban card is tapped.
        /// </summary>
        public ICommand CardTappedCommand { get; set; }

        #endregion

        #region Constructor

        /// <summary>
        /// Initializes a new instance of the <see cref="ViewModel"/> class.
        /// </summary>
        public ViewModel()
        {
            this.TaskDetails = this.GetTaskDetails();
            this.CardTappedCommand = new RelayCommand(OnCardTapped, CanExecuteCardTapped);
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

        /// <summary>
        /// Handles the event when a Kanban card is tapped.
        /// </summary>
        /// <param name="parameter">The object.</param>
        private void OnCardTapped(object parameter)
        {
            if (parameter is KanbanCardTappedEventArgs args)
            {
                var selectedCoumn = args.SelectedColumn;
            }
        }

        /// <summary>
        /// Determines whether the CardTapped command can be executed.
        /// </summary>
        /// <param name="sender">The source of the command.</param>
        /// <returns>Returns a boolean indicating whether the command can be executed.</returns>
        private bool CanExecuteCardTapped(object sender)
        {
            return true;
        }

        #endregion
    }

{% endhighlight %}

{% highlight C# tabtitle="RelayCommand.cs" %}

public class RelayCommand : ICommand
{
    public event EventHandler CanExecuteChanged;

    private readonly Action<object> execute;
    
    private readonly Predicate<object> canExecute;

    public RelayCommand(Action<object> execute, Predicate<object> canExecute = null)
    {
        this.execute = execute;
        this.canExecute = canExecute;
    }

    public RelayCommand(Action<object> executeAction)
    {
        this.execute = executeAction;
    }

    public bool CanExecute(object parameter) => canExecute == null || canExecute(parameter);

    public void Execute(object parameter) => execute(parameter);


    public void RaiseCanExecuteChanged()
    {
        if (CanExecuteChanged != null)
        {
            CanExecuteChanged(this, new EventArgs());
        }
    }
}

{% endhighlight %}
{% endtabs %}