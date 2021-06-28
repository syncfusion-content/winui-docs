---
layout: post
title: Value change restriction in WinUI NumberBox | Syncfusion
description: Learn here all about how to restrict the value change in Syncfusion WinUI NumberBox (SfNumberBox) control and more.
platform: winui
control:  SfNumberBox
documentation: ug
---

# Value change restriction in WinUI NumberBox

This section describes how to restrict the change in value of the `NumberBox` control using `AllowNull`, `Minimum`, and `Maximum` properties.

## Restrict null value

By default, an empty or null value is set in the `NumberBox` control when the input is cleared, as the default value of the `AllowNull` property is **true**. When the `AllowNull` property value is **false**, the `NumberBox` control return the value to **0** in the editor after clearing the input.

N> When the value of the `Minimum` property is **15** and the `AllowNull` property is **true**, **null** value is returned in `NumberBox` control after clearing the input.

N> When the value of the `Minimum` property is **15** and the `AllowNull` property is **false**, the minimum value is returned in `NumberBox` control after clearing the input.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center" 
                     Value="10" 
                     AllowNull="False" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.Value = 10;
sfNumberBox.AllowNull = false;

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox value restriction](Restriction_images/restrict_nullvalue.gif)

## Restrict value within range

You can restrict the users to enter input within a minimum and maximum range in `NumberBox` control using the `Minimum` and `Maximum` properties. The default value of the `Minimum` property is **double.MinValue** and `Maximum` property is **double.MaxValue**.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center"
                     Value="50"
                     Minimum="10"
                     Maximum="30" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.Minimum = 10;
sfNumberBox.Maximum = 30;
sfNumberBox.Value = 50;

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox value restriction](GettingStarted_images/value_restriction_img.png)

## Restrict text editing

You can prevent users from editing the numerical value in the editor using the `IsEditable` property. However, you can still change the value by using the up-down buttons, mouse scroll, keyboard arrows, and page keys. By default, the value of `IsEditable` property is **false**. 

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox x:Name="sfNumberBox" 
                     HorizontalAlignment="Center"
                     VerticalAlignment="Center"
                     IsEditable="True" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.IsEditable = true;

{% endhighlight %}
{% endtabs %}

