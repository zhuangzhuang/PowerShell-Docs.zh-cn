---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 58261830ca65da295aeb85cda22d0a78762e2502
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603614"
---
# Set-StrictMode

## 摘要
建立并强制执行表达式、脚本和脚本块中的编码规则。

## SYNTAX

### 版本 (默认值) 

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### 关

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## DESCRIPTION

`Set-StrictMode`Cmdlet 将为当前作用域和所有子作用域配置严格模式，并将其打开或关闭。 当 strict 模式处于开启状态时，如果表达式、脚本或脚本块的内容违反了基本的最佳实践编码规则，PowerShell 将生成终止错误。

使用 **Version** 参数确定强制执行哪些编码规则。

`Set-PSDebug -Strict` cmdlet 将为全局范围启用严格模式。 `Set-StrictMode` 仅影响当前作用域及其子作用域。 因此，你可以在脚本或函数中使用它来重写从全局作用域继承的设置。

当 `Set-StrictMode` 为 off 时，PowerShell 具有以下行为：

- 假定未初始化的变量的值为 0 (零) 或 `$Null` ，具体取决于类型
- 对不存在的属性的引用返回 `$Null`
- 不正确的函数语法的结果因错误条件而异
- 尝试使用数组中的无效索引检索值返回 `$Null`

## 示例

### 示例1：将严格模式启用为版本1。0

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

如果将 strict 模式设置为版本1.0，则将尝试引用未初始化的变量失败。

### 示例2：将严格模式启用为版本2。0

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

此命令打开严格模式并将其设置为版本2.0。 因此，如果使用用于函数调用的方法语法（使用括号和逗号）或引用未初始化的变量或不存在的属性，则 PowerShell 将返回错误。

示例输出显示2.0 版严格模式的效果。

如果不使用版本 2.0 严格模式，则将值“(3,4)”解释为未向其中添加任何值的单个数组对象。 使用2.0 版严格模式，会正确地将其解释为用于提交两个值的错误语法。

如果没有版本2.0，则对字符串的不存在的 **Month** 属性的引用仅返回 `$Null` 。 通过使用版本2.0，该版本被正确解释为引用错误。

### 示例3：将严格模式启用为版本3。0

当 strict 模式设置为 **Off** 时，无效或超出界限索引结果将返回 null 值。

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

将 strict 模式设置为版本3或更高版本时，无效或超出界限索引会导致错误。

## PARAMETERS

### -Off

指示此 cmdlet 为当前作用域和所有子作用域关闭严格模式。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

指定在严格模式下导致错误的条件。 此参数接受任何有效的 PowerShell 版本号。 大于3的任何数字均视为 **最新** 值。

此参数的有效值为：

- 1.0
  - 禁止对未初始化的变量的引用，不包括字符串中的未初始化变量。
- 2.0
  - 禁止引用未初始化的变量。 这包括字符串中的未初始化变量。
  - 禁止引用对象的不存在的属性。
  - 禁止使用语法调用方法的函数调用。
- 3.0
  - 禁止引用未初始化的变量。 这包括字符串中的未初始化变量。
  - 禁止引用对象的不存在的属性。
  - 禁止使用语法调用方法的函数调用。
  - 禁止范围外或无法解析的数组索引。
- 最新
  - 选择可用的最新版本。 最新版本最严格。 使用此值以确保脚本使用最严格的可用版本，即使在将新版本添加到 PowerShell 时也是如此。

> [!CAUTION]
> 使用脚本中的 **最新****版本**。 **最** 新的含义在 PowerShell 的新版本中可能会发生变化。 因此，在较新版本的 PowerShell 中运行时，为使用的较旧版本的 PowerShell 编写的脚本 `Set-StrictMode -Version Latest` 将受到更严格的规则的限制。

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

`Set-StrictMode` 仅在设置它的范围及其子范围内有效。 有关 PowerShell 中的作用域的详细信息，请参阅 [about_Scopes](about/about_Scopes.md)。

## 相关链接

[Set-PSDebug](Set-PSDebug.md)
