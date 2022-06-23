---
layout: post
title: Getting Started with WinUI Shadow control | Syncfusion
description: Learn here all about getting started with Syncfusion WinUI Shadow(SfShadow) control, its elements, and more.
platform: winui-controls
control: SfShadow
documentation: ug
---

# Getting Started with WinUI Shadow

This section explains the steps required to add the WinUI Shadow control and covers only basic features needed to get started with Syncfusion SfShadow control.

## Creating an application with WinUI Shadow

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Add reference to [Syncfusion.Core.WinUI](https://www.nuget.org/packages/Syncfusion.Core.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Core` in XAML or C# code.
4. Initialize the `SfShadow` control.


{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Core"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid>
       <syncfusion:SfShadow>
          <Button Height="50" width="100" Content="Button"         
              CornerRadius="5"/>
       </syncfusion:SfShadow>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

     // Creating an instance of the Shadow control.
     SfShadow shadow = new SfShadow();

     // Setting the SfShadow Content value
     Button button = new Button();
     shadow.Content = button;
     button.Height = 50;
     button.Width = 100;
     button.CornerRadius = 5;
     button.Content = "Button";
     this.Content = shadow;

{% endhighlight %}
{% endtabs %}

![Shadow added to the Button Control](Shadow_images/winui_shadow_button.png)


## Applying Shadow effect for image

If you can apply the shadow effect for any type of image with the help of shadow control.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Image Height="200" Width="250" 
   Source="/Assets/Shadow/Ellipse_Shadow.png/>
</syncfusion:SfShadow>

{% endhighlight %}
{% highlight C# %}

     SfShadow shadow = new SfShadow();

     Image image = new Image();
     shadow.Content = image;
     image.Height = 200;
     image.Width = 250;
     this.Content = shadow;

{% endhighlight %}
{% endtabs %}


![Shadow added to the Image](Shadow_images/winui_shadow_image.png)


## Applying Shadow effect for shape

If you can apply the shadow effect for any type of shapee with the help of shadow control.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfShadow>
    <Path Name="star" Data="M44.5 4L54.0608 33.4114H85L59.9696 51.5886L69.5304 81L44.5 62.8228L19.4696 81L29.0304 51.5886L4 33.4114H34.9392L44.5 4Z" Fill="#FFD700"/>  
</syncfusion:SfShadow>


{% endhighlight %}
{% highlight C# %}

     SfShadow shadow = new SfShadow();

     Path path = new Path();
     shadow.Content = path;
     path.Fill = new SolidColorBrush(Colors.Yellow);
     this.Content = shadow;

{% endhighlight %}
{% endtabs %}

![Shadow added to the Shape](Shadow_images/winui_shadow_star.png)



