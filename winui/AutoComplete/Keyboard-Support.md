---
layout: post
title: Keyboard Support in WinUI AutoComplete Control | Syncfusion
description: Learn about the keyboard shortcuts and navigation features supported in the Syncfusion WinUI SfAutoComplete control.
platform: winui
control: SfAutoComplete
documentation: UG
---

# Keyboard Support in WinUI AutoComplete (SfAutoComplete)

This section explains the keyboard shortcuts that are supported by the [SfAutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html) control.

> **Requirements**: WinUI 3, Syncfusion WinUI Editors package.

All keys described in the following tables work when the AutoComplete control has focus. The drop-down must be open for the navigation keys to take effect.

## Drop-down open and close

The following table explains the keyboard shortcuts for opening and closing the drop-down.

<table>
<tr>
<th>
Key or Key combinations
</th>
<th>
Behavior
</th>
</tr>
<tr>
<td>
<kbd>Escape</kbd>
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
If the drop-down is already open, pressing the <kbd>Tab</kbd> or <kbd>Shift+Tab</kbd> key will update the selected item and close the drop-down.
</td>
</tr>
</table>

## Item navigation

The following table explains how to use the keyboard shortcuts to navigate and highlight the items in a drop-down list.

<table>
<tr>
<th>
Key or Key combinations
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
Moves the focus and selection to the first item in the drop-down.
</td>
<td>
Moves the focus to the first item in the drop-down.
</td>
</tr>
<tr>
<td>
<kbd>End</kbd>
</td>
<td>
Moves the focus and selection to the last item in the drop-down.
</td>
<td>
Moves the focus to the last item in the drop-down.
</td>
</tr>
<tr>
<td>
<kbd>PageUp</kbd>
</td>
<td>
Moves the focus and selection up by one page of items.
</td>
<td>
Moves the focus up by one page of items.
</td>
</tr>
<tr>
<td>
<kbd>PageDown</kbd>
</td>
<td>
Moves the focus and selection down by one page of items.
</td>
<td>
Moves the focus down by one page of items.
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
Selects the highlighted item and closes the drop-down.
</td>
<td>
Selects the highlighted item and closes the drop-down.
</td>
</tr>
</table>

## Token navigation (multiple selection mode)

The following table explains the keyboard shortcuts for navigating the selected item tokens when the AutoComplete is in multiple selection mode. These keys work when the textbox has focus and there is at least one selected item.

<table>
<tr>
<th>
Key or Key combinations
</th>
<th>
Multiple selection mode
</th>
</tr>
<tr>
<td>
<kbd>Left</kbd>
</td>
<td>
Moves the focus among the selected item tokens from right to left.
</td>
</tr>
<tr>
<td>
<kbd>Right</kbd>
</td>
<td>
Moves the focus among the selected item tokens from left to right.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl+A</kbd>
</td>
<td>
Selects all items in the drop-down list.
</td>
</tr>
<tr>
<td>
<kbd>Backspace</kbd>, <kbd>Delete</kbd>
</td>
<td>
Removes the focused token from the selection.
</td>
</tr>
</table>

## Troubleshooting

* **Drop-down does not open with the keyboard**: Ensure the control has focus and `IsDropDownOpen` is not forced to `false` in code.
* **Navigation keys do not work**: The drop-down must be open. Verify that `ItemsSource` is bound and contains items.
* **Token navigation keys do not respond**: Multiple selection mode must be enabled and at least one item must be selected.

