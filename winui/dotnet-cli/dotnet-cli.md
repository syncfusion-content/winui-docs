---
layout: post
title: Syncfusion .NET CLI Overview for WinUI | Syncfusion®
description: Learn to install and use the Syncfusion® .NET CLI (sf) to create WinUI 3 apps, manage Syncfusion WinUI NuGet packages, and register licenses.
platform: winui
control: Syncfusion<sup>®</sup> .NET CLI
documentation: ug
---

# Overview of the Syncfusion<sup>®</sup> .NET CLI

The Syncfusion<sup>®</sup> .NET CLI (`sf`) is a cross-platform command line tool that creates WinUI 3 projects, manages Syncfusion<sup>®</sup> WinUI NuGet packages, and registers licenses from a terminal. After you install the CLI, you can run `sf` with no arguments to open an interactive menu, or run a direct command such as `sf new winui` for scripted, prompt-free creation.

N> The Syncfusion<sup>®</sup> .NET CLI is currently in preview and is installed with the `--prerelease` flag.

You can use the CLI to perform the following actions:

* Create a blank WinUI 3 app, or an app containing generated Syncfusion<sup>®</sup> control samples.
* Add or update Syncfusion<sup>®</sup> WinUI NuGet package references in an existing project.
* List available and installed packages, and search the package catalog.
* Activate Syncfusion<sup>®</sup> licenses for the controls used in a sample, and view installed licenses.
* Generate projects for .NET MAUI, Blazor, WPF, WinForms, and WinUI 3.

This documentation covers the WinUI 3 platform.

## Prerequisites

The following software is required before you install and use the CLI:

* [.NET SDK](https://dotnet.microsoft.com/download). The SDK selected through `PATH` takes precedence, with the running .NET installation as a fallback.
* A Windows development environment. WinUI 3 projects use the Windows App SDK, and building and launching the generated apps require Windows.
* An internet connection so package operations can reach [nuget.org](https://www.nuget.org).
* A Syncfusion<sup>®</sup> account to activate licenses. Sign in is performed through the browser during license activation.

N> Syncfusion<sup>®</sup> packages resolve from the official nuget.org feed, `https://api.nuget.org/v3/index.json`. The CLI accepts only this source through `--source`.

N> The CLI does not require an installed `dotnet new winui` template. WinUI projects use an unpackaged, self-contained Windows App SDK application pattern with a minimum Windows 10 build of 19041 and a win-x64 runtime identifier.

## Installation

The CLI is published as a .NET global tool with the package ID `Syncfusion.DotNet.CLI`.

1. Open a terminal and run the following command. Add `--prerelease` while only preview versions are available.

    ```bash
    dotnet tool install -g Syncfusion.DotNet.CLI --prerelease
    ```

2. Verify the installation and print the CLI version.

    ```bash
    sf --version
    ```

To update the tool to the latest release, run:

```bash
dotnet tool update -g Syncfusion.DotNet.CLI --prerelease
```

To remove the tool, run:

```bash
dotnet tool uninstall -g Syncfusion.DotNet.CLI
```

## Initialize the CLI

Run `sf` in an interactive terminal to open the main menu. The menu shows the current CLI version and groups the available operations.

![Syncfusion .NET CLI main menu](images/cli-main-menu.png)

| Group | Operation | Command reference |
| --- | --- | --- |
| Project creation | Create a new project | `sf new` |
| Package management | Add a package to an existing project | `sf add` |
| Package management | Update a package in an existing project | `sf update` |
| Discovery | List available packages | `sf list <platform> packages` |
| Discovery | List installed packages in an existing project | `sf list <platform> installed` |
| Discovery | Search for packages | `sf search` |
| License management | Activate license | `sf license activate` |
| License management | View installed licenses | `sf license view` |
| License management | Sign in to Syncfusion | `sf login` |
| License management | Sign out | `sf logout` |
| Help and information | View CLI information | `sf info` |
| Help and information | Show help | `sf help` |
| Exit | Exit | `Ctrl+C` |

N> The `<platform>` text is a usage placeholder. Use `winui` for WinUI 3.

Use the following keys to navigate the interactive screens:

| Key | Action |
| --- | --- |
| Up / Down | Move through the options |
| Enter | Choose the focused option, or continue |
| Space | Toggle a checkbox in a multi-selection list |
| Escape | Cancel the current question and return to the menu |
| `Ctrl+C` | Exit the interactive session |

Complete direct commands remain usable without opening the menu. `--no-interactive` disables prompts in any command.

## Available commands

| Command | Purpose |
| --- | --- |
| `sf new winui` | Create a new WinUI 3 project |
| `sf add winui <package>` | Add a Syncfusion<sup>®</sup> package to an existing project |
| `sf update winui <package>` | Update a package in an existing project |
| `sf list winui packages` | List available packages |
| `sf list winui installed` | List installed packages in an existing project |
| `sf search winui <text>` | Search packages |
| `sf login` | Sign in to Syncfusion through the browser |
| `sf logout` | Sign out and clear the local session |
| `sf license activate` | Download the license for the project's packages and register it in the project's startup code |
| `sf license view` | Show the licenses cached for the project (no network call) |
| `sf info` | Show CLI information |
| `sf help winui` | Show the WinUI command map |
| `sf --version` | Show the CLI version |

![Show help in the Syncfusion .NET CLI](images/cli-help-command.png)

## Create a WinUI 3 project

You can create a WinUI 3 project through the interactive wizard or a direct command. WinUI projects are created with C#, and the theme is the native WinUI theme.

### Create a project using the interactive wizard

Run `sf new`, or select **Create a new project** from the main menu. The WinUI creation flow is:

1. **Platform:** Select **WinUI**.

    ![Framework selection in the Syncfusion .NET CLI](images/cli-create-new-project.png)

2. **Framework:** Select the .NET version.

    * .NET 10 (`net10.0`), the default
    * .NET 9 (`net9.0`)
    * .NET 8 (`net8.0`)

3. **Location and name:** Enter the parent directory and the project name. The suggested name is `SyncfusionWinUIApp`, and the first available numeric suffix is used when the destination name collides.

4. **Setup:** Select **Blank app** or **Include Syncfusion controls**.

5. **Controls:** When you include controls, choose one or more controls from the list. Controls start unchecked, and at least one selection is required.

    ![Configured WinUI options in the Syncfusion .NET CLI](images/cli-winui-configuration.png)

6. **Post-create:** Select **Generate only** or **Build project**.
7. **Confirmation:** Review the selected values and confirm to create the project.

N> A complete direct command does not open the wizard. When a name is missing in an interactive terminal, the wizard supplies a default and collects the remaining unspecified inputs. Missing required values in scripts produce an error.

N> On macOS and Linux, use `--post-action generate` for portable source generation. The CLI explains that building and running WinUI apps requires Windows.

### Available controls

The following controls are available in a new WinUI 3 project:

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

Each selected control generates its own XAML page and code-behind. Data-driven samples also include a view model. The DataGrid sample contains 50 editable orders across eight columns, the TreeGrid sample contains three teams with 21 employees, and the Chart sample contains 12 monthly sales points.

### Create a project using direct commands

To create a blank project without the wizard:

```bash
sf new winui -n MyApp
```

To create a project containing Syncfusion<sup>®</sup> control samples:

```bash
sf new winui -n MyApp --control datagrid
sf new winui -n MyApp --control datagrid chart treeview
sf new winui -n MyApp --control datagrid chart treegrid ribbon docking-manager
```

To select the .NET version and generate sources without restoring or building:

```bash
sf new winui --name MyApp --target-framework net9.0 --control empty --post-action generate --no-interactive
```

## Run the created project

After creation, the CLI prints a copyable **Next commands** block. Build and run the generated project on Windows:

```powershell
cd .\MyApp
dotnet run --project .\MyApp\MyApp.csproj --no-build
```

Native XAML compilation and runtime checks require Windows. Restore can run on other hosts; use `--post-action generate` there and build after copying the project to a Windows machine.

![Sample generated in the Syncfusion .NET CLI](images/cli-generated-sample.png)

## Manage packages in an existing project

Package operations change NuGet references only. They do not generate control files.

`<package>` accepts a canonical package alias, a canonical package ID, or an exact unambiguous package display name:

```bash
sf add winui grid
sf add winui Syncfusion.Grid.WinUI
sf update winui chart --version 35.1.40
```

Package add and update support `-v/--version`, `--source`, `--configfile`, `--no-restore`, `--dry-run`, and `--force`. Existing-project commands accept `-p/--path` with a `.csproj` file, a project directory, or a supported subdirectory. `--json` emits one JSON document for script use.

To list the available WinUI packages:

```bash
sf list winui packages
```

![List of available packages in the Syncfusion .NET CLI](images/cli-package-list.png)

To list the Syncfusion<sup>®</sup> packages installed in an existing project:

```bash
sf list winui installed -p .\MyApp\MyApp.csproj
```

To search the WinUI package catalog:

```bash
sf search winui chart
sf search chart --framework winui
```

N> WinUI projects retain package-only operations. Package operations never apply control registration based on package metadata.

## Activate Syncfusion<sup>®</sup> licenses

The CLI detects the Syncfusion<sup>®</sup> controls used in a project, downloads the matching license keys from your Syncfusion<sup>®</sup> account, and registers the keys in the project's startup code. For example, when a sample is created with the DataGrid control, the CLI registers the license for `Syncfusion.Grid.WinUI` in `App.xaml.cs` so the build runs without a license warning.

N> Open the Command Prompt or Terminal in the target sample's project directory before running the license activation command. The license operation is project-specific, and the command path must point to the intended sample.

### How license activation works

1. The CLI scans the project at the current directory or at the path you pass through `--path`. It identifies the platform from the project file (`.csproj`) and detects all Syncfusion<sup>®</sup> `PackageReference` entries whose IDs start with `Syncfusion.`.
2. It checks your Syncfusion<sup>®</sup> account for entitlements that cover each detected package. When a paid or trial entitlement is available, the matching license keys are downloaded.
3. The keys are cached in `syncfusion-license.txt` and metadata in `.syncfusion/license-meta.json` inside the project directory.
4. The CLI inserts `SyncfusionLicenseProvider.RegisterLicense(...)` into the platform-specific startup file. For WinUI, the block is added to `App.xaml.cs` inside the `App` constructor, before any other initialization. The block is idempotent, so re-running the command refreshes the keys without duplicating the call.
5. If a control in the project is not covered by a paid entitlement, the CLI prompts you to accept the Syncfusion<sup>®</sup> trial EULA and download a trial key for the missing packages. Pass `--yes` to accept the prompt automatically.

### Activate a license through the interactive menu

1. Open the Command Prompt or Terminal in the target sample's project directory.

    ```bash
    cd D:\CLI\NetWinUISample
    ```

2. Run `sf` to open the main menu.

    ```bash
    sf
    ```

3. Under **License management**, select **Activate license**. The CLI focuses the **Activate License** entry and shows the navigation hint at the bottom of the screen.

    ![Activate license option in the Syncfusion .NET CLI](images/cli-activate-license.png)

4. If you are not signed in, the CLI opens your default browser to the Syncfusion<sup>®</sup> sign-in page. Complete sign in with your Syncfusion<sup>®</sup> account.

    ![Syncfusion sign-in page in the browser](images/cli-license-sign-in.png)

5. After sign in, the CLI checks your entitlements, downloads the matching keys for the Syncfusion<sup>®</sup> controls in the sample, and registers the keys in `App.xaml.cs`.

    ![License registered successfully in the Syncfusion .NET CLI](images/cli-license-registered.png)

6. Rebuild the application so the newly registered license is applied. The CLI prints the following reminder at the end of the activation output.

    > Note: Rebuild the application so the newly registered license is applied.

### Activate a license using a direct command

Run the activation command from the sample's project directory:

```bash
sf license activate
```

Pass `--path` to point the CLI at a specific project directory or `.csproj` file:

```bash
sf license activate --path ./MyApp
sf license activate --path ./MyApp/MyApp.csproj
```

Use `--yes` to accept the trial EULA prompt without asking:

```bash
sf license activate --yes
```

Use `--file` to activate from an existing key file. With no value, the CLI reads `./syncfusion-license.txt` from the project directory. With an absolute path, the CLI uses the specified file instead:

```bash
sf license activate --file
sf license activate --file C:\keys\syncfusion-license.txt
```

N> When a license key is supplied through `--file`, the CLI skips sign in and download and registers the keys already in the file. The file path must be absolute.

### View installed licenses

To see the licenses cached for the current project, run:

```bash
sf license view
```

The command reads the cached metadata, lists each product, the license type, the status, and the expiry date, and warns when a Syncfusion<sup>®</sup> package in the project is not covered.

![View installed licenses in the Syncfusion .NET CLI](images/cli-view-installed-license-menu.png)

The cached output reports the registered email, platform, major version, and one row per product.

![Installed license details in the Syncfusion .NET CLI](images/cli-view-installed-license.png)

### License operation notes

* License activation is project-specific. The command path must point to the intended sample, because each project is detected through its `.csproj` and scanned independently.
* The CLI writes `syncfusion-license.txt` and `.syncfusion/license-meta.json` to the project directory.
* The startup file the CLI modifies by platform is `MauiProgram.cs` for .NET MAUI, `Program.cs` for Blazor, `App.xaml.cs` for WPF, `App.xaml.cs` for WinUI, and `Program.cs` (or `Application.xaml.vb` for VB) for WinForms.
* Use `sf logout` to clear the local sign-in session. Use `sf login` to sign in again without running activation.

## Options reference

### Creation options

| Option | Description |
| --- | --- |
| `-n`, `--name` | Project name. Required when prompting is unavailable |
| `-p`, `--path` | Parent directory. Defaults to the current directory |
| `-t`, `--target-framework` | The .NET target framework: `net10.0`, `net9.0`, or `net8.0` |
| `--control` | One or more control IDs, or `empty`. Omit to create an empty project |
| `--post-action` | Post-create action: `generate` or `build`. Defaults to `build` for direct commands |
| `--dry-run` | Preview the action without making changes |
| `--force` | Allow supported overwrites |
| `--no-restore` | Skip `dotnet restore` after the action |
| `--no-build` | Skip `dotnet build` after the action |
| `--no-interactive` | Disable interactive prompts |
| `--json` | Emit a JSON document instead of table output |

N> `--post-action build` conflicts with `--no-build`. Neither `--force` nor confirmation authorizes overwriting an existing project destination.

### Package operation options

| Option | Description |
| --- | --- |
| `-p`, `--path` | The project directory, `.csproj` file, or a supported subdirectory |
| `-v`, `--version` | The Syncfusion<sup>®</sup> NuGet package version |
| `--source` | Package source; Syncfusion<sup>®</sup> packages require `https://api.nuget.org/v3/index.json` |
| `--configfile` | The NuGet configuration file to use |
| `--dry-run` | Preview the action without making changes |
| `--force` | Allow supported overwrites |
| `--no-restore` | Skip `dotnet restore` after the action |
| `--json` | Emit one JSON document |

### License options

| Option | Description |
| --- | --- |
| `-p`, `--path` | The project directory or `.csproj`/`.vbproj` to scan for Syncfusion<sup>®</sup> packages. Defaults to the current directory |
| `-y`, `--yes` | Accept the trial EULA prompt automatically during activation |
| `--file` | Activate from an existing key file. With no value, the CLI reads `./syncfusion-license.txt` from the project directory. With an absolute path, the CLI uses the specified file |
| `--json` | Emit one JSON document instead of table output |

## Licensing

You can register a Syncfusion<sup>®</sup> license for a generated or existing WinUI 3 project directly through the CLI. `sf license activate` scans the project for Syncfusion<sup>®</sup> `PackageReference` entries, downloads the matching license keys from your Syncfusion<sup>®</sup> account, and inserts `SyncfusionLicenseProvider.RegisterLicense(...)` into `App.xaml.cs`. For background information on Syncfusion<sup>®</sup> licensing, refer to the [licensing overview](https://help.syncfusion.com/common/essential-studio/licensing/overview).

To register an existing license without writing values into generated sources, you can also set the `SYNCFUSION_LICENSE_KEY` environment variable in the application environment. When controls are selected, generated apps read this variable and register the license at startup. Refer to the [WinUI licensing overview](https://help.syncfusion.com/winui/licensing/overview) to generate a license key.

## FAQs

**Does the CLI register a license?** Yes. `sf license activate` scans the project for Syncfusion<sup>®</sup> `PackageReference` entries, downloads the matching license keys from your Syncfusion<sup>®</sup> account, and inserts `SyncfusionLicenseProvider.RegisterLicense(...)` into `App.xaml.cs` (or the platform-specific startup file). The CLI signs you in through the browser the first time, or you can sign in ahead with `sf login`. For background information on Syncfusion<sup>®</sup> licensing, refer to the [licensing overview](https://help.syncfusion.com/common/essential-studio/licensing/overview).

**Where does the CLI register the license for WinUI?** In `App.xaml.cs`, inside the `App` constructor before any other initialization. For .NET MAUI, Blazor, WPF, and WinForms, the CLI targets `MauiProgram.cs`, `Program.cs`, `App.xaml.cs`, and `Program.cs` respectively.

**Can I use my own key file?** Yes. Run `sf license activate --file C:\keys\syncfusion-license.txt` with an absolute path. The CLI reads the keys from the file and registers them in the project's startup code without contacting the license service.

**Which .NET versions are supported for WinUI?** .NET 10 (`net10.0`), .NET 9 (`net9.0`), and .NET 8 (`net8.0`). C# is the supported language, and projects use the native WinUI theme.

**Can I build a WinUI project on macOS or Linux?** Use `--post-action generate` to generate the sources on other hosts. Building and launching require Windows because the projects use the Windows App SDK with a win-x64 runtime identifier.

**Why do DataGrid and TreeGrid share a package?** Both controls are provided by `Syncfusion.Grid.WinUI`. Use the control alias (`datagrid` or `treegrid`) to add the matching sample.

**Which platforms does the CLI support?** .NET MAUI, Blazor, WPF, WinForms, and WinUI 3. This documentation covers WinUI 3.

## See also

* [Syncfusion WinUI controls](https://www.syncfusion.com/winui-controls)
* [Syncfusion WinUI help documentation](https://help.syncfusion.com/winui/overview)
* [System requirements for WinUI](https://help.syncfusion.com/winui/system-requirements)
* [Windows App SDK unpackaged deployment](https://learn.microsoft.com/windows/apps/windows-app-sdk/deploy-unpackaged-apps)
* [Syncfusion<sup>®</sup> licensing overview](https://help.syncfusion.com/common/essential-studio/licensing/overview)