---
description: 证书
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certificate 提供程序
ms.openlocfilehash: 78536024e8e953a70485a7d950b187ba9a3fc405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596847"
---
# <a name="certificate-provider"></a>Certificate 提供程序

## <a name="provider-name"></a>提供程序名称

证书

## <a name="drives"></a>驱动器

`Cert:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>简短说明

在 PowerShell 中提供对 x.509 证书存储和证书的访问。

## <a name="detailed-description"></a>详细说明

PowerShell **证书** 提供程序允许你获取、添加、更改、清除和删除 PowerShell 中的证书和证书存储。

**证书** 驱动器是包含计算机上的证书存储和证书的分层命名空间。

此 **证书** 提供程序支持以下 cmdlet，本文将对此进行介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

证书驱动器公开以下类型。

- 将位置存储 (Microsoft.powershell.commands.x509storelocation) ，这是为当前用户和所有用户分组证书的高级容器。 每个系统都具有 CurrentUser 和 LocalMachine（所有用户）存储位置。

- 证书存储 (System.security.cryptography.x509certificates.x509certificate2. X509Store) ，这是保存和管理证书的物理存储。

- X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 证书，每个证书都代表计算机上的一个 x.509 证书。
  证书由其指纹标识。

## <a name="navigating-the-certificate-drive"></a>导航证书驱动器

**证书** 提供程序在 PowerShell 中将证书命名空间作为 `Cert:` 驱动器公开。 此命令使用 `Set-Location` 命令将当前位置更改为 LocalMachine 存储位置中的根证书存储。 使用反斜杠 (\\) 或正斜杠 (/) 来指示驱动器的级别 `Cert:` 。

```powershell
Set-Location Cert:
```

你还可以使用任何其他 PowerShell 驱动器中的证书提供程序。 若要从其他位置引用别名，请 `Cert:` 在路径中使用驱动器名称。

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。
> 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

## <a name="displaying-the-contents-of-the-cert-drive"></a>显示 Cert：驱动器的内容

此命令使用 `Get-ChildItem` cmdlet 来显示 CurrentUser 证书存储位置中的证书存储区。

如果不在 `Cert:` 驱动器中，请使用绝对路径。

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>在 Cert：驱动器中显示证书属性

此示例使用获取证书 `Get-Item` ，并将其存储在变量中。
该示例显示了使用 (**DnsNameList**， **EnhancedKeyUsageList**， **SendAsTrustedIssuer**) 的新证书脚本属性 `Select-Object` 。

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>查找所有代码签名证书

此命令使用 cmdlet 的 **CodeSigningCert** 和 **递归** 参数 `Get-ChildItem` 获取具有代码签名颁发机构的计算机上的所有证书。

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>查找过期的证书

此命令使用 cmdlet 的 **ExpiringInDays** 参数 `Get-ChildItem` 来获取将在接下来的30天内到期的证书。

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>查找服务器 SSL 证书

此命令使用 cmdlet 的 **SSLServerAuthentication** 参数 `Get-ChildItem` 来获取 My 和 WebHosting 存储中的所有服务器 SSL 证书。

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>在远程计算机上查找过期的证书

此命令使用 `Invoke-Command` cmdlet `Get-ChildItem` 在 Srv01 和 Srv02 计算机上运行命令。 如果 **ExpiringInDays** 参数中的值为零 (0) ，则将获取 Srv01 和 Srv02 计算机上已过期的证书。

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>合并筛选器以查找特定的一组证书

此命令获取 LocalMachine 存储位置中具有以下属性的所有证书：

- 其 DNS 名称中的 "fabrikam"
- EKU 中的 "客户端身份验证"
- `$true` **SendAsTrustedIssuer** 属性的值
- 不会在接下来的30天内过期。

**NotAfter** 属性存储证书的过期日期。

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>打开证书 MMC 管理单元

该 `Invoke-Item` cmdlet 将使用默认应用程序打开指定的路径。 对于证书，默认的应用程序是 "证书" MMC 管理单元。

此命令将打开证书 MMC 管理单元以管理指定的证书。

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>复制证书

**证书** 提供程序不支持复制证书。 尝试复制证书时，会看到此错误。

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>移动证书

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>将所有 SSL 服务器身份验证证书移到 WebHosting 存储

此命令使用 `Move-Item` cmdlet 将证书从 My 存储移到 WebHosting 存储。

`Move-Item` 不会移动证书存储，也不会将证书移到不同的存储位置，例如将证书从 LocalMachine 移动到 CurrentUser。 `Move-Item`Cmdlet 将移动证书，但不会移动私钥。

此命令使用 cmdlet 的 **SSLServerAuthentication** 参数 `Get-ChildItem` 来获取 "我的证书" 存储中的 SSL 服务器身份验证证书。

返回的证书将通过管道传递给 `Move-Item` cmdlet，这会将证书移到 WebHosting 存储区。

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>删除证书和私钥

该 `Remove-Item` cmdlet 将删除指定的证书。 `-DeleteKey`动态参数删除私钥。

### <a name="delete-a-certificate-from-the-ca-store"></a>从 CA 存储区中删除证书

此命令从 CA 证书存储中删除证书，但会使相关联的私钥保持不变。

在 `Cert:` 驱动器中， `Remove-Item` cmdlet 仅支持 **DeleteKey**、 **Path**、 **WhatIf** 和 **Confirm** 参数。 忽略所有其他参数。

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>使用 DNS 名称中的通配符删除证书

此命令删除具有包含“Fabrikam”的 DNS 名称的所有证书。 它使用 cmdlet 的 **DNSName** 参数 `Get-ChildItem` 来获取证书，并使用 cmdlet 将 `Remove-Item` 其删除。

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>从远程计算机中删除私钥

这一系列命令将启用委派，然后在远程计算机上删除该证书和相关联的私钥。 若要删除远程计算机上的私钥，你必须使用委派的凭据。

使用 `Enable-WSManCredSSP` cmdlet 在 S1 远程计算机上的客户端上启用凭据安全服务提供程序 (CredSSP) 身份验证。
CredSSP 允许使用委派的身份验证。

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

使用 `Connect-WSMan` cmdlet 将 S1 计算机连接到本地计算机上的 WinRM 服务。 此命令完成后，S1 计算机将显示在 `WSMan:` PowerShell 中的本地驱动器中。

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

现在，你可以使用 WSMan：驱动器中的 Set-Item cmdlet 启用 WinRM 服务的 CredSSP 属性。

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

使用 cmdlet 在 s1 计算机上启动远程会话 `New-PSSession` ，并指定 CredSSP 身份验证。 将会话保存在 `$s` 变量中。

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

最后，使用 `Invoke-Command` cmdlet 在 `Remove-Item` 变量中的会话中运行命令 `$s` 。 该 `Remove-Item` 命令使用 **DeleteKey** 参数删除私钥以及指定的证书。

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>删除过期的证书

此命令使用值为0的 cmdlet 的 **ExpiringInDays** 参数 `Get-ChildItem` 来获取 WebHosting 存储区中已过期的证书。

包含所返回证书的变量将通过管道传递给 `Remove-Item` cmdlet，后者将删除它们。 该命令使用 **DeleteKey** 参数来删除私钥以及证书。

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>创建证书

`New-Item`Cmdlet 不会在 **证书** 提供程序中创建新证书。 使用 [new-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 创建用于测试的证书。

## <a name="creating-certificate-stores"></a>创建证书存储

在 Cert：驱动器中， `New-Item` cmdlet 会在 LocalMachine 存储位置中创建证书存储。 它支持 **Name**、 **Path**、 **WhatIf** 和 **Confirm** 参数。 忽略所有其他参数。 该命令将返回表示新证书存储的 **system.security.cryptography.x509certificates.x509certificate2. X509Store。**

此命令在 LocalMachine 存储位置中创建名为“CustomStore”的新证书存储。

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>在远程计算机上创建新的证书存储

此命令在 Server01 计算机上的 LocalMachine 存储位置中创建名为“HostingStore”的新证书存储。

该命令使用 `Invoke-Command` cmdlet `New-Item` 在 Server01 计算机上运行命令。 该命令将返回表示新证书存储的 **system.security.cryptography.x509certificates.x509certificate2. X509Store。**

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>为 WS-Man 创建客户端证书

此命令创建 **ws-management** 客户端可以使用的 **ClientCertificate** 项。 新的 **ClientCertificate** 将在 **ClientCertificate** 目录下显示为 "ClientCertificate_1234567890"。 所有参数都是必需的。 **颁发者** 必须是颁发者证书的指纹。

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>删除证书存储

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>从远程计算机中删除证书存储

此命令使用 `Invoke-Command` cmdlet `Remove-Item` 在 S1 和 S2 计算机上运行命令。 此 `Remove-Item` 命令包含 **递归** 参数，该参数在删除存储之前删除存储中的证书。

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。 这些参数在证书提供程序的所有子目录中都有效，但仅对证书有效。

> [!NOTE]
> 对属性执行筛选的参数 `EnhancedKeyUsageList` 还会返回具有空 `EnhancedKeyUsageList` 属性值的项。
> 具有空 **EnhancedKeyUsageList** 的证书可用于所有目的。

PowerShell 7.1 中引入了以下证书提供程序参数。

- DNSName
- DocumentEncryptionCert
- EKU
- ExpiringInDays
- SSLServerAuthentication

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert <SwitchParameter>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此参数获取在其 **EnhancedKeyUsageList** 属性值中具有 "代码签名" 的证书。

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey <SwitchParameter>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

此参数删除证书时，删除相关联的私钥。

> [!IMPORTANT]
> 若要删除与远程计算机上的存储区中的用户证书关联的私钥 `Cert:\CurrentUser` ，必须使用委派的凭据。 `Invoke-Command`Cmdlet 使用 **CredSSP** 参数支持凭据委托。 使用 `Remove-Item` with 和 credential 委托之前，应考虑任何安全风险 `Invoke-Command` 。

此参数已被引入 PowerShell 7。1

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a>DnsName <DnsNameRepresentation>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此参数获取在证书的 **DNSNameList** 属性中具有指定域名或名称模式的证书。 此参数的值可以是 "Unicode" 或 "ASCII"。 Punycode 值将转换为 Unicode。 `*`允许使用通配符 () 。

此参数已被引入 PowerShell 7。1

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a>DocumentEncryptionCert <SwitchParameter>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此参数获取在其 **EnhancedKeyUsageList** 属性值中具有 "文档加密" 的证书。

### <a name="eku-systemstring"></a>EKU <System.string>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此参数获取证书的属性中具有指定文本或文本模式的证书 `EnhancedKeyUsageList` 。 `*`允许使用通配符 () 。 `EnhancedKeyUsageList`属性包含 EKU 的友好名称和 OID 字段。

此参数已被引入 PowerShell 7。1

### <a name="expiringindays-systemint32"></a>ExpiringInDays <>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此参数获取在指定天数内或之前过期的证书。 值 0（零）将获取已过期的证书。

此参数已被引入 PowerShell 7。1

### <a name="itemtype-string"></a>ItemType \<String\>

此参数允许你指定由创建的项的类型 `New-Item` 。

在 `Certificate` 驱动器中，允许使用以下值：

- Certificate 提供程序
- 证书
- 存储
- StoreLocation

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a>SSLServerAuthentication <SwitchParameter>

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

仅获取用于 SSL Web 托管的服务器证书。 此参数获取其属性值中具有 "服务器身份验证" 的证书 `EnhancedKeyUsageList` 。

此参数已被引入 PowerShell 7。1

## <a name="script-properties"></a>脚本属性

已将新的脚本属性添加到表示证书的 **x509Certificate2** 对象，以便轻松搜索和管理证书。

- `DnsNameList`：若要填充 `DnsNameList` 属性，证书提供程序将从 SubjectAlternativeName (SAN) 扩展中的 DNSName 条目复制内容。 如果 SAN 扩展为空，则使用证书的 Subject 字段中的内容填充该属性。

- `EnhancedKeyUsageList`：若要填充 `EnhancedKeyUsageList` 属性，证书提供程序将复制证书中 EnhancedKeyUsage (EKU) 字段的 OID 属性，并为其创建一个友好名称。

- `SendAsTrustedIssuer`：若要填充 `SendAsTrustedIssuer` 属性，证书提供程序将 `SendAsTrustedIssuer` 从证书复制属性。  有关详细信息，请参阅 [管理客户端身份验证的受信任颁发](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)者。

这些新功能允许你根据证书的 DNS 名称和到期日期搜索证书，并通过证书的增强型密钥使用 (EKU) 属性的值将客户端和服务器身份验证证书区分开来。

## <a name="using-the-pipeline"></a>使用管道

提供程序 cmdlet 接受管道输入。 可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。
若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。

## <a name="getting-help"></a>获取帮助

从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。

若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用的 `-Path` 参数 `Get-Help` 来指定文件系统驱动器。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>请参阅

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-PfxCertificate](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
