---
layout: post
title: Keyboard support in WinUI ComboBox control | Syncfusion
description: Learn here all about Keyboard support in Syncfusion WinUI ComboBox (multi-select ComboBox) control and more.
platform: winui
control: SfComboBox
documentation: ug
---

# Keyboard support in WinUI ComboBox

This section explains the shortcut keys that supported in SfComboBox. 

## Keyboard behaviors

The following table explains shortcut key for opening and closing drop-down.

<table>
<tr>
<th>
Key or KeyCombinations
</th>
<th>
Non-editable mode
</th>
<th>
Editable mode
</th>
</tr>
<tr>
<td>
<kbd>F4</kbd>
</td>
<td>
To open or close the drop-down.
</td>
<td>
To open or close the drop-down.
</td>
</tr>
<tr>
<td>
<kbd>Alt+Down</kbd>
</td>
<td>
To open or close the drop-down.
</td>
<td>
-
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
**Single selection** To open or close the drop-down. If the drop-down is already open, pressing the <kbd>Enter</kbd> key item will update the selected item and close the drop-down.
<br />
**Multiple selection** To open the drop-down when it is closed.
</td>
<td>
If the drop-down is already open, pressing the <kbd>Enter</kbd> key will update the selected item and close the drop-down.
</td>
</tr>
<tr>
<td>
<kbd>Up</kbd>, <kbd>Down</kbd>
</td>
<td>
-
</td>
<td>
To open the drop-down when it is closed.
</td>
</tr>
<tr>
<td>
<kbd>Escape</kbd>
</td>
<td>
**Single selection** If the drop-down is already open, pressing the <kbd>Escape</kbd> key will cancel the selection and close the drop-down.
<br />
**Multiple selection** If the drop-down is already open, pressing the <kbd>Escape</kbd> key will close the drop-down.
</td>
<td>
If the drop-down is already open, pressing the <kbd>Escape</kbd> key will cancel the selection and close the drop-down.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>
</td>
<td>
**Single selection** If the drop-down is already open, pressing the <kbd>Tab</kbd> or <kbd>Shift+Tab</kbd> key will update the selected item and close the drop-down. 
<br />
**Multiple selection** If the drop-down is already open, pressing the <kbd>Tab</kbd> or <kbd>Shift+Tab</kbd> key will close the drop-down.
</td>
<td>
If the drop-down is already open, pressing the <kbd>Tab</kbd> or <kbd>Shift+Tab</kbd> key will update selected item and close the drop-down.
</td>
</tr>
</table>

The following table explains shortcut key to navigate and highlight the items in drop-down list.

<table>
<tr>
<th>
Key or KeyCombinations
</th>
<th>
Single selection mode
</th>
<th>
Multiple selection mode
</th>
</tr>
<tr>
<td>
<kbd>Up</kbd>, <kbd>Ctrl+Up</kbd>, <kbd>Shift+Up</kbd>
</td>
<td>
Moves the focus and selection to the previous item from the current focused item.
</td>
<td>
Moves the focus to the previous item from the current focused item.
</td>
</tr>
<tr>
<td>
<kbd>Down</kbd>, <kbd>Ctrl+Down</kbd>, <kbd>Shift+Down</kbd>
</td>
<td>
Moves the focus and selection to the next item from the current focused item.
</td>
<td>
Moves the focus to the next item from the current focused item.
</td>
</tr>
<tr>
<td>
<kbd>Home</kbd>
</td>
<td>
Moves the focus and selection to the first item.
</td>
<td>
Moves the focus to the first item.
</td>
</tr>
<tr>
<td>
<kbd>End</kbd>
</td>
<td>
Moves the focus and selection to the last item.
</td>
<td>
Moves the focus to the last item.
</td>
</tr>
<tr>
<td>
<kbd>PageUp</kbd>
</td>
<td>
Move the selection up on the first fully visible item on the current page. If the first fully visible item is selected, move the selection on the first fully visible item on the previous page. 
</td>
<td>
Move the focus up on the first fully visible item on the current page. If the first fully visible item is focused, move the focus on the first fully visible item on the previous page. 
</td>
</tr>
<tr>
<td>
<kbd>PageDown</kbd>
</td>
<td>
Move the selection down on the last fully visible item on the current page. If the last fully visible item is selected, move the selection on the last fully visible item on the next page.
</td>
<td>
Move the focus down on the last fully visible item on the current page. If the last fully visible item is focused, move the focus on the last fully visible item on the next page.
</td>
</tr>
</table>