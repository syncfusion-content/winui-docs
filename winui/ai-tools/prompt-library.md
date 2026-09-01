---
layout: post
title: Syncfusion® AI Coding Assistant Prompt Library | Syncfusion®
description: Explore the AI Coding Assistant Prompt Library to enhance WinUI development productivity with code generation, configuration examples, and contextual guidance.
control: Syncfusion® AI Coding Assistant Prompt Library
platform: winui
documentation: ug
---

# Prompt Library for Syncfusion® AI Coding Assistants Tools

Speed up your WinUI projects using these ready-made prompts for popular Syncfusion components. Each prompt is short, easy to understand, and focused on real tasks—like quick setups, tweaks, and fixes.

## How to Use

* Choose a prompt that fits your needs.
* Customize the prompt as needed before running it.
* Run the prompt using either of the following AI tools:
    - **Skills:** Skills can also run automatically based on the query, or can be called explicitly using the /syncfusion-winui-datagrid skill.
    - **MCP Server:** Tool can start automatically based on the query, or can be invoked explicitly using #search_docs.
* Always review and test the generated code before adding it to the project.

## Component-Specific Prompts

### DataGrid

The Syncfusion WinUI DataGrid delivers fast, flexible tables for large datasets with built-in interactivity.

{% promptcards %}
{% promptcard Sorting %}
How do I enable sorting in the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Grouping and Filtering %}
Show me an example of grouping and filtering data in the DataGrid component.
{% endpromptcard %}
{% promptcard Editing with Column Types %}
How to configure in-place editing using numeric, text, date, checkbox, image, combo box, picker, and template editors in the DataGrid.
{% endpromptcard %}
{% promptcard Selection and Keyboard Navigation %}
Describe how to enable both single‑row and multiple‑row selection and how to perform programmatic row selection using APIs. Also provide explanation of all supported mouse and keyboard interactions.
{% endpromptcard %}
{% promptcard CRUD Operations %}
Give me the code example to perform full CRUD operations in the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard DataGrid Export to Excel %}
How to export data to Excel in syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Virtual Scrolling %}
How do I configure virtual scrolling for large datasets in the DataGrid?
{% endpromptcard %}
{% promptcard Multicolumn DataGrid Setup %}
Create a DataGrid with multiple columns that displays product details and includes features for sorting and filtering.
{% endpromptcard %}
{% promptcard Load control in a cell/column %}
How can I integrate or load a WinUI control inside each cell or column of the Syncfusion WinUI DataGrid?
{% endpromptcard %}
{% promptcard Advanced DataGrid Features %}
Show me a DataGrid with sorting, grouping, filtering, and virtual scrolling.
{% endpromptcard %}
{% promptcard Troubleshooting DataGrid Export %}
Why isn’t my DataGrid exporting to Excel correctly?
{% endpromptcard %}
{% promptcard Cell Editing %}
How to enable cell editing in the DataGrid?
{% endpromptcard %}
{% promptcard Dynamic Column Configuration %}
How can I add or display the predefined or multi columns in a drop-down in the DataGrid?
{% endpromptcard %}
{% promptcard Drag and drop support %}
How to Drag and Drop a Row in WinUI DataGrid?
{% endpromptcard %}
{% promptcard Styling and Conditional Formatting %}
Customize cell and header styles and apply conditional formatting based on data values in WinUI DataGrid.
{% endpromptcard %}
{% endpromptcards %}

### Chart

The Syncfusion WinUI Chart suite offers versatile visualization tools across various series types for insightful data representation.

{% promptcards %}
{% promptcard Data Binding %}
How to quickly bind data sources to a Syncfusion WinUI Chart for real-time insights?
{% endpromptcard %}
{% promptcard Selection and Highlighting Support %}
How to enable selection and highlighting of data points in WinUI Charts for better analysis?
{% endpromptcard %}
{% promptcard Chart Types Overview %}
What chart types are available in Syncfusion WinUI Chart and how to configure them?
{% endpromptcard %}
{% promptcard Zooming and panning %}
How to enable zooming and panning in WinUI Charts to make large datasets more interactive?
{% endpromptcard %}
{% promptcard Data Label and ToolTip Support %}
Enable tooltips and data labels in Syncfusion WinUI Chart component.
{% endpromptcard %}
{% promptcard Tooltips and Trackball %}
Show interactive tooltips and a trackball with formatted labels and multiple series value display.
{% endpromptcard %}
{% promptcard Axes and Multiple Axes %}
Configure CategoryAxis, NumericalAxis, DateTimeAxis, and add a secondary Y-axis with series mapped to it.
{% endpromptcard %}
{% promptcard Legend and Title %}
Add chart title, subtitle, and a responsive legend (positioning, overflow modes) in a WinUI chart.
{% endpromptcard %}
{% promptcard Series Types Quick Setup %}
Create a chart with Line, Spline, StepLine, Area, SplineArea, Column, Bar, Scatter, and Bubble series.
{% endpromptcard %}
{% promptcard Segment Color Mapping and Gradients %}
Apply segment color mapping and gradient fills based on Y-value ranges.
{% endpromptcard %}
{% promptcard Axis Customization %}
Configure axis intervals, labels format, inversed axis, axis crossing, and logarithmic axis.
{% endpromptcard %}
{% promptcard Gridlines and Chart Area Styling %}
Customize major/minor gridlines, tick lines, chart area background, and border.
{% endpromptcard %}
{% promptcard Animation Support %}
How to enable animations in WinUI Charts to make data visualization more engaging?
{% endpromptcard %}
{% promptcard Multiple Series Types %}
How do I combine bar and line chart types in a single Syncfusion Chart?
{% endpromptcard %}
{% promptcard Custom Labels %}
Show me an example of customizing chart data label styles.
{% endpromptcard %}
{% endpromptcards %}

### AI AssistView

The Syncfusion WinUI AI AssistView provides a ready-made conversational UI for integrating LLMs with features like message list, input box, suggestions, attachments, and tool/action invocation.

{% promptcards %}
{% promptcard Messages %}
Bind AssistView to a message collection with system, user, and pre load conversation history.
{% endpromptcard %}
{% promptcard Streaming and Typing Indicator %}
Enable token streaming with a typing indicator and incremental message updates.
{% endpromptcard %}
{% promptcard Suggestions (Quick Prompts) %}
How to add clickable suggestion chips that insert predefined prompts into the input box.
{% endpromptcard %}
{% promptcard Markdown and Rich Rendering %}
How to render assistant responses with Markdown (headings, code blocks) and support inline images/emojis.
{% endpromptcard %}
{% promptcard Avatars and Message Templates %}
How to customize assistant avatars and use DataTemplate/DataTemplateSelector for message bubbles.
{% endpromptcard %}
{% promptcard Error Handling and Retries %}
How to handle provider errors with retry/cancel UI and graceful fallback messages.
{% endpromptcard %}
{% promptcard Theming and Styling %}
Apply custom themes for message bubbles, background, input bar, and suggestion chips (Light/Dark support).
{% endpromptcard %}
{% promptcard Command/Enter Behavior %}
Configure Enter to send and Shift+Enter for newline; support multiline input with character counter.
{% endpromptcard %}
{% promptcard Citations and References %}
Display citations/references returned by the model as hyper links under the message.
{% endpromptcard %}
{% endpromptcards %}

### Scheduler

The Syncfusion WinUI Scheduler helps manage events, resources, and timelines with powerful views and customization.

{% promptcards %}
{% promptcard Views and Quick Switch %}
Configure Day, Week, Month, Timeline Day/Week/WorkWeek/Month views and add quick view switching.
{% endpromptcard %}
{% promptcard Appointment Mapping and Data Binding %}
How to bind custom appointment models using mapping (subject, notes, location, start time, end time) with MVVM.
{% endpromptcard %}
{% promptcard Recurring Events and Series Editing %}
Create recurring appointments (daily/weekly/monthly/yearly) and enable editing a single occurrence or the entire series.
{% endpromptcard %}
{% promptcard Time Zones %}
Show appointments in the WinUI Scheduler control for specific time zones.
{% endpromptcard %}
{% promptcard Work Time, Work Days, and First Day of Week %}
How to set working hours, configure work days and customize the first day of week.
{% endpromptcard %}
{% promptcard Min/Max Date Navigation Limits %}
How to restrict navigation with MinimumDateTime and MaximumDateTime to keep users in a valid planning range.
{% endpromptcard %}
{% promptcard Special Time Regions (Blocking Intervals) %}
Define special time regions to block interaction (e.g., holidays/breaks) and highlight them across views.
{% endpromptcard %}
{% promptcard Blackout Dates for MonthView %}
Disable specific dates like weekends or holidays to prevent selection and interaction for month view.
{% endpromptcard %}
{% promptcard Drag-and-Drop %}
Enable drag to reschedule, resize to change duration for quick appointment updates.
{% endpromptcard %}
{% promptcard Resources and Grouping %}
Group by resources (rooms/people/teams) with color-coding and timeline views optimized for many resources.
{% endpromptcard %}
{% promptcard Load on Demand %}
Load appointments on demand with a loading indicator for large schedules.
{% endpromptcard %}
{% promptcard Reminders and Notifications Integration %}
Add reminder metadata to appointments and integrate with app notifications for alerts.
{% endpromptcard %}
{% promptcard Theming and Customization %}
How to style headers, cells, appointments, selection, and special regions; support Light/Dark themes.
{% endpromptcard %}
{% endpromptcards %}

### Calendar

The Syncfusion WinUI Calendar supports flexible date selection, localization, and custom rendering.

{% promptcards %}
{% promptcard Date Range Selection %}
How to enable date range selection in the Syncfusion WinUI Calendar?
{% endpromptcard %}
{% promptcard Globalization Support %}
Configure the Calendar to support multiple cultures and languages.
{% endpromptcard %}
{% promptcard Multi-Date Selection %}
Show me how to allow users to select multiple dates in the Calendar.
{% endpromptcard %}
{% promptcard Blackout Dates %}
How to add the blackout dates in the WinUI calendar?
{% endpromptcard %}
{% promptcard Week Number %}
How to show week number in the WinUI calendar?
{% endpromptcard %}
{% promptcard Show Other Month Days %}
How to show days from adjacent months in the current Calendar view?
{% endpromptcard %}
{% promptcard Custom Day Cell Format %}
Customize the day cell format in the Calendar to show short weekday names.
{% endpromptcard %}
{% promptcard Multi-Selection and Range %}
Enable both multi-date selection and range selection in the Calendar.
{% endpromptcard %}
{% promptcard Troubleshooting Date Range %}
Why isn’t my Calendar selecting the correct date range?
{% endpromptcard %}
{% promptcard Advanced Calendar Setup %}
Create a Calendar with date range, multi-selection, globalization, and weekend highlights.
{% endpromptcard %}
{% endpromptcards %}

### Ribbon

The Syncfusion WinUI Ribbon is a command bar that organizes an application’s tools into tabs and supports a Backstage view similar to Microsoft Office.

{% promptcards %}
{% promptcard Add Ribbon Items %}
Add RibbonTab, RibbonGroup, RibbonButton, RibbonDropDownButton, and RibbonComboBox in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Backstage %}
Configure Backstage with pages, navigation, and commands in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Quick Access Toolbar (QAT) %}
Add, remove, and position it above or below the WinUI Ribbon?
{% endpromptcard %}
{% promptcard ScreenTips %}
Create ScreenTips with Title and content for WinUI Ribbon items?
{% endpromptcard %}
{% promptcard KeyTips %}
How to enable and customize KeyTips for keyboard navigation in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Simplified Layout %}
Enable simplified layout and configure group resizing behavior in the WinUI Ribbon?
{% endpromptcard %}
{% promptcard Contextual Tabs %}
Create contextual RibbonTab groups and show or hide them based on selection or app state?
{% endpromptcard %}
{% promptcard Ribbon Gallery %}
How to build Ribbon gallery with item templates, and selection change handling in WinUI Ribbon?
{% endpromptcard %}
{% promptcard Localization and RTL %}
How to localize WinUI Ribbon text and tooltips and enable right-to-left (RTL) layout?
{% endpromptcard %}
{% promptcard Theming %}
How to style ribbon items, screen tip, key tip and QAT; support Light/Dark themes.
{% endpromptcard %}
{% promptcard Group Resizing Policies %}
How to configure Ribbon group size definitions (Large, Normal, Small) and item collapsing for narrow widths?
{% endpromptcard %}
{% endpromptcards %}

### ComboBox

The WinUI ComboBox control (multi-select ComboBox) is an editable, searchable selection component that supports data binding, auto-complete, filtering, and custom item templates.

{% promptcards %}
{% promptcard Editing %}
Restrict editing WinUI ComboBox.
{% endpromptcard %}
{% promptcard Selection %}
Enable multiple selection with checkboxes in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Filtering %}
Enable filtering in WinUI ComboBox.
{% endpromptcard %}
{% promptcard Searching %}
Highlight matching items during search in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard PlaceholderText  %}
Display watermark text inside the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Customization %}
Customize dropdown list items with images or custom controls in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Styling %}
Apply conditional styling to dropdown items in WinUI ComboBox.
{% endpromptcard %}
{% promptcard Highlighting %}
Highlight unmatched characters during search in the WinUI ComboBox.
{% endpromptcard %}
{% promptcard Leading & Trailing Views %}
Add trailing views after the selection content in the WinUI ComboBox
{% endpromptcard %}
{% endpromptcards %}

### NumberBox

The WinUI NumberBox control provides an intuitive and advanced editor control that allows you to enter numeric values in currency, percent, decimal formats and validates the user input independent of the custom format applied.
{% promptcards %}
{% promptcard Editing %}
Prevent users from editing the numerical value directly in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Value Formatting %}
Format values as currency, percent, decimal, or apply custom numeric format strings in WinUI NumberBox.
{% endpromptcard %}
{% promptcard Input Restriction %}
Restrict input to numeric values, control negative inputs, and limit the number of integer or fractional digits in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Watermark %}
Display and customize watermark or placeholder text in the WinUI NumberBox.
{% endpromptcard %}
{% promptcard Keyboard / Mouse / Up Down  %}
Change values in the WinUI NumberBox using keyboard input, mouse scrolling, and the up/down buttons.
{% endpromptcard %}
{% promptcard Header & Description %}
Add the header and description for the WinUI NumberBox.
{% endpromptcard %}
{% promptcard ValueChanged Event %}
Notify value updates in the WinUI NumberBox.
{% endpromptcard %}
{% endpromptcards %}

## See also

* [Skills](https://help.syncfusion.com/winui/skills)
* [MCP Server](https://help.syncfusion.com/winui/mcp)