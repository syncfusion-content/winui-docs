---
layout: post
title: Tick features in Syncfusion WinUI Slider
description: This section explains about how to show minor and major ticks and also to customize them in the Slider.
platform: WinUI
control: SfSlider
documentation: ug
---

# Ticks Features in WinUI Slider

This section explains how to add major and minor ticks in the slider.

## Show Major Ticks

You can enable the major ticks on the track. It is a shape, which is used to represent the major interval points of the track. The default value of [`ShowTicks`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowTicks) property is false.

For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 10, and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 2, the RangeSlider will render the major ticks at 0, 2, 4 and so on.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 MinorTicksPerInterval="0"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.MinorTicksPerInterval = 0;
sfSlider.Value = 4;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-ticks.png)

## Show Minor Ticks

It is used to represent the number of smaller ticks between two major ticks. 
For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 10 and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 2, the RangeSlider will render the major ticks as 0, 2, 4 and so on. If [`MinorTicksPerInterval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTicksPerInterval) is 1, then smaller ticks will be rendered as 1, 3 and so on. The default value of [`MinorTicksPerInterval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTicksPerInterval) property is 1.


{% tabs %}

{% highlight xaml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 MinorTicksPerInterval="2"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.MinorTicksPerInterval = 2;
sfSlider.Value = 4;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-minorTicksPerInterval.png)

## Tick Length

You can change the major and minor ticks length of the slider using the [`MajorTickLength`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MajorTickLength) and [`MinorTickLength`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTickLength) properties respectively. The default value of [`MajorTickLength`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MajorTickLength) and [`MinorTickLength`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTickLength) properties are 10 and 5 respectively.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 MinorTicksPerInterval="2"
                 MajorTickLength="15"
                 MinorTickLength="10"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.Value = 4;
sfSlider.MinorTicksPerInterval = 2;
sfSlider.MajorTickLength = 15;
sfSlider.MinorTickLength = 10;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-majorMinorTickLength.png)

## Tick Placement

The [`TickPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickPlacement) property is used to place the ticks either before or after the track. The default value of the [`TickPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickPlacement) property is [`Placement.After`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.Placement.html#Syncfusion_UI_Xaml_Sliders_Placement_After).

{% tabs %}

{% highlight xaml %}

<slider:SfSlider ShowTicks="True"
                 TickPlacement="Before"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.TickPlacement = Placement.Before;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with tick placement customization](images/ticks/slider-tickPlacement.png)

## Ticks Offset

You can adjust the space between track and ticks of the slider using the [`TickOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickOffset) property. The default value of the [`TickOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickOffset) property is 0.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Minimum="0"
                 Maximum="10"
                 Interval="2"
                 Value="4"
                 MinorTicksPerInterval="2"
                 TickOffset="10"
                 ShowTicks="True"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Minimum = 0;
sfSlider.Maximum = 10;
sfSlider.Interval = 2;
sfSlider.Value = 4;
sfSlider.MinorTicksPerInterval = 2;
sfSlider.TickOffset = 10;
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-tickOffset.png)

## Tick Style

**Setting a Style for Major and Minor Ticks**

The [`MajorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MajorTickStyle) and [`MinorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTickStyle) properties allows you to define the style for the major and minor tick’s respectively as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Style x:Key="MajorTickStyle"
       TargetType="Line">
    <Setter Property="Stroke"
            Value="Red" />
    <Setter Property="StrokeThickness"
            Value="1.5" />
    <Setter Property="StrokeDashArray"
            Value="1,1" />
</Style>
<Style x:Key="MinorTickStyle"
       TargetType="Line">
    <Setter Property="Stroke"
            Value="Green" />
    <Setter Property="StrokeThickness"
            Value="1.5" />
    <Setter Property="StrokeDashArray"
            Value="1,1" />
</Style>

<slider:SfSlider ShowTicks="True"
                 Interval="10"
                 Value="50"
                 MajorTickStyle="{StaticResource MajorTickStyle}"
                 MinorTickStyle="{StaticResource MinorTickStyle}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.Interval = 10;
sfSlider.Value = 50;
sfSlider.MajorTickStyle = this.Resources["MajorTickStyle"] as Style;
sfSlider.MinorTickStyle = this.Resources["MinorTickStyle"] as Style;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-majorMinorTickStyle.png)

**Setting a Active Style for Major and Minor Ticks**

The [`ActiveMajorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveMajorTickStyle) and [`ActiveMinorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveMinorTickStyle) properties allows you to define the active style for the major and minor tick’s respectively as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<Style x:Key="ActiveMajorTickStyle"
       TargetType="Line">
    <Setter Property="Stroke"
            Value="{ThemeResource SystemAccentColor}" />
    <Setter Property="StrokeThickness"
            Value="1.5" />
</Style>

<Style x:Key="ActiveMinorTickStyle"
       TargetType="Line">
    <Setter Property="Stroke"
            Value="{ThemeResource SystemAccentColor}" />
    <Setter Property="StrokeThickness"
            Value="1" />
</Style>

<slider:SfSlider ShowTicks="True"
                 Interval="5"
                 Value="50"
                 ActiveMajorTickStyle="{StaticResource ActiveMajorTickStyle}"
                 ActiveMinorTickStyle="{StaticResource ActiveMinorTickStyle}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.Interval = 5;
sfSlider.Value = 50;
sfSlider.ActiveMajorTickStyle = this.Resources["ActiveMajorTickStyle"] as Style;
sfSlider.ActiveMinorTickStyle = this.Resources["ActiveMinorTickStyle"] as Style;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with ticks](images/ticks/slider-activeMajorMinorTickStyle.png)