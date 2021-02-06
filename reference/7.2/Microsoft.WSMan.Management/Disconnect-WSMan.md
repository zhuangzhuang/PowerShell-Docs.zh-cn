---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596435"
---
# <span data-ttu-id="cfcc7-102">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="cfcc7-102">Disconnect-WSMan</span></span>

## <span data-ttu-id="cfcc7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="cfcc7-103">SYNOPSIS</span></span>
<span data-ttu-id="cfcc7-104">断开客户端与远程计算机上的 WinRM 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-104">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="cfcc7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cfcc7-105">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="cfcc7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cfcc7-106">DESCRIPTION</span></span>
<span data-ttu-id="cfcc7-107">**断开连接-WSMan** cmdlet 会断开客户端与远程计算机上的 WinRM 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-107">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="cfcc7-108">如果将 WS-Management 会话保存在变量中，则会话对象将保留在该变量中，但 WS-Management 会话的状态将会关闭。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-108">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="cfcc7-109">你可以在 WSMan 提供程序的上下文中使用此 cmdlet 来断开客户端与远程计算机上的 WinRM 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-109">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="cfcc7-110">但是，你还可以在更改为 WSMan 提供程序之前，使用此 cmdlet 断开与远程计算机上的 WinRM 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-110">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="cfcc7-111">有关如何连接到远程计算机上的 WinRM 服务的详细信息，请参阅 Connect-WSMan。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-111">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="cfcc7-112">示例</span><span class="sxs-lookup"><span data-stu-id="cfcc7-112">EXAMPLES</span></span>

### <span data-ttu-id="cfcc7-113">示例1：删除与远程计算机的连接</span><span class="sxs-lookup"><span data-stu-id="cfcc7-113">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="cfcc7-114">此命令删除与名为 server01 的远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-114">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="cfcc7-115">通常在 WSMan 提供程序的上下文中，使用此 cmdlet 断开与远程计算机（在本例中为 server01 计算机）的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-115">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="cfcc7-116">但是，你还可以在更改为 WSMan 提供程序之前，使用 **Disconnect-WSMan** 删除与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-116">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="cfcc7-117">这些连接不会显示在 ComputerName 列表中。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-117">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="cfcc7-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cfcc7-118">PARAMETERS</span></span>

### <span data-ttu-id="cfcc7-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cfcc7-119">-ComputerName</span></span>
<span data-ttu-id="cfcc7-120">指定要对其运行管理操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-120">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="cfcc7-121">该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-121">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="cfcc7-122">使用本地计算机名称、localhost 或点 (.) 指定本地计算机。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-122">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="cfcc7-123">默认值为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-123">The local computer is the default.</span></span>
<span data-ttu-id="cfcc7-124">当远程计算机与用户位于不同的域时，必须使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-124">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="cfcc7-125">可以通过管道将此参数的值传递给 cmdle。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-125">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="cfcc7-126">不能从本地主机断开连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-126">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="cfcc7-127">也就是说，不能断开与本地计算机的默认连接。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-127">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="cfcc7-128">但是，如果您创建了与本地计算机的单独连接，例如，使用计算机名称。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-128">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfcc7-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cfcc7-129">CommonParameters</span></span>
<span data-ttu-id="cfcc7-130">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cfcc7-131">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cfcc7-132">输入</span><span class="sxs-lookup"><span data-stu-id="cfcc7-132">INPUTS</span></span>

### <span data-ttu-id="cfcc7-133">无</span><span class="sxs-lookup"><span data-stu-id="cfcc7-133">None</span></span>
<span data-ttu-id="cfcc7-134">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-134">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="cfcc7-135">输出</span><span class="sxs-lookup"><span data-stu-id="cfcc7-135">OUTPUTS</span></span>

### <span data-ttu-id="cfcc7-136">无</span><span class="sxs-lookup"><span data-stu-id="cfcc7-136">None</span></span>
<span data-ttu-id="cfcc7-137">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="cfcc7-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cfcc7-138">注释</span><span class="sxs-lookup"><span data-stu-id="cfcc7-138">NOTES</span></span>

## <span data-ttu-id="cfcc7-139">相关链接</span><span class="sxs-lookup"><span data-stu-id="cfcc7-139">RELATED LINKS</span></span>

[<span data-ttu-id="cfcc7-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="cfcc7-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="cfcc7-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="cfcc7-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="cfcc7-142">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="cfcc7-142">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="cfcc7-143">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="cfcc7-143">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="cfcc7-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="cfcc7-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="cfcc7-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="cfcc7-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="cfcc7-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="cfcc7-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="cfcc7-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="cfcc7-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="cfcc7-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="cfcc7-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="cfcc7-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="cfcc7-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="cfcc7-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="cfcc7-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="cfcc7-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="cfcc7-151">Test-WSMan</span></span>](Test-WSMan.md)

