---
layout: post
title: ClearEnabled in WinUI Rating control | Syncfusion
description: Learn all about how to enable the clear enable feature in the Rating control the user can remove their rating or not.
platform: WinUI
control: SfRating
documentation: ug
---

# Clear Rating

The Rating control provides value support to determine whether a user can remove their rating or not, by using the `IsClearEnabled` property.

`Note`- It supports Precision full value only.

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
![IsClearEnabled customization in WinUI Rating control](Rating_images/winui_rating_isclearenabled.gif)
