---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 00680a466c9cc9dd719fbce3d66f4eb10ec47860
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597845"
---
# <span data-ttu-id="606ba-102">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="606ba-102">Get-WSManInstance</span></span>

## <span data-ttu-id="606ba-103">摘要</span><span class="sxs-lookup"><span data-stu-id="606ba-103">SYNOPSIS</span></span>
<span data-ttu-id="606ba-104">显示由资源 URI 指定的资源实例的管理信息。</span><span class="sxs-lookup"><span data-stu-id="606ba-104">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="606ba-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="606ba-105">SYNTAX</span></span>

### <span data-ttu-id="606ba-106">GetInstance (默认值) </span><span class="sxs-lookup"><span data-stu-id="606ba-106">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="606ba-107">枚举</span><span class="sxs-lookup"><span data-stu-id="606ba-107">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="606ba-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="606ba-108">DESCRIPTION</span></span>
<span data-ttu-id="606ba-109">**Get-wsmaninstance** cmdlet 可检索由资源统一资源标识符 (URI) 指定的管理资源的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-109">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="606ba-110">检索到的信息可以是一个复杂的 XML 信息集，也可以是一个对象，也可以是一个简单值。</span><span class="sxs-lookup"><span data-stu-id="606ba-110">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="606ba-111">此 cmdlet 等效于用于管理的标准 Web 服务 (WS-MANAGEMENT) **Get** 命令。</span><span class="sxs-lookup"><span data-stu-id="606ba-111">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="606ba-112">此 cmdlet 使用 WS-Management 连接/传输层来检索信息。</span><span class="sxs-lookup"><span data-stu-id="606ba-112">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="606ba-113">示例</span><span class="sxs-lookup"><span data-stu-id="606ba-113">EXAMPLES</span></span>

### <span data-ttu-id="606ba-114">示例1：获取 WMI 中的所有信息</span><span class="sxs-lookup"><span data-stu-id="606ba-114">Example 1: Get all information from WMI</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

<span data-ttu-id="606ba-115">此命令将返回 Windows Management Instrumentation (WMI) 公开有关远程 server01 计算机上的 **WinRM** 服务的所有信息。</span><span class="sxs-lookup"><span data-stu-id="606ba-115">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="606ba-116">示例2：获取后台处理程序服务的状态</span><span class="sxs-lookup"><span data-stu-id="606ba-116">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="606ba-117">此命令仅返回远程 server01 计算机上的 **后台处理程序** 服务的状态。</span><span class="sxs-lookup"><span data-stu-id="606ba-117">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="606ba-118">示例3：获取所有服务的终结点引用</span><span class="sxs-lookup"><span data-stu-id="606ba-118">Example 3: Get endpoint references for all services</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="606ba-119">此命令将返回对应于本地计算机上的所有服务的终结点引用。</span><span class="sxs-lookup"><span data-stu-id="606ba-119">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="606ba-120">示例4：获取满足指定条件的服务</span><span class="sxs-lookup"><span data-stu-id="606ba-120">Example 4: Get services that meet specified criteria</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="606ba-121">此命令列出了远程 Server01 计算机上满足以下条件的所有服务：</span><span class="sxs-lookup"><span data-stu-id="606ba-121">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="606ba-122">服务的启动类型为 "自动"。</span><span class="sxs-lookup"><span data-stu-id="606ba-122">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="606ba-123">服务已停止。</span><span class="sxs-lookup"><span data-stu-id="606ba-123">The service is stopped.</span></span>

### <span data-ttu-id="606ba-124">示例5：获取与本地计算机上的条件匹配的侦听器配置</span><span class="sxs-lookup"><span data-stu-id="606ba-124">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

<span data-ttu-id="606ba-125">此命令列出本地计算机上与选择器集中的条件相符的侦听器的 WS-Management 侦听器配置。</span><span class="sxs-lookup"><span data-stu-id="606ba-125">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="606ba-126">示例6：获取与远程计算机上的条件匹配的侦听器配置</span><span class="sxs-lookup"><span data-stu-id="606ba-126">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

<span data-ttu-id="606ba-127">此命令列出 server01 远程计算机上与选择器集中的条件相符的侦听器的 WS-Management 侦听器配置。</span><span class="sxs-lookup"><span data-stu-id="606ba-127">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="606ba-128">示例7：获取与指定实例相关的关联实例</span><span class="sxs-lookup"><span data-stu-id="606ba-128">Example 7: Get associated instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

<span data-ttu-id="606ba-129">此命令获取与指定实例 (winrm) 相关的关联的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-129">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="606ba-130">你必须将筛选器用引号括起来，如该示例中所示。</span><span class="sxs-lookup"><span data-stu-id="606ba-130">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="606ba-131">示例8：获取与指定实例相关的关联实例</span><span class="sxs-lookup"><span data-stu-id="606ba-131">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="606ba-132">此命令获取与指定实例 (winrm) 相关的关联实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-132">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="606ba-133">由于 *方言* 值是关联的，并且使用了 *association* 参数，因此此命令将返回关联实例，而不是关联的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-133">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="606ba-134">你必须将筛选器用引号括起来，如该示例中所示。</span><span class="sxs-lookup"><span data-stu-id="606ba-134">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="606ba-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="606ba-135">PARAMETERS</span></span>

### <span data-ttu-id="606ba-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="606ba-136">-ApplicationName</span></span>
<span data-ttu-id="606ba-137">指定连接中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="606ba-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="606ba-138">*ApplicationName* 参数的默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="606ba-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="606ba-139">远程终结点的完整标识符采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="606ba-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="606ba-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="606ba-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="606ba-141">例如： `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="606ba-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="606ba-142">托管该会话的 Internet Information Services (IIS) 将带有此终结点的请求转发到指定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="606ba-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="606ba-143">默认设置 WSMAN 适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="606ba-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="606ba-144">如果许多计算机建立了与运行 PowerShell 的一台计算机的远程连接，则可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="606ba-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="606ba-145">在这种情况下，IIS 将 WS-Management 的效率。</span><span class="sxs-lookup"><span data-stu-id="606ba-145">In this case, IIS hosts WS-Management for efficiency.</span></span>

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

### <span data-ttu-id="606ba-146">-关联</span><span class="sxs-lookup"><span data-stu-id="606ba-146">-Associations</span></span>
<span data-ttu-id="606ba-147">指示此 cmdlet 获取关联实例，而不是关联的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-147">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="606ba-148">仅当 *方言* 参数具有值 Association 时，才能使用此参数。</span><span class="sxs-lookup"><span data-stu-id="606ba-148">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-149">-Authentication</span><span class="sxs-lookup"><span data-stu-id="606ba-149">-Authentication</span></span>
<span data-ttu-id="606ba-150">指定服务器上要使用的身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="606ba-150">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="606ba-151">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="606ba-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="606ba-152">基本。</span><span class="sxs-lookup"><span data-stu-id="606ba-152">Basic.</span></span>
<span data-ttu-id="606ba-153">Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。</span><span class="sxs-lookup"><span data-stu-id="606ba-153">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="606ba-154">默认。</span><span class="sxs-lookup"><span data-stu-id="606ba-154">Default.</span></span>
<span data-ttu-id="606ba-155">使用由 WS-Management 协议实现的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="606ba-155">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="606ba-156">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="606ba-156">This is the default.</span></span>
- <span data-ttu-id="606ba-157">摘要。</span><span class="sxs-lookup"><span data-stu-id="606ba-157">Digest.</span></span>
<span data-ttu-id="606ba-158">Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。</span><span class="sxs-lookup"><span data-stu-id="606ba-158">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="606ba-159">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="606ba-159">Kerberos.</span></span>
<span data-ttu-id="606ba-160">客户端计算机和服务器通过使用 Kerberos 证书相互进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="606ba-160">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="606ba-161">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="606ba-161">Negotiate.</span></span>
<span data-ttu-id="606ba-162">Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。</span><span class="sxs-lookup"><span data-stu-id="606ba-162">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="606ba-163">例如，此参数值允许协商以确定是使用 Kerberos 协议还是 NTLM。</span><span class="sxs-lookup"><span data-stu-id="606ba-163">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="606ba-164">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="606ba-164">CredSSP.</span></span>
<span data-ttu-id="606ba-165">使用凭据安全支持提供程序 (CredSSP) 身份验证，可允许用户委派凭据。</span><span class="sxs-lookup"><span data-stu-id="606ba-165">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="606ba-166">此选项专门用于这样的命令：在一台远程计算机上运行，但从其他远程计算机收集数据或在其他远程计算机上运行其他命令。</span><span class="sxs-lookup"><span data-stu-id="606ba-166">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="606ba-167">注意：CredSSP 将用户凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="606ba-167">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="606ba-168">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="606ba-168">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="606ba-169">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="606ba-169">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="606ba-170">-BasePropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="606ba-170">-BasePropertiesOnly</span></span>
<span data-ttu-id="606ba-171">指示此 cmdlet 仅枚举属于由 *ResourceURI* 参数指定的基类的属性。</span><span class="sxs-lookup"><span data-stu-id="606ba-171">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="606ba-172">如果指定了 *浅层* 参数，则此参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="606ba-172">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-173">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="606ba-173">-CertificateThumbprint</span></span>
<span data-ttu-id="606ba-174">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="606ba-174">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="606ba-175">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="606ba-175">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="606ba-176">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="606ba-176">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="606ba-177">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="606ba-177">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="606ba-178">若要获取证书指纹，请使用 PowerShell Cert：驱动器中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="606ba-178">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="606ba-179">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="606ba-179">-ComputerName</span></span>
<span data-ttu-id="606ba-180">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="606ba-180">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="606ba-181">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="606ba-181">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="606ba-182">使用本地计算机名称、localhost 或点 (.) 指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="606ba-182">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="606ba-183">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="606ba-183">The local computer is the default.</span></span>
<span data-ttu-id="606ba-184">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="606ba-184">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="606ba-185">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="606ba-185">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-186">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="606ba-186">-ConnectionURI</span></span>
<span data-ttu-id="606ba-187">指定连接终结点。</span><span class="sxs-lookup"><span data-stu-id="606ba-187">Specifies the connection endpoint.</span></span>
<span data-ttu-id="606ba-188">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="606ba-188">The format of this string is as follows:</span></span>

<span data-ttu-id="606ba-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="606ba-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="606ba-190">以下字符串是此参数的格式正确的值：</span><span class="sxs-lookup"><span data-stu-id="606ba-190">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="606ba-191">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="606ba-191">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-192">-Credential</span><span class="sxs-lookup"><span data-stu-id="606ba-192">-Credential</span></span>
<span data-ttu-id="606ba-193">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="606ba-193">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="606ba-194">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="606ba-194">The default is the current user.</span></span>
<span data-ttu-id="606ba-195">键入用户名，如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="606ba-195">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="606ba-196">或者输入一个 PSCredential 对象，例如 Get-Credential cmdlet 返回的一个 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="606ba-196">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="606ba-197">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="606ba-197">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="606ba-198">-Dialect</span><span class="sxs-lookup"><span data-stu-id="606ba-198">-Dialect</span></span>
<span data-ttu-id="606ba-199">指定要在筛选器谓词中使用的方言。</span><span class="sxs-lookup"><span data-stu-id="606ba-199">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="606ba-200">这可以是远程服务支持的任何方言。</span><span class="sxs-lookup"><span data-stu-id="606ba-200">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="606ba-201">以下别名可用于方言 URI：</span><span class="sxs-lookup"><span data-stu-id="606ba-201">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="606ba-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="606ba-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="606ba-203">选取 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="606ba-203">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="606ba-204">关联 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="606ba-204">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

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

### <span data-ttu-id="606ba-205">-枚举</span><span class="sxs-lookup"><span data-stu-id="606ba-205">-Enumerate</span></span>
<span data-ttu-id="606ba-206">指示此 cmdlet 返回管理资源的所有实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-206">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-207">-Filter</span><span class="sxs-lookup"><span data-stu-id="606ba-207">-Filter</span></span>
<span data-ttu-id="606ba-208">指定枚举的筛选器表达式。</span><span class="sxs-lookup"><span data-stu-id="606ba-208">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="606ba-209">如果指定此参数，则还必须指定 *方言*。</span><span class="sxs-lookup"><span data-stu-id="606ba-209">If you specify this parameter, you must also specify *Dialect*.</span></span>

<span data-ttu-id="606ba-210">此参数的有效值取决于 *方言* 中指定的方言。</span><span class="sxs-lookup"><span data-stu-id="606ba-210">The valid values of this parameter depend on the dialect that is specified in *Dialect*.</span></span>
<span data-ttu-id="606ba-211">例如，如果 *方言* 为 WQL，则 *Filter* 参数必须包含一个字符串，并且该字符串必须包含一个有效的 WQL 查询，例如以下查询：</span><span class="sxs-lookup"><span data-stu-id="606ba-211">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="606ba-212">如果 *方言* 是关联的，则 *Filter* 必须包含一个字符串，并且该字符串必须包含一个有效的筛选器，例如以下筛选器：</span><span class="sxs-lookup"><span data-stu-id="606ba-212">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-213">-Fragment</span><span class="sxs-lookup"><span data-stu-id="606ba-213">-Fragment</span></span>
<span data-ttu-id="606ba-214">指定实例内要针对指定操作更新或检索的部分。</span><span class="sxs-lookup"><span data-stu-id="606ba-214">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="606ba-215">例如，若要获取后台处理程序服务的状态，请指定以下各项：</span><span class="sxs-lookup"><span data-stu-id="606ba-215">For example, to get the status of a spooler service, specify the following:</span></span>

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-216">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="606ba-216">-OptionSet</span></span>
<span data-ttu-id="606ba-217">将一组开关指定到某个服务以修改或优化请求的性质。</span><span class="sxs-lookup"><span data-stu-id="606ba-217">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="606ba-218">这些开关类似于命令行 shell 中使用的开关，因为它们也特定于服务。</span><span class="sxs-lookup"><span data-stu-id="606ba-218">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="606ba-219">可以指定任何数量的选项。</span><span class="sxs-lookup"><span data-stu-id="606ba-219">Any number of options can be specified.</span></span>

<span data-ttu-id="606ba-220">以下示例演示为 a、b 和 c 参数传递值 1、2 和 3 的语法：</span><span class="sxs-lookup"><span data-stu-id="606ba-220">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-221">-Port</span><span class="sxs-lookup"><span data-stu-id="606ba-221">-Port</span></span>
<span data-ttu-id="606ba-222">指定要在客户端连接到 WinRM 服务时使用的端口。</span><span class="sxs-lookup"><span data-stu-id="606ba-222">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="606ba-223">当传输为 HTTP 时，默认端口为 80。</span><span class="sxs-lookup"><span data-stu-id="606ba-223">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="606ba-224">当传输为 HTTPS 时，默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="606ba-224">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="606ba-225">使用 HTTPS 作为传输协议时， *ComputerName* 参数的值必须与服务器的证书公用名 (CN) 相匹配。</span><span class="sxs-lookup"><span data-stu-id="606ba-225">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="606ba-226">但是，如果将 SkipCNCheck 参数指定为 SessionOption 参数的一部分，则服务器的证书公用名无需与服务器的主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="606ba-226">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="606ba-227">SkipCNCheck 参数应仅用于受信任的计算机。</span><span class="sxs-lookup"><span data-stu-id="606ba-227">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="606ba-228">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="606ba-228">-ResourceURI</span></span>
<span data-ttu-id="606ba-229">指定资源类或实例的 URI。</span><span class="sxs-lookup"><span data-stu-id="606ba-229">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="606ba-230">URI 标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="606ba-230">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="606ba-231">URI 由资源的前缀和路径组成。</span><span class="sxs-lookup"><span data-stu-id="606ba-231">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="606ba-232">例如：</span><span class="sxs-lookup"><span data-stu-id="606ba-232">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-233">-ReturnType</span><span class="sxs-lookup"><span data-stu-id="606ba-233">-ReturnType</span></span>
<span data-ttu-id="606ba-234">指定要返回的数据类型。</span><span class="sxs-lookup"><span data-stu-id="606ba-234">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="606ba-235">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="606ba-235">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="606ba-236">对象</span><span class="sxs-lookup"><span data-stu-id="606ba-236">Object</span></span>
- <span data-ttu-id="606ba-237">EPR</span><span class="sxs-lookup"><span data-stu-id="606ba-237">EPR</span></span>
- <span data-ttu-id="606ba-238">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="606ba-238">ObjectAndEPR</span></span>

<span data-ttu-id="606ba-239">默认值为 "Object"。</span><span class="sxs-lookup"><span data-stu-id="606ba-239">The default value is Object.</span></span>

<span data-ttu-id="606ba-240">如果指定 Object 或未指定此参数，则此 cmdlet 仅返回对象。</span><span class="sxs-lookup"><span data-stu-id="606ba-240">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="606ba-241">如果 (EPR 指定终结点引用) 则此 cmdlet 仅返回对象的终结点引用。</span><span class="sxs-lookup"><span data-stu-id="606ba-241">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="606ba-242">终结点引用包含有关实例的资源 URI 和选择器的信息。</span><span class="sxs-lookup"><span data-stu-id="606ba-242">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="606ba-243">如果指定 ObjectAndEPR，则此 cmdlet 将返回对象及其关联的终结点引用。</span><span class="sxs-lookup"><span data-stu-id="606ba-243">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-244">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="606ba-244">-SelectorSet</span></span>
<span data-ttu-id="606ba-245">指定一组用于选择特定管理资源实例的值对。</span><span class="sxs-lookup"><span data-stu-id="606ba-245">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="606ba-246">当存在多个资源实例时，将使用 *SelectorSet* 参数。</span><span class="sxs-lookup"><span data-stu-id="606ba-246">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="606ba-247">*SelectorSet* 参数的值必须为哈希表。</span><span class="sxs-lookup"><span data-stu-id="606ba-247">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="606ba-248">以下示例显示如何为此参数输入值：</span><span class="sxs-lookup"><span data-stu-id="606ba-248">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-249">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="606ba-249">-SessionOption</span></span>
<span data-ttu-id="606ba-250">为 WS-Management 会话指定扩展选项。</span><span class="sxs-lookup"><span data-stu-id="606ba-250">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="606ba-251">输入使用 New-WSManSessionOption cmdlet 创建的 **SessionOption** 对象。</span><span class="sxs-lookup"><span data-stu-id="606ba-251">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="606ba-252">有关可用选项的详细信息，请键入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="606ba-252">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-253">-浅</span><span class="sxs-lookup"><span data-stu-id="606ba-253">-Shallow</span></span>
<span data-ttu-id="606ba-254">指示此 cmdlet 仅返回资源 URI 中指定的基类的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-254">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="606ba-255">如果未指定此参数，则此 cmdlet 将返回在 URI 及其所有派生类中指定的基类的实例。</span><span class="sxs-lookup"><span data-stu-id="606ba-255">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-256">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="606ba-256">-UseSSL</span></span>
<span data-ttu-id="606ba-257">指定使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="606ba-257">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="606ba-258">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="606ba-258">By default, SSL is not used.</span></span>

<span data-ttu-id="606ba-259">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="606ba-259">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="606ba-260">*UseSSL* 参数允许你指定 HTTPS 的额外保护，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="606ba-260">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="606ba-261">如果 SSL 在用于连接的端口上不可用，并且指定了此参数，则命令将失败。</span><span class="sxs-lookup"><span data-stu-id="606ba-261">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="606ba-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="606ba-262">CommonParameters</span></span>
<span data-ttu-id="606ba-263">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="606ba-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="606ba-264">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="606ba-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="606ba-265">输入</span><span class="sxs-lookup"><span data-stu-id="606ba-265">INPUTS</span></span>

### <span data-ttu-id="606ba-266">无</span><span class="sxs-lookup"><span data-stu-id="606ba-266">None</span></span>
<span data-ttu-id="606ba-267">此命令不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="606ba-267">This command does not accept any input.</span></span>

## <span data-ttu-id="606ba-268">输出</span><span class="sxs-lookup"><span data-stu-id="606ba-268">OUTPUTS</span></span>

### <span data-ttu-id="606ba-269">System.Xml.XmlElement</span><span class="sxs-lookup"><span data-stu-id="606ba-269">System.Xml.XmlElement</span></span>
<span data-ttu-id="606ba-270">此 cmdlet 将生成一个 **XMLElement** 对象。</span><span class="sxs-lookup"><span data-stu-id="606ba-270">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="606ba-271">注释</span><span class="sxs-lookup"><span data-stu-id="606ba-271">NOTES</span></span>

## <span data-ttu-id="606ba-272">相关链接</span><span class="sxs-lookup"><span data-stu-id="606ba-272">RELATED LINKS</span></span>

[<span data-ttu-id="606ba-273">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="606ba-273">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="606ba-274">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="606ba-274">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="606ba-275">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="606ba-275">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="606ba-276">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="606ba-276">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="606ba-277">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="606ba-277">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="606ba-278">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="606ba-278">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="606ba-279">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="606ba-279">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="606ba-280">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="606ba-280">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="606ba-281">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="606ba-281">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="606ba-282">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="606ba-282">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="606ba-283">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="606ba-283">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="606ba-284">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="606ba-284">Test-WSMan</span></span>](Test-WSMan.md)

