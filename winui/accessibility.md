---
layout: post
title: Accessibility support for Syncfusion WinUI Controls | Syncfusion
description: Learn about Accessibility in the Syncfusion WinUI controls, including UI automation, Keyboard, and HighContrast theme support.
platform: winui
control: Accessibility
documentation: ug
---

# Accessibility for Syncfusion WinUI Controls

Accessibility is about making a windows application usable in a wide range of environments by people who use technology and approach a UI with a wide range of experiences. There are many different types of disabilities in the world including mobility, vision, color perception, hearing, speech, cognition, and literacy. However, these requirements can be met by utilizing the accessibility features of Syncfusion UI WinUI controls. The controls support assistive technologies like screen readers, which take advantage of accessibility frameworks.

The following sections explain the accessibility features.

## UI automation

The Syncfusion WinUI control provides accessibility for the UI automation framework as well as the support provided by base classes derived from `FrameworkElementAutomationPeer`. The control class makes use of the UI automation concepts such as automation peers and automation patterns to report the controls' role and content to UI automation clients.

A user can use a tool like screen readers to obtain the necessary information about the controls from UI Automation. When a control receives focus, the screen reader reads the text associated with that control. 

## Keyboard support

Syncfusion WinUI controls provide keyboard support including tab navigation, text input, and control-specific support. For example, the `SfTreeView` control supports arrow-key navigation for item selection.

## High contrast themes

The Windows operating system and applications support all of the high contrast themes that users can enable. These themes make the controls easier to see and are especially useful for people with limited vision.

![HighContrast theme support in Syncfusion WinUI controls](Common-images/winui-highcontrast-controls.png)






