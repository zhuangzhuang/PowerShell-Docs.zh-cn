---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603591"
---
# Invoke-DscResource

## 摘要
 (DSC) 资源运行指定的 PowerShell 所需状态配置的方法。

## SYNTAX

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

`Invoke-DscResource` cmdlet 运行指定的 PowerShell 所需状态配置 (DSC) 资源的方法。

此 cmdlet 直接调用 DSC 资源，而无需创建配置文档。 使用此 cmdlet，配置管理产品可以使用 DSC 资源来管理 windows 或 Linux。 在启用调试的情况下运行 DSC 引擎时，此 cmdlet 还可用于调试资源。

> [!NOTE]
> `Invoke-DscResource` 是 PowerShell 7 中的实验性功能。 若要使用 cmdlet，必须使用以下命令启用它。
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## 示例

### 示例1：通过指定资源的必需属性来调用该资源的 Set 方法

此示例调用名为 **WindowsProcess** 的资源的 **Set** 方法，并提供必需的 **路径** 和 **参数** 属性来启动指定的 Windows 进程。

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### 示例2：为指定模块调用资源的测试方法

此示例调用名为 **WindowsProcess** 的资源的 **测试** 方法，该资源位于名为 **PSDesiredStateConfiguration** 的模块中。

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETERS

### -方法

指定此 cmdlet 调用的资源的方法。 此参数可接受的值包括： **Get**、 **Set** 和 **Test**。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleName

指定此 cmdlet 从中调用指定资源的模块的名称。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

指定要启动的 DSC 资源的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Property

分别在哈希表中将资源属性名称及其值指定为键和值。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

### ModuleSpecification。

## 输出

### System.Object

## 注释

- 以前，Windows PowerShell 5.1 资源在系统上下文下运行，除非使用 key **PsDscRunAsCredential** 通过用户上下文指定。 在 PowerShell 7.0 中，资源在用户的上下文中运行，并且不再支持 **PsDscRunAsCredential** 。 使用此密钥的以前的配置将引发异常。

- 从 PowerShell 7 中， `Invoke-DscResource` 不再支持调用 WMI DSC 资源。 这包括 PSDesiredStateConfiguration 中的文件和日志资源  。

## 相关链接

[Windows PowerShell Desired State Configuration 概述](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscResource](Get-DscResource.md)
