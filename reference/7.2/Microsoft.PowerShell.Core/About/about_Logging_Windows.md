---
description: PowerShell 将引擎、提供程序和 cmdlet 的内部操作记录到 Windows 事件日志中。
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: d6ae50b50911417da8dd306cad69e3fc7129fedc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596407"
---
# <a name="about-logging-windows"></a>关于日志记录窗口

## <a name="short-description"></a>简短说明
PowerShell 将引擎、提供程序和 cmdlet 的内部操作记录到 Windows 事件日志中。

## <a name="long-description"></a>长说明

PowerShell 记录有关 PowerShell 操作的详细信息，例如启动和停止引擎和提供程序，以及执行 PowerShell 命令。

> [!NOTE]
> Windows PowerShell 版本3.0、4.0、5.0 和5.1 包含 Windows 事件日志的 **事件** 日志 cmdlet。 在这些版本中，若要显示 **EventLog** cmdlet 的列表，请键入： `Get-Command -Noun EventLog` 。 有关详细信息，请参阅你的 Windows PowerShell 版本的 cmdlet 文档和 about_EventLogs。

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>查看 Windows 上的 PowerShell 事件日志条目

可以使用 Windows 事件查看器查看 PowerShell 日志。 事件日志位于 "应用程序" 和 "服务日志" 组中，并命名为 `PowerShellCore` 。 关联的 ETW 提供程序 `GUID` 为 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 。

启用脚本块日志记录时，PowerShell 会将以下事件记录到 `PowerShellCore/Operational` 日志中：

|  字段  |       值       |
| ------- | ----------------- |
| EventId | `4104` / `0x1008` |
| 通道 | `Operational`     |
| 级别   | `Verbose`         |
| 操作码  | `Create`          |
| 任务    | `CommandStart`    |
| 关键字 | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a>在 Windows 上注册 PowerShell 事件提供程序

与 Linux 或 macOS 不同，Windows 要求先注册事件提供程序，然后才能将事件写入事件日志。 若要启用 PowerShell 事件提供程序，请从提升的 PowerShell 提示符中运行以下命令。

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a>在 Windows 上注销 PowerShell 事件提供程序

注册事件提供程序会在用于对事件进行解码的二进制库中放置锁。 若要更新此库，必须取消注册该提供程序以释放此锁定。

若要注销 PowerShell 提供程序，请从提升的 PowerShell 提示符中运行以下命令。

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

更新 PowerShell 后，运行 `$PSHOME\RegisterManifest.ps1` 以注册更新的事件提供程序。

## <a name="enabling-script-block-logging"></a>启用脚本块日志记录

启用脚本块日志记录时，PowerShell 将记录其处理的所有脚本块的内容。 启用后，任何新的 PowerShell 会话都将记录此信息。

> [!NOTE]
> 如果使用脚本块日志记录作为诊断目的以外的任何内容，则建议启用受保护的事件日志记录，如下所述。

可以通过组策略或注册表设置来启用脚本块日志记录。

### <a name="using-group-policy"></a>使用组策略

若要启用自动脚本，请 `Turn on PowerShell Script Block
Logging` 在组策略中启用该功能 `Administrative Templates -> Windows
Components -> Windows PowerShell` 。

### <a name="using-the-registry"></a>使用注册表

运行以下函数：

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>受保护的事件日志记录

提高系统日志记录的级别，可以提高记录的内容可能包含敏感数据的可能性。 例如，启用脚本日志记录后，可以将脚本使用的凭据或其他敏感数据写入事件日志。 当包含记录的敏感数据的计算机受到威胁时，日志可以为攻击者提供扩展其范围所需的信息。

为了保护此信息，Windows 10 引入了受保护的事件日志记录。
受保护的事件日志记录使参与的应用程序可以加密写入事件日志的敏感数据。 稍后，你可以通过更安全且集中的日志收集器来解密和处理这些日志。

使用 IETF 加密消息语法 (CMS) 标准保护事件日志内容。 CMS 使用公钥加密。 用于对内容进行加密和解密的密钥保持独立。

公钥可以广泛共享，并且不是敏感数据。 使用此公钥加密的任何内容只能通过私钥进行解密。 有关公钥加密的详细信息，请参阅 [维基百科-公钥加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。

若要启用受保护的事件日志记录策略，请将一个公钥部署到具有要保护的事件日志数据的所有计算机。 对应的私钥用于在更安全的位置（如中心事件日志收集器或 [SIEM][] 聚合器）后处理事件日志。 可以在 Azure 中设置 SIEM。 有关详细信息，请参阅 [通用 SIEM 集成](/cloud-app-security/siem)。

### <a name="enabling-protected-event-logging-via-group-policy"></a>通过组策略启用受保护的事件日志记录

若要启用受保护的事件日志记录，请 `Enable Protected Event Logging` 在组策略中启用该功能 `Administrative Templates -> Windows Components
-> Event Logging` 。 此设置需要一个加密证书，你可以使用以下几种形式之一提供该证书：

- 64编码的 x.509 证书的内容 (例如，如 `Export` 证书管理器) 中的选项所提供的那样。
- 可在本地计算机证书存储 (中找到的证书的指纹，可通过 PKI 基础结构) 部署。
- 证书的完整路径 (可以是本地的，也可以是远程共享) 。
- 包含证书的目录的路径或证书 (可以是本地的，也可以是远程共享) 。
- 可在本地计算机证书存储 (中找到的证书的使用者名称，可通过 PKI 基础结构) 部署。

生成的证书必须具有 `Document Encryption` () 的增强型密钥用法 `1.3.6.1.4.1.311.80.1` ，并 `Data Encipherment` 启用或 `Key
Encipherment` 启用密钥用法。

> [!WARNING]
> 不应将私钥部署到计算机日志记录事件。 应将其保存在一个安全的位置，以便对消息进行解密。

### <a name="decrypting-protected-event-logging-messages"></a>解密受保护的事件日志记录消息

下面的脚本将检索并解密，前提是你有私钥：

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>请参阅

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[向蓝色团队 PowerShell](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[通用 SIEM 集成](/cloud-app-security/siem)

<!-- link references -->
SIEM
