---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: a84dee14872ad5a7d0f7bac8e0057dc527855074
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99596217"
---
# Find-RoleCapability

## 摘要
在模块中查找角色功能。

## SYNTAX

### 全部

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Find-RoleCapability`Cmdlet 可搜索已注册的存储库，以便查找 PowerShell 角色功能和模块。

对于找到的每个角色功能 `Find-RoleCapability` ，都将返回 **PSGetRoleCapabilityInfo** 对象。 可以通过管道将 **PSGetRoleCapabilityInfo** 对象发送到 `Install-Module` 或 `Save-Module` cmdlet。

PowerShell 角色功能定义 (JEA) 终结点上的足够管理的用户可使用哪些命令和应用程序。 角色功能由扩展名为的文件定义 `.psrc` 。

## 示例

### 示例1：查找角色功能

`Find-RoleCapability` 查找每个已注册存储库中的角色功能。 若要搜索特定存储库，请使用 **存储库** 参数。

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 示例2：按名称查找角色功能

`Find-RoleCapability` 按名称查找角色功能。 使用逗号分隔名称数组。

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 示例3：查找并保存角色功能的模块

`Find-RoleCapability`Cmdlet 查找角色功能，并沿管道向下发送对象。
`Save-Module` 将角色功能的模块保存到文件系统。 `Get-ChildItem` 显示模块目录的内容。

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability` 使用 **Name** 参数指定 **一般的 Lev1** 角色功能。
对象沿管道向下发送。 `Save-Module` 使用文件系统位置的 **Path** 参数保存模块。 保存该模块后，将 `Get-ChildItem` 指定该模块的 **路径** 并显示 **JeaExamples** 模块的目录的内容。

### 示例4：查找和安装角色功能的模块

`Find-RoleCapability` 查找模块并沿管道向下发送对象。 `Install-Module` 安装模块。 安装后，请使用 `Get-InstalledModule` 查看结果。

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability` 使用 **Name** 参数指定 **一般的 Lev1** 角色功能。
对象沿管道向下发送。 `Install-Module` 使用 **Verbose** 参数显示安装过程中的状态消息。 安装完成后， `Get-InstalledModule` 输出确认已安装 **JeaExamples** 模块。

## PARAMETERS

### -AllowPrerelease

在结果中包括标记为预发行的资源。

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

### -AllVersions

指示此 cmdlet 获取模块的所有版本。 **AllVersions** 参数显示模块的每个可用版本。

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

### -Filter

基于 **PackageManagement** 提供程序的搜索语法查找资源。 例如，指定要在 **ModuleName** 和 **Description** 属性内搜索的字词。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定要包含在结果中的模块的最高版本。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

指定要包括在结果中的模块的最低版本。 不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleName

指定要在其中搜索角色功能的模块的名称。 默认值为所有模块。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定角色功能的名称。 默认值为所有角色功能。 使用逗号分隔资源名称的数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
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

指定有权使用 **代理** 参数中指定的代理服务器的用户帐户。

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

指定用于搜索角色功能的存储库。 使用逗号分隔存储库名称数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定要包含在结果中的模块的确切版本号。 无法在同一命令中使用 **RequiredVersion** 和 **MinimumVersion** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag

指定对存储库中的模块进行分类的标记。 使用逗号分隔标记数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Uri

### System.Management.Automation.PSCredential

## 输出

### PSGetRoleCapabilityInfo

`Find-RoleCapability`Cmdlet 将返回 **PSGetRoleCapabilityInfo** 对象。

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Save-Module](Save-Module.md)
