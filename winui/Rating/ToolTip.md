---
layout: post
title: ToolTip with WinUI Rating control | Syncfusion
description: Learn here all about Enable tooltip features and tooltip format support in the rating items in WinUI rating control.
platform: WinUI
control: SfRating
documentation: ug
---

# ToolTip in WinUI Rating

The Rating control EnableToolTip can be customized using the `EnableToolTip` property. The default value is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="3"
     ItemsCount="5"
     EnableToolTip="True">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 3;
rating.ItemsCount = 5;
rating.EnableToolTip = true;

{% endhighlight %}
{% endtabs %}

![Rating control using enabletooltip in WinUI](Rating_images/winui_rating_tooltip.png)

## Rating Control using the ToolTipFormat 

The Rating control ToolTipFormat can be customized using the `ToolTipFormat` property. The default value is `0.##`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="2.7"
     Precision="Exact"
     ItemsCount="5"
     EnableToolTip="True"
     ToolTipFormat="0.000">
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

![Rating control using tooltipformat in WinUI](Rating_images/winui_rating_tooltipformat1.png)

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="2.5"
     Precision="Half"
     ItemsCount="5"
     EnableToolTip="True"
     ToolTipFormat="$.00"  >

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 2;
rating.Precision= RatingPrecision.Half;
rating.ItemsCount = 5;
rating.EnableToolTip = true;
rating.ToolTipFormat = "$.00";

{% endhighlight %}
{% endtabs %}

![Rating control using tooltipformat in WinUI](Rating_images/winui_rating_tooltipformat2.png)
