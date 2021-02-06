---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598899"
---
# New-Module

## 摘要
创建一个仅存在于内存中的新动态模块。

## SYNTAX

### ScriptBlock（默认值）

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### 名称

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

`New-Module`Cmdlet 从脚本块创建动态模块。 动态模块的成员（如函数和变量）在会话中立即可用并保持可用状态，直到关闭此会话。

类似于静态模块，默认情况下，将导出动态模块中的 cmdlet 和函数，而不导出变量和别名。 但是，可以使用 Export-ModuleMember cmdlet 和的参数 `New-Module` 来覆盖默认值。

你还可以使用的 **AsCustomObject** 参数 `New-Module` ，以自定义对象的形式返回动态模块。 将模块的成员（例如函数）实现为自定义对象的脚本方法，而不是将其导入到会话中。

动态模块只存在于内存中，而不存在于磁盘上。 类似于所有模块，动态模块的成员在专用模块作用域中运行，此作用域是全局作用域的子级。 Get-Module 无法获取动态模块，但 Get-Command 可以获取导出的成员。

若要使动态模块可供使用 `Get-Module` ，请通过管道将 `New-Module` 命令传递给 import-module，或将返回的模块对象传递给 `New-Module` `Import-Module` 。 此操作将动态模块添加到 `Get-Module` 列表中，但它不会将模块保存到磁盘或使其保持不变。

## 示例

### 示例1：创建动态模块

此示例使用名为的函数创建新的动态模块 `Hello` 。 此命令返回表示新的动态模块的模块对象。

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### 示例2：使用动态模块、Get-Module 和 Get-Command

此示例演示 cmdlet 不返回动态模块 `Get-Module` 。 Cmdlet 将返回它们导出的成员 `Get-Command` 。

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### 示例3：将变量导出到当前会话中

此示例使用 `Export-ModuleMember` cmdlet 将变量导出到当前会话中。
如果没有 `Export-ModuleMember` 命令，则只会导出函数。

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

输出显示已将变量和函数导出到会话中。

### 示例4：使动态模块可用于 Get-Module

此示例演示如何通过管道将动态模块传递给，使动态模块可供使用 `Get-Module` `Import-Module` 。

`New-Module` 创建通过管道传递给 cmdlet 的模块对象 `Import-Module` 。 的 **name** 参数将为 `New-Module` 模块分配一个友好名称。 由于 `Import-Module` 默认情况下不返回任何对象，因此没有来自此命令的输出。 `Get-Module`**GreetingModule** 已导入到当前会话中。

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

`Get-Command`Cmdlet 显示 `Hello` 动态模块导出的函数。

### 示例5：生成具有导出函数的自定义对象

此示例演示如何使用的 **AsCustomObject** 参数 `New-Module` 生成一个自定义对象，该对象具有表示导出的函数的脚本方法。

`New-Module`Cmdlet 将创建包含两个函数和的动态 `Hello` 模块 `Goodbye` 。 **AsCustomObject** 参数创建自定义对象，而不是默认生成的 **PSModuleInfo** 对象 `New-Module` 。 此自定义对象保存在 `$m` 变量中。
`$m`变量似乎没有分配值。

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

管道传递 `$m` 到 `Get-Member` cmdlet 显示自定义对象的属性和方法。 输出显示对象具有表示和函数的脚本方法 `Hello` `Goodbye` 。
最后，我们调用这些脚本方法并显示结果。

### 示例6：获取脚本块的结果

此示例使用 **ReturnResult** 参数来请求运行脚本块的结果，而不是请求模块对象。 新模块中的脚本块定义 `SayHello` 函数，然后调用函数。

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETERS

### -ArgumentList

指定参数数组，这些参数是传递到脚本块的参数值。 有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

指示此 cmdlet 返回表示动态模块的自定义对象。 将模块成员实现为自定义对象的脚本方法，但是不将它们导入到会话中。 可以在变量中保存自定义对象，并使用点表示法来调用成员。

如果模块有多个具有相同名称的成员，如函数和名为的变量，则只能从自定义对象访问一个具有每个名称的成员。

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

### -Cmdlet

指定此 cmdlet 从模块导出到当前会话中的 cmdlet 的数组。
输入以逗号分隔的 cmdlet 列表。 允许使用通配符。 默认情况下，导出模块中的所有 cmdlet。

你无法在脚本块中定义 cmdlet，但如果从二进制模块导入 cmdlet，则动态模块可以包含 cmdlet。

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

### -Function

指定此 cmdlet 从模块导出到当前会话的函数数组。
输入以逗号分隔的函数列表。 允许使用通配符。 默认情况下，导出模块中定义的所有函数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

指定新模块的名称。 还可以通过管道将模块的名称传递给 New-Module。

默认值是自动生成的名称，该名称以开头， `__DynamicModule_` 后跟一个 GUID，它指定动态模块的路径。

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

指示此 cmdlet 运行脚本块并返回脚本块结果，而不是返回模块对象。

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

### -ScriptBlock

指定动态模块的内容。 将内容括在大括号中 (`{}`) 创建脚本块。 此参数是必需的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将模块名称传递给此 cmdlet。

## 输出

### System.Management.Automation.PSModuleInfo、System.Management.Automation.PSCustomObject 或无

默认情况下，此 cmdlet 将生成 **PSModuleInfo** 对象。 如果使用 **AsCustomObject** 参数，它将生成 **PSCustomObject** 对象。 如果使用 **ReturnResult** 参数，则它会返回对动态模块中的脚本块求值所得的结果。

## 注释

还可以 `New-Module` 通过其别名来引用 `nmo` 。 有关详细信息，请参阅 [about_Aliases](About/about_Aliases.md)。

## 相关链接

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[Remove-Module](Remove-Module.md)

