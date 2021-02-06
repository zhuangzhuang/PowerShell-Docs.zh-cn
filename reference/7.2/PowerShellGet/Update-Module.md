---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: f29c208805894634960085cd3816ce7780b7602f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598272"
---
# Update-Module

## 摘要
从联机库中下载指定模块的最新版本，并将其安装到本地计算机。

## SYNTAX

### 全部

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Update-Module`Cmdlet 可从联机库中安装模块的最新版本。 系统会在安装更新之前提示您确认。 只会为在本地计算机上安装的模块安装更新 `Install-Module` 。 `Update-Module` 搜索 `$env:PSModulePath` 已安装的模块。

`Update-Module` 如果未指定参数，则将更新所有已安装的模块。 若要指定要更新的模块，请使用 **Name** 参数。 您可以通过使用 **RequiredVersion** 参数，更新为模块的特定版本。

如果已安装的模块已经是最新版本，则不会更新该模块。 如果在中找不到该模块 `$env:PSModulePath` ，则会显示错误。

若要显示已安装的模块，请使用 `Get-InstalledModule` 。

## 示例

### 示例1：更新所有模块

此示例将所有已安装的模块更新到联机库中的最新版本。

```powershell
Update-Module
```

### 示例2：按名称更新模块

此示例将特定模块更新到联机库中的最新版本。

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module` 使用 **Name** 参数更新特定模块 **SpeculationControl**。

### 示例3：查看模拟 Update-Module 运行

此示例执行一个假设方案来显示在运行时所发生 `Update-Module` 的情况。 此命令不会运行。

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module` 使用 **WhatIf** 参数显示在运行时将发生 `Update-Module` 的情况。

### 示例4：将模块更新到指定版本

在此示例中，模块更新为特定版本。 该版本必须位于联机库中，否则将显示错误。

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module` 使用 **Name** 参数指定模块 **SpeculationControl**。 **RequiredVersion** 参数指定版本 **1.0.14**。

### 示例5：更新模块而不进行确认

此示例不会请求确认将模块从联机库更新到最新版本。 如果已安装该模块，则 **Force** 参数会重新安装该模块。

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module` 使用 **Name** 参数指定模块 **SpeculationControl**。 **Force** 参数更新模块，而不请求用户确认。

## PARAMETERS

### -AcceptLicense

如果包需要许可协议，则在安装过程中自动接受该协议。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrerelease

允许你使用标记为预发行版的新模块更新模块。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在运行之前提示你进行确认 `Update-Module` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有权更新模块的用户帐户。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

强制更新每个指定的模块，而不提示您请求确认。 如果已安装该模块，则 **强制** 重新安装该模块。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定要更新的单个模块的最高版本。 如果尝试更新多个模块，则无法添加此参数。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要更新的一个或多个模块的名称。 `Update-Module` 搜索 `$env:PSModulePath` 要更新的模块。 如果在指定的模块名称中找不到匹配项 `$env:PSModulePath` ，则会发生错误。

模块名称中接受通配符。 如果将通配符添加到指定的名称，但未找到匹配项，则不会发生错误。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

返回一个代表你所处理的项目的对象。 默认情况下，此 cmdlet 将不产生任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

为请求指定代理服务器，而不是直接连接到 internet 资源。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

指定有权使用 **代理** 参数指定的代理服务器的用户帐户。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定将更新现有已安装模块的确切版本。 **RequiredVersion** 指定的版本必须存在于联机库中，否则将显示错误。 如果在单个命令中更新了多个模块，则不能使用 **RequiredVersion**。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定模块的安装范围。 此参数可接受的值为 **AllUsers** 和 **CurrentUser**。 如果未指定 **作用域** ，则将在 **CurrentUser** 范围内安装更新。

**AllUsers** 作用域需要提升的权限，并将模块安装在计算机的所有用户都可以访问的位置：

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 不需要提升的权限，并且在只能由计算机的当前用户访问的位置中安装模块：

`$home\Documents\PowerShell\Modules`

如果未定义 **作用域** ，则将根据 PowerShellGet 版本设置默认值。

- 在 PowerShellGet 版本2.0.0 及更高版本中，默认值为 **CurrentUser**，无需进行提升即可安装。
- 在 PowerShellGet 1.x 版本中，默认值为 **AllUsers**，这需要提升才能进行安装。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行时将发生 `Update-Module` 的情况。 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

### System.String

### System.Management.Automation.PSCredential

### System.Uri

## 输出

### System.Object

## 注释

对于 PowerShell 版本6.0 及更高版本，默认安装范围始终为 **CurrentUser**。
**CurrentUser**、的模块更新 `$home\Documents\PowerShell\Modules` 不需要提升的权限。 **AllUsers** 的模块更新 `$env:ProgramFiles\PowerShell\Modules` 需要提升的权限。

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

`Update-Module` 在 Windows 7 或 Windows 2008 R2 及更高版本的 Windows 上的 powershell 3.0 或更高版本上运行。

如果未使用安装通过 **Name** 参数指定的模块 `Install-Module` ，则会发生错误。

仅可 `Update-Module` 通过运行在从联机库安装的模块上运行 `Install-Module` 。

如果 `Update-Module` 尝试更新正在使用的二进制文件，则将 `Update-Module` 返回一个错误，用于识别问题的处理过程。 停止进程后，通知用户重试 `Update-Module` 。

## 相关链接

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Uninstall-模块](Uninstall-Module.md)
