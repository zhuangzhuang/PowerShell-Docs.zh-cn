---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 831f40e9bd24cee20eeae54a41e0b022dc6300da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595831"
---
# Set-AuthenticodeSignature

## 摘要
将 [Authenticode](/windows-hardware/drivers/install/authenticode) 签名添加到 PowerShell 脚本或其他文件中。

## SYNTAX

### ByPath（默认值）

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-AuthenticodeSignature`Cmdlet 将验证码签名添加到支持主题界面包 (SIP) 的任何文件。

在 PowerShell 脚本文件中，该签名采用文本块的形式，它指示在脚本中执行的说明的结束。 如果在此 cmdlet 运行时文件中有签名，则该签名被删除。

## 示例

### 示例 1-使用本地证书存储中的证书对脚本进行签名

这些命令从 PowerShell 证书提供程序检索代码签名证书，并使用它对 PowerShell 脚本进行签名。

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

第一个命令使用 `Get-ChildItem` cmdlet 和 PowerShell 证书提供程序来获取 `Cert:\CurrentUser\My` 证书存储区中的证书。 `Cert:`驱动器是由证书提供程序公开的驱动器。 仅证书提供程序支持的 **CodeSigningCert** 参数将检索到的证书限制为具有代码签名颁发机构的证书。 该命令将结果存储在 `$cert` 变量中。

第二个命令使用 `Set-AuthenticodeSignature` cmdlet 对脚本进行签名 `PSTestInternet2.ps1` 。 它使用 **FilePath** 参数来指定脚本的名称，并使用 **certificate** 参数来指定在变量中存储证书 `$cert` 。

> [!NOTE]
> 使用 **CodeSigningCert** 参数 `Get-ChildItem` 只返回具有代码签名颁发机构并包含私钥的证书。 如果没有私钥，则不能使用证书进行签名。

### 示例 2-使用 PFX 文件中的证书对脚本进行签名

这些命令使用 `Get-PfxCertificate` cmdlet 加载代码签名证书。 然后，使用它对 PowerShell 脚本进行签名。

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

第一个命令使用 `Get-PfxCertificate` cmdlet 将 C:\Test\MySign.pfx 证书加载到 `$cert` 变量中。

第二个命令使用 `Set-AuthenticodeSignature` 对脚本进行签名。 的 **FilePath** 参数 `Set-AuthenticodeSignature` 指定要签名的脚本文件的路径， **Cert** 参数将 `$cert` 包含证书的变量传递到 `Set-AuthenticodeSignature` 。

如果证书文件受密码保护，则 PowerShell 会提示输入密码。

### 示例 3-添加包含根证书颁发机构的签名

此命令添加数字签名，它包括信任链中的根证书颁发机构，并由第三方时间戳服务器对其进行签名。

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

该命令使用 **FilePath** 参数来指定要签名的脚本，并使用 **Certificate** 参数来指定在变量中保存的证书 `$cert` 。 它使用 **IncludeChain** 参数来包括信任链中的所有签名，包括根证书颁发机构。 它还使用 **TimeStampServer** 参数将时间戳添加到签名。
这会阻止脚本在证书过期时失败。

## PARAMETERS

### -Certificate

指定将用来对脚本或文件进行签名的证书。 输入存储对象的变量，该对象表示证书或获取证书的表达式。

若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书驱动器中的 cmdlet `Cert:` 。 如果证书无效或没有 `code-signing` 权限，则该命令将失败。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定正进行签名的文件的路径。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

允许该 cmdlet 将签名追加到只读文件。 即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HashAlgorithm

指定 Windows 用来计算文件的数字签名的哈希算法。

对于 PowerShell 3.0，默认值为 SHA256，它是 Windows 默认哈希算法。 对于 PowerShell 2.0，默认值为 SHA1。 使用不同的哈希算法进行签名的文件可能无法在其他系统上识别。 支持哪些算法取决于操作系统的版本。

有关可能值的列表，请参阅 [HashAlgorithmName 结构](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeChain

确定证书信任链中的哪些证书包含在数字签名中。
默认值为 **NotRoot** 。

有效值是：

- 签名者：仅包括签名者的证书。
- NotRoot：包括证书链中的所有证书，根颁发机构除外。
- 所有：包括证书链中的所有证书。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimestampServer

使用指定的时间戳服务器将时间戳添加到签名。 以字符串的形式键入时间戳服务器的 URL。

时间戳表示将证书添加到文件的确切时间。 如果证书过期，时间戳可阻止脚本失败，因为用户和程序可以验证在签名时证书有效。

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

### -LiteralPath

指定正进行签名的文件的路径。 与 **FilePath** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

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

要添加数字签名的内容的文件或文件类型的路径。 此参数用于将文件内容作为字节数组传递的 **内容** 。

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

### -Content

文件内容作为为其添加数字签名的字节数组。 此参数必须与 **SourcePathOrExtension** 参数一起使用。 文件的内容必须采用 Unicode 格式 (UTF-16LE) 格式。

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

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含文件路径的字符串传递给 `Set-AuthenticodeSignature` 。

## 输出

### System.Management.Automation.Signature

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Get-PfxCertificate](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
