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
          Value="5"
          Precision="Standard"
          ItemSize="80"
          Items="{Binding list}"
          ItemsSpacing="5">
     </syncfusion:SfRating>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

ObservableCollection<object> data = new ObservableCollection<object>();
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());
data.Add(new SfRatingItem());

// Creating an instance of the Rating control.
SfRating rating = new SfRating();

rating.Value = 5;
rating.Precision = Precision.Standard;
rating.ItemSize = 80;
rating.Items = data; 
rating.ItemsSpacing = 5;

{% endhighlight %}
{% endtabs %}

## Rating Control using the itemscount property

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
          Value="5"
          Precision="Half"
          ItemSize="80"
          ItemsCount="5"
          ItemsSpacing="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 5;
rating.Precision = Precision.Half;
rating.ItemSize = 80;
rating.Items = 5;
rating.ItemsSpacing = 5;

{% endhighlight %}
{% endtabs %}