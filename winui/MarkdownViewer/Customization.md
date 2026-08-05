---
layout: post
title: Customization support in WinUI Markdown Viewer | Syncfusion
description: Learn how to customize the appearance and behavior of the Syncfusion® WinUI SfMarkdownViewer control, including styling elements and modifying themes.
platform: WinUI
control: SfMarkdownViewer
documentation: ug
---

# Customization in WinUI Markdown Viewer

The [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html) control in WinUI provides a flexible styling system through its [Settings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html#Syncfusion_UI_Xaml_Markdown_SfMarkdownViewer_Settings) property. This allows developers to customize the appearance of Markdown elements such as headings, paragraphs, lists, and more to match application themes and branding.

## Style settings for MarkdownViewer

The [MarkdownStyleSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html) class provides style customization for different Markdown elements through the following properties:

- [ParagraphStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_ParagraphStyle) – Defines the style for paragraph text.  
- [H1Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_H1Style) to [H6Style](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_H6Style) – Defines styles for heading levels.  
- [ListStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_ListStyle) – Applies to ordered and unordered lists.  
- [TableStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_TableStyle) – Applies to tables, including headers and rows.  
- [BlockQuoteStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_BlockQuoteStyle) – Used for block-level quotes.  
- [InlineQuoteStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_InlineQuoteStyle) – Used for inline quoted text.  
- [ThematicStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_ThematicStyle) – Used for horizontal rules.  
- [LinkStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_LinkStyle) – Defines hyperlink appearance.  
- [CodeBlockStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_CodeBlockStyle) – Applies to code blocks.  
- [MermaidStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html#Syncfusion_UI_Xaml_Markdown_MarkdownStyleSettings_MermaidStyle) – Applies to Mermaid diagram rendering.  

You can apply these custom styles by assigning a [MarkdownStyleSettings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.MarkdownStyleSettings.html) instance to the [Settings](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html#Syncfusion_UI_Xaml_Markdown_SfMarkdownViewer_Settings) property of [SfMarkdownViewer](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Markdown.SfMarkdownViewer.html), as shown in the following code example.

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
        <syncfusion:SfMarkdownViewer.Settings>
            <syncfusion:MarkdownStyleSettings>
                <syncfusion:MarkdownStyleSettings.H1Style>
                    <syncfusion:HeaderSettings FontStyle="Normal" FontSize="50" Foreground="MediumPurple" />
                </syncfusion:MarkdownStyleSettings.H1Style>
                <syncfusion:MarkdownStyleSettings.H2Style>
                    <syncfusion:HeaderSettings FontStyle="Normal" FontSize="50" Foreground="MediumPurple" />
                </syncfusion:MarkdownStyleSettings.H2Style>
                <syncfusion:MarkdownStyleSettings.ParagraphStyle>
                    <syncfusion:ParagraphSettings FontStyle="Italic" FontSize="15" />
                </syncfusion:MarkdownStyleSettings.ParagraphStyle>
            </syncfusion:MarkdownStyleSettings>
        </syncfusion:SfMarkdownViewer.Settings>
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
                    Foreground = new SolidColorBrush(Microsoft.UI.Colors.MediumPurple),
                    FontStyle = FontStyle.Normal,
                },
                H2Style = new HeaderSettings
                {
                    FontSize = 50,
                    Foreground = new SolidColorBrush(Microsoft.UI.Colors.MediumPurple),
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

The following image shows the rendered output with customized heading and paragraph styles:

![Customized Markdown Rendering](Images/WinUI-markdown-viewer-Customization.WEBP)
