---
layout: post
title: ToolTip in WinUI Rating control | Syncfusion
description: Learn here all about how to enable the tooltip and format the tooltip content in WinUI Syncfusion Rating (SfRating) control.
platform: WinUI
control: SfRating
documentation: ug
---

# ToolTip in WinUI Rating

The Rating control tooltip can be enabled by using the `EnableToolTip` property. It will show the rating value when the user hovers the mouse over the control. The default value is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3"
     ItemsCount="5" EnableToolTip="True">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.ItemsCount = 5;
rating.EnableToolTip = true;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with tooltip](Rating_images/winui_rating_tooltip.png)

## ToolTipFormat for Rating

The tooltip content can be formatted by using the `ToolTipFormat` property.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="2"
     Precision="Exact" ItemsCount="5"
     EnableToolTip="True" ToolTipFormat="0.000">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 2;
rating.Precision= RatingPrecision.Exact;
rating.ItemsCount = 5;
rating.EnableToolTip = true;
rating.ToolTipFormat = "0.000";

{% endhighlight %}
{% endtabs %}

![TooltipFormat in WinUI Rating control](Rating_images/winui_rating_tooltipformat.png)

