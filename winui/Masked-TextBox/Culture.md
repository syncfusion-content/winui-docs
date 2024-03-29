---
layout: post
title: Culture in WinUI Masked TextBox control | Syncfusion
description: Learn all about how to set the different culture support for currency symbols, date, time, decimal, and group separators in the Masked TextBox control.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Culture in WinUI Masked TextBox

The Masked TextBox allows you to set any [Culture](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfMaskedTextBox.html#Syncfusion_UI_Xaml_Editors_SfMaskedTextBox_Culture) support for currency symbols, date separators, time separators, group separators, and decimal separators by using the below special symbols.

<table>
<tr>
<th>
Characters</th><th>
Description</th>
</tr>
<tr>
<td>
.
</td>
<td>
Decimal separator determined by current culture.
</td>
</tr>
<tr>
<td>
,
</td>
<td>
Group separator determined by current culture.
</td>
</tr>
<tr>
<td>
/
</td>
<td>
Date separator determined by current culture.
</td>
</tr>
<tr>
<td>
:
</td>
<td>
Time separator determined by current culture.
</td>
</tr>
<tr>
<td>
$
</td>
<td>
Currency symbol determined by current culture.
</td>
</tr>
</table>

The following example shows how to set the the France culture for currency symbol, group separator and decimal separator.

{% tabs %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "200";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "$ 0,000.00";
maskedTextBox.Culture = new CultureInfo("fr-FR");

{% endhighlight %}
{% endtabs %}

Based on the France Culture, the ‘$’ will be localized to ‘€’; ‘.’ will be localized to ‘,’ and ‘,’ will be localized to ‘ ‘(single white space).

![WinUI Masked TextBox culture](MaskedTextBox_Images/winui_masked_textbox_culture.gif)