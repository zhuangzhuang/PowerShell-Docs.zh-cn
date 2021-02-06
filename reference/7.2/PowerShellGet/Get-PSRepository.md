---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597882"
---
# Get-PSRepository

## 摘要
获取 PowerShell 存储库。

## SYNTAX

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**Get-PSRepository** cmdlet 可获取为当前用户注册的 PowerShell 模块存储库。

## 示例

### 示例 1：获取所有模块存储库

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

此命令将获取为当前用户注册的所有模块存储库。

### 示例 2：按名称获取模块存储库

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

此命令将获取名称中含有 NuGet 的所有模块存储库。

### 示例 3：获取模块存储库并设置输出格式

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

此命令将获取名为 Local01 的存储库，并使用管道运算符将该对象传递给 Format-List cmdlet。

## PARAMETERS

### -Name

指定要获取的存储库名称。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

## 输出

### System.Object

## 注释

## 相关链接

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)

