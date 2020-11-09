# PowerShell Scripts to Install/Uninstall Context Menu Items for Windows Terminal [Nested Elevation Layout]

This is a fork of [lextm/windowsterminal-shell](https://github.com/lextm/windowsterminal-shell). It includes a new custom layout, `NestedElevation`.

Similar to the `Default` layout, `NestedElevation` nests the different terminals in a sub-menu. The difference being that the option to open Windows Terminal with elevated permissions (Administrator) is also moved into the context menu's sub-menu. This populates the right-click context menu with just one option for opening Windows Terminal while still allowing easy access to each individual non-elevated and elevated terminals.

To install this new layout, ensure you meet the requirements of **Install** and simply run `install.ps1 nestedelevation`.

In the future, I hope to implement another layout that places the elevated terminals in a Shift-Rightclick menu.

*A project backed by [LeXtudio Inc.](https://www.lextudio.com)*

## Install

1. [Install Windows Terminal](https://github.com/microsoft/terminal).
2. [Install PowerShell 7](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7).
3. Launch PowerShell 7 console as administrator, and run `install.ps1` to install context menu items to Windows Explorer.

   > Quickest way to run the latest script from GitHub at an elevated PowerShell 7 console is

   > ``` powershell
   > Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/lextm/windowsterminal-shell/master/install.ps1'))
   > ```

Now the menu items are added to Windows Explorer context menu.

----

![default layout](default.png)

Figure 1: Default layout

> The menu items are organized in the `default` layout. Other layouts such as `mini`, `flat`, and `nestedelevation` give different look and feel. To apply an alternative layout (like `nestedelevation`), simply run `install.ps1 nestedelevation`.

![flat layout](flat.png)

Figure 2: Flat layout

![mini layout](mini.png)

Figure 3: Mini layout

![nestedelevation layout](nestedelevation.png)

Figure 4: Nested Elevation

## Uninstall
1. Run `uninstall.ps1` to uninstall context menu items from Windows Explorer.

> To uninstall an alternative layout (like `nestedelevation`), run `uninstall.ps1 nestedelevation`.

## Notes
The current release only supports Windows 10 machines (Windows Terminal restriction) and Windows Terminal installed via the store or .appx file.

> If Windows Terminal is installed via Scoop, [scripts from another repo](https://github.com/grimux/windowsterminal-shell-scoop/tree/scoop-support) might help.

The install script must be run as administrator.

> That's because it pulls out data from Windows Terminal's installation folder, which is locked down by Windows 10.

`install.ps1` and `uninstall.ps1` only manipulate current user's Windows Explorer settings for the context menu items, and do not write to Windows Terminal settings.

> So different users on the same machine must install the context menu items separately, but possibly with different layouts.

Downloading Windows Terminal icon from GitHub (in `install.ps1`) requires internet connection, but in general is just an optional step that won't be executed in most cases.

## More Products
To learn more about other cool products from LeXtudio Inc. , please visit [our homepage](https://www.lextudio.com/#projects).
