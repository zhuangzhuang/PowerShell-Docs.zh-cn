---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 提供程序
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597883"
---
# <a name="wsman-provider"></a>WSMan 提供程序

## <a name="provider-name"></a>提供程序名称

WSMan

## <a name="drives"></a>驱动器

`WSMan:`

## <a name="short-description"></a>简短说明

提供对 Web 服务管理 (WS-Management) 配置信息的访问权限。

## <a name="detailed-description"></a>详细说明

通过用于 PowerShell 的 **WSMan** 提供程序，你可以在本地或远程计算机上添加、更改、清除和删除 WS-Management 配置数据。

**WSMan** 提供程序使用与 WS-Management 配置设置的逻辑分组相对应的目录结构公开 PowerShell 驱动器。 这些分组称为容器。

从 Windows PowerShell 3.0 开始， **WSMan** 提供程序已更新为支持会话配置的新属性，如 **OutputBufferingMode**。 会话配置在驱动器的插件目录中显示为项目 `WSMan:` ，并且属性在每个会话配置中显示为项。

**WSMan** 提供程序支持以下 cmdlet，本文将对此进行介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> 可以使用驱动器中的命令 `WSMan:` 更改新属性的值。 但是，不能使用 `WSMan:` PowerShell 2.0 中的驱动器来更改 Windows powershell 3.0 中引入的属性。
> 尽管不会生成任何错误，但命令对于更改这些设置是无效的，使用 Windows PowerShell 3.0 中的 **WSMan** 驱动器。

### <a name="organization-of-the-wsman-drive"></a>WSMan：驱动器的组织

- **客户端**：你可以配置 WS-Management 客户端的各个方面。 配置信息存储在注册表中。

- **服务**：可以配置 WS-Management 服务的各个方面。
  配置信息存储在注册表中。
  > [!NOTE]
  > 服务配置有时称为服务器配置。

- **Shell**：你可以配置 WS-Management 外壳程序的各个方面，例如允许) 远程 Shell 访问 (**AllowRemoteShellAccess** 和允许的最大并发用户 **数 ()** 。

- **侦听器**：你可以创建和配置侦听器。 侦听器是一项用于实现 WS-Management 协议以发送和接收消息的管理服务。

- **插件**：插件由 WS-Management 服务加载和使用，以提供各种功能。 默认情况下，PowerShell 提供三个插件：
  - 事件转发插件。
  - Microsoft PowerShell 插件。
  -  (WMI) 提供程序插件的 Windows Management Instrumentation。
  这三个插件支持事件转发、配置和 WMI 访问。

- **ClientCertificate**：你可以创建和配置客户端证书。
  当 WS-Management 客户端配置为使用证书身份验证时，将使用客户端证书。

### <a name="directory-hierarchy-of-the-wsman-provider"></a>WSMan 提供程序的目录层次结构

本地计算机的 WSMan 提供程序的目录层次结构如下所示。

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

远程计算机的 WSMan 提供程序的目录层次结构与本地计算机相同。 但是，为了访问远程计算机的配置设置，你需要使用 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan) 建立与远程计算机的连接。 建立与远程计算机的连接后，远程计算机的名称将显示在提供程序中。

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>导航 WSMan：驱动器

此命令使用 `Set-Location` cmdlet 将当前位置更改为 `WSMan:` 驱动器。

```powershell
Set-Location WSMan:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入。

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>导航到远程系统存储位置

此命令使用 `Set-Location` 命令将当前位置更改为远程系统存储位置中的根位置。 使用反斜杠 `\` 或正斜杠 `/` 来指示驱动器的级别 `WSMan:` 。

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> 以上命令假定与远程系统的连接已存在。

## <a name="displaying-the-contents-of-the-wsman-drive"></a>显示 WSMan：驱动器的内容

此命令使用 `Get-Childitem` cmdlet 来显示 Localhost 存储位置中的 WS-Management 存储。

```powershell
Get-ChildItem -path WSMan:\Localhost
```

如果在 `WSMan:` 驱动器中，则可以省略驱动器名称。

此命令使用 `Get-Childitem` cmdlet 来显示远程计算机 "SERVER01" 存储位置中的 WS-Management 存储。

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> 以上命令假定与远程系统的连接已存在。

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>设置 WSMAN：驱动器中的项的值

可以使用 `Set-Item` cmdlet 更改驱动器中的配置设置 `WSMAN` 。 下面的示例将 **TrustedHosts** 值设置为接受后缀为 "contoso.com" 的所有主机。

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

`Set-Item`Cmdlet 支持附加 `-Concatenate` 一个值而不是对其进行更改的附加参数。 下面的示例将一个新值 "* domain2.com" 追加到存储在 `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>在 WSMAN：驱动器中创建项

### <a name="creating-a-new-listener"></a>创建新侦听器

`New-Item`Cmdlet 在提供程序驱动器中创建项。 每个提供程序都具有您可以创建的不同项类型。 在 `WSMAN:` 驱动器中，可以创建可配置为接收和响应远程请求的 *侦听器* 。 以下命令使用 cmdlet 创建新的 HTTP 侦听器 `New-Item` 。

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>创建新插件

此命令将为 WS-Management 服务创建（注册）插件。

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>创建新资源条目

此命令在 TestPlugin 的 Resources 目录中创建资源条目。 此命令假设已使用单独的命令创建了 TestPlugin。

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>为资源创建新的安全条目

此命令将在 Resource_5967683（一种特定资源）的 Security 目录中创建一个安全条目。 此命令假定资源条目是使用单独的命令创建的。

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>创建新的客户端证书

此命令创建 WS-Management 客户端可以使用的 **ClientCertificate** 项。 新的 **ClientCertificate** 将在 **ClientCertificate** 目录下显示为 "ClientCertificate_1234567890"。 所有参数都是必需的。 **颁发者** 必须是颁发者证书的指纹。

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>创建新的初始化参数

此命令在 "InitializationParameters" 目录中创建名为 "testparametername" 的初始化参数。 此命令假设已使用单独的命令创建了 "TestPlugin"。

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。

### <a name="address-string"></a>Address \<String\>

指定已为其创建此侦听器的地址。 值可以是下列任一值：

- 文本字符串 "*"。  (通配符 (`*`) 使命令绑定所有网络适配器上的所有 IP 地址。 ) 
- 文本字符串 "IP：" 后跟采用 IPv4 点分十进制格式或 IPv6 克隆十六进制格式的有效 IP 地址。
- 文本字符串 "MAC：" 后跟适配器的 MAC 地址。
  例如： MAC： 32-a3-58-90。

> [!NOTE]
> 在创建侦听器时设置 Address 值。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Capability \<Enumeration\>

使用 *插件* 时，此参数将指定 (URI) 的统一资源标识符所支持的操作。 你必须为该 URI 支持的每种类型的操作都创建一个条目。 如果操作支持给定操作，则可以为该操作指定任何有效的特性。

这些属性包括 **SupportsFiltering** 和 **SupportsFragment**。

- **Create**： URI 支持创建操作。
  - 如果创建操作支持该概念，则使用 **SupportFragment**  属性。
  - **SupportFiltering** 特性对于 Create 操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **删除**：支持对 URI 执行删除操作。
  - 如果删除操作支持该概念，则使用 **SupportFragment** 属性。
  - **SupportFiltering** 特性对于删除操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **枚举**：在 URI 上支持枚举操作。
  - 枚举操作不支持 **SupportFragment** 属性，并且应将其设置为 False。
  - **SupportFiltering** 属性有效，并且如果插件支持筛选，则应将此属性设置为 "True"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **Get**：对 URI 支持 get 操作。
  - 如果 Get 操作支持该概念，则使用 **SupportFragment** 属性。
  - **SupportFiltering** 特性对于 Get 操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **调用**：对 URI 支持调用操作。
  - 调用操作不支持 **SupportFragment** 属性，并且应将其设置为 False。
  - **SupportFiltering** 特性无效，应将其设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **Put**：对 URI 支持 put 运算。
  - 如果 Put 操作支持该概念，则使用 **SupportFragment** 属性。
  - **SupportFiltering** 特性对于 Put 操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **订阅**： URI 上支持订阅操作。
  - 订阅操作不支持 **SupportFragment** 属性，并且应将其设置为 False。
  - **SupportFiltering** 属性对订阅操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持 Shell 操作，则此操作对于 URI 无效。
- **Shell**： URI 支持 shell 操作。
  - Shell 操作不支持 **SupportFragment** 属性，并且应将其设置为 "False"。
  - **SupportFiltering** 特性对 Shell 操作无效，应设置为 "False"。
  > [!NOTE]
  > 如果还支持任何其他操作，则此操作对于 URI 无效。
  > [!NOTE]
  > 如果为 URI 配置了 Shell 操作，则将在 WS-Management (WinRM) 服务中从内部处理 Get、Put、Create、Delete、Invoke 和 Enumerate 操作，以管理 shell。 因此，插件不能处理这些操作。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

指定服务证书的指纹。

此值表示证书的指纹字段中两位十六进制值的字符串。 它指定有权执行此操作的用户帐户的数字公钥证书 (X509)。 在基于客户端证书的身份验证中使用证书。 证书只能映射到本地用户帐户，而不适用于域帐户。 若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或 cmdlet `Cert:` 。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Enabled \<Boolean\>

指定是启用还是禁用侦听器。 默认值为 True。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>FileName（插件）\<String\>

指定操作插件的文件名。 收到请求时，将在用户的上下文中扩展放置在此项中的任何环境变量。 由于每个用户可能具有相同环境变量的不同版本，因此每个用户都可以具有不同的插件。 此项不能为空，并且必须指向有效的插件。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>HostName \<String\>

指定在其上运行 WS-Management (WinRM) 服务的计算机的主机名。

该值必须是完全限定的域名、IPv4 或 IPv6 文字字符串或通配符。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Issuer \<String\>

指定颁发证书的证书颁发机构名称。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>插件 \<\> WS-Management 插件是 (dll 的本机动态链接库) 

这会插入并扩展 WS-Management 的功能。 WSW-Management 插件 API 提供了一项功能，使用户能够通过针对受支持的资源 Uri 和操作实现某些 Api 来编写插件。 为 WS-Management (WinRM) 服务或 Internet Information Services (IIS) 配置插件后，这些插件将分别在 WS-Management 主机或 IIS 主机中加载。 远程请求会路由到这些插件的入口点以执行操作。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Port \<Unsigned Short Integer\>

指定为其创建此侦听器的 TCP 端口。 你可以指定 1 到 65535 之间的任何值。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

指定表示不同类型的管理操作或值的终结点。 服务将公开一个或多个资源，并且一些资源可以具有多个实例。 管理资源类似于 WMI 类或数据库表，而实例类似于该类的实例或该表中的行。 例如， **Win32_LogicalDisk** 类表示一个资源。 `Win32_LogicalDisk="C:\\"` 是资源的特定实例。

统一资源标识符 (URI) 包含资源的前缀和路径。
例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

指定用于标识计算机上特定类型的资源（例如磁盘或进程）的统一资源标识符 (URI)。

URI 由前缀和指向资源的路径组成。 例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

指定 WS-Management 插件 SDK 的版本。 唯一有效的值是 
1.

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Subject \<String\>

指定由证书标识的实体。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Transport \<String\>

指定要用于发送和接收 WS-Management 协议请求和响应的传输。 该值必须为 HTTP 或 HTTPS。

注意：传输值在创建侦听器时设置。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

标识为其基于 Sddl 参数的值授予访问权限的 URI。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

要在其上接受 HTTP 或 HTTPS 请求的 URL 前缀。 这是一个字符串，其中仅包含字符 `[a-z]` 、 `[A-Z]` 、 `[9-0]` 、下划线 (`_`) 和反斜杠 (`/`) 。 字符串不能以反斜杠开头或结尾 (`/`) 。 例如，如果计算机名称为 "SampleComputer"，则 WS-Management 客户端将 `http://SampleMachine/URLPrefix` 在目标地址中指定。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Value \<String\>

指定初始化参数的值，即一个用于指定配置选项的特定于插件的值。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

指定通过 **WSMAN_DATA** 对象将 XML 传递到插件的格式。 下面是有效的值：

- 文本：传入的 XML 数据包含在 **WSMAN_DATA_TYPE_TEXT** 结构中，该结构将 XML 表示为 **PCWSTR** 内存缓冲区。
- XMLReader：传入的 XML 数据包含在 **WSMAN_DATA_TYPE_WS_XML_READER** 结构中，该结构将 XML 表示为 **XmlReader** 对象，该对象是在 "WebServices" 标头文件中定义的。

#### <a name="cmdlets-supported"></a>支持的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>使用管道

提供程序 cmdlet 接受管道输入。 可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。
若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。

## <a name="getting-help"></a>获取帮助

从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。

若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>请参阅

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

