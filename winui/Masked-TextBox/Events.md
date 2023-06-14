---
layout: post
title: Events in WinUI MaskedTextBox control | Syncfusion
description: Learn all about the events in the MaskedTextBox (SfMaskedTextBox) control.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Events in WinUI MaskedTextBox

This section explains the events available in the WinUI MaskedTextBox control.

## ValueChanging

The ValueChanging event occurs when the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property is changing in the MaskedTextBox control. 

The MaskedTextBoxValueChangingEventArgs object contains the following properties:

* NewValue: Returns the current value of the MaskedTextBox control.
* OldValue: Returns the previous value of the MaskedTextBox control.
* IsValid: Gets or sets a boolean value indicating whether the input is considered valid according to mask completion.
* Cancel: Gets or sets a value indicating whether the event should be canceled.

## ValueChanged

The [ValueChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_ValueChanged) event occurs when the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property is changed in the MaskedTextBox control. 

The [MaskedTextBoxValueChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html) object contains the following properties:

* [IsMaskCompleted](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_IsMaskCompleted): Returns the boolean value based on whether all the required inputs value is completed.
* [NewValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_NewValue): Returns the current value of the MaskedTextBox control.
* [OldValue](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.MaskedTextBoxValueChangedEventArgs.html#Syncfusion_UI_Xaml_Editors_MaskedTextBoxValueChangedEventArgs_OldValue): Returns the previous value of the MaskedTextBox control.