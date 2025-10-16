---
layout: post
title: Sorting in .NET WinUI Kanban Board control | Syncfusion<sup>®</sup>
description: Learn here all about Sorting support in Syncfusion<sup>®</sup> .NET WinUI Kanban Board (SfKanban) control and more.
platform: WinUI
control: SfKanban
documentation: ug
---

# Card Item Sorting in .NET WinUI Kanban (SfKanban)

The Kanban control supports customizable card sorting within columns based on specific data fields such as `Priority`, `DueDate`, or `Status`. Sorting can be configured programmatically and updated dynamically at runtime using the following properties:

* `SortingMappingPath` - Used to map the sorting field to a property name in the `KanbanModel` or `CustomModel`. The default value is `string.Empty`, in which case the cards will not be sorted.
* `SortingOrder` - Used to define the direction of cards sorting within each column.
   * `Ascending` - Cards with lower values appear first.
   * `Descending` - Cards with higher values appear first. 

N> The `SortingOrder` property is applicable only when a valid value is assigned to `SortingMappingPath`.

## Customize card order with sorting configuration

Sorting in the Kanban control can be implemented using the following approaches.

   * Custom
   * Index

### Custom Field Sorting

To enable custom sorting behavior, a valid property name from the `ItemsSource` must be mapped using the `SortingMappingPath` property. This mapping ensures that cards are loaded and repositioned based on the corresponding property value, allowing consistent sorting during both initialization and drag-and-drop operations.

This example demonstrates how card positions are updated based on sorting configurations and property mappings.

{% tabs %}
{% highlight XAML hl_lines="3 5" %}

<kanban:SfKanban x:Name="kanban" 
                 SortingMappingPath="Priority"
                 SortingOrder="Ascending"
                 ItemsSource="{Binding Cards}"
                 ColumnMappingPath="Category">
    <kanban:SfKanban.CardTemplate>
        <DataTemplate>
            <Border Background="#F3CFCE" BorderBrush="Black" BorderThickness="1" CornerRadius="8" Padding="8">
                <Grid ColumnSpacing="8">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="Auto" />
                    </Grid.RowDefinitions>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="*" />
                    </Grid.ColumnDefinitions>
                    <StackPanel Grid.Row="0" Grid.ColumnSpan="2" Orientation="Horizontal"
                                Spacing="4" VerticalAlignment="Center" Height="20">
                        <TextBlock Text="•" FontSize="14" FontWeight="Bold" Foreground="Orange"
                                    VerticalAlignment="Center" HorizontalAlignment="Center" />
                        <TextBlock Text="{Binding Priority}" FontSize="14" FontWeight="Bold" Foreground="Orange"
                                    VerticalAlignment="Center" HorizontalAlignment="Left" Height="20" />
                    </StackPanel>
                    <TextBlock Grid.Row="1" Grid.ColumnSpan="2" Text="{Binding Title}" FontWeight="Bold"
                               FontSize="14" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="5" />
                    <TextBlock  Grid.Row="2" Grid.ColumnSpan="2" Text="{Binding Description}" FontSize="12"
                                TextWrapping="WrapWholeWords" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="5" />
                </Grid>
            </Border>
        </DataTemplate>
    </kanban:SfKanban.CardTemplate>
    <kanban:KanbanColumn HeaderText="Open" Categories="Open"/>
    <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress"/>
    <kanban:KanbanColumn HeaderText="Done" AllowDrag="False" Categories="Done"/>
    <kanban:SfKanban.DataContext>
        <local:SortingViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}
{% highlight C# hl_lines="2 6" %}

this.kanban.ItemsSource = new SortingViewModel().Cards;
this.kanban.CardDrop += this.OnCardDrop;

private void OnCardDrop(object sender, KanbanCardDropEventArgs e)
{
    this.kanban.RefreshKanbanColumn(e.TargetColumn.AllowedTransitionCategory.ToString());
}

{% endhighlight %}
{% highlight c# tabtitle="CardDetails.cs" %}

public class CardDetails
{
    public string? Title { get; set; }
    public string? Description { get; set; }
    public string? Priority { get; set; }
    public string? Category { get; set; }
}

{% endhighlight %}
{% highlight c# tabtitle="SortingViewModel.cs" %}

public class SortingViewModel
{
    public SortingViewModel()
    {
        this.Cards = new ObservableCollection<CardDetails>()
        {
            new CardDetails() { Title = "Task - 1", Priority = "Medium", Category = "Open", Description = "Fix the issue reported in the Edge browser." },
            new CardDetails() { Title = "Task - 3", Priority = "Low", Category = "In Progress", Description = "Analyze the new requirements gathered from the customer." },
            new CardDetails() { Title = "Task - 4", Priority = "Critical", Category = "Open", Description = "Arrange a web meeting with the customer to get new requirements." },
            new CardDetails() { Title = "Task - 2", Priority = "High", Category = "In Progress", Description = "Test the application in the Edge browser." },
            new CardDetails() { Title = "Task - 5", Priority = "Medium", Category = "Done", Description = "Enhance editing functionality." },
            new CardDetails() { Title = "Task - 8", Priority = "Medium", Category = "In Progress", Description = "Improve application performance." },
            new CardDetails() { Title = "Task - 9", Priority = "Medium", Category = "Done", Description = "Improve the performance of the editing functionality." },
            new CardDetails() { Title = "Task - 10", Priority = "High", Category = "Open", Description = "Analyze grid control." },
            new CardDetails() { Title = "Task - 12", Priority = "Low", Category = "Done", Description = "Analyze stored procedures." }
        };
    }

    public ObservableCollection<CardDetails> Cards { get; set; }
}

N> 
 * To apply sorting after a drop operation, handle the `CardDrop` event and explicitly call the `RefreshKanbanColumn` method. This ensures the column updates to reflect the new card order based on the defined sorting logic.
 * When using a custom data model, the default card UI is not applicable. To render the card content, you must define a custom `DataTemplate` using the `CardTemplate` property.

{% endhighlight %}
{% endtabs %}

### Index-Based Sorting

The index-based approach in the Kanban control allows cards to be dropped at precise positions within a column. Upon dropping, the card's index is updated based on the index of the previous card. Additionally, the index of the next card is incremented relative to the drop position to maintain continuous ordering.

N> The `SortingMappingPath` property must be mapped to a valid numeric property name from the `ItemsSource` to enable index-based sorting updates.

The following code example illustrates how cards numeric property updated using the index-based sorting approach.

{% tabs %}
{% highlight XAML hl_lines="2 3" %}

<kanban:SfKanban x:Name="kanban" 
                 SortingMappingPath="Index"
                 SortingOrder="Ascending"
                 ItemsSource="{Binding Cards}"
                 ColumnMappingPath="Category">
    <kanban:SfKanban.CardTemplate>
        <DataTemplate>
            <Border Background="#F3EADC" BorderBrush="Black" BorderThickness="1" CornerRadius="8" Padding="8">
                <Grid ColumnSpacing="8">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="Auto" />
                        <RowDefinition Height="Auto" />
                    </Grid.RowDefinitions>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto" />
                        <ColumnDefinition Width="*" />
                    </Grid.ColumnDefinitions>
                    <StackPanel Grid.Row="0" Grid.ColumnSpan="2" Orientation="Horizontal"
                                VerticalAlignment="Center" HorizontalAlignment="Right" >
                        <TextBlock Text="Rank #" FontSize="14" FontWeight="Bold" Foreground="#026B6E"
                                   VerticalAlignment="Center" HorizontalAlignment="Center" />
                        <TextBlock Text="{Binding Index}" FontSize="14" FontWeight="Bold" Foreground="#026B6E"
                                   VerticalAlignment="Center" HorizontalAlignment="Center"  />
                    </StackPanel>
                    <TextBlock Grid.Row="1" Grid.ColumnSpan="2" Text="{Binding Title}" FontWeight="Bold"
                               FontSize="14" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="5" />
                    <TextBlock  Grid.Row="2" Grid.ColumnSpan="2" Text="{Binding Description}" FontSize="12"
                                TextWrapping="WrapWholeWords" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="5" />
                </Grid>
            </Border>
        </DataTemplate>
    </kanban:SfKanban.CardTemplate>
    <kanban:KanbanColumn HeaderText="Open" Categories="Open"/>
    <kanban:KanbanColumn HeaderText="In Progress" Categories="In Progress"/>
    <kanban:KanbanColumn HeaderText="Done" AllowDrag="False" Categories="Done"/>
    <kanban:SfKanban.DataContext>
        <local:SortingViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}
{% highlight C# hl_lines="2 6 7" %}

this.kanban.ItemsSource = new SortingViewModel().Cards;
this.kanban.CardDrop += this.OnCardDrop;

private void OnCardDrop(object? sender, KanbanDragEndEventArgs e)
{
    this.ApplySortingWithoutPositionChange(e);
    this.kanban.RefreshKanbanColumn(e.TargetColumn.AllowedTransitionCategory.ToString());
}

{% endhighlight %}
{% highlight c# tabtitle="CardDetails.cs" %}

public class CardDetails
{
    public string? Title { get; set; }
    public string? Description { get; set; }
    public int? Index { get; set; }
    public string? Category { get; set; }
}

{% endhighlight %}
{% highlight c# tabtitle="SortingViewModel.cs" %}

public class SortingViewModel
{
    public SortingViewModel()
    {
        this.Cards = new ObservableCollection<CardDetails>()
        {
            new CardDetails() { Title = "Task - 1", Index = 5, Category = "Open", Description = "Fix the issue reported in the Edge browser." },
            new CardDetails() { Title = "Task - 3", Index = 9, Category = "In Progress", Description = "Analyze the new requirements gathered from the customer." },
            new CardDetails() { Title = "Task - 4", Index = 2, Category = "Open", Description = "Arrange a web meeting with the customer to get new requirements." },
            new CardDetails() { Title = "Task - 2", Index = 1, Category = "In Progress", Description = "Test the application in the Edge browser." },
            new CardDetails() { Title = "Task - 5", Index = 8, Category = "Done", Description = "Enhance editing functionality." },
            new CardDetails() { Title = "Task - 8", Index = 3, Category = "In Progress", Description = "Improve application performance." },
            new CardDetails() { Title = "Task - 9", Index = 6, Category = "Done", Description = "Improve the performance of the editing functionality." },
            new CardDetails() { Title = "Task - 10", Index = 4, Category = "Open", Description = "Analyze grid control." },
            new CardDetails() { Title = "Task - 12", Index = 7, Category = "Done", Description = "Analyze stored procedures." }
        };
    }
    
    public ObservableCollection<CardDetails> Cards { get; set; }
}

{% endhighlight %}
{% endtabs %}

N> 
 * The Index-based sorting can be achieved at the sample level after a drag-and-drop action. To implement this handle the `CardDrop` event, access the items in the target column using `e.TargetColumn.Items`, and update the numeric field used for sorting to maintain a continuous order. Finally, call `RefreshKanbanColumn` method to update the UI with the new order.
 * To disable sorting logic, avoid assigning a value to the `SortingMappingPath` property. This ensures that card positions remain static and reflect the order of the `ItemsSource` collection, making it suitable for scenarios where sorting is not required or is managed externally.
