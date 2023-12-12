---
layout: post
title: Error Indication in WinUI MaskedTextBox control | Syncfusion
description: Explore the various error types supported by the Syncfusion WinUI MaskedTextBox (SfMaskedTextBox) control to enhance user experience and input validation.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Error Indication in WinUI MaskedTextBox

The [WinUI MaskedTextBox](https://www.syncfusion.com/winui-controls/masked-textbox) control provides comprehensive error types support to facilitate effective input validation and enhance user experience. This feature enables users to utilize various error icons and styles based on specific validation scenarios.The following error types such as none, default, warning, information, critical, success, custom is available in the MaskedTextBox control.

* `None` : No visible signals for errors.
* `Default` : Red bottom border brush in the MaskedTextBox Control.
* `Warning ` : Visual highlight for potential concerns needing immediate attention.
* `Information` : Share non-essential details or guidance.
* `Critical` : Urgent issues requiring immediate action.
* `Success` : Positive confirmation for valid input or successful actions.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="None"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxNone = new SfMaskedTextBox();
maskedTextBoxNone.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxNone.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxNone.Width = 200;
maskedTextBoxNone.ErrorType = ErrorType.None;
maskedTextBoxNone.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype](MaskedTextBox_images/winui_masked_textbox_errortype.png)

# Custom:

The `Custom` error type in the SfMaskedTextBox allows users to define a unique error icon and customize the bottom border color using the `CustomErrorIcon` and `CustomErrorBorderBrush` properties, respectively.

* `CustomErrorIcon` :  Specifies a custom image for error indication in the SfMaskedTextBox control.
* `CustomErrorBorderBrush` : Determines the color of the bottom border of the SfMaskedTextBox control when an error occurs.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ErrorType="Custom"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            CustomErrorIcon="CustomIcon.png"
                            CustomErrorBorderBrush="Purple"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Custom;
maskedTextBox.CustomErrorIcon = new BitmapImage(new Uri("ms-appx:///CustomIcon.png"));
maskedTextBox.CustomErrorBorderBrush = new SolidColorBrush(Colors.Purple);
maskedTextBox.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Custom](MaskedTextBox_images/winui_masked_textbox_errortype_custom.png)

# ErrorContent:

The `ErrorContent` property is used to display content when hovering over the error icon.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Warning"
                            ErrorContent="Caps not allowed in the mail ID"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Warning;
maskedTextBox.ErrorContent = "Caps not allowed in the mail ID";
maskedTextBox.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Error Content](MaskedTextBox_images/winui_masked_textbox_errorcontent.png)