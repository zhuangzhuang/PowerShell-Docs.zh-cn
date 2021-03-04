---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 9c626192deb992861c7b2fcddd06d90dd6f85ff7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685613"
---
# Get-AuthenticodeSignature

## 摘要
获取有关文件的 Authenticode 签名的信息。

## SYNTAX

### ByPath（默认值）

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## 说明

`Get-AuthenticodeSignature`Cmdlet 获取有关作为字节数组的文件或文件内容的 Authenticode 签名信息。
如果该文件同时为嵌入签名和 Windows 目录签名，则使用 Windows 目录签名。
如果文件未签名，则将检索信息，但字段为空。

## 示例

### 示例 1：获取文件的 Authenticode 签名

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

此命令将获取有关 NewScript.ps1 文件中 Authenticode 签名的信息。 它使用 **FilePath** 参数指定文件。

### 示例 2：获取多个文件的 Authenticode 签名

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

此命令获取有关命令行中列出的四个文件的 Authenticode 签名的信息。 在此示例中，省略了 FilePath 参数（可选）的名称。

### 示例 3：仅获取多个文件的有效 Authenticode 签名

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

此命令列出 `$PSHOME` 目录中具有有效 Authenticode 签名的所有文件。 `$PSHOME`自动变量包含 PowerShell 安装目录的路径。

该命令使用 `Get-ChildItem` cmdlet 来获取目录中的文件 `$PSHOME` 。 它使用 *.* 模式 来排除目录（尽管它还将排除文件名中没有句点的文件）。

该命令使用管道运算符 (`|`) 将文件发送 `$PSHOME` 到 `ForEach-Object` cmdlet，其中 `Get-AuthenticodeSignature` 为每个文件调用。

命令的结果 `Get-AuthenticodeSignature` 将发送到一个 `Where-Object` 命令，该命令仅选择状态为 "有效" 的签名对象。

### 示例4：获取指定为字节数组的文件内容的 Authenticode 签名

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

此命令获取有关文件内容的 Authenticode 签名的信息。 在此示例中，文件扩展名与文件内容一起指定。

## PARAMETERS

### -Content

文件内容作为要为其检索 Authenticode 签名的字节数组。 此参数必须与 **SourcePathOrExtension** 参数一起使用。 文件的内容必须采用 Unicode 格式 (UTF-16LE) 格式。

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FilePath

指定要检查的文件的路径。 允许使用通配符，但它们必须指向单个文件。 为此参数指定值时，无需在命令行中键入 **FilePath** 。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

指定要检查的文件的路径。 与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号告诉 PowerShell 不要将任何字符解释为转义符。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

要为其检索 Authenticode 签名的内容的文件或文件类型的路径。 此参数用于将文件内容作为字节数组传递的 **内容** 。

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将包含文件路径的字符串传递给 `Get-AuthenticodeSignature` 。

## 输出

### System.Management.Automation.Signature

`Get-AuthenticodeSignature` 为获取的每个签名返回一个签名对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

有关 PowerShell 中 Authenticode 签名的信息，请参阅 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)。

## 相关链接

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
