---
layout: post
title: Data Label in WinUI Funnel Chart control | Syncfusion
description: Learn here all about data Label feature of Syncfusion WinUI Funnel Chart(SfFunnelChart) and more easily annotated with labels support.
platform: WinUI
control: SfFunnelChart
documentation: ug
---

# Data Label in WinUI Funnel Chart (SfFunnelChart)

Data points can be easily annotated with labels to help improve the readability of data. 

## Define Data Label 

To enable the Label in data label you have to set the [`Visible`]() property of [`FunnelDataLabelSettings`](). 

[`Content`]() property allows you to define the value to be displayed as data label.

The following code example demonstrates about define the value to be displayed as data label.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.DataLabelSettings>
    <chart:FunnelDataLabelSettings Visible="True" Context="YValue" />
</chart:SfFunnelChart.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}
        
SfFunnelChart chart = new SfFunnelChart();
. . . 
chart.DataLabelSettings = new FunnelDataLabelSettings() 
{ 
    Visible = true, 
    Context = LabelContext.YValue 
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

| Content values | Description | Output |
|---|--|---|
| DateTime | Displays LabelContent.DateTime value | ![ DateTime in DataLabel](Data-label_images/WinUI_Funnel_chart_labelcontent_datetime.png) |
|DataLabelItem | Displays the y value|![ LabelContentPath in DataLabel](Data-label_images/WinUI_Funnel_chart_labelcontent_datalabelitem.png)|
| Percentage | Displays the percentage value of series point among other points |![ Percentage in DataLabel](Data-label_images/WinUI_Funnel_chart_labelcontent_percentage.png) |
| XValue | Displays the X value of series point|![ XValue in DataLabel](Data-label_images/WinUI_Funnel_chart_labelcontent_xvalue.png) |
| YValue | Displays the Y value of series point| ![ YValue in DataLabel](Data-label_images/WinUI_Funnel_chart_labelcontent_yvalue.png) |

## Customizing Labels

The following properties are used to customize the data label.

* [`BorderBrush`]()- used to change the border color.
* [`BorderThickness`]()- used to change the thickness of the border.
* [`Margin`]()- used to change the margin size for label.
* [`FontStyle`]()-  used to change font style of the label.
* [`FontSize`]()-  used to change font size of the label.
* [`Foreground`]()- used to change the color of the label.
* [`FontFamily`]()-  used to change the font family of the label.
* [`Background`]()- used to change the label background color.

The following code example demonstrates the customization of label using the above properties:

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart.DataLabelSettings>
    <chart:FunnelDataLabelSettings Visible="True" Foreground="White" FontSize="16" FontFamily="Calibri" BorderBrush="White" BorderThickness="1" Margin="1" FontStyle="Italic" Background="#1E88E5" />
</chart:SfFunnelChart.DataLabelSettings>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
chart.DataLabelSettings = new FunnelDataLabelSettings() 
{ 
    Visible = true, 
    Foreground = new SolidColorBrush(Colors.White),
    BorderBrush = new SolidColorBrush(Colors.White),
    Background = "#1E88E5",
    BorderThickness = new Thickness(1),
    Margin = new Thickness(1),
    FontStyle = FontStyles.Italic,
    FontFamily = new FontFamily("Calibri"),
    FontSize = 16
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Data label content customization support in WinUI Funnel Chart](Data-label_images/WinUI_Funnel_chart_custom_Label.png)

## Label Template

The default appearance of the label can be customized using [`ContentTemplate`]() property as in the below code example:

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="dataLabelTemplate">
        <StackPanel Orientation="Vertical">               
            <Path Grid.Row="0"  Stretch="Uniform" Fill="LightGreen"                              
                       Width="15" Height="15" Margin="0,0,0,0"                              
                       RenderTransformOrigin="0.5,0.5"
                       Data="M22.5,15.8899993896484L37.5,                                
                       30.8899993896484 7.5,30.8899993896484 22.5,15.8899993896484z">
                <Path.RenderTransform>
                    <TransformGroup>
                        <TransformGroup.Children>
                            <RotateTransform Angle="0" />
                            <ScaleTransform ScaleX="1" ScaleY="1" />
                        </TransformGroup.Children>
                    </TransformGroup>
                </Path.RenderTransform>
            </Path>
            <TextBlock Grid.Row="1" Text="{Binding}" FontSize="11" Foreground="White"></TextBlock>
        </StackPanel>
    </DataTemplate>
</Page.Resources>

<Grid>
   <chart:SfFunnelChart x:Name="chart" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

        <chart:SfFunnelChart.DataLabelSettings>
            <chart:FunnelDataLabelSettings Visible="True" ContentTemplate="{StaticResource dataLabelTemplate}" />
        </chart:SfFunnelChart.DataLabelSettings>

    </chart:SfFunnelChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
. . . 
chart.DataLabelSettings = new FunnelDataLabelSettings() 
{ 
    Visible = true, 
    ContentTemplate = this.Resources["dataLabelTemplate"] as DataTemplate
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![LabelTemplate support for datamarkers in WinUI Funnel Chart](Data-label_images/WinUI_Funnel_chart_data_labeltemplate.png)

## Label Format

[`Format`]() property allows you to provide formatting for the labels.

The following code example demonstrates the y value having three decimal digits.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.DataLabelSettings>
        <chart:FunnelDataLabelSettings Visible="True" Format="#$" />
    </chart:SfFunnelChart.DataLabelSettings>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
. . . 
chart.DataLabelSettings = new FunnelDataLabelSettings() 
{ 
    Visible = true, 
    Format = "#$"
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Data label format support in WinUI Funnel Chart](Data-label_images/WinUI_Funnel_chart_data_labelformat.png)

## Label Rotation

[`Rotation`]() property is used to define the angle to which the label has to rotate. The following code demonstrates the label rotating angle.

{% tabs %}

{% highlight xaml %}

<chart:SfFunnelChart x:Name="chart" 
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfFunnelChart.DataLabelSettings>
        <chart:FunnelDataLabelSettings Visible="True" Rotation="45" BorderBrush="White" BorderThickness="1" Background="#1E88E5"/>
    </chart:SfFunnelChart.DataLabelSettings>

</chart:SfFunnelChart>

{% endhighlight %}

{% highlight c# %}

SfFunnelChart chart = new SfFunnelChart();
. . . 
chart.DataLabelSettings = new FunnelDataLabelSettings() 
{ 
    Visible = true, 
    Rotation = 45,
    BorderBrush = new SolidColorBrush(Colors.White),
    Background = "#1E88E5",
    BorderThickness = new Thickness(1)
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Data label rotation support in WinUI Funnel Chart](Data-label_images/WinUI_Funnel_chart_data_label_rotation.png)
