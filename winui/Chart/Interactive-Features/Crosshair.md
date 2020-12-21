---
layout: post
title: Serialization in Syncfusion SfChart WinUI.
description: Essental WinUI Chart (SfChart) supports Crosshair to view the values at mouse point or touch contact point.
platform: WinUI
control: SfChart
documentation: ug
---

# Crosshair in WinUI Charts (SfChart)

ChartCrosshairBehavior is used to view the values at mouse point or touch contact point. By moving these lines horizontally, you can get the X values and by moving these lines vertically, you can get the Y values.

## Adding CrosshairBehavior to SfChart

You can create an instance [`ChartCrosshairBehavior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#) and add it to the Behaviors collection.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartCrosshairBehavior />

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior();

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

To view the axis labels then set the [`ShowTrackballInfo`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_ShowTrackballInfo) property to true as in the below code snippet.

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis  ShowTrackballInfo="True"/>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis  ShowTrackballInfo="True"/>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior();

chart.Behaviors.Add(behavior);

chart.PrimaryAxis = new CategoryAxis()
{

    ShowTrackballInfo = true

};

chart.SecondaryAxis = new NumericalAxis()
{

    ShowTrackballInfo = true

};

{% endhighlight %}

{% endtabs %}

![Cross hair support in WinUI Chart](Interactive-Features_images/Interactive-Features_img46.jpeg)


Cross hair is composed of the following parts:

1. Vertical and horizontal line

2. Axis Labels

## Vertical and Horizontal Line

If you add [`ChartCrosshairBehavior`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#) to chart you can see horizontal and vertical lines.The horizontal and vertical lines can be customized using [`HorizontalLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_HorizontalLineStyle) and [`VerticalLineStyle`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_VerticalLineStyle) properties.

**HorizontalLineStyle**

The following code snippet demonstrates the line style for horizontal line in cross hair.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="Line" x:Key="lineStyle">

            <Setter Property="Stroke" Value="Green"></Setter>

            <Setter Property="StrokeThickness" Value="1"></Setter>

        </Style>
                
    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.Behaviors>

        <syncfusion:ChartCrosshairBehavior HorizontalLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.Behaviors>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior Crosshair = new ChartCrosshairBehavior()
{

    HorizontalLineStyle = chart.Resources["lineStyle"] as Style

};

chart.Behaviors.Add(Crosshair);

{% endhighlight %}

{% endtabs %}

![Cross hair line style in WinUI Chart](Interactive-Features_images/Interactive-Features_img47.jpeg)


**VerticalLineStyle**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="Line" x:Key="lineStyle">

            <Setter Property="StrokeDashArray" Value="10,5"/>

            <Setter Property="Stroke" Value="Red"/>

             <Setter Property="StrokeThickness" Value="1"/>

        </Style>
                
    </syncfusion:SfChart.Resources>

     <syncfusion:SfChart.Behaviors>

                <syncfusion:ChartCrosshairBehavior VerticalLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.Behaviors>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior Crosshair = new ChartCrosshairBehavior()
{

    VerticalLineStyle = chart.Resources["lineStyle"] as Style

};

chart.Behaviors.Add(Crosshair);

{% endhighlight %}

{% endtabs %}

![Cross hair line style in WinUI Chart](Interactive-Features_images/Interactive-Features_img48.jpeg)


## Horizontal axis label

The vertical line in contact with the x axes shows axis label. The horizontal axis label can be aligned using [`HorizontalAxisLabelAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_HorizontalAxisLabelAlignment) property.

Axis Label can be aligned by Near, Far, Center, Auto and None Options.

* [`Auto`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAlignment.html) – Axis label is aligned in Near/Far positions based on the movement of vertical line.

* [`Far`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAlignment.html) - Axis label is positioned far from the position of vertical line in cross hair.

* [`Near`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAlignment.html) - Axis label is near to the position of trackball.

* [`Center`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAlignment.html) - Axis label is aligned to the center of the vertical line. By default the axis label will positioned in center.

The following image demonstrates the horizontal axis label positioned center to the vertical line.

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img49.jpeg)


**Far**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartCrosshairBehavior HorizontalAxisLabelAlignment="Far ">

</syncfusion:ChartCrosshairBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior()
{

    HorizontalAxisLabelAlignment = ChartAlignment.Far

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img50.jpeg)


**Near**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartCrosshairBehavior HorizontalAxisLabelAlignment="Near ">

</syncfusion:ChartCrosshairBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior()
{

    HorizontalAxisLabelAlignment = ChartAlignment.Near

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img51.jpeg)


## Vertical axis label

Vertical axis label is displayed when the horizontal line in contact with x axis.The label can be aligned using [`VerticalAxisLabelAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartCrosshairBehavior.html#Syncfusion_UI_Xaml_Charts_ChartCrosshairBehavior_VerticalAxisLabelAlignment) property.

Axis Label can be aligned by Near, Far, Center, Auto, and None Options.

The following image demonstrates the horizontal axis label positioned center to the vertical line.

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img52.jpeg)


**Near**

{% tabs %}

{% highlight xml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartCrosshairBehavior VerticalAxisLabelAlignment="Near">

</syncfusion:ChartCrosshairBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior()
{

    VerticalAxisLabelAlignment = ChartAlignment.Near

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img53.jpeg)

**Far**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.Behaviors>

<syncfusion:ChartCrosshairBehavior VerticalAxisLabelAlignment="Far"  >

</syncfusion:ChartCrosshairBehavior>

</syncfusion:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

ChartCrosshairBehavior behavior = new ChartCrosshairBehavior()
{

    VerticalAxisLabelAlignment = ChartAlignment.Far

};

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}

![Axis label alignment support for cross hair in WinUI Chart](Interactive-Features_images/Interactive-Features_img54.jpeg)

## Customization of Crosshair axis labels

The default appearance of the Crosshair axis labels can be customized by using the [`CrosshairLabelTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartAxis.html#Syncfusion_UI_Xaml_Charts_ChartAxis_CrosshairLabelTemplateProperty) property of chart axis. It can be set as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>
    
    <chart:CategoryAxis ShowTrackballInfo="True">
        
        <chart:CategoryAxis.CrosshairLabelTemplate>
                
            <DataTemplate>
                            
                 <Border Background="Orange" 
                                   
                         CornerRadius="4" 
                                    
                          BorderThickness="1" BorderBrush="Black">

                 <TextBlock Margin="2" Text="{Binding ValueX}"/>
                            
                </Border>
                
            </DataTemplate>
             
        </chart:CategoryAxis.CrosshairLabelTemplate>
                
    </chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>
                
       <chart:NumericalAxis ShowTrackballInfo="True">
                    
            <chart:NumericalAxis.CrosshairLabelTemplate>
                        
                <DataTemplate>
                            
                    <Border Background="Orange" 
                                   
                            CornerRadius="4" 
                            
                             BorderThickness="1" 
                             
                             BorderBrush="Black">

                    <TextBlock  Margin="2" Text="{Binding ValueY}"/>
                   
                    </Border>
                        
                </DataTemplate>
            
            </chart:NumericalAxis.CrosshairLabelTemplate>
       
       </chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

<chart:SfChart.Behaviors>
       
    <chart:ChartCrosshairBehavior />
    
</chart:SfChart.Behaviors>

{% endhighlight %}

{% endtabs %}

![Crosshair axis labels customization in WinUI](Interactive-Features_images/CrosshairTemplate.png)