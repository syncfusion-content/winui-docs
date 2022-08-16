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
          Value="3"
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
rating.Value = 3;
rating.Items = data; 

{% endhighlight %}
{% endtabs %}

![Rating control Default in WinUI](Rating_images/winui_rating_overview.png)

## Rating control using TemplateSelector Property

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
  <DataTemplate x:Key="selectedTemplate">
    <Viewbox>
      <StackPanel Orientation="Vertical">
        <Image Source="{Binding SelectedTemplate}"/>
      </StackPanel>
    </Viewbox>
  </DataTemplate>
  <DataTemplate x:Key="unSelectedTemplate">
    <Viewbox>
      <StackPanel Orientation="Vertical">
        <Image Source="{Binding UnSelectedTemplate}"/>
      </StackPanel>
    </Viewbox>
   </DataTemplate>
   <local:ContentTemplate x:Key="template"
         SelectedTemplate="{StaticResource selectedTemplate}"
         ChildTemplate="{StaticResource unSelectedTemplate}"/> 
</ResourceDictionary>

<syncfusion:SfRating
         Value="3"
         TemplateSelector="{StaticResource template}"
         Items="{Binding data}">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

public class RatingViewModel
{
   public RatingViewModel()
   {
      data = new ObservableCollection<SfRatingItem>();
      data.Add(new RatingModel() {  UnSelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/AngryUnSelected.png")), SelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/AngrySelected.png")) });
      data.Add(new RatingModel() { UnSelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/UnhappyUnSelected.png")), SelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/UnhappySelected.png")) });
      data.Add(new RatingModel() { UnSelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/NeutralUnSelected.png")), SelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/NeutralSelected.png")) });
      data.Add(new RatingModel() {  UnSelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/HappyUnSelected.png")), SelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/HappySelected.png")) });
      data.Add(new RatingModel() { UnSelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/ExcitedUnSelected.png")), SelectedTemplate = new BitmapImage(new Uri("ms-appx:///Assets/Rating/ExcitedSelected.png")) });
   }
   public ObservableCollection<SfRatingItem> data
   {
      get; set;
   }
}
public class RatingModel : INotifyPropertyChanged
{
    private BitmapImage unSelectedTemplate;
    public BitmapImage UnSelectedTemplate
    {
      get { return unSelectedTemplate; }
      set
      {
         unSelectedTemplate = value; OnPropertyChanged("UnSelectedTemplate");
      }
    }
 
    private BitmapImage selectedTemplate;
    public BitmapImage SelectedTemplate
    {
      get { return selectedTemplate; }
      set
      {
         selectedTemplate = value; OnPropertyChanged("SelectedTemplate");
      }
    }
    private void OnPropertyChanged(String parameter)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(parameter));
    }

    public event PropertyChangedEventHandler PropertyChanged;
}
public class ContentTemplate : DataTemplateSelector
{
    public DataTemplate SelectedTemplate { get; set; }
    public DataTemplate ChildTemplate { get; set; }
    protected override DataTemplate SelectTemplateCore(object item, DependencyObject container)
    {
       if (container == null)
           return null;
       SfRating Rating = container as SfRating;
       if (Rating.Items.IndexOf(item) + 1 <= Rating.Value)
           return SelectedTemplate;
       return ChildTemplate;
    }
}

{% endhighlight %}
{% endtabs %}

![Rating control Customview in WinUI](Rating_images/winui_rating_customview.png)