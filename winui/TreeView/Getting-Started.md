---
layout: post
title: Getting Started with WinUI TreeView | Syncfusion
description: This section describes about how to add the TreeView control into WinUI application and its basic features.
platform: WinUI
control: TreeView
documentation: ug
---

# Getting Started with WinUI TreeView

This section explains the steps required to add the [TreeView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html) control and binding data in Treeview control. This section covers only basic features needed to get started with Syncfusion TreeView control.

## Creating an application with WinUI TreeView

1. Create a simple project using the instructions given in the [Getting Started with your first WinUI app](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp) documentation.
2. Install the [Syncfusion.TreeView.WinUI](https://www.nuget.org/packages/Syncfusion.TreeView.WinUI) NuGet packages.
3. Import the control namespace `Syncfusion.UI.Xaml.TreeView` in XAML or C# code.
4. Initialize the TreeView control.

{% tabs %} 
{% highlight xaml %} 

<Page x:Class="syncfusion.treeviewdemos.winui.GettingStartedPage "
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="using:syncfusion.treeviewdemos.winui"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.TreeView"
      mc:Ignorable="d"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">
      <Grid>
          <syncfusion:SfTreeView x:Name="treeView" />
      </Grid>
</Page>

{% endhighlight %}
{% highlight C# %} 

using Microsoft.UI.Xaml.Controls;
using Syncfusion.UI.Xaml.TreeView;

public sealed partial class GettingStartedPage : Page
{
    /// <summary>
    /// Interaction logic for GettingStartedPage.xaml
    /// </summary>
    public GettingStartedPage()
    {
        this.InitializeComponent();
        SfTreeView treeView = new SfTreeView();
        Root_Grid.Children.Add(treeView);
    }
}

{% endhighlight %}
{% endtabs %} 

## Bind to a hierarchical data source - Bound Mode

You can create a tree view by binding the ItemsSource to a hierarchical data source. To create a tree view using data binding, set a hierarchical collection to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemsSource) property. Then using [ItemTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemTemplate) and [ExpanderTemplate](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ExpanderTemplate), set the child items collection to the `ItemsSource` property.

{% tabs %} 
{% highlight xaml %} 

<Page x:Class="syncfusion.treeviewdemos.winui.NodeWithImagePage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:syncfusion.treeviewdemos.winui"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.TreeView"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      mc:Ignorable="d"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">

    <Page.DataContext>
        <local:NodeWithImageViewModel />
    </Page.DataContext>

    <Grid>
       <syncfusion:SfTreeView x:Name="treeView"
                              ChildPropertyName=”Files”  
                              ItemsSource="{Binding Folders}">
                    <syncfusion:SfTreeView.ItemTemplate>
                        <DataTemplate>
                            <StackPanel Orientation="Horizontal">
                                <ContentPresenter Width="20"
                                                  Height="20"
                                                  HorizontalAlignment="Stretch"
                                                  VerticalAlignment="Center"
                                                  ContentTemplate="{Binding ImageTemplate}" />
                                <TextBlock Margin="5"
                                           VerticalAlignment="Center"
                                           Text="{Binding FileName}" />
                            </StackPanel>
                        </DataTemplate>
                    </syncfusion:SfTreeView.ItemTemplate>
        </syncfusion:SfTreeView>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %} 

public class NodeWithImageViewModel
{
    public ObservableCollection<Folder> Folders { get; internal set; }

    private ResourceDictionary CommonResourceDictionary { get; set; }

    public NodeWithImageViewModel()
    {
        CommonResourceDictionary = new ResourceDictionary() { Source = new Uri("ms-appx:///Icons/PathIcon.xaml", UriKind.RelativeOrAbsolute) };
        this.Folders = GetFiles();
    }

    private ObservableCollection<Folder> GetFiles()
    {
        var nodeImageInfo = new ObservableCollection<Folder>();

        var doc = new Folder() { FileName = "Documents", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var download = new Folder() { FileName = "Downloads", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var mp3 = new Folder() { FileName = "Music", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var pictures = new Folder() { FileName = "Pictures", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var video = new Folder() { FileName = "Videos", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };

        var pollution = new Folder() { FileName = "Environmental Pollution.docx", ImageTemplate = CommonResourceDictionary["Word"] as DataTemplate };
        var globalWarming = new Folder() { FileName = "Global Warming.ppt", ImageTemplate = CommonResourceDictionary["PowerPoint"] as DataTemplate };
        var sanitation = new Folder() { FileName = "Sanitation.docx", ImageTemplate = CommonResourceDictionary["Word"] as DataTemplate };
        var socialNetwork = new Folder() { FileName = "Social Network.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate };
        var youthEmpower = new Folder() { FileName = "Youth Empowerment.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate };

        var games = new Folder() { FileName = "Game.exe", ImageTemplate = CommonResourceDictionary["EXE"] as DataTemplate };
        var tutorials = new Folder()  { FileName = "Tutorials.zip", ImageTemplate = CommonResourceDictionary["Zip"] as DataTemplate };
        var typeScript = new Folder() { FileName = "TypeScript.7z", ImageTemplate = CommonResourceDictionary["Zip"] as DataTemplate };
        var uiGuide = new Folder() { FileName = "UI-Guide.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate };

        var song = new Folder() { FileName = "Gouttes", ImageTemplate = CommonResourceDictionary["Audio"] as DataTemplate };

        var camera = new Folder() { FileName = "Camera Roll", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var stone = new Folder() { FileName = "Stone.jpg", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };
        var wind = new Folder() { FileName = "Wind.jpg", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };

        var img0 = new Folder() { FileName = "WIN_20160726_094117.JPG", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };
        var img1 = new Folder() { FileName = "WIN_20160726_094118.JPG", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };

        var video1 = new Folder() { FileName = "Natural World.mp4", ImageTemplate = CommonResourceDictionary["Video"] as DataTemplate };
        var video2 = new Folder() { FileName = "Wildlife.mpeg", ImageTemplate = CommonResourceDictionary["Video"] as DataTemplate };

        doc.Files = new ObservableCollection<Folder>
        {
            pollution,
            globalWarming,
            sanitation,
            socialNetwork,
            youthEmpower
        };

        download.Files = new ObservableCollection<Folder>
        {
            games,
            tutorials,
            typeScript,
            uiGuide
        };

        mp3.Files = new ObservableCollection<Folder>
        {
            song
        };

        pictures.Files = new ObservableCollection<Folder>
        {
            camera,
            stone,
            wind
        };

        camera.Files = new ObservableCollection<Folder>
        {
            img0,
             img1
        };

        video.Files = new ObservableCollection<Folder>
        {
            video1,
            video2
        };

        nodeImageInfo.Add(doc);
        nodeImageInfo.Add(download);
        nodeImageInfo.Add(mp3);
        nodeImageInfo.Add(pictures);
        nodeImageInfo.Add(video);

        return nodeImageInfo;
    }
}

public class Folder : NotificationObject
{ 
        
    private string fileName;

    private DataTemplate imageTemplate;
             
    private ObservableCollection<Folder> files;

    public Folder()
    {

    }

    public ObservableCollection< Folder> Files
    {
        get { return files; }
        internal set
        {
            files = value;
            RaisePropertyChanged(nameof(Files));
        }
    }

    public string FileName
    {
        get { return fileName; }
        set
        {
            fileName = value;
            RaisePropertyChanged(nameof(FileName));
        }
    }

    public DataTemplate ImageTemplate
    {
        get { return imageTemplate; }
        set { imageTemplate = value; }
    }
}

{% endhighlight %}
{% endtabs %} 

![Populating Nodes by data binding](DataPopulation_images/Bound_mode.jpg)

N> [View sample in GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-treeview-examples/tree/main/Samples/Populating-Nodes-with-Bound-mode)

## Bind to a Hierarchy Property Descriptors data source - Bound Mode

You can create a tree view by binding the `ItemsSource` to a hierarchy property descriptors data source. To create a tree view using hierarchical data binding, set a hierarchical collection to the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ItemsSource) property, and then set the TargetType and [ChildPropertyName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_ChildPropertyName) property values in [HierarchyPropertyDescriptors](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_HierarchyPropertyDescriptors).

{% tabs %} 
{% highlight xaml %} 

<Page x:Class="syncfusion.treeviewdemos.winui.NodeWithImagePage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:local="using:syncfusion.treeviewdemos.winui"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.TreeView"
      xmlns:treeviewengine="using:Syncfusion.UI.Xaml.TreeView.Engine"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      mc:Ignorable="d"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">

    <Page.DataContext>
        <local:NodeWithImageViewModel />
    </Page.DataContext>

    <Grid>
        <syncfusion:SfTreeView x:Name="treeView"
                               ItemsSource="{Binding Folders}">
                    <syncfusion:SfTreeView.HierarchyPropertyDescriptors>
                        <treeviewengine:HierarchyPropertyDescriptor ChildPropertyName="Files"
                                                                    TargetType="local:Folder" />
                        <treeviewengine:HierarchyPropertyDescriptor ChildPropertyName="SubFiles"
                                                                    TargetType="local:File" />
                    </syncfusion:SfTreeView.HierarchyPropertyDescriptors>
                    <syncfusion:SfTreeView.ItemTemplate>
                        <DataTemplate>
                            <StackPanel Orientation="Horizontal">
                                <ContentPresenter Width="20"
                                                  Height="20"
                                                  HorizontalAlignment="Stretch"
                                                  VerticalAlignment="Center"
                                                  ContentTemplate="{Binding ImageTemplate}" />
                                <TextBlock Margin="5"
                                           VerticalAlignment="Center"
                                           Text="{Binding FileName}" />
                            </StackPanel>
                        </DataTemplate>
                    </syncfusion:SfTreeView.ItemTemplate>
        </syncfusion:SfTreeView>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %} 

public class NodeWithImageViewModel
{
    public NodeWithImageViewModel()
    {
        CommonResourceDictionary = new ResourceDictionary() { Source = new Uri("ms-appx:///Icons/PathIcon.xaml", UriKind.RelativeOrAbsolute) };
        this.Folders = GetFiles();
    }

    public ObservableCollection<Folder> Folders { get; internal set; }

    public ObservableCollection<File> Files { get; internal set; }

    public ObservableCollection<SubFile> SubFiles { get; internal set; }

    private ResourceDictionary CommonResourceDictionary { get; set; }
        
    private ObservableCollection<Folder> GetFiles()
    {
        var nodeImageInfo = new ObservableCollection<Folder>();

        var doc = new Folder() { FileName = "Documents", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var download = new Folder() { FileName = "Downloads", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var mp3 = new Folder() { FileName = "Music", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var pictures = new Folder() { FileName = "Pictures", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var video = new Folder() { FileName = "Videos", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };

        var pollution = new File() { FileName = "Environmental Pollution.docx", ImageTemplate = CommonResourceDictionary["Word"] as DataTemplate };
        var globalWarming = new File() { FileName = "Global Warming.ppt", ImageTemplate = CommonResourceDictionary["PowerPoint"] as DataTemplate };
        var sanitation = new File() { FileName = "Sanitation.docx", ImageTemplate = CommonResourceDictionary["Word"] as DataTemplate };
        var socialNetwork = new File() { FileName = "Social Network.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate };
        var youthEmpower = new File() { FileName = "Youth Empowerment.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate};

        var games = new File() { FileName = "Game.exe", ImageTemplate = CommonResourceDictionary["EXE"] as DataTemplate };
        var tutorials = new File() { FileName = "Tutorials.zip", ImageTemplate = CommonResourceDictionary["Zip"] as DataTemplate };
        var typeScript = new File() { FileName = "TypeScript.7z", ImageTemplate = CommonResourceDictionary["Zip"] as DataTemplate };
        var uiGuide = new File() { FileName = "UI-Guide.pdf", ImageTemplate = CommonResourceDictionary["Pdf"] as DataTemplate };

        var song = new File() { FileName = "Gouttes", ImageTemplate = CommonResourceDictionary["Audio"] as DataTemplate };

        var camera = new File() { FileName = "Camera Roll", ImageTemplate = CommonResourceDictionary["Folder"] as DataTemplate };
        var stone = new File() { FileName = "Stone.jpg", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };
        var wind = new File() { FileName = "Wind.jpg", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };

        var img0 = new SubFile() { FileName = "WIN_20160726_094117.JPG", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };
        var img1 = new SubFile() { FileName = "WIN_20160726_094118.JPG", ImageTemplate = CommonResourceDictionary["Png"] as DataTemplate };

        var video1 = new File() { FileName = "Natural World.mp4", ImageTemplate = CommonResourceDictionary["Video"] as DataTemplate };
        var video2 = new File() { FileName = "Wildlife.mpeg", ImageTemplate = CommonResourceDictionary["Video"] as DataTemplate };

        doc.Files = new ObservableCollection<File>
        {
            pollution,
            globalWarming,
            sanitation,
            socialNetwork,
            youthEmpower
        };

        download.Files = new ObservableCollection<File>
        {
            games,
            tutorials,
            typeScript,
            uiGuide
        };

        mp3.Files = new ObservableCollection<File>
        {
            song
        };

        pictures.Files = new ObservableCollection<File>
        {
            camera,
            stone,
            wind
        };

        camera.SubFiles = new ObservableCollection<SubFile>
        {
            img0,
            img1
        };

        video.Files = new ObservableCollection<File>
        {
            video1,
            video2
        };

        nodeImageInfo.Add(doc);
        nodeImageInfo.Add(download);
        nodeImageInfo.Add(mp3);
        nodeImageInfo.Add(pictures);
        nodeImageInfo.Add(video);

        return nodeImageInfo;
    }
}

public class Folder : NotificationObject
{
    private string fileName;

    private DataTemplate imageTemplate;
        
    private ObservableCollection<File> files;
        
    public Folder()
    {

    }

    public ObservableCollection<File> Files
    {
        get { return files; }
        internal set
        {
            files = value;
            RaisePropertyChanged(nameof(Files));
        }
    }

    public string FileName
    {
        get { return fileName; }
        set
        {
            fileName = value;
            RaisePropertyChanged(nameof(FileName));
        }
    }

    public DataTemplate ImageTemplate
    {
        get { return imageTemplate; }
        set { imageTemplate = value; }
    }
}

public class File : NotificationObject
{
    private string fileName;

    private DataTemplate imageTemplate;

    private ObservableCollection<SubFile> subFiles;

    public File()
    {

    }

    public ObservableCollection<SubFile> SubFiles
    {
        get { return subFiles; }
        internal set
        {
            subFiles = value;
            RaisePropertyChanged(nameof(SubFiles));
        }
    }

    public string FileName
    {
        get { return fileName; }
        set
        {
            fileName = value;
            RaisePropertyChanged(nameof(FileName));
        }
    }

    public DataTemplate ImageTemplate
    {
        get { return imageTemplate; }
        set { imageTemplate = value; }
    }
}

public class SubFile : NotificationObject
{      
    private string fileName;

    private DataTemplate imageTemplate;  
      
    public SubFile()
    {

    }
        
    public string FileName
    {
        get { return fileName; }
        set
        {
            fileName = value;
            RaisePropertyChanged(nameof(FileName));
        }
    }

    public DataTemplate ImageTemplate
    {
        get { return imageTemplate; }
        set { imageTemplate = value; }
    }
}

{% endhighlight %}
{% endtabs %} 

## Populating Nodes without data source - Unbound Mode

You can create and manage the [TreeViewNode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.Engine.TreeViewNode.html) objects by yourself to display the data in a hierarchical view. To create a tree view, you can use a `TreeView` control and a hierarchy of `TreeViewNode` objects. You can create the node hierarchy by adding one or more root nodes to the [TreeView.Nodes](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeView.SfTreeView.html#Syncfusion_UI_Xaml_TreeView_SfTreeView_Nodes) collection. Each `TreeViewNode` can have more nodes added to its Children collection which helps in populating multiple level of tree view nodes based on needs.

{% tabs %} 
{% highlight xaml %} 

<Page x:Class="syncfusion.treeviewdemos.winui.GettingStartedPage"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="using:syncfusion.treeviewdemos.winui"
      xmlns:syncfusion="using:Syncfusion.UI.Xaml.TreeView"
      xmlns:node="using:Syncfusion.UI.Xaml.TreeView.Engine"
      mc:Ignorable="d"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"
      NavigationCacheMode="Disabled">
    <Grid> 
        <syncfusion:SfTreeView x:Name="unboundTreeView" Width="400" Height="500">
            <syncfusion:SfTreeView.Nodes>
                <node:TreeViewNode Content="Chairman and CEO"
                                   IsExpanded="True">
                    <node:TreeViewNode.ChildNodes>
                        <node:TreeViewNode Content="COO and Director">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Human Resources" />
                                <node:TreeViewNode Content="Platform, EMEA" />
                                <node:TreeViewNode Content="Mobile" />
                                <node:TreeViewNode Content="Mid-Market Sales EMED" />
                                <node:TreeViewNode Content="EMEA Regional Director" />
                                <node:TreeViewNode Content="Advertising and Global Operations" />
                                <node:TreeViewNode Content="Growth, Engagement, and Moblie" />
                                <node:TreeViewNode Content="Global Marketing and Solutions" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="CIO" />
                        <node:TreeViewNode Content="Security">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Security Services" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="Corporate Development" />
                        <node:TreeViewNode Content="Product"
                                           IsExpanded="True">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Product Advertising" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="Communication and Marketing"
                                           IsExpanded="True">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Consumer Marketing" />
                                <node:TreeViewNode Content="Platforms, Partners, and PR" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="Legal"
                                           IsExpanded="True">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Public Policy" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="Patnership and Marketing" />
                        <node:TreeViewNode Content="Engineering"
                                           IsExpanded="True">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Engineering" />
                                <node:TreeViewNode Content="Software Development" />
                                <node:TreeViewNode Content="Engineering and Products" />
                                <node:TreeViewNode Content="Infrastructure Engineering" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="CFO"
                                                       IsExpanded="True">
                            <node:TreeViewNode.ChildNodes>
                                <node:TreeViewNode Content="Treasurer" />
                            </node:TreeViewNode.ChildNodes>
                        </node:TreeViewNode>
                        <node:TreeViewNode Content="Brand Design" />
                    </node:TreeViewNode.ChildNodes>
                </node:TreeViewNode>
            </syncfusion:SfTreeView.Nodes>
        </syncfusion:SfTreeView>    
    </Grid>
</Page>

{% endhighlight %}
{% endtabs %} 

![Populating nodes without data source in TreeView ](GettingStarted_images/Unbound_Modes.jpg)

N> [View Getting started sample in GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-treeview-examples/tree/main/Samples/Getting-Started)
