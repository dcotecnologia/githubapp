# Installing GitHub Desktop

GitHub Desktop currently supports Windows 7 (or higher), macOS 10.9 (or higher) and Linux (x64).

### macOS

Download the `GitHub Desktop.zip`, unpack the application and put it wherever you want.

### Windows

On Windows you have two options:

 - Download the `GitHubDesktopSetup.exe` and run it to install it for the current user.
 - Download the `GitHubDesktopSetup.msi` and run it to install a machine-wide version of GitHub Desktop - each logged-in user will then be able to run GitHub Desktop from the program at `%PROGRAMFILES(x86)\GitHub Desktop Installer\desktop.exe`.

### Linux

The CI build (`.github/workflows/ci.yml`) uploads two Linux x64 artifacts:

 - `GitHubDesktop-amd64.deb` - install it with `sudo apt install ./GitHubDesktop-amd64.deb`. The app is installed to `/opt/GitHubDesktop`, available as the `github-desktop` command and in your application menu.
 - `GitHubDesktop-linux-x64.tar.gz` - unpack it anywhere and run the `desktop` executable inside.

You can also build these packages yourself, see [Setting Up Development Dependencies on Linux](./contributing/setup-linux.md) and the [packaging documentation](./technical/packaging.md#linux). Installers for other distributions are available from the [`shiftkey/desktop`](https://github.com/shiftkey/desktop) fork.

## Data Directories

GitHub Desktop will create directories to manage the files and data it needs to function. If you manage a network of computers and want to install GitHub Desktop, here is more information about how things work.

### macOS
 - `~/Library/Application Support/GitHub Desktop/` - this directory contains user-specific data which the application requires to run, and is created on launch if it doesn't exist. Log files are also stored in this location.

### Linux
 - `~/.config/GitHub Desktop/` - this directory contains user-specific data which the application requires to run, and is created on launch if it doesn't exist. Log files are also stored in this location.

### Windows

 - `%LOCALAPPDATA%\GitHubDesktop\` - contains the latest versions of the app, and some older versions if the user has updated from a previous version.
 - `%APPDATA%\GitHub Desktop\` - this directory contains user-specific data which the application requires to run, and is created on launch if it doesn't exist. Log files are also stored in this location.

## Log Files

GitHub Desktop will generate logs as part of its normal usage, to assist with troubleshooting. They are located in the data directory that GitHub Desktop uses (see above) under a `logs` subdirectory, organized by date using the format `YYYY-MM-DD.desktop.production.log`, where `YYYY-MM-DD` is the day the log was created.

## Installer Logs

Problems with installing or updating GitHub Desktop are tracked in a separate file which is managed by the updater frameworks used in the app.

### macOS

 - `~/Library/Caches/com.github.GitHubClient.ShipIt/ShipIt_stderr.log` - this file will contain details about why the installation or update failed - check the end of the file for recent activity.

### Windows

 - `%LOCALAPPDATA%\GitHubDesktop\SquirrelSetup.log` - this file will contain details about update attempts for GitHub Desktop after it's been successfully installed.
 - `%LOCALAPPDATA%\SquirrelSetup.log` - information about the initial installation may be found here. As this framework is used by different apps, it may also contain details about other apps. Ensure that you focus on mentions of `GitHubDesktop.exe` in the log.

