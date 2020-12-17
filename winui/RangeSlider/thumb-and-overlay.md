---
layout: post
title: Thumb features in Syncfusion WinUI Range Slider
description: This article describes about how to customize the thumb and thumb overlay of syncfusion Range Slider control in WinUI platform.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Thumb and Thumb Overlay Features in Range Slider

This section helps to learn about how to customize the thumb and thumb overlay in the range slider.

Thumb - It is one of the elements of range slider which can be used to drag and change the selected value of the range slider.
Thumb overlay - It is rendered around the thumb while interacting with them.

## Thumb Type

You can change the thumb type using the `ThumbType` property. The default value of `ThumbType` is `ThumbType.Circle`.


{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbType="Oval" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbType = ThumbType.Oval;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb type customization](images/thumb-and-overlay/slider-thumbtype.png)

## Thumb Height and Width

You can change the thumb height and width of the range slider using `ThumbHeight` and `ThumbWidth` properties respectively. The default values of both properties are 20.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbHeight="30"
                      ThumbWidth="30"
                      ActiveTrackHeight="8"
                      InactiveTrackHeight="8" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbWidth = 30;
sfRangeSlider.ActiveTrackHeight = 8;
sfRangeSlider.InactiveTrackHeight = 8;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb height and width customization](images/thumb-and-overlay/slider-thumbHeightWidth.png)

## Thumb Background

You can change the thumb background of the range slider using the `ThumbBackground` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#2A934D" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb background customization](images/thumb-and-overlay/slider-thumbbackground.png)

## Thumb Hover Background

You can change the thumb hover background of the range slider using the `ThumbHoverBackground` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#33b35c"
                      ThumbHoverBackground="#009688" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));
sfRangeSlider.ThumbHoverBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 51, 179, 92));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb hover background customization](images/thumb-and-overlay/slider-thumbhoverbackground.png)

## Thumb Pressed Background

You can change the thumb pressed background of the range slider using the `ThumbPressedBackground` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbBackground="#33b35c"
                      ThumbHoverBackground="#009688"
                      ThumbPressedBackground="#288e49" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 42, 147, 77));
sfRangeSlider.ThumbHoverBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 51, 179, 92));
sfRangeSlider.ThumbPressedBackground = new SolidColorBrush(ColorHelper.FromArgb(255, 40, 142, 73));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb pressed background customization](images/thumb-and-overlay/slider-thumbpressedbackground.png)

## Thumb Style

The `ThumbStyle` property allows you to define the style for the thumb as shown in the following code example.

{% tabs %}

{% highlight xml %}

<coreconverters:FormatStringConverter x:Key="FormatStringConverter" />

<Style x:Name="thumbStyle"
       TargetType="Thumb">
    <Setter Property="BorderBrush"
            Value="WhiteSmoke" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="Thumb">
                <Grid>
                    <Ellipse Height="{TemplateBinding Height}"
                             Width="{TemplateBinding Width}"
                             Fill="{TemplateBinding BorderBrush}"
                             Stroke="{TemplateBinding Background}"
                             StrokeThickness="2" />
                    <TextBlock Text="{Binding Converter={StaticResource FormatStringConverter},
                                              ConverterParameter='N0'}"
                               FontSize="14"
                               Margin="0,0,0,2"
                               HorizontalTextAlignment="Center"
                               VerticalAlignment="Center" />
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
    
<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="False"
                      ThumbHeight="30"
                      ThumbWidth="30"
                      ThumbStyle="{StaticResource thumbStyle}" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = false;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbHeight = 30;
sfRangeSlider.ThumbStyle = this.Resources["thumbStyle"] as Style;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with thumb style customization](images/thumb-and-overlay/slider-thumbstyle.png)

N> Its DataContext is current value of thumb.

## Thumb Overlay Radius

The `ThumbOverlayRadius` property allows you to define the radius for the overlay as shown in the following code example. The default value of `ThumbOverlayRadius` property is 10.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ShowToolTip="False"
                      ThumbOverlayRadius="20" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowToolTip = false;
sfRangeSlider.ThumbOverlayRadius = 20;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with overlay radius customization](images/thumb-and-overlay/slider-thumboverlayradius.png)

## Thumb Overlay Fill

The `ThumbOverlayFill` property allows you to define the fill color for the overlay as shown in the following code example.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbOverlayFill="Red" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ThumbOverlayFill = new SolidColorBrush(Colors.Red);
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with overlay fill customization](images/thumb-and-overlay/slider-thumboverlayfill.png)

N> Overlay effects displayed with 0.3 opacity.

## Events

**ThumbDragStarted**

The `ThumbDragStarted` event occurs when the thumb dragging started.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbDragStarted="SfRangeSlider_ThumbDragStarted" />

{% endhighlight %}

{% highlight c# %}

private void SfRangeSlider_ThumbDragStarted(object sender, DragStartedEventArgs e)
{
    //Perform action here.
}

{% endhighlight %}

{% endtabs %}

**ThumbDragCompleted**

The `ThumbDragCompleted` event occurs Event raised when the thumb dragged completed.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      ThumbDragCompleted="SfRangeSlider_ThumbDragCompleted" />

{% endhighlight %}

{% highlight c# %}

private void SfRangeSlider_ThumbDragCompleted(object sender, DragCompletedEventArgs e)
{
    //Perform action here.
}

{% endhighlight %}

{% endtabs %}