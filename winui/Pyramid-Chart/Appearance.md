---
layout: post
title: Appearance in WinUI Chart Control | Syncfusion
description: This section explains how to apply palettes and gradients in the Syncfusion® WinUI Chart (SfPyramidChart) control.
platform: WinUI
control: SfPyramidChart
documentation: ug
---

# Appearance in WinUI Chart (SfPyramidChart)

The appearance of the [SfPyramidChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html) can be customized using a predefined palette, custom palette, and gradient, which allows enhancing the application.

## Predefined PaletteBrushes

Currently, the [SfPyramidChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html) supports only one predefined [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_PaletteBrushes), and it is the default brush for the SfPyramidChart. The following screenshot shows the default appearance of the pyramid chart.

{% tabs %}

{% highlight xaml %}

<chart:SfPyramidChart x:Name="chart" 
                      ItemsSource="{Binding Data}" 
                      XBindingPath="Category"
                      YBindingPath="Value">

</chart:SfPyramidChart>

{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
. . .
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Predefined palette in WinUI Chart](Appearance_images/WinUI_chart_predefined_palette.png)

## Custom PaletteBrushes

The [SfPyramidChart](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html) provides support to define custom brushes for the chart in a preferred order using the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_PaletteBrushes) property, as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Grid>
    <Grid.Resources>
        <BrushCollection x:Key="customBrushes">
            <SolidColorBrush Color="#4dd0e1"/>
            <SolidColorBrush Color="#26c6da"/>
            <SolidColorBrush Color="#00bcd4"/>
            <SolidColorBrush Color="#00acc1"/>
            <SolidColorBrush Color="#0097a7"/>
            <SolidColorBrush Color="#00838f"/>
        </BrushCollection>
    </Grid.Resources>

     <chart:SfPyramidChart x:Name="chart" 
                           Palette="Custom" 
                           ItemsSource="{Binding Data}" 
                           XBindingPath="Category"
                           YBindingPath="Value"
                           PaletteBrushes="{StaticResource customBrushes}">
     . . .
    </chart:SfPyramidChart>
</Grid>
{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
...
List<Brush> CustomBrushes = new List<Brush>();
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 77, 208, 225)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 38, 198, 218)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 188, 212)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 172, 193)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 151, 167)));
CustomBrushes.Add(new SolidColorBrush(Color.FromArgb(255, 0, 131, 143)));

chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.PaletteBrushes = CustomBrushes;

. . .            
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Custom palette in WinUI Chart](Appearance_images/WinUI_chart_custom_palette.png)

## Applying Gradient

Gradients for the pyramid chart can be set using the [PaletteBrushes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Charts.SfPyramidChart.html#Syncfusion_UI_Xaml_Charts_SfPyramidChart_PaletteBrushes) property of the pyramid chart with the help of the `LinearGradientBrush` or `RadialGradientBrush`.

{% tabs %}

{% highlight xaml %}

<Grid>
    <Grid.Resources>
        <BrushCollection x:Key="customBrushes">
            <LinearGradientBrush>
                    <GradientStop Offset="1" Color="#FFE7C7" />
                    <GradientStop Offset="0" Color="#FCB69F" />
                </LinearGradientBrush>
                <LinearGradientBrush>
                    <GradientStop Offset="1" Color="#fadd7d" />
                    <GradientStop Offset="0" Color="#fccc2d" />
                </LinearGradientBrush>
                <LinearGradientBrush>
                    <GradientStop Offset="1" Color="#DCFA97" />
                    <GradientStop Offset="0" Color="#96E6A1" />
                </LinearGradientBrush>
                <LinearGradientBrush>
                    <GradientStop Offset="1" Color="#DDD6F3" />
                    <GradientStop Offset="0" Color="#FAACA8" />
                </LinearGradientBrush>
                <LinearGradientBrush>
                    <GradientStop Offset="1" Color="#A8EAEE" />
                    <GradientStop Offset="0" Color="#7BB0F9" />
                </LinearGradientBrush>
        </BrushCollection>
    </Grid.Resources>

     <chart:SfPyramidChart x:Name="chart" 
                           Palette="Custom" 
                           ItemsSource="{Binding Data}" 
                           XBindingPath="Category"
                           YBindingPath="Value"
                           PaletteBrushes="{StaticResource customBrushes}">
     . . .
    </chart:SfPyramidChart>
</Grid>
{% endhighlight %}

{% highlight c# %}

SfPyramidChart chart = new SfPyramidChart();
...
List<Brush> customBrushes = new List<Brush>();
LinearGradientBrush gradientColor1 = new LinearGradientBrush();
GradientStop stop1 = new GradientStop() { Offset = 1, Color = Color.FromArgb(255, 255, 231, 199) };
GradientStop stop2 = new GradientStop() { Offset = 0, Color = Color.FromArgb(255, 252, 182, 159) };
gradientColor1.GradientStops.Add(stop1);
gradientColor1.GradientStops.Add(stop2);
LinearGradientBrush gradientColor2 = new LinearGradientBrush();
stop1 = new GradientStop() { Offset = 1, Color = Color.FromArgb(255, 250, 221, 125) };
stop2 = new GradientStop() { Offset = 0, Color = Color.FromArgb(255, 252, 204, 45) };
gradientColor2.GradientStops.Add(stop1);
gradientColor2.GradientStops.Add(stop2);
...
customBrushes.Add(gradientColor1);
customBrushes.Add(gradientColor2);

chart.SetBinding(SfPyramidChart.ItemsSourceProperty, new Binding() { Path = new PropertyPath("Data") });
chart.XBindingPath = "Category";
chart.YBindingPath = "Value";
chart.PaletteBrushes = CustomBrushes;

. . .            
this.Content = chart;

{% endhighlight %}

{% endtabs %}

![Gradient support in WinUI Chart](Appearance_images/WinUI_chart_gradient_color.png)
