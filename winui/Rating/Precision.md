---
layout: post
title: Precision in WinUI Rating control | Syncfusion
description: Learn here all about the precision feature in the Rating control to set the accuracy level such as full, half, and exact.
platform: WinUI
control: SfRating
documentation: ug
---

# Precision in WinUI Rating

The rating value can be provided with three options such as full, half, and exact using the `Precision` property. The default value is `Full`.

## Full

Rating value can be provided with whole precision.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3" 
     Precision="Full" ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.Precision = RatingPrecision.Full;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with full precision](Rating_images/winui_rating_precision_full.png)

## Half

Rating value can be provided with half precision.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3.5"
     Precision="Half" ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3.5;
rating.Precision = RatingPrecision.Half;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with half precision](Rating_images/winui_rating_precision_half.png)

## Exact

Rating value can be provided with exact precision.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3.7"
     Precision="Exact" ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3.7;
rating.Precision = RatingPrecision.Exact;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with exact precision](Rating_images/winui_rating_precision_exact.png)

