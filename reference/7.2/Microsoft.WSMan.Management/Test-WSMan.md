---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: a29a9ef1e35f0c0f802952b99d853c617614a97b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597025"
---
# <span data-ttu-id="fc511-102">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="fc511-102">Test-WSMan</span></span>

## <span data-ttu-id="fc511-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fc511-103">SYNOPSIS</span></span>
<span data-ttu-id="fc511-104">测试 WinRM 服务是否正在本地或远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-104">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="fc511-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc511-105">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="fc511-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fc511-106">DESCRIPTION</span></span>

<span data-ttu-id="fc511-107">**Test-WSMan** 将提交一个标识请求，此请求可确定 WinRM 服务是否正在本地或远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-107">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="fc511-108">如果接受测试的计算机正在运行该服务，则该 cmdlet 将显示被测服务的 WS-Management 标识架构、协议版本、产品供应商以及产品版本。</span><span class="sxs-lookup"><span data-stu-id="fc511-108">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="fc511-109">示例</span><span class="sxs-lookup"><span data-stu-id="fc511-109">EXAMPLES</span></span>

### <span data-ttu-id="fc511-110">示例 1：确定 WinRM 服务的状态</span><span class="sxs-lookup"><span data-stu-id="fc511-110">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="fc511-111">此命令确定 WinRM 服务是否正在本地计算机或远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-111">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="fc511-112">示例 2：确定远程计算机上 WinRM 服务的状态</span><span class="sxs-lookup"><span data-stu-id="fc511-112">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="fc511-113">此命令确定 WinRM 服务是否正在 server01 计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-113">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="fc511-114">示例 3：确定 WinRM 服务的状态和操作系统版本</span><span class="sxs-lookup"><span data-stu-id="fc511-114">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="fc511-115">此命令将使用 authentication 参数进行测试以了解 WS-Management (WinRM) 服务是否正在本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-115">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="fc511-116">使用 authentication 参数可允许 **Test-WSMan** 返回操作系统版本。</span><span class="sxs-lookup"><span data-stu-id="fc511-116">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="fc511-117">示例 4：确定远程计算机上 WinRM 服务的状态和操作系统版本</span><span class="sxs-lookup"><span data-stu-id="fc511-117">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="fc511-118">此命令将使用 authentication 参数进行测试以了解 WS-Management (WinRM) 服务是否正在名为 server01 的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fc511-118">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="fc511-119">使用 authentication 参数可允许 **Test-WSMan** 返回操作系统版本。</span><span class="sxs-lookup"><span data-stu-id="fc511-119">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="fc511-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc511-120">PARAMETERS</span></span>

### <span data-ttu-id="fc511-121">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="fc511-121">-ApplicationName</span></span>

<span data-ttu-id="fc511-122">指定连接中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="fc511-122">Specifies the application name in the connection.</span></span>
<span data-ttu-id="fc511-123">*ApplicationName* 参数的默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="fc511-123">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="fc511-124">远程终结点的完整标识符采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="fc511-124">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="fc511-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="fc511-125">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="fc511-126">例如： `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="fc511-126">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="fc511-127">托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc511-127">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="fc511-128">默认设置 WSMAN 适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="fc511-128">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="fc511-129">如果许多计算机建立了与运行 PowerShell 的一台计算机的远程连接，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="fc511-129">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="fc511-130">在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。</span><span class="sxs-lookup"><span data-stu-id="fc511-130">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="fc511-131">-Authentication</span><span class="sxs-lookup"><span data-stu-id="fc511-131">-Authentication</span></span>

<span data-ttu-id="fc511-132">指定服务器上要使用的身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="fc511-132">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="fc511-133">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="fc511-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fc511-134">基本。</span><span class="sxs-lookup"><span data-stu-id="fc511-134">Basic.</span></span>
<span data-ttu-id="fc511-135">Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。</span><span class="sxs-lookup"><span data-stu-id="fc511-135">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="fc511-136">默认。</span><span class="sxs-lookup"><span data-stu-id="fc511-136">Default.</span></span>
<span data-ttu-id="fc511-137">使用由 WS-Management 协议实现的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="fc511-137">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="fc511-138">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="fc511-138">This is the default.</span></span>
- <span data-ttu-id="fc511-139">摘要。</span><span class="sxs-lookup"><span data-stu-id="fc511-139">Digest.</span></span>
<span data-ttu-id="fc511-140">Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。</span><span class="sxs-lookup"><span data-stu-id="fc511-140">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="fc511-141">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="fc511-141">Kerberos.</span></span>
<span data-ttu-id="fc511-142">客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="fc511-142">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="fc511-143">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="fc511-143">Negotiate.</span></span>
<span data-ttu-id="fc511-144">Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。</span><span class="sxs-lookup"><span data-stu-id="fc511-144">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="fc511-145">例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。</span><span class="sxs-lookup"><span data-stu-id="fc511-145">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="fc511-146">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="fc511-146">CredSSP.</span></span>
<span data-ttu-id="fc511-147">使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。</span><span class="sxs-lookup"><span data-stu-id="fc511-147">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="fc511-148">此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="fc511-148">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="fc511-149">注意：CredSSP 将用户凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="fc511-149">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="fc511-150">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="fc511-150">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="fc511-151">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="fc511-151">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="fc511-152">重要提示：如果不指定 *Authentication* 参数，则以匿名方式（不使用身份验证）将 **Test-WSMan** 请求发送到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="fc511-152">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="fc511-153">如果以匿名方式发出请求，不会返回特定于操作系统版本的信息。</span><span class="sxs-lookup"><span data-stu-id="fc511-153">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="fc511-154">相反，此 cmdlet 会将操作系统版本和 Service Pack 级别显示为空值（操作系统：0.0.0 SP：0.0）。</span><span class="sxs-lookup"><span data-stu-id="fc511-154">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

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

### <span data-ttu-id="fc511-155">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="fc511-155">-CertificateThumbprint</span></span>

<span data-ttu-id="fc511-156">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="fc511-156">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="fc511-157">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="fc511-157">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="fc511-158">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="fc511-158">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="fc511-159">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="fc511-159">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="fc511-160">若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="fc511-160">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="fc511-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fc511-161">-ComputerName</span></span>

<span data-ttu-id="fc511-162">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="fc511-162">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="fc511-163">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fc511-163">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="fc511-164">使用本地计算机名称、localhost 或点 (.) 指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="fc511-164">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="fc511-165">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="fc511-165">The local computer is the default.</span></span>
<span data-ttu-id="fc511-166">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="fc511-166">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="fc511-167">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="fc511-167">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc511-168">-Credential</span><span class="sxs-lookup"><span data-stu-id="fc511-168">-Credential</span></span>

<span data-ttu-id="fc511-169">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fc511-169">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="fc511-170">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="fc511-170">The default is the current user.</span></span>
<span data-ttu-id="fc511-171">键入用户名，如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="fc511-171">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="fc511-172">或者输入一个 PSCredential 对象，例如 Get-Credential cmdlet 返回的一个 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="fc511-172">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="fc511-173">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="fc511-173">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="fc511-174">-Port</span><span class="sxs-lookup"><span data-stu-id="fc511-174">-Port</span></span>

<span data-ttu-id="fc511-175">指定要在客户端连接到 WinRM 服务时使用的端口。</span><span class="sxs-lookup"><span data-stu-id="fc511-175">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="fc511-176">当传输为 HTTP 时，默认端口为 80。</span><span class="sxs-lookup"><span data-stu-id="fc511-176">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="fc511-177">当传输为 HTTPS 时，默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="fc511-177">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="fc511-178">使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。</span><span class="sxs-lookup"><span data-stu-id="fc511-178">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="fc511-179">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="fc511-179">-UseSSL</span></span>

<span data-ttu-id="fc511-180">指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="fc511-180">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="fc511-181">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="fc511-181">By default, SSL is not used.</span></span>

<span data-ttu-id="fc511-182">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="fc511-182">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="fc511-183">*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="fc511-183">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="fc511-184">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="fc511-184">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="fc511-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc511-185">CommonParameters</span></span>

<span data-ttu-id="fc511-186">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fc511-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc511-187">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fc511-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc511-188">输入</span><span class="sxs-lookup"><span data-stu-id="fc511-188">INPUTS</span></span>

### <span data-ttu-id="fc511-189">无</span><span class="sxs-lookup"><span data-stu-id="fc511-189">None</span></span>

<span data-ttu-id="fc511-190">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="fc511-190">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="fc511-191">输出</span><span class="sxs-lookup"><span data-stu-id="fc511-191">OUTPUTS</span></span>

### <span data-ttu-id="fc511-192">无</span><span class="sxs-lookup"><span data-stu-id="fc511-192">None</span></span>

<span data-ttu-id="fc511-193">此 cmdlet 将不生成任何输出对象。</span><span class="sxs-lookup"><span data-stu-id="fc511-193">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="fc511-194">注释</span><span class="sxs-lookup"><span data-stu-id="fc511-194">NOTES</span></span>

* <span data-ttu-id="fc511-195">默认情况下，**Test-WSMan** cmdlet 在不使用身份验证的情况下查询 WinRM 服务，并且它不会返回特定于操作系统版本的信息。</span><span class="sxs-lookup"><span data-stu-id="fc511-195">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="fc511-196">相反，它会将操作系统版本和 Service Pack 级别显示为空值（操作系统：0.0.0 SP：0.0）。</span><span class="sxs-lookup"><span data-stu-id="fc511-196">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="fc511-197">相关链接</span><span class="sxs-lookup"><span data-stu-id="fc511-197">RELATED LINKS</span></span>

[<span data-ttu-id="fc511-198">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="fc511-198">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="fc511-199">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fc511-199">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="fc511-200">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="fc511-200">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="fc511-201">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fc511-201">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="fc511-202">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fc511-202">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="fc511-203">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fc511-203">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="fc511-204">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="fc511-204">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="fc511-205">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fc511-205">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="fc511-206">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="fc511-206">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="fc511-207">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fc511-207">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="fc511-208">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fc511-208">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="fc511-209">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="fc511-209">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

