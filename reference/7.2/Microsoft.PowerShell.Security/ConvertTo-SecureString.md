---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 0f95f66bdd13fd57f71823f2d44a28a1323d0d15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597440"
---
# ConvertTo-SecureString

## 摘要
将纯文本或加密字符串转换为安全字符串。

## SYNTAX

### Secure（默认值）

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### PlainText

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### 打开

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-SecureString`Cmdlet 将加密的标准字符串转换为安全字符串。 它还可以将纯文本转换为安全字符串。 它与和一起 `ConvertFrom-SecureString` 使用 `Read-Host` 。 Cmdlet 创建的安全字符串可与需要类型为 **SecureString** 的参数的 cmdlet 或函数一起使用。 安全字符串可以使用 cmdlet 转换回加密的标准字符串 `ConvertFrom-SecureString` 。 这使它能够存储在文件中以供以后使用。

如果使用指定的密钥对要转换的标准字符串进行了加密 `ConvertFrom-SecureString` ，则必须将同一密钥作为 cmdlet 的 **Key** 或 **SecureKey** 参数的值提供 `ConvertTo-SecureString` 。

> [!NOTE]
> 请注意，在非 Windows 系统上，每个 [DotNet](/dotnet/api/system.security.securestring#remarks)不会加密 SecureString 的内容。

## 示例

### 示例1：将安全字符串转换为加密字符串

此示例显示了从用户输入创建安全字符串、将安全字符串转换为加密的标准字符串，然后将加密的标准字符串重新转换为安全字符串的方式。

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

第一个命令使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 创建安全字符串。 输入该命令后，你键入的任何字符都将转换为安全字符串，然后保存在变量中 `$Secure` 。

第二个命令显示变量的内容 `$Secure` 。 由于 `$Secure` 变量包含安全字符串，因此 PowerShell 仅显示 **SecureString** 类型。

第三个命令使用 `ConvertFrom-SecureString` cmdlet 将变量中的安全字符串转换为 `$Secure` 加密的标准字符串。 它将结果保存在 `$Encrypted` 变量中。

第四个命令显示变量值中的加密字符串 `$Encrypted` 。

第五个命令使用 `ConvertTo-SecureString` cmdlet 将变量中的加密的标准字符串转换 `$Encrypted` 回安全字符串。 它将结果保存在 `$Secure2` 变量中。
第六个命令显示变量的值 `$Secure2` 。 SecureString 类型指示命令已成功。

### 示例2：从文件中的加密字符串创建安全字符串

此示例显示了如何从保存在文件中的加密的标准字符串中创建安全字符串。

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

第一个命令使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 创建安全字符串。 输入该命令后，你键入的任何字符都将转换为安全字符串，然后保存在变量中 `$Secure` 。

第二个命令使用 `ConvertFrom-SecureString` cmdlet，通过使用指定的键将变量中的安全字符串转换为 `$Secure` 加密的标准字符串。 内容保存在 `$Encrypted` 变量中。

第三个命令使用管道运算符 (`|`) 将变量的值发送 `$Encrypted` 到 `Set-Content` cmdlet，这会将值保存在 Encrypted.txt 文件中。

第四个命令使用 `Get-Content` cmdlet 来获取 Encrypted.txt 文件中的加密的标准字符串。 该命令使用管道运算符将加密字符串发送到 `ConvertTo-SecureString` cmdlet，该 cmdlet 使用指定的密钥将其转换为安全字符串。
结果保存在 `$Secure2` 变量中。

### 示例3：将纯文本字符串转换为安全字符串

此命令将纯文本字符串转换为 `P@ssW0rD!` 安全字符串，并将结果存储在 `$Secure_String_Pwd` 变量中。 若要使用 **AsPlainText** 参数，还必须将 **Force** 参数包含在该命令中。

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> 应避免在脚本或命令行中使用纯文本字符串。 纯文本可以显示在事件日志和命令历史记录日志中。

## PARAMETERS

### -AsPlainText

指定要转换为安全字符串的纯文本字符串。 安全字符串 cmdlet 有助于保护机密文本。 为保护隐私，应对文本进行加密，并在使用后将其从计算机内存中删除。 如果你使用此参数来提供纯文本作为输入，则系统无法采用此方式保护该输入。 若要使用此参数，还必须指定 **Force** 参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

确认你了解使用 **AsPlainText** 参数的含义并仍要使用它。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key

指定用于将原始安全字符串转换为加密的标准字符串的加密密钥。 有效的密钥长度为16、24和32字节。

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

指定用于将原始安全字符串转换为加密的标准字符串的加密密钥。 必须采用安全字符串的格式提供密钥。 安全字符串将转换为字节数组，以用作键。 有效的安全密钥长度为8、12和16个码位。

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -String

指定要转换为安全字符串的字符串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将标准加密字符串传递给 `ConvertTo-SecureString` 。

## 输出

### System.Security.SecureString

`ConvertTo-SecureString` 返回 **SecureString** 对象。

## 注释

一些字符（如图释）对应于包含它们的字符串中的几个码位。 避免使用这些字符，因为在密码中使用时，它们可能会导致问题和误解。

## 相关链接

[ConvertFrom-SecureString](ConvertFrom-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
