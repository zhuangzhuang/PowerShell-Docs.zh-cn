---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: f9cba90ffa69d04df196f4062c8f190d545b9bc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595396"
---
# Find-Module

## 摘要
查找存储库中与指定条件匹配的模块。

## SYNTAX

### 全部

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## DESCRIPTION

`Find-Module`Cmdlet 可在存储库中查找与指定条件匹配的模块。
`Find-Module` 返回它找到的每个模块的 **PSRepositoryItemInfo** 对象。 这些对象可通过管道向下发送到 cmdlet，例如 `Install-Module` 。

第一次 `Find-Module` 尝试使用存储库时，系统可能会提示您安装更新。
如果存储库源未注册 `Register-PSRepository` 到 cmdlet，则会返回错误。

`Find-Module` 如果未使用限制版本的参数，则返回模块的最新版本。 若要获取存储库的模块版本的列表，请使用参数 **AllVersions**。

如果指定了 **MinimumVersion** 参数，则将 `Find-Module` 返回等于或大于最小值的模块的版本。 如果存储库中有可用的更新版本，则返回较新版本。

如果指定了 **MaximumVersion** 参数，则将 `Find-Module` 返回最新版本的模块，该模块不超过指定的版本。

如果指定了 **RequiredVersion** 参数，则 `Find-Module` 仅返回与指定版本完全匹配的模块版本。 `Find-Module` 搜索所有可用的模块，因为源之间的名称冲突可能会发生。

下面的示例使用 [PowerShell 库](https://www.powershellgallery.com/) 作为唯一的已注册存储库。 `Get-PSRepository` 显示已注册的存储库。 如果有多个已注册的存储库，请使用 `-Repository` 参数指定存储库的名称。

## 示例

### 示例1：按名称查找模块

此示例查找默认存储库中的模块。

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。

### 示例2：查找具有类似名称的模块

此示例使用 `*`) 通配符 (星号来查找具有类似名称的模块。

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

`Find-Module`Cmdlet 将 **Name** 参数与星号一起使用 (`*`) 通配符来查找包含 **PowerShell** 的所有模块。

### 示例3：按最低版本查找模块

此示例将搜索模块的最低版本。 如果存储库包含较新版本的模块，则返回较新版本。

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。 **MinimumVersion** 指定版本 **1.6.5**。 `Find-Module` 返回 PowerShellGet 版本 **2.1.0** ，因为它超过最低版本并且是最新版本。

### 示例4：查找特定版本的模块

此示例将返回一个对象，该对象表示模块的特定版本。 如果找不到指定版本，则会返回错误。

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。 **RequiredVersion** 参数指定版本 **1.6.5**。

### 示例5：查找特定存储库中的模块

此示例使用 **存储库** 参数查找特定存储库中的模块。

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdlet 使用 **Name** 参数来指定 **PowerShellGet** 模块。 **存储库** 参数指定搜索 **PSGallery** 存储库。

### 示例6：在多个存储库中查找模块

此示例使用 `Register-PSRepository` 指定存储库。 `Find-Module` 使用存储库搜索模块。

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

`Register-PSRepository`Cmdlet 将注册一个新存储库。 **Name** 参数将命名为 **MySource**。 **SourceLocation** 参数指定存储库的地址。

`Find-Module`Cmdlet 将 **Name** 参数与星号一起使用 (`*`) 通配符来指定 **Contoso** 模块。 **存储库** 参数指定搜索两个存储库，即 **PSGallery** 和 **MySource**。

### 示例7：查找包含 DSC 资源的模块

此命令返回包含 DSC 资源的模块。 **包含** 参数具有四个用于搜索存储库的预定义功能。 使用 "选项卡-完成" 显示 **包含** 参数支持的四项功能。

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

`Find-Module`Cmdlet 使用 **存储** 库参数搜索存储库 **PSGallery**。
**包含** 参数指定 **get-dscresource**，它是参数可在存储库中搜索的功能。

### 示例8：查找带有筛选器的模块

在此示例中，若要查找模块，请使用筛选器搜索存储库。

对于基于 NuGet 的存储库， **筛选器** 参数会搜索参数的名称、说明和标记。

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

`Find-Module`Cmdlet 使用 **筛选器** 参数在存储库中搜索 **AppDomain**。

## PARAMETERS

### -AllowPrerelease

包含在标记为预发行版的结果模块中。

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

指定在结果中包括某个模块的所有版本。 不能将 **AllVersions** 参数与 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion** 参数一起使用。

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

### -Command

指定要在模块中查找的命令数组。 命令可以是函数或工作流。

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

### -Credential

指定有权为指定的包提供程序或源安装模块的用户帐户。

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

### -DscResource

指定包含 DSC 资源的模块的名称或名称的一部分。 在提供多个参数时，按 PowerShell 约定执行 **或** 搜索。

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

### -Filter

基于 **PackageManagement** 提供程序特定的搜索语法指定筛选器。 对于 NuGet 模块，此参数等效于使用 [PowerShell 库](https://www.powershellgallery.com/) 网站上的搜索栏进行搜索。

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

### -IncludeDependencies

指示此操作包含依赖于在 **Name** 参数中指定的模块的所有模块。

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

### -Includes

仅返回那些包含特定类型的 PowerShell 功能的模块。 例如，你可能只想查找包含 **get-dscresource** 的模块。 此参数可接受的值如下所示：

- Cmdlet
- DscResource
- 函数
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定要包括在搜索结果中的模块的最大或最新版本。
不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 。

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

### -MinimumVersion

指定要包括在结果中的模块的最低版本。 不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 。

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

指定要在存储库中搜索的模块的名称。 接受以逗号分隔的模块名称列表。 可以使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Proxy

为请求指定代理服务器，而不是直接连接到 Internet 资源。

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

使用 " **存储库** " 参数可以指定要搜索模块的存储库。 当注册多个存储库时使用。 接受以逗号分隔的存储库列表。 若要注册存储库，请使用 `Register-PSRepository` 。 若要显示已注册的存储库，请使用 `Get-PSRepository` 。

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

指定要包含在结果中的模块的确切版本号。 对于 **MinimumVersion** 或 **MaximumVersion**，不能在同一命令中使用 **RequiredVersion** 。

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

### -Find-rolecapability

指定角色功能的数组。

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

### -Tag

指定标记的数组。 示例标记包括 **DesiredStateConfiguration**、 **DSC**、 **DSCResourceKit** 或 **PSModule**。

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

### System.String[]

### System.String

### System.Uri

### System.Management.Automation.PSCredential

## 输出

### PSRepositoryItemInfo

`Find-Module` 创建可通过管道向下发送到 cmdlet （如）的 **PSRepositoryItemInfo** 对象 `Install-Module` 。

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接

[Get-PSRepository](Get-PSRepository.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[Register-PSRepository](Register-PSRepository.md)
