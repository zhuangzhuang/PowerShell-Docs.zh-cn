---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 5563413400abd28ce376265970631ad1206ca518
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685263"
---
# Read-Host

## 摘要
从控制台读取一行输入。

## SYNTAX

### AsString（默认值）

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### AsSecureString

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## 说明

`Read-Host`Cmdlet 从控制台读取一行输入。 可使用它来提示用户输入数据。 因为可以将输入保存为安全字符串，所以可以使用此 cmdlet 来提示用户输入安全数据（如密码）以及共享的数据。

> [!NOTE]
> `Read-Host` 的长度限制为1022个字符，它可以接受用户的输入。

## 示例

### 示例1：将控制台输入保存到变量

此示例显示字符串 "请输入你的年龄：" 作为提示。 输入值并按下 Enter 键时，该值将存储在 `$Age` 变量中。

```powershell
$Age = Read-Host "Please enter your age"
```

### 示例2：将控制台输入另存为安全字符串

此示例显示字符串 "Enter a Password：" 作为提示。 输入值时，将在 `*` 控制台上显示星号 () 以替代输入。 按下 Enter 键时，该值将作为 **SecureString** 对象存储在 `$pwd_secure_string` 变量中。

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### 示例3：掩码输入和纯文本字符串

此示例显示字符串 "Enter a Password：" 作为提示。 输入值时，将在 `*` 控制台上显示星号 () 以替代输入。 按下 Enter 键时，该值将作为纯文本 **字符串** 对象存储在 `$pwd_string` 变量中。

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## PARAMETERS

### -AsSecureString

指示该 cmdlet 显示星号 (`*`) 用户键入作为输入的字符。 使用此参数时，该 cmdlet 的输出 `Read-Host` 是 **SecureString** 对象， (**SecureString**) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaskInput

指示该 cmdlet 显示星号 (`*`) 用户键入作为输入的字符。 当你使用此参数时，该 cmdlet 的输出 `Read-Host` 是一个 **字符串** 对象。
这样，你就可以安全地提示输入以纯文本形式返回的密码，而不是 **SecureString**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prompt

指定提示的文本。 键入一个字符串。 如果该字符串包含空格，请将其括在引号中。 PowerShell 将向你输入的文本追加一个冒号 (`:`) 。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### None

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.String 或 System.Security.SecureString

如果使用 **AsSecureString** 参数，则 `Read-Host` 将返回 **SecureString**。 否则，它将返回一个字符串。

## 注释

## 相关链接

[Clear-Host](../microsoft.powershell.core/clear-host.md)

[Get-Host](Get-Host.md)

[Write-Host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
