---
layout: post
title: Custom Layout in WinUI Shimmer control | Syncfusion
description: Learn here all about the Custom Layout support in Syncfusion WinUI Shimmer (SfShimmer) control and more.
platform: WinUI
control: Shimmer
documentation: ug
---

# Custom Layout of WinUI Shimmer (SfShimmer)

The `Custom Layout` property of the SfShimmer can be used to create your shimmer view. The below code demonstrates how to customize the shimmer view using the WinUI framework elements by `Custom Layout`.

{% tabs %}
{% highlight xaml %} 

<syncfusion:SfShimmer>
    <syncfusion:SfShimmer.CustomLayout>
        <Grid   ColumnSpacing="15"
                RowSpacing="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>

                <Rectangle  Grid.Row="0"
                            Grid.ColumnSpan="2"
                            RadiusX="3"
                            RadiusY="3"
                            HorizontalAlignment="Left"
                            Height="10"
                            Width="280" />
                
                <Rectangle  Grid.Row="1"
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.ColumnSpan="2"
                            Height="10"
                            HorizontalAlignment="Left"                            
                            Width="260" />
                
                <Rectangle  Grid.Row="2" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.RowSpan="8"/>

                <Rectangle  Grid.Row="2" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="190" />

                <Rectangle  Grid.Row="3" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="190" />

                <Rectangle  Grid.Row="4" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="170" />

                <Rectangle  Grid.Row="5"
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="190" />

                <Rectangle  Grid.Row="6" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="150" />

                <Rectangle  Grid.Row="7" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="160" />

                <Rectangle Grid.Row="8" 
                            RadiusX="3" 
                            RadiusY="3"
                            Grid.Column="1"
                            Height="10"
                            HorizontalAlignment="Left"                           
                            Width="175" />

                <Rectangle  Grid.Row="10" 
                            RadiusX="3" 
                            RadiusY="3"
                            Height="10"
                            HorizontalAlignment="Left"                            
                            Width="160" />

                <Rectangle  Grid.Row="10" 
                            RadiusX="3" 
                            RadiusY="3"
                            Height="30" 
                            Grid.RowSpan="12"
                            HorizontalAlignment="Left"  
                            Grid.Column="1"
                            Width="175" />

                <Rectangle  Grid.Row="11" 
                            RadiusX="3" 
                            RadiusY="3"
                            Height="10"
                            HorizontalAlignment="Left"
                            Width="175" />
        </Grid>
    </syncfusion:SfShimmer.CustomLayout>
</syncfusion:SfShimmer>

{% endhighlight %}
{% highlight C# %} 

SfShimmer sfShimmer = new SfShimmer();
Grid customLayout = new Grid()
{
    ColumnSpacing = 15,
    RowSpacing = 10,
};

for (int i = 0; i < 12; i++)
{
    customLayout.RowDefinitions.Add(new RowDefinition() { Height = GridLength.Auto });
}

customLayout.ColumnDefinitions.Add(new ColumnDefinition() { Width = GridLength.Auto });
customLayout.ColumnDefinitions.Add(new ColumnDefinition() { Width = GridLength.Auto });

Rectangle rectangle1 = new Rectangle()
{               
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 280,
    
};
Grid.SetRow(rectangle1, 0);
Grid.SetColumnSpan(rectangle1, 2);

Rectangle rectangle2 = new Rectangle()
{        
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 260,
};
Grid.SetRow(rectangle2, 1);
Grid.SetColumnSpan(rectangle2, 2);

Rectangle rectangle3 = new Rectangle()
{       
    RadiusX = 3,
    RadiusY = 3,
};
Grid.SetRow(rectangle3, 2);
Grid.SetRowSpan(rectangle3, 8);

Rectangle rectangle4 = new Rectangle()
{       
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 190,
};
Grid.SetRow(rectangle4, 2);
Grid.SetColumn(rectangle4, 1);

Rectangle rectangle5 = new Rectangle()
{      
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 190,
};
Grid.SetRow(rectangle5, 3);
Grid.SetColumn(rectangle5, 1);

Rectangle rectangle6 = new Rectangle()
{     
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 170,
};
Grid.SetRow(rectangle6, 4);
Grid.SetColumn(rectangle6, 1);

Rectangle rectangle7 = new Rectangle()
{      
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 190,
};
Grid.SetRow(rectangle7, 5);
Grid.SetColumn(rectangle7, 1);

Rectangle rectangle8 = new Rectangle()
{      
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 150,
};
Grid.SetRow(rectangle8, 6);
Grid.SetColumn(rectangle8, 1);

Rectangle rectangle9 = new Rectangle()
{     
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 160,
};
Grid.SetRow(rectangle9, 7);
Grid.SetColumn(rectangle9, 1);

Rectangle rectangle10 = new Rectangle()
{    
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 175,
};
Grid.SetRow(rectangle10, 8);
Grid.SetColumn(rectangle10, 1);

Rectangle rectangle11 = new Rectangle()
{     
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 160,
};
Grid.SetRow(rectangle11, 10);

Rectangle rectangle12 = new Rectangle()
{     
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 30,
    Width = 175,
};
Grid.SetRow(rectangle12, 10);
Grid.SetColumn(rectangle12, 1);
Grid.SetRowSpan(rectangle12, 12);

Rectangle rectangle13 = new Rectangle()
{     
    RadiusX = 3,
    RadiusY = 3,
    HorizontalAlignment = HorizontalAlignment.Left,
    Height = 10,
    Width = 175,
};
Grid.SetRow(rectangle13,11);

customLayout.Children.Add(rectangle1);
customLayout.Children.Add(rectangle2);
customLayout.Children.Add(rectangle3);
customLayout.Children.Add(rectangle4);
customLayout.Children.Add(rectangle5);
customLayout.Children.Add(rectangle6);
customLayout.Children.Add(rectangle7);
customLayout.Children.Add(rectangle8);
customLayout.Children.Add(rectangle9);
customLayout.Children.Add(rectangle10);
customLayout.Children.Add(rectangle11);
customLayout.Children.Add(rectangle12);
customLayout.Children.Add(rectangle13);

sfShimmer.CustomLayout = customLayout;

Grid mainGrid = new Grid();
mainGrid.Children.Add(sfShimmer);
this.Content = mainGrid;

{% endhighlight %}
{% endtabs %}

![Shimmer Custom Layout in WinUI](Shimmer_images/winui_shimmer_customlayout.gif)