---
layout: post
title: Getting Started with WinUI Rating control | Syncfusion
description: Learn all about getting started with the Syncfusion WinUI Rating(SfRating) control, its elements, and more here.
platform: WinUI
control: SfRating
documentation: ug
---

# Getting Started with WinUI Rating

This section explains the steps required to add the Rating control and covers only the basic features needed to get started with Syncfusion SfRating control.

## Creating an application with WinUI Rating control

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Editors` in XAML or C# code.
4. Initialize the SfRating control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Editors"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid>
     <syncfusion:SfRating 
          Value="2"
          Items="{Binding data}">
     </syncfusion:SfRating>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

ObservableCollection<SfRatingItem> data = new ObservableCollection<SfRatingItem>();
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());

// Creating an instance of the Rating control.
SfRating rating = new SfRating();

//Setting the property value to the Rating control instance.
rating.Value = 2;
rating.Items = data; 

{% endhighlight %}
{% endtabs %}

## Rating control using TemplateSelector Property

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
  <DataTemplate x:Key="AngrySelectedTemplate">
     <Viewbox>
       <StackPanel Orientation="Vertical">
         <Image Source="/Assets/Rating/AngrySelected.png"/>
       </StackPanel>
     </Viewbox>
  </DataTemplate>
  <DataTemplate x:Key="AngryUnSelectedTemplate">
     <Viewbox>
       <StackPanel Orientation="Vertical">
         <Image Source="/Assets/Rating/AngryUnselected.png"/>
       </StackPanel>
     </Viewbox>
  </DataTemplate>
  <local:ContentTemplateView x:Key="viewtemplate"
         AngryTemplate="{StaticResource AngrySelectedTemplate}"                             
         AngryUnSelectedTemplate="{StaticResource AngryUnSelectedTemplate}"/>
</ResourceDictionary>
  
<syncfusion:SfRating
         Value="2"
         TemplateSelector="{StaticResource viewtemplate}"
         Items="{Binding data}">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

ObservableCollection<SfRatingItem> data = new ObservableCollection<SfRatingItem>();
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());

public class ImageDataTemplateSelector : DataTemplateSelector
{
  public DataTemplate AngryTemplate { get; set; }
  public DataTemplate AngryUnSelectedTemplate { get; set; }
        
  protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
  {
    if (container == null)
        return null;
    SfRating Rating = container as SfRating;
    SfRatingItem Item = item as SfRatingItem;
    if (Rating.Items.IndexOf(Item) + 1 == Rating.Value)
    {
        if (Rating.Items.IndexOf(Item) == 0)
            return AngryTemplate;
    }
    else
    {
        if (Rating.Items.IndexOf(Item) == 0)
            return AngryUnSelectedTemplate;
    }
    return null;
  } 
}

{% endhighlight %}
{% endtabs %}
