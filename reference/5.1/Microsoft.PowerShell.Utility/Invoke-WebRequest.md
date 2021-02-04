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
# <span data-ttu-id="8f722-102">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="8f722-102">Invoke-WebRequest</span></span>

## <span data-ttu-id="8f722-103">摘要</span><span class="sxs-lookup"><span data-stu-id="8f722-103">SYNOPSIS</span></span>
<span data-ttu-id="8f722-104">从 Internet 上的网页中获取内容。</span><span class="sxs-lookup"><span data-stu-id="8f722-104">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="8f722-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8f722-105">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="8f722-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f722-106">DESCRIPTION</span></span>

<span data-ttu-id="8f722-107">`Invoke-WebRequest`Cmdlet 可将 HTTP、HTTPS、FTP 和文件请求发送到网页或 web 服务。</span><span class="sxs-lookup"><span data-stu-id="8f722-107">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="8f722-108">它将分析该响应并返回表单、链接、图像和其他重要的 HTML 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="8f722-108">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="8f722-109">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="8f722-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="8f722-110">默认情况下，在分析页时，可能会运行网页中的脚本代码来填充 `ParsedHtml` 属性。</span><span class="sxs-lookup"><span data-stu-id="8f722-110">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="8f722-111">使用 `-UseBasicParsing` 开关可取消显示此选项。</span><span class="sxs-lookup"><span data-stu-id="8f722-111">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="8f722-112">示例</span><span class="sxs-lookup"><span data-stu-id="8f722-112">EXAMPLES</span></span>

### <span data-ttu-id="8f722-113">示例1：发送 web 请求</span><span class="sxs-lookup"><span data-stu-id="8f722-113">Example 1: Send a web request</span></span>

<span data-ttu-id="8f722-114">此命令使用 `Invoke-WebRequest` cmdlet 向 Bing.com 站点发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="8f722-114">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="8f722-115">第一个命令发出请求，并将响应保存在 `$R` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8f722-115">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="8f722-116">第二个命令筛选 **大于** 属性中的对象，其中 **name** 属性类似于 "\* Value"， **tagName** 为 "INPUT"。</span><span class="sxs-lookup"><span data-stu-id="8f722-116">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="8f722-117">筛选后的结果将通过管道传递到 `Select-Object` ，以选择 **名称** 和 **值** 属性。</span><span class="sxs-lookup"><span data-stu-id="8f722-117">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="8f722-118">示例2：使用有状态 web 服务</span><span class="sxs-lookup"><span data-stu-id="8f722-118">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="8f722-119">此示例演示如何将 `Invoke-WebRequest` cmdlet 与有状态 web 服务（如 Facebook）结合使用。</span><span class="sxs-lookup"><span data-stu-id="8f722-119">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="8f722-120">第一个命令使用 `Invoke-WebRequest` cmdlet 发送登录请求。</span><span class="sxs-lookup"><span data-stu-id="8f722-120">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="8f722-121">该命令为 **SessionVariable** 参数的值指定值 "FB"，并将结果保存在 `$R` 变量中。</span><span class="sxs-lookup"><span data-stu-id="8f722-121">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="8f722-122">当该命令完成时， `$R` 变量将包含一个 **HtmlWebResponseObject** ，该 `$FB` 变量将包含一个 **WebRequestSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="8f722-122">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="8f722-123">Cmdlet 登录 `Invoke-WebRequest` 到 facebook 后，变量中的 web 响应对象的 **StatusDescription** 属性 `$R` 指示用户已成功登录。</span><span class="sxs-lookup"><span data-stu-id="8f722-123">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="8f722-124">示例3：获取网页中的链接</span><span class="sxs-lookup"><span data-stu-id="8f722-124">Example 3: Get links from a web page</span></span>

<span data-ttu-id="8f722-125">此命令将获取网页中的链接。</span><span class="sxs-lookup"><span data-stu-id="8f722-125">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="8f722-126">`Invoke-WebRequest`Cmdlet 将获取网页内容。</span><span class="sxs-lookup"><span data-stu-id="8f722-126">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="8f722-127">然后，返回的 **HtmlWebResponseObject** 的 **Links** 属性用于显示每个链接的 **Href** 属性。</span><span class="sxs-lookup"><span data-stu-id="8f722-127">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="8f722-128">示例4：捕获 Invoke-WebRequest 中的非成功消息</span><span class="sxs-lookup"><span data-stu-id="8f722-128">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="8f722-129">如果 `Invoke-WebRequest` 遇到非成功 HTTP 消息 (404、500等 ) ，它将不返回任何输出，并引发终止错误。</span><span class="sxs-lookup"><span data-stu-id="8f722-129">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="8f722-130">若要捕获错误并查看 **StatusCode** ，可以在块中包含执行 `try/catch` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-130">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="8f722-131">下面的示例演示如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="8f722-131">The following example shows how to accomplish this.</span></span>

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

<span data-ttu-id="8f722-132">终止错误由 `catch` 块捕获，后者从 **异常** 对象中检索 **StatusCode** 。</span><span class="sxs-lookup"><span data-stu-id="8f722-132">The terminating error is caught by the `catch` block, which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="8f722-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f722-133">PARAMETERS</span></span>

### <span data-ttu-id="8f722-134">-Body</span><span class="sxs-lookup"><span data-stu-id="8f722-134">-Body</span></span>

<span data-ttu-id="8f722-135">指定请求的正文。</span><span class="sxs-lookup"><span data-stu-id="8f722-135">Specifies the body of the request.</span></span>
<span data-ttu-id="8f722-136">正文是请求的内容，位于标头之后。</span><span class="sxs-lookup"><span data-stu-id="8f722-136">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="8f722-137">还可以通过管道将正文值传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-137">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="8f722-138">可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。</span><span class="sxs-lookup"><span data-stu-id="8f722-138">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="8f722-139">当输入是一个 GET 请求且正文是一个 **IDictionary** (通常情况下) 哈希表中，主体将作为查询参数添加到 URI 中。</span><span class="sxs-lookup"><span data-stu-id="8f722-139">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="8f722-140">对于其他 GET 请求，主体将设置为标准格式的请求正文的值 `name=value` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-140">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="8f722-141">当正文是窗体或调用的输出时 `Invoke-WebRequest` ，PowerShell 会将请求内容设置为窗体字段。</span><span class="sxs-lookup"><span data-stu-id="8f722-141">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="8f722-142">例如：</span><span class="sxs-lookup"><span data-stu-id="8f722-142">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="8f722-143">或 -</span><span class="sxs-lookup"><span data-stu-id="8f722-143">or -</span></span>

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

### <span data-ttu-id="8f722-144">-Certificate</span><span class="sxs-lookup"><span data-stu-id="8f722-144">-Certificate</span></span>

<span data-ttu-id="8f722-145">指定用于安全的 Web 请求的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="8f722-145">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="8f722-146">输入一个包含证书的变量，或可获取该证书的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="8f722-146">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="8f722-147">若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` **证书** () 驱动器中的 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-147">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="8f722-148">如果证书无效或不具有足够的权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="8f722-148">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="8f722-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="8f722-149">-CertificateThumbprint</span></span>

<span data-ttu-id="8f722-150">指定有权发送请求的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="8f722-150">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="8f722-151">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="8f722-151">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="8f722-152">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="8f722-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="8f722-153">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="8f722-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="8f722-154">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-154">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="8f722-155">-ContentType</span><span class="sxs-lookup"><span data-stu-id="8f722-155">-ContentType</span></span>

<span data-ttu-id="8f722-156">指定 Web 请求的内容类型。</span><span class="sxs-lookup"><span data-stu-id="8f722-156">Specifies the content type of the web request.</span></span>

<span data-ttu-id="8f722-157">如果省略此参数且请求方法为 POST，则 `Invoke-WebRequest` 将内容类型设置为 application/x-url 编码。</span><span class="sxs-lookup"><span data-stu-id="8f722-157">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="8f722-158">否则，将不会在调用中指定内容类型。</span><span class="sxs-lookup"><span data-stu-id="8f722-158">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="8f722-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="8f722-159">-Credential</span></span>

<span data-ttu-id="8f722-160">指定有权发送请求的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8f722-160">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="8f722-161">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="8f722-161">The default is the current user.</span></span>

<span data-ttu-id="8f722-162">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-162">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="8f722-163">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="8f722-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8f722-164">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="8f722-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="8f722-165">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="8f722-165">-DisableKeepAlive</span></span>

<span data-ttu-id="8f722-166">指示该 cmdlet 将 HTTP 头中的 **KeepAlive** 值设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="8f722-166">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="8f722-167">默认情况下， **KeepAlive** 为 **True**。</span><span class="sxs-lookup"><span data-stu-id="8f722-167">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="8f722-168">**KeepAlive** 建立到服务器的持续性连接，以促进后续请求。</span><span class="sxs-lookup"><span data-stu-id="8f722-168">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="8f722-169">-标头</span><span class="sxs-lookup"><span data-stu-id="8f722-169">-Headers</span></span>

<span data-ttu-id="8f722-170">指定 Web 请求的标头。</span><span class="sxs-lookup"><span data-stu-id="8f722-170">Specifies the headers of the web request.</span></span> <span data-ttu-id="8f722-171">输入哈希表或字典。</span><span class="sxs-lookup"><span data-stu-id="8f722-171">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="8f722-172">若要设置 **UserAgent** 标头，请使用 **UserAgent** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-172">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="8f722-173">不能使用此参数指定 **UserAgent** 或 cookie 标头。</span><span class="sxs-lookup"><span data-stu-id="8f722-173">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="8f722-174">-InFile</span><span class="sxs-lookup"><span data-stu-id="8f722-174">-InFile</span></span>

<span data-ttu-id="8f722-175">从文件中获取 Web 请求的内容。</span><span class="sxs-lookup"><span data-stu-id="8f722-175">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="8f722-176">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="8f722-176">Enter a path and file name.</span></span> <span data-ttu-id="8f722-177">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="8f722-177">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="8f722-178">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="8f722-178">-MaximumRedirection</span></span>

<span data-ttu-id="8f722-179">指定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。</span><span class="sxs-lookup"><span data-stu-id="8f722-179">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="8f722-180">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="8f722-180">The default value is 5.</span></span> <span data-ttu-id="8f722-181">值为 0（零）将阻止所有重定向。</span><span class="sxs-lookup"><span data-stu-id="8f722-181">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="8f722-182">-方法</span><span class="sxs-lookup"><span data-stu-id="8f722-182">-Method</span></span>

<span data-ttu-id="8f722-183">指定用于 Web 请求的方法。</span><span class="sxs-lookup"><span data-stu-id="8f722-183">Specifies the method used for the web request.</span></span> <span data-ttu-id="8f722-184">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="8f722-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f722-185">默认</span><span class="sxs-lookup"><span data-stu-id="8f722-185">Default</span></span>
- <span data-ttu-id="8f722-186">删除</span><span class="sxs-lookup"><span data-stu-id="8f722-186">Delete</span></span>
- <span data-ttu-id="8f722-187">获取</span><span class="sxs-lookup"><span data-stu-id="8f722-187">Get</span></span>
- <span data-ttu-id="8f722-188">Head</span><span class="sxs-lookup"><span data-stu-id="8f722-188">Head</span></span>
- <span data-ttu-id="8f722-189">合并</span><span class="sxs-lookup"><span data-stu-id="8f722-189">Merge</span></span>
- <span data-ttu-id="8f722-190">选项</span><span class="sxs-lookup"><span data-stu-id="8f722-190">Options</span></span>
- <span data-ttu-id="8f722-191">修补程序</span><span class="sxs-lookup"><span data-stu-id="8f722-191">Patch</span></span>
- <span data-ttu-id="8f722-192">邮递</span><span class="sxs-lookup"><span data-stu-id="8f722-192">Post</span></span>
- <span data-ttu-id="8f722-193">Put</span><span class="sxs-lookup"><span data-stu-id="8f722-193">Put</span></span>
- <span data-ttu-id="8f722-194">跟踪</span><span class="sxs-lookup"><span data-stu-id="8f722-194">Trace</span></span>

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

### <span data-ttu-id="8f722-195">-OutFile</span><span class="sxs-lookup"><span data-stu-id="8f722-195">-OutFile</span></span>

<span data-ttu-id="8f722-196">指定此 cmdlet 为其保存响应正文的输出文件。</span><span class="sxs-lookup"><span data-stu-id="8f722-196">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="8f722-197">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="8f722-197">Enter a path and file name.</span></span>
<span data-ttu-id="8f722-198">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="8f722-198">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="8f722-199">默认情况下，将 `Invoke-WebRequest` 结果返回到管道。</span><span class="sxs-lookup"><span data-stu-id="8f722-199">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="8f722-200">若要将这些结果发送到文件和管道，请使用 **Passthru** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-200">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="8f722-201">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8f722-201">-PassThru</span></span>

<span data-ttu-id="8f722-202">指示除了将结果写入文件外，该 cmdlet 还会返回结果。</span><span class="sxs-lookup"><span data-stu-id="8f722-202">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="8f722-203">仅当命令中还使用了 **OutFile** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="8f722-203">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="8f722-204">-Proxy</span><span class="sxs-lookup"><span data-stu-id="8f722-204">-Proxy</span></span>

<span data-ttu-id="8f722-205">为请求指定代理服务器，而不是直接连接到 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="8f722-205">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="8f722-206">输入网络代理服务器的 URI。</span><span class="sxs-lookup"><span data-stu-id="8f722-206">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="8f722-207">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8f722-207">-ProxyCredential</span></span>

<span data-ttu-id="8f722-208">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8f722-208">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="8f722-209">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="8f722-209">The default is the current user.</span></span>

<span data-ttu-id="8f722-210">键入用户名（如 `User01` 或 `Domain01\User01` ），或输入 PSCredential 对象，例如由 cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-210">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="8f722-211">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="8f722-211">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="8f722-212">不能在同一命令中使用 **ProxyCredential** 参数和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-212">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="8f722-213">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="8f722-213">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="8f722-214">指示该 cmdlet 使用当前用户的凭据来访问 **代理** 参数指定的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="8f722-214">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="8f722-215">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="8f722-215">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="8f722-216">不能在同一命令中使用 **ProxyCredential** 参数和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-216">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="8f722-217">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="8f722-217">-SessionVariable</span></span>

<span data-ttu-id="8f722-218">指定此 cmdlet 为其创建 web 请求会话的变量，并将其保存在值中。</span><span class="sxs-lookup"><span data-stu-id="8f722-218">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="8f722-219">输入一个不带美元符号 () 符号的变量名称 `$` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-219">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="8f722-220">指定会话变量时，将 `Invoke-WebRequest` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。</span><span class="sxs-lookup"><span data-stu-id="8f722-220">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="8f722-221">命令完成后可以立即在会话中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="8f722-221">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="8f722-222">与远程会话不同，Web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="8f722-222">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="8f722-223">它是一个包含有关连接和请求的信息的对象，包括 Cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="8f722-223">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="8f722-224">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="8f722-224">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="8f722-225">若要在后续的 Web 请求中使用 Web 请求会话，请在 **WebSession** 参数的值中指定会话变量。</span><span class="sxs-lookup"><span data-stu-id="8f722-225">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="8f722-226">PowerShell 在建立新连接时使用 web 请求会话对象中的数据。</span><span class="sxs-lookup"><span data-stu-id="8f722-226">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="8f722-227">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential**。</span><span class="sxs-lookup"><span data-stu-id="8f722-227">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="8f722-228">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="8f722-228">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="8f722-229">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-229">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="8f722-230">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="8f722-230">-TimeoutSec</span></span>

<span data-ttu-id="8f722-231">指定在超时之前请求可以挂起多长时间。输入一个值（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="8f722-231">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="8f722-232">默认值 0 指定无限超时。</span><span class="sxs-lookup"><span data-stu-id="8f722-232">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="8f722-233">域名系统 (DNS) 查询可能需要长达15秒钟的时间来返回或超时。如果你的请求包含需要解析的主机名，并将 **TimeoutSec** 设置为大于零的值，但不超过15秒，则在引发 **WebException** 之前可能需要15秒或更长时间，并且你的请求会超时。</span><span class="sxs-lookup"><span data-stu-id="8f722-233">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="8f722-234">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="8f722-234">-TransferEncoding</span></span>

<span data-ttu-id="8f722-235">指定传输编码 HTTP 响应头的值。</span><span class="sxs-lookup"><span data-stu-id="8f722-235">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="8f722-236">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="8f722-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f722-237">块</span><span class="sxs-lookup"><span data-stu-id="8f722-237">Chunked</span></span>
- <span data-ttu-id="8f722-238">压缩</span><span class="sxs-lookup"><span data-stu-id="8f722-238">Compress</span></span>
- <span data-ttu-id="8f722-239">Deflate</span><span class="sxs-lookup"><span data-stu-id="8f722-239">Deflate</span></span>
- <span data-ttu-id="8f722-240">GZip</span><span class="sxs-lookup"><span data-stu-id="8f722-240">GZip</span></span>
- <span data-ttu-id="8f722-241">标识</span><span class="sxs-lookup"><span data-stu-id="8f722-241">Identity</span></span>

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

### <span data-ttu-id="8f722-242">-Uri</span><span class="sxs-lookup"><span data-stu-id="8f722-242">-Uri</span></span>

<span data-ttu-id="8f722-243">指定将 Web 请求发送到的 Internet 资源的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="8f722-243">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="8f722-244">输入 URI。</span><span class="sxs-lookup"><span data-stu-id="8f722-244">Enter a URI.</span></span> <span data-ttu-id="8f722-245">此参数支持 HTTP、HTTPS、FTP 和 FILE 值。</span><span class="sxs-lookup"><span data-stu-id="8f722-245">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="8f722-246">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="8f722-246">This parameter is required.</span></span>

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

### <span data-ttu-id="8f722-247">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="8f722-247">-UseBasicParsing</span></span>

<span data-ttu-id="8f722-248">指示 cmdlet 使用 HTML 内容的响应对象，而不文档对象模型 (DOM) 进行分析。</span><span class="sxs-lookup"><span data-stu-id="8f722-248">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="8f722-249">当 Internet Explorer 未安装在计算机上（例如在 Windows Server 操作系统安装 Server Core）时，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="8f722-249">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="8f722-250">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="8f722-250">-UseDefaultCredentials</span></span>

<span data-ttu-id="8f722-251">指示 cmdet 使用当前用户的凭据来发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="8f722-251">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="8f722-252">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="8f722-252">-UserAgent</span></span>

<span data-ttu-id="8f722-253">指定 Web 请求的用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="8f722-253">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="8f722-254">默认的用户代理类似于 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 每个操作系统和平台稍有不同。</span><span class="sxs-lookup"><span data-stu-id="8f722-254">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="8f722-255">若要使用大多数 Internet 浏览器使用的标准用户代理字符串测试网站，请使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 类的属性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="8f722-255">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="8f722-256">例如，以下命令使用 Internet Explorer 的用户代理字符串</span><span class="sxs-lookup"><span data-stu-id="8f722-256">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="8f722-257">-WebSession</span><span class="sxs-lookup"><span data-stu-id="8f722-257">-WebSession</span></span>

<span data-ttu-id="8f722-258">指定一个 Web 请求会话。</span><span class="sxs-lookup"><span data-stu-id="8f722-258">Specifies a web request session.</span></span> <span data-ttu-id="8f722-259">输入变量名称，包括美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="8f722-259">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="8f722-260">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential**。</span><span class="sxs-lookup"><span data-stu-id="8f722-260">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="8f722-261">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="8f722-261">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="8f722-262">与远程会话不同，Web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="8f722-262">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="8f722-263">它是一个包含有关连接和请求的信息的对象，包括 Cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="8f722-263">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="8f722-264">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="8f722-264">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="8f722-265">若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号)  (的变量名称 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-265">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="8f722-266">`Invoke-WebRequest` 创建会话并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="8f722-266">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="8f722-267">在后续命令中，将该变量用作 **WebSession** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="8f722-267">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="8f722-268">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="8f722-268">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="8f722-269">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f722-269">CommonParameters</span></span>

<span data-ttu-id="8f722-270">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-270">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8f722-271">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8f722-271">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f722-272">输入</span><span class="sxs-lookup"><span data-stu-id="8f722-272">INPUTS</span></span>

### <span data-ttu-id="8f722-273">System.Object</span><span class="sxs-lookup"><span data-stu-id="8f722-273">System.Object</span></span>

<span data-ttu-id="8f722-274">你可以通过管道将 web 请求的正文传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="8f722-274">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="8f722-275">输出</span><span class="sxs-lookup"><span data-stu-id="8f722-275">OUTPUTS</span></span>

### <span data-ttu-id="8f722-276">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="8f722-276">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="8f722-277">注释</span><span class="sxs-lookup"><span data-stu-id="8f722-277">NOTES</span></span>

## <span data-ttu-id="8f722-278">相关链接</span><span class="sxs-lookup"><span data-stu-id="8f722-278">RELATED LINKS</span></span>

[<span data-ttu-id="8f722-279">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="8f722-279">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="8f722-280">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="8f722-280">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="8f722-281">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="8f722-281">ConvertTo-Json</span></span>](ConvertTo-Json.md)
