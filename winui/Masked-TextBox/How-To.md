---
layout: post
title: Validation support in WinUI MaskedTextBox control | Syncfusion
description: Learn all about restricting the validation support in the MaskedTextBox (SfMaskedTextBox) control.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# How to restrict the default validation in WinUI MaskedTextBox

The MaskedTextBox control provides the ability to validate the input according to the completion of masked input. By default, validation is enabled in the MaskedTextBox control. However, you can disable the validation by assigning `true` to the `IsValid` property of the ValueChanging event.

{% tabs %}

{% highlight XAML %}

<syncfusion:SfMaskedTextBox x:Name="maskedTextBox"
                            Width="200"
                            MaskType="Simple"
                            Mask="000-000-0000"
                            ValueChanging="maskedTextBox_ValueChanging">
</syncfusion:SfMaskedTextBox>

{% endhighlight %}

{% highlight C# %}

private void maskedTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    e.IsValid = true;
}

{% endhighlight %}

{% endtabs %}

![Validation support restriction in WinUI MaskedTextBox](MaskedTextBox_Images/winui_masked_textbox_validation.gif)