---
layout: post
title: Load Markdown Content in WinUI Markdown Viewer | Syncfusion
description: Learn how to load Markdown content from various sources (strings, local files, URLs) in the Syncfusion WinUI SfMarkdownViewer control.
platform: WinUI
control: SfMarkdownViewer
documentation: ug
---

# Loading Markdown Content in WinUI Markdown Viewer

The [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) control offers versatile options for loading Markdown content from various sources. Its [Source](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html#Syncfusion_UI_Xaml_Markdown_SfMarkdownViewer_Source) property automatically identifies the input type and manages content loading seamlessly, supporting raw Markdown text, local file paths, as well as HTTP/HTTPS URLs.

## Loading from Raw Markdown String

Assign a Markdown-formatted string to the Source property of the [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) control to display Markdown content directly within your application.

{% tabs %} 
{% highlight xaml %}

<Grid>
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
                        
![WinUI SfMarkdownViewer](Images/WinUI-markdown-viewer-gettingstarted.WEBP)
                ]]>
            </x:String>
        </syncfusion:SfMarkdownViewer.Source>
    </syncfusion:SfMarkdownViewer>
</Grid>

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
                        
![WinUI SfMarkdownViewer](Images/WinUI-markdown-viewer-gettingstarted.WEBP)
";
            this.Content = markdownViewer;
        }
    }   
}

{% endhighlight %}
{% endtabs %}

## Loading from Local File

To load Markdown content from a local file, simply set the file path as the value of the [Source](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html#Syncfusion_UI_Xaml_Markdown_SfMarkdownViewer_Source) property. The control automatically recognizes valid file paths and reads the file content accordingly.

**C#**

{% highlight C# %}

public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
        SfMarkdownViewer markdownViewer = new SfMarkdownViewer();
        string filePath = @"D:\WinUI\MarkdownViewer\Files\MarkdownContent.md";
        string markdownContent = File.ReadAllText(filePath);
        markdownViewer.Source = markdownContent;
        this.Content = markdownViewer;  
    }
}

{% endhighlight %}

## Loading from URL

The [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) control is capable of loading Markdown content directly from publicly accessible URLs. This feature is especially useful for presenting remote documentation, release notes, or any Markdown content hosted online.

{% tabs %}
{% highlight xaml %}

<Window>
    <syncfusion:SfMarkdownViewer Source="https://raw.githubusercontent.com/SyncfusionExamples/WinUI-tabsplitter-example/refs/heads/master/README.md">
    </syncfusion:SfMarkdownViewer>
</Window>

{% endhighlight %}

{% highlight C# %}

public partial class MainWindow : Window
{ 
    public MainWindow()
    {
        InitializeComponent();  
        SfMarkdownViewer markdownViewer = new SfMarkdownViewer();
        markdownViewer.Source = "https://raw.githubusercontent.com/SyncfusionExamples/WinUI-tabsplitter-example/refs/heads/master/README.md";
        this.Content = markdownViewer;       
    }
} 

{% endhighlight %}
{% endtabs %}
