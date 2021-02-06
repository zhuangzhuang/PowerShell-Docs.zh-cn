---
description: 概述了用于管理的 Web 服务 (WS-MANAGEMENT) 作为使用 Windows PowerShell 中 WS-Management cmdlet 的背景。
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: faf0f0b08d604f7568ac316557788eea21feea8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595637"
---
# <a name="about-ws-management-cmdlets"></a>关于 WS-Management Cmdlet

## <a name="short-description"></a>简短说明

概述了用于管理的 Web 服务 (WS-MANAGEMENT) 作为使用 Windows PowerShell 中 WS-Management cmdlet 的背景。

## <a name="long-description"></a>详细说明

本主题概述了用于管理的 Web 服务 (WS-MANAGEMENT) 作为使用 Windows PowerShell 中 WS-Management cmdlet 的背景。 本主题还提供了有关 WS-MANAGEMENT 的详细信息的链接。 WS-Management 的 Microsoft 实现也称为 (WinRM) Windows 远程管理。

## <a name="about-ws-management"></a>关于 WS-Management

Windows 远程管理是 WS-Management 协议的 Microsoft 实现，它是一种基于 SOAP 的标准、防火墙友好的协议，它允许不同供应商的硬件和操作系统互操作。 WS-Management 协议规范为系统提供了一种通用的方法来访问和交换信息技术) 基础结构 (的管理信息。 WS-Management 和智能平台管理接口 (IPMI) 和事件收集器都是 Windows 硬件管理功能的组成部分。

WS-Management 协议基于以下标准 Web 服务规范： HTTPS、SOAP over HTTP (WS-I profile) 、SOAP 1.2、WS-ADDRESSING、WS 传输、WS 枚举和 WS-EVENTING。

## <a name="ws-management-and-wmi"></a>WS-Management 和 WMI

WS-Management 可用于检索由 Windows Management Instrumentation (WMI) 公开的数据。 可以使用脚本或使用 WS-Management 脚本编写 API 的应用程序或 WinRM 命令行工具获取 WMI 数据。 WS-Management 支持大多数常见的 WMI 类和操作（包括嵌入对象）。 WS-Management 可以利用 WMI 收集有关资源的数据，或在基于 Windows 的计算机上管理资源。 这意味着你可以通过现有的 WMI 类集来获取有关企业中的磁盘、网络适配器、服务或进程的数据。 你还可以访问标准 WMI IPMI 提供商提供的硬件数据。

## <a name="ws-management-windows-powershell-provider-wsman"></a>WS-Management Windows PowerShell 提供程序 (WSMan) 

WSMan 提供程序为可用 WS-Management 配置设置提供了层次结构视图。 提供程序允许您浏览和设置不同的 WS-Management 配置选项。

## <a name="ws-management-configuration"></a>WS-Management 配置

如果未安装和配置 WS-Management，则无法使用 Windows PowerShell 远程处理，WS-Management cmdlet 将不会运行，WS-Management 脚本不会运行，并且 WSMan 提供程序无法执行数据操作。 WS-Management 命令行工具、WinRM 和事件转发也依赖于 WS-Management 配置。

## <a name="ws-management-cmdlets"></a>WS-Management Cmdlet

WS-Management 功能是在 Windows PowerShell 中通过包含一组 cmdlet 和 WSMan 提供程序的模块实现的。 你可以使用这些 cmdlet 来完成管理本地和远程计算机上 WS-Management 设置所需的端到端任务。

以下 WS-Management cmdlet 可用。

## <a name="connection-cmdlets"></a>连接 Cmdlet

- Connect-WSMan：将本地计算机连接到远程计算机上的 WS-Management (WinRM) 服务。

- 断开连接-WSMan：将本地计算机从远程计算机上的 WS-Management (WinRM) 服务断开连接。

## <a name="management-data-cmdlets"></a>Management-Data Cmdlet

- Get-wsmaninstance：显示由资源 URI 指定的资源实例的管理信息。

- Invoke-wsmanaction：对由资源 URI 和选择器指定的目标对象调用操作。

- Get-wsmaninstance：创建新的管理资源实例。

- Get-wsmaninstance：删除管理资源实例。

- Get-wsmaninstance：修改与资源相关的管理信息。

## <a name="setup-and-configuration-cmdlets"></a>安装和配置 Cmdlet

- Set-wsmanquickconfig：配置本地计算机以进行远程管理。
  你可以使用 Set-WSManQuickConfig cmdlet 配置 WS-Management，以允许 WS-Management (WinRM) 服务的远程连接。 Set-WSManQuickConfig cmdlet 执行以下操作：
  - 它确定 WS-Management (WinRM) 服务是否正在运行。 如果 WinRM 服务未运行，则 Set-WSManQuickConfig cmdlet 将启动该服务。
  - 它将 WS-Management (WinRM) 服务启动类型设置为 "自动"。
  - 它将创建接受来自任何 IP 地址的请求的侦听器。 默认传输协议为 HTTP。
  - 它为 WS-Management 流量启用防火墙例外。

  注意：若要在 Windows Vista、Windows Server 2008 和更高版本的 Windows 中运行此 cmdlet，必须用 "以管理员身份运行" 选项启动 Windows PowerShell。

- 测试-WSMan：验证是否安装并配置了 WS-Management。 Test-WSMan cmdlet 测试 WS-Management (WinRM) 服务是否正在本地或远程计算机上运行和配置。

- Enable-wsmancredssp：禁用客户端计算机上的 CredSSP 身份验证。

- Enable-wsmancredssp：在客户端计算机上启用 CredSSP 身份验证。

- Enable-wsmancredssp：获取客户端计算机的 CredSSP 相关配置。

## <a name="ws-management-specific-cmdlets"></a>WS-MANAGEMENT 特定的 Cmdlet

- New-wsmansessionoption：创建 New-wsmansessionoption 对象，该对象用作 WS-Management cmdlet 的一个或多个参数的输入。

## <a name="additional-ws-management-information"></a>其他 WS-Management 信息

有关 WS-MANAGEMENT 的详细信息，请参阅 Windows 文档中的以下主题。

[Windows 远程管理](/windows/win32/winrm/portal)

[关于 Windows 远程管理](/windows/win32/winrm/about-windows-remote-management)

[Windows 远程管理的安装和配置](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Windows 远程管理体系结构](/windows/win32/winrm/windows-remote-management-architecture)

[WS-Management 协议](/windows/win32/winrm/ws-management-protocol)

[Windows 远程管理和 WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[资源 URI](/windows/win32/winrm/resource-uris)

[远程硬件管理](/windows/win32/winrm/remote-hardware-management)

[事件](/windows/win32/winrm/events)

## <a name="see-also"></a>另请参阅

[Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Disconnect-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Enable-WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Test-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
