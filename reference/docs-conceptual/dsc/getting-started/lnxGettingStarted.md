---
ms.date: 01/07/2021
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 Desired State Configuration (DSC) 入门
description: 本主题说明如何开始使用适用于 Linux 的 PowerShell Desired State Configuration (DSC)。
ms.openlocfilehash: 6f0dea956b16c0828964a10b43abbbc65879ea33
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040916"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>适用于 Linux 的 Desired State Configuration (DSC) 入门

本主题说明如何开始使用适用于 Linux 的 PowerShell Desired State Configuration (DSC)。
有关 DSC 的常规信息，请参阅 [Windows PowerShell Desired State Configuration 入门](../overview/overview.md)。

## <a name="supported-linux-operation-system-versions"></a>支持的 Linux 操作系统版本

适用于 Linux 的 DSC 支持以下 Linux 操作系统版本。

- CentOS 5、6 和 7 (x86/x64)
- Debian GNU/Linux 6、7 和 8 (x86/x64)
- Oracle Linux 5、6 和 7 (x86/x64)
- Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)
- SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)
- Ubuntu Server 12.04 LTS、14.04 LTS、16.04 LTS、18.04 (x86/x64)

## <a name="installing-dsc-for-linux"></a>安装适用于 Linux 的 DSC

必须先安装[开放式管理基础结构 (OMI)](https://github.com/Microsoft/omi)，才能安装适用于 Linux 的 DSC。

### <a name="installing-omi"></a>安装 OMI

适用于 Linux 的 Desired State Configuration 需要开放式管理基础结构 (OMI) CIM 服务器版本 1.0.8.1 或更高版本。 可从 The Open Group：[Open Management Infrastructure (OMI)（开放式管理基础结构）](https://github.com/Microsoft/omi)下载 OMI。

若要安装 OMI，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。 RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。

> [!NOTE]
> 若要确定安装的 OpenSSL 版本，请运行 `openssl version` 命令。

运行以下命令以在 CentOS 7 x64 系统上安装 OMI。

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>安装 DSC

适用于 Linux 的 DSC 可从存储库中的 [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-926) 存储库下载。

若要安装 DSC，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。 RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。

> [!NOTE]
> 若要确定安装的 OpenSSL 版本，请运行 openssl version 命令。

运行以下命令以在 CentOS 7 x64 系统上安装 DSC。

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>使用适用于 Linux 的 DSC

以下章节说明了如何在 Linux 计算机上创建和运行 DSC 配置。

### <a name="creating-a-configuration-mof-document"></a>创建配置 MOF 文档

使用 Windows PowerShell Configuration 关键字为 Linux 计算机创建配置，与为 Windows 计算机创建配置类似。 以下步骤描述了如何使用 Windows PowerShell 为 Linux 计算机创建配置文档。

1. 导入 nx 模块。 此 nx Windows PowerShell 模块包含适用于 Linux 的 DSC 内置资源的架构，必须将其安装到本地计算机上并导入到配置中。

   - 若要安装 nx 模块，请将 nx 模块目录复制到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules` 中。 该 nx 模块包含在适用于 Linux 的 DSC 安装包中。 若要在配置中导入 nx 模块，请使用 `Import-DSCResource` 命令：

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. 定义配置并生成配置文档：

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>将配置推送到 Linux 计算机

可使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置文档（MOF 文件）推送到 Linux 计算机。 若要将此 cmdlet 和 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlet 远程运用到 Linux 计算机，必须使用 CIMSession。 使用 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet 将 CIMSession 创建到 Linux 计算机中。

以下代码表明了如何创建适用于 Linux 的 DSC CIMSession。

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
# $opt = New-CimSessionOption -UseSsl -SkipCACheck -SkipCNCheck -SkipRevocationCheck

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl

$sessParams = @{
    Credential = $credential
    ComputerName = $Node
    Port = 5986
    Authentication = 'basic'
    SessionOption = $opt
    OperationTimeoutSec = 90
}

$Sess = New-CimSession @sessParams
```

> [!NOTE]
> 对于“推送”模式，用户凭据必须为 Linux 计算机上的根用户。 适用于 Linux 的 DSC 仅支持 SSL/TLS 连接，使用 `New-CimSession` 时必须将 –UseSSL 参数设置为 $true。 在 `/etc/opt/omi/conf/omiserver.conf` 文件中通过 pemfile 和 keyfile 属性指定（DSC 的）OMI 使用的 SSL 证书。 如果 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet 运行于的 Windows 计算机不信任此证书，你可以通过以下 CIMSession 选项选择忽略证书验证：`-SkipCACheck -SkipCNCheck -SkipRevocationCheck`

运行以下命令以将 DSC 配置推送到 Linux 节点。

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>使用请求服务器分发配置

可使用请求服务器将配置分发到 Linux 计算机，与分发到 Windows 计算机类似。 有关使用请求服务器的指南，请参阅 [Windows PowerShell Desired State Configuration 请求服务器](../pull-server/pullServer.md)。 有关通过请求服务器使用 Linux 计算机其他信息和限制条件，请参阅“适用于 Linux 的 Desired State Configuration 发行说明”。

### <a name="working-with-configurations-locally"></a>从本地进行配置

适用于 Linux 的 DSC 包括用于从本地 Linux 计算机进行配置的脚本。 这些脚本位于 `/opt/microsoft/dsc/Scripts` 中，包括以下内容：

- GetDscConfiguration.py

  返回应用于此计算机的当前配置。 与使用 Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet 类似。

  `# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

  返回应用于此计算机的当前元配置。 与 cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet 类似。

  `# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

  安装自定义 DSC 资源模块。 需要包含模块共享对象库和架构 MOF 文件的 .zip 文件的路径。

  `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

  删除自定义 DSC 资源模块。 需要待删除模块的名称。

  `# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

  将配置 MOF 文件应用于计算机。 与 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 类似。 需要待应用的配置 MOF 的路径。

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

  将元配置 MOF 文件应用于计算机。 与 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 类似。 需要待应用的元配置 MOF 的路径。

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>适用于 Linux 的 PowerShell Desired State Configuration 日志文件

为适用于 Linux 的.DSC 生成了以下日志文件。

|     日志文件      |     Directory      |                                               说明                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| **omiserver.log** | `/var/opt/omi/log` | 与 OMI CIM 服务器操作相关的消息。                                                |
| **dsc.log**       | `/var/opt/omi/log` | 与本地配置管理器 (LCM) 操作和 DSC 资源操作相关的消息。 |
