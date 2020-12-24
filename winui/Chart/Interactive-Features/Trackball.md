---
layout: post
title: Trackball feature in Syncfusion SfChart WinUI
description: This section describles how to customize the Trackball behavior, label in Essential WinUI Chart (SfChart).
platform: WinUI
control: SfChart
documentation: ug
---

# Trackball in WinUI Charts (SfChart)

The [`ChartTrackballBehavior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#) allows you to track a data point closer to the cursor position. The x values are determined from the position of the vertical line in the axis and y values are determined from the points touching the vertical line in the series.

## Adding Trackball to the SfChart

You can create an instance [`ChartTrackballBehavior`](http://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#) and add it to the [`Behaviors`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.SfChart.html#Syncfusion_UI_Xaml_Charts_SfChart_Behaviors) collection.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior>                                                  

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

ChartTrackballBehavior behavior = new ChartTrackballBehavior();

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

To view the Trackball in the particular Axis, you have to enable the ShowTrackballInfo property in that axis as in the following code snippet.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis  ShowTrackballInfo="True" />

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior();

chart.Behaviors.Add(behavior);

chart.PrimaryAxis = new CategoryAxis()
{

    ShowTrackballInfo = true

};

{% endhighlight %}

{% endtabs %}

The default appearance of the Trackball in primary axis (CategoryAxis).

![Trackball support in WinUI Chart](Interactive-Features_images/Interactive-Features_img7.jpeg)


The Trackball is composed of the following parts:

1. Vertical Line

2. Symbol

3. Axis Label

4. Series Label

## Vertical Line

The vertical line in the Trackball is visible when you initialize the TrackballBehavior. If you want to collapse the visibility of the Trackball line, then you have to set [`ShowLine`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_ShowLine) to false.

The following code snippet explains how to collapse the visibility of Trackball line.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior ShowLine="False" />

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    ShowLine = false

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Trackball support in WinUI Chart](Interactive-Features_images/Interactive-Features_img8.jpeg)


**Customization of Trackball Line**

SfChart allows you to customize the appearance of Trackball vertical line using the [`LineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LineStyle) property.

The following code snippet explains the customization of Trackball line.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="Line" x:Key="lineStyle">

            <Setter Property="StrokeDashArray" Value="5,2"/>

            <Setter Property="Stroke" Value="Red"/>

            <Setter Property="StrokeThickness" Value="1.2"/>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.Behaviors>

        <syncfusion:ChartTrackballBehavior LineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.Behaviors>
            
</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior Trackball = new ChartTrackballBehavior()
{

    LineStyle = chart.Resources["lineStyle"] as Style

};

chart.Behaviors.Add(Trackball);

{% endhighlight %}

{% endtabs %}

![Trackball line customization in WinUI Chart](Interactive-Features_images/Interactive-Features_img9.jpeg)


## Symbol

By default, the Trackball symbol is displayed as ellipse to change the default style of the symbol using [`ChartTrackballStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_ChartTrackballStyle) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="syncfusion:ChartTrackballControl" x:Key="TrackballStyle">

            <Setter Property="Background" Value="Red"></Setter>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.Behaviors>

        <syncfusion:ChartTrackballBehavior ChartTrackballStyle="{StaticResource TrackballStyle}"/>

    </syncfusion:SfChart.Behaviors>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

ChartTrackballBehavior Trackball = new ChartTrackballBehavior()
{

    ChartTrackballStyle = chart.Resources["TrackballStyle"] as Style

};

chart.Behaviors.Add(Trackball);

{% endhighlight %}

{% endtabs %}

![Symbol for Trackball in WinUI Chart](Interactive-Features_images/Interactive-Features_img10.jpeg)


## Axis Label

The axis label will be viewed when the [`ShowTrackballInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property is set to true. If you want to collapse the visibility of axis label in Trackball then you have to set ShowTrackballInfo as false.

N>By default the value of [`ShowTrackballInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) is false.

**Alignment** **of** **Axis** **Label**

The alignment of the axis label while moving Trackball can be defined using [`AxisLabelAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_AxisLabelAlignment) property.

Auto - Axis label is aligned in Near/Far positions based on the Trackball movement.

Far - Axis label is positioned far from the position of Trackball.

Near - Axis label is near to the position of Trackball.

Center - Axis label is aligned to the center of the Trackball. By default, the axis label will positioned in center.

**Far**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior AxisLabelAlignment="Far">

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    AxisLabelAlignment = ChartAlignment.Far

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Alignment support for Trackball axis label in WinUI Chart](Interactive-Features_images/Interactive-Features_img11.jpeg)


**Near**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior AxisLabelAlignment="Near"  >       

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    AxisLabelAlignment = ChartAlignment.Near

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Alignment support for Trackball axis label in WinUI Chart](Interactive-Features_images/Interactive-Features_img12.jpeg)


### Customization of axis label

You can change the default appearance of the axis label in Trackball using [`TrackballLabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_TrackballLabelTemplate) property in `ChartAxis` as in the below code snippet.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="labelTemplate">

            <Border CornerRadius="4" BorderThickness="1" BorderBrush="Black"
                            
                    Background="BlueViolet" Margin="8">

                    <TextBlock Foreground="White" Text="{Binding ValueX}"/>

            </Border>

        </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.Behaviors>

            <syncfusion:ChartTrackballBehavior />

    </syncfusion:SfChart.Behaviors>

    <syncfusion:SfChart.PrimaryAxis>

            <syncfusion:CategoryAxis ShowTrackballInfo="True" 
                                         
                                     LabelTemplate="{StaticResource labelTemplate}"/>

    </syncfusion:SfChart.PrimaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

chart.PrimaryAxis = new NumericalAxis()
{

    ShowTrackballInfo = true,

    TrackballLabelTemplate = chart.Resources["labelTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![Customization support for Trackball axis label in WinUI Chart](Interactive-Features_images/Interactive-Features_img13.jpeg)


### Series Label

When the Trackball is hovered over, you can view the label is also displayed over the series in addition the axis label.

**ShowTrackballInfo**

The `ShowTrackballInfo` property of [`Cartesian Series`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.CartesianSeries.html) allows user to enable or disable the [`Trackball`](https://help.syncfusion.com/WinUI/sfchart/interactive-features#Trackball) label for corresponding series. By default, `ShowTrackballInfo` property is true. The property can be set as shown in the below code example:

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart >
            <syncfusion:SplineSeries />    
            <syncfusion:SplineSeries ShowTrackballInfo="False"/>
            <syncfusion:SplineSeries />
 </syncfusion:SfChart>
 
{% endhighlight %}

{% highlight c# %}

  SplineSeries series1 = new SplineSeries();
  chart.Series.Add(series1);
  SplineSeries series2 = new SplineSeries()
  {
      ShowTrackballInfo = false
  };
  chart.Series.Add(series2);
  SplineSeries series3 = new SplineSeries();
  chart.Series.Add(series3);

{% endhighlight %}

{% endtabs %}

![Trackball series label in WinUI Chart](Interactive-Features_images/ShowTrackball.png)

**Alignment** **of** **Series** **Label**

The Trackball label displayed over the series can be aligned using the [`LabelHorizontalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelHorizontalAlignment) and [`LabelVerticalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelVerticalAlignment) properties. By default, the series label will be horizontally aligned to the left and vertically to the top.

The following code snippet explains how to align the series label to the center of the Trackball.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior LabelHorizontalAlignment="Center" 

LabelVerticalAlignment="Center">

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    LabelHorizontalAlignment = ChartAlignment.Center,

    LabelVerticalAlignment = ChartAlignment.Center

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Alignment support for Trackball series label in WinUI Chart](Interactive-Features_images/Interactive-Features_img14.jpeg)


### Label Display Mode

When there is a multiple series, by default, the Trackball series label will be displayed only for the nearest point. If you want to display all the y values with respect to the x value then the [`LabelDisplayMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayMode) property is set to [`FloatAllPoints`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.TrackballLabelDisplayMode.html).

**FloatAllPoints**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior LabelDisplayMode="FloatAllPoints" >

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    LabelDisplayMode = TrackballLabelDisplayMode.FloatAllPoints

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![LabelDisplayMode support for Trackball in WinUI Chart](Interactive-Features_images/Interactive-Features_img15.jpeg)


**NearestPoint**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior LabelDisplayMode="NearestPoint" >

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    LabelDisplayMode = TrackballLabelDisplayMode.NearestPoint

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![LabelDisplayMode support for Trackball in WinUI Chart](Interactive-Features_images/Interactive-Features_img16.jpeg)

**GroupAllPoints**

[`ChartTrackballBehavior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) supports to group the multiple selected Trackball points, and allows to display the Trackball points in a single Trackball label. It can be achieved by setting the [`LabelDisplayMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayModeProperty) property of [`ChartTrackballBehavior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) as GroupAllPoints.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior LabelDisplayMode="GroupAllPoints" >

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

    LabelDisplayMode = TrackballLabelDisplayMode.GroupAllPoints

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

The following screenshot illustrates the Trackball label for multiple series, when the [`LabelDisplayMode`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_LabelDisplayModeProperty) property value is GroupAllPoints.

![LabelDisplayMode support for Trackball in WinUI Chart](Interactive-Features_images/grouping1.png)

### Trackball Label Template

[`TrackballLabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_TrackballLabelTemplate) property in [`ChartSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#) allows you to customize the appearance of series label in Trackball.

{% tabs %}

{% highlight xaml %}

  <syncfusion:SfChart x:Name="chart">

        <syncfusion:SfChart.Resources>

            <DataTemplate x:Key="labelTemplate">

                <Border CornerRadius="5" BorderThickness="1" 
                            
                        BorderBrush="Black" Background="BlueViolet" Margin="8">

                    <TextBlock Foreground="White" Text="{Binding ValueY}"/>

                </Border>

            </DataTemplate>

         </syncfusion:SfChart.Resources>

        <syncfusion:SfChart.Behaviors>

                <syncfusion:ChartTrackballBehavior />

        </syncfusion:SfChart.Behaviors>

        <syncfusion:ColumnSeries Label="2010"     

                                 ItemsSource="{Binding Demands}" 

                                 XBindingPath="Demand" 
                                     
                                 YBindingPath="Year2010"
                                 
                                 TrackballLabelTemplate="{StaticResource labelTemplate}"/>
          
</syncfusion:SfChart>


{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

ChartTrackballBehavior Trackball = new ChartTrackballBehavior();

chart.Behaviors.Add(Trackball);

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    TrackballLabelTemplate = chart.Resources["labelTemplate"] as DataTemplate,

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![Trackball templte support for Trackball in WinUI Chart](Interactive-Features_images/Interactive-Features_img17.jpeg)


**Applying** **Palette** **to** **the** **Series** **Label**

Palette or interior color of the Series is applied to the series label by setting [`UseSeriesPalette`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#Syncfusion_UI_Xaml_Charts_ChartTrackballBehavior_UseSeriesPalette) to True as shown in the following code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartTrackballBehavior UseSeriesPalette="True" >

</syncfusion:ChartTrackballBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartTrackballBehavior behavior = new ChartTrackballBehavior()
{

     UseSeriesPalette = true

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Applying palette to the Trackball series label in WinUI Chart](Interactive-Features_images/Interactive-Features_img18.jpeg)


## Events

The following events are available in ChartTrackballBehavior:

**PositionChanging**

The [`PositionChanging`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) event occurs when the [`Trackball`](http://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#) position is changing from current mouse position to new mouse position. This argument contains the following information.

* [`Cancel`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PositionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_PositionChangingEventArgs_Cancel) - Gets or sets a value that indicates whether to show the Trackball on new mouse pointer position.
* [`PointInfos`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PositionChangingEventArgs.html#Syncfusion_UI_Xaml_Charts_PositionChangingEventArgs_PointInfos) - Gets or sets the current [`ChartPointInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html).

**PositionChanged**

The [`PositionChanged`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html) event occurs when the [`Trackball`](http://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTrackballBehavior.html#) position is changed from current mouse position to new mouse position. This argument contains the following information.

* [`PreviousPointInfos`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PositionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_PositionChangedEventArgs_PreviousPointInfos) - Gets or sets the previous [`ChartPointInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html).
* [`CurrentPointInfos`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.PositionChangedEventArgs.html#Syncfusion_UI_Xaml_Charts_PositionChangedEventArgs_CurrentPointInfos) - Gets or sets the current [`ChartPointInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html).

The [`ChartPointInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html) class contains the following properties to customize the appearance of Trackball label:

* [`Axis`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Axis) - Gets the associated axis in which the Trackball is activated.
* [`BaseX`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_BaseX) - Gets the x-initial coordinate of the Trackball label. 
* [`BaseY`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_BaseY) - Gets the y-initial coordinate of the Trackball label.
* [`BorderBrush`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_BorderBrush) - Gets or sets the border color of the Trackball label.
* [`Close`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Close) - Gets the close value of the Trackball label when it is applicable.
* [`Foreground`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Foreground) - Gets or sets the foreground color of the Trackball label.
* [`High`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_High) - Gets the high value of the Trackball label when it is applicable.
* [`Interior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Interior) - Gets or sets the interior color of the Trackball label.
* [`Item`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Item) - Gets the respective underlying object of the data in which the Trackball is activated.
* [`Low`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Low) - Gets the low value of the Trackball label when it is applicable.
* [`Median`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Median) - Gets the median value when it is applicable.
* [`Open`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Open) - Gets the open value of the Trackball label when it is applicable.
* [`PolygonPoints`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_PolygonPoints) - Gets the point collection to render Trackball.
* [`Series`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Series) - Gets the associated series in which the Trackball is activated.
* [`SeriesValues`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_SeriesValues) - Gets the SeriesValues in which the Trackball is activated.
* [`ValueX`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_ValueX) - Gets the x-value of the Trackball label.
* [`ValueY`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_ValueY) - Gets the y-value of the Trackball label.
* [`X`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_X) - Gets the x-coordinate of the Trackball label.
* [`Y`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartPointInfo.html#Syncfusion_UI_Xaml_Charts_ChartPointInfo_Y) - Gets the y-coordinate of the Trackball label.