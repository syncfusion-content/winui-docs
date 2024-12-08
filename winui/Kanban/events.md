---
layout: post
title: Events in WinUI Kanban control | Syncfusion
description: Learn here all about the interaction-related events support in Syncfusion WinUI Kanban (SfKanban) control.
platform: winui
control: SfKanban
documentation: ug
---

# Events in WinUI Kanban Control

## Notifying Kanban card drag start

The `CardDragStarting` event occurs when the card start to drag. We can get the below details from the `CardDragStarting` event.

* Column -  Returns the source column from which the card is being dragged.
* Card - Returns the dragging card in the kanban.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 CardDragStarting="OnKanbanCardDragStarting"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}

this.kanban.CardDragStarting += this.OnKanbanCardDragStarting;

private void OnKanbanCardDragStarting(object sender, KanbanCardDragStartingEventArgs e)
{
    var selectedCard = e.Card;
    var selectedcolumn = e.Column;
}

{% endhighlight %}
{% endtabs %}

## Notifying Kanban card drag over 

The `CardDragOver` event occurs when card drag started in a column. We can get the below details from the `CardDragOver` event.

* Column - Returns the column in which the card is currently being dragged.
* CurrentIndex - Returns the current index position of the card within its column.
* CurrentColumnIndex - Returns the current index of the column that contains the card.
* CurrentRowIndex - Returns the current row index of the swimlane that contains the card. The current row index is relevant only for the swimlane column and is used to get the swimlane's index.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 CardDragOver="OnKanbanCardDragOver"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}

this.kanban.CardDragOver += this.OnKanbanCardDragOver;

private void OnKanbanCardDragOver(object sender, KanbanCardDragOverEventArgs e)
{
    var currentColumn = e.Column;
    var currentIndex = e.CurrentIndex;
    var currentColumnIndex = e.CurrentColumnIndex;
    var currentRowIndex = e.CurrentRowIndex;
}

{% endhighlight %}
{% endtabs %}

## Notifying Kanban card drop

The `CardDrop` event occurs when leaving the dragging card from one column. We can get the below details from the `CardDrop` event.

* SourceColumn - Returns the target column out of which the user drags the card.
* PreviousCardIndex - Returns the integer value that indicates the previous card index while dragging into the next column.
* PreviousColumnIndex - Returns the integer value indicating the previous card's column index while drag enters next column.
* PreviousRowIndex - Returns the integer value indicating the previous card's swimlane index while drag enters next swimlane. It is applicable only for the swimlane column.
* TargetColumn - Returns the target column upon which the card is dropped.
* TargetSwimlane - Returns the target swimlane on which the card is dropped.
* TargetCardIndex - Returns the index in the target column where the card is going to be inserted.
* TargetColumnIndex - Returns the target column index where the card is going to be inserted.
* TargetRowIndex - Returns the integer value indicating the target row index of the swimlane where the card is going to be inserted. It is applicable only for the swimlane column.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 CardDrop="OnKanbanCardDrop"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}

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
{% endtabs %}

## Notifying Kanban card tap

The `CardTapped` event occurs when the card is tapped. We can get the below details from the `CardTapped` event.

* SelectedCard - Returns the instance of the card that was tapped.
* SelectedColumn - Returns the instance of the column containing the tapped card.
* SelectedCardIndex - Returns the index position of the tapped card within its column.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 CardTapped="OnKanbanCardTapped"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="1" %}

this.kanban.CardTapped += this.OnKanbanCardTapped;

private void OnKanbanCardTapped(object sender, KanbanCardTappedEventArgs e)
{
    var selectedCard = e.SelectedCard;
    var selectedColumn = e.SelectedColumn;
    var selectedCardIndex = e.SelectedCardIndex;
}

{% endhighlight %}
{% endtabs %}

#### Command

The `CardTappedCommand` property is used to associate a command with an instance of SfKanban. This property is most often set with MVVM pattern to bind callbacks back into the ViewModel.

{% tabs %}
{% highlight XAML tabtitle="MainWindow.xaml" hl_lines="2" %}

<kanban:SfKanban x:Name="kanban"
                 CardTappedCommand="KanbanCardTappedCommand"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="ViewModel"  %}

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
            CardTappedCommand = new RelayCommand(OnCardTapped, CanExecuteCardTapped);
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
        /// <param name="parameter"></param>
        private void OnCardTapped(object parameter)
        {
            if (parameter is KanbanCardTappedEventArgs args)
            {
                var selectedCoumn = args.SelectedColumn;
            }
        }

        /// <summary>
        /// Determines whether card tapped can be executed.
        /// </summary>
        /// <param name="sender"></param>
        /// <returns></returns>
        private bool CanExecuteCardTapped(object sender)
        {
            return true;
        }

        #endregion
    }

{% endhighlight %}

{% highlight C# tabtitle="RelayCommand"  %}

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