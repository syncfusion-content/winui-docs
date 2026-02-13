---
layout: post
title: Syncfusion AI Coding Assistant Prompt Library | Syncfusion
description: Explore the AI Coding Assistant Prompt Library to enhance WinUI development productivity with code generation, configuration examples, and contextual guidance.
control: Syncfusion AI Coding Assistant Prompt Library
platform: winui
documentation: ug
---

# Prompt Library - AI Coding Assistant

Speed up your WinUI projects using these ready-made prompts for popular Syncfusion components. Each prompt is short, easy to understand, and focused on real tasks—like quick setups, tweaks, and fixes.

## How to Use

Before starting, make sure your MCP Server is set up and running.

* Choose a prompt that fits your need.
* Copy the full prompt with the #SyncfusionWinUIAssistant handle.
* Customize the prompt for your specific use case.
* Execute via the MCP Server.
* Always check and test the code before adding it to your project.

## Component-Specific Prompts

### DataGrid

The Syncfusion WinUI DataGrid delivers fast, flexible tables for large datasets with built-in interactivity.

{% promptcards %}
{% promptcard Sorting %}
#SyncfusionWinUIAssistant How do I enable sorting in the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Grouping and Filtering %}
#SyncfusionWinUIAssistant Show me an example of grouping and filtering data in the DataGrid component.
{% endpromptcard %}
{% promptcard Editing with Column Types %}
#SyncfusionWinUIAssistant How to configure in-place editing using numeric, text, date, checkbox, image, combo box, picker, and template editors in the DataGrid.
{% endpromptcard %}
{% promptcard Selection and Keyboard Navigation %}
#SyncfusionWinUIAssistant Describe how to enable both single‑row and multiple‑row selection and how to perform programmatic row selection using APIs. Also provide explanation of all supported mouse and keyboard interactions.
{% endpromptcard %}
{% promptcard CRUD Operations %}
#SyncfusionWinUIAssistant Give me the code example to perform full CRUD operations in the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard DataGrid Export to Excel %}
#SyncfusionWinUIAssistant How to export data to Excel in syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Virtual Scrolling %}
#SyncfusionWinUIAssistant How do I configure virtual scrolling for large datasets in the DataGrid?
{% endpromptcard %}
{% promptcard Multicolumn DataGrid Setup %}
#SyncfusionWinUIAssistant Create a DataGrid with multiple columns that displays product details and includes features for sorting and filtering.
{% endpromptcard %}
{% promptcard Load control in a cell/column %}
#SyncfusionWinUIAssistant How can I integrate or load a WinUI control inside each cell or column of the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Advanced DataGrid Features %}
#SyncfusionWinUIAssistant Show me a DataGrid with sorting, grouping, filtering, and virtual scrolling.
{% endpromptcard %}
{% promptcard Troubleshooting DataGrid Export %}
#SyncfusionWinUIAssistant Why isn’t my DataGrid exporting to Excel correctly?
{% endpromptcard %}
{% promptcard Cell Editing %}
#SyncfusionWinUIAssistant How to enable cell editing in the DataGrid?
{% endpromptcard %}
{% promptcard Dynamic Column Configuration %}
#SyncfusionWinUIAssistant How can I add or display the predefined or multi columns in a drop-down in the DataGrid?
{% endpromptcard %}
{% promptcard Drag and drop support %}
#SyncfusionWinUIAssistant How to Drag and Drop a Row in WinUI DataGrid?
{% endpromptcard %}
{% promptcard Styling and Conditional Formatting %}
#SyncfusionWinUIAssistant Customize cell and header styles and apply conditional formatting based on data values in WinUI DataGrid.
{% endpromptcard %}
{% endpromptcards %}

### Chart

The Syncfusion WinUI Chart suite offers versatile visualization tools across various series types for insightful data representation.

{% promptcards %}
{% promptcard Data Binding %}
#SyncfusionWinUIAssistant How to quickly bind data sources to a Syncfusion WinUI Chart for real-time insights?
{% endpromptcard %}
{% promptcard Selection and Highlighting Support %}
#SyncfusionWinUIAssistant How to enable selection and highlighting of data points in WinUI Charts for better analysis?
{% endpromptcard %}
{% promptcard Chart Types Overview %}
#SyncfusionWinUIAssistant What chart types are available in Syncfusion WinUI Chart and how to configure them?
{% endpromptcard %}
{% promptcard Zooming and panning %}
#SyncfusionWinUIAssistant How to enable zooming and panning in WinUI Charts to make large datasets more interactive?
{% endpromptcard %}
{% promptcard Data Label and ToolTip Support %}
#SyncfusionWinUIAssistant Enable tooltips and data labels in Syncfusion WinUI Chart component.
{% endpromptcard %}
{% promptcard Tooltips and Trackball %}
#SyncfusionWinUIAssistant Show interactive tooltips and a trackball with formatted labels and multiple series value display.
{% endpromptcard %}
{% promptcard Axes and Multiple Axes %}
#SyncfusionWinUIAssistant Configure CategoryAxis, NumericalAxis, DateTimeAxis, and add a secondary Y-axis with series mapped to it.
{% endpromptcard %}
{% promptcard Legend and Title %}
#SyncfusionWinUIAssistant Add chart title, subtitle, and a responsive legend (positioning, overflow modes) in a WinUI chart.
{% endpromptcard %}
{% promptcard Series Types Quick Setup %}
#SyncfusionWinUIAssistant Create a chart with Line, Spline, StepLine, Area, SplineArea, Column, Bar, Scatter, and Bubble series.
{% endpromptcard %}
{% promptcard Segment Color Mapping and Gradients %}
#SyncfusionWinUIAssistant Apply segment color mapping and gradient fills based on Y-value ranges.
{% endpromptcard %}
{% promptcard Axis Customization %}
#SyncfusionWinUIAssistant Configure axis intervals, labels format, inversed axis, axis crossing, and logarithmic axis.
{% endpromptcard %}
{% promptcard Gridlines and Chart Area Styling %}
#SyncfusionWinUIAssistant Customize major/minor gridlines, tick lines, chart area background, and border.
{% endpromptcard %}
{% promptcard Animation Support %}
#SyncfusionWinUIAssistant How to enable animations in WinUI Charts to make data visualization more engaging?
{% endpromptcard %}
{% promptcard Multiple Series Types %}
#SyncfusionWinUIAssistant How do I combine bar and line chart types in a single Syncfusion Chart?
{% endpromptcard %}
{% promptcard Custom Labels %}
#SyncfusionWinUIAssistant Show me an example of customizing chart data label styles.
{% endpromptcard %}
{% endpromptcards %}

### AI AssistView

The Syncfusion WinUI AI AssistView provides a ready-made conversational UI for integrating LLMs with features like message list, input box, suggestions, attachments, and tool/action invocation.

{% promptcards %}
{% promptcard Messages %}
#SyncfusionWinUIAssistant Bind AssistView to a message collection with system, user, and pre load conversation history.
{% endpromptcard %}
{% promptcard Streaming and Typing Indicator %}
#SyncfusionWinUIAssistant Enable token streaming with a typing indicator and incremental message updates.
{% endpromptcard %}
{% promptcard Suggestions (Quick Prompts) %}
#SyncfusionWinUIAssistant How to add clickable suggestion chips that insert predefined prompts into the input box.
{% endpromptcard %}
{% promptcard Markdown and Rich Rendering %}
#SyncfusionWinUIAssistant How to render assistant responses with Markdown (headings, code blocks) and support inline images/emojis.
{% endpromptcard %}
{% promptcard Avatars and Message Templates %}
#SyncfusionWinUIAssistant How to customize assistant avatars and use DataTemplate/DataTemplateSelector for message bubbles.
{% endpromptcard %}
{% promptcard Error Handling and Retries %}
#SyncfusionWinUIAssistant How to handle provider errors with retry/cancel UI and graceful fallback messages.
{% endpromptcard %}
{% promptcard Theming and Styling %}
#SyncfusionWinUIAssistant Apply custom themes for message bubbles, background, input bar, and suggestion chips (Light/Dark support).
{% endpromptcard %}
{% promptcard Command/Enter Behavior %}
#SyncfusionWinUIAssistant Configure Enter to send and Shift+Enter for newline; support multiline input with character counter.
{% endpromptcard %}
{% promptcard Citations and References %}
#SyncfusionWinUIAssistant Display citations/references returned by the model as hyper links under the message.
{% endpromptcard %}
{% endpromptcards %}

### Scheduler

The Syncfusion WinUI Scheduler helps manage events, resources, and timelines with powerful views and customization.

{% promptcards %}
{% promptcard Views and Quick Switch %}
#SyncfusionWinUIAssistant Configure Day, Week, Month, Timeline Day/Week/WorkWeek/Month views and add quick view switching.
{% endpromptcard %}
{% promptcard Appointment Mapping and Data Binding %}
#SyncfusionWinUIAssistant How to bind custom appointment models using mapping (subject, notes, location, start time, end time) with MVVM.
{% endpromptcard %}
{% promptcard Recurring Events and Series Editing %}
#SyncfusionWinUIAssistant Create recurring appointments (daily/weekly/monthly/yearly) and enable editing a single occurrence or the entire series.
{% endpromptcard %}
{% promptcard Time Zones %}
#SyncfusionWinUIAssistant Show appointments in the WinUI Scheduler control for specific time zones.
{% endpromptcard %}
{% promptcard Work Time, Work Days, and First Day of Week %}
#SyncfusionWinUIAssistant How to set working hours, configure work days and customize the first day of week.
{% endpromptcard %}
{% promptcard Min/Max Date Navigation Limits %}
#SyncfusionWinUIAssistant How to restrict navigation with MinimumDateTime and MaximumDateTime to keep users in a valid planning range.
{% endpromptcard %}
{% promptcard Special Time Regions (Blocking Intervals) %}
#SyncfusionWinUIAssistant Define special time regions to block interaction (e.g., holidays/breaks) and highlight them across views.
{% endpromptcard %}
{% promptcard Blackout Dates for MonthView %}
#SyncfusionWinUIAssistant Disable specific dates like weekends or holidays to prevent selection and interaction for month view.
{% endpromptcard %}
{% promptcard Drag-and-Drop %}
#SyncfusionWinUIAssistant Enable drag to reschedule, resize to change duration for quick appointment updates.
{% endpromptcard %}
{% promptcard Resources and Grouping %}
#SyncfusionWinUIAssistant Group by resources (rooms/people/teams) with color-coding and timeline views optimized for many resources.
{% endpromptcard %}
{% promptcard Load on Demand %}
#SyncfusionWinUIAssistant Load appointments on demand with a loading indicator for large schedules.
{% endpromptcard %}
{% promptcard Reminders and Notifications Integration %}
#SyncfusionWinUIAssistant Add reminder metadata to appointments and integrate with app notifications for alerts.
{% endpromptcard %}
{% promptcard Theming and Customization %}
#SyncfusionWinUIAssistant How to style headers, cells, appointments, selection, and special regions; support Light/Dark themes.
{% endpromptcard %}
{% endpromptcards %}

### Calendar

The Syncfusion WinUI Calendar supports flexible date selection, localization, and custom rendering.

{% promptcards %}
{% promptcard Date Range Selection %}
#SyncfusionWinUIAssistant How to enable date range selection in the Syncfusion WinUI Calendar?
{% endpromptcard %}
{% promptcard Globalization Support %}
#SyncfusionWinUIAssistant Configure the Calendar to support multiple cultures and languages.
{% endpromptcard %}
{% promptcard Multi-Date Selection %}
#SyncfusionWinUIAssistant Show me how to allow users to select multiple dates in the Calendar.
{% endpromptcard %}
{% promptcard Blackout Dates %}
#SyncfusionWinUIAssistant How to add the blackout dates in the WinUI calendar?
{% endpromptcard %}
{% promptcard Week Number %}
#SyncfusionWinUIAssistant How to show week number in the WinUI calendar?
{% endpromptcard %}
{% promptcard Show Other Month Days %}
#SyncfusionWinUIAssistant How to show days from adjacent months in the current Calendar view?
{% endpromptcard %}
{% promptcard Custom Day Cell Format %}
#SyncfusionWinUIAssistant Customize the day cell format in the Calendar to show short weekday names.
{% endpromptcard %}
{% promptcard Multi-Selection and Range %}
#SyncfusionWinUIAssistant Enable both multi-date selection and range selection in the Calendar.
{% endpromptcard %}
{% promptcard Troubleshooting Date Range %}
#SyncfusionWinUIAssistant Why isn’t my Calendar selecting the correct date range?
{% endpromptcard %}
{% promptcard Advanced Calendar Setup %}
#SyncfusionWinUIAssistant Create a Calendar with date range, multi-selection, globalization, and weekend highlights.
{% endpromptcard %}
{% endpromptcards %}

### Ribbon

The Syncfusion WinUI Ribbon is a command bar that organizes an application’s tools into tabs and supports a Backstage view similar to Microsoft Office.

{% promptcards %}
{% promptcard Add Ribbon Items %}
#SyncfusionWinUIAssistant Add RibbonTab, RibbonGroup, RibbonButton, RibbonDropDownButton, and RibbonComboBox in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Backstage %}
#SyncfusionWinUIAssistant Configure Backstage with pages, navigation, and commands in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Quick Access Toolbar (QAT) %}
#SyncfusionWinUIAssistant Add, remove, and position it above or below the WinUI Ribbon?
{% endpromptcard %}
{% promptcard ScreenTips %}
#SyncfusionWinUIAssistant Create ScreenTips with Title and content for WinUI Ribbon items?
{% endpromptcard %}
{% promptcard KeyTips %}
#SyncfusionWinUIAssistant How to enable and customize KeyTips for keyboard navigation in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Simplified Layout %}
#SyncfusionWinUIAssistant Enable simplified layout and configure group resizing behavior in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Contextual Tabs %}
#SyncfusionWinUIAssistant Create contextual RibbonTab groups and show or hide them based on selection or app state?
{% endpromptcard %}
{% promptcard Ribbon Gallery %}
#SyncfusionWinUIAssistant How to build Ribbon gallery with item templates, and selection change handling in WinUI Ribbon?
{% endpromptcard %}
{% promptcard Localization and RTL %}
#SyncfusionWinUIAssistant How to localize WinUI Ribbon text and tooltips and enable right-to-left (RTL) layout?
{% endpromptcard %}
{% promptcard Theming %}
#SyncfusionWinUIAssistant How to style ribbon items, screen tip, key tip and QAT; support Light/Dark themes.
{% endpromptcard %}
{% promptcard Group Resizing Policies %}
#SyncfusionWinUIAssistant How to configure Ribbon group size definitions (Large, Normal, Small) and item collapsing for narrow widths?
{% endpromptcard %}
{% endpromptcards %}

### ComboBox

The WinUI ComboBox control (multi-select ComboBox) is an editable, searchable selection component that supports data binding, auto-complete, filtering, and custom item templates.

{% promptcards %}
{% promptcard Editing %}
#SyncfusionWinUIAssistant Restrict editing WinUI ComboBox.
{% endpromptcard %}
{% promptcard Selection %}
#SyncfusionWinUIAssistant Enable multiple selection with checkboxes in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Filtering %}
#SyncfusionWinUIAssistant Enable filtering in WinUI ComboBox.
{% endpromptcard %}
{% promptcard Searching %}
#SyncfusionWinUIAssistant Highlight matching items during search in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard PlaceholderText  %}
#SyncfusionWinUIAssistant Display watermark text inside the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Customization %}
#SyncfusionWinUIAssistant Customize dropdown list items with images or custom controls in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Styling %}
#SyncfusionWinUIAssistant Apply conditional styling to dropdown items in WinUI ComboBox.
{% endpromptcard %}
{% promptcard Highlighting %}
#SyncfusionWinUIAssistant Highlight unmatched characters during search in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Leading & Trailing Views %}
#SyncfusionWinUIAssistant Add trailing views after the selection content in the WinUI ComboBox
{% endpromptcard %}
{% endpromptcards %}

### NumberBox

The WinUI NumberBox control provides an intuitive and advanced editor control that allows you to enter numeric values in currency, percent, decimal formats and validates the user input independent of the custom format applied.
{% promptcards %}
{% promptcard Editing %}
#SyncfusionWinUIAssistant Prevent users from editing the numerical value directly in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Value Formatting %}
#SyncfusionWinUIAssistant Format values as currency, percent, decimal, or apply custom numeric format strings in WinUI NumberBox.
{% endpromptcard %}
{% promptcard Input Restriction %}
#SyncfusionWinUIAssistant Restrict input to numeric values, control negative inputs, and limit the number of integer or fractional digits in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Watermark %}
#SyncfusionWinUIAssistant Display and customize watermark or placeholder text in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Keyboard / Mouse / Up Down  %}
#SyncfusionWinUIAssistant Change values in the WinUI NumberBox using keyboard input, mouse scrolling, and the up/down buttons.
{% endpromptcard %}
{% promptcard Header & Description %}
#SyncfusionWinUIAssistant Add the header and description for the WinUI NumberBox.
{% endpromptcard %}
{% promptcard ValueChanged Event %}
#SyncfusionWinUIAssistant Notify value updates in the WinUI NumberBox.
{% endpromptcard %}
{% endpromptcards %}

## See also

* [AI Coding Assistant Overview](https://help.syncfusion.com/winui/ai-coding-assistant/overview)
* [SyncfusionWinUIAssistant MCP Server](https://help.syncfusion.com/winui/ai-coding-assistant/mcp-server)
