---
title: 在 Windows 上安装 PowerShell
description: 介绍如何在 Windows 上安装 PowerShell
ms.date: 02/02/2021
ms.openlocfilehash: befc5ff156cb7c3843d89e394e903778682ba28e
ms.sourcegitcommit: 40b6d8e9b6d791ac69e2ff85224e900b21552bc1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2021
ms.locfileid: "99536486"
---
# <a name="installing-powershell-on-windows"></a>在 Windows 上安装 PowerShell

有多种方法可以在 Windows 中安装 PowerShell。

## <a name="prerequisites"></a>先决条件

Windows 7 SP1、Server 2008 R2 及更高版本支持最新版 PowerShell。

若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：

- 在低于 Windows 10 的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。 可以通过直接下载或 Windows 更新来获取它。 完全修补的系统已安装此包。
- 在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) 4.0 或更高版本。 有关 WMF 的详细信息，请参阅 [WMF 概述](/powershell/scripting/wmf/overview)。

## <a name="download-the-installer-package"></a>下载安装程序包

若要在 Windows 上安装 PowerShell，请从 GitHub 下载[最新][]安装包。 你也可以找到最新的[预览版][]版本。 向下滚动到“版本”页的“资产”  部分。 由于“资产”  部分可能处于折叠状态，因此可能需要单击展开它。

## <a name="installing-the-msi-package"></a><a id="msi" />安装 MSI 包

MSI 文件如下所示：`PowerShell-<version>-win-<os-arch>.msi`。 例如：

- `PowerShell-7.1.1-win-x64.msi`
- `PowerShell-7.1.1-win-x86.msi`

下载后，双击安装程序并按照提示进行操作。

安装程序在 Windows“开始”菜单中创建一个快捷方式。

- 默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\<version>`
- 可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 启动 PowerShell

> [!NOTE]
> PowerShell 7.1 安装到新目录，并与 Windows PowerShell 5.1 并行运行。
> PowerShell 7.1 是就地升级，升级后会替换 PowerShell 6.x 或 PowerShell 7.0。
>
> - PowerShell 7.1 安装到 `$env:ProgramFiles\PowerShell\7`
> - `$env:ProgramFiles\PowerShell\7` 文件夹已添加到 `$env:PATH`
> - `$env:ProgramFiles\PowerShell\6` 文件夹已删除
>
> 如果需要与其他版本并行运行 PowerShell 7.1，请使用 [ZIP 安装](#zip)方法将其他版本安装到其他文件夹。

### <a name="administrative-install-from-the-command-line"></a>通过命令行进行管理安装

可以通过命令行安装 MSI 包，这样管理员能够在没有用户交互的情况下部署包。 MSI 包中有下列控制安装选项的属性：

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此属性控制向 Windows 资源管理器中的上下文菜单添加“打开 PowerShell”  项的选项。
- **ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - 此属性控制向 Windows 资源管理器中的上下文菜单添加“使用 PowerShell 运行”项的选项。
- **ENABLE_PSREMOTING** - 此属性控制用于在安装过程中启用 PowerShell 远程处理的选项。
- **REGISTER_MANIFEST** - 此属性控制用于注册 Windows 事件日志记录清单的选项。

下面的示例展示了如何在启用所有安装选项的情况下无提示安装 PowerShell。

```powershell
msiexec.exe /package PowerShell-7.1.1-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

有关 `Msiexec.exe` 命令行选项的完整列表，请参阅[命令行选项](/windows/desktop/Msi/command-line-options)。

### <a name="registry-keys-created-during-installation"></a>在安装过程中创建注册表项

从 PowerShell 7.1 开始，MSI 包将创建用于存储 PowerShell 安装位置和版本的注册表项。 这些值位于 `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` 中。 每种内部版本类型（发行版或预览版）、主要版本和体系结构的 `<GUID>` 的值都是唯一的。

|    发布    | 体系结构 |                                          注册表项                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| 7.1.x 版本 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| 7.1.x 版本 |     X64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| 7.1.x 预览版 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| 7.1.x 预览版 |     X64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

管理员和开发人员可以使用此值查找 PowerShell 的路径。 所有预览版本和次要版本的 `<GUID>` 值都是相同的。 每个主要版本的 `<GUID>` 值都有所变化。

## <a name="installing-the-zip-package"></a><a id="zip" />安装 ZIP 包

提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。 从 [版本][releases] 页下载以下某个 ZIP 存档。

- PowerShell-7.1.1-win-x64.zip
- PowerShell-7.1.1-win-x86.zip
- PowerShell-7.1.1-win-arm64.zip
- PowerShell-7.1.1-win-arm32.zip

根据该文件的下载方式，你可能需要使用 `Unblock-File` cmdlet 解锁。 将内容解压到你选择的位置，然后从该位置运行 `pwsh.exe`。 与安装 MSI 包不一样，安装 ZIP 存档不会检查先决条件。 为了让使用 WSMan 的远程处理能够正常运行，请确保已满足[先决条件](#prerequisites)。

使用此方法在类似于 Microsoft Surface Pro X 的计算机上安装基于 ARM 的 PowerShell 版本。为获得最佳结果，请将 PowerShell 安装到 `$env:ProgramFiles\PowerShell\7` 文件夹。

## <a name="deploying-on-windows-10-iot-enterprise"></a>Windows 10 IoT 企业版部署

Windows 10 IoT 企业版随附 Windows PowerShell，可用来部署 PowerShell 7。

1. 在目标设备中创建 `PSSession`

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. 将 ZIP 包复制到设备

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. 连接到设备并展开存档

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. 设置 PowerShell 7 远程处理

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. 连接到设备上的 PowerShell 7 终结点

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Windows 10 IoT 核心版部署

当你添加 IOT_POWERSHELL  功能后，Windows 10 IoT 核心版便会添加 Windows PowerShell，我们可以使用它来部署 PowerShell 7。 对于 IoT 核心版，还可以遵循为 Windows 10 IoT 企业版定义的步骤。

若要在随附映像中添加最新的 PowerShell，请使用 [Import-PSCoreRelease][] 命令在工作区域中添加包，然后将 OPENSRC_POWERSHELL 功能添加到映像中。

> [!NOTE]
> 对于 ARM64 体系结构，在你添加 IOT_POWERSHELL 功能后，它不会添加 Windows PowerShell。 因此，基于 zip 的安装将不起作用。 需要使用 `Import-PSCoreRelease` 命令将其添加到映像中。

## <a name="deploying-on-nano-server"></a>在 Nano Server 上进行部署

为了更好地理解这些说明，假定 Nano Server 是已运行 PowerShell 版本的“无外设”操作系统。 有关详细信息，请参阅 [Nano Server 映像生成器](/windows-server/get-started/deploy-nano-server)文档。

可以使用两种不同的方法来部署 PowerShell 二进制文件。

1. 脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。
1. 联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。

在这两种情况下，都需要 Windows 10 x64 ZIP 版本包。 在 PowerShell 的“管理员”实例中运行命令。

### <a name="offline-deployment-of-powershell"></a>PowerShell 脱机部署

1. 使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。
1. 卸载映像并启动。
1. 连接到 Windows PowerShell 的内置实例。
1. 按照说明使用[“另一种实例技术”][]创建远程处理终结点。

### <a name="online-deployment-of-powershell"></a>PowerShell 联机部署

若要将 PowerShell 部署到 Nano Server，请按照以下步骤操作。

- 连接到 Windows PowerShell 的内置实例

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- 将文件复制到 Nano Server 实例

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- 输入会话

  ```powershell
  Enter-PSSession $session
  ```

- 提取 ZIP 文件

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- 如果需要基于 WSMan 的远程处理，请按照说明使用[“另一种实例技术”][]创建远程处理终结点。

## <a name="install-as-a-net-global-tool"></a>作为 .NET 全局工具安装

如果你已安装 [.NET Core SDK](/dotnet/core/sdk)，则可以轻松地安装 PowerShell 作为 [.NET 全局工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

dotnet 工具安装程序将 `$env:USERPROFILE\dotnet\tools` 添加到 `$env:PATH` 环境变量中。 不过，当前运行的 shell 没有更新后的 `$env:PATH`。 若要从新 shell 启动 PowerShell，可以键入“`pwsh`”。

## <a name="install-powershell-via-winget"></a>通过 Winget 安装 PowerShell

通过 `winget` 命令行工具，开发人员可以在 Windows 10 计算机上查找、安装、升级、删除和配置应用程序。 此工具是 Windows 程序包管理器服务的客户端接口。

> [!NOTE]
> 目前 `winget` 是预览功能。 当前并非所有计划功能都可用。
> 不应在生产部署方案中使用此方法。 若要查看系统要求列表和安装说明，请参阅 [winget] 文档。

通过以下命令，可使用已发布的 `winget` 包安装 PowerShell：

1. 搜索最新版本的 PowerShell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.1.1
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.1-preview.5
   ```

1. 使用 `--exact` 参数安装 PowerShell 版本

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><a id="msix" />从 Microsoft Store 安装

PowerShell 7.1 已发布到 Microsoft Store。 你可以在 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 网站上或在 Windows 应用商店应用程序中找到 PowerShell 版本。

Microsoft Store 包的权益：

- 直接内置于 Windows 10 的自动更新
- 与其他软件分发机制（如 Intune 和 SCCM）集成

的限制：

MSIX 包在应用程序沙盒中运行，后者用于虚拟化对某些文件系统和注册表位置的访问。

- HKEY_CURRENT_USER 下的所有注册表更改都将在写入到专用、每个用户、每个应用位置时进行复制。 因此，这些值不能用于其他应用程序。
- 不能修改存储在 `$PSHOME` 中的任何系统级配置设置。 其中包括 WSMAN 配置。 这可以防止远程会话连接到 PowerShell 的基于应用商店的安装。 支持用户级配置和 SSH 远程处理。

有关详细信息，请参阅[了解打包的桌面应用如何在 Windows 上运行](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)。

### <a name="using-the-msix-package"></a>使用 MSIX 包

> [!NOTE]
> PowerShell 的预览版本包含一个 MSIX 包。 MSIX 包尚未获得正式支持。 生成此包的目的是为了在预览期间进行测试。

要在 Windows 10 客户端上手动安装 MSIX 包，请从 GitHub [版本][releases] 页下载 MSIX 包。 向下滚动到要安装的版本的“资产”部分。  “资产”部分可能处于折叠状态，因此可能需要单击使其展开。

MSIX 文件类似于 - `PowerShell-<version>-win-<os-arch>.msix`

必须使用 `Add-AppxPackage` cmdlet，才能安装此包。

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a>如何创建远程处理终结点

PowerShell 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。 有关详细信息，请参阅：

- [在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]
- [在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]

## <a name="upgrading-an-existing-installation"></a>升级现有安装

若要在升级时获得最佳结果，应使用首次安装 PowerShell 时使用的相同安装方法。 每个安装方法都会将 PowerShell 安装在不同的位置中。 如果你不确定如何安装 PowerShell，可以将安装的位置与本文中的包信息进行比较。 如果是通过 MSI 包安装的，则该信息将显示在“程序和功能”控制面板中。

## <a name="installation-support"></a>安装支持

Microsoft 支持本文档中的安装方法。 其他源可能会提供其他安装方法。 尽管这些工具和方法可能有效，但 Microsoft 无法支持这些方法。

<!-- link references -->

[预览版]: https://aka.ms/powershell-release?tag=preview
[latest]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
