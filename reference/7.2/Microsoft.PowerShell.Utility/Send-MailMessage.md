---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 0a68c665e8a0b504cfef416134374c5598ba55a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595602"
---
# Send-MailMessage

## 摘要
发送电子邮件。

## SYNTAX

### 全部

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## DESCRIPTION

`Send-MailMessage`Cmdlet 可从 PowerShell 内部发送电子邮件。

必须 (SMTP) 服务器指定简单邮件传输协议，否则命令将 `Send-MailMessage` 失败。 使用 **SmtpServer** 参数或将变量设置 `$PSEmailServer` 为有效的 SMTP 服务器。
分配给的值 `$PSEmailServer` 是 PowerShell 的默认 SMTP 设置。 有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

> [!WARNING]
> `Send-MailMessage`Cmdlet 已过时。 此 cmdlet 不保证与 SMTP 服务器的安全连接。 虽然 PowerShell 中没有即时替换，但建议你不要使用 `Send-MailMessage` 。 有关详细信息，请参阅 [平台兼容性说明 DE0005](https://aka.ms/SendMailMessage)。

## 示例

### 示例1：向其他人发送电子邮件

此示例将一封电子邮件发送给其他人。

需要使用 **From**、 **To** 和 **Subject** 参数 `Send-MailMessage` 。 此示例使用 `$PSEmailServer` SMTP 服务器的默认变量，因此不需要 **SmtpServer** 参数。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。 **To** 参数指定消息的接收方。 **Subject** 参数使用文本字符串 **测试邮件** 作为消息，因为不包括可选的 **Body** 参数。

### 示例2：发送附件

此示例发送一封电子邮件，其中包含附件。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。 **To** 参数指定邮件的收件人。 **Subject** 参数描述消息的内容。 **Body** 参数是消息的内容。

**附件** 参数指定附加到电子邮件的当前目录中的文件。 **Priority** 参数将消息设置为 **高** 优先级。 **-DeliveryNotificationOption** 参数指定了两个值： **OnSuccess** 和 **OnFailure**。 发件人将收到电子邮件通知，以确认消息传递的成功或失败。
**SmtpServer** 参数将 SMTP 服务器设置为 **smtp.fabrikam.com**。

### 示例3：向邮件列表发送电子邮件

此示例向邮件列表发送电子邮件。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。 **To** 参数指定邮件的收件人。 **Cc** 参数将消息的副本发送到指定的收件人。 **Bcc** 参数发送邮件的直接副本。 直接副本是隐藏在其他收件人的电子邮件地址。 **Subject** 参数是消息，因为不包括可选的 **Body** 参数。

**Credential** 参数指定用于发送消息的域管理员凭据。 **UseSsl** 参数指定安全套接字层 (SSL) 创建安全连接。

## PARAMETERS

### -Attachments

指定要附加到电子邮件的文件的路径和文件名。 可以使用此参数或通过管道将路径和文件名传递给 `Send-MailMessage` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Bcc

指定接收邮件副本但未列为邮件收件人的电子邮件地址。 输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Body

指定电子邮件的内容。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -BodyAsHtml

指定 **Body** 参数的值包含 HTML。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Cc

指定电子邮件的抄送 (CC) 发送到的电子邮件地址。 输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 默认为当前用户。

键入用户名，如 **User01** 或 **Domain01\User01**。 或者输入 **PSCredential** 对象，例如 cmdlet 中的一个 `Get-Credential` 。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DeliveryNotificationOption

指定电子邮件的送达通知选项。 你可以指定多个值。
None 为默认值。 此参数的别名为 **DNO**。

送达通知将发送到 **From** 参数中的地址。

此参数可接受的值如下所示：

- `None`：无通知。
- `OnSuccess`：通知传送是否成功。
- `OnFailure`：通知传送是否失败。
- `Delay`：通知传送是否已延迟。
- `Never`：从不通知。

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

指定目标文件的编码类型。 默认值是 `utf8NoBOM`。

此参数可接受的值如下所示：

- `ascii`：使用 ASCII (7 位) 字符集的编码。
- `bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。
- `bigendianutf32`：使用大字节序字节顺序编码为32格式。
- `oem`：使用 MS-DOS 和控制台程序的默认编码。
- `unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。
- `utf7`：以 UTF-7 格式进行编码。
- `utf8`：以 UTF-8 格式进行编码。
- `utf8BOM`：以 UTF-8 格式编码 (BOM) 
- `utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) 
- `utf32`：以32格式编码。

从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。 有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -From

**From** 参数是必需的。 此参数指定发件人的电子邮件地址。 输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定 SMTP 服务器上的备用端口。 默认值为 25，这是默认的 SMTP 端口。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Priority

指定电子邮件的优先级。 默认值为 Normal。 此参数可接受的值为 Normal、High 和 Low。

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ReplyTo

指定其他电子邮件地址，而不是 "发件人" 地址) 使用来回复此邮件 (。
输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SmtpServer

指定发送电子邮件的 SMTP 服务器的名称。

默认值为 `$PSEmailServer` 首选项变量的值。 如果未设置首选项变量，并且未使用此参数，则该 `Send-MailMessage` 命令将失败。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Subject

**Subject** 参数不是必需的。 此参数指定电子邮件的主题。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -To

**To** 参数是必需的。 此参数指定收件人的电子邮件地址。 如果有多个收件人，请用逗号分隔其地址 (`,`) 。 输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

安全套接字层 (SSL) 协议用于建立到远程计算机的安全连接以发送邮件。 默认情况下，不使用 SSL。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

你可以通过管道将附件的路径和文件名传递给 `Send-MailMessage` 。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

