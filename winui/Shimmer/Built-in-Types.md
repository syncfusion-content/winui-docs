---
layout: post
title: Built-in types of WinUI Shimmer control | Syncfusion
description: Learn about the various built-in types available in the WinUI Shimmer control, including CirclePersona, SquarePersona, Profile, Article, Video, Feed, and Shopping.
platform: WinUI
control: Shimmer
documentation: ug
---

# Built-in Types of WinUI Shimmer Control 

The WinUI Shimmer control offers a range of built-in shimmer types, each designed to serve specific user interface needs. These built-in types provide convenient options for creating captivating loading animations in your WinUI applications. The following built-in shimmer types such as [CirclePersona](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_CirclePersona), [SquarePersona](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_SquarePersona), [Profile](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_Profile), [Article](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_Article), [Video](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_Video), [Feed](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_Feed), and [Shopping](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_Shopping) is available in Shimmer control.

![WinUI Shimmmer control with DefaultView](Shimmer_Images/winui_shimmer_built_in_types.gif)

By default, the WinUI Shimmer control initializes with the [CirclePersona](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.ShimmerType.html#Syncfusion_UI_Xaml_Core_ShimmerType_CirclePersona) type. You can easily switch between these built-in types by setting the Type property of the SfShimmer control.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfShimmer x:Name="Shimmer"
                      Type="CirclePersona">
</syncfusion:SfShimmer>

{% endhighlight %} 
{% highlight C# %}

SfShimmer Shimmer = new SfShimmer();
Shimmer.Type = ShimmerType.CirclePersona;
this.Content = Shimmer;

{% endhighlight %}
{% endtabs %}