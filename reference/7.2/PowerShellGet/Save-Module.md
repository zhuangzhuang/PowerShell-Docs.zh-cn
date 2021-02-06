---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: df5056b4402664602409388825c8b2b8acd4e02f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598052"
---
# Save-Module

## 摘要
将模块及其依赖项保存在本地计算机上，但不会安装该模块。

## SYNTAX

### NameAndPathParameterSet (默认值) 

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameAndLiteralPathParameterSet

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObjectAndLiteralPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObjectAndPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Save-Module`Cmdlet 从已注册的存储库下载模块和任何依赖项。
`Save-Module` 下载并保存模块的最新版本。 文件将保存到本地计算机上的指定路径。 未安装该模块，但可以由管理员检查内容。 然后，可以将保存的模块复制到 `$env:PSModulePath` 脱机计算机的相应位置。

`Get-PSRepository` 显示本地计算机的已注册存储库。 你可以使用 `Find-Module` cmdlet 来搜索已注册的存储库。

## 示例

### 示例1：保存模块

在此示例中，模块及其依赖项保存到本地计算机。

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。 **Path** 参数指定下载的模块的存储位置。 **存储库** 参数指定已注册的存储库 **PSGallery**。 下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。

### 示例2：保存模块的特定版本

此示例演示如何使用参数（如 **MaximumVersion**）或 **RequiredVersion** 来指定模块版本。

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。 **Path** 参数指定下载的模块的存储位置。 **存储库** 参数指定已注册的存储库 **PSGallery**。 **MaximumVersion** 指定下载并保存版本 **2.1.0** 。 下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。

### 示例3：查找并保存模块的特定版本

在此示例中，在存储库中找到所需的模块版本，并将其保存到本地计算机。

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

`Find-Module` 使用 **Name** 参数指定模块 **PowerShellGet**。 **存储库** 参数指定已注册的存储库 **PSGallery**。 **RequiredVersion** 指定版本 **1.6.5**。

将对象向下发送到 `Save-Module` 。 **Path** 参数指定下载的模块的存储位置。 下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。

## PARAMETERS

### -AcceptLicense

如果包需要许可协议，则自动接受该协议。

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

允许您保存标记为预发行的模块。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

提示你在运行之前进行确认 `Save-Module` 。

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

指定有权保存模块的用户帐户。

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

强制 `Save-Module` 运行而不请求用户确认。

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

### -InputObject

接受 **PSRepositoryItemInfo** 对象。 例如，输出 `Find-Module` 到变量，并将该变量用作 **InputObject** 参数。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定一个或多个位置的路径。 **LiteralPath** 参数的值完全按输入方式使用。 不会将任何字符解释为通配符。 如果路径包含转义符，请将其括在单引号内。 PowerShell 不会将括在单引号中的任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaximumVersion

指定要保存的模块的最大或最新版本。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要保存的单个模块的最低版本。 如果尝试安装多个模块，则无法添加此参数。 不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要保存的模块的名称数组。

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定本地计算机上存储已保存模块的位置。 接受通配符。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。

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

### -Repository

指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。 用于 `Get-PSRepository` 显示已注册的存储库。

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定要保存的模块的确切版本号。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

显示运行时将发生的情况 `Save-Module` 。 cmdlet 未运行。

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

### System.web. system.exception []

### System.String

### System.Uri

### System.Management.Automation.PSCredential

## 输出

### System.Object

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接
