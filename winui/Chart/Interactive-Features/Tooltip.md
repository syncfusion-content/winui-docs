---
layout: post
title: Tooltip in WinUI Chart control | Syncfusion
description: Learn here all about Tooltip feature of Syncfusion WinUI Chart control. It is set to display the metadata of the particular segment or data point.
platform: WinUI
control: SfChart
documentation: ug
---

# Tooltip in WinUI Chart

The Tooltip feature allows you to display any information over a [`ChartSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeries.html#). It appears at the data point position when the mouse hovers over any chart segment. It is set to display the metadata of the particular segment or data point.

## Define Tooltip

By default, a small box containing the data points y values are displayed as the Tooltip. The y values vary depending on the [`ChartSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeries.html#). For example, a single y value is usually displayed in [`Column`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ColumnSeries.html#) and [`BarSeries`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.BarSeries.html#). 

The tooltip will be visible if you enable [`ShowTooltip`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_ShowTooltip) property as in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:ColumnSeries  ShowTooltip="True"                                                  

ItemsSource="{Binding Demands}" 

XBindingPath="Demand"  YBindingPath="Year2010"/>

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}" 

ShowTooltip="True"                           

XBindingPath="Demand"  YBindingPath="Year2011"/>           

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true

};

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011",

    ShowTooltip = true

};

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Tooltip support in WinUI Chart](Interactive-Features_images/Interactive-Features_img1.png)

## Customizing tooltip using ChartTooltipBehavior

The `ChartTooltipBehavior` is commonly used for all series to customize the tooltip. For customizing the tooltip, you can create an instance `ChartTooltipBehavior` and add it to the SfChart Behaviors collection.

The following properties are used to customize and configure tooltip which is available in the `ChartTooltipBehavior.`

* `EnableAnimation` - Used to enable the animation when showing the tooltip.
* `Style` - Used to customize the fill and stroke of the tooltip.
* `LabelStyle` - Used to customize the tooltip label.
* `HorizontalOffset` - Used to position the tooltip at a distance from the data point or cursor position horizontally.
* `VerticalOffset` - Used to position the tooltip at a distance from the data point or cursor position vertically.
* `HorizontalAlignment` - Used to align the tooltip label at left, right and center of the data point position or cursor position horizontally.
* `VerticalAlignment` - Used to align the tooltip label at top, center and bottom of the data point position or cursor position vertically.
* `ShowDuration` - Used to set the amount of time that the tooltip remains visible in milliseconds.
* `InitialShowDelay` - Used to delay in milliseconds to show the tooltip once the user interacts with series.

{% tabs %}

{% highlight xml %}

<chart:SfChart.Behaviors>

<chart:ChartTooltipBehavior/>                                                  

</chart:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();

ChartTooltipBehavior behavior = new ChartTooltipBehavior();

chart.Behaviors.Add(behavior);

{% endhighlight %}

{% endtabs %}


### Customizing the tooltip background

The tooltip's fill and stroke color can be customized using the `Style` property. To define a `Style` for tooltip, specify the style of `TargetType` as `Path.`

The following code example explains applying the style for tooltip.

{% tabs %}

{% highlight xml %}

<chart:SfChart.Resources>
    <Style TargetType="Path" x:Key="style">
       <Setter Property="Stroke" Value="Gray"/>
       <Setter Property="Fill" Value="Black"/>
    </Style>
</chart:SfChart.Resources>
...
<chart:SfChart.Behaviors>
    <chart:ChartTooltipBehavior LabelStyle = {StaticResource style}/>
</chart:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();
Style style = new Style(typeof(Path));
style.Setters.Add(new Setter(Path.StrokeProperty, new SolidColorBrush(Colors.Gray)));
style.Setters.Add(new Setter(Path.FillProperty, new SolidColorBrush(Colors.Black)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.Style = style;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip background style customization in WPF Chart](Interactive-Features_images/Interactive-Features_img2.png)

### Customizing the tooltip label style

The tooltip label style can be customized using the `LabelStyle` property. To define a `Style` for the tooltip label, specify the style of `TargetType` as `TextBlock.`

The following code example explains applying the style for a tooltip label.

{% tabs %}

{% highlight xml %}

<chart:SfChart.Resources>
    <Style TargetType="TextBlock" x:Key="labelStyle">
       <Setter Property="FontSize" Value="14"/>
       <Setter Property="Foreground" Value="Red"/>
    </Style>
</chart:SfChart.Resources>
...
<chart:SfChart.Behaviors>
   <chart:ChartTooltipBehavior LabelStyle = {StaticResource labelStyle}/>
</chart:SfChart.Behaviors>

{% endhighlight %}

{% highlight c# %}

SfChart chart = new SfChart();
Style labelStyle = new Style(typeof(TextBlock));
labelStyle.Setters.Add(new Setter(TextBlock.FontSizeProperty, 14d));
labelStyle.Setters.Add(new Setter(TextBlock.ForegroundProperty, new SolidColorBrush(Colors.Red)));
...
ChartTooltipBehavior tooltipBehavior = new ChartTooltipBehavior();
tooltipBehavior.LabelStyle = labelStyle;
chart.Behaviors.Add(tooltipBehavior);

{% endhighlight %}

{% endtabs %}

![Tooltip label style customization in WPF Chart](Interactive-Features_images/Interactive-Features_img3.png)

## Customizing tooltip using ChartTooltip attached properties

### Aligning the Tooltip

The tooltip can be aligned with respect to the cursor position using the [`HorizontalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#) and [`VerticalAlignment`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#) properties.

**HorizontalAlignment**

The following code example explains the positioning of tooltip to the left of the cursor.

{% tabs %}

{% highlight xaml %}

<Chart:ColumnSeries ShowTooltip="True" ItemsSource="{Binding Demands}"  

Chart:ChartTooltip.HorizontalAlignment="Left"

XBindingPath="Demand"  YBindingPath="Year2010" />

<Chart:ColumnSeries ItemsSource="{Binding Demands}" 

Chart:ChartTooltip.HorizontalAlignment="Left" ShowTooltip="True"

XBindingPath="Demand"  YBindingPath="Year2011"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true
    
};

ChartTooltip.SetHorizontalAlignment(series1, HorizontalAlignment.Left);

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011",

    ShowTooltip = true

};

ChartTooltip.SetHorizontalAlignment(series2, HorizontalAlignment.Left);

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Tooltip alignment support in WinUI Chart](Interactive-Features_images/Interactive-Features_img4.png)

N> By default the horizontal alignment is center for the tooltip.

**VerticalAlignment**

The following code example explains the positioning of tooltip to the bottom of the cursor.

{% tabs %}

{% highlight xaml %}

<Chart:ColumnSeries ShowTooltip="True" ItemsSource="{Binding Demands}"  

Chart:ChartTooltip.VerticalAlignment="Bottom"

XBindingPath="Demand" YBindingPath="Year2010" />

<Chart:ColumnSeries ItemsSource="{Binding Demands}"

Chart:ChartTooltip.VerticalAlignment="Bottom"

ShowTooltip="True" XBindingPath="Demand"  YBindingPath="Year2011"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true
    
};

ChartTooltip.SetVerticalAlignment(series1, VerticalAlignment.Bottom);

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011",

    ShowTooltip = true

};

ChartTooltip.SetVerticalAlignment(series2, VerticalAlignment.Bottom);

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Tooltip alignment support in WinUI Char](Interactive-Features_images/Interactive-Features_img5.png)


**TooltipMargin**

You can also set the distance for the margin to be positioned from the cursor using the TooltipMargin property as in the following code sample.

{% tabs %}

{% highlight xaml %}

<Chart:ColumnSeries Label="2010" ShowTooltip="True"

ItemsSource="{Binding Demands}"

Chart:ChartTooltip.TooltipMargin="25"

XBindingPath="Demand" YBindingPath="Year2010" />

<Chart:ColumnSeries Label="2011"  ItemsSource="{Binding Demands}"

Chart:ChartTooltip.TooltipMargin="25"

ShowTooltip="True" XBindingPath="Demand"  YBindingPath="Year2011"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true,

    Label = "2010"

};

ChartTooltip.SetTooltipMargin(series1, new Thickness(25));

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011",

    ShowTooltip = true,

    Label = "2011"

};

ChartTooltip.SetTooltipMargin(series2, new Thickness(25));

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![Margin for tooltip in WinUI Char](Interactive-Features_images/Interactive-Features_img6.png)


N>By default, the VerticalAlignment of the Tooltip is Top.

**VerticalOffset and HorizontalOffset**

The tooltip can be positioned at a particular distance from the cursor horizontally using the [`HorizontalOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#Syncfusion_UI_Xaml_Charts_ChartTooltip_SetHorizontalOffset_System_Windows_DependencyObject_System_Double_) and vertically using [`VerticalOffset`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#Syncfusion_UI_Xaml_Charts_ChartTooltip_SetVerticalOffset_System_Windows_DependencyObject_System_Double_) properties.

{% tabs %}

{% highlight xaml %}

<Chart:ColumnSeries ShowTooltip="True"

ItemsSource="{Binding Demands}" 

Chart:ChartTooltip.HorizontalOffset="40"

Chart:ChartTooltip.VerticalOffset="40"

XBindingPath="Demand" YBindingPath="Year2010" />

<Chart:ColumnSeries ItemsSource="{Binding Demands}"

Chart:ChartTooltip.HorizontalOffset="40"

Chart:ChartTooltip.VerticalOffset="40" ShowTooltip="True"

XBindingPath="Demand"  YBindingPath="Year2011"/>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true,

    Label = "2010"

};

ChartTooltip.SetHorizontalOffset(series1, 40);

ChartTooltip.SetVerticalOffset(series1, 40);

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011",

    ShowTooltip = true,

    Label = "2011"

};

ChartTooltip.SetHorizontalOffset(series2, 40);

ChartTooltip.SetVerticalOffset(series2, 40);

chart.Series.Add(series1);

chart.Series.Add(series2);

{% endhighlight %}

{% endtabs %}

![VerticalOffset and HorizontalOffset support for tooltip in WinUI Chart](Interactive-Features_images/Interactive-Features_img7.png)

### Tooltip duration

The attached property [`ShowDuration`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#Syncfusion_UI_Xaml_Charts_ChartTooltip_SetShowDuration_System_Windows_DependencyObject_System_Int32_) in [`ChartTooltip`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#) sets the duration time for tooltip to be displayed in milliseconds.

The following code example demonstrates the duration of the tooltip set as 5 seconds.

{% tabs %}

{% highlight xml %}

<Chart:ColumnSeries ShowTooltip="True"  

Chart:ChartTooltip.ShowDuration="5000"                                          

ItemsSource="{Binding Demands}"                                     

XBindingPath="Demand"  YBindingPath="Year2010">                                   

</Chart:ColumnSeries>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true,

    Label = "2010"

};

ChartTooltip.SetShowDuration(series, 5000);

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

N> The tooltip by default will be displayed for 1000 milliseconds.

**Show delay**

Tooltip also has support to delay the time to display by setting the [`SetInitialShowDelay`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#Syncfusion_UI_Xaml_Charts_ChartTooltip_SetInitialShowDelay_System_Windows_DependencyObject_System_Int32_) property in milliseconds.

The following code example demonstrates the tooltip will be delayed for 1 second at the before display.

{% tabs %}

{% highlight xml %}

<Chart:ColumnSeries Label="2010" ShowTooltip="True"  

Chart:ChartTooltip.InitialShowDelay="1000"                                          

ItemsSource="{Binding Demands}"                                     

XBindingPath="Demand"  YBindingPath="Year2010" />                                   

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true,

    Label = "2010"

};

ChartTooltip.SetInitialShowDelay(series, 1000);

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

### Animation for Tooltip

You can also provide animation effects for tooltip by setting the [`EnableAnimation`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartTooltip.html#Syncfusion_UI_Xaml_Charts_ChartTooltip_SetEnableAnimation_System_Windows_UIElement_System_Boolean_) property to true as shown in the following code snippet.

{% tabs %}

{% highlight xml %}

<Chart:ColumnSeries Label="2010" ShowTooltip="True"  

Chart:ChartTooltip.EnableAnimation="True"                                          

ItemsSource="{Binding Demands}"                                     

XBindingPath="Demand"  YBindingPath="Year2010">                                   

</Chart:ColumnSeries>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    ShowTooltip = true,

    Label = "2010"

};

ChartTooltip.SetEnableAnimation(series, true);

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

### Customizing the Appearance

The [`TooltipTemplate`](https://help.syncfusion.com/cr/WinUI/Syncfusion.UI.Xaml.Charts.ChartSeriesBase.html#Syncfusion_UI_Xaml_Charts_ChartSeriesBase_TooltipTemplate) property allows you to customize the default appearance of the tooltip as explained in the following code snippet.

{% tabs %}

{% highlight xaml %}

...
<chart:SfChart.Resources>
    <DataTemplate x:Key="tooltipTemplate1">
        <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding Item.Demand}"
                Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text=" : " Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text="{Binding Item.Year2010}"
                Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
        </StackPanel>
    </DataTemplate>

    <DataTemplate x:Key="tooltipTemplate2">
        <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding Item.Demand}"
                Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text=" : " Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
            <TextBlock Text="{Binding Item.Year2011}"
                Foreground="Black" FontWeight="Medium" FontSize="12" HorizontalAlignment="Center" VerticalAlignment="Center"/>
        </StackPanel>
    </DataTemplate>

    <Style TargetType="Path" x:Key="style">
        <Setter Property="Stroke" Value="Black"/>
        <Setter Property="Fill" Value="LightGreen"/>
        <Setter Property="StrokeThickness" Value="2"/>
    </Style>
</chart:SfChart.Resources>
...

<chart:ColumnSeries ShowTooltip="True" ItemsSource="{Binding Demands}"
    XBindingPath="Demand" YBindingPath="Year2010" 
    TooltipTemplate="{StaticResource tooltipTemplate1}">
</chart:ColumnSeries>

<chart:ColumnSeries  ItemsSource="{Binding Demands}"
    ShowTooltip="True" XBindingPath="Demand"  YBindingPath="Year2011"
    TooltipTemplate="{StaticResource tooltipTemplate2}">
</chart:ColumnSeries>
...
<chart:SfChart.Behaviors>
    <chart:ChartTooltipBehavior Style="{StaticResource style}"/>
</chart:SfChart.Behaviors>
...

{% endhighlight %}

{% highlight c# %}

...

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = Demands,
    XBindingPath = "Demand",
    YBindingPath = "Year2010",
    Label = "2010",
    ShowTooltip = true,
    TooltipTemplate = chart.Resources["tooltipTemplate1"] as DataTemplate,

};

ColumnSeries series2 = new ColumnSeries()
{

    ItemsSource = Demands,
    XBindingPath = "Demand",
    YBindingPath = "Year2011",
    Label = "2011",
    ShowTooltip = true,
    TooltipTemplate = chart.Resources["tooltipTemplate2"] as DataTemplate,

};

chart.Series.Add(series1);
chart.Series.Add(series2);

...
        
{% endhighlight %}

{% endtabs %}

![Tooltip customization support in WinUI Chart](Interactive-Features_images/Interactive-Features_img8.png)

N> The `ChartTooltipBehavior` is commonly used for all series to customize the tooltip. You can use the attached `ChartTooltip` properties in a series if you need to customize the appearance of the tooltip based on a particular series. Series attached properties are considered as a high precedence.
