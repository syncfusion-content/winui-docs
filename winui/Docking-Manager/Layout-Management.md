---
layout: post
title: Layout Management in WinUI DockingManager Control | Syncfusion®
description: Learn how to manage pane placement, docking operations, dock indicators, and layout resizing in the Syncfusion® WinUI DockingManager control.
platform: winui
control: DockingManager
documentation: ug
---

# Layout Management

The DockingManager control provides several layout management features that help organize application content efficiently. Panes can be positioned declaratively in XAML, arranged programmatically, moved through drag-and-drop interactions, and resized to suit different workflows.

## Place Panes Using XAML

You can define the initial position and state of panes directly in XAML by setting the `DockDirection` and `DockState` properties.

{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="Docked">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockDirection="Right"
                          DockState="Docked">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

## Place Panes Programmatically

You can create and arrange panes dynamically at runtime using the DockingManager APIs.

{% highlight c# %}

DockPane toolboxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.Docked
};

DockPane solutionExplorerPane = new DockPane()
{
    Header = "Solution Explorer",
    DockDirection = DockDirection.Right,
    DockState = DockState.Docked
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

dockingManager.Panes.Add(toolboxPane);
dockingManager.Panes.Add(solutionExplorerPane);
dockingManager.Panes.Add(documentPane);

{% endhighlight %}

## Drag-and-Drop Docking

Users can rearrange panes at runtime through drag-and-drop interactions. Panes can be moved between docking regions, converted into floating windows, or grouped as tabs.

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

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane solutionExplorerPane = new DockPane()
{
    Header = "Solution Explorer",
    DockState = DockState.Floating
};

dockingManager.Panes.Add(solutionExplorerPane);

{% endhighlight %}
{% endtabs %}

## Dock Indicators

Dock indicators provide visual feedback while dragging panes. These indicators display valid docking targets and help users place panes in the desired region.

When a pane is dragged, docking targets appear around the layout and document area. Dropping the pane onto one of these targets docks the pane in the corresponding position.

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

        <docking:DockPane Header="Solution Explorer"
                          DockState="Floating">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane toolboxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.Docked
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane floatingPane = new DockPane()
{
    Header = "Solution Explorer",
    DockState = DockState.Floating
};

dockingManager.Panes.Add(toolboxPane);
dockingManager.Panes.Add(documentPane);
dockingManager.Panes.Add(floatingPane);

{% endhighlight %}
{% endtabs %}

## Layout Resizing

The DockingManager control allows users to resize docked regions interactively at runtime. Splitters are automatically displayed between adjacent docked panes, enabling users to allocate more space to frequently used windows while maintaining access to other panes.

The following example creates multiple docked panes and a document window. Users can resize the docking regions by dragging the splitters between adjacent panes.

{% tabs %}
{% highlight xaml %}

<Grid>
    <docking:SfDockingManager>

        <docking:DockPane Header="Toolbox"
                          DockDirection="Left"
                          DockState="Docked">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane Header="Solution Explorer"
                          DockDirection="Right"
                          DockState="Docked">
            <TextBlock Text="Solution Explorer Content"/>
        </docking:DockPane>

        <docking:DockPane Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

        <docking:DockPane Header="Output"
                          DockDirection="Bottom"
                          DockState="Docked">
            <TextBlock Text="Build Output Window"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

DockPane toolboxPane = new DockPane()
{
    Header = "Toolbox",
    DockDirection = DockDirection.Left,
    DockState = DockState.Docked
};

DockPane solutionExplorerPane = new DockPane()
{
    Header = "Solution Explorer",
    DockDirection = DockDirection.Right,
    DockState = DockState.Docked
};

DockPane documentPane = new DockPane()
{
    Header = "MainWindow.xaml",
    DockState = DockState.Document
};

DockPane outputPane = new DockPane()
{
    Header = "Output",
    DockDirection = DockDirection.Bottom,
    DockState = DockState.Docked
};

dockingManager.Panes.Add(toolboxPane);
dockingManager.Panes.Add(solutionExplorerPane);
dockingManager.Panes.Add(documentPane);
dockingManager.Panes.Add(outputPane);

{% endhighlight %}
{% endtabs %}