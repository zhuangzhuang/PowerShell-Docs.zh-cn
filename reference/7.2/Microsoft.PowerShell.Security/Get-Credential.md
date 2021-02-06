---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 5630c4d09a2806eb117d005466d4925c1740d3a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595610"
---
# Get-Credential

## 摘要
获取基于用户名和密码的凭据对象。

## SYNTAX

### CredentialSet（默认值）

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### MessageSet

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Credential`Cmdlet 将为指定的用户名和密码创建凭据对象。 你可以在安全操作中使用凭据对象。

该 `Get-Credential` cmdlet 会提示用户输入密码或用户名和密码。 您可以使用 **Message** 参数在命令行提示符下指定自定义消息。

## 示例

### 示例 1

```powershell
$c = Get-Credential
```

此命令将获取凭据对象，并将其保存在 `$c` 变量中。

当你输入命令时，系统将提示你输入用户名和密码。 输入所需的信息时，该 cmdlet 将创建一个表示用户凭据的 **PSCredential** 对象，并将其保存在 `$c` 变量中。

你可以将对象用作请求用户身份验证的 cmdlet（例如，具有 **Credential** 参数的 cmdlet）的输入。 但是，某些随 PowerShell 一起安装的提供程序不支持 **Credential** 参数。

### 示例 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

这些命令使用 cmdlet 返回的凭据对象对 `Get-Credential` 远程计算机上的用户进行身份验证，以便它们可以使用 Windows Management Instrumentation (WMI) 来管理计算机。

第一个命令将获取凭据对象，并将其保存在 `$c` 变量中。 第二个命令使用命令中的凭据对象 `Get-CimInstance` 。 此命令将获取 Server01 计算机上有关磁盘驱动器的信息。

### 示例 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

此命令显示如何将命令包含 `Get-Credential` 在命令中  `Get-CimInstance` 。

此命令使用 `Get-CimInstance` cmdlet 来获取有关 Server01 计算机上的 BIOS 的信息。 它使用 **credential** 参数对 user、Domain01\User01 和 `Get-Credential` command 作为 **Credential** 参数的值进行身份验证。

### 示例 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

此示例将创建一个包含用户名（不带域名）的凭据。

第一个命令获取用户名为 User01 的凭据，并将其存储在 `$c` 变量中。
第二个命令将显示生成的凭据对象的 **Username** 属性值。

### 示例 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

此命令使用 **PromptForCredential** 方法提示用户输入其用户名和密码。 该命令将生成的凭据保存在 `$Credential` 变量中。

**PromptForCredential** 方法是使用 cmdlet 的替代方法 `Get-Credential` 。 当使用 **PromptForCredential** 时，可以指定在提示中显示的标题、消息和用户名。

有关详细信息，请参阅 SDK 中的 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 文档。

### 示例 6

此示例演示如何创建一个与不提示用户就返回的对象完全相同的凭据对象 `Get-Credential` 。 此方法要求输入纯文本密码，这可能会违反某些企业内的安全标准。

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

第一个命令将用户帐户名称保存在 `$User` 参数中。 该值必须具有“Domain\User”或“ComputerName\User”格式。

第二个命令使用 `ConvertTo-SecureString` cmdlet 从纯文本密码创建一个安全字符串。 该命令使用 **AsPlainText** 参数来指示该字符串为纯文本，并使用 **Force** 参数来确认你了解使用纯文本的风险。

第三个命令使用 `New-Object` cmdlet 从和变量中的值创建 **PSCredential** 对象 `$User` `$PWord` 。

### 示例 7

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

此命令使用 cmdlet 的 **Message** 和 **UserName** 参数 `Get-Credential` 。 此命令格式旨在用于共享的脚本和函数。 在此示例中，消息将告知用户为何需要凭据，并使他们能够确信此请求是合法的。

### 示例 8

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

此命令将从 Server01 远程计算机获取凭据。 该命令使用 `Invoke-Command` cmdlet `Get-Credential` 在远程计算机上运行命令。 输出显示 `Get-Credential` 在身份验证提示中包含的远程安全消息。

## PARAMETERS

### -Credential

指定凭据的用户名，例如 **User01** 或 **Domain01\User01**。 参数名称 `-Credential` 是可选的。

提交该命令并指定用户名时，系统将提示你输入密码。 如果省略此参数，系统会提示输入用户名和密码。

从 PowerShell 3.0 开始，如果输入的用户名没有域，则不再在 `Get-Credential` 名称之前插入反斜杠。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

指定将在身份验证提示中显示的消息。 此参数旨在用于函数或脚本。 你可以使用该消息向用户说明你为什么要请求凭据以及将如何使用它们。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

设置控制台中身份验证提示的标题行的文本。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

指定用户名。 身份验证提示要求输入该用户名对应的密码。 默认情况下，用户名为空并且身份验证提示将请求输入用户名和密码。

此参数是在 PowerShell 3.0 中引入的。

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.PSCredential

`Get-Credential` 返回凭据对象。

## 注释

你可以使用 `Get-Credential` 在请求用户身份验证的 cmdlet （例如，具有 **Credential** 参数的 Cmdlet）中创建的 PSCredential 对象。

与 PowerShell 一起安装的所有提供程序都不支持 **Credential** 参数。
从 PowerShell 3.0 开始，在 select cmdlet （如和 cmdlet）上受 `Get-Content` 支持 `New-PSDrive` 。

## 相关链接

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
