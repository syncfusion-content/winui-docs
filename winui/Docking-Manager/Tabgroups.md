---
layout: post
title: Tab Groups and Documents in WinUI DockingManager Control | Syncfusion®
description: Learn how to organize documents and tool windows using tab groups in the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Tab Groups and Documents

The DockingManager control allows multiple tool windows and documents to be organized into tab groups. This helps reduce workspace clutter and provides an efficient way to navigate between related content.

## Create Document Tabs

Document windows are automatically displayed as tabs when multiple panes are configured with the `Document` state.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="App.xaml"
                          DockState="Document">
            <TextBox Text="Application resources..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane documentPane1 = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane documentPane2 = new DockPane()
{
    Header = "App.xaml",
    DockState = DockState.Document
};

dockingManager.Panes.Add(documentPane1);
dockingManager.Panes.Add(documentPane2);

{% endhighlight %}
{% endtabs %}

## Create Tab Groups

Tool windows can be grouped into the same docking region and displayed as tabs. This allows users to switch between related windows without occupying additional layout space.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane x:Name="OutputPane"
                          Header="Output"
                          DockDirection="Bottom"
                          DockState="Docked">
            <TextBlock Text="Build Output Window"/>
        </docking:DockPane>

        <docking:DockPane Header="Error List"
                          DockDirection="Bottom"
                          DockState="Tabbed"
                          TargetNameInTabbedState="OutputPane">
            <TextBlock Text="Error List Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane outputPane = new DockPane()
{
    Header = "Output",
    DockDirection = DockDirection.Bottom,
    DockState = DockState.Docked
};

DockPane errorListPane = new DockPane()
{
    Header = "Error List",
    DockDirection = DockDirection.Bottom,
    DockState = DockState.Tabbed,
    TargetNameInTabbedState = "OutputPane"
};

dockingManager.Panes.Add(outputPane);
dockingManager.Panes.Add(errorListPane);

{% endhighlight %}
{% endtabs %}

## TargetNameInTabbedState

The `TargetNameInTabbedState` property specifies the target pane with which the current pane should be grouped as a tab.

The following example tabs the **Error List** pane with the **Output** pane.

{% tabs %}
{% highlight xaml %}

<docking:DockPane x:Name="OutputPane"
                  Header="Output"
                  DockDirection="Bottom"
                  DockState="Docked">
    <TextBlock Text="Build Output Window"/>
</docking:DockPane>

<docking:DockPane Header="Error List"
                  DockDirection="Bottom"
                  DockState="Tabbed"
                  TargetNameInTabbedState="OutputPane">
    <TextBlock Text="Error List Content"/>
</docking:DockPane>

{% endhighlight %}

{% highlight c# %}

DockPane outputPane = new DockPane()
{
    Header = "Output",
    DockDirection = DockDirection.Bottom,
    DockState = DockState.Docked
};

DockPane errorListPane = new DockPane()
{
    Header = "Error List",
    DockDirection = DockDirection.Bottom,
    DockState = DockState.Tabbed,
    TargetNameInTabbedState = "OutputPane"
};

dockingManager.Panes.Add(outputPane);
dockingManager.Panes.Add(errorListPane);

{% endhighlight %}
{% endtabs %}