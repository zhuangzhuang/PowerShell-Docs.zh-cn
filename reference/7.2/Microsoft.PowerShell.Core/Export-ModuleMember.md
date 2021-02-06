---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: fcb9af654f9e95f44e49ea984294b80752aa3453
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598258"
---
# Export-ModuleMember

## 摘要
指定要导出的模块成员。

## SYNTAX

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

**Export-ModuleMember** cmdlet 指定从脚本模块 (.psm1) 文件或从使用 New-Module cmdlet 创建的动态模块中导出的模块成员。
模块成员包括 cmdlet、函数、变量和别名。
此 cmdlet 只能用于脚本模块文件或动态模块。

如果脚本模块不包含 **export-modulemember** 命令，则会导出脚本模块中的函数和别名，但不会导出变量。
当脚本模块包含 **export-modulemember** 命令时，只会导出 **export-modulemember** 命令中指定的成员。
还可以使用 **export-modulemember** 来禁止或导出脚本模块从其他模块导入的成员。

**Export-modulemember** 命令是可选的，但这是最佳做法。
即使该命令确认了默认值，但它演示了模块作者的初衷。

## 示例

### 示例1：导出脚本模块中的函数和别名

```powershell
Export-ModuleMember -Function * -Alias *
```

此命令导出在脚本模块中定义的所有函数和别名。

### 示例 2：导出特定别名和函数

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

此命令导出在脚本模块中定义的三个别名和三个函数。

可以使用此命令格式指定模块成员的名称。

### 示例 3：不导出成员

```powershell
Export-ModuleMember
```

此命令指定不导出在脚本模块中定义的成员。

此命令阻止导出模块成员，但不隐藏模块成员。
用户可以读取和复制模块成员，或使用调用运算符 (&) 来调用未导出的模块成员。

### 示例 4：导出某一特定变量

```powershell
Export-ModuleMember -Variable increment
```

此命令只从脚本模块中导出 $increment 变量。
不导出其他成员。

如果要导出某个变量，除了导出模块中的函数外， **export-modulemember** 命令必须包含所有函数的名称和该变量的名称。

### 示例 5：多个导出命令

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

这些命令显示了如何在脚本模块 (. hbase-runner.psm1) 文件中解释多个 **export-modulemember** 命令。

这些命令创建了三个函数和一个别名，然后导出其中两个函数和该别名。

如果没有 **export-modulemember** 命令，则将导出所有三个函数和别名。
对于 **export-modulemember** 命令，只会导出新的 **测试** 和 **启动测试** 函数以及 STT 别名。

### 示例 6：导出动态模块中的成员

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

此命令显示了如何在使用 **新模块** cmdlet 创建的动态模块中使用 Export-ModuleMember。

在此示例中，使用 **export-modulemember** 导出动态模块中的 "Hi" 和 " **SayHello** " 函数。

### 示例 7：声明和导出单个命令中的函数

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

此示例包含一个名为 **Export** 的函数，该函数声明函数或创建一个变量，然后 `Export-ModuleMember` 为该函数或变量编写命令。
这样可以通过单个命令声明和导出函数或变量。

若要使用 **Export** 函数，请将其包含在脚本模块中。
若要导出某个函数，请在 **Function** 关键字之前键入 `Export`。

若要导出某个变量，请使用以下格式声明该变量并为其设置值：

`Export variable <variable-name> <value>`

该示例中的命令显示了正确的格式。
在此示例中，仅导出 **新的测试** 函数和 $Interval 变量。

## PARAMETERS

### -Alias

指定要从脚本模块文件中导出的别名。
输入别名。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Cmdlet

指定要从脚本模块文件中导出的 cmdlet。
输入 cmdlet 名称。
允许使用通配符。

不能在脚本模块文件中创建 cmdlet，但可将二进制模块中的 cmdlet 导入到脚本模块中，然后重新从该脚本模块中导出这些 cmdlet。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Function

指定要从脚本模块文件中导出的函数。
输入函数名称。
允许使用通配符。
还可以通过管道将函数名称字符串传递给 **export-modulemember**。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Variable

指定要从脚本模块文件中导出的变量。
输入变量名称（不带美元符号）。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将函数名称字符串传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

* 若要从导出的成员列表中排除某一成员，请添加一个 **export-modulemember** 命令，该命令列出所有其他成员，但省略你要排除的成员。

## 相关链接

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[Remove-Module](Remove-Module.md)

