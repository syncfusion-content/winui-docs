---
layout: post
title: Getting started with WinUI Markdown Viewer control | Syncfusion
description: Learn how to get started with Syncfusion® WinUI SfMarkdownViewer control and explore its capabilities for rendering Markdown content.
platform: WinUI
control: SfMarkdownViewer
documentation: ug
keywords: WinUI markdownviewer, syncfusion markdownviewer WinUI, markdown viewer WinUI, WinUI markdown rendering, sfmarkdownviewer WinUI, WinUI markdown control, markdown rendering WinUI, WinUI markdown getting started
---

# Getting Started with WinUI Markdown Viewer (SfMarkdownViewer)

This section outlines a step‑by‑step guide for integrating and using the `SfMarkdownViewer` control in your WinUI applications.

## Creating an application with SfMarkdownViewer (WinUI)

1. Create a WinUI 3 desktop application.

2. Install the following NuGet package in your project:
   - Syncfusion.MarkdownViewer.WinUI

3. Import the following namespace in XAML or C# code:
   - Syncfusion.UI.Xaml.Markdown

4. Initialize an instance of the `SfMarkdownViewer` control.

You can initialize the control in both XAML and C# as shown below:

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Markdown">

    <Grid>
        <syncfusion:SfMarkdownViewer />
    </Grid>
</Window>

{% endhighlight %}

{% highlight C# %}

using Syncfusion.UI.Xaml.Markdown;

namespace MarkdownViewerGettingStarted
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();

            // Creating an instance of the SfMarkdownViewer control
            SfMarkdownViewer markdownViewer = new SfMarkdownViewer();
            this.Content = markdownViewer;
        }
    }
}

{% endhighlight %}
{% endtabs %}

## Populating Source to the SfMarkdownViewer

The `Source` property is used to supply Markdown content to the control. It supports raw Markdown text, file paths, and HTTP/HTTPS URLs.

{% tabs %} 
{% highlight xaml %}

<syncfusion:SfMarkdownViewer>
    <syncfusion:SfMarkdownViewer.Source>
        <x:String xml:space="preserve">
            <![CDATA[

# What is the Markdown Viewer ?
                        
The Markdown Viewer is a UI control in WinUI that allows developers to render Markdown content with full formatting support. It was designed to
work efficiently on both mobile and desktop platforms. The viewer supports headings, bold and italic text, lists, tables, images, code blocks and more.                        
 
# Header 1
                        
Used for the Main title or top-level heading in a Markdown document.
                        
## Header 2
                        
Used to define major sections within your Markdown content. 
                        
![WinUi SfMarkdownViewer](Images/WinUI-markdown-viewer-gettingstarted.WEBP)
            ]]>
        </x:String>
    </syncfusion:SfMarkdownViewer.Source>
</syncfusion:SfMarkdownViewer>

{% endhighlight %}

{% highlight C# %}

public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
        SfMarkdownViewer markdownViewer = new SfMarkdownViewer();
        markdownViewer.Source =
@"
# What is the Markdown Viewer ?
                        
The Markdown Viewer is a UI control in WinUI that allows developers to render Markdown content with full formatting support. It was designed to
work efficiently on both mobile and desktop platforms. The viewer supports headings, bold and italic text, lists, tables, images, code blocks and more.                        
 
# Header 1
                        
Used for the Main title or top-level heading in a Markdown document.
                        
## Header 2
                        
Used to define major sections within your Markdown content. 
                        
![WinUi SfMarkdownViewer](Images/WinUI-markdown-viewer-gettingstarted.WEBP)
";
        this.Content = markdownViewer;
    }
}  

{% endhighlight %}
{% endtabs %}

![WinUI SfMarkdownViewer](Images/WinUI-markdown-viewer-gettingstarted.WEBP)