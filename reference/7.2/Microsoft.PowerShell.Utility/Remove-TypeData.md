---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 8ede1375faa1287b70eeb49689ec7fe1bb800d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603601"
---
# Remove-TypeData

## 摘要
从当前会话中删除扩展的类型。

## 语法

### RemoveTypeDataSet（默认值）

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-TypeData`Cmdlet 从当前会话中删除扩展类型数据。 此 cmdlet 只影响当前会话和当前会话中创建的会话。

可以通过在命令和文件中定义来向 PowerShell 中的对象添加属性和方法 `Update-TypeData` `Types.ps1xml` 。 `Remove-TypeData` 从当前会话中删除这些扩展属性和方法。 `Remove-TypeData` 不会删除 `Types.ps1xml` 文件或从文件中删除任何扩展类型定义 `Types.ps1xml` 。 有关文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例 1：删除指定类型的类型数据

此示例将从会话中删除 **system.object** 类型的所有类型数据，包括通过 `Types.ps1xml` 使用 cmdlet 添加到会话中的文件和动态类型数据添加的类型数据 `Update-TypeData` 。

```powershell
Remove-TypeData -TypeName System.Array
```

### 示例 2：从会话中删除扩展数据类型

此示例演示了从会话中删除扩展类型数据的效果。 第一 `Get-TypeData` 种是为 system.string 类型获取扩展类型数据。 输出显示已将 **datetime** 属性添加到 PowerShell 中的所有 **system.web** 对象。 `Get-Date`Cmdlet 将返回 **system.object** 对象。 该命令使用点表示法来获取返回的 **system.object** 对象的 **datetime** 属性的值 `Get-Date` 。

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

下一个 `Get-TypeData` cmdlet，用于获取 **system.web** 类型的所有扩展类型数据，并通过管道将其用于 `Remove-TypeData` 删除扩展类型数据。 最后一个 `Get-Date` cmdlet 显示删除 **system.object** 类型的扩展类型数据的效果。 由于不存在 **system.web** 属性，因此用于获取其值的命令不会返回任何内容。

### 示例 3：删除模块的扩展类型

此示例将删除模块对象的所有扩展类型数据。 将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取该对象类型的名称，并删除该类型的所有对象的所有类型数据。

```powershell
Get-Module | Remove-TypeData
```

### 示例 4：删除指定模块中的扩展类型

此示例使用 cmdlet 的 **Path** 参数 `Remove-TypeData` 删除 `Types.ps1xml` **PSScheduledJob** 和 **PSWorkflow** 模块添加的文件中定义的扩展类型。 此命令不会影响使用 cmdlet 添加的动态类型数据 `Update-TypeData` 。 仅当已将模块导入当前会话时，此命令才能够成功执行。

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

有关模块的详细信息，请参阅 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

### 示例 5：从远程会话中删除扩展类型

此示例将从远程会话中删除扩展类型。 该命令使用 `Invoke-Command` cmdlet 删除变量的会话中的所有 CIM 类型的扩展类型数据 `$S` 。

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## 参数

### -Path

指定此 cmdlet 将从会话扩展类型数据中删除的文件数组。 此参数是必需的。

输入一个或多个文件的路径和文件名 `Types.ps1xml` 。 不支持通配符。 如果省略路径，则默认位置为当前目录。

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

指定此 cmdlet 将从会话中删除的类型数据。 此参数是必需的。 输入包含 **update-typedata** 对象的变量， (**update-typedata**) 或获取 **update-typedata** 对象的命令（如命令）。 `Get-TypeData` 还可以通过管道将 **update-typedata** 对象传递给 `Remove-TypeData` 。

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

指定此 cmdlet 将删除其所有扩展类型数据的类型。 对于 System 命名空间中的类型，请输入其短名称。 否则，必须输入完整类型名称。 不支持通配符。

可以通过管道将类型命名为 `Remove-TypeData` 。 将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取对象的类型名称，并移除该对象类型的所有类型数据。

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

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

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

### System.Management.Automation.Runspaces.TypeData

可以通过管道将 **update-typedata** 对象（例如 cmdlet 返回的对象）传递 `Get-TypeData` 给 `Remove-TypeData` 。

### System.String

可以通过管道将类型名称传递给 `Remove-TypeData` 。 将对象通过管道传递给时 `Remove-TypeData` ，将 `Remove-TypeData` 获取对象的类型名称，并移除该对象类型的所有类型数据。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 说明

`Remove-TypeData` 只能删除当前会话中的扩展类型数据。 它无法删除位于计算机上的但未添加到当前会话的扩展类型数据，例如模块中定义的但未导入到当前会话中的扩展类型数据。

## 相关链接

[Get-TypeData](Get-TypeData.md)

[Update-TypeData](Update-TypeData.md)

