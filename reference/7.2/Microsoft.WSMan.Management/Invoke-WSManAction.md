---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: e2456e1da866929d60c36cc0e09990399b41614b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595801"
---
# <span data-ttu-id="21730-102">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="21730-102">Invoke-WSManAction</span></span>

## <span data-ttu-id="21730-103">摘要</span><span class="sxs-lookup"><span data-stu-id="21730-103">SYNOPSIS</span></span>
<span data-ttu-id="21730-104">对由资源 URI 和选择器指定的对象调用操作。</span><span class="sxs-lookup"><span data-stu-id="21730-104">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="21730-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21730-105">SYNTAX</span></span>

### <span data-ttu-id="21730-106">URI (默认值) </span><span class="sxs-lookup"><span data-stu-id="21730-106">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="21730-107">计算机名</span><span class="sxs-lookup"><span data-stu-id="21730-107">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="21730-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="21730-108">DESCRIPTION</span></span>
<span data-ttu-id="21730-109">**Invoke-wsmanaction** 对 RESOURCE_URI 指定的对象运行操作，其中的参数由键值对指定。</span><span class="sxs-lookup"><span data-stu-id="21730-109">The **Invoke-WSManAction** runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="21730-110">此 cmdlet 使用 WSMan 连接/传输层来运行操作。</span><span class="sxs-lookup"><span data-stu-id="21730-110">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="21730-111">示例</span><span class="sxs-lookup"><span data-stu-id="21730-111">EXAMPLES</span></span>

### <span data-ttu-id="21730-112">示例1：调用方法</span><span class="sxs-lookup"><span data-stu-id="21730-112">Example 1: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="21730-113">此命令调用对应于后台处理程序服务 Win32_Service WMI 类实例的 **StartService** 方法。</span><span class="sxs-lookup"><span data-stu-id="21730-113">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="21730-114">返回值指示操作是否成功。</span><span class="sxs-lookup"><span data-stu-id="21730-114">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="21730-115">在这种情况下，返回值 0 指示成功。</span><span class="sxs-lookup"><span data-stu-id="21730-115">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="21730-116">返回值 5 指示该服务已启动。</span><span class="sxs-lookup"><span data-stu-id="21730-116">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="21730-117">示例2：调用方法</span><span class="sxs-lookup"><span data-stu-id="21730-117">Example 2: Invoke a method</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="21730-118">此命令通过使用来自文件的输入对后台处理程序服务调用 **StopService** 方法。</span><span class="sxs-lookup"><span data-stu-id="21730-118">This command calls the **StopService** method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="21730-119">文件 Input.xml 包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="21730-119">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### <span data-ttu-id="21730-120">示例3：使用指定的参数值调用方法</span><span class="sxs-lookup"><span data-stu-id="21730-120">Example 3: Invoke a method with specified parameter values</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="21730-121">此命令调用 Win32_Process 类的 **Create** 方法。</span><span class="sxs-lookup"><span data-stu-id="21730-121">This command calls the **Create** method of the Win32_Process class.</span></span>
<span data-ttu-id="21730-122">它将方法传递两个参数值，Notepad.exe 和 C:\</span><span class="sxs-lookup"><span data-stu-id="21730-122">It passes the method two parameter values, Notepad.exe and C:\.</span></span>
<span data-ttu-id="21730-123">因此，将创建一个新进程来运行记事本，新进程的当前目录将设置为 C:\。</span><span class="sxs-lookup"><span data-stu-id="21730-123">As a result, a new process is created to run Notepad, and the current directory of the new process is set to C:\.</span></span>

### <span data-ttu-id="21730-124">示例4：在远程计算机上调用方法</span><span class="sxs-lookup"><span data-stu-id="21730-124">Example 4: Invoke a method on a remote computer</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="21730-125">此命令调用对应于后台处理程序服务 Win32_Service WMI 类实例的 **StartService** 方法。</span><span class="sxs-lookup"><span data-stu-id="21730-125">This command calls the **StartService** method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="21730-126">由于指定了 *ComputerName* 参数，因此该命令针对远程 server01 计算机运行。</span><span class="sxs-lookup"><span data-stu-id="21730-126">Because the *ComputerName* parameter is specified, the command runs against the remote server01 computer.</span></span>

## <span data-ttu-id="21730-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21730-127">PARAMETERS</span></span>

### <span data-ttu-id="21730-128">-Action</span><span class="sxs-lookup"><span data-stu-id="21730-128">-Action</span></span>
<span data-ttu-id="21730-129">指定要在由 ResourceURI 和选择器指定的管理对象上运行的方法。</span><span class="sxs-lookup"><span data-stu-id="21730-129">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21730-130">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="21730-130">-ApplicationName</span></span>
<span data-ttu-id="21730-131">指定连接中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="21730-131">Specifies the application name in the connection.</span></span>
<span data-ttu-id="21730-132">*ApplicationName* 参数的默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="21730-132">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="21730-133">远程终结点的完整标识符采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="21730-133">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="21730-134">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="21730-134">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="21730-135">例如： `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="21730-135">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="21730-136">托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="21730-136">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="21730-137">默认设置 WSMAN 适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="21730-137">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="21730-138">如果许多计算机建立了与运行 PowerShell 的一台计算机的远程连接，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="21730-138">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="21730-139">在此情况下，IIS 将托管 Web Services for Management (WS-Management) 以提高效率。</span><span class="sxs-lookup"><span data-stu-id="21730-139">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="21730-140">-Authentication</span><span class="sxs-lookup"><span data-stu-id="21730-140">-Authentication</span></span>
<span data-ttu-id="21730-141">指定服务器上要使用的身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="21730-141">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="21730-142">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="21730-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="21730-143">基本。</span><span class="sxs-lookup"><span data-stu-id="21730-143">Basic.</span></span>
<span data-ttu-id="21730-144">Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。</span><span class="sxs-lookup"><span data-stu-id="21730-144">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="21730-145">默认。</span><span class="sxs-lookup"><span data-stu-id="21730-145">Default.</span></span>
<span data-ttu-id="21730-146">使用由 WS-Management 协议实现的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="21730-146">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="21730-147">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="21730-147">This is the default.</span></span>
- <span data-ttu-id="21730-148">摘要。</span><span class="sxs-lookup"><span data-stu-id="21730-148">Digest.</span></span>
<span data-ttu-id="21730-149">Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。</span><span class="sxs-lookup"><span data-stu-id="21730-149">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="21730-150">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="21730-150">Kerberos.</span></span>
<span data-ttu-id="21730-151">客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="21730-151">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="21730-152">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="21730-152">Negotiate.</span></span>
<span data-ttu-id="21730-153">Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。</span><span class="sxs-lookup"><span data-stu-id="21730-153">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="21730-154">例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。</span><span class="sxs-lookup"><span data-stu-id="21730-154">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="21730-155">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="21730-155">CredSSP.</span></span>
<span data-ttu-id="21730-156">使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。</span><span class="sxs-lookup"><span data-stu-id="21730-156">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="21730-157">此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="21730-157">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="21730-158">注意：CredSSP 将用户凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="21730-158">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="21730-159">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="21730-159">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="21730-160">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="21730-160">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="21730-161">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="21730-161">-CertificateThumbprint</span></span>
<span data-ttu-id="21730-162">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="21730-162">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="21730-163">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="21730-163">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="21730-164">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="21730-164">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="21730-165">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="21730-165">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="21730-166">若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="21730-166">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="21730-167">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="21730-167">-ComputerName</span></span>
<span data-ttu-id="21730-168">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="21730-168">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="21730-169">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="21730-169">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="21730-170">使用本地计算机名称、localhost 或点 (.) 指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="21730-170">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="21730-171">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="21730-171">The local computer is the default.</span></span>
<span data-ttu-id="21730-172">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="21730-172">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="21730-173">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="21730-173">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="21730-174">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="21730-174">-ConnectionURI</span></span>
<span data-ttu-id="21730-175">指定连接终结点。</span><span class="sxs-lookup"><span data-stu-id="21730-175">Specifies the connection endpoint.</span></span>
<span data-ttu-id="21730-176">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="21730-176">The format of this string is as follows:</span></span>

<span data-ttu-id="21730-177">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="21730-177">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="21730-178">以下字符串是此参数的格式正确的值：</span><span class="sxs-lookup"><span data-stu-id="21730-178">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="21730-179">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="21730-179">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="21730-180">-Credential</span><span class="sxs-lookup"><span data-stu-id="21730-180">-Credential</span></span>
<span data-ttu-id="21730-181">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="21730-181">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="21730-182">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="21730-182">The default is the current user.</span></span>
<span data-ttu-id="21730-183">键入用户名，如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="21730-183">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="21730-184">或者输入一个 PSCredential 对象，例如 Get-Credential cmdlet 返回的一个 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="21730-184">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="21730-185">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="21730-185">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="21730-186">-FilePath</span><span class="sxs-lookup"><span data-stu-id="21730-186">-FilePath</span></span>
<span data-ttu-id="21730-187">指定用于更新管理资源的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="21730-187">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="21730-188">通过使用 *ResourceURI* 参数和 *SelectorSet* 参数来指定管理资源。</span><span class="sxs-lookup"><span data-stu-id="21730-188">You specify the management resource by using the *ResourceURI* parameter and the *SelectorSet* parameter.</span></span>
<span data-ttu-id="21730-189">例如，以下命令使用 *FilePath* 参数：</span><span class="sxs-lookup"><span data-stu-id="21730-189">For example, the following command uses the *FilePath* parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="21730-190">此命令通过使用来自文件的输入对 **后台处理程序** 服务调用 **StopService** 方法。</span><span class="sxs-lookup"><span data-stu-id="21730-190">This command calls the **StopService** method on the **Spooler** service by using input from a file.</span></span>
<span data-ttu-id="21730-191">文件 Input.xml 包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="21730-191">The file, Input.xml, contains the following content:</span></span>

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

### <span data-ttu-id="21730-192">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="21730-192">-OptionSet</span></span>
<span data-ttu-id="21730-193">将一组开关指定到某个服务以修改或优化请求的性质。</span><span class="sxs-lookup"><span data-stu-id="21730-193">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="21730-194">这些开关类似于命令行 shell 中使用的开关，因为它们也特定于服务。</span><span class="sxs-lookup"><span data-stu-id="21730-194">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="21730-195">可以指定任何数量的选项。</span><span class="sxs-lookup"><span data-stu-id="21730-195">Any number of options can be specified.</span></span>

<span data-ttu-id="21730-196">以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：</span><span class="sxs-lookup"><span data-stu-id="21730-196">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21730-197">-Port</span><span class="sxs-lookup"><span data-stu-id="21730-197">-Port</span></span>
<span data-ttu-id="21730-198">指定要在客户端连接到 WinRM 服务时使用的端口。</span><span class="sxs-lookup"><span data-stu-id="21730-198">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="21730-199">当传输为 HTTP 时，默认端口为 80。</span><span class="sxs-lookup"><span data-stu-id="21730-199">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="21730-200">当传输为 HTTPS 时，默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="21730-200">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="21730-201">使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。</span><span class="sxs-lookup"><span data-stu-id="21730-201">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="21730-202">但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="21730-202">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="21730-203">SkipCNCheck 参数应仅用于受信任的计算机。</span><span class="sxs-lookup"><span data-stu-id="21730-203">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="21730-204">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="21730-204">-ResourceURI</span></span>
<span data-ttu-id="21730-205">指定资源类或实例的 URI。</span><span class="sxs-lookup"><span data-stu-id="21730-205">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="21730-206">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="21730-206">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="21730-207">URI 由资源的前缀和路径组成。</span><span class="sxs-lookup"><span data-stu-id="21730-207">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="21730-208">例如：</span><span class="sxs-lookup"><span data-stu-id="21730-208">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21730-209">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="21730-209">-SelectorSet</span></span>
<span data-ttu-id="21730-210">指定一组用于选择特定管理资源实例的值对。</span><span class="sxs-lookup"><span data-stu-id="21730-210">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="21730-211">当存在多个资源实例时，将使用 *SelectorSet* 。</span><span class="sxs-lookup"><span data-stu-id="21730-211">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="21730-212">SelectorSet 的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="21730-212">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="21730-213">以下示例显示如何为此参数输入值：</span><span class="sxs-lookup"><span data-stu-id="21730-213">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21730-214">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="21730-214">-SessionOption</span></span>
<span data-ttu-id="21730-215">为 WS-Management 会话指定扩展选项。</span><span class="sxs-lookup"><span data-stu-id="21730-215">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="21730-216">输入使用 New-WSManSessionOption cmdlet 创建的 **SessionOption** 对象。</span><span class="sxs-lookup"><span data-stu-id="21730-216">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="21730-217">有关可用选项的详细信息，请键入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="21730-217">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="21730-218">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="21730-218">-UseSSL</span></span>
<span data-ttu-id="21730-219">指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="21730-219">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="21730-220">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="21730-220">By default, SSL is not used.</span></span>

<span data-ttu-id="21730-221">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="21730-221">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="21730-222">*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="21730-222">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="21730-223">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="21730-223">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="21730-224">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="21730-224">-ValueSet</span></span>
<span data-ttu-id="21730-225">指定可帮助修改管理资源的哈希表。</span><span class="sxs-lookup"><span data-stu-id="21730-225">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="21730-226">使用 *ResourceURI* 和 *SelectorSet* 指定管理资源。</span><span class="sxs-lookup"><span data-stu-id="21730-226">You specify the management resource by using *ResourceURI* and *SelectorSet*.</span></span>
<span data-ttu-id="21730-227">*ValueSet* 参数的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="21730-227">The value of the *ValueSet* parameter must be a hash table.</span></span>

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

### <span data-ttu-id="21730-228">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21730-228">CommonParameters</span></span>
<span data-ttu-id="21730-229">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="21730-229">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21730-230">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="21730-230">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21730-231">输入</span><span class="sxs-lookup"><span data-stu-id="21730-231">INPUTS</span></span>

### <span data-ttu-id="21730-232">无</span><span class="sxs-lookup"><span data-stu-id="21730-232">None</span></span>
<span data-ttu-id="21730-233">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="21730-233">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="21730-234">输出</span><span class="sxs-lookup"><span data-stu-id="21730-234">OUTPUTS</span></span>

### <span data-ttu-id="21730-235">无</span><span class="sxs-lookup"><span data-stu-id="21730-235">None</span></span>
<span data-ttu-id="21730-236">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="21730-236">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="21730-237">注释</span><span class="sxs-lookup"><span data-stu-id="21730-237">NOTES</span></span>

## <span data-ttu-id="21730-238">相关链接</span><span class="sxs-lookup"><span data-stu-id="21730-238">RELATED LINKS</span></span>

[<span data-ttu-id="21730-239">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="21730-239">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="21730-240">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="21730-240">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="21730-241">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="21730-241">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="21730-242">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="21730-242">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="21730-243">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="21730-243">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="21730-244">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="21730-244">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="21730-245">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="21730-245">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="21730-246">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="21730-246">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="21730-247">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="21730-247">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="21730-248">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="21730-248">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="21730-249">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="21730-249">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="21730-250">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="21730-250">Test-WSMan</span></span>](Test-WSMan.md)

