---
layout: post
title: Getting Started with WinUI Segmented Control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Segmented Control(SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Getting Started with WinUI Segmented Control

This section provides an overview for working with the [WinUI Segmented Control](). Walk through the entire process of creating a real world application with this control.

## Creating an application with WinUI Barcode

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).

2. Add reference to [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet. 

3. Import the control namespace `using Syncfusion.UI.Xaml.Editors` in XAML or C# code.

4. Initialize the SfSegmentedControl.


{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors" 
    mc:Ignorable="d">
    <Grid x:Name="Root_Grid">
        <syncfusion:SfSegmentedControl x:Name="segmentedControl" />
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %} 

using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Editors;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        SfSegmentedControl SegmentedControl = new SfSegmentedControl();
        Root_Grid.Children.Add(SegmentedControl);
    }
}

{% endhighlight %}
{% endtabs %} 

## Populating items through string collection

The segmented control provides the collection of strings as a data source.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors" 
    mc:Ignorable="d">
    <Grid>
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
        <syncfusion:SfSegmentedControl x:Name="segmentedControl"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="2"
                                    ItemsSource="{Binding Days}" />
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %

public class SegmentedViewModel
{
    public SegmentedViewModel()
    {
        Days = new List<string>();
        Days.Add("Day");
        Days.Add( "Week");
        Days.Add("Month");
        Days.Add("Year");
    }

    public List<string> Days
    {
        get; set;
    }
}

{% endhighlight %}
{% endtabs %} 

## Populating items using business objects

You can populate items to the Segmented Control by setting the collection value to the `ItemsSource` property.

### ItemTemplate

Users can customize the appearance of each `SfSegmentedItem` by using the `ItemTemplate` property.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:markup="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors" 
    markup:Ignorable="d">
    <Grid>
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
        <syncfusion:SfSegmentedControl x:Name="segmentedControl"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="2"
                                    ItemsSource="{Binding Days}">
            <syncfusion:SfSegmentedControl.ItemTemplate>
                <DataTemplate>
                    <Grid>
                        <TextBlock Text="{Binding Name}"
                                   HorizontalAlignment="Center"
                                   VerticalAlignment="Center"/>
                    </Grid>
                </DataTemplate>
            </syncfusion:SfSegmentedControl.ItemTemplate>
        </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %} 

public class SegmentedViewModel
{
    public SegmentedViewModel()
    {
        Days = new List<SegmentedModel>();
        Days.Add(new SegmentedModel() { Name = "Day" });
        Days.Add(new SegmentedModel() { Name = "Week" });
        Days.Add(new SegmentedModel() { Name = "Month" });
        Days.Add(new SegmentedModel() { Name = "Year" });
    }

    public List<SegmentedModel> Days
    {
        get; set;
    }
}

public class SegmentedModel : INotifyPropertyChanged
{
    private string name;

    public string Name
    {
        get { return name; }
        set { name = value; OnPropertyChanged("Name"); }
    }

    public event PropertyChangedEventHandler PropertyChanged;

    private void OnPropertyChanged(string parameter)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(parameter));
    }
}

{% endhighlight %}
{% endtabs %} 

### DisplayMemberPath

You can set `DisplayMemberPath` which denotes the path to a value on the source object (SfSegmentedControl.ItemsSource) to serve as the visual representation of object. The below code snippet will be used to bind the DataSource to the ComboBoxAdv.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:markup="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors" 
    markup:Ignorable="d">
    <Grid>
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
        <syncfusion:SfSegmentedControl x:Name="segmentedControl"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="2"
                                    DisplayMemberPath="Name"
                                    ItemsSource="{Binding Days}">
            <syncfusion:SfSegmentedControl.ItemTemplate>
                <DataTemplate>
                    <Grid>
                        <TextBlock Text="{Binding Name}"
                                   HorizontalAlignment="Center"
                                   VerticalAlignment="Center"/>
                    </Grid>
                </DataTemplate>
            </syncfusion:SfSegmentedControl.ItemTemplate>
        </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% highlight C# %} 

public class SegmentedViewModel
{
    public SegmentedViewModel()
    {
        Days = new List<SegmentedModel>();
        Days.Add(new SegmentedModel() { Name = "Day" });
        Days.Add(new SegmentedModel() { Name = "Week" });
        Days.Add(new SegmentedModel() { Name = "Month" });
        Days.Add(new SegmentedModel() { Name = "Year" });
    }

    public List<SegmentedModel> Days
    {
        get; set;
    }
}

public class SegmentedModel : INotifyPropertyChanged
{
    private string name;

    public string Name
    {
        get { return name; }
        set { name = value; OnPropertyChanged("Name"); }
    }

    public event PropertyChangedEventHandler PropertyChanged;

    private void OnPropertyChanged(string parameter)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(parameter));
    }
}

{% endhighlight %}
{% endtabs %} 

![WinUI Segmented Control with DisplayMemberPath](Getting_Started_Images/gettingstarted.png)

