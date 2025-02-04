---
title: Set up a Default App
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn how to set up a default app using the Windows Device Portal or the shell.
keywords: windows iot, default app, PowerShell, iot
---

# Set up a default app
Here you'll learn the ways to set your application as the default application. The default application is the one that is launched when the system boots.  

> [!NOTE]
> Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.

## Runtime options

During development / experimental phases, you can change the default app by following means.

### Using Windows Device Portal

You can click on **Startup** column corresponding to the app.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### Using the shell

Steps to set the default app using the shell 

1. Connect to the device via [PowerShell](../connect-your-device/PowerShell.md)

2. List the applications installed using `iotstartup list`

3. Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`. For headless app, you should use `iotstartup add headless <appid>`.


## Build time option

For large deployments, you can achieve this using provisioning package

You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example. You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).

## How to configure "Home" key

Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.

To see how to enable the "Home" key, please visit our [IoT Shell page](./iotcoreshell.md#switching-between-apps-with-hid-injection-keys)