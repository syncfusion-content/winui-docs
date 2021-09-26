---
layout: post
title: Selection with WinUI Segmented Control | Syncfusion
description: Learn here all about selection support in Syncfusion WinUI Segmented Control(SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Selection in WinUI Segmented Control

This section explains how to customize the selected item and its related operations in the Segmented control.

## Selected item customization

The Segmented control allows you to customize the appearance of SelectedItem using the `SelectedSegmentStyle` property. we need to provide style of target type as [Border](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.border).

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
{% endtabs %} 

![WinUI Segmented Control with selecteditem customization](Selection_Images/winui-segmented-control-selected-item-customization.png)

N> Users can't change the selected item foreground using SelectedSegmentStyle.

## Animation

The Segmented control supports slide animation for selecting the item. Also users can enable or disable the selection animation using `SelectionAnimationType` property. The default value is `Slide`. This property has following two values:

* `Slide` - The slide animation effect applied while selecting the item. 
* `None` - Disables animation while selecting the item.

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
{% endtabs %} 

![WinUI Segmented Control with animation](Selection_Images/winui-segmented-control-animation.gif)

## Keyboard behaviors

<table>
<tr>
<th>
Key or KeyCombinations
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
<kbd>LeftArrow</kbd>
</td>
<td>
Moves to the previous item on the segmented control's left side. It doesn't make any selection and only navigates to the previous item. If the focus border is on the first item, pressing <kbd>LeftArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>RightArrow</kbd>
</td>
<td>
Moves to the next item on the segmented control's right side. It doesn't make any selection and only navigates to the next item. If the focus border is on the last item, pressing <kbd>RightArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>
</td>
<td>
The focus border appears on the selected item when users press the <kbd>Tab</kbd> key. The focus border appears on the first item if there is no selected item. It will leave the control after pressing the <kbd>Tab</kbd> key with focus. 
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
Pressing the <kbd>Enter</kbd> key after moving to the next or previous item makes a selection.
</td>
</tr>
</table>

![WinUI Segmented Control with keyboard behaviors](Selection_Images/winui-segmentedcontrol-keyboard-behaviors.png)

## SelectionChanged event

The SelectionChanged event will occur once selection process has been completed for the selected item in the Segmented Control. The    `SegmentSelectionChangedEventArgs` has the following values which provides information for SelectionChanged event:

* NewValue: Gets the new value of `SelectedItem` has been assigned to the SegmentedControl.
* OldValue: Gets the old value of `SelectedItem` has been assigned to the SegmentedControl.

{% highlight C# %} 

segmentedControl.SelectionChanged += SegmentedControl_SelectionChanged;

private void SegmentedControl_SelectionChanged(object sender, SegmentSelectionChangedEventArgs e)
{
   var newValue = e.NewValue;
   var oldValue = e.OldValue;         
}

{% endhighlight %}





