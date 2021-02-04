---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: f3545065d4879830a5051ef687f210c7fbd1251e
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860654"
---
# Invoke-WebRequest

## 摘要
从 Internet 上的网页中获取内容。

## SYNTAX

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-WebRequest`Cmdlet 可将 HTTP、HTTPS、FTP 和文件请求发送到网页或 web 服务。
它将分析该响应并返回表单、链接、图像和其他重要的 HTML 元素的集合。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

> [!NOTE]
> 默认情况下，在分析页时，可能会运行网页中的脚本代码来填充 `ParsedHtml` 属性。
> 使用 `-UseBasicParsing` 开关可取消显示此选项。

## 示例

### 示例1：发送 web 请求

此命令使用 `Invoke-WebRequest` cmdlet 向 Bing.com 站点发送 web 请求。

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

第一个命令发出请求，并将响应保存在 `$R` 变量中。

第二个命令筛选 **大于** 属性中的对象，其中 **name** 属性类似于 "* Value"， **tagName** 为 "INPUT"。 筛选后的结果将通过管道传递到 `Select-Object` ，以选择 **名称** 和 **值** 属性。

### 示例2：使用有状态 web 服务

此示例演示如何将 `Invoke-WebRequest` cmdlet 与有状态 web 服务（如 Facebook）结合使用。

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

第一个命令使用 `Invoke-WebRequest` cmdlet 发送登录请求。 该命令为 **SessionVariable** 参数的值指定值 "FB"，并将结果保存在 `$R` 变量中。 当该命令完成时， `$R` 变量将包含一个 **HtmlWebResponseObject** ，该 `$FB` 变量将包含一个 **WebRequestSession** 对象。

Cmdlet 登录 `Invoke-WebRequest` 到 facebook 后，变量中的 web 响应对象的 **StatusDescription** 属性 `$R` 指示用户已成功登录。

### 示例3：获取网页中的链接

此命令将获取网页中的链接。

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

`Invoke-WebRequest`Cmdlet 将获取网页内容。 然后，返回的 **HtmlWebResponseObject** 的 **Links** 属性用于显示每个链接的 **Href** 属性。

### 示例4：捕获 Invoke-WebRequest 中的非成功消息

如果 `Invoke-WebRequest` 遇到非成功 HTTP 消息 (404、500等 ) ，它将不返回任何输出，并引发终止错误。 若要捕获错误并查看 **StatusCode** ，可以在块中包含执行 `try/catch` 。 下面的示例演示如何实现此目的。

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

### -Body

指定请求的正文。
正文是请求的内容，位于标头之后。
还可以通过管道将正文值传递给 `Invoke-WebRequest` 。

可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。

当输入是一个 GET 请求且正文是一个 **IDictionary** (通常情况下) 哈希表中，主体将作为查询参数添加到 URI 中。 对于其他 GET 请求，主体将设置为标准格式的请求正文的值 `name=value` 。

当正文是窗体或调用的输出时 `Invoke-WebRequest` ，PowerShell 会将请求内容设置为窗体字段。
例如：

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- 或 -

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` **证书** () 驱动器中的 cmdlet `Cert:` 。 如果证书无效或不具有足够的权限，则该命令将失败。

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

指定有权发送请求的用户帐户的数字公钥证书 (X509)。 输入证书的证书指纹。 在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。

若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或命令 `Cert:` 。

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

如果省略此参数且请求方法为 POST，则 `Invoke-WebRequest` 将内容类型设置为 application/x-url 编码。 否则，将不会在调用中指定内容类型。

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

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
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

### -标头

指定 Web 请求的标头。 输入哈希表或字典。

若要设置 **UserAgent** 标头，请使用 **UserAgent** 参数。 不能使用此参数指定 **UserAgent** 或 cookie 标头。

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

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutFile

指定此 cmdlet 为其保存响应正文的输出文件。 请输入路径和文件名。
如果省略路径，则默认路径为当前位置。

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

### -Proxy

为请求指定代理服务器，而不是直接连接到 Internet 资源。
输入网络代理服务器的 URI。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。 默认为当前用户。

键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。

仅当命令中还使用了 **代理** 参数时，此参数才有效。 不能在同一命令中使用 **ProxyCredential** 参数和 **ProxyUseDefaultCredentials** 参数。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

指示该 cmdlet 使用当前用户的凭据来访问 **代理** 参数指定的代理服务器。

仅当命令中还使用了 **代理** 参数时，此参数才有效。 不能在同一命令中使用 **ProxyCredential** 参数和 **ProxyUseDefaultCredentials** 参数。

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

### -SessionVariable

指定此 cmdlet 为其创建 web 请求会话的变量，并将其保存在值中。
输入一个不带美元符号 () 符号的变量名称 `$` 。

指定会话变量时，将 `Invoke-WebRequest` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。 命令完成后可以立即在会话中使用该变量。

与远程会话不同，Web 请求会话不是持续性连接。 它是一个包含有关连接和请求的信息的对象，包括 Cookie、凭据、最大重定向值和用户代理字符串。 可用于共享 Web 请求之间的状态和数据。

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

### -TimeoutSec

指定在超时之前请求可以挂起多长时间。输入一个值（以秒为单位）。 默认值 0 指定无限超时。

域名系统 (DNS) 查询可能需要长达15秒钟的时间来返回或超时。如果你的请求包含需要解析的主机名，并将 **TimeoutSec** 设置为大于零的值，但不超过15秒，则在引发 **WebException** 之前可能需要15秒或更长时间，并且你的请求会超时。

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

指定将 Web 请求发送到的 Internet 资源的统一资源标识符 (URI)。 输入 URI。 此参数支持 HTTP、HTTPS、FTP 和 FILE 值。

此参数是必需的。

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

指示 cmdlet 使用 HTML 内容的响应对象，而不文档对象模型 (DOM) 进行分析。 当 Internet Explorer 未安装在计算机上（例如在 Windows Server 操作系统安装 Server Core）时，此参数是必需的。

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

指示 cmdet 使用当前用户的凭据来发送 web 请求。

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

指定 Web 请求的用户代理字符串。 默认的用户代理类似于 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 每个操作系统和平台稍有不同。

若要使用大多数 Internet 浏览器使用的标准用户代理字符串测试网站，请使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 类的属性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。 例如，以下命令使用 Internet Explorer 的用户代理字符串

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

若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential**。 参数值优先于 Web 请求会话中的值。

与远程会话不同，Web 请求会话不是持续性连接。 它是一个包含有关连接和请求的信息的对象，包括 Cookie、凭据、最大重定向值和用户代理字符串。 可用于共享 Web 请求之间的状态和数据。

若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号)  (的变量名称 `Invoke-WebRequest` 。 `Invoke-WebRequest` 创建会话并将其保存在变量中。 在后续命令中，将该变量用作 **WebSession** 参数的值。

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

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Object

你可以通过管道将 web 请求的正文传递给 `Invoke-WebRequest` 。

## 输出

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## 注释

## 相关链接

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
