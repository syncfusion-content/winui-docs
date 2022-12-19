---
layout: post
title: Culture in WinUI MaskedTextBox control | Syncfusion
description: Learn all about the culture in the MaskedTextBox (SfMaskedTextBox) control for the specific set of symbols such as '.', ',', '/', ':' and '$'.
platform: WinUI
control: SfMaskedTextBox
documentation: ug
---

# Culture in WinUI MaskedTextBox

Special symbols like currency symbols, date separators, decimal separators, and others are applied based on the specified culture.

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

{% tabs %}
{% highlight C# %}

SfMaskedTextBox maskedTextBox = new SfMaskedTextBox();
maskedTextBox.Width = "195";
maskedTextBox.MaskType = MaskedTextBoxMaskType.Simple;
maskedTextBox.Mask = "$ 0,000.00";
maskedTextBox.Culture = new CultureInfo("fr-FR");

{% endhighlight %}
{% endtabs %}

Now the ‘$’ will be localized to ‘€’; ‘.’ will be localized to ‘,’ and ‘,’ will be localized to ‘ ‘(single white space).

![WinUI MaskedTextBox culture](MaskedTextBox_Images/winui_masked_textbox_culture.gif)