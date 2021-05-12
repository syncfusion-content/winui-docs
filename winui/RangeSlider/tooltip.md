---
layout: post
title: ToolTip in WinUI RangeSlider control | Syncfusion
description: Learn about ToolTip support in Syncfusion WinUI RangeSlider(SfRangeSlider) control with placement and more.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# ToolTip in WinUI RangeSlider (Range Slider)

This section explains how to add the tooltip in the RangeSlider.

## Show Tooltip

You can enable tooltip for the thumb using the [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property of RangeSlider. It is used to indicate the current selection of the value during interaction. The default value of [`ShowToolTip`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ShowToolTip) property is true.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![WinUI RangeSlider with Tooltip](images/tooltip/winui-range-slider-tooltip.png)

## Tooltip Option

You can display tooltip for either active thumb or both thumb (RangeStart and RangeEnd) using the [`ToolTipOption`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_ToolTipOption) property of the RangeSlider. The default value of the [`ToolTipOption`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SfRangeSlider.html#Syncfusion_UI_Xaml_Sliders_SfRangeSlider_ToolTipOption) property is [`ToolTipOption.BothThumb`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.TooltipOption.html#Syncfusion_UI_Xaml_Sliders_TooltipOption_BothThumb).

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ToolTipOption="ActiveThumb" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ToolTipOption = ToolTipOption.ActiveThumb;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Tooltip Option of WinUI RangeSlider](images/tooltip/winui-range-slider-tooltip-option.png)

## Tooltip Text Format

The [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property allows to customize the axis label with the globalized label format. The default value of [`ToolTipFormat`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipFormat) property is N2.

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipFormat="c" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipFormat = "c";
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Tooltip Text Format of WinUI RangeSlider](images/tooltip/winui-range-slider-tooltip-text-format.png)

## Tooltip Placement

The [`ToolTipPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipPlacement) property is used to place the tooltip either before or after the track. The default value of the [`ToolTipPlacement`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipPlacement) property is [`Placement.Before`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.Placement.html#Syncfusion_UI_Xaml_Sliders_Placement_Before).

{% tabs %}

{% highlight xaml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipPlacement="After" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipPlacement = Placement.After;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Customizing Tooltip Position of WinUI RangeSlider](images/tooltip/winui-range-slider-tooltip-position.png)

## Tooltip Style

The [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property allows you to define the style for the range slider tooltip as shown in the following code example. The default value of [`ToolTipStyle`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipStyle) property is null.

{% tabs %}

{% highlight xaml %}

<Style x:Name="ToolTipStyle"
       TargetType="slider:SliderToolTip">
    <Setter Property="Background"
            Value="#1257eb" />
    <Setter Property="Foreground"
            Value="White" />
</Style>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipStyle="{StaticResource ToolTipStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipStyle = this.Resources["ToolTipStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Changing Tooltip Style of WinUI RangeSlider](images/tooltip/winui-range-slider-tooltip-style.png)

## Tooltip Template

The [`ToolTipTemplate`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.SliderBase.html#Syncfusion_UI_Xaml_Sliders_SliderBase_ToolTipTemplate) property allows you to define the data template for the range slider tooltip as shown in the following code example.

{% tabs %}

{% highlight xaml %}

<DataTemplate x:Name="ToolTipTemplate">
    <StackPanel Orientation="Horizontal">
        <TextBlock Text="{Binding RangeStartValue}" />
        <TextBlock Text=":"
                   Margin="5,0,5,0" />
        <TextBlock Text="{Binding RangeEndValue}" />
    </StackPanel>
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="True"
                      ToolTipTemplate="{StaticResource ToolTipTemplate}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = true;
sfRangeSlider.ToolTipTemplate = this.Resources["ToolTipTemplate"] as DataTemplate;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![WinUI RangeSlider with Tooltip Template](images/tooltip/winui-range-slider-tooltip-template.png)

N> Its DataContext is [`RangeSliderToolTipInfo`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Sliders.RangeSliderToolTipInfo.html).
