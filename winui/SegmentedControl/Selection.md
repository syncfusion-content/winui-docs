---
layout: post
title: Selection using WinUI Segmented Control | Syncfusion
description: Learn here all about selection support in Syncfusion WinUI Segmented Control (SfSegmentedControl), its elements, and more.
platform: WinUI
control: Segmented Control
documentation: ug
---

# Selection in WinUI Segmented Control

This section explains about features that aid in the selection of items, customization of the selected item, and its related operations in the Segmented control.

## Selected index

The Segmented control allows you to select the segment item based on data source index using the [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectedIndex) property.

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
        <syncfusion:SfSegmentedControl x:Name="segmentWithSelectedIndex"
                                    Margin="0,20,0,0"              
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    SelectedIndex="2"
                                    DisplayMemberPath="Name"
                                    ItemsSource="{Binding Days}">
            </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %}

![WinUI Segmented Control with selected index customization](Selection_Images/winui-segmented-control-selected-index-customization.png)

## Selected item customization

The Segmented control allows you to customize the appearance of selected item using the [SelectedSegmentStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectedSegmentStyle) property. You need to provide the style with target type [Border](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.border).

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
                                    DisplayMemberPath="Name"
                                    ItemsSource="{Binding Days}">
        </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %} 

N> Users cannot change the selected item foreground using SelectedSegmentStyle.

![WinUI Segmented Control with selecteditem customization](Selection_Images/winui-segmented-control-selected-item-customization.png)

## Shadow effect

By setting the [SelectedSegmentStyle]((https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectedSegmentStyle)) property on the Segmented control, you can enable a shadow effect for a selected segment item. Set the [HasShadow](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedSegmentBorder.html#Syncfusion_UI_Xaml_Editors_SelectedSegmentBorder_HasShadowProperty) property to true in the style and set it the target type SelectedSegmentBorder. Also, you can enable the appearance of the shadow effect can be customized using the [ShadowColor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SelectedSegmentBorder.html#Syncfusion_UI_Xaml_Editors_SelectedSegmentBorder_ShadowColorProperty) property.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="Shadow_effect.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:Shadow_effect"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d">
    <Grid x:Name="rootGrid">
        <Grid.DataContext>
            <local:SegmentedViewModel/>
        </Grid.DataContext>
        <Grid.Resources>
            <ResourceDictionary>
                <ResourceDictionary.ThemeDictionaries>
                    <ResourceDictionary x:Key="Light">
                        <SolidColorBrush x:Key="SelectedBackground" Color="#00b7c0"/>
                    </ResourceDictionary>
                    <ResourceDictionary x:Key="Dark">
                        <SolidColorBrush x:Key="SelectedBackground" Color="#00b7c0"/>
                    </ResourceDictionary>
                </ResourceDictionary.ThemeDictionaries>
                <Style TargetType="syncfusion:SelectedSegmentBorder" x:Key="shirtModelStyle">
                    <Setter Property="CornerRadius" Value="4"/>
                    <Setter Property="HasShadow" Value="True"/>
                    <Setter Property="ShadowColor" Value="#00b7c0"/>
                    <Setter Property="Background" Value="{ThemeResource SelectedBackground}"/>
                </Style>
            </ResourceDictionary>
        </Grid.Resources>
        <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
            <syncfusion:SfSegmentedControl x:Name="segmentWithShadow"
                                    Height="40"   
                                    SelectedIndex="1"
                                    CornerRadius="4"
                                    BorderThickness="2"
                                    ItemBorderThickness="0"
                                    SelectedSegmentStyle="{StaticResource shirtModelStyle}"
                                    ItemsSource="{Binding ShirtModels}">
                <syncfusion:SfSegmentedControl.Resources>
                    <ResourceDictionary>
                        <ResourceDictionary.ThemeDictionaries>
                            <ResourceDictionary x:Key="Light">
                                <SolidColorBrush x:Key="SyncfusionSegmentedControlBackground" Color="#F2F2F2"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemBackground" Color="#F2F2F2"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedBackground" Color="#00b7c0"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemHoverBackground" Color="#5bdae4"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedHoverBackground" Color="#00b7c0"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemForeground" Color="Black"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemHoverForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedHoverForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedControlBorderBrush" Color="#D9D9D9"/>
                            </ResourceDictionary>
                            <ResourceDictionary x:Key="Dark">
                                <SolidColorBrush x:Key="SyncfusionSegmentedControlBackground" Color="#414141"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemBackground" Color="#414141"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedBackground" Color="#00b7c0"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemHoverBackground" Color="#5bdae4"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedHoverBackground" Color="#00b7c0"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemHoverForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedHoverForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedItemSelectedForeground" Color="White"/>
                                <SolidColorBrush x:Key="SyncfusionSegmentedControlBorderBrush" Color="#5F5E5E"/>
                            </ResourceDictionary>
                        </ResourceDictionary.ThemeDictionaries>
                    </ResourceDictionary>
                </syncfusion:SfSegmentedControl.Resources>
                <syncfusion:SfSegmentedControl.ItemContainerStyle>
                    <Style TargetType="syncfusion:SfSegmentedItem">
                        <Setter Property="Margin" Value="3" />
                        <Setter Property="CornerRadius" Value="4" />
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
        </StackPanel>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %} 


![WinUI Segmented Control with shadow effect](Selection_Images/winui-segmented-control-shadow-effect.png)

## Animation

The Segmented control supports slide animation for selecting the item. Also, users can enable or disable the selection animation using the [SelectionAnimationType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectionAnimationType) property. This property has following two values:

* `Slide` - The slide animation effect is applied while selecting the item. 
* `None` - Disables animation while selecting the item.

N>The default value of  [SelectionAnimationType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectionAnimationType) property property is [Slide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SegmentSelectionAnimationType.html#Syncfusion_UI_Xaml_Editors_SegmentSelectionAnimationType_Slide).

### Slide

When setting  [SelectionAnimationType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectionAnimationType) to [Slide](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SegmentSelectionAnimationType.html#Syncfusion_UI_Xaml_Editors_SegmentSelectionAnimationType_Slide), then the slide animation effect is applied while selecting the item.

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
                                    SelectionAnimationType="Slide"
                                    DisplayMemberPath="Name"
                                    ItemsSource="{Binding Days}">
        </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %} 

![WinUI Segmented Control with slide animation](Selection_Images/winui-segmented-control-slide-animation.gif)

### None

The animation effect can be disabled while selecting the item by setting the [SelectionAnimationType] to [None](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SegmentSelectionAnimationType.html#Syncfusion_UI_Xaml_Editors_SegmentSelectionAnimationType_None).

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
                                    SelectionAnimationType="None"
                                    DisplayMemberPath="Name" 
                                    ItemsSource="{Binding Days}">
        </syncfusion:SfSegmentedControl>
    </Grid>
</Window>

{% endhighlight %}
{% endtabs %} 

![WinUI Segmented Control with animation disabled](Selection_Images/winui-segmented-control-disable-animation.gif)

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
Moves to the previous item on the segmented control's left side. It does not make any selection and only navigates to the previous item. If the focus border is on the first item, pressing <kbd>LeftArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>RightArrow</kbd>
</td>
<td>
Moves to the next item on the segmented control's right side. It does not make any selection and only navigates to the next item. If the focus border is on the last item, pressing <kbd>RightArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>
</td>
<td>
The focus border appears on the selected item when users press the <kbd>Tab</kbd> key. The focus border appears on the first item, if there is no selected item. It will leave the control after pressing the <kbd>Tab</kbd> key with focus. 
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
Pressing the <kbd>Enter</kbd> key when segment item in focus will make selection.
</td>
</tr>
</table>

![WinUI Segmented Control with keyboard behaviors](Selection_Images/winui-segmentedcontrol-keyboard-behaviors.png)

## SelectionChanged event

The [SelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectionChanged) event is triggered, once the selection process has been completed for the selected item in the Segmented Control. The [SegmentSelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SegmentSelectionChangedEventArgs.html) has the following values, which provides information for SelectionChanged event:

* `NewValue`: Gets the new value of [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectedItem) that has been assigned to the SegmentedControl.
* `OldValue`: Gets the old value of [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfSegmentedControl.html#Syncfusion_UI_Xaml_Editors_SfSegmentedControl_SelectedItem) that has been assigned to the SegmentedControl.

{% highlight C# %} 

segmentedControl.SelectionChanged += SegmentedControl_SelectionChanged;

private void SegmentedControl_SelectionChanged(object sender, SegmentSelectionChangedEventArgs e)
{
   var newValue = e.NewValue;
   var oldValue = e.OldValue;         
}

{% endhighlight %}

N> [View sample in GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-segmentedcontrol-examples/tree/main/Samples/Selection-Style)