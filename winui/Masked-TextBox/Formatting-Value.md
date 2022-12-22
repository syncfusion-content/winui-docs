---
layout: post
title: Mask formats in WinUI Masked TextBox control | Syncfusion
description: Learn all about how to set the mask format for the value in the Masked TextBox (SfMaskedTextBox) control with prompts and literals.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Formatting value in WinUI Masked TextBox

The `Masked TextBox` control allows you to format input values with prompt and literal characters which are defined in the mask expression by setting the [ValueMaskFormat](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_ValueMaskFormat) property. By default, the [Value](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Value) property of the control includes the characters typed by the user, as well as any prompt or literal characters in the input. The control provides several formatting options, which are listed below.

1. ExcludePromptAndLiterals
2. IncludePrompt
3. IncludeLiterals
4. IncludePromptAndLiterals

## Exclude prompts and literals

Set up the Masked TextBox to exclude prompt and literal characters, preserving only the typed characters.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox Width="200"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="ExcludePromptAndLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.ExcludePromptAndLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI Masked TextBox excludes prompts and literals](MaskedTextBox_Images/winui_masked_textbox_exclude_prompts_and_literals.png)

## Include prompts

Set up the Masked TextBox to preserve typed and prompt characters, excluding literals.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox Width="200"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludePrompt"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludePrompt;

{% endhighlight %}
{% endtabs %}

![WinUI Masked TextBox includes prompts](MaskedTextBox_Images/winui_masked_textbox_include_prompts.png)

## Include literals

Keep typed and literal characters in the input but exclude prompt characters.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox Width="200"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludeLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludeLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI Masked TextBox includes literals](MaskedTextBox_Images/winui_masked_textbox_include_literals.png)

## Include prompts and literals

Maintain typed, prompt, and literal characters in the input.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox Width="200"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludePromptAndLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludePromptAndLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI Masked TextBox includes prompts and literals](MaskedTextBox_Images/winui_masked_textbox_include_prompts-and_literals.png)