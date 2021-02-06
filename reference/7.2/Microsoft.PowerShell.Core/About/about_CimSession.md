---
description: 描述 **CimSession** 对象以及 CIM 会话与 PowerShell 会话之间的差异。
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 556c3db21ea5e410b28f5546cdd8a433e0bc3e50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596853"
---
# <a name="about-cimsession"></a>关于 CimSession

## <a name="short-description"></a>简短说明
描述 **CimSession** 对象以及 CIM 会话与 PowerShell 会话之间的差异。

## <a name="long-description"></a>长说明

 (CIM) 会话通用信息模型是表示与本地计算机或远程计算机的连接的客户端对象。 可以使用 CIM 会话作为 PowerShell 会话 (Pssession) 的替代方法。 这两种方法都具有优势。

可以使用 `New-CimSession` cmdlet 创建一个 CIM 会话，其中包含有关连接的信息，例如计算机名称、用于连接的协议、会话 id 和实例 id。

创建指定建立连接所需信息的 **CimSession** 对象后，PowerShell 不会立即建立连接。 当 cmdlet 使用 CIM 会话时，PowerShell 会连接到指定的计算机，然后在该 cmdlet 完成后，PowerShell 将终止连接。

如果创建的是 **PSSession** 而不是使用 CIM 会话，则 PowerShell 将验证连接设置，然后建立并维护连接。 如果使用 CIM 会话，则在需要时，PowerShell 不会打开网络连接。 有关 PowerShell 会话的详细信息，请参阅 [about_PSSessions](about_PSSessions.md)。

## <a name="when-to-use-a-cim-session"></a>何时使用 CIM 会话

只有处理 Windows Management Instrumentation (WMI) 提供程序或 WS-Man CIM 的 cmdlet 才能接受 CIM 会话。 对于其他 cmdlet，请使用 **pssession**。

使用 CIM 会话时，PowerShell 会在本地客户端上运行 cmdlet。 它使用 CIM 会话连接到 WMI 提供程序。 目标计算机不需要 PowerShell，甚至任何版本的 Windows 操作系统。

与此相反，cmdlet 在目标计算机 **上运行。**
它需要目标系统上的 PowerShell。 而且，该 cmdlet 会将数据发送回本地计算机。 PowerShell 管理通过连接发送的数据，并保留 Windows 远程管理 (WinRM) 设置的限制中的大小。 CIM 会话不会强制实施 WinRM 限制。

## <a name="using-cdxml-cmdlets"></a>使用 CDXML cmdlet

可以编写基于 CIM 的 Cmdlet 定义 XML (CDXML) cmdlet 以使用任意 WMI 提供程序。 所有 WMI 提供程序都使用 **CimSession** 对象。 有关 CDXML 的详细信息，请参阅 [cdxml 定义和字词](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)。

CDXML cmdlet 具有可采用 **CimSession** 对象数组的自动 **CimSession** 参数。 默认情况下，PowerShell 将并发 CIM 连接数限制为15。 此限制可由实现 **ThrottleLimit** 的 CDXML cmdlet 重写。 若要了解 **ThrottleLimit**，请参阅各个 cmdlet 文档。

## <a name="see-also"></a>另请参阅

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)

