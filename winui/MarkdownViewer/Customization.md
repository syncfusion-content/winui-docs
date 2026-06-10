---
layout: post
title: About .NET WinUI Markdown Viewer control | Syncfusion
description: Learn how to customize the appearance and behavior of the Syncfusion® WinUI SfMarkdownViewer control, including styling elements and modifying themes.
platform: WinUI
control: SfMarkdownViewer
documentation: ug
---

# Customize Appearance in WinUI SfMarkdownViewer

The [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) control in WinUI provides a powerful styling system through the [MarkdownStyleSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) class. This allows developers to customize the visual presentation of Markdown content with precision and flexibility.

## Customization with MarkdownStyleSettings

The appearance of headings and body content in [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) can be customized using the [MarkdownStyleSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) class.

* [ParagraphStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for paragraph elements.

* [H1Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), [H2Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), [H3Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), [H4Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), [H5Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), [H6Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for H1 to H6 heading elements respectively.

* [TableStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for table elements, including headers and data rows.

* [ListStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for ordered and unordered list elements.

* [LinkStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for hyperlink elements.

* [InlineQuoteStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for inline quote (blockquote within text) elements.

* [BlockQuoteStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for block quote elements.

* [CodeBlockStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for code block elements.

* [ThematicStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for thematic break (horizontal rule) elements.

* [MermaidStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) – Gets or sets the style for rendering Mermaid diagram content.

## Add MarkdownStyleSettings to the SfMarkdownViewer

{% tabs %} 
{% highlight xaml %}

<Grid>
    <syncfusion:SfMarkdownViewer x:Name="markdownviewer">
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
                        
![Syncfusion WinUI Markdown Viewer](Images/WinUI-markdown-viewer-Customization.WEBP)
                            
                ]]>
            </x:String>
        </syncfusion:SfMarkdownViewer.Source>
        <markdown:SfMarkdownViewer.Settings>
            <markdown:MarkdownStyleSettings>
                <markdown:MarkdownStyleSettings.H1Style>
                    <markdown:HeaderSettings FontStyle="Normal" FontSize="50" Foreground="Blue" />
                </markdown:MarkdownStyleSettings.H1Style>
                <markdown:MarkdownStyleSettings.H2Style>
                    <markdown:HeaderSettings FontStyle="Normal" FontSize="50" Foreground="Blue" />
                </markdown:MarkdownStyleSettings.H2Style>
                <markdown:MarkdownStyleSettings.ParagraphStyle>
                    <markdown:ParagraphSettings FontStyle="Italic" FontSize="15" />
                </markdown:MarkdownStyleSettings.ParagraphStyle>
            </markdown:MarkdownStyleSettings>
        </markdown:SfMarkdownViewer.Settings>
    </syncfusion:SfMarkdownViewer>
</Grid>

{% endhighlight %}

{% highlight C# %}

    public sealed partial class MainWindow : Window
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
                        
![Syncfusion WinUI Markdown Viewer](Images/WinUI-markdown-viewer-Customization.WEBP)
";
            markdownViewer.Settings = new MarkdownStyleSettings
            {
                H1Style = new HeaderSettings
                {
                    FontSize = 50,
                    Foreground = new SolidColorBrush(Microsoft.UI.Colors.Blue),
                    FontStyle = FontStyle.Normal,
                },
                H2Style = new HeaderSettings
                {
                    FontSize = 50,
                    Foreground = new SolidColorBrush(Microsoft.UI.Colors.Blue),
                    FontStyle = FontStyle.Normal,
                },
                ParagraphStyle = new ParagraphSettings
                {
                    FontStyle = FontStyle.Italic,
                    FontSize = 15,
                },
            };
            Content = markdownViewer;
        }
    }

{% endhighlight %}
{% endtabs %}

The following output shows how these style settings enhance the appearance of rendered Markdown content:

![Syncfusion WinUI Markdown Viewer](Images/WinUI-markdown-viewer-Customization.WEBP)
