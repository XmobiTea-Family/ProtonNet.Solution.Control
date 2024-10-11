
# ProtonNet Server

![GitHub release](https://img.shields.io/github/release/XmobiTea-Family/ProtonNetSolution.svg)
![License](https://img.shields.io/github/license/XmobiTea-Family/ProtonNetSolution)
[![GitHub star chart](https://img.shields.io/github/stars/XmobiTea-Family/ProtonNetSolution?style=social)](https://star-history.com/#XmobiTea-Family/ProtonNetSolution)

# ProtonNet Control

## I. Introduction
`ProtonNet Control` is a deployment tool that helps to deploy your `ProtonNet Server` applications into `production` environments. With high flexibility, `ProtonNet Control` is compatible with various operating systems like `Windows`, `Linux`, and `macOS`.

## II. Installation Requirements
- If your project uses **.NET Core**: Download **.NET** here: [Download .NET](https://dotnet.microsoft.com/en-us/download/dotnet)
- If your project uses **.NET Framework**: Download **.NET Framework** here: [Download .NET Framework](https://dotnet.microsoft.com/en-us/download/dotnet-framework)

### Note:
Only `Windows` supports `.NET Framework`.

- If your server runs on `Windows`, in addition to `.NET Core` versions like `net6.0`, `net8.0`, `netcoreapp3.1`, you can configure the `TargetFramework` with `.NET Framework` versions like `net46`, `net461`, `net462`, `net47`, `net471`, `net472`, `net48`, `net481`.
- If your server runs on `Linux` or `macOS`, only `.NET Core` versions like `net6.0`, `net8.0`, or `netcoreapp3.1` are supported.

## III. Usage

### Download and extract [ProtonNet Control Release](https://github.com/XmobiTea-Family/ProtonNet.Solution.Control/releases) to your server.


After building your `ProtonNet Server` application, copy all files and folders from the final `build` folder and paste them into `applications/your_project_name`.

Next, modify the `ProtonNetServerSettings.json` file to configure `ProtonNet Control` to recognize your project:

```json
{
  "$schema": "https://schema.protonnetserver.com/1.0/ServerSettings/schema.json",
  "TargetFramework": "net8.0", // Defines the .NET version of your project, e.g., net46, net481, netcoreapp3.1, net6.0,...
  "TargetRuntime": "win-x64", // The operating system and architecture that will run the ProtonNet Server project
  "Instances": [ // Configure the instances in this project
    {
      "Name": "webapiserver", // Instance name, must be unique
      "Enable": true, // Enable or disable this instance
      "ServerType": "WebApi", // WebApi for WebApi projects, Socket for Socket projects
      "BinPath": "webapiserver", // Path to the binary files in the applications folder
      "AssemblyName": "webapiserver", // The Assembly name of your project
      "StartupSettingsFilePath": "StartupSettings.json", // Path to the StartupSettings configuration file
      "Log4NetFilePath": "log4net.config", // Path to the Log4Net configuration file
      "StartupType": "auto" // Startup type
    }
  ]
}
```

### Commands:

#### On Windows, use the command:
```
control.bat command [instance_name]
```

#### On Linux or macOS, use the command:
```
./control.sh command [instance_name]
```

Example to check the status of an instance with the Name `webapiserver`:
```
./control.sh status webapiserver
```

## IV. List of Commands

- `version`: Displays the operating system and ProtonNet Control version.
- `help`: Displays available commands.
- `debug [instance_name]`: Debug whether the ProtonNet Server project is running properly.
- `start [instance_name]`: Start the ProtonNet Server project as a service (must be `installed` first).
- `stop [instance_name]`: Stop the service that was previously started.
- `restart [instance_name]`: Restart the service.
- `install [instance_name]`: Install the ProtonNet Server project as a service.
- `uninstall [instance_name]`: Remove the service from the ProtonNet Server project.
- `status [instance_name]`: Show the current status of the project.
- `log [instance_name]`: Display all logs during the execution of this project.

## V. Support
If you encounter issues, feel free to share them on [ProtonNet Discussions](https://discussions.protonnetserver.com) for support, or contact me via email at changx.develop@gmail.com.

**Happy development with ProtonNet!**
