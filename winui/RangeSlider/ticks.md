---
layout: post
title: Tick features in Syncfusion WinUI Range Slider
description: This section explains about how to show minor and major ticks and also to customize them in the RangeSlider.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Ticks Features in WinUI Range Slider

This section explains how to add major and minor ticks in the RangeSlider.

## Show Major Ticks

You can enable the major ticks on the track. It is a shape, which is used to represent the major interval points of the track. The default value of [`ShowTicks`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowTicks) property is false.

For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 10, and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 2, the RangeSlider will render the major ticks at 0, 2, 4 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      MinorTicksPerInterval="0"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.MinorTicksPerInterval = 0;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-ticks.png)

## Show Minor Ticks

It is used to represent the number of smaller ticks between two major ticks. For example, if [`Minimum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Minimum) is 0, [`Maximum`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Maximum) is 10 and [`Interval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_Interval) is 2, the RangeSlider will render the major ticks as 0, 2, 4 and so on. If [`MinorTicksPerInterval`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTicksPerInterval) is 1, then smaller ticks will be rendered as 1, 3 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      MinorTicksPerInterval="2"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.MinorTicksPerInterval = 2;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-minorTicksPerInterval.png)

## Tick Length

You can change the major and minor ticks length of the range slider using the MajorTickLength and MinorTickLength properties respectively. The default value of MajorTickLength and MinorTickLength properties are 10 and 5 respectively.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      MinorTicksPerInterval="2"
                      MajorTickLength="15"
                      MinorTickLength="10"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.MinorTicksPerInterval = 2;
sfRangeSlider.MajorTickLength = 15;
sfRangeSlider.MinorTickLength = 10;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-majorMinorTickLength.png)

## Tick Placement

The [`TickPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickPlacement) property is used to place the ticks either before or after the track. The default value of the [`TickPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickPlacement) property is [`Placement.After`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.Placement.html#Syncfusion_UI_Xaml_Sliders_Placement_After).

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider ShowTicks="True"
                      TickPlacement="Before"
                      RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowTicks = true;
sfRangeSlider.TickPlacement = Placement.Before;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with tick placement customization](images/ticks/slider-tickPlacement.png)

## Ticks Offset

You can adjust the space between track and ticks of the range slider using the [`TickOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickOffset) property. The default value of the [`TickOffset`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_TickOffset) property is 0.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider Minimum="0"
                      Maximum="10"
                      Interval="2"
                      RangeStart="2"
                      RangeEnd="8"
                      MinorTicksPerInterval="2"
                      TickOffset="10"
                      ShowTicks="True"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.Minimum = 0;
sfRangeSlider.Maximum = 10;
sfRangeSlider.Interval = 2;
sfRangeSlider.RangeStart = 2;
sfRangeSlider.RangeEnd = 8;
sfRangeSlider.MinorTicksPerInterval = 2;
sfRangeSlider.TickOffset = 10;
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-tickOffset.png)

## Tick Style

**Setting a Style for Major and Minor Ticks**

The [`MajorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MajorTickStyle) and [`MinorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_MinorTickStyle) properties allows you to define the style for the major and minor tick’s respectively as shown in the following code example.

{% tabs %}

{% highlight xml %}

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

<slider:SfRangeSlider ShowTicks="True"
                      Interval="10"
                      RangeStart="30"
                      RangeEnd="70"
                      MajorTickStyle="{StaticResource MajorTickStyle}"
                      MinorTickStyle="{StaticResource MinorTickStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowTicks = true;
sfRangeSlider.Interval = 10;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.MajorTickStyle = this.Resources["MajorTickStyle"] as Style;
sfRangeSlider.MinorTickStyle = this.Resources["MinorTickStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-majorMinorTickStyle.png)

**Setting a Active Style for Major and Minor Ticks**

The [`ActiveMajorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveMajorTickStyle) and [`ActiveMinorTickStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ActiveMinorTickStyle) properties allows you to define the active style for the major and minor tick’s respectively as shown in the following code example.

{% tabs %}

{% highlight xml %}

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

<slider:SfRangeSlider ShowTicks="True"
                      Interval="5"
                      RangeStart="30"
                      RangeEnd="70"
                      ActiveMajorTickStyle="{StaticResource ActiveMajorTickStyle}"
                      ActiveMinorTickStyle="{StaticResource ActiveMinorTickStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowTicks = true;
sfRangeSlider.Interval = 5;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ActiveMajorTickStyle = this.Resources["ActiveMajorTickStyle"] as Style;
sfRangeSlider.ActiveMinorTickStyle = this.Resources["ActiveMinorTickStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with ticks](images/ticks/slider-activeMajorMinorTickStyle.png)