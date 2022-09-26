---
layout: post
title: Customization with WinUI Rating control | Syncfusion
description: Learn here all about UI customization with Syncfusion WinUI Rating Control (SfRating), its elements, and more.
platform: WinUI
control: SfRating
documentation: ug
---

# Customization in WinUI Rating

This section explains the customization features available in the WinUI `Rating` control.

## Initialize Rating control using Value

The Rating control value can be customized using the `Value` Property. The default value is 0.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3" ItemsCount="5">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();
rating.Value = 3;
rating.ItemsCount = 5;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with value](Rating_images/winui_rating_value.png)

## Initialize Rating control using ItemSize 

The Rating control itemsize can be customized using the `ItemSize` Property. The default value is 24.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3"
     ItemsCount="5" ItemSize="50">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 3;
rating.ItemsCount = 5;
rating.ItemSize = 50;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with itemsize](Rating_images/winui_rating_itemsize.png)

## Initialize Rating control using Style

The Rating control style can be customized using the `RatedItemStyle`, `UnratedItemStyle` Property.

{% tabs %}
{% highlight XAML %}

<ResourceDictionary>
 <Style TargetType="Path" x:Key="ratedStyle">
    <Setter Property="Fill" Value="Red"/>
    <Setter Property="Stroke" Value="Black"/>
    <Setter Property="StrokeThickness" Value="1"/>
 </Style>
 <Style TargetType="Path" x:Key="unratedStyle">   
    <Setter Property="Fill" Value="LightGray"/>
    <Setter Property="Stroke" Value="CornflowerBlue"/>
    <Setter Property="StrokeThickness" Value="1"/>
 </Style>
</ResourceDictionary>

<syncfusion:SfRating Value="3"
      ItemsCount="5" RatedItemStyle={StaticResource ratedStyle}
      UnratedItemStyle={StaticResource unratedStyle}>
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

//RatedItemStyle
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
setter3.Value = 1;
style1.Setters.Add(setter3);

//UnratedItemStyle
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
setter3.Value = 1;
style2.Setters.Add(setter3);

SfRating rating = new SfRating();

rating.Value = 3;
rating.ItemsCount = 5;
rating.RatedItemStyle = style1;
rating.UnratedItemStyle = style2;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with style](Rating_images/winui_rating_style.png)

## Initialize Rating control using IsReadOnly

The Rating control isreadonly can be customized using the `IsReadOnly` Property. The default value is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfRating Value="3"
     ItemsCount="5" IsReadOnly="True">
</syncfusion:SfRating>

{% endhighlight %}
{% highlight C# %}

SfRating rating = new SfRating();

rating.Value = 3;
rating.ItemsCount = 5;
rating.IsReadOnly = true;

{% endhighlight %}
{% endtabs %}

![WinUI Rating control with isreadonly](Rating_images/winui_rating_isreadonly.png)

