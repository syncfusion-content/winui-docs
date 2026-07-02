---
layout: post
title: Event in WinUI Markdown Viewer (SfMarkdownViewer) | Syncfusion
description: Learn here all about events support in Syncfusion MarkdownViewer control, its elements and more details.
platform: WinUI
control: SfMarkdownViewer
documentation: ug
---

# Event in WinUI Markdown Viewer (SfMarkdownViewer)

This section describes how to manage hyperlink interactions in the SfMarkdownViewer using the HyperlinkClicked event.
The HyperlinkClicked event is raised when a user clicks a hyperlink within the Markdown content. It provides access to the selected URL and enables you to handle the interaction or override the default navigation behavior if needed.

## HyperlinkClicked Event

The HyperlinkClicked event supplies information about the selected hyperlink through the MarkdownHyperlinkClickedEventArgs class.

This event argument includes the following properties:

- Url  : Retrieves the URL of the clicked hyperlink.
- Cancel  : Gets or sets a value that determines whether the default navigation behavior should be canceled.

## Disable hyperlink navigation

You can prevent hyperlink navigation by setting the Cancel property of the MarkdownHyperlinkClickedEventArgs to true within the HyperlinkClicked event handler.

{% highlight c# %}

// Wires the event handler for `HyperlinkClicked` event.    
markdownViewer.HyperlinkClicked += MarkdownViewer_HyperlinkClicked;

private void MarkdownViewer_HyperlinkClicked(object? sender, MarkdownHyperlinkClickedEventArgs args)
{
    // Gets or sets the value to handle the navigation of hyperlink.
    args.Cancel = true;
}

{% endhighlight %}

## Retrieve the clicked URI

You can obtain the URL of the clicked hyperlink by accessing the Url property from the event arguments.

{% highlight c# %}

// Wires the event handler for `HyperlinkClicked` event.    
markdownViewer.HyperlinkClicked += MarkdownViewer_HyperlinkClicked;

private void MarkdownViewer_HyperlinkClicked(object? sender, MarkdownHyperlinkClickedEventArgs args)
{
    //Returns the URL clicked in the Markdown viewer control.
    string URL = args.Url;
}

{% endhighlight %}
