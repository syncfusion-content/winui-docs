---
layout: post
title: Getting Started with WinUI AIAssistView | Syncfusion®
description: Learn how to get started with the Syncfusion® WinUI AIAssistView control. Explore setup, features, examples, and customization options.
platform: WinUI
control: SfAIAssistView
documentation: ug
---

# Getting Started with WinUI AIAssistView

This section explains how to add the WinUI [AI AssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) control to an application and bind it to a simple chat data source.

## Creating an application with the WinUI AIAssistView

1. Create a [WinUI 3 desktop application in C#](https://learn.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop).
2. Install the [Syncfusion.Chat.WinUI](https://www.nuget.org/packages/Syncfusion.Chat.WinUI) NuGet package.
3. Import the **Syncfusion.UI.Xaml.Chat** namespace in XAML or C#.
4. Add and initialize the [AI AssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) control.

## Initialize the AI AssistView

{% tabs %}
{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Chat"
    mc:Ignorable="d">
    <Grid>
      <syncfusion:SfAIAssistView />
    </Grid>
</Window>

{% endhighlight %}

{% highlight c# %}

using Microsoft.UI.Xaml;
using Microsoft.UI.Xaml.Controls;
using Syncfusion.UI.Xaml.Chat;

namespace GettingStarted;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        // Create an instance of the SfAIAssistView control.
        SfAIAssistView aiAssistView = new SfAIAssistView();

        // Host the control inside a Grid and assign it as the window's content.
        Grid grid = new Grid();
        grid.Children.Add(aiAssistView);
        this.Content = grid;
    }
}

{% endhighlight %}
{% endtabs %}

## Creating a view model for the AI AssistView

To bind data to the [AI AssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) control, update the XAML, set the window's DataContext in the code-behind, and add a _ViewModel.cs_ file to the project, as shown in the following example.

{% tabs %}

{% highlight xaml %}

<Window
    x:Class="GettingStarted.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:syncfusion="using:Syncfusion.UI.Xaml.Chat"
    mc:Ignorable="d">
    <Grid x:Name="grid">
      <syncfusion:SfAIAssistView CurrentUser="{Binding CurrentUser}"
                                 Messages="{Binding Chats}"/>
    </Grid>
</Window>

{% endhighlight %}

{% highlight c# %}

// MainWindow class
using Microsoft.UI.Xaml;

namespace GettingStarted;

public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        grid.DataContext = new ViewModel();
    }
}

// ViewModel class
using System.Collections.ObjectModel;
using System.ComponentModel;
using System.Threading.Tasks;
using Syncfusion.UI.Xaml.Chat;

namespace GettingStarted;

public class ViewModel : INotifyPropertyChanged
{
    private ObservableCollection<object> chats;
    private Author currentUser;

    public ViewModel()
    {
        this.Chats = new ObservableCollection<object>();
        this.CurrentUser = new Author { Name = "John" };
        this.GenerateMessages();
    }

    private async void GenerateMessages()
    {
        this.Chats.Add(new TextMessage { Author = this.CurrentUser, Text = "What is WinUI?" });
        await Task.Delay(1000);
        this.Chats.Add(new TextMessage { Author = new Author { Name = "Bot" }, Text = "WinUI is a user interface layer that contains modern controls and styles for building Windows apps." });
    }

    public ObservableCollection<object> Chats
    {
        get { return this.chats; }
        set
        {
            this.chats = value;
            this.RaisePropertyChanged(nameof(this.Chats));
        }
    }

    public Author CurrentUser
    {
        get { return this.currentUser; }
        set
        {
            this.currentUser = value;
            this.RaisePropertyChanged(nameof(this.CurrentUser));
        }
    }

    protected void RaisePropertyChanged(string propertyName)
    {
        this.PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }

    public event PropertyChangedEventHandler PropertyChanged;
}

{% endhighlight %}
{% endtabs %}

![WinUI AI AssistView control](aiassistview_images/winui_aiassistview_gettingstarted.png)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/Syncfusion-winui-ai-assistView-examples/tree/master/Samples/Getting-Started)
