---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 0925bef2e7b0f5ad46f6dc1aabf96e0de604c08a
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "99603413"
---
# Invoke-WebRequest

## 摘要
从 internet 上的网页中获取内容。

## SYNTAX

### StandardMethod (默认值) 

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-WebRequest`Cmdlet 将 HTTP 和 HTTPS 请求发送到网页或 web 服务。 它分析响应并返回链接、图像和其他重要 HTML 元素的集合。

此 cmdlet 是在 PowerShell 3.0 中引入的。

从 PowerShell 7.0 开始， `Invoke-WebRequest` 支持由环境变量定义的代理配置。 请参阅本文的 " [备注](#notes) " 部分。

## 示例

### 示例1：发送 web 请求

此示例使用 `Invoke-WebRequest` cmdlet 向 Bing.com 站点发送 web 请求。

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

第一个命令发出请求，并将响应保存在 `$Response` 变量中。

第二个命令获取 **Name** 属性所喜欢的任何 **InputField** `"* Value"` 。 筛选后的结果将通过管道传递到 `Select-Object` ，以选择 **名称** 和 **值** 属性。

### 示例2：使用有状态 web 服务

此示例演示如何将 `Invoke-WebRequest` cmdlet 与有状态 web 服务一起使用。

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

发送登录请求的第一次调用 `Invoke-WebRequest` 。 命令为 **-SessionVariable** 参数的值指定值 "Session"，并将结果保存在 `$LoginResponse` 变量中。 当该命令完成时， `$LoginResponse` 变量将包含 `BasicHtmlWebResponseObject` ，并且该 `$Session` 变量包含一个 `WebRequestSession` 对象。 这会将用户记录到站点中。

对的调用 `$Session` 本身显示 `WebRequestSession` 变量中的对象。

第二次调用会 `Invoke-WebRequest` 提取用户的配置文件，要求用户登录到站点。 变量中存储的会话数据 `$Session` 用于向在登录时创建的站点提供会话 cookie。 结果保存在 `$ProfileResponse` 变量中。

对的调用 `$ProfileResponse` 本身显示 `BasicHtmlWebResponseObject` 变量中的。

### 示例3：获取网页中的链接

此示例将获取网页中的链接。 它使用 `Invoke-WebRequest` cmdlet 来获取网页内容。 然后，它使用返回的的 Links `BasicHtmlWebResponseObject` 属性 `Invoke-WebRequest` 和每个链接的 **Href** 属性。

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### 示例4：使用请求页中定义的编码将响应内容写入文件。

此示例使用 `Invoke-WebRequest` cmdlet 检索 PowerShell 文档页的网页内容。

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

第一个命令检索页面，并将响应对象保存在 `$Response` 变量中。

第二个命令创建用于将 `StreamWriter` 响应内容写入文件的。 响应对象的 " **编码** " 属性用于设置文件的编码。

最后几个命令将 **Content** 属性写入文件，然后释放 `StreamWriter` 。

请注意，如果 web 请求未返回文本内容，则 **编码** 属性为 null。

### 示例5：提交多部分/窗体数据文件

此示例使用 `Invoke-WebRequest` cmdlet 将文件上传为 `multipart/form-data` 提交。 文件 `c:\document.txt` 将作为的窗体字段进行提交 `document` `Content-Type` `text/plain` 。

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### 示例6：简化的多部分/表单数据提交

某些 Api 需要 `multipart/form-data` 提交来上传文件和混合内容。 此示例演示如何更新用户配置文件。

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
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

配置文件窗体需要以下字段： `firstName` 、 `lastName` 、、、 `email` `avatar` `birthday` 和 `hobbies` 。 该 API 需要在字段中提供用户配置文件 pic 的映像 `avatar` 。 该 API 还接受 `hobbies` 同一窗体中提交的多个条目。

创建 `$Form` 哈希表时，键名称将用作窗体字段名称。 默认情况下，哈希表的值将转换为字符串。 如果存在 **FileInfo** 值，则提交文件内容。 如果存在数组或列表这样的集合，则将多次提交窗体字段。

通过 `Get-Item` 对键使用 `avatar` ，将 `FileInfo` 对象设置为值。 结果就是提交的图像数据 `jdoe.png` 。

通过向键提供一个列表 `hobbies` ， `hobbies` 每个列表项的提交一次中都有该字段。

### 示例7：从 Invoke-WebRequest 中捕获非成功消息

如果 `Invoke-WebRequest` 遇到非成功 HTTP 消息 (404、500等 ) ，它将不返回任何输出，并引发终止错误。 若要捕获错误并查看 **StatusCode** ，可以在块中包含执行 `try/catch` 。

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost"
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

终止错误由 `catch` 块捕获，后者从 **异常** 对象中检索 **StatusCode** 。

## PARAMETERS

### -AllowUnencryptedAuthentication

允许通过未加密的连接发送凭据和密码。 默认情况下，如果提供 **凭据** 或任何具有不以开头的 **Uri** 的 **身份验证** 选项，将 `https://` 会导致错误，请求会中止，以防止无意中以纯文本方式在未加密的连接上传递机密。 若要重写此行为，需自行承担相应的风险，请提供 **AllowUnencryptedAuthentication** 参数。

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

- **无**：这是未提供 **身份验证** 时的默认选项;不使用显式身份验证。
- **基本**：需要 **凭据**。 凭据以的格式在 RFC 7617 基本身份验证标头中发送 `base64(user:password)` 。
- **持有** 者：需要 **标记**。 `Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。 这是 **OAuth** 的别名
- **OAuth**：需要 **标记**。 `Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。 这是 **持有** 者的别名

提供 **身份验证** `Authorization` 将覆盖提供给 **标头** 或包含在 **WebSession** 中的任何标头。

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
还可以通过管道将正文值传递给 `Invoke-WebRequest` 。

可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。

如果输入是 GET 请求且正文是 `IDictionary` (通常是) 哈希表，则会将正文作为查询参数添加到 URI 中。 对于其他请求类型 (如 POST) ，主体将设置为标准格式的请求正文的值 `name=value` 。

**Body** 参数还可以接受一个 `System.Net.Http.MultipartFormDataContent` 对象。 这便于 `multipart/form-data` 请求。 为 **正文** 提供 **MultipartFormDataContent** 对象时，提供给 **ContentType**、**标头** 或 **WebSession** 参数的任何相关标题的任何内容都将被 **MultipartFormDataContent** 对象的内容标头重写。 此功能已添加到 PowerShell 6.0.0。

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

指定用于安全的 web 请求的客户端证书。 输入一个包含证书的变量，或可获取该证书的命令或表达式。

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

在基于客户端证书的身份验证中使用证书。 它们只能映射到本地用户帐户;它们不适用于域帐户。

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

如果省略此参数且请求方法为 POST，则 `Invoke-WebRequest` 将内容类型设置为 `application/x-www-form-urlencoded` 。 否则，不会在调用中指定内容类型。

为 **正文** 提供 **MultipartFormDataContent** 对象时，会重写 **ContentType** 。

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

**凭据** 可以单独使用，也可以与某些 **身份验证** 参数选项一起使用。 当远程服务器发送身份验证质询请求时，它仅向远程服务器提供凭据。 与 **身份验证** 选项一起使用时，会显式发送凭据。

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

指定用于 web 请求的自定义方法。 如果终结点所需的请求方法不可用于 **方法**，则可以使用此方法。 **方法** 和 **CustomMethod** 不能一起使用。

此示例 `TEST` 向 API 发出 HTTP 请求：

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

此功能已添加到 PowerShell 6.0.0。

```yaml
Type: System.String
Parameter Sets: CustomMethod, CustomMethodNoProxy
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

指示该 cmdlet 将 HTTP 头中的 **KeepAlive** 值设置为 **False**。 默认情况下， **KeepAlive** 为 **True**。 **KeepAlive** 建立到服务器的持续性连接，以促进后续请求。

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

### -窗体

将字典转换为 `multipart/form-data` 提交。 **窗体** 不能与 **正文** 一起使用。
如果使用 **ContentType** ，则会将其忽略。

字典的键用作窗体字段名称。 默认情况下，窗体值将转换为字符串值。

如果值是 **FileInfo** 对象，则会提交二进制文件内容。 文件的名称将作为 **filename** 属性提交。 MIME 类型设置为 `application/octet-stream` 。 `Get-Item` 可用于简化 **FileInfo** 对象的提供。

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

如果值是集合类型（如数组或列表），则将多次提交 for 字段。
默认情况下，列表的值被视为字符串。 如果值是 **FileInfo** 对象，则会提交二进制文件内容。 嵌套集合不受支持。

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

在上面的示例中， `tags` 字段在窗体中提供三次，一次用于 `Vacation` 、 `Italy` 和 `2017` 。 `pictures`对于文件夹中的每个文件，该字段也会提交一次 `2017-Italy` 。 将该文件夹中的文件的二进制内容提交为值。

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

若要设置 UserAgent 标头，请使用 **UserAgent** 参数。 不能使用此参数指定 **用户代理** 或 cookie 标头。

为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，会重写与内容相关的标头（例如）。

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

从文件中获取 Web 请求的内容。 请输入路径和文件名。 如果省略路径，则默认路径为当前位置。

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

### -MaximumRedirection

指定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。 默认值为 5。 值为 0（零）将阻止所有重定向。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
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

指示 cmdlet 不应使用代理来访问目标。 如果需要绕过环境中配置的代理，请使用此开关。 此功能已添加到 PowerShell 6.0.0。

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

指定此 cmdlet 为其保存响应正文的输出文件。 请输入路径和文件名。
如果省略路径，则默认路径为当前位置。 该名称被视为文本路径。
包含方括号 () 的名称 `[]` 必须用单引号括起来 (`'`) 。

默认情况下，将 `Invoke-WebRequest` 结果返回到管道。 若要将这些结果发送到文件和管道，请使用 **Passthru** 参数。

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

指示除了将结果写入文件外，该 cmdlet 还会返回结果。 仅当命令中还使用了 **OutFile** 参数时，此参数才有效。

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

为请求指定代理服务器，而不是直接连接到 internet 资源。
输入网络代理服务器的 URI。

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
Default value: Current user
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

### -Resume

尽力尝试恢复下载部分文件。 **Resume** 需要 **OutFile**。

**Resume** 仅对本地文件和远程文件的大小进行操作，并且不执行本地文件和远程文件相同的其他验证。

如果本地文件的大小小于远程文件大小，则该 cmdlet 将尝试继续下载文件，并将剩余字节追加到文件末尾。

如果本地文件大小与远程文件大小相同，则不会执行任何操作，并且 cmdlet 会假设下载已完成。

如果本地文件大小大于远程文件大小，则会覆盖本地文件，并重新下载整个远程文件。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

如果远程服务器不支持下载恢复，则会覆盖本地文件，并重新下载整个远程文件。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

如果本地文件不存在，则将创建本地文件并下载整个远程文件。 此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。

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

指定会话变量时，将 `Invoke-WebRequest` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。 命令完成后可以立即在会话中使用该变量。

与远程会话不同，Web 请求会话不是持续性连接。 它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。 可用于共享 Web 请求之间的状态和数据。

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

跳过证书验证检查。 这包括所有验证，如过期、吊销、受信任的根证书颁发机构等。

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

此开关将对传递给 **ContentType**、 **标头** 和 **UserAgent** 参数的值禁用验证。

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

**SslProtocol** 使用 **WebSslProtocol** 标志枚举。 可以使用标志表示法来提供多个协议，或将多个 **WebSslProtocol** 选项与 **bor** 结合使用，但不支持在所有平台上提供多个协议。

> [!NOTE]
> 在非 Windows 平台上，可能无法提供 `Tls` 或 `Tls12` 作为选项。 的支持 `Tls13` 在所有操作系统上都不可用，将需要根据每个操作系统进行验证。

此功能已添加到 powershell 6.0.0 中，并且 `Tls13` 已在 powershell 7.1 中添加了对的支持。

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

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
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token

要包含在请求中的 OAuth 或持有者令牌。 某些 **身份验证** 选项需要 **标记**。 不能单独使用。

**令牌** 采用 `SecureString` 包含标记的。 若要手动提供令牌，请使用以下内容：

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

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

指定将 web 请求发送到的 internet 资源 (URI) 的统一资源标识符。 输入 URI。 此参数仅支持 HTTP 或 HTTPS。

此参数是必需的。 参数名称 **Uri** 是可选的。

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

例如，以下命令使用 Internet Explorer 的用户代理字符串：

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号的变量名称 `Invoke-WebRequest` 。 `Invoke-WebRequest` 创建会话并将其保存在变量中。 在后续命令中，将该变量用作 **WebSession** 参数的值。

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

你可以通过管道将 web 请求的正文传递给 `Invoke-WebRequest` 。

## 输出

### BasicHtmlWebResponseObject。

## 注释

从 PowerShell 6.0.0 开始 `Invoke-WebRequest` 仅支持基本分析。

有关详细信息，请参阅 [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)。

由于 .NET Core 3.1 中发生了更改，因此 PowerShell 7.0 和更高版本使用 [DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 属性来确定代理配置。

此属性的值由您的平台确定：

- **对于 Windows**：从环境变量读取代理配置。 如果未定义这些变量，则将从用户的代理设置派生属性。
- **对于 macOS**：从环境变量读取代理配置。 如果未定义这些变量，则属性派生自系统的代理设置。
- **对于 Linux**：从环境变量读取代理配置。 如果未定义这些变量，则属性初始化将绕过所有地址的非配置实例。

用于 `DefaultProxy` 在 Windows 和基于 Unix 的平台上进行初始化的环境变量包括：

- ` HTTP_PROXY`：用于 HTTP 请求的代理服务器的主机名或 IP 地址。
- `HTTPS_PROXY`：用于 HTTPS 请求的代理服务器的主机名或 IP 地址。
- `ALL_PROXY`：在 HTTP 和 HTTPS 请求上使用的代理服务器的主机名或 IP 地址（ `HTTP_PROXY` 如果 `HTTPS_PROXY` 未定义）或 IP 地址。
- `NO_PROXY`：应从代理中排除的主机名的逗号分隔列表。

## 相关链接

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
