---
layout: post
title: Columns in WinUI Kanban control | Syncfusion
description: Learn here all about configuring and customizing columns in Syncfusion WinUI Kanban (SfKanban) control.
platform: winui
control: SfKanban
documentation: ug
---

# Column in WinUI Kanban Control

The WinUI Kanban control organizes its layout into columns, representing distinct stages of a workflow or process. Common stages include To-Do, In-Progress, Testing, Validation, and Completed.

## Customizing column width

Columns are smartly sized by default to ensure optimal arrangement and readability of card elements. However, you can customize column widths to suit your specific requirements by using `MinimumColumnWidth` and `MinimumColumnWidth` properties of `SfKanban`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 4" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 MinimumColumnWidth="300"
                 MinimumColumnWidth="350">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" %}

this.kanban.MinimumColumnWidth = 300;
this.kanban.MaximumColumnWidth = 350;

{% endhighlight %}
{% endtabs %}

You can also define the exact width for the columns using `ColumnWidth` property of `SfKanban`.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 ColumnWidth="400">
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" %}

this.kanban.ColumnWidth = 400;

{% endhighlight %}
{% endtabs %}

## Categorizing columns

In the WinUI Kanban Control, cards are categorized and placed into their respective columns based on the value of the `Category` property of `KanbanModel`.

### Populating columns with cards from Multiple categories

You can populate a single column with cards from multiple categories by assigning multiple values to the `Categories` collection of the `KanbanColumn`. For example, to group tasks categorized as `Review` and `Closed` under a single `Done`column, you can include both category values in the `Categories` collection.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="3 6" %}

<kanban:SfKanban x:Name="kanban"
                 ItemsSource="{Binding TaskDetails}"
                 AutoGenerateColumns="False">
    <kanban:KanbanColumn Categories="Open" HeaderText="To Do"/>
    <kanban:KanbanColumn Categories="In Progress" HeaderText="Progress"/>
    <kanban:KanbanColumn Categories="Review,Closed" HeaderText="Done"/>
</kanban:SfKanban>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" hl_lines="3" %}

this.kanban.Columns.Add(new KanbanColumn() { Categories = "Open", HeaderText = "To Do", });
this.kanban.Columns.Add(new KanbanColumn() { Categories = "In Progress", HeaderText = "Progress", });
this.kanban.Columns.Add(new KanbanColumn() { Categories = "Review,Closed", HeaderText = "Done", });

{% endhighlight %}
{% endtabs %}

## Customizing column headers

### Customizing column header text

You can set the header text for a column using the `HeaderText` property, which allows you to display simple text as the column title.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<kanban:KanbanColumn Categories="Open" HeaderText="To Do"/>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" %}

this.kanban.Columns.Add(new KanbanColumn() { Categories = "Open", HeaderText = "To Do" });

{% endhighlight %}
{% endtabs %}}

### Customizing column header template

To replace the UI of the header, you can use the `ColumnHeaderTemplate` of the `SfKanban`. The following code example illustrates how this can be done.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<kanban:SfKanban x:Name="kanban"
                    ItemsSource="{Binding TaskDetails}">
    <kanban:SfKanban.ColumnHeaderTemplate>
        <DataTemplate>
            <StackPanel Background="LightBlue">
                <TextBlock Margin="10" Text="{Binding  HeaderText}" Foreground="Red" HorizontalAlignment="Center"/>
            </StackPanel>
        </DataTemplate>
    </kanban:SfKanban.ColumnHeaderTemplate>
    <kanban:SfKanban.DataContext>
        <local:ViewModel/>
    </kanban:SfKanban.DataContext>
</kanban:SfKanban>

{% endhighlight %}
{% endtabs %}

## Expand/Collapse column

To expand or collapse a column programmatically, use the `KanbanColumn.IsExpanded` property. Set this property to `true` to expand the column or `false` to collapse it.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<kanban:KanbanColumn Categories="Open" HeaderText="To Do" IsExpanded="False"/>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" %}

this.kanban.Columns.Add(new KanbanColumn() { Categories = "Open", HeaderText = "To Do", IsExpanded = false });

{% endhighlight %}
{% endtabs %}

## Enable/Disable Drag & Drop

The WinUI Kanban Control allows you to enable or disable the drag-and-drop functionality for cards using the `KanbanColumn.AllowDrag` property.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" %}

<kanban:KanbanColumn Categories="Open" HeaderText="To Do" AllowDrag="False" AllowDrop="False"/>

{% endhighlight %}

{% highlight C# tabtitle="MainWindow.xaml.cs" %}

this.kanban.Columns.Add(new KanbanColumn() { Categories = "Open", HeaderText = "To Do", AllowDrag = false, AllowDrop = false });

{% endhighlight %}
{% endtabs %}