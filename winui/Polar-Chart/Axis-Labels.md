---
layout: post
title: Axis labels in WinUI Chart control | Syncfusion
description: Learn here all about the chart axis lables and its customization in Syncfusion WinUI Chart (SfPolarChart) control.
platform: WinUI
control: SfPolarChart
documentation: ug
---

# Axis labels in WinUI Chart

Axis labels are used to show the units or measures or category values of axis to visualize the data. It will be generated based on the range and values binded to the series in the chart. 

## Custom Axis Labels

Chart axis allows user to define the own axis labels. The [Content](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Content) and [Position](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Position) property of [ChartAxisLabel](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html) used to define the labels for axis using the [CustomLabels](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_CustomLabels) property.

N> Also, directly bind the collection of labels to the [LabelSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelSource) property for defining custom labels.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
                
    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis >
            <chart:CategoryAxis.CustomLabels>
                <chart:ChartAxisLabel Position="0" Content="North(0°)"/>
                <chart:ChartAxisLabel Position="1" Content="NorthEast(45°)"/>
                <chart:ChartAxisLabel Position="2" Content="East(90°)"/>
                <chart:ChartAxisLabel Position="3" Content="SouthEast(135°)"/>
                <chart:ChartAxisLabel Position="4" Content="South(180°)"/>
                <chart:ChartAxisLabel Position="5" Content="SouthWest(225°)"/>
                <chart:ChartAxisLabel Position="6" Content="West(270°)"/>
                <chart:ChartAxisLabel Position="7" Content="NorthWest(315°)"/>
            </chart:CategoryAxis.CustomLabels>
        </chart:CategoryAxis>
    </chart:SfPolarChart.PrimaryAxis>
                    
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

CategoryAxis axis = new CategoryAxis();

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 0, Content = "North(0°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 1, Content = "NorthEast(45°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 2, Content = "East(90°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 3, Content = "SouthEast(135°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 4, Content = "South(180°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 5, Content = "SouthWest(225°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 6, Content = "West(270°)" });
axis.CustomLabels.Add(new ChartAxisLabel() { Position = 7, Content = "NorthWest(315°)" });

chart.PrimaryAxis = axis;

chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![Custom axis labels in WinUI Chart](Axis_Images/WinUI_Chart_CustomLabels.png)

The following code sample demonstrates how to bind the collection of labels to the [LabelSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelSource).

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
        
    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis LabelSource="{Binding Labels}" ContentPath="Content"/>
    </chart:SfPolarChart.PrimaryAxis>
        
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight C# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new CategoryAxis()
{
    ContentPath = "Content",
    PositionPath = "Position",
    LabelsSource = viewModel.Labels,
};

...

public List<LabelItem> Labels { get; set; }

Labels = new List<LabelItem>
{
    new LabelItem() {Position=0, Content = "North(0°)"},
    new LabelItem() {Position=1, Content = "NorthEast(45°)"},
    new LabelItem() {Position=2, Content = "East(90°)" },
    new LabelItem() {Position=3, Content = "SouthEast(135°)"},
    new LabelItem() {Position=4, Content = "South(180°)"},
    new LabelItem() {Position=5, Content = "SouthWest(225°)"},
    new LabelItem() {Position=6, Content = "West(270°)"},
    new LabelItem() {Position=7, Content = "NorthWest(315°)"},
};

public class LabelItem
{
    public string Content { get; set; }
    public int Position { get; set; }
}

{% endhighlight %}

{% endtabs %}

## Rotation

The [LabelRotationAngle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotationAngle) property is used to define the angle for the label content.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
    ...
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis LabelRotationAngle="30"/>
    </chart:SfPolarChart.SecondaryAxis>
    ...
</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();
...
chart.PrimaryAxis = new CategoryAxis();
chart.SecondaryAxis = new NumericalAxis()
{
    LabelRotationAngle = 30,
}
...

{% endhighlight %}

{% endtabs %}

![Chart axis label rotation angle support in WinUI chart](Axis_Images/WinUI_Chart_LabelRotationAngle.png)

## Format

Axis labels can be formatted by predefined formatting types by using the [LabelFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelFormat) property based on the axis types.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>
            
    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis/>
    </chart:SfPolarChart.PrimaryAxis>
                
    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis LabelFormat="0.0"/>
    </chart:SfPolarChart.SecondaryAxis>
    ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new CategoryAxis();

chart.SecondaryAxis = new NumericalAxis()
{
    LabelFormat = "0.0",
};
...

{% endhighlight %}

{% endtabs %}

![Axis label formart support in WinUI Chart](Axis_Images/WinUI_Chart_Numerical_LabelFormat.png)

## Template

The appearance of the axis labels can be customized by using the [LabelTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property of axis.

{% tabs %}

{% highlight xaml %}

<chart:SfPolarChart>

    <chart:SfPolarChart.Resources>
        <DataTemplate x:Key="labelTemplate">
            <Border Background="Blue" CornerRadius="5" BorderThickness="1">
                <TextBlock Text="{Binding Content}" Foreground="White" FontStyle="Italic" FontSize="10" FontWeight="Bold" Margin="3"/>
            </Border>
        </DataTemplate>
    </chart:SfPolarChart.Resources>

    <chart:SfPolarChart.PrimaryAxis>
        <chart:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>
    </chart:SfPolarChart.PrimaryAxis>

    <chart:SfPolarChart.SecondaryAxis>
        <chart:NumericalAxis/>
    </chart:SfPolarChart.SecondaryAxis>
    ...

</chart:SfPolarChart>

{% endhighlight %}

{% highlight c# %}

SfPolarChart chart = new SfPolarChart();

chart.PrimaryAxis = new CategoryAxis()
{
    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate
};

chart.SecondaryAxis = new NumericalAxis();
...

{% endhighlight %}

{% endtabs %}

![LabelTemplate support for ChartAxis in WinUI Chart](Axis_Images/WinUI_Chart_AxisLabelTemplate.png)

