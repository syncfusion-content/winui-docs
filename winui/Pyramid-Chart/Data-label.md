---
layout: post
title: Data labels in WinUI Pyramid Chart control | Syncfusion
description: This section explains about how to add and customize the data labels in Syncfusion WinUI Pyramid Chart(SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Data label in WinUI Pyramid Chart (SfPyramidChart)

To improve the readability of data in the pyramid chart, data points can be easily annotated with data labels.

## Define data label 

To define the data label in the chart, set the [ShowDataLabels]() property to true. The default value of [ShowDataLabels]() property is false.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">
. . .
 </chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
chart.Palette = ChartColorPalette.BlueChrome;
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
. . . 
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Data label support in WinUI Pyramid chart](Data-label_images/WinUI_pyramid_chart_data_label.png)

## Data label context customization

The [ShowDataLabels]() property of pyramid chart is used to enable the data label, and the [Context]() property specifies, which value should be displayed in the data label in [PyramidDataLabelSettings]().

The following code example demonstrates how to define the data label and its value.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">
. . .
    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Context="YValue" />
    </chart:SfPyramidChart.DataLabelSettings>
. . .
 </chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}
        
SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
. . . 
chart.DataLabelSettings = new PyramidDataLabelSettings() 
{ 
    Context = LabelContext.YValue 
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

| Context values | Description | Output |
|---|--|---|
| DateTime | Displays LabelContent.DateTime value | ![ DateTime in DataLabel](Data-label_images/WinUI_pyramid_chart_labelcontent_datetime.png) |
|DataLabelItem | Displays the y value|![ LabelContentPath in DataLabel](Data-label_images/WinUI_pyramid_chart_labelcontent_datalabelitem.png)|
| Percentage | Displays the percentage value of series point among other points |![ Percentage in DataLabel](Data-label_images/WinUI_pyramid_chart_labelcontent_percentage.png) |
| XValue | Displays the X value of series point|![ XValue in DataLabel](Data-label_images/WinUI_pyramid_chart_labelcontent_xvalue.png) |
| YValue | Displays the Y value of series point| ![ YValue in DataLabel](Data-label_images/WinUI_pyramid_chart_labelcontent_yvalue.png) |

## Data label customization

The following properties are used to customize the data label:

* [`BorderBrush`]()- used to change the border color.
* [`BorderThickness`]()- used to change the thickness of the border.
* [`Margin`]()- used to change the margin of the label.
* [`FontStyle`]()-  used to change font style of the label.
* [`FontSize`]()-  used to change font size of the label.
* [`Foreground`]()- used to change the text color of the label.
* [`FontFamily`]()-  used to change the font family of the label.
* [`Background`]()- used to change the label background color.

The following code example demonstrates the customization of data label using the above properties:

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">
. . .
    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Foreground="White" FontSize="16" FontFamily="Calibri" BorderBrush="White" BorderThickness="1" Margin="1" FontStyle="Italic" Background="#1E88E5" />
    </chart:SfPyramidChart.DataLabelSettings>
. . .
</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
. . .
chart.DataLabelSettings = new PyramidDataLabelSettings() 
{ 
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

![Data label customization support in WinUI Pyramid Chart](Data-label_images/WinUI_pyramid_chart_custom_label.png)

## Data label template

The appearance of the data label can be customized by using the [ContentTemplate]() property of [`PyramidDataLabelSettings`]() as follows.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <DataTemplate x:Key="dataLabelTemplate">
        <StackPanel Orientation="Vertical">
            <Path Grid.Row="0"  Stretch="Uniform" Fill="LightGreen" Width="15" Height="15" Margin="0,0,0,0" RenderTransformOrigin="0.5,0.5" Data="M11.771002,1.993L5.0080013,14.284 10.752002,14.284 6.6450019,22.804 17.900003,11.921 11.655003,11.921 18.472004,1.993z M10.593002,0L22.256004,0 15.440003,9.9280005 22.827004,9.9280005 0,32 7.5790019,16.277 1.637001,16.277z">
                    <Path.RenderTransform>
                        <TransformGroup>
                            <TransformGroup.Children>
                                <RotateTransform Angle="0" />
                                <ScaleTransform ScaleX="1" ScaleY="1" />
                            </TransformGroup.Children>
                        </TransformGroup>
                    </Path.RenderTransform>
                </Path>
            <TextBlock Grid.Row="1" Text="{Binding}" FontSize="12" Foreground="White"></TextBlock>
        </StackPanel>
    </DataTemplate>
</Page.Resources>
<Grid>
   <chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

        <chart:SfPyramidChart.DataLabelSettings>
            <chart:PyramidDataLabelSettings ContentTemplate="{StaticResource dataLabelTemplate}" />
        </chart:SfPyramidChart.DataLabelSettings>

    </chart:SfPyramidChart>
</Grid>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
. . . 
chart.DataLabelSettings = new PyramidDataLabelSettings() 
{ 
    ContentTemplate = this.Resources["dataLabelTemplate"] as DataTemplate
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Template support for data label in WinUI Pyramid Chart](Data-label_images/WinUI_pyramid_chart_data_labeltemplate.png)

## Label format

The [Format]() property is used to format the data labels. The following code example demonstrates how to format data labels with three decimal digits.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Format="#.000" Foreground="White" />
    </chart:SfPyramidChart.DataLabelSettings>

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
. . . 
chart.DataLabelSettings = new PyramidDataLabelSettings() 
{  
    Format = "#.000",
    Foreground = new SolidColorBrush(Colors.White)
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Label format support for data label in WinUI Pyramid Chart](Data-label_images/WinUI_pyramid_chart_data_labelformat.png)

## Label rotation

The [`Rotation`]() property is used to rotate the data labels based on the value as angle.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                ShowDataLabels="True"
                Palette="BlueChrome" 
                ItemsSource="{Binding Data}" 
                XBindingPath="Category"
                YBindingPath="Value">

    <chart:SfPyramidChart.DataLabelSettings>
        <chart:PyramidDataLabelSettings Rotation="45" BorderBrush="White" BorderThickness="1" Background="#1E88E5"/>
    </chart:SfPyramidChart.DataLabelSettings>

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.ShowDataLabels = true;
. . . 
chart.DataLabelSettings = new PyramidDataLabelSettings() 
{ 
    Rotation = 45,
    BorderBrush = new SolidColorBrush(Colors.White),
    Background = "#1E88E5",
    BorderThickness = new Thickness(1)
};

this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Rotation support for data label in WinUI Pyramid Chart](Data-label_images/WinUI_pyramid_chart_data_label_rotation.png)

