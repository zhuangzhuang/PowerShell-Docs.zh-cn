---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596412"
---
# Get-FormatData

## 摘要
获取当前会话中的格式设置数据。

## SYNTAX

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## DESCRIPTION

`Get-FormatData`Cmdlet 将获取当前会话中的格式设置数据。

会话中的格式设置数据包括格式设置文件中的格式设置数据， `Format.ps1xml` 例如目录中的数据 `$PSHOME` 、导入到会话中的模块的格式数据，以及使用 cmdlet 导入到会话中的命令的格式设置数据的格式 `Import-PSSession` 。

可以使用此 cmdlet 来检查格式设置数据。 然后，可以使用 `Export-FormatData` cmdlet 序列化对象，将它们转换为 XML，然后将它们保存在 `Format.ps1xml` 文件中。

有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 示例

### 示例1：获取所有格式设置数据

此示例获取会话中的所有格式设置数据。

```powershell
Get-FormatData
```

### 示例2：按类型名称获取格式设置数据

此示例获取名称以开头的格式设置数据项 `System.Management.Automation.Cmd` 。

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### 示例3：检查格式设置数据对象

此命令演示如何获取格式设置数据对象并检查其属性。

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### 示例4：获取格式设置数据并将其导出

此示例演示如何使用 `Get-FormatData` 和 `Export-FormatData` 导出模块添加的格式设置数据。

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

前四个命令使用 `Get-FormatData` 、 `Import-Module` 和 `Compare-Object` Cmdlet 来标识 **BitsTransfer** 模块添加到会话中的格式类型。

第五个命令使用 `Get-FormatData` cmdlet 来获取 **BitsTransfer** 模块添加的格式类型。 它使用管道运算符 (`|`) 将格式类型对象发送到 `Export-FormatData` cmdlet，后者将该对象转换回 XML 并将其保存到指定文件中 `format.ps1xml` 。

最后一个命令显示文件内容的摘录 `format.ps1xml` 。

### 示例5：基于指定的 PowerShell 版本获取格式设置数据

此示例演示如何使用 `Get-FormatData` 来获取指定的 **TypeName** 和 PowerShell 版本的格式数据。

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETERS

### -PowerShellVersion

指定此 cmdlet 为格式化数据获取的 PowerShell 版本。 输入用句点分隔的两位数字。

此参数是在 PowerShell 5.1 中添加的，用于在远程计算机运行较早版本的 PowerShell 时提高兼容性。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定此 cmdlet 为格式化数据获取的类型名称。
输入类型名称。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.ExtendedTypeDefinition

## 注释

## 相关链接

[Export-FormatData](Export-FormatData.md)

[Update-FormatData](Update-FormatData.md)
