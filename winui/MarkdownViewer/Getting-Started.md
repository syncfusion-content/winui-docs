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

This section outlines a step‑by‑step guide for integrating and using the SfMarkdownViewer control in your WinUI applications.

## Assembly deployment

Refer to the Control Dependencies section for a list of required assemblies or NuGet packages that must be added as references to use the control in any application.

Refer to this documentation for detailed guidance on installing NuGet packages in a WinUI application.

## Create a New WinUI Project

1. Create a WinUI 3 desktop app for C# and .NET 6, And then click **Next**.
2. Name the project and choose a location, And then click **Create**.

## Install the Syncfusion<sup>&reg;</sup> WinUI MarkdownViewer NuGet Package

1. In **Solution Explorer,** right-click the project and choose **Manage NuGet Packages.**
2. Search for Syncfusion.MarkdownViewer.WinUI and install the latest version.
3. Ensure the necessary dependencies are installed correctly, and the project is restored.

## Adding WinUI SfMarkdownViewer via XAML

To manually add the SfMarkdownViewer control in XAML, follow these steps:

1. Create a new WinUI project in Visual Studio.

2. Add the following required assembly references to the project:

    * Syncfusion.MarkdownViewer.WinUI
    * Syncfusion.Markdown
    * Syncfusion.Core.WinUI

3. Import the control namespace `Syncfusion.UI.Xaml.Markdown` in XAML, and declare the `SfMarkdownViewer` in XAML page.

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:markdown="using:Syncfusion.UI.Xaml.Markdown">
    <Grid>
        <markdown:SfMarkdownViewer />
    </Grid>
</Window>
 
{% endhighlight %}
{% endtabs %}

## Adding WinUI SfMarkdownViewer via C#

To manually add the SfMarkdownViewer control in C#, follow these steps:

1. Create a new WinUI project in Visual Studio.

2. Add the following required assembly references to the project:

    * Syncfusion.MarkdownViewer.WinUI
    * Syncfusion.Markdown
    * Syncfusion.Core.WinUI

3. Import the control namespace `Syncfusion.UI.Xaml.Markdown` in C#, and add the `SfMarkdownViewer` in C# page.

{% tabs %}
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

## Add Source to the SfMarkdownViewer

The `Source` property is used to supply Markdown content to the control. It supports raw Markdown text, file paths, and HTTP/HTTPS URLs as input.

{% tabs %} 
{% highlight xaml %}

<markdown:SfMarkdownViewer>
    <markdown:SfMarkdownViewer.Source>
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
    </markdown:SfMarkdownViewer.Source>
</markdown:SfMarkdownViewer>

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