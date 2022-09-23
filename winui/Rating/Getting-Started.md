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
          Value="2">
         <syncfusion:SfRating.Items>
             <syncfusion:SfRatingItem/>
             <syncfusion:SfRatingItem/>
             <syncfusion:SfRatingItem/>
             <syncfusion:SfRatingItem/>
             <syncfusion:SfRatingItem/>
         </syncfusion:SfRating.Items>
     </syncfusion:SfRating>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

// Creating an instance of the Rating control.
SfRating rating = new SfRating();

//Setting the property value to the Rating control instance.
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Value = 2;
           
{% endhighlight %}
{% endtabs %}

[!Rating control default in WinUI](Rating_images/winui_rating_default.png)

## Rating control using TemplateSelector Property with Images

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
  <DataTemplate x:Key="sadSelectedTemplate">
     <Viewbox>
       <StackPanel Orientation="Vertical">
         <Image Source="/Assets/Rating/SadSelected.png"/>
       </StackPanel>
     </Viewbox>
  </DataTemplate>
  <DataTemplate x:Key="sadUnselectedTemplate">
     <Viewbox>
       <StackPanel Orientation="Vertical">
         <Image Source="/Assets/Rating/SadUnselected.png"/>
       </StackPanel>
     </Viewbox>
  </DataTemplate>
  <local:ImageDataTemplateSelector x:Key="emojiTemplate"
         SadTemplate="{StaticResource sadSelectedTemplate}"                             
         SadUnselectedTemplate="{StaticResource sadUnselectedTemplate}"/>
</ResourceDictionary>
  
<syncfusion:SfRating
     Value="4"
     ItemTemplateSelector="{StaticResource emojiTemplate}">
     <syncfusion:SfRating.Items>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
     </syncfusion:SfRating.Items>
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());

public class ImageDataTemplateSelector : DataTemplateSelector
{
  public DataTemplate SadTemplate { get; set; }
  public DataTemplate SadUnselectedTemplate { get; set; }
        
   protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
  {
    SfRating Rating = container as SfRating; 
    SfRatingItem RatingItem = item as SfRatingItem; 
    if(RatingItem == null)
       return null;
    if(RatingItem.IsSelected) 
       if (Rating.Items.IndexOf(RatingItem)+1 == (Rating.Value)) 
           return SadTemplate; 
    return SadUnselectedTemplate; 
  }
}

{% endhighlight %}
{% endtabs %}

[!Rating control image in WinUI](Rating_images/winui_rating_emoji.png)

## Rating control using TemplateSelector Property with PathShape

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
  <ResourceDictionary.ThemeDictionaries>
    <ResourceDictionary x:Key="Light">
      <SolidColorBrush x:Key="FillColor" Color="#DCDCDC"/>
    </ResourceDictionary>
    <ResourceDictionary x:Key="Dark">
      <SolidColorBrush x:Key="FillColor" Color="#474747"/>
    </ResourceDictionary>
  </ResourceDictionary.ThemeDictionaries>
  <DataTemplate x:Key="selectedTemplate">
    <Viewbox>
      <Path Margin="4" Fill="#F44D57" Data="M16.2551 1.76462L16.2552 1.76479C16.6493 2.16617 16.9623 2.64325 17.1761 3.16901C17.3899 3.69479 17.5 4.25866 17.5 4.82833C17.5 5.39799 17.3899 5.96186 17.1761 6.48764C16.9623 7.0134 16.6493 7.49048 16.2552 7.89187L16.2551 7.89195L15.3424 8.82219L8.99977 15.2861L2.65718 8.82219L1.74439 7.89195C0.94868 7.08101 0.5 5.97917 0.5 4.82833C0.5 3.67748 0.94868 2.57564 1.74439 1.7647C2.53979 0.954092 3.61655 0.500469 4.73725 0.500469C5.85795 0.500469 6.9347 0.954092 7.7301 1.7647L8.64288 2.69495C8.73691 2.79077 8.86552 2.84476 8.99977 2.84476C9.13402 2.84476 9.26263 2.79077 9.35666 2.69495L10.2694 1.7647L10.2695 1.76462C10.6634 1.36307 11.1304 1.04504 11.6438 0.828245C12.1572 0.611455 12.7072 0.5 13.2623 0.5C13.8174 0.5 14.3674 0.611454 14.8807 0.828245C15.3941 1.04504 15.8612 1.36307 16.2551 1.76462Z"/>
    </Viewbox>
  </DataTemplate>
  <DataTemplate x:Key="unselectedTemplate">
    <Viewbox>
      <Path Margin="4" Fill="{ThemeResource FillColor}" Data="M16.612 1.41452C16.1722 0.966073 15.65 0.610337 15.0752 0.367629C14.5005 0.124922 13.8844 0 13.2623 0C12.6401 0 12.0241 0.124922 11.4493 0.367629C10.8746 0.610337 10.3524 0.966073 9.91255 1.41452L8.99977 2.34476L8.08699 1.41452C7.19858 0.509117 5.99364 0.0004693 4.73725 0.000469309C3.48085 0.000469319 2.27591 0.509117 1.38751 1.41452C0.499101 2.31992 9.36088e-09 3.5479 0 4.82833C-9.36088e-09 6.10875 0.499101 7.33674 1.38751 8.24214L2.30029 9.17238L8.99977 16L15.6992 9.17238L16.612 8.24214C17.0521 7.79391 17.4011 7.26171 17.6393 6.67596C17.8774 6.0902 18 5.46237 18 4.82833C18 4.19428 17.8774 3.56645 17.6393 2.9807C17.4011 2.39494 17.0521 1.86275 16.612 1.41452Z"/>
    </Viewbox>
  </DataTemplate>
  <local:PathDataTemplateSelector x:Key="pathTemplate"
      SelectedTemplate="{StaticResource selectedTemplate}"
      UnselectedTemplate="{StaticResource unselectedTemplate}"/>
</ResourceDictionary>

<syncfusion:SfRating
     Value="3"
     ItemTemplateSelector="{StaticResource pathTemplate}">
     <syncfusion:SfRating.Items>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
        <syncfusion:SfRatingItem/>
     </syncfusion:SfRating.Items>
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());
rating.Items.Add(new SfRatingItem());

public class PathDataTemplateSelector : DataTemplateSelector
{
  public DataTemplate SelectedTemplate { get; set; }
  public DataTemplate UnselectedTemplate { get; set; }

   protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
  {
    SfRatingItem RatingItem = item as SfRatingItem;
    if (RatingItem == null)
        return null;
    if (RatingItem.IsSelected)
        return SelectedTemplate;
    return UnselectedTemplate;
  }
}

[!Rating control pathshape in WinUI](Rating_images/winui_rating_path.png)

