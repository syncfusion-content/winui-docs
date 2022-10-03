---
layout: post
title: Precision in WinUI Rating control | Syncfusion
description: Learn all about the precision feature in the Rating control to set the accuracy level such as full, half, and exact here.
platform: WinUI
control: SfRating
documentation: ug
---

# Precision in WinUI Rating

The [Rating control](https://www.syncfusion.com/winui-controls/rating) provides an option to set an accuracy level for ratings with flexible precision to handle full, half, or exact values using the [Precision](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfRating.html#Syncfusion_UI_Xaml_Editors_SfRating_Precision) property. The default value is `Full`.

## Full

The rating value can be provided with the nearest rounded value.

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

The rating value can be provided with the nearest half value.

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

The rating value can be provided with the exact value.

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

