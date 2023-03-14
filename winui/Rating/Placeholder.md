---
layout: post
title: Placeholder value in WinUI Rating control | Syncfusion
description: Learn all about the placeholder feature in the Rating control to show the average rating value before the user provide their own rating.
platform: WinUI
control: SfRating
documentation: ug
---

# Placeholder value in WinUI Rating

The Rating control provides the average rating value before the user provide or click any other actions by using the `PlaceholderValue` property.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3"
     ItemsCount="5" PlaceholderValue="2">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.ItemsCount = 5;
rating.PlaceholderValue = 2;

{% endhighlight %}
{% endtabs %}

![PlaceholderValue feature in WinUI Rating control](Rating_images/winui_rating_placeholdervalue.png)
