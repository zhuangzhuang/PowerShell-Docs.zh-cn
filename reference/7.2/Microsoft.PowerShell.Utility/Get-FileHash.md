---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599064"
---
# Get-FileHash

## 摘要
通过使用指定的哈希算法，计算文件的哈希值。

## SYNTAX

### Path（默认值）

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### StreamParameterSet

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## DESCRIPTION

`Get-FileHash`Cmdlet 通过使用指定的哈希算法来计算文件的哈希值。
哈希值是对应文件内容的唯一值。 哈希将唯一值分配到文件的内容，而不是通过其文件名、扩展名或其他指定标识文件的内容。 可以更改文件名和扩展名，而无需更改文件的内容，而且无需更改哈希值。 同样，可以更改文件的内容，而无需更改名称或扩展名。 但是，即使更改文件内容中的单个字符也会更改该文件的哈希值。

哈希值的用途是提供加密型安全的方式，以验证尚未更改文件的内容。 尽管一些哈希算法（包括 MD5 和 SHA1）不再被认为是安全的，但安全哈希算法的目标是使它无法更改文件的内容，无论是意外发生，还是恶意或未经授权的尝试--并维护相同的哈希值。 你还可以使用哈希值来确定两个不同的文件是否具有完全相同的内容。 如果两个文件的哈希值相同，则文件的内容也相同。

默认情况下，该 `Get-FileHash` cmdlet 使用 SHA256 算法，尽管可以使用目标操作系统支持的任何哈希算法。

## 示例

### 示例1：计算文件的哈希值

此示例使用 `Get-FileHash` cmdlet 来计算文件的哈希值 `/etc/apt/sources.list` 。 使用的哈希算法是默认值 **SHA256**。 将输出通过管道传输到 `Format-List` cmdlet，以将输出的格式设置为列表。

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### 示例2：计算 ISO 文件的哈希值

此示例使用 `Get-FileHash` cmdlet 和 **SHA384** 算法来计算管理员已从 INTERNET 下载的 ISO 文件的哈希值。 将输出通过管道传输到 `Format-List` cmdlet，以将输出的格式设置为列表。

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### 示例3：计算流的哈希值

在此示例中，我们将使用 **系统 .net. WebClient** 从 [Powershell 版本页](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)下载包。 发布页面还记录每个包文件的 SHA256 哈希。 我们可以将发布的哈希值与我们用计算的哈希值进行比较 `Get-FileHash` 。

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### 示例4：计算字符串的哈希值

PowerShell 不提供 cmdlet 来计算字符串的哈希。 但是，您可以将字符串写入流，并使用的 **InputStream** 参数 `Get-FileHash` 获取哈希值。

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETERS

### -算法

指定用于计算指定文件或流的内容的哈希值的加密哈希函数。 加密哈希函数的属性可以查找具有相同哈希值的两个不同文件。 哈希函数通常与数字签名一起使用并用来保持数据的完整性。 此参数的可接受值为：

- SHA1
- SHA256
- SHA384
- SHA512
- MD5

如果未指定任何值，或省略了参数，则默认值为 SHA256。

出于安全原因，MD5 和 SHA1（不再认为是安全的）仅应该用于简单的更改验证，而且不应该用于生成要求保护免受攻击或篡改的文件的哈希值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputStream

指定输入流。

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定到文件的路径。 与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径包括转义符，则请将其括在单引号中。 单引号指示 PowerShell 不要将字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

将一个或多个文件的路径指定为一个数组。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将字符串传递给 `Get-FileHash` 包含一个或多个文件的路径的 cmdlet。

## 输出

### Get-filehash。

`Get-FileHash` 返回一个对象，该对象表示指定文件的路径、计算所得的哈希的值以及用于计算哈希值的算法。

## 注释

## 相关链接

[Format-List](Format-List.md)

