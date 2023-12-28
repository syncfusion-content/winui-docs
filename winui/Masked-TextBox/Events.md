---
layout: post
title: Events in WinUI Masked TextBox control | Syncfusion
description: Learn all about the events in the Masked TextBox (SfMaskedTextBox) control.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Events in WinUI Masked TextBox

This section provides information about the events available in the WinUI Masked TextBox control.

## ValueChanging Event

The ValueChanging event occurs when the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property is about to change in the Masked TextBox control. The MaskedTextBoxValueChangingEventArgs provides the following properties:

* NewValue: Gets the current value of the Masked TextBox control.
* OldValue: Gets the previous value of the Masked TextBox control.
* IsValid: Gets or sets a boolean value indicating whether the input is considered valid based on the mask completion.
* Cancel: Gets or sets a value indicating whether the event should be canceled.

{% tabs %}

{% highlight C# %}

private void MaskedTextBox_ValueChanging(object sender, MaskedTextBoxValueChangingEventArgs e)
{
    // Access the new and old values
    string newValue = e.NewValue;
    string oldValue = e.OldValue;

    // Check the validity of the input
    bool isValid = e.IsValid;

    // Cancel the event if needed
    if (newValue == "1234")
    {
        e.Cancel = true;
    }

    // Perform additional actions based on the value changing
    // ...
}

{% endhighlight %}

{% endtabs %}

## ValueChanged Event

The [ValueChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_ValueChanged) event occurs when the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property is changed in the Masked TextBox control. The [MaskedTextBoxValueChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html) provides the following properties:

* [IsMaskCompleted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_IsMaskCompleted): Gets a boolean value indicating whether all the required inputs for the mask are completed.
* [NewValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_NewValue): Gets the current value of the Masked TextBox control.
* [OldValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_OldValue): Gets the previous value of the Masked TextBox control.

{% tabs %}

{% highlight C# %}

private void MaskedTextBox_ValueChanged(object sender, MaskedTextBoxValueChangedEventArgs e)
{
    // Access the new and old values
    string newValue = e.NewValue;
    string oldValue = e.OldValue;

    // Check if the mask input is completed
    bool isMaskCompleted = e.IsMaskCompleted;

    // Perform actions based on the value change
    // ...
}

{% endhighlight %}

{% endtabs %}