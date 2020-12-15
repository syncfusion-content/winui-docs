---
layout: post
title: Label features in Syncfusion WinUI Range Slider
description: This section explains about how to show labels, divisors and how to customize them in the WinUI range slider.
platform: WinUI
control: SfRangeSlider
documentation: ug
---

# Labels and divisors in the range slider

This section explains about how to add the labels and divisors in the range slider.

## Show labels

The `ShowLabels` property is used to render the labels on given `Interval`. The default value of `ShowLabels` property is false.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider ShowLabels="True"
                      RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowLabels = true;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with labels](images/labels-and-divisors/slider-labels.png)

## Maximum number of labels per 100 logical pixels

By default, a maximum of three labels are displayed for each 100 logical pixels in range slider. The maximum number of labels that should present within 100 logical pixels length can be customized using the `MaximumLabelsCount` property of the range slider. This property is applicable only for automatic range calculation and will not work if you set value for `Interval` property of a range slider.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      MaximumLabelsCount="1"
                      ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.MaximumLabelsCount = 1;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.ShowLabels = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with maximum labels count](images/labels-and-divisors/slider-maximumLabelsCount.png)

## Label placement

The `labelPlacement` property is used to place the labels either before or after the track. The default value of the `LabelPlacement` property is `Placement.After`.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider ShowLabels="True"
                      RangeStart="30"
                      RangeEnd="70"
                      LabelPlacement="Before" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowLabels = true;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.LabelOffset = Placement.Before;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with labels placement customization](images/labels-and-divisors/slider-labelPlacement.png)

## Label offset

You can adjust the space between ticks and labels of the slider using the `LabelOffset` property. The default value of `LabelOffset` property is 5.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider ShowTicks="True"
                      ShowLabels="True"
                      RangeStart="30"
                      RangeEnd="70"
                      LabelOffset="10" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowTicks = true;
sfRangeSlider.ShowLabels = true;
sfRangeSlider.LabelOffset = 10;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with labels offset customization](images/labels-and-divisors/slider-labelOffset.png)

## Label template

**Setting template for labels**

The `LabelTemplate` property allows you to define the data template for the label’s like the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="TrackLabelTemplate">
    <Grid CornerRadius="5"
          Background="{ThemeResource SystemBaseLowColor}">
        <TextBlock Text="{Binding Text}"
                   Margin="6" />
    </Grid>
</DataTemplate>

<slider:SfRangeSlider ShowLabels="True"
                      LabelOffset="15"
                      LabelTemplate="{StaticResource TrackLabelTemplate}"
                      RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowLabels = true;
sfRangeSlider.LabelOffset = 15;
sfRangeSlider.LabelTemplate = this.Resources["TrackLabelTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with labels template customization](images/labels-and-divisors/slider-labelTemplate.png)

N> Its DataContext is `SliderLabelInfo`.

**Setting active template for labels**

The `ActiveLabelTemplate` property allows you to define the data template for the active label’s like the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="ActiveTrackLabelTemplate">
    <TextBlock Text="{Binding Text}"
               Foreground="{ThemeResource SystemAccentColor}" />
</DataTemplate>

<slider:SfRangeSlider ShowLabels="True"
                      LabelOffset="10"
                      ActiveLabelTemplate="{StaticResource ActiveTrackLabelTemplate}"
                      RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowLabels = true;
sfRangeSlider.LabelOffset = 10;
sfRangeSlider.ActiveLabelTemplate = this.Resources["ActiveTrackLabelTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with active labels template customization](images/labels-and-divisors/slider-activelabelTemplate.png)

N> Its DataContext is `SliderLabelInfo`.

**Formating track labels using label template**

By adding `Converters` in `LabelTemplate` you can customize the format the labels or display the custom text.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="LabelTemplate">
    <TextBlock Text="{Binding Value,
                              Converter={StaticResource FormatStringConverter},
                              ConverterParameter='N2'}" />
</DataTemplate>


<slider:SfRangeSlider ShowLabels="True"
                      Interval="20"
                      LabelOffset="15"
                      LabelTemplate="{StaticResource LabelTemplate}"
                      RangeStart="30"
                      RangeEnd="70" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowLabels = true;
sfRangeSlider.Interval = 20;
sfRangeSlider.LabelOffset = 15;
sfRangeSlider.LabelTemplate = this.Resources["TLabelTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with label format customization](images/labels-and-divisors/slider-labelformat.png)

N> Its DataContext is `SliderLabelInfo`.

## Show divisors

The `ShowDivisors` property is used to render the divisors on the track. The default value of the `ShowDivisors` property is false. It is a shape which is used to represent the major interval points of the track.

For example, if `Minimum` is 0 and `Maximum` is 100 and `Interval` is 10, the slider will render the divisors at 0, 10, 20 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisors](images/labels-and-divisors/slider-showDivisors.png)

## Divisors height and width

You can change the divisor height and width of the range slider using `DivisorHeight` and `DivisorWidth` properties respectively.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="4"
                      DivisorWidth="4" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 4;
sfRangeSlider.DivisorWidth = 4;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor height and width customization](images/labels-and-divisors/slider-divisorHeightWidth.png)

## Divisor stroke thickness and stroke color

You can change the divisor stroke thickness of the range slider using the `DivisorStrokeThickness` property. The default value of `DivisorStrokeThickness` is 0. Also, you can change the divisor stroke of the range slider using the `DivisorStroke` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorStrokeThickness="2"
                      DivisorStroke="Red" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorStrokeThickness = 2;
sfRangeSlider.DivisorStroke = new SolidColorBrush(Colors.Red);
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor stroke customization](images/labels-and-divisors/slider-divisorstroke.png)

## Divisor fill

You can change the divisor fill of the range slider using the `DivisorFill` property.

{% tabs %}

{% highlight xml %}

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorFill="#ff7979" />

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
sfRangeSlider.Interval = 10;
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorFill = new SolidColorBrush(ColorHelper.FromArgb(255,255, 121, 121));
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor fill customization](images/labels-and-divisors/slider-divisorfill.png)

## Divisor template

**Setting template for divisors**

The `DivisorTemplate` property allows you to define the data template for the divisor's like the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="DivisorTemplate">
    <Rectangle Height="{Binding DivisorHeight}"
               Width="{Binding DivisorWidth}"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColor}"
               StrokeThickness="{Binding DivisorStrokeThickness}" />
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="10"
                      DivisorWidth="10"
                      DivisorStrokeThickness="2"
                      DivisorTemplate="{StaticResource DivisorTemplate}">
</slider:SfRangeSlider>

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 10;
sfRangeSlider.DivisorWidth = 10;
sfRangeSlider.DivisorStrokeThickness = 2;
sfRangeSlider.DivisorTemplate = this.Resources["DivisorTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Range slider with divisor template customization](images/labels-and-divisors/slider-divisorTemplate.png)

N> Its DataContext is `SliderBase`.

**Setting active template for labels**

The `DivisorTemplate` property allows you to define the data template for the divisor's like the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="ActiveDivisorTemplate">
    <Rectangle Height="6"
               Width="6"
               Fill="{ThemeResource SystemAltHighColor}"
               Stroke="{ThemeResource SystemAccentColor}"
               StrokeThickness="2" />
</DataTemplate>

<slider:SfRangeSlider RangeStart="30"
                      RangeEnd="70"
                      Interval="10"
                      ShowDivisors="True"
                      DivisorHeight="5"
                      DivisorWidth="5"
                      ActiveDivisorTemplate="{StaticResource ActiveDivisorTemplate}">
</slider:SfRangeSlider>

{% endhighlight %}

{% highlight c# %}

SfRangeSlider sfRangeSlider = new SfRangeSlider();
sfRangeSlider.ShowDivisors = true;
sfRangeSlider.DivisorHeight = 5;
sfRangeSlider.DivisorWidth = 5;
sfRangeSlider.ActiveDivisorTemplate = this.Resources["ActiveDivisorTemplate"] as DataTemplate;
sfRangeSlider.RangeStart = 30;
sfRangeSlider.RangeEnd = 70;
this.Content = sfRangeSlider;

{% endhighlight %}

{% endtabs %}

![Slider with active divisor template customization](images/labels-and-divisors/slider-activeDivisorTemplate.png)