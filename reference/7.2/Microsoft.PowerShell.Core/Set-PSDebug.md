---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595820"
---
# Set-PSDebug

## 摘要
启用和禁用脚本调试功能、设置跟踪级别和切换严格模式。

## SYNTAX

### on

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### 关闭

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-PSDebug` cmdlet 将启用和禁用脚本调试功能、设置跟踪级别和切换严格模式。 默认情况下，PowerShell 调试功能处于关闭状态。

如果 **Trace** 参数的值为，则 `1` 会在运行时跟踪脚本的每一行。 当参数的值为时 `2` ，还将跟踪变量赋值、函数调用和脚本调用。 如果指定了 **Step** 参数，将在每个脚本行运行之前提示您。

## 示例

### 示例1：设置跟踪级别

此示例将跟踪级别设置为 `2` ，然后运行一个显示数字1、2和
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### 示例2：打开单步执行

此示例将启用 "单步执行"，然后运行显示数字1、2和3的脚本。

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### 示例3：使用严格模式

此示例将 PowerShell 置于严格模式下，并尝试访问不具有赋值的变量。

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### 示例4：关闭调试功能

此示例关闭所有调试功能，然后运行一个显示数字1、2和3的脚本。

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## PARAMETERS

### -Off

禁用所有脚本调试功能。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Step

启用脚本步进。 在每行运行之前，PowerShell 会提示你停止、继续或输入新的解释器级别来检查脚本的状态。

指定 **Step** 参数会自动将跟踪级别设置为 `1` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

指定在脚本中引用变量之前，必须先为其赋值。 如果在分配值之前引用变量，则 PowerShell 将返回异常错误。 这等效于 `Set-StrictMode -Version 1`。 有关详细信息，请参阅 [set-strictmode](Set-StrictMode.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trace

为脚本中的每一行指定跟踪级别。 每行在运行时都会被跟踪。

此参数可接受的值如下所示：

- 0：关闭脚本跟踪。
- 1：跟踪运行的脚本行。
- 2：跟踪脚本行、变量赋值、函数调用和脚本。

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入用于此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何输出。

## 注释

## 相关链接

[about_Debuggers](./About/about_Debuggers.md)

[Debug-Process](../Microsoft.PowerShell.Management/Debug-Process.md)

[Set-PSBreakpoint](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[Set-StrictMode](Set-StrictMode.md)

[Write-Debug](../Microsoft.PowerShell.Utility/Write-Debug.md)

