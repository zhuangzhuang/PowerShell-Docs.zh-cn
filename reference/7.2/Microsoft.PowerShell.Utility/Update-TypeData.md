---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 1314d388bff5a46bcf335f3da7908a65233aa46e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598681"
---
# Update-TypeData

## 摘要
更新会话中的扩展类型数据。

## 语法

### FileSet（默认值）

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 说明

该 `Update-TypeData` cmdlet 将更新会话中的扩展类型数据，方法是 `Types.ps1xml` 将文件重新加载到内存中并添加新的扩展类型数据。

默认情况下，PowerShell 将在需要时加载扩展类型数据。 如果没有参数，则 `Update-TypeData` 会重新加载 `Types.ps1xml` 已在会话中加载的所有文件，包括你添加的所有类型文件。 您可以使用的参数 `Update-TypeData` 添加新的类型文件以及添加和替换扩展类型数据。

`Update-TypeData`Cmdlet 可用于预加载所有类型数据。 当你要开发类型并且想要加载这些新类型用于测试目的时，此功能尤其有用。

从 Windows PowerShell 3.0 开始，你可以使用 `Update-TypeData` 添加和替换会话中的扩展类型数据，而无需使用 `Types.ps1xml` 文件。 仅将动态（即无需文件）添加的类型数据添加到当前会话中。 若要将类型数据添加到所有会话，请将 `Update-TypeData` 命令添加到 PowerShell 配置文件。 有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

此外，从 Windows PowerShell 3.0 开始，你可以使用 `Get-TypeData` cmdlet 来获取当前会话中的扩展类型，使用 `Remove-TypeData` cmdlet 从当前会话中删除扩展类型。

在属性中发生的异常或通过将属性添加到 `Update-TypeData` 命令中时，不会报告错误。 这是为了取消显示在格式设置和输出期间在许多常见类型中发生的异常。 如果你正在获取 .NET 属性，则可以通过使用方法语法来解决禁止显示异常的情况，如以下示例中所示：

`"hello".get_Length()`

请注意，方法语法仅可用于 .NET 属性。 通过运行 cmdlet 添加的属性 `Update-TypeData` 不能使用方法语法。

有关 PowerShell 中的文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。

## 示例

### 示例1：更新扩展类型

```powershell
Update-TypeData
```

此命令从已 `Types.ps1xml` 在会话中使用的文件中更新扩展类型配置。

### 示例2：多次更新类型

此示例显示了如何在同一会话中多次更新类型文件中的类型。

第一个命令从文件更新扩展类型配置 `Types.ps1xml` ， `TypesA.types.ps1xml` 并首先处理和 `TypesB.types.ps1xml` 文件。

第二个命令显示如何重新更新 `TypesA.types.ps1xml` ，如您在文件中添加或更改了类型时可能会执行的操作。 您可以为文件重复前面的命令 `TypesA.types.ps1xml` ，也可以运行 `Update-TypeData` 不带参数的命令，因为已 `TypesA.types.ps1xml` 在当前会话的类型文件列表中。

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### 示例3：向 DateTime 对象添加脚本属性

此示例使用 `Update-TypeData` 将 "**季度** 脚本" 属性添加到当前会话中的 **system.object** 对象，如 cmdlet 返回的对象。 `Get-Date`

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

该 `Update-TypeData` 命令使用 **TypeName** 参数来指定 system.string 类型，使用 **成员** 名称参数指定新属性的名称，使用 **MemberType** 属性指定 **ScriptProperty** 类型，并使用 **Value** 参数指定用于确定年季度的脚本。

**Value** 属性的值是一个用于计算当前年度季度的脚本。 脚本块使用 `$this` 自动变量来表示对象的当前实例，并使用 In 运算符来确定每个整数数组中是否出现月份值。 有关运算符的详细信息 `-in` ，请参阅 [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)。

第二个命令将获取当前日期的新 Quarter 属性。

### 示例4：更新默认显示在列表中的类型

此示例演示如何设置默认情况下在列表中显示的类型的属性，即，当未指定任何属性时。 由于未在文件中指定类型数据 `Types.ps1xml` ，因此它仅在当前会话中有效。

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

第一个命令使用 `Update-TypeData` cmdlet 为 system.string 类型设置默认列表属性。  该命令使用 **TypeName** 参数指定类型，并使用 **DefaultDisplayPropertySet** 参数指定列表的默认属性。 所选属性包括在前面的示例中添加的新的 " **季度** 脚本" 属性。

第二个命令使用 `Get-Date` cmdlet 获取表示当前日期的 system.string 对象。 该命令使用管道运算符 (`|`) 将 **DateTime** 对象发送到 `Format-List` cmdlet。 由于该 `Format-List` 命令未指定要在列表中显示的属性，因此 PowerShell 将使用通过命令建立的默认值 `Update-TypeData` 。

### 示例5：更新管道对象的类型数据

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

此示例演示当你通过管道将对象传递给时 `Update-TypeData` ，会 `Update-TypeData` 为该对象类型添加扩展类型数据。

此方法比使用 `Get-Member` cmdlet 或 `Get-Type` 方法获取对象类型要快。 但是，如果您通过管道将对象的集合传递给 `Update-TypeData` ，它会更新第一个对象类型的类型数据，然后为该集合中的所有其他对象返回一个错误，因为已在该类型上定义了成员。

第一个命令使用 `Get-Module` cmdlet 来获取 PSScheduledJob 模块。 命令通过管道将模块对象传递给 `Update-TypeData` cmdlet，这会更新 **PSModuleInfo** 类型的类型数据以及从其派生的类型，例如， `Get-Module` 当你在命令中使用 **ListAvailable** 参数时返回的 ModuleInfoGrouping 类型。

这些 `Update-TypeData` 命令将 **SupportsUpdatableHelp** 脚本属性添加到所有导入的模块中。 **Value** 参数的值是一个脚本， `$True` 如果填充了模块的 **HelpInfoUri** 属性，则返回，否则返回 `$False` 。

第二个命令通过管道将模块对象传递 `Get-Module` 给 `Format-Table` cmdlet，后者将显示列表中所有模块的 **Name** 和 **SupportsUpdatableHelp** 属性。

## 参数

### -AppendPath

指定可选文件的路径 `.ps1xml` 。 按加载内置文件后列出指定文件的顺序来加载这些文件。 还可以通过管道将 **AppendPath** 值传递给 `Update-TypeData` 。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

指定 `Format-Wide` 在未指定其他属性时由 cmdlet 显示的类型的属性。

键入类型的标准或扩展属性的名称。 此参数的值可以是已添加到同一命令中的类型的名称。

仅当没有为文件中的类型定义宽视图时，此值才有效 `Format.ps1xml` 。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

指定类型的一个或多个属性。 `Format-List`如果未指定其他属性，则 cmdlet 将显示这些属性。

键入类型的标准或扩展属性的名称。 此参数的值可以是已添加到同一命令中的类型的名称。

仅当没有为文件中的类型定义列表视图时，此值才有效 `Format.ps1xml` 。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

指定类型的一个或多个属性。 `Group-Object` `Sort-Object` 当未指定其他属性时，和 cmdlet 将使用这些属性。

键入类型的标准或扩展属性的名称。 此参数的值可以是已添加到同一命令中的类型的名称。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示该 cmdlet 使用指定的类型数据，即使已为该类型指定了类型数据。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

指示是否继承序列化的属性集。 默认值是 `$Null`。 此参数的可接受值为：

- `$True`. 继承属性集。
- `$False`. 不继承属性集。
- `$Null`. 未定义继承。

仅当 **SerializationMethod** 参数的值为时，此参数才有效 `SpecificProperties` 。 当此参数的值为时 `$False` ， **PropertySerializationSet** 参数是必需的。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberName

指定属性或方法的名称。

将此参数与 **TypeName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberType

指定要添加或更改的成员类型。

将此参数与 **TypeName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。 此参数的可接受值为：

- AliasProperty
- CodeMethod
- CodeProperty
- Noteproperty
- ScriptMethod
- ScriptProperty

有关这些值的信息，请参阅 [PSMemberTypes 枚举](/dotnet/api/system.management.automation.psmembertypes)。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

指定可选文件的路径 `.ps1xml` 。 按加载内置文件前列出指定文件的顺序来加载这些文件。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

指定已进行序列化的属性的名称。 当 **SerializationMethod** 参数的值为 **SpecificProperties** 时，使用此参数。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

指定 **AliasProperty**、**ScriptProperty**、**CodeProperty** 或 **CodeMethod** 成员的其他值。

将此参数与 **TypeName**、 **MemberType**、 **Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。

当 **MemberType** 参数的值为时 `AliasProperty` ， **SecondValue** 参数的值必须是数据类型。 PowerShell) 会将别名属性的值转换 (为指定的类型。 例如，如果添加 **了为字符串** 属性提供备用名称的别名属性，则还可以指定 **SecondValue** 来将别名字符串值转换为整数。

当 **MemberType** 参数的值为时 `ScriptProperty` ，可以使用 **SecondValue** 参数来指定其他脚本块。 **Value** 参数的值中的脚本块将获取变量的值。 **SecondValue** 参数的值中的脚本块将设置该变量的值。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

指定将多少个级别的类型对象序列化为字符串。 默认值将 `1` 序列化对象及其属性。 值用于 `0` 序列化对象，但不序列化其属性。 值用于 `2` 序列化对象、其属性和属性值中的任何对象。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationMethod

为类型指定序列化方法。 序列化方法将确定序列化类型的哪些属性以及用于对其进行序列化的方法。 此参数的可接受值为：

- `AllPublicProperties`. 序列化类型的所有公共属性。 可以使用 **SerializationDepth** 参数确定是否序列化子属性。
- `String`. 将类型序列化为一个字符串。 可以使用 **StringSerializationSource** 指定要用作序列化结果的类型的属性。 否则，通过使用对象的 **ToString** 方法序列化该类型。
- `SpecificProperties`. 仅序列化此类型的指定属性。 使用 **PropertySerializationSet** 参数指定已进行序列化的类型的属性。
  还可以使用 **InheritPropertySerializationSet** 参数确定是否继承属性集，并使用 **SerializationDepth** 参数确定是否序列化子属性。

在 PowerShell 中，序列化方法存储在 **PSStandardMembers** 内部对象中。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

指定类型的属性的名称。 指定属性的值将用作序列化结果。 仅当 **SerializationMethod** 参数的值为 String 时，此参数才有效。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

指定此类型的对象被反序列化时将转换为哪种类型。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

指定类型适配器的类型（如 **microsoft.powershell.cim.ciminstanceadapter 等**）。 类型适配器使 PowerShell 能够获取类型的成员。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeConverter

指定可在不同类型之间转换值的类型转换器。 如果为某个类型定义一个类型转换器，则该类型转换器的实例将用于转换过程。

输入派生自 **System.ComponentModel.TypeConverter** 或 **System.Management.Automation.PSTypeConverter** 类的 **System.Type** 值。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

指定此 cmdlet 添加到会话中的类型数据的数组。 输入包含 **update-typedata** 对象的变量或获取 **update-typedata** 对象的命令（如 `Get-TypeData` 命令）。 还可以通过管道将 **update-typedata** 对象传递给 `Update-TypeData` 。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

指定要扩展的类型的名称。

对于 **System** 命名空间中的类型，请输入短名称。 否则，必须输入完整类型名称。 不支持通配符。

可以通过管道将类型命名为 `Update-TypeData` 。 将对象通过管道传递给时 `Update-TypeData` ，将 `Update-TypeData` 获取对象的类型名称，并将数据键入到对象类型。

将此参数与 **MemberName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Value

指定属性或方法的值。

如果添加 `AliasProperty` 、 `CodeProperty` 、 `ScriptProperty` 或 `CodeMethod` 成员，则可以使用 **SecondValue** 参数添加其他信息。

将此参数与 **MemberName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### System.String

可以通过管道将包含 **AppendPath**、 **TypeName** 或 **update-typedata** 参数值的字符串传递给 `Update-TypeData` 。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 说明

## 相关链接

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)

