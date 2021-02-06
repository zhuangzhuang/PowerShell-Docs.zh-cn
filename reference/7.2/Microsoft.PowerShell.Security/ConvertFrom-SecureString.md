---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 9dcc79755854cc7b9f1928cfbc5d602632eca3cc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596832"
---
# ConvertFrom-SecureString

## 摘要
将安全字符串转换为加密的标准字符串。

## SYNTAX

### Secure（默认值）

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### AsPlainText

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### 打开

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## DESCRIPTION

**Convertfrom-csv** cmdlet 将 (**SecureString**) 的安全字符串转换为加密的标准 **字符串 (的**) 。 和安全字符串不同，加密的标准字符串可保存在文件中以供以后使用。 使用 cmdlet 可以将加密的标准字符串转换回其安全字符串格式 `ConvertTo-SecureString` 。

如果使用 **Key** 或 **SecureKey** 参数指定加密密钥，则使用高级加密标准 (AES) 加密算法。 指定的密钥必须具有 128、192 或 256 字节的长度，因为这些是 AES 加密算法支持的密钥长度。 如果未指定密钥，则使用 Windows 数据保护 API (DPAPI) 加密标准字符串表示形式。

> [!NOTE]
> 请注意，在非 Windows 系统上，每个 [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)不会加密 SecureString 的内容。

## 示例

### 示例1：创建安全字符串

```powershell
$SecureString = Read-Host -AsSecureString
```

此命令从你在命令提示符处键入的字符创建安全字符串。 输入命令后，键入要存储为安全字符串的字符串。 将显示一个星号 (`*`) ，用于表示你键入的每个字符。

### 示例2：将安全字符串转换为加密的标准字符串

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

此命令将变量中的安全字符串转换 `$SecureString` 为加密的标准字符串。 生成的加密标准字符串存储在变量中 `$StandardString` 。

### 示例3：使用192位密钥将安全字符串转换为加密的标准字符串

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

这些命令使用高级加密标准 (AES) 算法将变量中存储的安全字符串转换 `$SecureString` 为具有192位密钥的加密的标准字符串。 生成的加密标准字符串存储在变量中 `$StandardString` 。

第一个命令将密钥存储在 `$Key` 变量中。 该密钥是24个十进制数字的数组，其中每个数字都必须小于256，才能容纳在一个无符号字节内。

由于每个十进制数字代表单个字节 (8 位) ，因此， (8 x 24) ，该密钥的总大小为192位。 这是用于 AES 算法的有效的密钥长度值。

第二个命令使用变量中的密钥 `$Key` 将安全字符串转换为加密的标准字符串。

### 示例4：将安全字符串直接转换为纯文本字符串

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

设置后， `ConvertFrom-SecureString` 会将安全字符串转换为加密的纯文本字符串作为输出。

此参数已添加到 PowerShell 7.0。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key

将加密密钥指定为字节数组。

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

将加密密钥指定为安全字符串。 在将安全字符串值用作密钥之前，需将其转换为字节数组。

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

### -SecureString

指定安全字符串转换为加密的标准字符串。

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。
有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Security.SecureString

可以通过管道将 **SecureString** 对象传递给 Convertfrom-csv-SecureString。

## 输出

### System.String

ConvertFrom-SecureString 返回标准字符串对象。

## 注释

- 若要从在命令提示符处键入的字符创建安全字符串，请使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 。
- 使用 **key** 或 **SecureKey** 参数指定密钥时，密钥长度必须正确。 例如，128位的密钥可以指定为16个十进制数字的字节数组。
  同样，192位和256位的密钥分别对应于24和32十进制数字的字节数组。
- 一些字符（如图释）对应于包含它们的字符串中的几个码位。 避免使用这些字符，因为在密码中使用时，它们可能会导致问题和误解。

## 相关链接

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
