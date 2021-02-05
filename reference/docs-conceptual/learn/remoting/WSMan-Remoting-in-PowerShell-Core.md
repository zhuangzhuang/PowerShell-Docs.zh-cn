---
title: PowerShell Core 中的 WS-Management (WSMan) 远程处理
description: 在 PowerShell Core 中使用 WSMan 进行远程处理
ms.date: 08/06/2018
ms.openlocfilehash: fdc4159279db28b8ee60bc0853e19512a1f9ec14
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501297"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>PowerShell Core 中的 WS-Management (WSMan) 远程处理

## <a name="instructions-to-create-a-remoting-endpoint"></a>有关创建远程处理终结点的说明

适用于 Windows 的 PowerShell Core 包包括 WinRM 插件 (`pwrshplugin.dll`) 和 `$PSHome` 中的安装脚本 (`Install-PowerShellRemoting.ps1`)。 指定终结点时，这些文件可使 PowerShell 接受传入的 PowerShell 远程连接。

### <a name="motivation"></a>动机

安装 PowerShell 可使用 `New-PSSession` 和 `Enter-PSSession` 针对远程计算机创建 PowerShell 会话。 若要使其接受传入的 PowerShell 远程连接，用户必须创建一个 WinRM 远程处理终结点。 这是一个显式选择加入方案，其中用户运行 Install-PowerShellRemoting.ps1 创建 WinRM 终结点。 将其他功能添加到 `Enable-PSRemoting` 以执行相同操作前，安装脚本是一个短期解决方案。 有关详细信息，请参阅问题 [#1193](https://github.com/PowerShell/PowerShell/issues/1193)。

### <a name="script-actions"></a>脚本操作

脚本

1. 在 `$env:windir\System32\PowerShell` 中创建插件目录
1. 将 pwrshplugin.dll 复制到该位置
1. 生成配置文件
1. 使用 WinRM 注册该插件

### <a name="registration"></a>注册

脚本必须在管理员级别的 PowerShell 会话中执行，并且以两种模式中运行。

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>由其将注册的 PowerShell 实例执行

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>由代表其注册实例的另一 PowerShell 实例执行

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

例如：

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

> [!NOTE]
> 远程处理注册脚本将重启 WinRM。 运行此脚本后，所有现有 PSRP 会话将立即终止。 如果在远程会话期间运行，脚本将终止连接。

## <a name="how-to-connect-to-the-new-endpoint"></a>如何连接到新的终结点

指定 `-ConfigurationName "some endpoint name"`，从而针对新 PowerShell 终结点创建一个 PowerShell 会话。 若要连接到上述示例中的 PowerShell 实例，请使用以下任意一种方式：

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

请注意，未指定 `-ConfigurationName` 的 `New-PSSession` 和 `Enter-PSSession` 调用将以默认 PowerShell 终结点 `microsoft.powershell` 为目标。
