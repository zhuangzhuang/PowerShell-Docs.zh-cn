---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 91cd2dda912d6e79177e8a961012a1604d9460ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603581"
---
# Invoke-RestMethod

## 摘要
将 HTTP 或 HTTPS 请求发送到 RESTful Web 服务。

## SYNTAX

### StandardMethod (默认值) 

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## 说明

`Invoke-RestMethod`Cmdlet 将 HTTP 和 HTTPS 请求发送到具象状态传输 (REST) web 服务返回丰富的结构化数据。

PowerShell 基于数据类型设置响应的格式。 对于 RSS 或 ATOM 源，PowerShell 返回项或条目 XML 节点。 对于 JavaScript 对象表示法 (JSON) 或 XML，PowerShell 将内容转换或反序列化为对象。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

从 PowerShell 7.0 开始， `Invoke-RestMethod` 支持由环境变量定义的代理配置。 请参阅本文的 " [备注](#notes) " 部分。

## 示例

### 示例1：获取 PowerShell RSS 源

此示例使用 `Invoke-RestMethod` cmdlet 从 PowerShell 博客 rss 源获取信息。 该命令使用 `Format-Table` cmdlet 来显示表中每个博客的 **Title** 和 **e** 属性的值。

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

### 示例2：运行 POST 请求

在此示例中，用户运行 `Invoke-RestMethod` 以在用户组织中的 intranet 网站上执行 POST 请求。

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

系统会提示输入凭据，然后将其存储在中 `$Cred` ，并在中定义要访问的 URL `$Url` 。

`$Body`变量描述搜索条件，将 CSV 指定为输出模式，并指定从两天前开始到一天结束的返回数据的时间段。 Body 变量指定适用于与之通信的特定 REST API 的参数的值 `Invoke-RestMethod` 。

`Invoke-RestMethod`使用所有变量运行命令，并为生成的 CSV 输出文件指定路径和文件名。

### 示例3：跟随关系链接

某些 REST Api 支持通过每个 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的关系链接进行分页。 你可以让 cmdlet 为你执行此操作，而不是分析标头以获取下一页的 URL。 此示例返回 PowerShell GitHub 存储库中的前两页问题。

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### 示例4：简化的多部分/表单数据提交

某些 Api 需要 `multipart/form-data` 提交来上传文件和混合内容。 此示例演示如何更新用户的配置文件。

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

配置文件窗体需要以下字段： `firstName` 、 `lastName` 、、、 `email` `avatar` `birthday` 和 `hobbies` 。 该 API 需要在字段中提供用户配置文件 pic 的映像 `avatar` 。 该 API 还将接受 `hobbies` 同一窗体中提交的多个条目。

创建 `$Form` 哈希表时，键名称将用作窗体字段名称。 默认情况下，哈希表的值将转换为字符串。 如果 `System.IO.FileInfo` 存在值，将提交文件内容。 如果存在诸如数组或列表这样的集合，则将多次提交窗体字段。

通过 `Get-Item` 对键使用 `avatar` ，将 `FileInfo` 对象设置为值。 结果是将提交的图像数据 `jdoe.png` 。

通过向键提供一个列表 `hobbies` ， `hobbies` 每个列表项的提交将会出现一次该字段。

### 示例5：传递多个标头

Api 通常要求传递的标头用于身份验证或验证。 此示例演示如何将多个标头从传递 `hash-table` 到 REST API。

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## 参数

### -AllowUnencryptedAuthentication

允许通过未加密的连接发送凭据和密码。 默认情况下，如果提供 **凭据** 或任何具有不以开头的 **Uri** 的 **身份验证** 选项，则 `https://` 会导致错误，请求将中止，以防止无意中以纯文本方式传递未加密连接的机密。 若要重写此行为，需自行承担相应的风险，请提供 **AllowUnencryptedAuthentication** 参数。

> [!WARNING]
> 使用此参数并不安全，不建议使用。 提供它只是为了与无法提供加密连接的旧系统兼容。 使用自己的风险。

此功能已添加到 PowerShell 6.0.0。

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

### -Authentication

指定要用于请求的显式身份验证类型。 默认值为“无”。
**身份验证** 不能与 **UseDefaultCredentials** 一起使用。

可用的身份验证选项：

- **无**：这是未提供 **身份验证** 时的默认选项。 不会使用显式身份验证。
- **基本**：需要 **凭据**。 凭据将用于以格式发送 RFC 7617 基本身份验证 `Authorization: Basic` 标头 `base64(user:password)` 。
- **持有** 者：需要 **标记**。 将 `Authorization: Bearer` 随提供的令牌一起发送和 RFC 6750 标头。 这是 **OAuth** 的别名
- **OAuth**：需要 **标记**。 将 `Authorization: Bearer` 使用提供的令牌发送 RFC 6750 标头。 这是 **持有** 者的别名

提供 **身份验证** 将覆盖 `Authorization` 提供给 **标头** 或包含在 **WebSession** 中的任何标头。

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

指定请求的正文。 正文是请求的内容，位于标头之后。
还可以通过管道将正文值传递给 `Invoke-RestMethod` 。

可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。

如果输入是 GET 请求，且正文是 `IDictionary` (通常是) 哈希表，则主体将添加到统一资源标识符 (URI) 作为查询参数。 对于其他请求类型（如 POST），将正文按标准的“名称=值”格式设置为请求正文的值。

如果正文为窗体，或者它是另一个调用的输出 `Invoke-WebRequest` ，则 PowerShell 会将请求内容设置为窗体字段。

**Body** 参数还可以接受 **系统 MultipartFormDataContent** 对象。 这将简化 `multipart/form-data` 请求。 为 **正文** 提供 **MultipartFormDataContent** 对象时，提供给 **ContentType**、**标头** 或 **WebSession** 参数的任何与内容相关的标头都将被对象的内容标头重写 `MultipartFormDataContent` 。 此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Certificate

指定用于安全的 Web 请求的客户端证书。 输入一个包含证书的变量，或可获取该证书的命令或表达式。

若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书 () 驱动器中的 cmdlet `Cert:` 。 如果证书无效或没有足够的权限，则该命令将失败。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定有权发送请求的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。

在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或命令 `Cert:` 。

> [!NOTE]
> 目前只有 Windows 操作系统平台支持此功能。

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

### -ContentType

指定 Web 请求的内容类型。

如果省略此参数且请求方法为 POST，则 `Invoke-RestMethod` 将内容类型设置为 `application/x-www-form-urlencoded` 。 否则，不会在调用中指定内容类型。

为 `MultipartFormDataContent` **正文** 提供对象时，将覆盖 ContentType。

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

### -Credential

指定有权发送请求的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。

**凭据** 可以单独使用，也可以与某些 **身份验证** 参数选项一起使用。 单独使用时，如果远程服务器发送身份验证质询请求，则仅向远程服务器提供凭据。 与 **身份验证** 选项一起使用时，将显式发送凭据。

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
Accept pipeline input: False
Accept wildcard characters: False
```

### -CustomMethod

指定用于 web 请求的自定义方法。 这可以与终结点所需的请求方法一起使用，而不是 **方法** 上的可用选项。 **方法** 和 **CustomMethod** 不能一起使用。

例如：

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

这会 `TEST` 向 API 发出 HTTP 请求。

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

指示该 cmdlet 将 HTTP 头中的 **KeepAlive** 值设置为 False。 默认情况下，**KeepAlive** 为 True。 **KeepAlive** 建立到服务器的持续性连接，以促进后续请求。

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

### -FollowRelLink

指示 cmdlet 应遵循关系链接。

某些 REST Api 支持通过每个 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的关系链接进行分页。 你可以让 cmdlet 为你执行此操作，而不是分析标头以获取下一页的 URL。 若要设置跟踪关系链接的次数，请使用 **MaximumFollowRelLink** 参数。

使用此开关时，cmdlet 将返回结果页的集合。 每页结果可能包含多个结果项。

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -窗体

将字典转换为 `multipart/form-data` 提交。 **窗体** 不能与 **正文** 一起使用。
如果将忽略 **ContentType** 。

字典的键将用作窗体字段名称。 默认情况下，窗体值将转换为字符串值。

如果值是 **FileInfo** 对象，则将提交二进制文件内容。
文件的名称将作为进行提交 `filename` 。 MIME 将设置为 `application/octet-stream` 。 `Get-Item` 可用于简化 **FileInfo** 对象的提供。

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

如果值是集合类型（如数组或列表），则将多次提交 for 字段。 默认情况下，列表的值将作为字符串处理。 如果值是 **FileInfo** 对象，则将提交二进制文件内容。 嵌套集合不受支持。

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

在上面的示例中，该 `tags` 字段将在窗体中提供三次，一次针对每个 `Vacation` 、 `Italy` 和 `2017` 。 `pictures`对于文件夹中的每个文件，该字段也会提交一次 `2017-Italy` 。 该文件夹中的文件的二进制内容将提交为值。

此功能已添加到 PowerShell 6.1.0。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -标头

指定 Web 请求的标头。 输入哈希表或字典。

若要设置 UserAgent 标头，请使用 **UserAgent** 参数。 不能使用此参数来指定 `User-Agent` 或 cookie 标头。

`Content-Type`当为 `MultipartFormDataContent` **正文** 提供对象时，将重写与内容相关的标头。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InFile

从文件中获取 Web 请求的内容。

请输入路径和文件名。 如果省略路径，则默认路径为当前位置。

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

### -MaximumFollowRelLink

如果使用了 **FollowRelLink** ，则指定跟踪关系链接的次数。 如果 REST api 由于请求过多而受到限制，则可能需要较小的值。 默认值是 `[Int32]::MaxValue`。 值 0 (零) 阻止以下关系链接。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

指定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。 默认值为 5。 值为 0（零）将阻止所有重定向。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRetryCount

指定在收到400与599（含）或304之间的失败代码时，PowerShell 重试连接的次数。 另请参阅 **RetryIntervalSec** 参数以指定重试次数。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -方法

指定用于 Web 请求的方法。 此参数的可接受值为：

- 默认
- 删除
- 获取
- Head
- 合并
- 选项
- 修补程序
- 邮递
- Put
- 跟踪

**CustomMethod** 参数可用于上面未列出的请求方法。

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoProxy

指示该 cmdlet 将不使用代理来访问目标。

如果需要跳过在 Internet Explorer 中配置的代理，或在环境中指定的代理，则使用此开关。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutFile

将响应正文保存在指定的输出文件中。 请输入路径和文件名。 如果省略路径，则默认路径为当前位置。 该名称被视为文本路径。 包含方括号 () 的名称 `[]` 必须用单引号括起来 (`'`) 。

默认情况下，将 `Invoke-RestMethod` 结果返回到管道。 若要将这些结果发送到文件和管道，请使用 **Passthru** 参数。

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

### -PassThru

除了将结果写入文件外，还将返回结果。 仅当命令中还使用了 **OutFile** 参数时，此参数才有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreserveAuthorizationOnRedirect

指示 cmdlet 应在重定向中保留 `Authorization` 标头（如果存在）。

默认情况下，该 cmdlet 会 `Authorization` 在重定向前去除标头。 如果指定此参数，则会在需要将标头发送到重定向位置的情况下禁用此逻辑。

此功能已添加到 PowerShell 6.0.0。

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

### -Proxy

为请求使用代理服务器，而不是直接连接到 internet 资源。 输入网络代理服务器 (URI) 的统一资源标识符。

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。 默认为当前用户。

键入用户名（如 **User01** 或 **Domain01\User01**）， **User@Domain.Com** 或输入一个 `PSCredential` 对象，例如由 cmdlet 生成的对象 `Get-Credential` 。

仅当命令中还使用了 **代理** 参数时，此参数才有效。 不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

指示该 cmdlet 使用当前用户的凭据来访问 **代理** 参数指定的代理服务器。

仅当命令中还使用了 **代理** 参数时，此参数才有效。 不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResponseHeadersVariable

创建响应标头字典，并将其保存在指定变量的值中。 字典的键将包含 web 服务器返回的响应标头的字段名称，并且值将是各自的字段值。

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Resume

尽力尝试恢复下载部分文件。 **Resume** 参数需要 **OutFile** 参数。

**Resume** 仅对本地文件和远程文件的大小进行操作，并且不执行本地文件和远程文件相同的其他验证。

如果本地文件的大小小于远程文件大小，则该 cmdlet 将尝试继续下载文件，并将剩余字节追加到文件末尾。

如果本地文件大小与远程文件大小相同，则不会执行任何操作，并且该 cmdlet 会假设已完成下载。

如果本地文件大小大于远程文件大小，则本地文件将被覆盖，整个远程文件将被完全下载。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

如果远程服务器不支持下载恢复，则本地文件将被覆盖，整个远程文件将被完全重新下载。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

如果本地文件不存在，则将创建本地文件并完全下载整个远程文件。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

此功能已添加到 PowerShell 6.1.0。

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

### -RetryIntervalSec

指定在收到400与599（含）或304之间的失败代码时，连接的重试间隔。 另请参阅 **MaximumRetryCount** 参数以指定重试次数。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionVariable

指定此 cmdlet 为其创建 web 请求会话的变量，并将其保存在值中。
输入一个不带美元符号 () 符号的变量名称 `$` 。

指定会话变量时，将 `Invoke-RestMethod` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。 命令完成后可以立即在会话中使用该变量。

与远程会话不同，web 请求会话不是持续性连接。 它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。 可用于共享 Web 请求之间的状态和数据。

若要在后续的 Web 请求中使用 Web 请求会话，请在 **WebSession** 参数的值中指定会话变量。 PowerShell 在建立新连接时使用 web 请求会话对象中的数据。 若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential**。 参数值优先于 Web 请求会话中的值。

不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCertificateCheck

跳过证书验证检查，其中包括所有验证，如过期、吊销、受信任的根证书颁发机构等。

> [!WARNING]
> 使用此参数并不安全，不建议使用。 此开关仅用于用于测试目的的已知主机使用自签名证书。 使用自己的风险。

此功能已添加到 PowerShell 6.0.0。

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

### -SkipHeaderValidation

指示 cmdlet 应将标头添加到无验证的请求。

此开关适用于需要不符合标准的标头值的站点。
如果指定此开关，则将禁用验证以允许取消选中值。 指定时，将添加所有标头，而不进行验证。

这将禁止验证传递到 **ContentType**、 **标头** 和 **UserAgent** 参数的值。

此功能已添加到 PowerShell 6.0.0。

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

### -SkipHttpErrorCheck

此参数会导致 cmdlet 忽略 HTTP 错误状态并继续处理响应。
错误响应将写入管道，就像它们成功一样。

此参数是在 PowerShell 7 中引入的。

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

### -SslProtocol

设置允许用于 web 请求的 SSL/TLS 协议。 默认情况下，允许系统支持的 SSL/TLS 协议。 **SslProtocol** 允许出于符合性目的限制特定协议。

**SslProtocol** 使用 `WebSslProtocol` 标志 Enum。 可以使用标志表示法来提供多个协议，也可以将多个 `WebSslProtocol` 选项与结合使用 `-bor` ，但是不支持在所有平台上提供多个协议。

> [!NOTE]
> 在非 Windows 平台上，可能无法提供 `Tls` 或 `Tls12` 作为选项。 的支持 `Tls13` 在所有操作系统上都不可用，将需要根据每个操作系统进行验证。

此功能已添加到 powershell 6.0.0 中，并且 `Tls13` 已在 powershell 7.1 中添加了对的支持。

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12, Tls13

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StatusCodeVariable

此参数指定一个变量，该变量分配有状态代码的整数值。 参数可在与 **SkipHttpErrorCheck** 参数一起使用时识别成功消息或失败消息。

输入参数的变量名称作为字符串（例如） `-StatusCodeVariable "scv"` 。

此参数是在 PowerShell 7 中引入的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

指定在超时之前请求可以挂起多长时间。输入一个值（以秒为单位）。 默认值 0 指定无限超时。

域名系统 (DNS) 查询可能需要长达15秒钟的时间来返回或超时。如果你的请求包含需要解析的主机名，并将 **TimeoutSec** 设置为大于零的值，但不超过15秒，则在引发 WebException 之前可能需要15秒或更长时间，并且你的请求会超时。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token

要包含在请求中的 OAuth 或持有者令牌。 某些 **身份验证** 选项需要 **标记**。 不能单独使用。

**令牌** 采用 `SecureString` 包含标记的。 若要提供令牌，请手动使用以下内容：

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

此参数是在 PowerShell 6.0 中引入的。

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

### -TransferEncoding

指定传输编码 HTTP 响应头的值。 此参数的可接受值为：

- 块
- 压缩
- Deflate
- GZip
- 标识

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uri

指定将 web 请求发送到的 internet 资源 (URI) 的统一资源标识符。 此参数支持 HTTP、HTTPS、FTP 和 FILE 值。

此参数是必需的。  (**Uri**) 的参数名称是可选的。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseBasicParsing

此参数已弃用。 从 PowerShell 6.0.0 开始，所有 Web 请求仅使用基本分析。 提供此参数只是为了实现向后兼容性，并且对此参数的任何使用都不会影响 cmdlet 的操作。

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

### -UseDefaultCredentials

指示该 cmdlet 使用当前用户的凭据来发送 web 请求。 这不能用于 **身份验证** 或 **凭据** ，并且可能在所有平台上都不受支持。

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

### -UserAgent

指定 Web 请求的用户代理字符串。

默认的用户代理类似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每个操作系统和平台稍有不同。

若要使用大多数 internet 浏览器使用的标准用户代理字符串测试网站，请使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 类的属性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。

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

### -WebSession

指定一个 Web 请求会话。 输入变量名称，包括美元符号 (`$`) 。

若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential**。 参数值优先于 Web 请求会话中的值。 为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，也会重写与内容相关的标头（例如）。

与远程会话不同，web 请求会话不是持续性连接。 它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。 可用于共享 Web 请求之间的状态和数据。

若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号的变量名称 `Invoke-RestMethod` 。 `Invoke-RestMethod` 创建会话并将其保存在变量中。 在后续命令中，将该变量用作 **WebSession** 参数的值。

不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
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

### System.Object

你可以通过管道将 web 请求的正文传递给 `Invoke-RestMethod` 。

## 输出

### System.object、System.string System.Xml.Xml文档

此 cmdlet 的输出取决于检索内容的格式。

### PSObject

如果请求返回 JSON 字符串，则 `Invoke-RestMethod` 返回表示字符串的 **PSObject** 。

## 注释

某些功能可能无法在所有平台上使用。

由于 .NET Core 3.1 中发生了更改，因此 PowerShell 7.0 和更高版本使用 [DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 属性来确定代理配置。

此属性的值不同于平台的规则：

- **对于 Windows**：从环境变量读取代理配置，或者从用户的代理设置中读取代理配置（如果未定义）。
- **对于 macOS**：从环境变量读取代理配置，或从系统的代理设置中读取代理配置。
- **对于 Linux**：从环境变量读取代理配置，或者，如果未定义，此属性将初始化绕过所有地址的非配置实例。

用于 `DefaultProxy` 在 Windows 和基于 Unix 的平台上进行初始化的环境变量包括：

- ` HTTP_PROXY`：用于 HTTP 请求的代理服务器的主机名或 IP 地址。
- `HTTPS_PROXY`：用于 HTTPS 请求的代理服务器的主机名或 IP 地址。
- `ALL_PROXY`：在 HTTP 和 HTTPS 请求上使用的代理服务器的主机名或 IP 地址（ `HTTP_PROXY` 如果 `HTTPS_PROXY` 未定义）或 IP 地址。
- `NO_PROXY`：应从代理中排除的主机名的逗号分隔列表。

## 相关链接

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
