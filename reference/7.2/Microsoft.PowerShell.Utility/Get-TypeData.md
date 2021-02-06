---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: db5dc586f2a165d83c25bdf2addaeb625f9e1ba0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596403"
---
# Get-TypeData

## 摘要
获取当前会话中的扩展类型数据。

## 语法

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## 说明

`Get-TypeData`Cmdlet 将获取当前会话中的扩展类型数据。 这包括通过 `Types.ps1xml` 使用 cmdlet 的参数添加的文件和动态类型数据添加到会话中的类型数据 `Update-TypeData` 。

您可以使用返回的扩展类型数据 `Get-TypeData` 来检查会话中的类型数据，并将其发送到 `Update-TypeData` 和 `Remove-TypeData` cmdlet。

扩展类型数据将属性和方法添加到 PowerShell 中的对象。 可采用与使用对象类型中所定义的属性和方法相同的方式来使用已添加的属性和方法。 但是，在编写脚本时，请注意，已添加的属性和方法可能不会出现在每个 PowerShell 会话中。

有关文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。 有关 cmdlet 添加的动态类型数据的详细信息 `Update-TypeData` ，请参阅 `Update-TypeData` 。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例1：获取所有扩展类型数据

此示例获取当前会话中的所有扩展类型数据。

 ```powershell
Get-TypeData
```

### 示例2：按名称获取类型

此示例获取当前会话中具有包含事件的名称的所有类型。

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### 示例3：获取创建属性值的脚本块

此示例将获取用于创建 **EventLogEntry** 对象的 **EventID** 属性值的脚本块。

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### 示例4：获取为指定的对象定义属性的脚本块

此示例获取在 PowerShell 中定义 system.exception 对象的 **datetime** 属性 **的脚本** 块。

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

该命令使用 `Get-TypeData` cmdlet 来获取 **DataTime** 类型的扩展类型数据。 该命令将获取 **TypeData** 对象的 **Members** 属性。

**Members** 属性包含一个由扩展类型数据定义的属性和方法的哈希表。 Members 哈希表中的每个键均为某个属性或方法名称，每个值均为该属性或方法值的定义。

此命令获取 **Members** 中的 **DateTime** 键及其 **GetScriptBlock** 属性值。

输出显示脚本块，该脚本块创建 PowerShell 中每个 **system.web** 对象的 **datetime** 属性的值。

## 参数

### -TypeName

仅将类型数据指定为具有指定名称的类型的数组。 默认情况下， `Get-TypeData` 获取会话中的所有类型。

输入类型名称或名称模式。 即使对于 System 命名空间中的类型，也需要带有通配符的全名或名称模式。 支持通配符，参数名 **TypeName** 是可选的。 还可以通过管道将类型命名为 `Get-TypeData` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将类型命名为 `Get-TypeData` 。

## 输出

### System.Management.Automation.Runspaces.TypeData

## 说明

`Get-TypeData` 仅获取当前会话中的扩展类型数据。 它不获取位于计算机上但未添加到当前会话中的扩展类型数据，例如在模块中定义但未导入到当前会话中的扩展类型。

## 相关链接

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Update-TypeData](Update-TypeData.md)

