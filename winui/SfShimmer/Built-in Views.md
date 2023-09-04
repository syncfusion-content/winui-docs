---
layout: post
title: Built-in Views of WinUI Shimmer Control | Syncfusion
description: Learn about the various built-in views available in the Syncfusion WinUI Shimmer(SfShimmer) control, including Circle Persona, Square Persona, Profile, Article, Video, Feed, and Shopping.
platform: WinUI
control: SfShimmer
documentation: ug
---

# Built-in Views of WinUI Shimmer Control (SfShimmer)

## Built-in types

Syncfusion WinUI Shimmer (SfShimmer) control provides seven built-in shimmer view types such as CirclePersona, SquarePersona, Profile, Article, Video, Feed, and Shopping.

![WinUI Shimmmer control with DefaultView](SfShimmer_images/BuiltinView_images/winui_shimmer_BuiltinView.gif)

The built-in shimmer types can be used by setting the Type of SfShimmer. By default, the CirclePersona is initially rendered.

{% tabs %}
{% highlight xaml tabtitle="XAML" hl_lines="2" %}

<syncfusion:SfShimmer x:Name="Shimmer"
                   Type="CirclePersona">
</syncfusion:SfShimmer>

{% endhighlight %}
{% highlight c# tabtitle="C#" hl_lines="3" %}

SfShimmer shimmer = new SfShimmer();
Shimmer.Type = shimmerType.CirclePersona;
this.Content = shimmer;

{% endhighlight %}
{% endtabs %}