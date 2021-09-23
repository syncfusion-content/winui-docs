---
layout: post
title: Disable Items with WinUI Segmented Control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Segmented Control(SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Disable in WinUI Segmented Control

The WinUI Segmented control provides options to disable the segmented item.

## Disable Items

You can disable the items using the `SetItemEnabled` Method.

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

using Microsoft.UI.Xaml;
using Syncfusion.UI.Xaml.Editors;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        segmentedControl.SetItemEnabled(0, false);
        segmentedControl.SetItemEnabled(3, false);
    }
}

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

![WinUI Segmented Control with disable](Disable_Images/disable.png)

