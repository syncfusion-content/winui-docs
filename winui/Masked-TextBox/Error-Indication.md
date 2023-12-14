---
layout: post
title: Error Indication in WinUI MaskedTextBox control | Syncfusion
description: Explore the various error types supported by the Syncfusion WinUI MaskedTextBox (SfMaskedTextBox) control to enhance user experience and input validation.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Error Indication in WinUI MaskedTextBox

The MaskedTextBox control supports error indication by displaying an icon and providing additional details upon hovering over the icon. This powerful feature allows users to employ various error icons based on specific validation scenarios.

## Built-in error types:

The MaskedTextBox control offers several built-in error types:

* `None` : No visible signals for errors.
* `Default` : Red bottom border brush in the MaskedTextBox Control.
* `Warning` : Visual highlight for potential concerns needing immediate attention.
* `Information` : Share non-essential details or guidance.
* `Critical` : Urgent issues requiring immediate action.
* `Success` : Positive confirmation for valid input or successful actions.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox Name="maskedTextBox"
                            MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ErrorType="Warning"
                            ValueChanging="ErrorTypeMaskTextBox_ValueChanging"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Warning;
maskedTextBox.ValueChanging += ErrorTypeMaskTextBox_ValueChanging;

private void ErrorTypeMaskTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    // Show a success icon for valid input, or display a warning icon otherwise.
    maskedTextBox.ErrorType = e.IsValid ? ErrorType.Success : ErrorType.Warning;
}

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with error type](MaskedTextBox_images/winui_masked_textbox_errortype.png)

## Custom error type:

The `Custom` error type provides users with the flexibility to customize both the error icon and the border brush. This customization is achieved through the following properties:

* `CustomErrorIcon`: Allows you to set a custom error icon.
* `CustomErrorBorderBrush`: Enables customization of the border brush for the `Custom` error type.


{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox Name="maskedTextBox"
                            MaskType="Simple" 
                            Mask="(+00) 000 000-0000" 
                            Width="200"
                            ErrorType="Custom"
                            CustomErrorIcon="CustomIcon.png"
                            CustomErrorBorderBrush="DarkViolet"
                            ValueChanging="ErrorTypeMaskTextBox_ValueChanging"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "(+00) 000 000-0000";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Custom;
maskedTextBox.CustomErrorIcon = new BitmapImage(new Uri("ms-appx:///CustomIcon.png"));
maskedTextBox.CustomErrorBorderBrush = new SolidColorBrush(Colors.DarkViolet);
maskedTextBox.ValueChanging += ErrorTypeMaskTextBox_ValueChanging;

private void ErrorTypeMaskTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    maskedTextBox.ErrorType = e.IsValid ? ErrorType.Success : ErrorType.Custom;
}

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with custom error type](MaskedTextBox_images/winui_masked_textbox_errortype_custom.png)

## Error content:

The `ErrorContent` property is used to display content when hovering over the error icon. This feature allows you to provide additional information or guidance related to the specific error scenario.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox Name="maskedTextBox"
                            MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ErrorType="Warning"
                            ErrorContent="Caps not allowed in the mail ID"
                            ValueChanging="ErrorTypeMaskTextBox_ValueChanging"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Warning;
maskedTextBox.ErrorContent = "Caps not allowed in the mail ID";
maskedTextBox.ValueChanging += ErrorTypeMaskTextBox_ValueChanging;

private void ErrorTypeMaskTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    maskedTextBox.ErrorType = e.IsValid ? ErrorType.Success : ErrorType.Warning;
}

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with error content](MaskedTextBox_images/winui_masked_textbox_errorcontent.png)