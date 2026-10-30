---
layout: post
title: Create WinUI 3 Projects using Syncfusion .NET CLI | Syncfusion®
description: Learn here about how to create a Syncfusion® WinUI 3 project using the Syncfusion® .NET CLI (sfdotnet) through the interactive wizard or direct commands.
platform: winui
control: Syncfusion<sup>®</sup> .NET CLI
documentation: ug
---

# Create a WinUI 3 project

You can create a WinUI 3 project through the interactive wizard or a direct command. WinUI projects are created with C#, and the theme is the native WinUI theme. For CLI installation and the main menu, refer to the [overview](/winui/dotnet-cli/overview).

## Create a project using the interactive wizard

Run `sfdotnet new`, or select **Create a new project** from the main menu. The WinUI creation flow is:

1. **Platform:** Select **WinUI**.

    ![Framework selection in the Syncfusion .NET CLI](images/cli-create-new-project.png)

2. **Framework:** Select the .NET version: .NET 10 (`net10.0`), the default, or .NET 9 (`net9.0`).

3. **Location and name:** Enter the parent directory and the project name. The suggested location is `%USERPROFILE%\source\repos`, and the suggested name is `SyncfusionWinUIApp`. The first available numeric suffix is used when the destination name collides.

4. **Setup:** Select **Blank app** or **Include Syncfusion controls**.

5. **Controls:** When you include controls, choose one or more controls from the following list. Controls start unchecked, and at least one selection is required. Each selected control generates its own XAML page and code-behind, and data-driven samples also include a view model.

    ![Configured WinUI options in the Syncfusion .NET CLI](images/cli-winui-configuration.png)

    | Control | Control ID | NuGet package |
    | --- | --- | --- |
    | AI AssistView | `ai-assist-view` | `Syncfusion.Chat.WinUI` |
    | Cartesian Chart | `cartesian-chart` | `Syncfusion.Chart.WinUI` |
    | Circular Chart | `circular-chart` | `Syncfusion.Chart.WinUI` |
    | DataGrid | `datagrid` | `Syncfusion.Grid.WinUI` |
    | DockingManager | `docking-manager` | `Syncfusion.DockingManager.WinUI` |
    | Kanban | `kanban` | `Syncfusion.Kanban.WinUI` |
    | Markdown Viewer | `markdown-viewer` | `Syncfusion.MarkdownViewer.WinUI` |
    | Ribbon | `ribbon` | `Syncfusion.Ribbon.WinUI` |
    | Scheduler | `scheduler` | `Syncfusion.Scheduler.WinUI` |
    | TreeGrid | `treegrid` | `Syncfusion.Grid.WinUI` |
    | TreeView | `treeview` | `Syncfusion.TreeView.WinUI` |

6. **Post-create:** Select **Generate only** or **Build project**.
7. **Confirmation:** Review the selected values and confirm to create the project.

N> A complete direct command does not open the wizard. When a name is missing in an interactive terminal, the wizard supplies a default and collects the remaining unspecified inputs. Missing required values in scripts produce an error.

N> On macOS and Linux, use `--post-action generate` for portable source generation. The CLI explains that building and running WinUI apps requires Windows.

## Create a project using direct commands

To create a blank project without the wizard:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet new winui -n MyApp

{% endhighlight %}
{% endtabs %}

To create a project containing Syncfusion<sup>®</sup> control samples:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet new winui -n MyApp --control datagrid
sfdotnet new winui -n MyApp --control datagrid chart treeview
sfdotnet new winui -n MyApp --control datagrid chart treegrid ribbon docking-manager

{% endhighlight %}
{% endtabs %}

To select the .NET version and generate sources without restoring or building:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

sfdotnet new winui --name MyApp --target-framework net10.0 --control empty --post-action generate --no-interactive

{% endhighlight %}
{% endtabs %}

## Run the created project

After creation, the CLI prints a copyable **Next commands** block. Build and run the generated project on Windows:

{% tabs %}
{% highlight bash tabtitle="Bash" %}

cd <project-location>\MyApp
dotnet run --project .\MyApp\MyApp.csproj --no-build

{% endhighlight %}
{% endtabs %}

Native XAML compilation and runtime checks require Windows. Restore can run on other hosts; use `--post-action generate` there and build after copying the project to a Windows machine.

![Sample generated in the Syncfusion .NET CLI](images/cli-generated-sample.png)

## Creation options

| Option | Description |
| --- | --- |
| `-n`, `--name` | Project name. Required when prompting is unavailable |
| `-p`, `--path` | Parent directory. Defaults to `%USERPROFILE%\source\repos` |
| `-t`, `--target-framework` | The .NET target framework: `net10.0` (default) or `net9.0` |
| `--control` | One or more control IDs, or `empty`. Omit to create an empty project |
| `--post-action` | Post-create action: `generate` or `build`. Defaults to `build` for direct commands |
| `--dry-run` | Preview the action without making changes |
| `--force` | Allow supported overwrites |
| `--no-restore` | Skip `dotnet restore` after the action |
| `--no-build` | Skip `dotnet build` after the action |
| `--no-interactive` | Disable interactive prompts |
| `--json` | Emit a JSON document instead of table output |

N> `--post-action build` conflicts with `--no-build`. Neither `--force` nor confirmation authorizes overwriting an existing project destination.

## FAQs

**Which .NET versions are supported for WinUI?**

.NET 10 (`net10.0`) and .NET 9 (`net9.0`). C# is the supported language, and projects use the native WinUI theme.

**Can I build a WinUI project on macOS or Linux?**

Use `--post-action generate` to generate the sources on other hosts. Building and launching require Windows because the projects use the Windows App SDK with a win-x64 runtime identifier.

**Why do DataGrid and TreeGrid share a package?**

Both controls are provided by `Syncfusion.Grid.WinUI`. Use the control alias (`datagrid` or `treegrid`) to add the matching sample.

## See also

* [Manage packages in an existing project](/winui/dotnet-cli/manage-packages)
* [License activation](/winui/dotnet-cli/licensing)
* [MCP configuration](/winui/dotnet-cli/configure-mcp)
* [AI skills installation](/winui/dotnet-cli/install-skills)
* [Windows App SDK unpackaged deployment](https://learn.microsoft.com/windows/apps/windows-app-sdk/deploy-unpackaged-apps)
