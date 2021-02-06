---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 4d1273fe1ed643f8d45b627db9863b75212b6b24
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596424"
---
# <span data-ttu-id="7131a-102">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7131a-102">Remove-WSManInstance</span></span>

## <span data-ttu-id="7131a-103">摘要</span><span class="sxs-lookup"><span data-stu-id="7131a-103">SYNOPSIS</span></span>
<span data-ttu-id="7131a-104">删除管理资源实例。</span><span class="sxs-lookup"><span data-stu-id="7131a-104">Deletes a management resource instance.</span></span>

## <span data-ttu-id="7131a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7131a-105">SYNTAX</span></span>

### <span data-ttu-id="7131a-106">ComputerName（默认值）</span><span class="sxs-lookup"><span data-stu-id="7131a-106">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="7131a-107">URI</span><span class="sxs-lookup"><span data-stu-id="7131a-107">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="7131a-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7131a-108">DESCRIPTION</span></span>

<span data-ttu-id="7131a-109">**Remove-WSManInstance** cmdlet 删除在 ResourceURI 和 SelectorSet 参数中指定的管理资源的实例。</span><span class="sxs-lookup"><span data-stu-id="7131a-109">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="7131a-110">此 cmdlet 使用 WinRM 连接/传输层来删除管理资源实例。</span><span class="sxs-lookup"><span data-stu-id="7131a-110">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="7131a-111">示例</span><span class="sxs-lookup"><span data-stu-id="7131a-111">EXAMPLES</span></span>

### <span data-ttu-id="7131a-112">示例 1：删除侦听器</span><span class="sxs-lookup"><span data-stu-id="7131a-112">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="7131a-113">此命令删除计算机上的 WS-Management HTTP 侦听器。</span><span class="sxs-lookup"><span data-stu-id="7131a-113">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="7131a-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7131a-114">PARAMETERS</span></span>

### <span data-ttu-id="7131a-115">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="7131a-115">-ApplicationName</span></span>

<span data-ttu-id="7131a-116">指定连接中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="7131a-116">Specifies the application name in the connection.</span></span>
<span data-ttu-id="7131a-117">*ApplicationName* 参数的默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="7131a-117">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="7131a-118">远程终结点的完整标识符采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="7131a-118">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="7131a-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="7131a-119">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="7131a-120">例如： `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="7131a-120">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="7131a-121">托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7131a-121">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="7131a-122">默认设置 WSMAN 适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="7131a-122">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="7131a-123">如果许多计算机建立了与运行 PowerShell 的一台计算机的远程连接，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="7131a-123">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="7131a-124">在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。</span><span class="sxs-lookup"><span data-stu-id="7131a-124">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7131a-125">-Authentication</span><span class="sxs-lookup"><span data-stu-id="7131a-125">-Authentication</span></span>

<span data-ttu-id="7131a-126">指定服务器上要使用的身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="7131a-126">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="7131a-127">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="7131a-127">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7131a-128">基本。</span><span class="sxs-lookup"><span data-stu-id="7131a-128">Basic.</span></span>
<span data-ttu-id="7131a-129">Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。</span><span class="sxs-lookup"><span data-stu-id="7131a-129">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="7131a-130">默认。</span><span class="sxs-lookup"><span data-stu-id="7131a-130">Default.</span></span>
<span data-ttu-id="7131a-131">使用由 WS-Management 协议实现的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="7131a-131">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="7131a-132">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="7131a-132">This is the default.</span></span>
- <span data-ttu-id="7131a-133">摘要。</span><span class="sxs-lookup"><span data-stu-id="7131a-133">Digest.</span></span>
<span data-ttu-id="7131a-134">Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。</span><span class="sxs-lookup"><span data-stu-id="7131a-134">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="7131a-135">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="7131a-135">Kerberos.</span></span>
<span data-ttu-id="7131a-136">客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7131a-136">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="7131a-137">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="7131a-137">Negotiate.</span></span>
<span data-ttu-id="7131a-138">Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。</span><span class="sxs-lookup"><span data-stu-id="7131a-138">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="7131a-139">例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。</span><span class="sxs-lookup"><span data-stu-id="7131a-139">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="7131a-140">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="7131a-140">CredSSP.</span></span>
<span data-ttu-id="7131a-141">使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。</span><span class="sxs-lookup"><span data-stu-id="7131a-141">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="7131a-142">此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="7131a-142">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="7131a-143">注意：CredSSP 将用户凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="7131a-143">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="7131a-144">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="7131a-144">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="7131a-145">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="7131a-145">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="7131a-146">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="7131a-146">-CertificateThumbprint</span></span>

<span data-ttu-id="7131a-147">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="7131a-147">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="7131a-148">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="7131a-148">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="7131a-149">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="7131a-149">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="7131a-150">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="7131a-150">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="7131a-151">若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="7131a-151">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="7131a-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7131a-152">-ComputerName</span></span>

<span data-ttu-id="7131a-153">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="7131a-153">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="7131a-154">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7131a-154">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="7131a-155">使用本地计算机名称、localhost 或点 (.) 指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="7131a-155">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="7131a-156">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="7131a-156">The local computer is the default.</span></span>
<span data-ttu-id="7131a-157">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="7131a-157">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="7131a-158">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="7131a-158">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7131a-159">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="7131a-159">-ConnectionURI</span></span>

<span data-ttu-id="7131a-160">指定连接终结点。</span><span class="sxs-lookup"><span data-stu-id="7131a-160">Specifies the connection endpoint.</span></span>
<span data-ttu-id="7131a-161">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="7131a-161">The format of this string is as follows:</span></span>

<span data-ttu-id="7131a-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="7131a-162">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="7131a-163">以下字符串是此参数的格式正确的值：</span><span class="sxs-lookup"><span data-stu-id="7131a-163">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="7131a-164">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="7131a-164">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7131a-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="7131a-165">-Credential</span></span>

<span data-ttu-id="7131a-166">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7131a-166">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="7131a-167">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="7131a-167">The default is the current user.</span></span>
<span data-ttu-id="7131a-168">键入用户名，如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="7131a-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="7131a-169">或者输入一个 PSCredential 对象，例如 Get-Credential cmdlet 返回的一个 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="7131a-169">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="7131a-170">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="7131a-170">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="7131a-171">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="7131a-171">-OptionSet</span></span>

<span data-ttu-id="7131a-172">将一组开关指定到某个服务以修改或优化请求的性质。</span><span class="sxs-lookup"><span data-stu-id="7131a-172">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="7131a-173">这些开关类似于命令行 shell 中使用的开关，因为它们也特定于服务。</span><span class="sxs-lookup"><span data-stu-id="7131a-173">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="7131a-174">可以指定任何数量的选项。</span><span class="sxs-lookup"><span data-stu-id="7131a-174">Any number of options can be specified.</span></span>

<span data-ttu-id="7131a-175">以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：</span><span class="sxs-lookup"><span data-stu-id="7131a-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="7131a-176">-Port</span><span class="sxs-lookup"><span data-stu-id="7131a-176">-Port</span></span>

<span data-ttu-id="7131a-177">指定要在客户端连接到 WinRM 服务时使用的端口。</span><span class="sxs-lookup"><span data-stu-id="7131a-177">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="7131a-178">当传输为 HTTP 时，默认端口为 80。</span><span class="sxs-lookup"><span data-stu-id="7131a-178">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="7131a-179">当传输为 HTTPS 时，默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="7131a-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="7131a-180">使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。</span><span class="sxs-lookup"><span data-stu-id="7131a-180">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="7131a-181">但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="7131a-181">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="7131a-182">SkipCNCheck 参数应仅用于受信任的计算机。</span><span class="sxs-lookup"><span data-stu-id="7131a-182">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="7131a-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="7131a-183">-ResourceURI</span></span>

<span data-ttu-id="7131a-184">指定资源类或实例的 URI。</span><span class="sxs-lookup"><span data-stu-id="7131a-184">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="7131a-185">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="7131a-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="7131a-186">URI 由资源的前缀和路径组成。</span><span class="sxs-lookup"><span data-stu-id="7131a-186">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="7131a-187">例如：</span><span class="sxs-lookup"><span data-stu-id="7131a-187">For example:</span></span>

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

### <span data-ttu-id="7131a-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="7131a-188">-SelectorSet</span></span>

<span data-ttu-id="7131a-189">指定一组用于选择特定管理资源实例的值对。</span><span class="sxs-lookup"><span data-stu-id="7131a-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="7131a-190">当存在多个资源实例时，将使用 *SelectorSet* 参数。</span><span class="sxs-lookup"><span data-stu-id="7131a-190">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="7131a-191">SelectorSet 的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="7131a-191">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="7131a-192">以下示例显示如何为此参数输入值：</span><span class="sxs-lookup"><span data-stu-id="7131a-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7131a-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="7131a-193">-SessionOption</span></span>

<span data-ttu-id="7131a-194">为 WS-Management 会话指定扩展选项。</span><span class="sxs-lookup"><span data-stu-id="7131a-194">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="7131a-195">输入使用 New-WSManSessionOption cmdlet 创建的 **SessionOption** 对象。</span><span class="sxs-lookup"><span data-stu-id="7131a-195">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="7131a-196">有关可用选项的详细信息，请键入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="7131a-196">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="7131a-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="7131a-197">-UseSSL</span></span>

<span data-ttu-id="7131a-198">指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="7131a-198">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="7131a-199">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="7131a-199">By default, SSL is not used.</span></span>

<span data-ttu-id="7131a-200">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="7131a-200">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="7131a-201">*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="7131a-201">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="7131a-202">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="7131a-202">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7131a-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7131a-203">CommonParameters</span></span>

<span data-ttu-id="7131a-204">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7131a-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7131a-205">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7131a-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7131a-206">输入</span><span class="sxs-lookup"><span data-stu-id="7131a-206">INPUTS</span></span>

### <span data-ttu-id="7131a-207">无</span><span class="sxs-lookup"><span data-stu-id="7131a-207">None</span></span>

<span data-ttu-id="7131a-208">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="7131a-208">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="7131a-209">输出</span><span class="sxs-lookup"><span data-stu-id="7131a-209">OUTPUTS</span></span>

### <span data-ttu-id="7131a-210">无</span><span class="sxs-lookup"><span data-stu-id="7131a-210">None</span></span>

<span data-ttu-id="7131a-211">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="7131a-211">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7131a-212">注释</span><span class="sxs-lookup"><span data-stu-id="7131a-212">NOTES</span></span>

* <span data-ttu-id="7131a-213">Windows Management Instrumentation (WMI) cmdlet 类似于 Remove-WmiObject cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7131a-213">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="7131a-214">**Get-wmiobject** 使用 DCOM 连接/传输层来创建或更新 WMI 实例。</span><span class="sxs-lookup"><span data-stu-id="7131a-214">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="7131a-215">相关链接</span><span class="sxs-lookup"><span data-stu-id="7131a-215">RELATED LINKS</span></span>

[<span data-ttu-id="7131a-216">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="7131a-216">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="7131a-217">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7131a-217">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="7131a-218">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="7131a-218">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="7131a-219">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7131a-219">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="7131a-220">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="7131a-220">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="7131a-221">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7131a-221">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="7131a-222">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="7131a-222">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="7131a-223">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7131a-223">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="7131a-224">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="7131a-224">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="7131a-225">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="7131a-225">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="7131a-226">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="7131a-226">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="7131a-227">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="7131a-227">Test-WSMan</span></span>](Test-WSMan.md)

