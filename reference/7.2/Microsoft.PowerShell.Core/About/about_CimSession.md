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
# <a name="about-cimsession"></a><span data-ttu-id="b321f-103">关于 CimSession</span><span class="sxs-lookup"><span data-stu-id="b321f-103">About CimSession</span></span>

## <a name="short-description"></a><span data-ttu-id="b321f-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="b321f-104">Short description</span></span>
<span data-ttu-id="b321f-105">描述 **CimSession** 对象以及 CIM 会话与 PowerShell 会话之间的差异。</span><span class="sxs-lookup"><span data-stu-id="b321f-105">Describes a **CimSession** object and the difference between CIM sessions and PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b321f-106">长说明</span><span class="sxs-lookup"><span data-stu-id="b321f-106">Long description</span></span>

<span data-ttu-id="b321f-107"> (CIM) 会话通用信息模型是表示与本地计算机或远程计算机的连接的客户端对象。</span><span class="sxs-lookup"><span data-stu-id="b321f-107">A Common Information Model (CIM) session is a client-side object that represents a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="b321f-108">可以使用 CIM 会话作为 PowerShell 会话 (Pssession) 的替代方法。</span><span class="sxs-lookup"><span data-stu-id="b321f-108">You can use CIM sessions as an alternative to PowerShell sessions (PSSessions).</span></span> <span data-ttu-id="b321f-109">这两种方法都具有优势。</span><span class="sxs-lookup"><span data-stu-id="b321f-109">Both approaches have advantages.</span></span>

<span data-ttu-id="b321f-110">可以使用 `New-CimSession` cmdlet 创建一个 CIM 会话，其中包含有关连接的信息，例如计算机名称、用于连接的协议、会话 id 和实例 id。</span><span class="sxs-lookup"><span data-stu-id="b321f-110">You can use the `New-CimSession` cmdlet to create a CIM session that contains information about a connection, such as computer name, the protocol used for the connection, session ID, and instance ID.</span></span>

<span data-ttu-id="b321f-111">创建指定建立连接所需信息的 **CimSession** 对象后，PowerShell 不会立即建立连接。</span><span class="sxs-lookup"><span data-stu-id="b321f-111">After you create a **CimSession** object that specifies information required to establish a connection, PowerShell does not establish the connection immediately.</span></span> <span data-ttu-id="b321f-112">当 cmdlet 使用 CIM 会话时，PowerShell 会连接到指定的计算机，然后在该 cmdlet 完成后，PowerShell 将终止连接。</span><span class="sxs-lookup"><span data-stu-id="b321f-112">When a cmdlet uses the CIM session, PowerShell connects to the specified computer, and then, when the cmdlet finishes, PowerShell terminates the connection.</span></span>

<span data-ttu-id="b321f-113">如果创建的是 **PSSession** 而不是使用 CIM 会话，则 PowerShell 将验证连接设置，然后建立并维护连接。</span><span class="sxs-lookup"><span data-stu-id="b321f-113">If you create a **PSSession** instead of using a CIM session, PowerShell validates connection settings, and then establishes and maintains the connection.</span></span> <span data-ttu-id="b321f-114">如果使用 CIM 会话，则在需要时，PowerShell 不会打开网络连接。</span><span class="sxs-lookup"><span data-stu-id="b321f-114">If you use CIM sessions, PowerShell does not open a network connection until needed.</span></span> <span data-ttu-id="b321f-115">有关 PowerShell 会话的详细信息，请参阅 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="b321f-115">For more information about PowerShell sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="when-to-use-a-cim-session"></a><span data-ttu-id="b321f-116">何时使用 CIM 会话</span><span class="sxs-lookup"><span data-stu-id="b321f-116">When to use a CIM session</span></span>

<span data-ttu-id="b321f-117">只有处理 Windows Management Instrumentation (WMI) 提供程序或 WS-Man CIM 的 cmdlet 才能接受 CIM 会话。</span><span class="sxs-lookup"><span data-stu-id="b321f-117">Only cmdlets that work with a Windows Management Instrumentation (WMI) provider or CIM over WS-Man accept CIM sessions.</span></span> <span data-ttu-id="b321f-118">对于其他 cmdlet，请使用 **pssession**。</span><span class="sxs-lookup"><span data-stu-id="b321f-118">For other cmdlets, use **PSSessions**.</span></span>

<span data-ttu-id="b321f-119">使用 CIM 会话时，PowerShell 会在本地客户端上运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b321f-119">When you use a CIM session, PowerShell runs the cmdlet on the local client.</span></span> <span data-ttu-id="b321f-120">它使用 CIM 会话连接到 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="b321f-120">It connects to the WMI provider using the CIM session.</span></span> <span data-ttu-id="b321f-121">目标计算机不需要 PowerShell，甚至任何版本的 Windows 操作系统。</span><span class="sxs-lookup"><span data-stu-id="b321f-121">The target computer does not require PowerShell, or even any version of the Windows operating system.</span></span>

<span data-ttu-id="b321f-122">与此相反，cmdlet 在目标计算机 **上运行。**</span><span class="sxs-lookup"><span data-stu-id="b321f-122">In contrast, a cmdlet run using a **PSSession** runs on the target computer.</span></span>
<span data-ttu-id="b321f-123">它需要目标系统上的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b321f-123">It requires PowerShell on the target system.</span></span> <span data-ttu-id="b321f-124">而且，该 cmdlet 会将数据发送回本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b321f-124">Furthermore, the cmdlet sends data back to the local computer.</span></span> <span data-ttu-id="b321f-125">PowerShell 管理通过连接发送的数据，并保留 Windows 远程管理 (WinRM) 设置的限制中的大小。</span><span class="sxs-lookup"><span data-stu-id="b321f-125">PowerShell manages the data sent over the connection, and keeps the size within the limits set by Windows Remote Management (WinRM).</span></span> <span data-ttu-id="b321f-126">CIM 会话不会强制实施 WinRM 限制。</span><span class="sxs-lookup"><span data-stu-id="b321f-126">CIM sessions do not impose the WinRM limits.</span></span>

## <a name="using-cdxml-cmdlets"></a><span data-ttu-id="b321f-127">使用 CDXML cmdlet</span><span class="sxs-lookup"><span data-stu-id="b321f-127">Using CDXML cmdlets</span></span>

<span data-ttu-id="b321f-128">可以编写基于 CIM 的 Cmdlet 定义 XML (CDXML) cmdlet 以使用任意 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="b321f-128">CIM-based Cmdlet Definition XML (CDXML) cmdlets can be written to use any WMI Provider.</span></span> <span data-ttu-id="b321f-129">所有 WMI 提供程序都使用 **CimSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="b321f-129">All WMI providers use **CimSession** objects.</span></span> <span data-ttu-id="b321f-130">有关 CDXML 的详细信息，请参阅 [cdxml 定义和字词](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)。</span><span class="sxs-lookup"><span data-stu-id="b321f-130">For more information about CDXML, see [CDXML definition and terms](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).</span></span>

<span data-ttu-id="b321f-131">CDXML cmdlet 具有可采用 **CimSession** 对象数组的自动 **CimSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="b321f-131">CDXML cmdlets have an automatic **CimSession** parameter that can take an array of **CimSession** objects.</span></span> <span data-ttu-id="b321f-132">默认情况下，PowerShell 将并发 CIM 连接数限制为15。</span><span class="sxs-lookup"><span data-stu-id="b321f-132">By default, PowerShell limits number of concurrent CIM Connections to 15.</span></span> <span data-ttu-id="b321f-133">此限制可由实现 **ThrottleLimit** 的 CDXML cmdlet 重写。</span><span class="sxs-lookup"><span data-stu-id="b321f-133">This limit can be overridden by CDXML cmdlets that implement the **ThrottleLimit**.</span></span> <span data-ttu-id="b321f-134">若要了解 **ThrottleLimit**，请参阅各个 cmdlet 文档。</span><span class="sxs-lookup"><span data-stu-id="b321f-134">See the individual cmdlet documentation to understand the **ThrottleLimit**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b321f-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b321f-135">SEE ALSO</span></span>

[<span data-ttu-id="b321f-136">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="b321f-136">New-CimSession</span></span>](xref:CimCmdlets.New-CimSession)

[<span data-ttu-id="b321f-137">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b321f-137">about_PSSessions</span></span>](about_PSSessions.md)

