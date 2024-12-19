---
layout: post
title: Cards in WinUI Kanban control | Syncfusion
description: This section describes about cards in Syncfusion WinUI Kanban (SfKanban) control, its elements and more.
platform: winui
control: SfKanban
documentation: ug
---

# Cards in WinUI Kanban (SfKanban) control

The Kanban cards visually represent tasks and their progression through various stages. The default UI of each card can be customized using the following properties of the [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html).

* [Title](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Title) - Sets the title of the card.
* [Description](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Description) - Sets the description text of the card.
* [Category](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Category) - Sets the category of the card, determining which column it will be placed in.
* [Assignee](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Assignee) - Defines the assignee associated with the card in the [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html).
* [Image](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Image) - Sets the image for the card, which is displayed on the right side in the default card template.
* [IndicatorColorKey](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_IndicatorColorKey) - Specifies the indicator color for the card, commonly used for categorize or prioritize card based on color key values.
* [Id](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Id) - Sets the unique ID of the card.
* [Tags](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#Syncfusion_UI_Xaml_Kanban_KanbanModel_Tags) - Specifies the tags for the card, displayed at the bottom of the default card template.

Below is an example that shows how to define values in the [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html).

{% highlight C# %}

new KanbanModel()
{
    Title = "UWP Issue",
    Id = "651",
    Description = "Crosshair label template not visible in UWP",
    Category = "Open",
    IndicatorColorKey = "High",
    Tags = new List() { "Bug Fixing" },
    Image = new Image
    {
        Source = new BitmapImage(new Uri("ms-appx:///Assets/Kanban/People_Circle1.png"))
    }
};

{% endhighlight %}

The following code snippet defines the colors for each key.

{% tabs %}
{% highlight XAML hl_lines="6 7 8 9 10" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
    <kanban:SfKanban.IndicatorColorPalette>
        <kanban:KanbanColorMapping Key="Low" Color="Blue"/>
        <kanban:KanbanColorMapping Key="Normal" Color="Green"/>
        <kanban:KanbanColorMapping Key="High" Color="Red"/>
    </kanban:SfKanban.IndicatorColorPalette>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# hl_lines="2 3 4 5 6" %}

this.kanban.ItemsSource = new ViewModel().TaskDetails;
List<KanbanColorMapping> indicatorColorPalette = new List();
indicatorColorPalette.Add(new KanbanColorMapping() { Key="Low", Color = Colors.Blue });
indicatorColorPalette.Add(new KanbanColorMapping() { Key= "Normal", Color = Colors.Green });
indicatorColorPalette.Add(new KanbanColorMapping() { Key= "High", Color = Colors.Red });
this.kanban.IndicatorColorPalette = indicatorColorPalette;

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
        taskDetail.Category = "In Progress";
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
        taskDetail.Category = "Closed";
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
{% endtabs %}

## Card appearance customization

The card appearance customization can be achieved by using the [CardTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplate) and [CardTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplateSelector) properties in the [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html).

### Customize card appearance using DataTemplate

You can replace the entire card template with your own design and customize its appearance using the [CardTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplate) property in [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html).

The following code snippet demonstrates, how to use the [CardTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplate) property to apply a custom template to kanban cards.

{% tabs %}
{% highlight XAML hl_lines="3 4 5 6 7 8 9 10 11 12" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.CardTemplate>
        <DataTemplate>
            <Border BorderBrush="LightGray" BorderThickness="1" CornerRadius="3" Background="#F3F3F2">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" TextAlignment="Center" FontWeight="Bold" FontSize="14" />
                    <TextBlock Text="{Binding Description}" TextAlignment="Center" FontSize="12" TextWrapping="Wrap" Margin="5" />
                </StackPanel>
            </Border>
        </DataTemplate>
    </kanban:SfKanban.CardTemplate>
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
        taskDetail.Description = "In minimized state, first and last segments have incorrect spacing";
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
        taskDetail.Title = "WPF Issue";
        taskDetail.Id = "25678";
        taskDetail.Description = "Minimum and maximum properties are not working in dynamic update";
        taskDetail.Category = "In Progress";
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
        taskDetail.Description = "Need to implement tooltip support for Kanban";
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

### Customize card appearance using DataTemplateSelector

You can customize the card appearance by using the [CardTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplateSelector) property in the [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html). The `DataTemplateSelector` can choose a `DataTemplate` at runtime based on the value of a data-bound to kanban card appearance by using the [CardTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplateSelector). It allows you to choose a different data template for each card, as well as to customize the appearance of a particular card based on certain conditions.

{% tabs %}
{% highlight XAML hl_lines="28" %}

<Grid>
    <Grid.DataContext>
        <local:ViewModel/>
    </Grid.DataContext>    
    <Grid.Resources>
        <DataTemplate x:Key="highPriorityTemplate">
            <Border BorderBrush="Black" BorderThickness="1" CornerRadius="3" Background="#F3CFCE">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" FontWeight="Bold" TextAlignment="Center" FontSize="14" />
                    <TextBlock Text="{Binding Description}" FontSize="12" TextAlignment="Center" TextWrapping="Wrap" Margin="5" />
                </StackPanel>
            </Border>
        </DataTemplate>
        <DataTemplate x:Key="defaultTemplate">
            <Border BorderBrush="Black" BorderThickness="1" CornerRadius="3" Background="#F3EADC">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" FontWeight="Bold" TextAlignment="Center" FontSize="14" />
                    <TextBlock Text="{Binding Description}" FontSize="12" TextAlignment="Center" TextWrapping="Wrap" Margin="5" />
                </StackPanel>
            </Border>
        </DataTemplate>
        <local:KanbanCardTemplateSelector x:Key="cardTemplateSelector"
                                          HighPriorityTemplate="{StaticResource highPriorityTemplate}"
                                          DefaultTemplate="{StaticResource defaultTemplate}"/>
    </Grid.Resources>

    <kanban:SfKanban x:Name="kanban" 
                     CardTemplateSelector="{StaticResource cardTemplateSelector}"
                     ItemsSource="{Binding TaskDetails}">
    </kanban:SfKanban>
</Grid>

{% endhighlight %}

{% highlight C# tabtitle="KanbanCardTemplateSelector.cs" %}

public class KanbanCardTemplateSelector : DataTemplateSelector
{
    public DataTemplate HighPriorityTemplate { get; set; }
    public DataTemplate DefaultTemplate { get; set; }

    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
        var task = item as KanbanModel;
        if (task != null && task.IndicatorColorKey == "High")
        {
            return HighPriorityTemplate;
        }

        return DefaultTemplate;
    }
}

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
        taskDetail.Description = "In minimized state, first and last segments have incorrect spacing";
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
        taskDetail.Title = "WPF Issue";
        taskDetail.Id = "25678";
        taskDetail.Description = "Minimum and maximum properties are not working in dynamic update";
        taskDetail.Category = "In Progress";
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
        taskDetail.Description = "Need to implement tooltip support for Kanban";
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

N> The `DataContext` for both the [CardTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplate) and [CardTemplateSelector](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html#Syncfusion_UI_Xaml_Kanban_SfKanban_CardTemplateSelector) properties in the [SfKanban](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.SfKanban.html) is set to [KanbanModel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html).