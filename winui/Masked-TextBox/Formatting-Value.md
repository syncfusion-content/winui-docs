---
layout: post
title: Mask formats in WinUI MaskedTextBox control | Syncfusion
description: Learn all about how to set the mask format for the value in the MaskedTextBox (SfMaskedTextBox) control with prompts and literals.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Formatting value in WinUI MaskedTextBox

The `MaskedTextBox` control allows you to format input values with prompt and literal characters which are defined in the mask expression by setting the `ValueMaskFormat` property. By default, the `Value` property of the control includes the characters typed by the user, as well as any prompt or literal characters in the input. The control provides several formatting options, which are listed below.

1. ExcludePromptAndLiterals
2. IncludePrompt
3. IncludeLiterals
4. IncludePromptAndLiterals

## Exclude prompts and literals

Set up the MaskedTextBox to exclude prompt and literal characters, preserving only the typed characters.

### Example

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox x:Name="sfMaskedTextBox"
                            Width="195"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="ExcludePromptAndLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "195";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.ExcludePromptAndLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox excludes prompts and literals](MaskedTextBox_Images/winui_masked_textbox_exclude_prompts_and_literals.png)

## Include prompts

Set up the MaskedTextBox to preserve typed and prompt characters, excluding literals.

### Example

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox x:Name="sfMaskedTextBox"
                            Width="195"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludePrompt"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "195";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludePrompt;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox includes prompts](MaskedTextBox_Images/winui_masked_textbox_include_prompts.png)

## Include literals

Keep typed and literal characters in the input but exclude prompt characters.

### Example

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox x:Name="sfMaskedTextBox"
                            Width="195"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludeLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "195";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludeLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox includes literals](MaskedTextBox_Images/winui_masked_textbox_include_literals.png)

## Include prompts and literals

Maintain typed, prompt, and literal characters in the input.

### Example

{% tabs %}
{% highlight XAML %}

<syncfusion:SfMaskedTextBox x:Name="sfMaskedTextBox"
                            Width="195"
                            MaskType="Simple"
                            Mask=">AAAAA-AAAAA-AAAAA-AAAAA"
                            Value="DF321SD1A"
                            ValueMaskFormat="IncludePromptAndLiterals"/>

{% endhighlight %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "195";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = ">AAAAA-AAAAA-AAAAA-AAAAA";
maskedTextBox.Value = "DF321SD1A";
maskedTextBox.ValueMaskFormat = MaskedTextBoxMaskFormat.IncludePromptAndLiterals;

{% endhighlight %}
{% endtabs %}

![WinUI MaskedTextBox includes prompts and literals](MaskedTextBox_Images/winui_masked_textbox_include_prompts-and_literals.png)