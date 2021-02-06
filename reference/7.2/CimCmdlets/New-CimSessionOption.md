---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 54a2ca8a28d54bfe1d9676acdaace4592f62620f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599057"
---
# <span data-ttu-id="6a815-102">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="6a815-102">New-CimSessionOption</span></span>

## <span data-ttu-id="6a815-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6a815-103">SYNOPSIS</span></span>
<span data-ttu-id="6a815-104">指定 New-CimSession cmdlet 的高级选项。</span><span class="sxs-lookup"><span data-stu-id="6a815-104">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="6a815-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a815-105">SYNTAX</span></span>

### <span data-ttu-id="6a815-106">ProtocolTypeSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="6a815-106">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="6a815-107">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a815-107">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="6a815-108">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a815-108">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="6a815-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6a815-109">DESCRIPTION</span></span>

<span data-ttu-id="6a815-110">`New-CimSessionOption`Cmdlet 可创建 CIM 会话选项对象的实例。</span><span class="sxs-lookup"><span data-stu-id="6a815-110">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="6a815-111">使用 CIM 会话选项对象作为 cmdlet 的输入 `New-CimSession` 来指定 CIM 会话的选项。</span><span class="sxs-lookup"><span data-stu-id="6a815-111">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="6a815-112">此 cmdlet 具有两个参数集，一个用于 WsMan 选项，一个用于分布式组件对象模型 (DCOM) 选项。</span><span class="sxs-lookup"><span data-stu-id="6a815-112">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="6a815-113">根据你使用的参数，该 cmdlet 将返回 DCOM 会话选项的实例，或返回 WsMan 会话选项。</span><span class="sxs-lookup"><span data-stu-id="6a815-113">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="6a815-114">示例</span><span class="sxs-lookup"><span data-stu-id="6a815-114">EXAMPLES</span></span>

### <span data-ttu-id="6a815-115">示例1：为 DCOM 创建 CIM 会话选项对象</span><span class="sxs-lookup"><span data-stu-id="6a815-115">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="6a815-116">此示例为 DCOM 协议创建一个 CIM 会话选项对象，并将其存储在一个名为的变量中 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="6a815-116">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="6a815-117">然后，将变量的内容传递给 `New-CimSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a815-117">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="6a815-118">`New-CimSession` 然后，使用变量中定义的选项，使用名为 Server01 的远程服务器创建一个新的 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="6a815-118">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="6a815-119">示例2：为 WsMan 创建 CIM 会话选项对象</span><span class="sxs-lookup"><span data-stu-id="6a815-119">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="6a815-120">此示例为 WsMan 协议创建 CIM 会话选项对象。</span><span class="sxs-lookup"><span data-stu-id="6a815-120">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="6a815-121">对象包含 **ProxyAuthentication** 参数所指定的 **Kerberos** 身份验证模式的配置、 **ProxyCredential** 参数指定的凭据，并指定该命令将跳过 CA 检查，跳过 CN 检查并使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="6a815-121">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="6a815-122">示例3：使用指定的区域性创建 CIM 会话选项对象</span><span class="sxs-lookup"><span data-stu-id="6a815-122">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="6a815-123">此示例指定用于 CIM 会话的区域性。</span><span class="sxs-lookup"><span data-stu-id="6a815-123">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="6a815-124">默认情况下，在执行操作时将使用客户端的区域性。</span><span class="sxs-lookup"><span data-stu-id="6a815-124">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="6a815-125">但是，可以使用 **culture** 参数重写默认区域性。</span><span class="sxs-lookup"><span data-stu-id="6a815-125">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="6a815-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a815-126">PARAMETERS</span></span>

### <span data-ttu-id="6a815-127">-Culture</span><span class="sxs-lookup"><span data-stu-id="6a815-127">-Culture</span></span>

<span data-ttu-id="6a815-128">指定要用于 CIM 会话的用户界面区域性。</span><span class="sxs-lookup"><span data-stu-id="6a815-128">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="6a815-129">使用以下格式之一指定此参数的值：</span><span class="sxs-lookup"><span data-stu-id="6a815-129">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="6a815-130">格式为的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 "en-us"。</span><span class="sxs-lookup"><span data-stu-id="6a815-130">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="6a815-131">包含 **CultureInfo** 对象的变量。</span><span class="sxs-lookup"><span data-stu-id="6a815-131">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="6a815-132">用于获取 **CultureInfo** 对象的命令，如 [获取区域性](../Microsoft.PowerShell.Utility/Get-Culture.md)</span><span class="sxs-lookup"><span data-stu-id="6a815-132">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-133">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="6a815-133">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="6a815-134">指示 Kerberos 连接连接到其服务主体名称 (SPN) 包含服务端口号的服务。</span><span class="sxs-lookup"><span data-stu-id="6a815-134">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="6a815-135">这种类型的连接不常用。</span><span class="sxs-lookup"><span data-stu-id="6a815-135">This type of connection is not common.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-136">-Encoding</span><span class="sxs-lookup"><span data-stu-id="6a815-136">-Encoding</span></span>

<span data-ttu-id="6a815-137">指定用于 WsMan 协议的编码。</span><span class="sxs-lookup"><span data-stu-id="6a815-137">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="6a815-138">此参数的可接受值为： **Default**、 **Utf8** 或 **Utf16**。</span><span class="sxs-lookup"><span data-stu-id="6a815-138">The acceptable values for this parameter are: **Default**, **Utf8**, or **Utf16**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-139">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="6a815-139">-HttpPrefix</span></span>

<span data-ttu-id="6a815-140">指定计算机名称和端口号后面的 HTTP URL 部分。</span><span class="sxs-lookup"><span data-stu-id="6a815-140">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="6a815-141">更改此情况并不常见。</span><span class="sxs-lookup"><span data-stu-id="6a815-141">Changing this is not common.</span></span> <span data-ttu-id="6a815-142">默认情况下，此参数的值为 **/wsman**。</span><span class="sxs-lookup"><span data-stu-id="6a815-142">By default, the value of this parameter is **/wsman**.</span></span>

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-143">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="6a815-143">-Impersonation</span></span>

<span data-ttu-id="6a815-144">使用模拟 Windows Management Instrumentation (WMI) 创建 DCOM 会话。</span><span class="sxs-lookup"><span data-stu-id="6a815-144">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="6a815-145">此参数的有效值是：</span><span class="sxs-lookup"><span data-stu-id="6a815-145">Valid values for this parameter are:</span></span>

- <span data-ttu-id="6a815-146">默认： DCOM 可以使用其常规安全协商算法选择模拟级别。</span><span class="sxs-lookup"><span data-stu-id="6a815-146">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="6a815-147">无：客户端对于服务器是匿名的。</span><span class="sxs-lookup"><span data-stu-id="6a815-147">None: The client is anonymous to the server.</span></span> <span data-ttu-id="6a815-148">服务器进程可以模拟客户端，但模拟标记不包含任何信息，因此不能使用。</span><span class="sxs-lookup"><span data-stu-id="6a815-148">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="6a815-149">标识：允许对象查询调用方的凭据。</span><span class="sxs-lookup"><span data-stu-id="6a815-149">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="6a815-150">模拟：允许对象使用调用方的凭据。</span><span class="sxs-lookup"><span data-stu-id="6a815-150">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="6a815-151">委托：允许对象允许其他对象使用调用方的凭据。</span><span class="sxs-lookup"><span data-stu-id="6a815-151">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="6a815-152">如果未指定 **模拟** ，则 `New-CimSession` cmdlet 将使用值 " **模拟**"。</span><span class="sxs-lookup"><span data-stu-id="6a815-152">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-153">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="6a815-153">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="6a815-154">指定任一方向的 WsMan XML 消息的大小限制。</span><span class="sxs-lookup"><span data-stu-id="6a815-154">Specifies the size limit of WsMan XML messages for either direction.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-155">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="6a815-155">-NoEncryption</span></span>

<span data-ttu-id="6a815-156">指定禁用数据加密。</span><span class="sxs-lookup"><span data-stu-id="6a815-156">Specifies that data encryption is turned off.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-157">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="6a815-157">-PacketIntegrity</span></span>

<span data-ttu-id="6a815-158">指定创建到 WMI 的 DCOM 会话使用组件对象模型 (COM) _PacketIntegrity_ 功能。</span><span class="sxs-lookup"><span data-stu-id="6a815-158">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="6a815-159">默认情况下，使用 DCOM 创建的所有 CIM 会话都将 **PacketIntegrity** 参数设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="6a815-159">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-160">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="6a815-160">-PacketPrivacy</span></span>

<span data-ttu-id="6a815-161">使用 COM _PacketPrivacy_ 创建到 WMI 的 DCOM 会话。</span><span class="sxs-lookup"><span data-stu-id="6a815-161">Creates a DCOM session to WMI using the COM _PacketPrivacy_.</span></span> <span data-ttu-id="6a815-162">默认情况下，使用 DCOM 创建的所有 CIM 会话都将 **PacketPrivacy** 参数设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="6a815-162">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-163">-Protocol</span><span class="sxs-lookup"><span data-stu-id="6a815-163">-Protocol</span></span>

<span data-ttu-id="6a815-164">指定要使用的协议。</span><span class="sxs-lookup"><span data-stu-id="6a815-164">Specifies the protocol to use.</span></span> <span data-ttu-id="6a815-165">此参数可接受的值包括： **DCOM**、 **默认** 或 **Wsman**。</span><span class="sxs-lookup"><span data-stu-id="6a815-165">The acceptable values for this parameter are: **DCOM**, **Default**, or **Wsman**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-166">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="6a815-166">-ProxyAuthentication</span></span>

<span data-ttu-id="6a815-167">指定用于代理解析的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="6a815-167">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="6a815-168">此参数可接受的值包括： **Default**、 **Digest**、 **Negotiate**、 **Basic**、 **Kerberos**、 **NtlmDomain** 或 **CredSsp**。</span><span class="sxs-lookup"><span data-stu-id="6a815-168">The acceptable values for this parameter are: **Default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain**, or **CredSsp**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-169">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6a815-169">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="6a815-170">指定用于代理身份验证的用户帐户的 (x.509) 数字公钥证书。</span><span class="sxs-lookup"><span data-stu-id="6a815-170">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="6a815-171">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="6a815-171">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="6a815-172">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="6a815-172">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6a815-173">它们只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="6a815-173">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="6a815-174">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a815-174">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6a815-175">-ProxyCredential</span></span>

<span data-ttu-id="6a815-176">指定用于代理身份验证的凭据。</span><span class="sxs-lookup"><span data-stu-id="6a815-176">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="6a815-177">输入下列项之一：</span><span class="sxs-lookup"><span data-stu-id="6a815-177">Enter one of the following:</span></span>

- <span data-ttu-id="6a815-178">包含 PSCredential 对象的变量。</span><span class="sxs-lookup"><span data-stu-id="6a815-178">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="6a815-179">用于获取 PSCredential 对象的命令，例如 `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="6a815-179">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="6a815-180">如果未设置此选项，则不能指定任何凭据。</span><span class="sxs-lookup"><span data-stu-id="6a815-180">If this option is not set, then you cannot specify any credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-181">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="6a815-181">-ProxyType</span></span>

<span data-ttu-id="6a815-182">指定要使用的主机名解析机制。</span><span class="sxs-lookup"><span data-stu-id="6a815-182">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="6a815-183">此参数的可接受值为： **None**、 **WinHttp**、 **Auto** 或 **microsoft-windows-ie-internetexplorer**。</span><span class="sxs-lookup"><span data-stu-id="6a815-183">The acceptable values for this parameter are: **None**, **WinHttp**, **Auto**, or **InternetExplorer**.</span></span>

<span data-ttu-id="6a815-184">此参数的默认值为 **microsoft-windows-ie-internetexplorer**。</span><span class="sxs-lookup"><span data-stu-id="6a815-184">The default value of this parameter is **InternetExplorer**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-185">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="6a815-185">-SkipCACheck</span></span>

<span data-ttu-id="6a815-186">指示当通过 HTTPS 进行连接时，客户端不会验证服务器证书是否由受信任的证书颁发机构签名 (CA) 。</span><span class="sxs-lookup"><span data-stu-id="6a815-186">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="6a815-187">仅在使用其他机制信任远程计算机时（例如，当远程计算机是物理安全和隔离的网络的一部分，或者当远程计算机在 WinRM 配置中列为受信任的主机时）才使用此参数。</span><span class="sxs-lookup"><span data-stu-id="6a815-187">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-188">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="6a815-188">-SkipCNCheck</span></span>

<span data-ttu-id="6a815-189">指示服务器 (CN) 的证书公用名无需与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="6a815-189">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="6a815-190">此参数仅适用于使用 HTTPS 协议的受信任计算机的远程操作。</span><span class="sxs-lookup"><span data-stu-id="6a815-190">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-191">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="6a815-191">-SkipRevocationCheck</span></span>

<span data-ttu-id="6a815-192">指示跳过对服务器证书的吊销检查。</span><span class="sxs-lookup"><span data-stu-id="6a815-192">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="6a815-193">仅对受信任的计算机使用此参数。</span><span class="sxs-lookup"><span data-stu-id="6a815-193">Use this parameter only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-194">-UICulture</span><span class="sxs-lookup"><span data-stu-id="6a815-194">-UICulture</span></span>

<span data-ttu-id="6a815-195">指定要用于 CIM 会话的用户界面区域性。</span><span class="sxs-lookup"><span data-stu-id="6a815-195">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="6a815-196">使用以下格式之一指定此参数的值：</span><span class="sxs-lookup"><span data-stu-id="6a815-196">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="6a815-197">格式为的区域性名称 `<languagecode2>-<country/regioncode2>` ，如 "en-us"。</span><span class="sxs-lookup"><span data-stu-id="6a815-197">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="6a815-198">包含 CultureInfo 对象的变量。</span><span class="sxs-lookup"><span data-stu-id="6a815-198">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="6a815-199">用于获取 CultureInfo 对象的命令，例如 `Get-Culture` 。</span><span class="sxs-lookup"><span data-stu-id="6a815-199">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-200">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="6a815-200">-UseSsl</span></span>

<span data-ttu-id="6a815-201">指示应使用 SSL 建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="6a815-201">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="6a815-202">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="6a815-202">By default, SSL is not used.</span></span> <span data-ttu-id="6a815-203">WsMan 会对通过网络传输的所有内容进行加密，即使在使用 HTTP 时也是如此。</span><span class="sxs-lookup"><span data-stu-id="6a815-203">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="6a815-204">此参数可用于指定对 HTTPS （而非 HTTP）的额外保护。</span><span class="sxs-lookup"><span data-stu-id="6a815-204">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="6a815-205">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="6a815-205">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="6a815-206">建议仅在未指定 **PacketPrivacy** 参数时使用此参数。</span><span class="sxs-lookup"><span data-stu-id="6a815-206">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a815-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a815-207">CommonParameters</span></span>

<span data-ttu-id="6a815-208">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6a815-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a815-209">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6a815-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a815-210">输入</span><span class="sxs-lookup"><span data-stu-id="6a815-210">INPUTS</span></span>

### <span data-ttu-id="6a815-211">无</span><span class="sxs-lookup"><span data-stu-id="6a815-211">None</span></span>

<span data-ttu-id="6a815-212">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="6a815-212">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="6a815-213">输出</span><span class="sxs-lookup"><span data-stu-id="6a815-213">OUTPUTS</span></span>

### <span data-ttu-id="6a815-214">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="6a815-214">CIMSessionOption</span></span>

<span data-ttu-id="6a815-215">此 cmdlet 将返回包含 CIM 会话选项信息的对象。</span><span class="sxs-lookup"><span data-stu-id="6a815-215">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="6a815-216">注释</span><span class="sxs-lookup"><span data-stu-id="6a815-216">NOTES</span></span>

## <span data-ttu-id="6a815-217">相关链接</span><span class="sxs-lookup"><span data-stu-id="6a815-217">RELATED LINKS</span></span>

[<span data-ttu-id="6a815-218">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="6a815-218">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="6a815-219">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="6a815-219">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="6a815-220">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="6a815-220">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="6a815-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="6a815-221">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="6a815-222">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="6a815-222">New-CimSession</span></span>](New-CimSession.md)

