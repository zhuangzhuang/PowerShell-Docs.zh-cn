---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599053"
---
# Get-HotFix

## 摘要
获取本地或远程计算机上安装的修补程序。

## SYNTAX

### Default（默认值）

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### 说明

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## DESCRIPTION

`Get-Hotfix`Cmdlet 可获取本地计算机或指定远程计算机上安装的修补程序或更新。 可以 Windows 更新、Microsoft 更新、Windows Server Update Services 或手动安装这些更新。

## 示例

### 示例1：获取本地计算机上的所有修补程序

`Get-Hotfix`Cmdlet 将获取在本地计算机上安装的所有修补程序。

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### 示例2：从由字符串筛选的多台计算机获取修补程序

该 `Get-Hotfix` 命令使用参数获取远程计算机上安装的修补程序。 结果按指定的描述字符串进行筛选。

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix` 用 **Description** 参数和包含星号 () 通配符的字符串 **安全** 筛选输出 `*` 。 **ComputerName** 参数包含以逗号分隔的远程计算机名字符串。 **Credential** 参数指定有权访问远程计算机并运行命令的用户帐户。

### 示例3：验证是否已安装更新并将计算机名称写入文件

此示例中的命令验证是否安装了特定更新。 如果未安装该更新，则会将计算机名称写入文本文件。

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

`$A`变量包含通过文本文件获取的计算机名称 `Get-Content` 。 中的对象 `$A` 将向下发送到 `ForEach-Object` 。 `if`语句将 cmdlet 用于 `Get-Hotfix` **Id** 参数，并为每个计算机名称使用特定 id 号。 如果计算机未安装指定的修补程序 Id，则该 `Add-Content` cmdlet 会将计算机名称写入文件。

### 示例4：获取本地计算机上的最新修补程序

此示例获取计算机上安装的最新修补程序。

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` 将对象向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 按升序对对象排序，并使用 **Property** 参数来评估每个 **InstalledOn** 日期。 数组表示法 `[-1]` 选择最新安装的修补程序。

## PARAMETERS

### -ComputerName

指定远程计算机。 键入远程计算机的 NetBIOS 名称、Internet 协议 (IP) 地址或完全限定的域名 (FQDN)。

当 **ComputerName** 参数未指定时， `Get-Hotfix` 将在本地计算机上运行。

**ComputerName** 参数不依赖于 Windows PowerShell 远程处理。 如果你的计算机未配置为运行远程命令，请使用 **ComputerName** 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权访问计算机并运行命令的用户帐户。 默认值为当前用户

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

`Get-HotFix` 使用 **Description** 参数指定修补程序类型。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

筛选 `Get-HotFix` 特定修补程序 id 的结果。 不接受通配符。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 字符串

可以通过管道将一个或多个计算机名称传递给修补程序。

## 输出

### System.management.managementobject # root\CIMV2\ Win32_QuickFixEngineering

`Get-HotFix` 返回表示计算机上的修补程序的对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

**Win32_QuickFixEngineering** [WMI 类](/windows/desktop/WmiSdk/retrieving-a-class)表示系统范围较小的更新，通常称为 "快速修补工程"， (QFE) update，应用于当前操作系统。 此类仅返回由基于组件的服务所提供的更新 (CBS) 。 注册表中未列出这些更新。 **Win32_QuickFixEngineering** 未返回 MICROSOFT WINDOWS INSTALLER (MSI) 或 [Windows 更新](https://update.microsoft.com)站点提供的更新。 有关详细信息，请参阅 [Win32_QuickFixEngineering 类](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)。

`Get-HotFix`不同操作系统上的输出可能有所不同。

## 相关链接

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Add-Content](Add-Content.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Win32_QuickFixEngineering 类](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
