---
layout: post
title: Label features in Syncfusion WinUI Slider
description: This section explains about how to show labels, divisors and how to customize them in the WinUI slider.
platform: WinUI
control: SfSlider
documentation: ug
---

# Labels and divisors in the slider

This section explains about how to add the labels and divisors in the slider.

## Show labels

The `ShowLabels` property is used to render the labels on given `Interval`. The default value of `ShowLabels` property is false.

{% tabs %}

{% highlight xml %}

<slider:SfSlider ShowLabels="True"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with labels](images/labels-and-divisors/slider-labels.png)

## Maximum number of labels per 100 logical pixels

By default, a maximum of three labels are displayed for each 100 logical pixels in slider. The maximum number of labels that should present within 100 logical pixels length can be customized using the `MaximumLabelsCount` property of the slider. This property is applicable only for automatic range calculation and will not work if you set value for `Interval` property of an slider.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 MaximumLabelsCount="1"
                 ShowLabels="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.MaximumLabelsCount = 1;
sfSlider.Value = 50;
sfSlider.ShowLabels = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with maximum labels count](images/labels-and-divisors/slider-maximumLabelsCount.png)

## Label placement

The `labelPlacement` property is used to place the labels either before or after the track. The default value of the `LabelPlacement` property is `Placement.After`.

{% tabs %}

{% highlight xml %}

<slider:SfSlider ShowLabels="True"
                 Value="50"
                 LabelPlacement="Before" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Value = 50;
sfSlider.LabelOffset = Placement.Before;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with labels placement customization](images/labels-and-divisors/slider-labelPlacement.png)

## Label offset

You can adjust the space between ticks and labels of the slider using the `LabelOffset` property. The default value of `LabelOffset` property is 5.

{% tabs %}

{% highlight xml %}

<slider:SfSlider ShowTicks="True"
                 ShowLabels="True"
                 Value="50"
                 LabelOffset="10" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowTicks = true;
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 10;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with labels offset customization](images/labels-and-divisors/slider-labelOffset.png)

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

<slider:SfSlider ShowLabels="True"
                 LabelOffset="15"
                 LabelTemplate="{StaticResource TrackLabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 15;
sfSlider.LabelTemplate = this.Resources["TrackLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with labels template customization](images/labels-and-divisors/slider-labelTemplate.png)

N> Its DataContext is `SliderLabelInfo`.

**Setting active template for labels**

The `ActiveLabelTemplate` property allows you to define the data template for the active label’s like the following code example.

{% tabs %}

{% highlight xml %}

<DataTemplate x:Key="ActiveTrackLabelTemplate">
    <TextBlock Text="{Binding Text}"
               Foreground="{ThemeResource SystemAccentColor}" />

</DataTemplate>

<slider:SfSlider ShowLabels="True"
                 LabelOffset="10"
                 LabelTemplate="{StaticResource ActiveTrackLabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.LabelOffset = 10;
sfSlider.LabelTemplate = this.Resources["ActiveTrackLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with active labels template customization](images/labels-and-divisors/slider-activelabelTemplate.png)

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


<slider:SfSlider ShowLabels="True"
                 Interval="20"
                 LabelOffset="15"
                 LabelTemplate="{StaticResource LabelTemplate}"
                 Value="50" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowLabels = true;
sfSlider.Interval = 20;
sfSlider.LabelOffset = 15;
sfSlider.LabelTemplate = this.Resources["TLabelTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with label format customization](images/labels-and-divisors/slider-labelformat.png)

N> Its DataContext is `SliderLabelInfo`.

## Show divisors

The `ShowDivisors` property is used to render the divisors on the track. The default value of the `ShowDivisors` property is false. It is a shape which is used to represent the major interval points of the track.

For example, if `Minimum` is 0 and `Maximum` is 100 and `Interval` is 10, the slider will render the divisors at 0, 10, 20 and so on.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divisors](images/labels-and-divisors/slider-showDivisors.png)

## Divisors height and width

You can change the divisor height and width of the slider using `DivisorHeight` and `DivisorWidth` properties respectively.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="4"
                 DivisorWidth="4" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 4;
sfSlider.DivisorWidth = 4;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divisor height and width customization](images/labels-and-divisors/slider-divisorHeightWidth.png)

## Divisor stroke thickness and stroke color

You can change the divisor stroke thickness of the slider using the `DivisorStrokeThickness` property. The default value of `DivisorStrokeThickness` is 0. Also, you can change the divisor stroke of the slider using the `DivisorStroke` property.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorStrokeThickness="2"
                 DivisorStroke="Red" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorStrokeThickness = 2;
sfSlider.DivisorStroke = new SolidColorBrush(Colors.Red);
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divisor stroke customization](images/labels-and-divisors/slider-divisorstroke.png)

## Divisor fill

You can change the divisor fill of the slider using the `DivisorFill` property.

{% tabs %}

{% highlight xml %}

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorFill="#ff7979" />

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.Value = 50;
sfSlider.Interval = 10;
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorFill = new SolidColorBrush(ColorHelper.FromArgb(255,255, 121, 121));
this.MainGrid.Children.Add(sfSlider);

{% endhighlight %}

{% endtabs %}

![Slider with divisor fill customization](images/labels-and-divisors/slider-divisorfill.png)

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

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="10"
                 DivisorWidth="10"
                 DivisorStrokeThickness="2"
                 DivisorTemplate="{StaticResource DivisorTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 10;
sfSlider.DivisorWidth = 10;
sfSlider.DivisorStrokeThickness = 2;
sfSlider.DivisorTemplate = this.Resources["DivisorTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with divisor template customization](images/labels-and-divisors/slider-divisorTemplate.png)

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

<slider:SfSlider Value="50"
                 Interval="10"
                 ShowDivisors="True"
                 DivisorHeight="5"
                 DivisorWidth="5"
                 ActiveDivisorTemplate="{StaticResource ActiveDivisorTemplate}">
</slider:SfSlider>

{% endhighlight %}

{% highlight c# %}

SfSlider sfSlider = new SfSlider();
sfSlider.ShowDivisors = true;
sfSlider.DivisorHeight = 5;
sfSlider.DivisorWidth = 5;
sfSlider.ActiveDivisorTemplate = this.Resources["ActiveDivisorTemplate"] as DataTemplate;
sfSlider.Value = 50;
this.Content = sfSlider;

{% endhighlight %}

{% endtabs %}

![Slider with active divisor template customization](images/labels-and-divisors/slider-activeDivisorTemplate.png)
