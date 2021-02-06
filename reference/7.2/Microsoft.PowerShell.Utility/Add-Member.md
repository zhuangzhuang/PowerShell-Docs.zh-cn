---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 4e9e5ec6d188bec0b4032151fb92e6995d8efbb8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595811"
---
# Add-Member

## 摘要
将自定义属性和方法添加到 PowerShell 对象的实例。

## SYNTAX

### TypeNameSet (默认值) 

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### NotePropertyMultiMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### 集

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Add-Member`Cmdlet 允许你向 PowerShell 对象的实例 (属性和方法) 添加成员。 例如，可以添加包含对象说明的 NoteProperty 成员或运行脚本的 **ScriptMethod** 成员，以更改对象。

若要使用 `Add-Member` ，请将对象传递给 `Add-Member` ，或使用 **InputObject** 参数来指定对象。

**MemberType** 参数指示要添加的成员的类型。 **Name** 参数将名称分配给新成员，**值** 参数设置成员的值。

你添加的属性和方法只会添加到你指定的对象的特定实例中。 `Add-Member` 不会更改对象类型。 若要创建新的对象类型，请使用 `Add-Type` cmdlet。

你还可以使用 `Export-Clixml` cmdlet 在文件中保存对象的实例，包括其他成员。 然后，可以使用 `Import-Clixml` cmdlet 从导出文件中存储的信息重新创建对象的实例。

从 Windows PowerShell 3.0 开始， `Add-Member` 具有新功能，使你可以更轻松地向对象添加注释属性。
可以使用 **NotePropertyName** 和 **NotePropertyValue** 参数定义附注属性，或使用 **NotePropertyMembers** 参数，该参数采用包含附注属性名称和值的哈希表。

此外，从 Windows PowerShell 3.0 开始，将很少需要使用用于生成输出对象的 **PassThru** 参数。 `Add-Member` 现在将新成员直接添加到更多类型的输入对象。 有关详细信息，请参阅 **PassThru** 参数说明。

## 示例

### 示例1：向 PSObject 添加注释属性

下面的示例将值为 "Done" 的 **状态** 注释属性添加到表示该文件的 **FileInfo** 对象 `Test.txt` 。

第一个命令使用 `Get-ChildItem` cmdlet 来获取表示该文件的 **FileInfo** 对象 `Test.txt` 。 它将其保存在 `$a` 变量中。

第二个命令将 note 属性添加到中的对象 `$a` 。

第三个命令使用点表示法来获取中对象的 **Status** 属性的值 `$a` 。 如输出所示，值为 "Done"。

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### 示例2：向 PSObject 添加 alias 属性

下面的示例将一个 **Size** alias 属性添加到表示该文件的对象 `Test.txt` 。 新属性是 **Length** 属性的别名。

第一个命令使用 `Get-ChildItem` cmdlet 来获取 `Test.txt` **FileInfo** 对象。

第二个命令添加 **Size** alias 属性。
第三个命令使用点表示法来获取新的 **Size** 属性的值。

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### 示例3：向字符串添加 StringUse 注释属性

此示例将 **StringUse** note 属性添加到字符串。
由于 `Add-Member` 无法将类型添加到 **字符串** 输入对象，因此可以指定 **PassThru** 参数来生成输出对象。 示例中的最后一个命令将显示新属性。

此示例使用 **NotePropertyMembers** 参数。 **NotePropertyMembers** 参数的值是一个哈希表。 键为便笺属性名称 **StringUse**，值为 "注释" 属性值 " **显示**"。

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### 示例4：将脚本方法添加到 FileInfo 对象

此示例将 **SizeInMB** 脚本方法添加到 **FileInfo** 对象，该对象将文件大小计算为最接近的兆字节。 第二个命令创建一个 **ScriptBlock** ，该 ScriptBlock 使用类型中的 **循环** 静态方法将 `[math]` 文件大小舍入到第二个小数位。

**Value** 参数还使用 `$This` 自动变量，它表示当前的对象。 `$This`变量仅在定义新属性和方法的脚本块中有效。

最后一个命令使用点表示法对变量中的对象调用新的 **SizeInMB** 脚本方法 `$A` 。

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### 示例5：将对象的所有属性复制到另一个

此函数将一个对象的所有属性复制到另一个对象中。

`foreach`循环使用 `Get-Member` cmdlet **从** 对象获取的每个属性。 循环内的命令 `foreach` 在每个属性上以序列的顺序执行。

`Add-Member`命令将 **从** 对象的属性作为 **NoteProperty** 添加到对象 。 使用 **value** 参数复制值。 它使用 **Force** 参数添加具有相同成员名称的成员。

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### 示例6：创建自定义对象

此示例将创建一个 **资产** 自定义对象。

`New-Object`Cmdlet 将创建 **PSObject**。 该示例将 **PSObject** 保存在 `$Asset` 变量中。

第二个命令使用 `[ordered]` 类型加速器创建名称和值的有序字典。 该命令将结果保存在 `$D` 变量中。

第三个命令使用 cmdlet 的 **NotePropertyMembers** 参数 `Add-Member` 将变量中的字典添加 `$D` 到 **PSObject**。
**TypeName** 属性将新名称、**资产** 分配给 **PSObject**。

最后一个命令通过管道将新的 **资产** 对象传递给 `Get-Member` cmdlet。 该输出显示该对象具有类型名称 " **资产** " 和在 "排序字典" 中定义的附注属性。

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETERS

### -Force

指示此 cmdlet 添加新成员，即使该对象具有同名的自定义成员。
不能使用 **Force** 参数来替换类型的标准成员。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要向其添加新成员的对象。
输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

指定要添加的成员的类型。
此参数是必需的。
此参数的可接受值为：

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

有关这些值的信息，请参阅 PowerShell SDK 中的 [PSMemberTypes 枚举](/dotnet/api/system.management.automation.psmembertypes) 。

并非所有对象都具有每种类型的成员。
如果指定了对象不具有的成员类型，则 PowerShell 将返回错误。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定此 cmdlet 添加的成员的名称。

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyMembers

指定附注属性名称和值的哈希表或有序字典。
键入哈希表或字典，其中的键为附注属性名称，值为附注属性值。

有关 PowerShell 中的哈希表和有序字典的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyName

指定便笺属性名称。

将此参数与 **NotePropertyValue** 参数一起使用。
此参数可选。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyValue

指定 note 属性值。

将此参数与 **NotePropertyName** 参数一起使用。
此参数可选。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回一个代表你所处理的项目的对象。
默认情况下，此 cmdlet 将不产生任何输出。

对于大多数对象，会 `Add-Member` 将新成员添加到输入对象。
但是，当输入对象是一个字符串时， `Add-Member` 不能将该成员添加到 input 对象。
对于这些对象，请使用 **PassThru** 参数来创建输出对象。

在 Windows PowerShell 2.0 中， `Add-Member` 只将成员添加到了对象的 **PSObject** 包装，而不是添加到对象。
使用 **PassThru** 参数为具有 **PSObject** 包装器的任何对象创建输出对象。

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

### -SecondValue

指定有关 **AliasProperty**、**ScriptProperty**、**CodeProperty** 或 **CodeMethod** 成员的可选附加信息。

如果在添加 **AliasProperty** 时使用此参数，则此参数必须为数据类型。
到指定数据类型的转换将添加到 **AliasProperty** 的值中。

例如，如果添加了为字符串属性提供备用名称的 **AliasProperty** ，则还可以指定 **SecondValue** 参数，以指示在使用相应的 **AliasProperty** 进行访问时，应将该字符串属性的值转换为 **整数。**

添加 **ScriptProperty** 成员时，可以使用 **SecondValue** 参数来指定其他 **ScriptBlock** 。 在 **Value** 参数中指定的第一个 **ScriptBlock** 用于获取变量的值。 在 **SecondValue** 参数中指定的第二个 **ScriptBlock** 用于设置变量的值。

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定已添加成员的初始值。
如果添加了 **AliasProperty**、 **CodeProperty**、 **ScriptProperty** 或 **CodeMethod** 成员，则可以使用 **SecondValue** 参数提供可选的附加信息。

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定类型的名称。

如果类型是 **System** 命名空间中的类或具有类型加速器的类型，则可以输入类型的短名称。 否则，必须输入完整类型名称。
仅当 **InputObject** 为 **PSObject** 时，此参数才有效。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象类型传递给此 cmdlet。

## 输出

### None 或 system.string

当使用 **PassThru** 参数时，此 cmdlet 将返回新扩展的对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

只能向 **PSObject** 对象添加成员。 若要确定某个对象是否为 **PSObject** 对象，请使用 `-is` 运算符。

例如，若要测试变量中存储的对象 `$obj` ，请键入 `$obj -is [PSObject]` 。

**MemberType**、 **Name**、 **Value** 和 **SecondValue** 参数的名称是可选的。
如果省略参数名称，则未命名参数值必须按以下顺序出现： " **MemberType**"、" **Name**"、" **Value**" 和 " **SecondValue**"。

如果包括参数名称，则参数能够以任何顺序出现。

可以 `$this` 在定义新属性和方法的值的脚本块中使用自动变量。
`$this`变量引用要向其中添加属性和方法的对象的实例。 有关变量的详细信息 `$this` ，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

## 相关链接

[Export-Clixml](Export-Clixml.md)

[Get-Member](Get-Member.md)

[Import-Clixml](Import-Clixml.md)

[New-Object](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

