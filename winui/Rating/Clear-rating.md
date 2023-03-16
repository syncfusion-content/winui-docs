---
layout: post
title: Clear rating value in WinUI Rating control | Syncfusion
description: Learn all about how to clear the rating value in the WinUI Rating (SfRating) control.
platform: WinUI
control: SfRating
documentation: ug
---

# Clear rating value in WinUI Rating

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
