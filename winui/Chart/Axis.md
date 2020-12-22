---
layout: post
title: Axis| SfChart | WinUI | Syncfusion 
description: Explains the parts of axis, types of axis, it's behavior and customization options in WinUI Chart (SfChart)
platform: WinUI
control: SfChart
documentation: ug
---


# Axis in WinUI Chart (SfChart)

[`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#) is used to locate a data point inside the chart area. Charts typically have two axes that are used to measure and categorize data: a vertical (Y) axis, and a horizontal (X) axis.

Vertical(Y) axis always uses numerical scale. Horizontal(X) axis supports the following types of scale:

* Category
* Numeric
* Date time

The following are the API’s in ChartAxis

* [`ArrangeRect`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ArrangeRect) – Represents the bounds of chart axis size. 
* [`VisibleRange`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_VisibleRange) – Represent the axis start and end values.
* [`VisibleLabels`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_VisibleLabels) – Represents the axis label collection which are visible in axis.

The following topics explains in detail about the axis and its parts

## Header

In [`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#) you can define any object as header using [`Header`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_Header) property. The following code example demonstrates the defining header in primary and secondary axis. 

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Metals"/>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Header="Values(In Tonnes)"/>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis() { Header = "Medals" };

chart.SecondaryAxis = new NumericalAxis() { Header = "Values(In Tonnes)" };

{% endhighlight %}

{% endtabs %}

![Header support for ChartAxis in WinUI](Axis_images/Axis_img1.jpeg)


**Header** **Customization**

Default appearance of the header can be customized using [`HeaderTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderTemplate) property. The following code snippet demonstrates the header customization.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="headerTemplate1">

            <Border BorderBrush="Black" CornerRadius="5" BorderThickness="1">

                    <TextBlock Text="Demands" FontSize="12" 
                                   
                               FontStyle="Italic" 
                                   
                               FontWeight="Bold" Margin="3"/>

            </Border>

        </DataTemplate>

        <DataTemplate x:Key="headerTemplate2">

            <Border BorderBrush="Black" CornerRadius="5" BorderThickness="1">

                    <TextBlock FontSize="12" Margin="3"
                                   
                               FontStyle="Italic" FontWeight="Bold"/>

            </Border>

        </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

        <syncfusion:CategoryAxis HeaderTemplate="{StaticResource headerTemplate1}"/>

    </syncfusion:SfChart.PrimaryAxis>

    <syncfusion:SfChart.SecondaryAxis>

        <syncfusion:NumericalAxis Header="Values(In Tonnes)"
                                          
                                  HeaderTemplate="{StaticResource headerTemplate2}"/>

    </syncfusion:SfChart.SecondaryAxis>
        
</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    HeaderTemplate = chart.Resources["headerTemplate1"] as DataTemplate

};

chart.SecondaryAxis = new NumericalAxis()
{

    HeaderTemplate = chart.Resources["headerTemplate2"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![Header customization for ChartAxis in WinUI](Axis_images/Axis_img2.jpeg)


**HeaderStyle**

[`HeaderStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_HeaderStyle) property is used to provide style for the axis header. The following code example explains header style customization.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Metals" >

<syncfusion:CategoryAxis.HeaderStyle>

<syncfusion:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Black"> 

</syncfusion:LabelStyle>

</syncfusion:CategoryAxis.HeaderStyle>

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Header="Values(In Tonnes)"/>

<syncfusion:NumericalAxis.HeaderStyle>

<syncfusion:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Black"> 

</syncfusion:LabelStyle>

</syncfusion:NumericalAxis.HeaderStyle>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

LabelStyle style = new LabelStyle()
{

    FontFamily = new FontFamily("Algerian"),

    FontSize = 13,

    Foreground = new SolidColorBrush(Colors.Black)

};

chart.PrimaryAxis = new CategoryAxis()
{

    Header = "Medals",

    LabelStyle = style

};

chart.SecondaryAxis = new NumericalAxis()
{

    Header = "Values(In Tonnes)",

    LabelStyle = style

};

{% endhighlight %}

{% endtabs %}

![HeaderStyle for header support in WinUI](Axis_images/Axis_img3.jpeg)

## Axis Labels

Labels will be generated by the range and the values binded to [`XBindingPath`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_XBindingPath) or [`YBindingPath`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.XyDataSeries.html#Syncfusion_UI_Xaml_Charts_XyDataSeries_YBindingPath) properties.



**Positioning** **the** **Labels**

The [`LabelPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelPosition) property is used to position the axis label either inside or outside the chart plotting area. By default, LabelPosition is [`Outside`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AxisElementPosition.html).

**Inside**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  LabelPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    LabelPosition = AxisElementPosition.Inside

};

{% endhighlight %}

{% endtabs %}

![Positioning axis labels support in WinUI](Axis_images/Axis_img4.jpeg)


**LabelRotationAngle**

[`LabelRotationAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotationAngle) property allows you to define the angle for the label content. The following code example illustrates the [`LabelRotationAngle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelRotationAngle).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelRotationAngle="90" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

     LabelRotationAngle = 90

};

{% endhighlight %}

{% endtabs %}

![Axis Rotation angle support in WinUI Chart](Axis_images/Axis_img5.jpeg)

**Custom** **Labels**

SfChart allows user to define the labels for the axis. For defining the axis label you have to set the [`Content`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Content) and [`Position`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Position) property .You can define the labels using [`CustomLabels`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_CustomLabels) property as in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis >

<syncfusion:CategoryAxis.CustomLabels>

<syncfusion:ChartAxisLabel Position="0" Content="0-1"/>

<syncfusion:ChartAxisLabel Position="1" Content="1-2"/>

<syncfusion:ChartAxisLabel Position="2" Content="2-3"/>

<syncfusion:ChartAxisLabel Position="3" Content="3-4"/>

<syncfusion:ChartAxisLabel Position="4" Content="4-5"/>

<syncfusion:ChartAxisLabel Position="5" Content="5-5"/>

</syncfusion:CategoryAxis.CustomLabels>

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

CategoryAxis axis = new CategoryAxis();

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 0, Content = "0-1" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 1, Content = "1-2" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 2, Content = "2-3" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 3, Content = "3-4" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 4, Content = "4-5" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 5, Content = "5-5" });

chart.PrimaryAxis = axis;

{% endhighlight %}

{% endtabs %}

![Axis label customization support in WinUI](Axis_images/Axis_img6.jpeg)


You can also directly bind the collection of labels to the [`LabelSource`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelSource) property for defining custom labels. The following code example demonstrates the defining the label collection in code behind and binding the property in XAML page.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelSource="{Binding Labels}" ContentPath="Content" PositionPath="Position">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight C# %}

chart.PrimaryAxis = new CategoryAxis()
{

    ContentPath ="Content",

    PositionPath = "Position",

    LabelSource = Labels

};


public List<LabelItem> Labels { get; set; }

Labels = new List<LabelItem>
{

    new LabelItem() {Position=0, Content = "0-1"},

    new LabelItem() {Position=1, Content = "1-2"},

    new LabelItem() {Position=2, Content = "2-3"},

    new LabelItem() {Position=3, Content = "3-4"},

    new LabelItem() {Position=4, Content = "4-5"},

    new LabelItem() {Position=5, Content = "5-6"},

    new LabelItem() {Position=6, Content = "6-7"},

    new LabelItem() {Position=7, Content = "7-8"},

};

public class LabelItem
{

    public string Content { get; set; }

    public int Position { get; set; }

}

{% endhighlight %}

{% endtabs %}

![Axis label customization support in WinUI](Axis_images/Axis_img7.jpeg)


**Label** **Formatting**

Axis labels can be formatting by predefined formatting types based on the axis types.

**DateTimeAxis**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis LabelFormat="MMM/dd" FontSize="12" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelFormat = "MM/dd",

    FontSize = 12

};

{% endhighlight %}

{% endtabs %}

![Axis labels formatting support in WinUI Chart](Axis_images/Axis_img8.jpeg)

**NumericalAxis**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis LabelFormat="0.00" />

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    LabelFormat = "0.00",

};

{% endhighlight %}

{% endtabs %}

![Axis labels formatting support in WinUI Chart](Axis_images/Axis_img10.jpeg)

**LabelTemplate**

[`LabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property allows you to define the appearance for the axis labels .the following code example illustrates the [`LabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelTemplate) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="labelTemplate">

            <Border Background="Gray" CornerRadius="5" >

                    <TextBlock Text="{Binding Content}" Foreground="White"
                                   
                                FontStyle="Normal" FontSize="10" 
                                   
                                FontWeight="Bold" Margin="3"/>

                    <Border.Effect>

                        <DropShadowEffect ShadowDepth="6" Direction="315"
                                              
                                          Color="LightGray" Opacity="0.25"
                                              
                                          BlurRadius="0.8" />

                    </Border.Effect>

            </Border>

       </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

        <syncfusion:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>

    </syncfusion:SfChart.PrimaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![LabelTemplate support for ChartAxis in WinUI](Axis_images/Axis_img13.jpeg)


**LabelExtent**

This property allows us to set the distance between the axis header and the axis using [`LabelExtent`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelExtent) property.The following code snippet defines the [`LabelExtent`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelExtent) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Demand" LabelExtent="50" >

</syncfusion:CategoryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Header = "Demand",

    LabelExtent = 50

};

{% endhighlight %}

{% endtabs %}

![LabelExtent support for ChartAxis in WinUI](Axis_images/Axis_img14.jpeg)


**Smart** **Axis** **Labels**

When there are more number of axis labels, they may overlap with each other. SfChart provides support to handle the overlapping labels using the [`LabelIntersectAction`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) property. By default the [`LabelIntersectAction`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) value is [`Hide`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AxisLabelIntersectAction.html).

The following are the options for intersecting action.

* None
* Hide
* MultipleRows
* Rotate

**None**

None option is used to display all the label even if it intersects. The following code snippet demonstrates the LabelIntersectAction as None option.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelIntersectAction="None"/>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelIntersectAction = AxisLabelIntersectAction.None

};

{% endhighlight %}

{% endtabs %}

![Smart axis labels support in WinUI Chart](Axis_images/Axis_img15.jpeg)


**Hide**

Hide option is used to hide the labels if it intersects .You can define the hide as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelIntersectAction="Hide"/>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelIntersectAction = AxisLabelIntersectAction.Hide

};

{% endhighlight %}

{% endtabs %}

![Smart axis labels support in WinUI Chart](Axis_images/Axis_img16.jpeg)


**MultipleRows**

This option is used to move the labels to next row if it intersects .The following code demonstrates the MultipleRows option in [`LabelIntersectAction`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelIntersectAction="MultipleRows">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelIntersectAction = AxisLabelIntersectAction.MultipleRows

};

{% endhighlight %}

{% endtabs %}

![Smart axis labels support in WinUI Chart](Axis_images/Axis_img17.jpeg)


**Auto**

This option in [`LabelIntersectAction`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) property is used to rotate the labels if it intersects .The following code snippet and image demonstrates the rotate option in [`LabelIntersectAction`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_LabelIntersectAction) property.

{% tabs %}

{% highlight xml %}

<syncfusion:CategoryAxis LabelIntersectAction="Auto">

</syncfusion:CategoryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelIntersectAction = AxisLabelIntersectAction.Auto

};

{% endhighlight %}

{% endtabs %}

![Smart axis labels support in WinUI Chart](Axis_images/Axis_img18.jpeg)


**EdgeLabelsDrawingMode**

SfChart provides support to customize the position of the edge labels in axis using the [`EdgeLabelsDrawingMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property. [`EdgeLabelsDrawingMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode) property default value is [`Center`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.EdgeLabelsDrawingMode.html).

The following are the customizing options in [`EdgeLabelsDrawingMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsDrawingMode).

* Center- Positions the label with tick line as center.
* Fit- Position the gridline inside based on the edge label size.
* Hide- Hides the edge labels.
* Shift- Shifts the edge labels to the left or right so that it comes inside the chart area.

**Center**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Center" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Center

};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/Axis_img19.jpeg)

**Shift**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Shift" ></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Shift

};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/Axis_img20.jpeg)


**Hide**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Hide">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Hide

};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/Axis_img21.jpeg)


**Fit**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Fit">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Fit

};

{% endhighlight %}

{% endtabs %}

![Axis edge label positioning support in WinUI Chart](Axis_images/Axis_img22.jpeg)


**EdgeLabelsVisibilityMode**

The visibility of the extreme labels of the axis can be controlled using [`EdgeLabelsVisibilityMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) property. By default the [`Default`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.EdgeLabelsVisibilityMode.html) option in [`EdgeLabelsVisibilityMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) is set, which displays the edge label based on auto interval calculations .The following image depicts the default option in [`EdgeLabelsVisibilityMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) while zooming.

![Axis edge label visibility support in WinUI Chart](Axis_images/Axis_img23.jpeg)


**Always** **Visible**

AlwaysVisible option in [`EdgeLabelsVisibilityMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EdgeLabelsVisibilityMode) is used to view the edge labels even while performing zooming.

The following code example and image demonstrates the AlwaysVisible option while zooming.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis EdgeLabelsVisibilityMode="AlwaysVisible" 

EnableScrollBar="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.AlwaysVisible

};

{% endhighlight %}

{% endtabs %}

![Axis edge label visibility support in WinUI Chart](Axis_images/Axis_img24.jpeg)


**Visible**

Visible option is used to display the edge labels (first and last label) irrespective of the auto interval calculation until zooming (i.e., in normal state)

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis EdgeLabelsVisibilityMode="Visible">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.Visible

};

{% endhighlight %}

{% endtabs %}

![Axis edge label visibility support in WinUI Chart](Axis_images/Axis_img25.jpeg)

## Grid lines

By default, gridlines are automatically added to the [`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#) in its defined intervals. SfChart supports customization of gridline. The visibility of the gridlines can be controlled using the [`ShowGridLines`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowGridLines) property.

The following code example illustrates the [`ShowGridLines`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowGridLines) property as false in the primary axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  ShowGridLines="False"  >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    ShowGridLines = false
    
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/Axis_img26.jpeg)


Style can also be applied to Major and Minor Gridlines using [`MajorGridLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorGridLineStyle) and [`MinorGridLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MinorGridLineStyle) properties.

**MajorGridLineStyle**

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

     <syncfusion:SfChart.Resources>

         <Style TargetType="Line" x:Key="lineStyle">

                <Setter Property="StrokeThickness" Value="2"/>

                <Setter Property="Stroke" Value="Black"/>

                <Setter Property="StrokeDashArray" Value="3,3"/>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

            <syncfusion:NumericalAxis MajorGridLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.PrimaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/Axis_img27.jpeg)


**MinorGridLineStyle**

Minor gridlines will be added automatically when the small tick lines is defined inside the chart area.

{% tabs %}

{% highlight xaml %}

  <syncfusion:SfChart x:Name="chart">

      <syncfusion:SfChart.Resources>

            <Style TargetType="Line" x:Key="lineStyle">

                    <Setter Property="StrokeThickness" Value="1"/>

                    <Setter Property="Stroke" Value="DarkGray"/>

                    <Setter Property="StrokeDashArray" Value="3,3"/>

            </Style>

        </syncfusion:SfChart.Resources>

        <syncfusion:SfChart.SecondaryAxis>

                <syncfusion:NumericalAxis SmallTicksPerInterval="3" 
                                          
                                          MinorGridLineStyle="{StaticResource lineStyle}"/>

       </syncfusion:SfChart.SecondaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    SmallTicksPerInterval = 3,

    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![Gridlines customization support in WinUI Chart](Axis_images/Axis_img28.jpeg)


## Tick lines

Tick line are the small lines which is drawn on the axis line representing the axis labels .Tick lines will be drawn outside of the axis by default. 

**TickLineSize**

Tick lines thickness can be customized using [`TickLineSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TickLineSize) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  TickLineSize="10" ></syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

   TickLineSize = 10 
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/Axis_img29.jpeg)


**Positioning** **the** **Major** **Tick** **Lines**

Tick lines can be positioned inside or outside of the chart area using [`TickLinesPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TickLinesPosition) property. By default the tick lines will positioned outside of the chart area. The following code example demonstrates the positioning tick lines inside chart area.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis TickLinesPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

   TickLinesPosition = AxisElementPosition.Inside
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines positioning support in WinUI Chart](Axis_images/Axis_img30.jpeg)


**Customization**

Style can be applied to major tick lines using [`MajorTickLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MajorTickLineStyle) property .The following code snippet demonstrates the styling of major tick lines.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="Line" x:Name="lineStyle">

            <Setter Property="StrokeThickness" Value="1"/>

            <Setter Property="Stroke" Value="Black"/>

            <Setter Property="StrokeDashArray" Value="3,3"/>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.SecondaryAxis>

                <syncfusion:NumericalAxis TickLineSize="10"
                                          
                                          MajorTickLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.SecondaryAxis>

 </syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    TickLineSize = 10,

    MajorTickLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/Axis_img31.jpeg)


**MinorTickLines**

Minor tick lines can be added by defining [`SmallTicksPerInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_SmallTicksPerInterval) property. This property will add the tick lines  to every interval.

The following code example demonstrates the small ticks set for every interval.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis Interval="1" SmallTicksPerInterval="4" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 4
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/Axis_img32.jpeg)


**Positioning** **the** **minor** **tick** **lines**

Minor tick lines can be positioned inside or outside using [`SmallTickLinesPosition`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_SmallTickLinesPosition) property. By default the minor tick lines will be positioned outside.

The following code example demonstrates the positioning of minor tick lines inside the chart area.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis SmallTicksPerInterval="2" SmallTickLinesPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    SmallTicksPerInterval = 2,

    SmallTickLinesPosition = AxisElementPosition.Inside
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines positioning support in WinUI Chart](Axis_images/Axis_img33.jpeg)


**Customization** **of** **Minor** **Ticklines**

The thickness of the minor tick lines can be customized using [`SmallTickLineSize`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.RangeAxisBase.html#Syncfusion_UI_Xaml_Charts_RangeAxisBase_SmallTickLineSize) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis Interval="1" SmallTicksPerInterval="3" SmallTickLineSize="10">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 3,

    SmallTickLineSize = 10
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/Axis_img34.jpeg)

Styling customization of minor tick lines can be defined using [`MinorTickLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MinorTickLineStyle) property. The following code example and image demonstrates the style for minor tick lines.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

     <syncfusion:SfChart.Resources>

                <Style TargetType="Line" x:Name="lineStyle" >

                    <Setter Property="StrokeThickness" Value="0.5"/>

                    <Setter Property="Stroke" Value="Black"/>

                </Style>

     </syncfusion:SfChart.Resources>

     <syncfusion:SfChart.SecondaryAxis>

            <syncfusion:NumericalAxis FontSize="12"  Interval="1"
                                          
                                      SmallTicksPerInterval="3" 
                                          
                                      TickLineSize="10" SmallTickLineSize="5"
                                          
                                      MinorTickLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.SecondaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 3,

    TickLineSize = 10,

    SmallTickLineSize = 5

    MinorTickLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![Ticklines customization support in WinUI Chart](Axis_images/Axis_img35.jpeg)


N> For category axis, small tick lines is not applicable since it is rendered based on index positions.

## AxisLine

SfChart provides support to customize the style of the axis line by defining the [`AxisLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineStyle) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  Interval="1" >

<syncfusion:NumericalAxis.AxisLineStyle>

<Style TargetType="Line"  >

<Setter Property="StrokeThickness" Value="2"/>

<Setter Property="Stroke" Value="Red"/>

<Setter Property="StrokeDashArray" Value="2,2"/>

</Style>

</syncfusion:NumericalAxis.AxisLineStyle>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    AxisLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![AxisLine customization support in WinUI Chart](Axis_images/Axis_img36.jpeg)


**Applying** **Padding** **to** **the** **Axis** **line**

The padding to the axis line is defined using [`AxisLineOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineOffset) property. The following code example demonstrates the setting [`AxisLineOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_AxisLineOffset) for x axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis AxisLineOffset="20" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    AxisLineOffset = 20
    
};

{% endhighlight %}

{% endtabs %}

![Padding support for axis line in WinUI](Axis_images/Axis_img37.jpeg)

## Types of Axis

[`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#) supports the following types.

* NumericalAxis
* CategoryAxis
* DateTimeAxis

You can choose any type of [`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#), like [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#), [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#), [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#) depending on the value type. 

### NumericalAxis

[`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is used to plot numerical values to the chart. [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) can be defined for both [`PrimaryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_PrimaryAxis) and [`SecondaryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_SecondaryAxis). The following code snippet shows how to define the [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis();

chart.SecondaryAxis = new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![NumericalAxis support in WinUI Chart](Axis_images/Axis_img42.jpeg)


**Customizing** **the** **NumericalAxis** **Range**

[`Maximum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Maximum) property used for setting the maximum value for the axis range and [`Minimum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Minimum) property is used for setting the minimum value for the axis range.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Maximum="2750" Minimum="250" Interval="250">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Maximum = 2750,

    Minimum = 250,

    Interval = 250

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Chart](Axis_images/Axis_img43.jpeg)


N> If  minimum or maximum value is set, the other value is calculated by default internally.

**StartRangeFromZero**

[`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) will calculate the range based on the data points binded to the axis. To start the range from zero have to define the [`StartRangeFromZero`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_StartRangeFromZero) property to True. The following code example demonstrates the NumericalAxis range starting from zero.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis StartRangeFromZero="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

   StartRangeFromZero = true

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis customization support in WinUI Chart](Axis_images/Axis_img44.jpeg)


N> By default, Range is calculated between the minimum and maximum value of the data points.

### CategoryAxis

[`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#) is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here. The following code example initializes the [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis >

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis();

{% endhighlight %}

{% endtabs %}

![CategoryAxis support in WinUI Chart](Axis_images/Axis_img45.jpeg)


**LabelPlacement**

In [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#), labels is placed based on tick lines using [`LabelPlacement`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#Syncfusion_UI_Xaml_Charts_CategoryAxis_LabelPlacement) property. By default the labels is placed [`OnTicks`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.LabelPlacement.html). The following code example demonstrates placing the label between ticks in [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#)

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelPlacement="BetweenTicks">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelPlacement = LabelPlacement.BetweenTicks

};

{% endhighlight %}

{% endtabs %}

![Axis label placement support in WinUI Chart](Axis_images/Axis_img46.jpeg)


**IsIndexed**

By default, [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html) plots the values based on the index of the data points. However, the [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html) can be made to plot the data points based on its data, instead of index value by disabling the [`IsIndexed`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#Syncfusion_UI_Xaml_Charts_CategoryAxis_IsIndexed) property of [`CategoryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html), and it is shown in the following code example.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis IsIndexed="False"/>
                
 </syncfusion:SfChart.PrimaryAxis>


{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()

{
                
    IsIndexed = false,
            
};

{% endhighlight %}

{% endtabs %}

The following screenshot illustrates the series with IsIndexed value as False.

![Axis label IsIndexed support in WinUI Chart](Axis_images/isindexed_false.png)

By default, the IsIndexed property value is true, and it is shown in following screenshot.

![Axis label IsIndexed support in WinUI Chart](Axis_images/isindexed_true.png)

N> This feature is not applicable for Accumulation series, RadarSeries, and PolarSeries.

### DateTimeAxis

[`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is used to plot DateTime values. The [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is widely used to make financial charts in places like the Stock Market, where index plotting is done every day.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelFormat="MMM-dd"></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelFormat = "MMM-dd"

};

{% endhighlight %}

{% endtabs %}

![DateTimeCategoryAxis support in WinUI Chart](Axis_images/Axis_img47.jpeg)


**Customizing** **the** **Range**

[`Minimum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_Minimum) and [`Maximum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_Maximum) properties behavior is same as in NumericalAxis instead of setting numerical value, you have to set date time values.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  Minimum="2015/01/10" Maximum="2015/07/01" LabelFormat="MMM-dd" 

IntervalType="Months" Interval="1">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    Minimum = new DateTime(2015,01,10),

    Maximum = new DateTime(2015,07,01),

    LabelFormat = "MMM-dd",

    IntervalType = DateTimeIntervalType.Months,

    Interval = 1

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range customization support in WinUI Chart](Axis_images/Axis_img48.jpeg)


**Business** **Hours** **Range** **Calculation**

SfChart provides support to plot only the business hours in DateTimeAxis.This support is enabled by setting [`EnableBusinessHours`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_EnableBusinessHours) property to true.

The following properties are used for business hour range calculation

* [`OpenTime`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_OpenTime)- Represents the open working time of a day.
* [`CloseTime`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_CloseTime)- Represents the close working time of a day.
* [`WorkingDays`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_WorkingDays)- Represents the working [`days`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.Day.html) of a week.

The following code snippet demonstrates the business hours support in DateTimeAxis

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis EnableBusinessHours="True" OpenTime="9" 

CloseTime="24" WorkingDays="Friday,Saturday,Sunday,Monday,Tuesday,Wednesday,Sunday">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EnableBusinessHours = true,

    OpenTime = 9,

    CloseTime = 24,

    WorkingDays = Day.Friday | Day.Saturday | Day.Sunday |
                Day.Monday | Day.Tuesday| Day.Wednesday| Day.Sunday

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range customization support in WinUI Chart](Axis_images/Axis_img49.jpeg)

## Inverting axis

Axis can be inverted using the [`IsInversed`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_IsInversedProperty) property. The default value of this property is `False`.

{% tabs %}

{% highlight xaml %}

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis IsInversed="True"/>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

this.Chart.SecondaryAxis.IsInversed = true;

{% endhighlight %}

{% endtabs %}

![Inversed axis support in WinUI Chart](Axis_images/InversedAxis.png)


## Customizing the Intervals

[`ChartAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#) calculates the range and intervals automatically based on the data points. The axis range and interval can be defined using the [`Minimum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Minimum), [`Maximum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Maximum) and [`Interval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Interval) properties.

**NumericalAxis**

The following code snippet demonstrates the [`Interval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_Interval) customization in NumericalAxis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Interval="250">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Interval = 250

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis Interval customization support in WinUI Chart](Axis_images/Axis_img56.jpeg)


**CategoryAxis**

The following code snippet demonstrates the [`Interval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CategoryAxis.html#Syncfusion_UI_Xaml_Charts_CategoryAxis_Interval) customization in CategoryAxis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Interval="2">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    Interval = 2

};

{% endhighlight %}

{% endtabs %}

![CategoryAxis Interval customization support in WinUI Chart](Axis_images/Axis_img57.jpeg)

**DateTimeAxis**

The DateTimeAxis [`Interval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_Interval) value corresponds to the type specified in the [`IntervalType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_IntervalType) property.

For instance, if the [`Interval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_Interval) is set as 2 and [`IntervalType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_IntervalType) is set as [`Days`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), the labels are plotted for every two days. The following are the options for [`IntervalType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_IntervalType) property

Auto
* Days
* Hours
* Milliseconds
* Minutes
* Months
* Seconds
* Years

The default [`IntervalType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_IntervalType) of a [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is Auto. It calculates the type automatically and the interval, accordingly.

The following code snippet demonstrates the DateTimeAxis having one month interval.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  Interval="1"  IntervalType="Months" LabelFormat="MMM-dd"></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    Interval = 1,

    IntervalType = DateTimeIntervalType.Months,

    LabelFormat = "MMM-dd"

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis Interval customization support in WinUI Chart](Axis_images/Axis_img58.jpeg)


**DesiredIntervalsCount**

[`DesiredIntervalsCount`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_DesiredIntervalsCount) property is used to specify the count of the axis labels between the first and last label. The following sample code defines the [`DesiredIntervalsCount`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_DesiredIntervalsCount) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis DesiredIntervalsCount="7">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    DesiredIntervalsCount = 7

};

{% endhighlight %}

{% endtabs %}

![Interval customization support in WinUI Chart](Axis_images/Axis_img59.jpeg)


**Maximum** **Labels**

[`MaximumLabels`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_MaximumLabels) property defines the count of the axis labels in the 100 pixels.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis  MaximumLabels="2">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}" XBindingPath="Demand" YBindingPath="Year2010">

<syncfusion:ColumnSeries.YAxis>

<syncfusion:NumericalAxis MaximumLabels="2" >

</syncfusion:NumericalAxis>

</syncfusion:ColumnSeries.YAxis>

</syncfusion:ColumnSeries>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    MaximumLabels = 2

};

NumericalAxis axis = new NumericalAxis() { MaximumLabels = 2 };

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    YAxis = axis

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Interval customization support in WinUI Chart](Axis_images/Axis_img60.jpeg)


## Apply Padding to the Range

The [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) and [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) have a [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) property that can be used to add padding to the range of a chart’s axes.

### DateTimeRangePadding

The [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) types available in the [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) are: 

* Auto
* Additional
* None
* Round
* RoundStart
* RoundEnd
* PrependInterval
* AppendInterval

**Auto**

By default the date time range padding is [`Auto`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html).

![DateTimeAxis range padding support in WinUI Chart](Axis_images/Axis_img61.jpeg)


**Additional**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#), the DateTime interval of the axis is added as padding, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="Additional">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.Additional

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/Axis_img62.jpeg)


**Round**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is set to [`Round`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html), the range of the chart axis is rounded off to the nearest possible DateTime value, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="Round">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.Round

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/Axis_img63.jpeg)


**None**

When the [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for a [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is [`None`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html).

The following screenshot demonstrates a chart’s x-axis with `RangePadding` set to `None`. 

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="None">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.None

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/Axis_img64.jpeg)

**RoundStart**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is set to [`RoundStart`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html), the range of the chart axis is rounded in the start off to the nearest possible DateTime value, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="RoundStart">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.RoundStart

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/DateTimeAxis_RoundStart.png)


**RoundEnd**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is set to [`RoundEnd`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html), the range of the chart axis is rounded in the end off to the nearest possible DateTime value, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="RoundEnd">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.RoundEnd

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/DateTimeAxis_RoundEnd.png)


**PrependInterval**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is set to [`PrependInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html), the DateTime interval of the axis is added in the start as padding, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="PrependInterval">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.PrependInterval

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/DateTimeAxis_PrependInterval.png)


**AppendInterval**

When [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is set to [`AppendInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeRangePadding.html), the DateTime interval of the axis is added in the end as padding, as shown in the following screenshot.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="AppendInterval">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.AppendInterval

};

{% endhighlight %}

{% endtabs %}

![DateTimeAxis range padding support in WinUI Chart](Axis_images/DateTimeAxis_AppendInterval.png)


### NumericalRangePadding

The following types are available for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#):

* Additional
* None
* Normal
* Round
* Auto
* RoundStart
* RoundEnd
* PrependInterval
* AppendInterval

**Round**

By default, the default [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) value for [`PrimaryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_PrimaryAxis) is Auto and for [`SecondaryAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_SecondaryAxis), the default value is [`Round`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

The following screenshot illustrates a chart’s y-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`Round`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

![NumericalAxis range padding support in WinUI Chart](Axis_images/Axis_img65.jpeg)


**Normal**

[`Normal`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html) [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for a [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is used mostly for the y-axis to have padding based on the Range calculation.

The following screenshot illustrates a chart’s y-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`Normal`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="Normal">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.Additional

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/Axis_img66.jpeg)


**Additional**

If [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is set to [`Additional`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), the interval of the axis is added as padding.

The following screenshot demonstrates a chart’s x-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`Additional`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="Additional">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.Additional

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/Axis_img67.jpeg)


**None**

The following screenshot demonstrates [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) as [`None`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), where no padding is applied for the axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="None">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.None

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/Axis_img68.jpeg)

**RoundStart**

If [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is set to [`RoundStart`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), rounds the range of the chart axis in the start to the nearest possible value.

The following screenshot demonstrates a chart’s x-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`RoundStart`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="RoundStart">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.RoundStart

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/NumericalAxis_RoundStart.png)


**RoundEnd**

If [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is set to [`RoundEnd`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), rounds the range of the chart axis in the end to the nearest possible value.

The following screenshot demonstrates a chart’s x-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`RoundEnd`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="RoundEnd">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.RoundEnd

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/NumericalAxis_RoundEnd.png)


**PrependInterval**

If [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is set to [`PrependInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), the interval of the axis is added in the start as padding.

The following screenshot demonstrates a chart’s x-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`PrependInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="PrependInterval">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.PrependInterval

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/NumericalAxis_PrependInterval.png)


**AppendInterval**

If [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) for [`NumericalAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is set to [`AppendInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html), the interval of the axis is added in the end as padding.

The following screenshot demonstrates a chart’s x-axis with [`RangePadding`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalAxis.html#Syncfusion_UI_Xaml_Charts_NumericalAxis_RangePadding) set to [`AppendInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.NumericalPadding.html).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="AppendInterval">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.AppendInterval

};

{% endhighlight %}

{% endtabs %}

![NumericalAxis range padding support in WinUI Chart](Axis_images/NumericalAxis_AppendInterval.png)


##  Applying Padding to the Axis

[`PlotOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffset) property is used to provide padding to the axis. The following code snippet demonstrates the padding applied to both x and y axes.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  PlotOffset="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis PlotOffset="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    PlotOffset = 30

};

chart.SecondaryAxis = new NumericalAxis()
{

    PlotOffset = 30

};

{% endhighlight %}

{% endtabs %}

![Padding for ChartAxis support in WinUI](Axis_images/Axis_img69.jpeg)

### PlotOffsetStart

[`PlotOffsetStart`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffsetStart) property is used to provide padding to the axis at start position. The following code snippet demonstrates the padding applied to start position for both x and y axes.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  PlotOffsetStart="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis PlotOffsetStart="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    PlotOffsetStart = 30

};

chart.SecondaryAxis = new NumericalAxis()
{

    PlotOffsetStart = 30

};

{% endhighlight %}

{% endtabs %}

![PlotOffsetStart for ChartAxis support in WinUI](Axis_images/PlotOffset_Start.png)

### PlotOffsetEnd

[`PlotOffsetEnd`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_PlotOffsetEnd) property is used to provide padding to the axis at end position. The following code snippet demonstrates the padding applied to end position for both x and y axes.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  PlotOffsetEnd="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis PlotOffsetEnd="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    PlotOffsetEnd = 30

};

chart.SecondaryAxis = new NumericalAxis()
{

    PlotOffsetEnd = 30

};

{% endhighlight %}

{% endtabs %}

![PlotOffsetEnd for ChartAxis support in WinUI](Axis_images/PlotOffset_End.png)

## AutoScrollingDelta

[`AutoScrollingDelta`](https://help.syncfusion.com/cr/WinUI/Syncfusion.Windows.Chart.ChartAxis.html#Syncfusion_Windows_Chart_ChartAxis_AutoScrollingDelta) is used to ensure whether the specified range of data is always visible in the chart. It always shows the recently added data points at the end, and the scrolling will be reset to the end of the range whenever a new point is added. 

### AutoScrollingDeltaType

In [`DateTimeAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html), you can apply auto scrolling delta value in [`Years`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), [`Months`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), [`Days`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), [`Hours`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), [`Minutes`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), [`Seconds`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html) and [`Milliseconds`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html) by setting the [`AutoScrollingDeltaType`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#Syncfusion_UI_Xaml_Charts_DateTimeAxis_AutoScrollingDeltaType) property. The default value of this property is [`Auto`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.DateTimeIntervalType.html), and the delta will be calculated automatically based on range.

{% tabs %} 

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

    <chart:DateTimeAxis AutoScrollingDelta = "3" AutoScrollingDeltaType = "Days">

</chart:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
      AutoScrollingDelta = 3,
	  
      AutoScrollingDeltaType = DateTimeIntervalType.Days
};

{% endhighlight %}

{% endtabs %}

### AutoScrollingMode

The [`AutoScrollingMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBase2D.html#Syncfusion_UI_Xaml_Charts_ChartAxisBase2D_AutoScrollingMode) property is used to determine whether the axis should be scrolled from the start position or end position. The default value of this property is [`End`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAutoScrollingMode.html).

{% tabs %} 

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

    <chart:DateTimeAxis AutoScrollingDelta = "3" AutoScrollingMode = "Start">

</chart:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{
      AutoScrollingDelta = 3,
	  
      AutoScrollingMode = ChartAutoScrollingMode.Start
};

{% endhighlight %}

{% endtabs %}


## Auto Interval Calculation on Zooming

[`EnableAutoIntervalOnZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EnableAutoIntervalOnZooming) property is used to maintain the interval even it is in zooming state only if we set the interval to the axis. Default value of this property is true. While zooming based on the auto range padding the interval will be calculated.

![Auto interval on zooming support in WinUI](Axis_images/Axis_img70.jpeg)


If you set [`EnableAutoIntervalOnZooming`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_EnableAutoIntervalOnZooming) as False, the intervals will be calculated on the interval based on the axis while zooming.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis Interval="1"

EnableAutoIntervalOnZooming="False">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EnableAutoIntervalOnZooming = false,

    Interval = 1

};

{% endhighlight %}

{% endtabs %}

![Auto interval on zooming support in WinUI](Axis_images/Axis_img71.jpeg)


## Multiple Axes

SfChart provides a way to arrange multiple series inside the same chart area, giving the chart more space than x-axis and y-axis. These axes can be arranged in a stacking order or in a side by side pattern.

By default, all the series are plotted based on primary and secondary axis. You can add more axes by adding additional axis to the series. There are two properties [`XAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CartesianSeries.html#Syncfusion_UI_Xaml_Charts_CartesianSeries_XAxis) and [`YAxis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CartesianSeries.html#Syncfusion_UI_Xaml_Charts_CartesianSeries_YAxis) in all the series type which is used to provide Multiple axes support, except [`AccumulationSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}"

XBindingPath="Demand"  YBindingPath="Year2011">

</syncfusion:ColumnSeries>

<syncfusion:LineSeries  ItemsSource="{Binding Demands}"

XBindingPath="Date"  YBindingPath="Year2011">

<syncfusion:LineSeries.XAxis>

<syncfusion:DateTimeAxis />

</syncfusion:LineSeries.XAxis>

<syncfusion:LineSeries.YAxis>

<syncfusion:NumericalAxis/>

</syncfusion:LineSeries.YAxis>

</syncfusion:LineSeries>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011"
    
};

LineSeries series2 = new LineSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Date",

    YBindingPath = "Year2011",

};

series2.XAxis = new DateTimeAxis()
{

    Header = "Additional X Axis"

};

series2.YAxis = new NumericalAxis()
{

    Header = "Additional Y Axis"

};

chart.Series.Add(series1);

chart.Series.Add(series2);


{% endhighlight %}

{% endtabs %}

![Multiple axes support in WinUI Chart](Axis_images/Axis_img72.jpeg)

In the above screenshot, the LineSeries is plotted based on additional X & Y axes, and ColumnSeries (or remaining series) is plotted based on the primary and secondary axes.

## Events

### ActualRangeChanged

The [`ActualRangeChanged`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html) event occurs when an axis range is changed. This argument contains the following information.

* [`ActualMinimum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_ActualMinimum) - Gets or sets the actual minimum value of axis.
* [`ActualMaximum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_ActualMaximum) - Gets or sets the actual maximum value of axis.
* [`VisibleMinimum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_VisibleMinimum) - Gets or sets the visible minimum value of axis.
* [`VisibleMaximum`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_VisibleMaximum) - Gets or sets the visible maximum value of axis.
* [`ActualInterval`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ActualRangeChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_ActualRangeChangedEventArgs_ActualInterval) - Gets the actual interval of axis.

### LabelCreated

The [`LabelCreated`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html) event occurs when the axis label is created. This argument contains [`AxisLabel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.LabelCreatedEventArgs.html#Syncfusion_UI_Xaml_Charts_LabelCreatedEventArgs_AxisLabel) of [`ChartAxisLabel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html), which contains the following properties.

* [`Content`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Content) - Gets or sets the content of label.
* [`Position`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Position) - Gets or sets the position of label.

### AxisBoundsChanged

The [`AxisBoundsChanged`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html) event occurs when the bounds of the axis are changed. This argument contains the following information.

* [`NewBounds`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBoundsEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartAxisBoundsEventArgs_NewBounds) - Gets the new axis bounds.
* [`OldBounds`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBoundsEventArgs.html#Syncfusion_UI_Xaml_Charts_ChartAxisBoundsEventArgs_OldBounds) - Gets the old axis bounds.

### LabelClicked

The [`LabelClicked`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisBase2D.html) event is triggered when labels are clicked. Supports for 2D axis. The argument contains [`Label`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.AxisLabelClickedEventArgs.html#Syncfusion_UI_Xaml_Charts_AxisLabelClickedEventArgs_Label) of [`ChartAxisLabel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html), which contains the following properties.

* [`Content`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Content) - Gets the content of label.
* [`Position`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxisLabel.html#Syncfusion_UI_Xaml_Charts_ChartAxisLabel_Position) - Gets the position of label.