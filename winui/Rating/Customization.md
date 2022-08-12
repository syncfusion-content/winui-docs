---
layout: post
title: Customization in WinUI Rating Control | Syncfusion
description: Learn here all about UI customization with Syncfusion WinUI Rating Control (SfRating), its elements, and more.
platform: WinUI
control: SfRating
documentation: ug
---

# Customization in WinUI Rating

This section explains the customization features available in the WinUI Rating control.

## Rating Control using the itemscount property

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
          Value="5"
          Precision="Half"
          ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 5;
rating.Precision = Precision.Half;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

## Rating Control using the Style property

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
 <Style TargetType="Path" x:Key="ratedStyle">
    <Setter Property="Fill" Value="Red"/>
    <Setter Property="Stroke" Value="Black"/>
    <Setter Property="StrokeThickness" Value="2"/>
 </Style>
 <Style TargetType="Path" x:Key="unRatedStyle">   
    <Setter Property="Fill" Value="Blue"/>
    <Setter Property="Stroke" Value="Black"/>
    <Setter Property="StrokeThickness" Value="2"/>
 </Style>
 <Style TargetType="Path" x:Key="highlightStyle">             
    <Setter Property="Fill" Value="Black"/>
    <Setter Property="Stroke" Value="Red"/>
    <Setter Property="StrokeThickness" Value="2"/>
 </Style>
</ResourceDictionary>

<syncfusion:SfRating
          Value="5"
          Precision="Exact"
          ItemsCount="5"
          RatedStyle={StaticResource ratedStyle}
          UnRatedStyle={StaticResource unRatedStyle}
          HighlightStyle={StaticResource highlightStyle}>
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

//RatedStyle
Style style1 = new Style(typeof(Path));
Setter setter1 = new Setter();
setter1.Property = Path.FillProperty;
setter1.Value = new SolidColorBrush(Colors.Red);
style1.Setters.Add(setter1);

Setter setter2 = new Setter();
setter2.Property = Path.StrokeProperty;
setter2.Value = new SolidColorBrush(Colors.Black);
style1.Setters.Add(setter2);

Setter setter3 = new Setter();
setter3.Property = Path.StrokeThicknessProperty;
setter3.Value = 2;
style1.Setters.Add(setter3);

//UnRatedStyle
Style style2 = new Style(typeof(Path));
Setter setter1 = new Setter();
setter1.Property = Path.FillProperty;
setter1.Value = new SolidColorBrush(Colors.LightGray);
style2.Setters.Add(setter1);

Setter setter2 = new Setter();
setter2.Property = Path.StrokeProperty;
setter2.Value = new SolidColorBrush(Colors.CornflowerBlue);
style2.Setters.Add(setter2);

Setter setter3 = new Setter();
setter3.Property = Path.StrokeThicknessProperty;
setter3.Value = 2;
style2.Setters.Add(setter3);

//HighlightStyle
Style style3 = new Style(typeof(Path));
Setter setter1 = new Setter();
setter1.Property = Path.FillProperty;
setter1.Value = new SolidColorBrush(Colors.Navy);
style3.Setters.Add(setter1);

Setter setter2 = new Setter();
setter2.Property = Path.StrokeProperty;
setter2.Value = new SolidColorBrush(Colors.LightSkyBlue);
style3.Setters.Add(setter2);

Setter setter3 = new Setter();
setter3.Property = Path.StrokeThicknessProperty;
setter3.Value = 2;
style3.Setters.Add(setter3);

SfRating rating = new SfRating();

rating.Value = 5;
rating.Precision = Precision.Exact;
rating.ItemsCount = 5;
rating.RatedStyle = style1;
rating.UnRatedStyle = style2;
rating.HighlightStyle = style3;

{% endhighlight %}
{% endtabs %}