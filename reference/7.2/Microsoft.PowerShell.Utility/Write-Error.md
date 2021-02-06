---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597667"
---
# Write-Error

## 摘要
将对象写入错误流。

## SYNTAX

### NoException（默认值）

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## DESCRIPTION

`Write-Error`Cmdlet 声明非终止错误。 默认情况下，将错误随输出一起在错误流中发送到主机程序来显示。

若要编写非终止错误，请输入错误消息字符串、**ErrorRecord** 对象，或 **Exception** 对象。 使用的其他参数 `Write-Error` 填充错误记录。

非终止错误将错误写入错误流，但它们不会停止命令处理。
如果在输入项的集合中的一个项上声明非终止错误，则该命令会继续处理集合中的其他项。

若要声明终止错误，请使用 `Throw` 关键字。
有关详细信息，请参阅 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)。

## 示例

### 示例1：为 RegistryKey 对象写入错误

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

当 `Get-ChildItem` cmdlet 返回 `Microsoft.Win32.RegistryKey` 对象（例如 `HKLM:` `HKCU:` PowerShell 注册表提供程序的或驱动器中的对象）时，此命令声明一个非终止错误。

### 示例2：将错误消息写入控制台

```powershell
Write-Error "Access denied."
```

此命令声明一个非终止错误，并写入“拒绝访问”错误。 此命令使用 **Message** 参数来指定消息，但省略可选的 **Message** 参数名称。

### 示例3：将错误写入控制台并指定类别

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

此命令声明一个非终止错误，并指定错误类别。

### 示例4：使用 Exception 对象编写错误

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

此命令使用 **Exception** 对象来声明一个非终止错误。

第一个命令使用哈希表来创建 **System.Exception** 对象。 它将异常对象保存在 `$E` 变量中。 可以使用哈希表来创建具有空构造函数的类型的任何对象。

第二个命令使用 `Write-Error` cmdlet 声明非终止错误。 **Exception** 参数的值是变量中的 **异常** 对象 `$E` 。

## PARAMETERS

### -Category

指定的错误类别。 默认值为 **NotSpecified**。 此参数的可接受值为：

- NotSpecified
- OpenError
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- NotImplemented
- NotInstalled
- ObjectNotFound
- OperationStopped
- OperationTimeout
- SyntaxError
- ParserError
- PermissionDenied
- ResourceBusy
- ResourceExists
- ResourceUnavailable
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

有关错误类别的信息，请参阅 [ErrorCategory 枚举](https://go.microsoft.com/fwlink/?LinkId=143600)。

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

指定导致错误的操作。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

指定活动导致错误的方式或原因。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

指定当发生错误时被处理的对象的名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

指定当发生错误时被处理的对象的类型。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

指定 ID 字符串以标识错误。 字符串应该是唯一的错误。

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

指定一个表示错误的错误记录对象。 使用对象的属性来描述错误。

若要创建错误记录对象，请使用 `New-Object` cmdlet 或从自动变量中的数组获取错误记录对象 `$Error` 。

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exception

指定一个表示错误的异常对象。 使用对象的属性来描述错误。

若要创建异常对象，请使用哈希表或使用 `New-Object` cmdlet。

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

指定错误的消息文本。 如果文本包含空格或特殊字符，则将其括在引号中。 还可以通过管道将消息字符串传递给 `Write-Error` 。

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

指定用户在解决或阻止错误时应采取的操作。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetObject

指定当发生错误时被处理的对象。 输入对象、包含对象的变量或获取对象的命令。

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
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

### System.String

可以通过管道将包含错误消息的字符串传递给 `Write-Error` 。

## 输出

### 错误对象

`Write-Error` 仅写入错误流。 它不返回任何对象。

## 注释

`Write-Error` 不会更改自动变量的值 `$?` ，因此它不会指示终止错误情况。 若要通知终止错误，请使用 [$PSCmdlet ( # B1 ](/dotnet/api/system.management.automation.cmdlet.writeerror) 方法。

## 相关链接

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
