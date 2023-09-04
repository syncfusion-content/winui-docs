---
layout: post
title: About WinUI Shimmer control | Syncfusion
description: Learn here all about the Custom Layout support in Syncfusion WinUI Shimmer (SfShimmer) control and more.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Custom Layout of WinUI Shimmer (SfShimmer)

The `Custom Layout` property of the SfShimmer can be used to create your shimmer view. The below code demonstrates how to customize the shimmer view using the WinUI framework elements by `Custom Layout`.

{% tabs %}
{% highlight xaml %} 

    <syncfusion:SfShimmer>
        <syncfusion:SfShimmer.CustomLayout>
            <Grid Height="640" Width="640" Background="White">
                <Grid.RowDefinitions>
                    <RowDefinition Height="400"/>
                    <RowDefinition Height="50"/>
                    <RowDefinition Height="50"/>
                    <RowDefinition Height="50"/>
                    <RowDefinition Height="100"/>
                </Grid.RowDefinitions>
                <Rectangle Fill="LightGray" Grid.Row="0" Margin="40,40,20,40" RadiusX="7" RadiusY="7"/>
                <Rectangle Fill="LightGray" Grid.Row="1" Margin="40,0,100,20" RadiusX="7" RadiusY="7"/>
                <Rectangle Fill="LightGray" Grid.Row="2" Margin="40,0,100,20" RadiusX="7" RadiusY="7"/>
                <Rectangle Fill="LightGray" Grid.Row="3" Margin="40,0,300,20" RadiusX="7" RadiusY="7"/>
            </Grid>
        </syncfusion:SfShimmer.CustomLayout>
    </syncfusion:SfShimmer>

{% endhighlight %}
{% highlight C# %} 

    SfShimmer sfShimmer = new SfShimmer();
    Grid customLayout = new Grid
    {
        Height = 640, 
        Width = 640, 
        Background = new SolidColorBrush(Colors.White)
    };         
    for (int i = 0; i < 4; i++)
    {
        customLayout.RowDefinitions.Add(new RowDefinition
        {
            Height = new GridLength(i == 0 ? 400 : 50)
        });
    }
    for (int i = 0; i < 4; i++)
    {
        Rectangle rectangle = new Rectangle
        {
            Fill = new SolidColorBrush(Colors.LightGray),
            Margin = i switch
            {
                0 => new Thickness(40, 40, 20, 40),
                1 => new Thickness(40, 0, 100, 20),
                2 => new Thickness(40, 0, 100, 20),
                3 => new Thickness(40, 0, 300, 20),
                _ => new Thickness()
            },
            RadiusX = 7,
            RadiusY = 7
        };
        Grid.SetRow(rectangle, i);
        customLayout.Children.Add(rectangle);
    }
    sfShimmer.CustomLayout = customLayout;
    Grid mainGrid = new Grid();
    mainGrid.Children.Add(sfShimmer);
    this.Content = mainGrid;

{% endhighlight %}
{% endtabs %}

![Shimmer Custom Layout in WinUI](SfShimmer_images/CustomLayout_images/winui_shimmer_customlayout.gif)