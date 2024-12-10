---
layout: post
title: Cards in WinUI Kanban control | Syncfusion
description: This section describes about cards in Syncfusion WinUI Kanban (SfKanban) control, its elements and more.
platform: winui
control: SfKanban
documentation: ug
---

# Cards in WinUI Kanban Control

Cards in the WinUI Kanban Control provide a visual representation of tasks as they move through different stages of a workflow. Each card corresponds to a task and displays key information, such as the title, description, tags, and status, helping users track progress and manage tasks effectively.

The appearance and content of the cards can be customized using the below properties of `KanbanModel`.

* `Title` - Gets or sets the string value used to display the header of a card in the KanbanModel.
* `Description` - Gets or sets the string value used to display the description of a card in the KanbanModel.
* `Category` - Gets or sets the category associated with the card in the KanbanModel.
* `Assignee` - Gets or sets the assignee associated with the card in the KanbanModel.
* `Image` - Specifies the image source representing the card's assignee or related entity.
* `IndicatorColorKey` - Provides unique key with each Kanban card to dynamically assign indicator colors. It is often used in scenarios where cards are categorized or prioritized by color, based on specific key values.
* `Id` - Used to uniquely identify each Kanban card, allowing for efficient management, tracking, and updates of individual cards within Kanban control.
* `Tags` - Used to assign multiple tags to a kanban card, which can be used for categorization, filtering, or additional metadata.

{% highlight C# %}

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

{% endhighlight %}

Following code snippet is used to define the colors for each key.

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

{% highlight C# hl_lines="5" %}

List<KanbanColorMapping> indicatorColorPalette = new List<KanbanColorMapping>();
indicatorColorPalette.Add(new KanbanColorMapping() { Key="Low", Color = Colors.Blue });
indicatorColorPalette.Add(new KanbanColorMapping() { Key= "Normal", Color = Colors.Green });
indicatorColorPalette.Add(new KanbanColorMapping() { Key= "High", Color = Colors.Red });
this.kanban.IndicatorColorPalette = indicatorColorPalette;

{% endhighlight %}
{% endtabs %}

## Customizing kanban cards

### Customize kanban cards using template

The appearance of Kanban cards can be fully customized using the `CardTemplate` property of the `SfKanban` control. By setting this property, you can define a custom design for the entire card.

The following code snippet demonstrates how to use the `CardTemplate` property to apply a custom template to Kanban cards:

{% highlight xaml %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.CardTemplate>
        <DataTemplate>
            <Border BorderBrush="Green" BorderThickness="1" CornerRadius="10" Background="LightGreen">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" TextAlignment="Center" FontWeight="Bold" FontSize="14" />
                    <TextBlock Text="{Binding Description}" TextAlignment="Center" FontSize="14" TextWrapping="Wrap" />
                </StackPanel>
            </Border>
        </DataTemplate>
    </kanban:SfKanban.CardTemplate>
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

### Customize kanban cards using template selector

To dynamically apply different templates to Kanban cards based on specific conditions, use the `CardTemplateSelector` property. This allows you to define multiple templates and choose one at runtime based on card data.

{% tabs %}
{% highlight XAML hl_lines="28" %}

<Grid>
    <Grid.DataContext>
        <local:ViewModel/>
    </Grid.DataContext>    
    <Grid.Resources>
        <DataTemplate x:Key="highPriorityTemplate">
            <Border BorderBrush="Red" BorderThickness="2" CornerRadius="10" Background="LightPink">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" FontWeight="Bold" FontSize="16" />
                    <TextBlock Text="{Binding Description}" FontSize="14" TextWrapping="Wrap" />
                </StackPanel>
            </Border>
        </DataTemplate>
        <DataTemplate x:Key="defaultTemplate">
            <Border BorderBrush="Green" BorderThickness="1" CornerRadius="10" Background="LightGreen">
                <StackPanel Margin="10">
                    <TextBlock Text="{Binding Title}" FontWeight="Bold" FontSize="16" />
                    <TextBlock Text="{Binding Description}" FontSize="14" TextWrapping="Wrap" />
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
{% endtabs %}