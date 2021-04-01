---
layout: post
title: Accessibility support for Syncfusion WinUI Controls | Syncfusion
description: Learn about Accessibility in the Syncfusion WinUI controls, including UI automation, Keyborad and HighContrast theme support.
platform: winui
control: Accessibility
documentation: ug
---

# Accessibility

Accessibility is about making your windows application usable in a wide range of environments by people who use technology and approach your UI with a wide range of experiences. There are many different types of disabilities in the world, including mobility, vision, color perception, hearing, speech, cognition, and literacy. However, These requirements can be met by utilizing the accessibility features of Syncfusion UI WinUI controls. The controls support assistive technologies such as screen readers, which take advantage of accessibility frameworks.

The sections below explain the accessibility features.

## UI Automation

All controls have built-in accessibility for the UI automation framework and support provided by base classes which derived from FrameworkElementAutomationPeer. Syncfusion WinUI control class also uses the UI Automation concepts of automation peers and automation patterns that report the control's role and content to UI Automation clients.

A user can use a tool like screen readers to obtain the necessary information about the controls from UI Automation. When a control receives focus, the screen reader reads the text associated with that control. 

## Keyboard Support

The basic xaml control proivdes built-in keyboard support including tab navigation, text input, and control-specific support. Syncfusion WinUI controls also have the same features in it. For example, If you use `SfTreeView` controls to display the data, it provides arrow-key navigation.

## High Contrast Themes

The Windows operating system and applications support all of the high contrast themes that users can enable and these themes make the controls more efficient to see and are especially useful for people with limited vision.

![HighContast theme for Syncfusion WinUI Ribbon](Common-Images/Common-image1.png)






