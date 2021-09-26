---
layout: post
title: Selection with WinUI Segmented Control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Segmented Control(SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Selection in WinUI Segmented Control

This section explains how to customize the selected item and its related operations in the Segmented Control.

## Selected Item Customization

The Segmented Control allows you to customize the appearance of SelectedItem using the `SelectedSegmentStyle` property. we need to provide style of target type as [Border](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.border).

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
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
         <Grid.Resources>
            <Style TargetType="Border" x:Key="selectedItemStyle">
               <Setter Property="Background" Value="Olive"/>
            </Style>
        </Grid.Resources>
        <syncfusion:SfSegmentedControl x:Name="segmentedControl"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="2" 
                                    SelectedSegmentStyle="{StaticResource selectedItemStyle}"
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

![WinUI Segmented Control with selecteditem customization](Selection_Images/winui-segmented-control-selected-item-customization.png)

N> Users can't change the selected item foreground using SelectedSegmentStyle.


## SelectionChanged Event

The SelectionChanged event will occur once selection process has been completed for the selected item in the Segmented Control. The    `SegmentSelectionChangedEventArgs` has the following values which provides information for SelectionChanged event:

* NewValue: Gets the new value of `SelectedItem` has been assigned to the SegmentedControl.
* OldValue: Gets the old value of `SelectedItem` has been assigned to the SegmentedControl.

{% highlight C# %} 

segmentedControl.SelectionChanged += SegmentedControl_SelectionChanged;

private void SegmentedControl_SelectionChanged(object sender, SegmentSelectionChangedEventArgs e)
{
            
}

{% endhighlight %}


## Animation

Provided the slide animation support for selecting the item. Also users can enable or disable the selection animation. The default value is `Slide`.

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
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
        <syncfusion:SfSegmentedControl x:Name="segmentedControl"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="0" 
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

![WinUI Segmented Control with animation](Selection_Images/winui-segmented-control-animation.gif)



