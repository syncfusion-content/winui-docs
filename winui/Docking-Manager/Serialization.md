---
layout: post
title: Layout Serialization in WinUI DockingManager Control | Syncfusion®
description: Learn how to save and restore the pane layout of the Syncfusion® WinUI DockingManager control using SaveLayout and LoadLayout.
platform: winui
control: DockingManager
documentation: ug
---

# Layout Serialization in WinUI DockingManager

The DockingManager control can save the current arrangement of its panes to a stream and restore it later. This allows an application to preserve the user's workspace between sessions.

The layout is written as an XML document. The application owns the storage, so the stream can be a file, isolated storage, or any other writable stream.

| Method | Description |
|--------|-------------|
| `SaveLayout(Stream)` | Writes the current layout as XML to the specified stream. |
| `LoadLayout(Stream)` | Reads a layout produced by `SaveLayout` and applies it to the panes. |

## What is saved

For each pane, the layout stores:

* The pane `Name`.
* The dock state (`Docked`, `Document`, `Floating`, `AutoHidden`, `Hidden`, or `Tabbed`).
* The dock side (`DockDirection`).
* The tab group the pane belongs to.
* The auto-hide edge, for auto-hidden panes.
* The floating window the pane belongs to.
* The docked size, stored as a ratio of the available size.

The position and size of floating windows are saved as well. Pane content is never saved; the application provides the content when it creates the panes.

## Save and load a layout

The following example saves the layout to a file when a button is clicked and restores it from the same file.

{% tabs %}
{% highlight xaml %}

<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition/>
    </Grid.RowDefinitions>

    <StackPanel Orientation="Horizontal" Spacing="8">
        <Button Content="Save Layout" Click="OnSaveLayout"/>
        <Button Content="Load Layout" Click="OnLoadLayout"/>
    </StackPanel>

    <docking:SfDockingManager x:Name="dockingManager" Grid.Row="1">

        <docking:DockPane x:Name="ToolboxPane"
                          Header="Toolbox"
                          DockDirection="Left"
                          DockState="Docked">
            <TextBlock Text="Toolbox Content"/>
        </docking:DockPane>

        <docking:DockPane x:Name="OutputPane"
                          Header="Output"
                          DockDirection="Bottom"
                          DockState="Docked">
            <TextBlock Text="Build Output Window"/>
        </docking:DockPane>

        <docking:DockPane x:Name="MainDocument"
                          Header="MainWindow.xaml"
                          DockState="Document">
            <TextBox Text="Main document editor..."
                     AcceptsReturn="True"/>
        </docking:DockPane>

    </docking:SfDockingManager>
</Grid>

{% endhighlight %}

{% highlight c# %}

using System.IO;
using Windows.Storage;

private readonly string layoutPath =
    Path.Combine(ApplicationData.Current.LocalFolder.Path, "DockLayout.xml");

private void OnSaveLayout(object sender, RoutedEventArgs e)
{
    using (FileStream stream = File.Create(layoutPath))
    {
        dockingManager.SaveLayout(stream);
    }
}

private void OnLoadLayout(object sender, RoutedEventArgs e)
{
    if (!File.Exists(layoutPath))
    {
        return;
    }

    using (FileStream stream = File.OpenRead(layoutPath))
    {
        dockingManager.LoadLayout(stream);
    }
}

{% endhighlight %}
{% endtabs %}

## Restore the layout when the application starts

Create all panes first, and call `LoadLayout` after the control has loaded.

{% highlight c# %}

dockingManager.Loaded += (s, e) =>
{
    if (File.Exists(layoutPath))
    {
        using (FileStream stream = File.OpenRead(layoutPath))
        {
            dockingManager.LoadLayout(stream);
        }
    }
};

{% endhighlight %}

## Handle invalid layout files

`LoadLayout` throws an `XmlException` when the document is not well-formed XML. Catch the exception to fall back to the default layout.

{% highlight c# %}

try
{
    using (FileStream stream = File.OpenRead(layoutPath))
    {
        dockingManager.LoadLayout(stream);
    }
}
catch (System.Xml.XmlException)
{
    // The layout file is corrupt. Keep the default layout.
}

{% endhighlight %}

## Guidelines

* Set a unique `Name` (or `x:Name` in XAML) on every pane. Panes are matched to the saved layout by name.
* Entries in the saved layout that do not match an existing pane are skipped.
* Panes that are not in the saved layout keep their current state.
* The `AllowFloat` and `AllowAutoHide` settings still apply while loading. A saved `Floating` or `AutoHidden` state is not applied to a pane that does not allow it.

N> Panes are not created from the saved layout. Create the panes before calling `LoadLayout`.
