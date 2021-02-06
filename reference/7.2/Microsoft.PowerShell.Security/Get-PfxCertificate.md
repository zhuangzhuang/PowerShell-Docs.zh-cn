---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597866"
---
# Get-PfxCertificate

## 摘要
获取计算机上的 PFX 证书文件的相关信息。

## SYNTAX

### ByPath（默认值）

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-PfxCertificate`Cmdlet 可获取表示每个指定的 PFX 证书文件的对象。
PFX 文件包括证书和私钥。

## 示例

### 示例1：获取 PFX 证书

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

此命令获取有关系统上的 Test .pfx 证书文件的信息。

### 示例2：从远程计算机获取 PFX 证书

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

此命令从 Server01 远程计算机获取 PFX 证书文件。 它使用 `Invoke-Command` 来远程运行 `Get-PfxCertificate` 命令。

如果 PFX 证书文件不受密码保护，则的 **Authentication** 参数的值 `Invoke-Command` 必须是 CredSSP。

## PARAMETERS

### -FilePath

指定受保护文件的 PFX 文件的完整路径。 如果指定此参数的值，则不需要在命令行键入 `-FilePath`。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

受保护文件的 PFX 文件的完整路径。 与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

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

### -NoPromptForPassword

禁止提示输入密码。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Password

指定访问证书文件所需的密码 `.pfx` 。

此参数是在 PowerShell 6.1 中引入的。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
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

可以通过管道将包含文件路径的字符串传递给 `Get-PfxCertificate` 。

## 输出

### System.Security.Cryptography.X509Certificates.X509Certificate2

`Get-PfxCertificate` 为获取的每个证书返回一个对象。

## 注释

使用 `Invoke-Command` cmdlet `Get-PfxCertificate` 远程运行命令时，如果 PFX 证书文件不受密码保护，则的 **Authentication** 参数的值 `Invoke-Command` 必须是 CredSSP。

## 相关链接

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

