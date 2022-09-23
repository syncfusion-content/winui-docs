---
layout: post
title: Precision with WinUI Rating control | Syncfusion
description: Learn here all about precision mode defines the accuracy level and it has full, half and exact options of the SfRating control.
platform: WinUI
control: SfRating
documentation: ug
---

# Precision in WinUI Rating

This section explains the precision features available in the WinUI Rating control.

## Rating Control using the Precision property

The Rating control Precision can be customized using the `Precision` Property. It have three types Full, Half and Exact. The default value is "Full".  

## Full

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="3"
     Precision="Full"
     ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

//Rating Value setted with Full Precision 
rating.Value = 3;
rating.Precision = RatingPrecision.Full;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

[Rating control](Rating_images/winui_rating_precisionfull.png)

## Half

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="3.5"
     Precision="Half"
     ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

//Rating Value setted with Half Precision
rating.Value = 3.5;
rating.Precision = RatingPrecision.Half;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

[Rating control](Rating_images/winui_rating_precisionhalf.png)

## Exact

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="3.7"
     Precision="Exact"
     ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

//Rating value setted with Exact Precision
rating.Value = 3.7;
rating.Precision = RatingPrecision.Exact;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

[Rating control](Rating_images/winui_rating_precisionexact.png)

