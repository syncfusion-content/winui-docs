---
layout: post
title: ToolTip in WinUI Rating control | Syncfusion
description: Learn all about how to enable the tooltip and format the tooltip content in WinUI Syncfusion Rating (SfRating) control here.
platform: WinUI
control: SfRating
documentation: ug
---

# ToolTip in WinUI Rating

The Rating control tooltip can be enabled by using the [EnableToolTip](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfRating.html#Syncfusion_UI_Xaml_Editors_SfRating_EnableToolTip) property. When the mouse hovers over the control, it will show the rating value content as a tooltip. The default value is `false`.

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

The tooltip content can be formatted by using the [ToolTipFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfRating.html#Syncfusion_UI_Xaml_Editors_SfRating_ToolTipFormat) property. It can aslo be provided as [Custom numeric format strings](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-numeric-format-strings) and [Standard numeric format strings](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings).

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

