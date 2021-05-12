---
layout: post
title: ToolTip in WinUI Slider control | Syncfusion
description: Learn here all about ToolTip feature of Syncfusion WinUI Slider(SfSlider) control with style, placement support and more.
platform: WinUI
control: SfSlider
documentation: ug
---

# ToolTip in WinUI Slider

This section explains how to add the tooltip in the Slider.

## Show Tooltip

You can enable tooltip for the thumb using the [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property of Slider. It is used to indicate the current selection of the value during interaction. The default value of [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property is true.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider with Tooltip](images/tooltip/winui-slider-tooltip.png)

## Tooltip Text Format

The [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property allows to customize the axis label with the globalized label format. The default value of [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property is N2.

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipFormat="c" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipFormat = "c";
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Tooltip Format of WinUI Slider](images/tooltip/winui-slider-tooltip-format.png)

## Tooltip Placement

The [`ToolTipPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipPlacement) property is used to place the tooltip either before or after the track. The default value of the [`ToolTipPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipPlacement) property is [`Placement.Before`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.Placement.html#Syncfusion_UI_Xaml_Sliders_Placement_Before).

{% tabs %}

{% highlight xaml %}

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipPlacement="After" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipPlacement = Placement.After;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Tooltip Position of WinUI Slider](images/tooltip/winui-slider-tooltip-position.png)

## Tooltip Style

The [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property allows you to define the style for the slider tooltip as shown in the following code example. The default value of [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property is null.

{% tabs %}

{% highlight xaml %}

<Style x:Name="ToolTipStyle"
       TargetType="slider:SliderToolTip">
    <Setter Property="Background"
            Value="#1257eb" />
    <Setter Property="Foreground"
            Value="White" />
</Style>

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipStyle="{StaticResource ToolTipStyle}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipStyle = this.Resources["ToolTipStyle"] as Style;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Changing Tooltip Style of WinUI Slider](images/tooltip/winui-slider-tooltip-style.png)

## Tooltip Template

The [`ToolTipTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipTemplate) property allows you to define the data template for the slider tooltip as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Name="ToolTipTemplate">
    <StackPanel Orientation="Horizontal">
        <TextBlock Text="Current Value : "
                   Margin="0,0,5,0" />
        <TextBlock Text="{Binding ToolTipText}" />
    </StackPanel>
</DataTemplate>

<slider:SfSlider Value="50"
                 ShowToolTip="True"
                 ToolTipTemplate="{StaticResource ToolTipTemplate}" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.ShowToolTip = true;
sfSlider.ToolTipTemplate = this.Resources["ToolTipTemplate"] as DataTemplate;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![WinUI Slider with tooltip Template](images/tooltip/winui-slider-tooltip-template.png)

N> Its DataContext is [`SliderToolTipInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderToolTipInfo.html).
