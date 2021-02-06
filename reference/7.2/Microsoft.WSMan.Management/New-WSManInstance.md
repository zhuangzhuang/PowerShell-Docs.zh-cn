---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: dd0343e9b6014e079c322309b699874683bacd6a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597024"
---
# <span data-ttu-id="bfe2d-102">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bfe2d-102">New-WSManInstance</span></span>

## <span data-ttu-id="bfe2d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="bfe2d-103">SYNOPSIS</span></span>
<span data-ttu-id="bfe2d-104">创建管理资源的新实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-104">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="bfe2d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bfe2d-105">SYNTAX</span></span>

### <span data-ttu-id="bfe2d-106">ComputerName（默认值）</span><span class="sxs-lookup"><span data-stu-id="bfe2d-106">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="bfe2d-107">URI</span><span class="sxs-lookup"><span data-stu-id="bfe2d-107">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="bfe2d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bfe2d-108">DESCRIPTION</span></span>

<span data-ttu-id="bfe2d-109">`New-WSManInstance`Cmdlet 创建管理资源的新实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-109">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="bfe2d-110">它使用资源 URI 和值集或输入文件来创建管理资源的新实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-110">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="bfe2d-111">此 cmdlet 使用 WinRM 连接/传输层来创建管理资源实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-111">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="bfe2d-112">示例</span><span class="sxs-lookup"><span data-stu-id="bfe2d-112">EXAMPLES</span></span>

### <span data-ttu-id="bfe2d-113">示例1：创建 HTTPS 侦听器</span><span class="sxs-lookup"><span data-stu-id="bfe2d-113">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="bfe2d-114">此命令在所有 IP 地址上创建 WS-Management HTTPS 侦听器的实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-114">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="bfe2d-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bfe2d-115">PARAMETERS</span></span>

### <span data-ttu-id="bfe2d-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="bfe2d-116">-ApplicationName</span></span>

<span data-ttu-id="bfe2d-117">指定连接中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-117">Specifies the application name in the connection.</span></span> <span data-ttu-id="bfe2d-118">**ApplicationName** 参数的默认值为 **WSMAN**。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-118">The default value of the **ApplicationName** parameter is **WSMAN**.</span></span> <span data-ttu-id="bfe2d-119">远程终结点的完整标识符采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-119">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="bfe2d-120">例如：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-120">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="bfe2d-121">托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="bfe2d-122">**WSMAN** 的默认设置适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-122">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="bfe2d-123">当有许多计算机建立了与运行 Windows PowerShell 的一台计算机的远程连接时，需要使用此参数。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-123">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="bfe2d-124">在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-125">-Authentication</span><span class="sxs-lookup"><span data-stu-id="bfe2d-125">-Authentication</span></span>

<span data-ttu-id="bfe2d-126">指定服务器上要使用的身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-126">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="bfe2d-127">可能的值有：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-127">Possible values are:</span></span>

- <span data-ttu-id="bfe2d-128">基本： Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-128">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="bfe2d-129">默认值：使用由 WS-Management 协议实现的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-129">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="bfe2d-130">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-130">This is the default.</span></span>
- <span data-ttu-id="bfe2d-131">Digest：Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-131">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="bfe2d-132">Kerberos：客户端计算机和服务器使用 Kerberos 证书相互进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-132">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="bfe2d-133">Negotiate：Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-133">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="bfe2d-134">例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-134">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="bfe2d-135">CredSSP：使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-135">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="bfe2d-136">此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-136">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="bfe2d-137">CredSSP 将用户的凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-137">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="bfe2d-138">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-138">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="bfe2d-139">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-139">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-140">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="bfe2d-140">-CertificateThumbprint</span></span>

<span data-ttu-id="bfe2d-141">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-141">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="bfe2d-142">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-142">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="bfe2d-143">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-143">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="bfe2d-144">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-144">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="bfe2d-145">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或命令。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-145">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="bfe2d-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bfe2d-146">-ComputerName</span></span>

<span data-ttu-id="bfe2d-147">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-147">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="bfe2d-148">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-148">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="bfe2d-149">使用本地计算机名称、使用 localhost 或使用点 (`.`) 来指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-149">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="bfe2d-150">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-150">The local computer is the default.</span></span> <span data-ttu-id="bfe2d-151">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-151">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="bfe2d-152">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-152">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-153">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="bfe2d-153">-ConnectionURI</span></span>

<span data-ttu-id="bfe2d-154">指定连接终结点。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-154">Specifies the connection endpoint.</span></span>
<span data-ttu-id="bfe2d-155">此字符串的格式为：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-155">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="bfe2d-156">以下字符串是此参数的格式正确的值：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-156">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="bfe2d-157">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-157">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="bfe2d-158">-Credential</span></span>

<span data-ttu-id="bfe2d-159">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-159">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="bfe2d-160">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-160">The default is the current user.</span></span> <span data-ttu-id="bfe2d-161">键入用户名，如 "User01"、"Domain01\User01" 或 " User@Domain.com "。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-161">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="bfe2d-162">或者输入 PSCredential 对象，例如 cmdlet 返回的一个 PSCredential 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-162">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="bfe2d-163">键入用户名时，将会提示你输入密码。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-163">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-164">-FilePath</span><span class="sxs-lookup"><span data-stu-id="bfe2d-164">-FilePath</span></span>

<span data-ttu-id="bfe2d-165">指定用于创建管理资源的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-165">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="bfe2d-166">使用 **ResourceURI** 参数和 **SelectorSet** 参数指定管理资源。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-166">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="bfe2d-167">例如，以下命令使用 **File** 参数：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-167">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="bfe2d-168">此命令使用文件的输入对后台处理程序服务调用 **StopService** 方法。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-168">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="bfe2d-169">文件 `Input.xml` 包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-169">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-170">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="bfe2d-170">-OptionSet</span></span>

<span data-ttu-id="bfe2d-171">将一组开关传递到某个服务以修改或优化请求的性质。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-171">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="bfe2d-172">这些开关与命令行 shell 中使用的开关相似，因为它们也是特定于服务的。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-172">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="bfe2d-173">可以指定任何数量的选项。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-173">Any number of options can be specified.</span></span>

<span data-ttu-id="bfe2d-174">以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-174">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-175">-Port</span><span class="sxs-lookup"><span data-stu-id="bfe2d-175">-Port</span></span>

<span data-ttu-id="bfe2d-176">指定要在客户端连接到 WinRM 服务时使用的端口。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-176">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="bfe2d-177">当传输为 HTTP 时，默认端口为 80。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-177">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="bfe2d-178">当传输为 HTTPS 时，默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="bfe2d-179">使用 HTTPS 作为传输协议时， **ComputerName** 参数的值必须与服务器的证书公用名 (CN) 相匹配。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-179">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="bfe2d-180">但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-180">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="bfe2d-181">SkipCNCheck 参数应仅用于受信任的计算机。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-181">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-182">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="bfe2d-182">-ResourceURI</span></span>

<span data-ttu-id="bfe2d-183">包含资源类或实例的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-183">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="bfe2d-184">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-184">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="bfe2d-185">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-185">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="bfe2d-186">例如：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-186">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-187">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="bfe2d-187">-SelectorSet</span></span>

<span data-ttu-id="bfe2d-188">指定一组用于选择特定管理资源实例的值对。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-188">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="bfe2d-189">当存在多个资源实例时，将使用 **SelectorSet** 参数。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-189">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="bfe2d-190">**SelectorSet** 参数的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-190">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="bfe2d-191">以下示例显示如何为此参数输入值：</span><span class="sxs-lookup"><span data-stu-id="bfe2d-191">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-192">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="bfe2d-192">-SessionOption</span></span>

<span data-ttu-id="bfe2d-193">为 WS-Management 会话定义一组扩展选项。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-193">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="bfe2d-194">输入使用 cmdlet 创建的 **SessionOption** 对象 `New-WSManSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-194">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="bfe2d-195">有关可用选项的详细信息，请参阅 `New-WSManSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-195">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-196">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="bfe2d-196">-UseSSL</span></span>

<span data-ttu-id="bfe2d-197">指定应使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-197">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="bfe2d-198">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-198">By default, SSL is not used.</span></span>

<span data-ttu-id="bfe2d-199">WS-Management 对通过网络传输的所有 Windows PowerShell 内容进行加密。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-199">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="bfe2d-200">**UseSSL** 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-200">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="bfe2d-201">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-201">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-202">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="bfe2d-202">-ValueSet</span></span>

<span data-ttu-id="bfe2d-203">指定可帮助修改管理资源的哈希表。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-203">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="bfe2d-204">使用 **ResourceURI** 参数和 **SelectorSet** 参数指定管理资源。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-204">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="bfe2d-205">**ValueSet** 参数的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-205">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfe2d-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfe2d-206">CommonParameters</span></span>

<span data-ttu-id="bfe2d-207">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfe2d-208">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-208">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bfe2d-209">输入</span><span class="sxs-lookup"><span data-stu-id="bfe2d-209">INPUTS</span></span>

### <span data-ttu-id="bfe2d-210">无</span><span class="sxs-lookup"><span data-stu-id="bfe2d-210">None</span></span>

<span data-ttu-id="bfe2d-211">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-211">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="bfe2d-212">输出</span><span class="sxs-lookup"><span data-stu-id="bfe2d-212">OUTPUTS</span></span>

### <span data-ttu-id="bfe2d-213">无</span><span class="sxs-lookup"><span data-stu-id="bfe2d-213">None</span></span>

<span data-ttu-id="bfe2d-214">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-214">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bfe2d-215">注释</span><span class="sxs-lookup"><span data-stu-id="bfe2d-215">NOTES</span></span>

<span data-ttu-id="bfe2d-216">`Set-WmiInstance`Cmdlet （Windows Management Instrumentation (WMI) cmdlet）类似。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-216">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="bfe2d-217">`Set-WmiInstance` 使用 DCOM 连接/传输层来创建或更新 WMI 实例。</span><span class="sxs-lookup"><span data-stu-id="bfe2d-217">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="bfe2d-218">相关链接</span><span class="sxs-lookup"><span data-stu-id="bfe2d-218">RELATED LINKS</span></span>

[<span data-ttu-id="bfe2d-219">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bfe2d-219">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="bfe2d-220">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bfe2d-220">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="bfe2d-221">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bfe2d-221">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="bfe2d-222">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bfe2d-222">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="bfe2d-223">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bfe2d-223">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="bfe2d-224">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bfe2d-224">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="bfe2d-225">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="bfe2d-225">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="bfe2d-226">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="bfe2d-226">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="bfe2d-227">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bfe2d-227">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="bfe2d-228">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bfe2d-228">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="bfe2d-229">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="bfe2d-229">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="bfe2d-230">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="bfe2d-230">Test-WSMan</span></span>](Test-WSMan.md)

