---
layout: post
title: UI Customization with WinUI Segmented Control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Segmented Control(SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Customization in WinUI Segmented Control

The WinUI Segmented control provides options to customize the background, text color, selection style, and much more.

## BorderThickness of the Segmented Control

You can customize the thickness of the `SfSegmentedControl` using `BorderThickness` key. The default value is 1.

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
                                    BorderThickness="3"
                                    ItemBorderThickness="0"
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

![WinUI Segmented Control with borderthickness](UI_Customization_Images/borderthickness.png)

### ItemBorderThickness 

You can customize the thickness of the `SfSegmentedItem` using `ItemBorderThickness` key. The default value is 0,0,1,0. 

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
                                    BorderThickness="0"
                                    ItemBorderThickness="1"
                                    ItemsSource="{Binding Days}">
            <syncfusion:SfSegmentedControl.ItemContainerStyle>
                <Style TargetType="syncfusion:SfSegmentedItem">
                    <Setter Property="Margin" Value="3" />
                </Style>
            </syncfusion:SfSegmentedControl.ItemContainerStyle>                                            
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

![WinUI Segmented Control with itemborderthickness](UI_Customization_Images/itemborderthickness.png)

## CornerRadius

You can customize the thickness of the Segmented control using `CornerRadius` key. The default value is 0. 

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
                                    CornerRadius="5"
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

![WinUI Segmented Control with cornerradius](UI_Customization_Images/cornerradius.png)

## Border color

You can customize the border color of the segmented control using `SyncfusionSegmentedControlBorderBrush` key.

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
            <syncfusion:SfSegmentedControl.Resources>
                <ResourceDictionary>
                    <ResourceDictionary.ThemeDictionaries>
                        <ResourceDictionary x:Key="Light">
                            <SolidColorBrush x:Key="SyncfusionSegmentedControlBorderBrush" Color="Red"/>
                        </ResourceDictionary>
                        <ResourceDictionary x:Key="Dark">
                            <SolidColorBrush x:Key="SyncfusionSegmentedControlBorderBrush" Color="Red"/>
                        </ResourceDictionary>
                    </ResourceDictionary.ThemeDictionaries>
                </ResourceDictionary>
            </syncfusion:SfSegmentedControl.Resources>                        
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

![WinUI Segmented Control with bordercolor](UI_Customization_Images/bordercolor.png)

## Customization using Keys

You can customize the background, foreground of the segmented item using the below table.

<table>
<tr>
<th>Key</th>
<th>Description</th>
</tr>
<tr>
<td>
SyncfusionSegmentedControlBackground
</td>
<td>
Used to set the background of the segmented control.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemBackground
</td>
<td>
Used to set the background of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemHoverBackground
</td>
<td>
Used to set the hover background of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemSelectedHoverBackground
</td>
<td>
Used to set the selected hover background of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemSelectedBackground
</td>
<td>
Used to set the selected background of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemForeground
</td>
<td>
Used to set the foreground of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemHoverForeground
</td>
<td>
Used to set the hover foreground of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemSelectedHoverForeground
</td>
<td>
Used to set the selected hover foreground of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemSelectedForeground
</td>
<td>
Used to set the selected foreground of the segmented item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedControlBorderBrush
</td>
<td>
Used to set the border color of the segmented control.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemDisabledBackground
</td>
<td>
Used to set the background of the disabled item.
</td>
</tr>
<tr>
<td>
SyncfusionSegmentedItemDisabledForeground
</td>
<td>
Used to set the foreground of the disabled item.
</td>
</tr>
</table>

