---
layout: post
title: Use UpDown Button (Spin Button) in WinUI NumberBox | Syncfusion
description: Learn here all about how to use UpDown Button (SpinButton) in Syncfusion WinUI NumberBox (SfNumberBox) control and more.
platform: winui
control:  SfNumberBox
documentation: ug
---

# UpDown Button (SpinButton) in WinUI NumberBox

This section describes how to change value in the [NumberBox](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html) control using keys, mouse scrolling and the up-down button.

## Increase or decrease value

You can increment or decrement the value in the `NumberBox` control by using **UpArrow**, **DownArrow**, **PageUp** and **PageDown** keys. You can change the increment or decrement value when Arrow keys are pressed, using the [SmallChange](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_SmallChange) property and for Page keys using the [LargeChange](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_LargeChange) property. By default, the value of `SmallChange` property is **1** and `LargeChange` property  is **10**.

N> The value in `NumberBox` can also be changed by mouse scrolling. The mouse scrolling increases or decreases the value based on the `SmallChange` property.

{% tabs %}
{% highlight xaml %}

<editors:SfNumberBox HorizontalAlignment="Center"
                     VerticalAlignment="Center" 
                     SmallChange="5"
                     Value="10"
                     LargeChange="10" />

{% endhighlight %}
{% highlight C# %}

SfNumberBox SfNumberBox= new SfNumberBox();
SfNumberBox.PlaceholderText = "Enter input here...";
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;

{% endhighlight %}
{% endtabs %}

![WinUI NumberBox Watermark Text](GettingStarted_images/valuechange-bykeys.gif)

## UpDown button placement

You can increase or decrease the value of the `NumberBox` control using the up-down button. By default, the value of [UpDownPlacementMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfNumberBox.html#Syncfusion_UI_Xaml_Editors_SfNumberBox_UpDownPlacementMode) property is **Hidden**. You can change the up-down button position by assigning the value `UpDownPlacementMode` property as **Inline** or **Compact**.

N> When using the up-down button, the `NumberBox` control value changes based on the value of the `SmallChange` property.

{% tabs %}
{% highlight XAML %}

<editors:SfNumberBox x:Name="sfNumberBox" 
                     HorizontalAlignment="Center"
                     VerticalAlignment="Center"
                     UpDownPlacementMode="Inline" />

{% endhighlight %}
{% highlight c# %}

SfNumberBox sfNumberBox = new SfNumberBox();
sfNumberBox.HorizontalAlignment = HorizontalAlignment.Center;
sfNumberBox.VerticalAlignment = VerticalAlignment.Center;
sfNumberBox.UpDownPlacementMode = NumberBoxUpDownPlacementMode.Inline;

{% endhighlight %}
{% endtabs %}

![UpDown Placement in WinUI NumberBox](SpinButton_images/spinbuttonPlacement_img.gif)

## TextBox visibility

The `TextBoxVisibility` property can be used to hide or show the visibility of a text box in a number box.
When the text box visibility is collapsed, only the UpDown buttons are visible. You can change the control values by using the UpDown buttons.



N> This feature is enabled when the UpDownPlacementMode value is **Inline**.

{% tabs %}
{% highlight XAML %}

<editors:SfNumberBox x:Name="numberBox"
                     Height="75" 
                     Width="300"
                     TextBoxVisibility="Collapsed"
                     UpDownPlacementMode="Inline"/>

{% endhighlight %}
{% highlight c# %}

SfNumberBox SfNumberBox = new SfNumberBox();
SfNumberBox.TextBoxVisibility = Visibility.Collapsed;
SfNumberBox.UpDownPlacementMode = NumberBoxUpDownPlacementMode.Inline;


{% endhighlight %}
{% endtabs %}

If the TextBoxVisibility value is collapsed,

![WinUI NumberBox with TextBox collapsed](SpinButton_images/textbox_visibility_collapsed.gif)

If the TextBoxVisibility value is Visible,

![WinUI NumberBox with TextBox Visible](SpinButton_images/textbox_visibility_visible.png)