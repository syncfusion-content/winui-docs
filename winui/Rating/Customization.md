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

## Rating Control using the ItemsCount property

The Rating control itemscount can be customized using the `ItemsCount` Property. The default value is 0.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

## Rating Control using the Value property

The Rating control value can be customized using the `Value` Property. The default value is 0.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
      Value="3"
      ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
 
rating.Value = 3;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

## Rating Control using the Precision property

The Rating control Precision can be customized using the `Precision` Property. It have three types Standard, Half and Exact. The default value is "Standard".   

{% tabs %}
{% highlight XAML %}

//Rating Value setted with Standard Precision
<syncfusion:SfRating
     Value="3"
     Precision="Standard"
     ItemsCount="5">
</syncfusion:SfRating>

//Rating Value setted with Half Precision
<syncfusion:SfRating
     Value="3"
     Precision="Half"
     ItemsCount="5">
</syncfusion:SfRating>

Rating value setted with Exact Precision
<syncfusion:SfRating
     Value="3"
     Precision="Exact"
     ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
 
rating.Value = 3;
rating.Precision = Precision.Standard;
rating.ItemsCount = 5;

rating.Value = 3;
rating.Precision = Precision.Half;
rating.ItemsCount = 5;

rating.Value = 3;
rating.Precision = Precision.Exact;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

## Rating Control using the ItemSize property

The Rating control itemsize can be customized using the `ItemSize` Property. The default value is 50.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
      Value="2"
      ItemsCount="5"
      ItemSize="60">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 2;
rating.ItemsCount = 5;
rating.ItemSize = 60;

{% endhighlight %}
{% endtabs %}

## Rating Control using the ItemsSpacing property

The Rating control itemsspacing can be customized using the `ItemsSpacing` Property. The default value is 0.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
      Value="2"
      ItemsCount="5"
      ItemsSpacing="2">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 2;
rating.ItemsCount = 5;
rating.ItemsSpacing = 2;

{% endhighlight %}
{% endtabs %}



## Rating Control using the Style property

The Rating control style can be customized using the `RatedStyle`, `UnRatedStyle` and `HighlightStyle` Property. The default value is null.

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
      Value="2"
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

rating.Value = 2;
rating.ItemsCount = 5;
rating.RatedStyle = style1;
rating.UnRatedStyle = style2;
rating.HighlightStyle = style3;

{% endhighlight %}
{% endtabs %}

## Rating Control using the IsReadOnly property

The Rating control isreadonly can be customized using the `IsReadOnly` Property. The default value is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating
     Value="3"
     ItemsCount="5"
     IsReadOnly="True">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.ItemsCount = 5;
rating.Value = 3;
rating.IsReadOnly = true;

{% endhighlight %}
{% endtabs %}



