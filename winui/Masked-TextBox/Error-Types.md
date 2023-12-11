---
layout: post
title: Error Types in WinUI MaskedTextBox control | Syncfusion
description: Explore the various error types supported by the Syncfusion WinUI MaskedTextBox (SfMaskedTextBox) control to enhance user experience and input validation.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Error Types in WinUI MaskedTextBox

The [WinUI MaskedTextBox](https://www.syncfusion.com/winui-controls/masked-textbox) control provides comprehensive error types support to facilitate effective input validation and enhance user experience. This feature enables users to utilize various error icons and styles based on specific validation scenarios.The following Error types such as None, Default, Warning, Information, Critical, Success, Custom is available in the MaskedTextBox control.

# None:

The `None` error type is ideal when users prefer no visible signals for errors.

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

![WinUI MaskedTextBox control with Errortype None](MaskedTextBox_images/winui_masked_textbox_errortype_none.png)

# Default:

The `Default` error type shows a red color botttom border brush in the MaskedTextBox Control.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Default"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxDefault = new SfMaskedTextBox();
maskedTextBoxDefault.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxDefault.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxDefault.Width = 200;
maskedTextBoxDefault.ErrorType = ErrorType.Default;
maskedTextBoxDefault.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Default](MaskedTextBox_images/winui_masked_textbox_errortype_default.png)

# Warning:

The `Warning` error type to visually highlight potential concerns that need immediate attention.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Warning"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxWarning = new SfMaskedTextBox();
maskedTextBoxWarning.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxWarning.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxWarning.Width = 200;
maskedTextBoxWarning.ErrorType = ErrorType.Warning;
maskedTextBoxWarning.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Warning](MaskedTextBox_images/winui_masked_textbox_errortype_warning.png)

# Information:

The `Information` error type uses an icon to share non-essential details or guidance.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Information"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxInformation = new SfMaskedTextBox();
maskedTextBoxInformation.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxInformation.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxInformation.Width = 200;
maskedTextBoxInformation.ErrorType = ErrorType.Information;
maskedTextBoxInformation.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Information](MaskedTextBox_images/winui_masked_textbox_errortype_information.png)

# Critical:

The `Critical` error type for urgent issues that require immediate action.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Critical"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxCritical = new SfMaskedTextBox();
maskedTextBoxCritical.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxCritical.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxCritical.Width = 200;
maskedTextBoxCritical.ErrorType = ErrorType.Critical;
maskedTextBoxCritical.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Critical](MaskedTextBox_images/winui_masked_textbox_errortype_critical.png)

# Success:

The `Success` error type offers a positive visual confirmation for successful actions or valid input.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Success"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxSuccess = new SfMaskedTextBox();
maskedTextBoxSuccess.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxSuccess.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxSuccess.Width = 200;
maskedTextBoxSuccess.ValueChanging += SfMaskedTextBox_ValueChanging;

// If the entered text is valid, then the success icon will show in the maskedTextbox.

 private void SfMaskedTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
 {
     if(e.IsValid)
     {
         maskedTextBoxSuccess.ErrorType = ErrorType.Success;
     }
 }

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Success](MaskedTextBox_images/winui_masked_textbox_errortype_success.png)

# Custom:

The `Custom` error type enables users to define a unique error icon using the `CustomErrorIcon` property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ErrorType="Custom"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            CustomErrorIcon="CustomIcon.png"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBoxCustom = new SfMaskedTextBox();
maskedTextBoxCustom.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBoxCustom.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBoxCustom.Width = 200;
maskedTextBoxCustom.ErrorType = ErrorType.Custom;
maskedTextBoxCustom.CustomErrorIcon = new BitmapImage(new Uri("ms-appx:///CustomIcon.png"));
maskedTextBoxCustom.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Custom](MaskedTextBox_images/winui_masked_textbox_errortype_custom.png)

# CustomErrorBorderBrush:

The `CustomErrorBorderBrush` property sets the color of the bottom border of the MaskedTextBox control.

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
maskedTextBox.CustomErrorBorderBrush = new SolidColorBrush(Colors.Purple);
maskedTextBox.CustomErrorIcon = new BitmapImage(new Uri("ms-appx:///CustomIcon.png"));
maskedTextBox.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Custom](MaskedTextBox_images/winui_masked_textbox_customerrorborderbrush.png)

# ErrorContent:

The `ErrorContent` property is used to display content when hovering over the error icon.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfMaskedTextBox MaskType="RegEx" 
                            Mask="[a-z0-9._%-]+@[a-z0-9]+\.[a-z]{2,3}" 
                            Width="200"
                            ValueChanging="SfMaskedTextBox_ValueChanging"
                            ErrorType="Warning"
                            ErrorContent="Caps not allowed in the mail id"/>

{% endhighlight %}
{% highlight c# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.MaskType = MaskedTextBoxMaskType.RegEx;
maskedTextBox.Mask = "[a-z0-9._%-]+@[a-z0-9]+\\.[a-z]{2,3}";
maskedTextBox.Width = 200;
maskedTextBox.ErrorType = ErrorType.Warning;
maskedTextBox.ErrorContent = "Caps not allowed in the mail id";
maskedTextBox.ValueChanging += SfMaskedTextBox_ValueChanging;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox control with Errortype Custom](MaskedTextBox_images/winui_masked_textbox_errorcontent.png)