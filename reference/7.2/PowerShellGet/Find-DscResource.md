---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: e1cb814d349d6b77885ebaaf176a7c3153d93eb5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "99598253"
---
# Find-DscResource

## 摘要
 (DSC) 资源中查找所需的状态配置。

## SYNTAX

### 全部

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Find-DscResource`Cmdlet 可搜索已注册的存储库，以查找模块中包含的 DSC 资源。 默认情况下， `Find-DscResource` 搜索所有已注册的存储库。

对于找到的每个模块 `Find-DscResource` ，都将返回 **PSGetDscResourceInfo** 对象。
可以通过管道将 **PSGetDscResourceInfo** 对象发送到 `Install-Module` cmdlet。
`Install-Module` 安装模块。

## 示例

### 示例1：查找所有 DSC 资源

`Find-DscResource` 返回已注册存储库中的 DSC 资源。 若要搜索特定存储库，请使用 **存储库** 参数。

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### 示例2：按名称查找 DSC 资源

`Find-DscResource` 按名称定位 DSC 资源。 使用逗号分隔资源名称的数组。

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource` 使用 **Name** 参数查找指定的 DSC 资源数组。

### 示例3：查找 DSC 资源并安装它

`Find-DscResource` 定位 DSC 资源，并将对象向下发送到要安装的管道。
安装后，请使用 `Get-InstalledModule` 查看结果。

同一个模块中的多个资源可以通过管道向下发送到 `Install-Module` 。
`Install-Module` 尝试仅安装该模块一次。

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource` 使用 **Name** 参数查找名为 **xWebsite** 的资源。 对象通过管道向下发送到 `Install-Module` cmdlet。 `Install-Module` 安装资源的 **xWebAdministration** 模块。

### 示例4：查找模块中的所有 DSC 资源

`Find-DscResource` 查找指定模块中包含的所有 DSC 资源。 默认情况下，将显示当前版本。 若要显示其他版本，请使用 **AllVersions** 或 **RequiredVersions** 参数。

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource` 使用 **ModuleName** 参数指定 **xWebAdministration** ，并查找模块中包含的 DSC 资源。 显示每个资源的当前版本。

### 示例5：按标记和所需版本查找 DSC 资源

可以使用参数 **标记** 和 **RequiredVersion** 定位 DSC 资源。 **标记** 显示存储库中包含指定标记的每个资源的当前版本。
**RequiredVersion** 需要 **ModuleName** 参数， **Name** 参数是可选的。 **Name** 和 **ModuleName** 参数会限制输出。 使用 **AllVersions** 参数显示 DSC 资源的可用版本。

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### 示例6：使用筛选器查找资源

`Find-DscResource` 查找所有资源，并使用 **Filter** 参数按 **域** 指定结果。 **Filter** 参数在对象的说明或模块名称中查找筛选器值。 使用 `Select-Object` cmdlet 查看对象的属性。

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

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

**AllVersions** 参数显示每个 DSC 资源的可用版本。 不能将 **AllVersions** 参数与 **MinimumVersion**、 **MaximumVersion** 或 **RequiredVersion** 参数一起使用。

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

指定要包含在结果中的资源的最大版本。 不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。

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

指定要包含在结果中的资源的最低版本。 不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。

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

指定包含 DSC 资源的模块。

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

指定资源的名称。 默认值为 "所有资源"。 使用逗号分隔资源名称的数组。

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

指定要在其中搜索资源的存储库。 使用逗号分隔存储库名称数组。

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

## 输出

### PSGetDscResourceInfo

`Find-DscResource` 返回 **PSGetDscResourceInfo** 对象。

## 注释

> [!IMPORTANT]
> 自 2020 年 4 月起，PowerShell 库已不再支持传输层安全性 (TLS) 版本 1.0 和 1.1。 如果你使用的不是 TLS 1.2 或更高版本，那么，在尝试访问 PowerShell 库时，将会收到错误。 使用以下命令可以确定使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 有关详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)。

## 相关链接

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-模块](Uninstall-Module.md)
