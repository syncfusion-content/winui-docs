---
layout: post
title: Clear Rating Value in WinUI Rating | Syncfusion®
description: Clear rating value support in WinUI Rating enables users to reset or remove the selected rating, providing greater flexibility in rating interactions.
platform: WinUI
control: SfRating
documentation: ug
---

# Clear Rating Value in WinUI Rating

The `IsClearEnabled` property of the Rating control allows you to clear the provided rating value when the value is true. The default value of the `IsClearEnabled` property is `true`.

N> It supports precision mode `full` only.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3"
     ItemsCount="5" IsClearEnabled="true">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.ItemsCount = 5;
rating.IsClearEnabled = true;

{% endhighlight %}
{% endtabs %}

![Clear rating value in WinUI Rating control](Rating_images/winui_rating_isclearenabled.gif)
