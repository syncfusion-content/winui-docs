---
layout: post
title: Tooltip features in Syncfusion WinUI Range Slider
description: This article describes about how to show tooltip, and customize its appearance of syncfusion Range Slider control in WinUI platform.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Tooltip features in Flutter range slider

This section helps to learn about how to add tooltip in the range slider.

## Show tooltip

You can enable tooltip for the thumb using `ShowToolTip` property of range slider. It is used to clearly indicate the current selection of the value during interaction. The default value of `ShowToolTip` property is true.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip](images/tooltip/slider-tooltip.png)

## Tooltip option

You can display tooltip for either active thumb or both thumb using `ToolTipOption` property of range slider. The default value of `ToolTipOption` property is `ToolTipOption.Both`.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip option customization](images/tooltip/slider-tooltipoption.png)

## Tooltip text format

The `ToolTipFormat` property allows to customize the axis label with the globalized label format. The default value of `ToolTipFormat` property is N2.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip format customization](images/tooltip/slider-tooltipformat.png)

## Tooltip placement

The `ToolTipPlacement` property is used to place the tooltip either before or after the track. The default value of the `ToolTipPlacement` property is `Placement.Before`.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip placement customization](images/tooltip/slider-tooltipplacement.png)

## Tooltip style

The `ToolTipStyle` property allows you to define the style for the range slider tooltip as shown in the following code example. The default value of `ToolTipStyle` property is null.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip style](images/tooltip/slider-tooltipstyle.png)

## Tooltip template

The `ToolTipTemplate` property allows you to define the data template for the range slider tooltip as shown in the following code example.

{% tabs %}

{% highlight xml %}

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

![Range slider with tooltip template](images/tooltip/slider-tooltiptemplate.png)

N> Its DataContext is `RangeSliderToolTipInfo`.