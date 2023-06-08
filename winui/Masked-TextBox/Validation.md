---
layout: post
title: Validation in WinUI MaskedTextBox control | Syncfusion
description: Learn all about how to set the validation support for the MaskedTextBox (SfMaskedTextBox) control using ValueChanging event.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Validation in WinUI MaskedTextBox

The `MaskedTextBox` control allows you to validate the input entered using the `ValueChanging` event. The validation condition can be customized using the properties of the `ValueChanging` event.

To implement validation support for the MaskedTextBox, you can utilize the `IsMaskCompleted` property in the `ValueChanging` event. When all the required input is provided, `IsMaskCompleted` will be true, indicating valid input. If it is false, the MaskedTextBox border turns red; otherwise, it returns to its default state.

{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="5" %}
<syncfusion:SfMaskedTextBox x:Name="maskedTextBox"
                            Width="200"
                            MaskType="Simple"
                            Mask="000-000-0000"
                            ValueChanging="maskedTextBox_ValueChanging">
</syncfusion:SfMaskedTextBox>
{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" %}
private void maskedTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    e.IsInputValid = e.IsMaskCompleted;
}
{% endhighlight %}
{% endtabs %}

![Validation support in WinUI MaskedTextBox](MaskedTextBox_Images/winui_masked_textbox_validation.gif)