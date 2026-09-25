---
layout: post
title: Window States in WinUI DockingManager Control | Syncfusion®
description: Learn about the different window states supported in the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Window States

The DockingManager control supports multiple window states that help organize application content into flexible and customizable layouts. Each state determines how a pane is displayed and interacts with other panes within the docking layout.

The following window states are supported:

* Docked
* Document
* Floating
* AutoHidden
* Tabbed

## Docked Window

A docked window is attached to one of the docking regions such as the left, right, top, or bottom side of the layout. Docked windows are commonly used for tool windows and navigation panels.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="Docked">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane toolboxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.Docked,
    Content = new TextBlock()
    {
        Text = "Toolbox Content"
    }
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

dockingManager.Panes.Add(toolboxPane);
dockingManager.Panes.Add(documentPane);

{% endhighlight %}
{% endtabs %}

## Document Window

A document window is displayed in the central document area and is commonly used to host editable content such as source files, documents, and design surfaces.

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

## Floating Window

A floating window is displayed outside the docking layout and can be moved independently across the desktop.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane floatingPane = new DockPane()
{
    Header = "Solution Explorer",
    DockState = DockState.Floating,
    Content = new TextBlock()
    {
        Text = "Solution Explorer Content"
    }
};

dockingManager.Panes.Add(documentPane);
dockingManager.Panes.Add(floatingPane);

{% endhighlight %}
{% endtabs %}

## Auto-Hidden Window

An auto-hidden window remains collapsed along the edge of the layout and expands temporarily when selected.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="AutoHidden">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane autoHiddenPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.AutoHidden,
    Content = new TextBlock()
    {
        Text = "Toolbox Content"
    }
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

dockingManager.Panes.Add(autoHiddenPane);
dockingManager.Panes.Add(documentPane);

{% endhighlight %}
{% endtabs %}

## Tabbed Window

A tabbed window groups multiple panes within the same docking region and displays them as tabs.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane x:Name="OutputPane"
                          Header="Output"
                          DockDirection="Bottom"
                          DockState="Docked">
            <TextBlock Text="Output Content"/>
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