---
layout: post
title: Placeholder value in WinUI Rating control | Syncfusion
description: Learn all about the placeholder feature in the Rating control to show the average rating value before the user provide their own rating.
platform: WinUI
control: SfRating
documentation: ug
---

# Placeholder value in WinUI Rating

By using the `PlaceholderValue` property, the Rating control can display the average rating value before the user provides their own rating by click or other action.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating 
     ItemsCount="5" PlaceholderValue="2">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.ItemsCount = 5;
rating.PlaceholderValue = 2;

{% endhighlight %}
{% endtabs %}

![Placeholder value feature in WinUI Rating control](Rating_images/winui_rating_placeholdervalue.png)
