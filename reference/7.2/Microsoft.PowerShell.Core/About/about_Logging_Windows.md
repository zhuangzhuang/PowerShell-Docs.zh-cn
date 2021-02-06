---
description: PowerShell 将引擎、提供程序和 cmdlet 的内部操作记录到 Windows 事件日志中。
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: d6ae50b50911417da8dd306cad69e3fc7129fedc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596407"
---
# <a name="about-logging-windows"></a><span data-ttu-id="ff527-103">关于日志记录窗口</span><span class="sxs-lookup"><span data-stu-id="ff527-103">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="ff527-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="ff527-104">Short description</span></span>
<span data-ttu-id="ff527-105">PowerShell 将引擎、提供程序和 cmdlet 的内部操作记录到 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="ff527-105">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="ff527-106">长说明</span><span class="sxs-lookup"><span data-stu-id="ff527-106">Long description</span></span>

<span data-ttu-id="ff527-107">PowerShell 记录有关 PowerShell 操作的详细信息，例如启动和停止引擎和提供程序，以及执行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="ff527-107">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="ff527-108">Windows PowerShell 版本3.0、4.0、5.0 和5.1 包含 Windows 事件日志的 **事件** 日志 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff527-108">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="ff527-109">在这些版本中，若要显示 **EventLog** cmdlet 的列表，请键入： `Get-Command -Noun EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="ff527-109">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="ff527-110">有关详细信息，请参阅你的 Windows PowerShell 版本的 cmdlet 文档和 about_EventLogs。</span><span class="sxs-lookup"><span data-stu-id="ff527-110">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="ff527-111">查看 Windows 上的 PowerShell 事件日志条目</span><span class="sxs-lookup"><span data-stu-id="ff527-111">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="ff527-112">可以使用 Windows 事件查看器查看 PowerShell 日志。</span><span class="sxs-lookup"><span data-stu-id="ff527-112">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="ff527-113">事件日志位于 "应用程序" 和 "服务日志" 组中，并命名为 `PowerShellCore` 。</span><span class="sxs-lookup"><span data-stu-id="ff527-113">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="ff527-114">关联的 ETW 提供程序 `GUID` 为 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 。</span><span class="sxs-lookup"><span data-stu-id="ff527-114">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="ff527-115">启用脚本块日志记录时，PowerShell 会将以下事件记录到 `PowerShellCore/Operational` 日志中：</span><span class="sxs-lookup"><span data-stu-id="ff527-115">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="ff527-116">字段</span><span class="sxs-lookup"><span data-stu-id="ff527-116">Field</span></span>  |       <span data-ttu-id="ff527-117">值</span><span class="sxs-lookup"><span data-stu-id="ff527-117">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="ff527-118">EventId</span><span class="sxs-lookup"><span data-stu-id="ff527-118">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="ff527-119">通道</span><span class="sxs-lookup"><span data-stu-id="ff527-119">Channel</span></span> | `Operational`     |
| <span data-ttu-id="ff527-120">级别</span><span class="sxs-lookup"><span data-stu-id="ff527-120">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="ff527-121">操作码</span><span class="sxs-lookup"><span data-stu-id="ff527-121">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="ff527-122">任务</span><span class="sxs-lookup"><span data-stu-id="ff527-122">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="ff527-123">关键字</span><span class="sxs-lookup"><span data-stu-id="ff527-123">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="ff527-124">在 Windows 上注册 PowerShell 事件提供程序</span><span class="sxs-lookup"><span data-stu-id="ff527-124">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="ff527-125">与 Linux 或 macOS 不同，Windows 要求先注册事件提供程序，然后才能将事件写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="ff527-125">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="ff527-126">若要启用 PowerShell 事件提供程序，请从提升的 PowerShell 提示符中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="ff527-126">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="ff527-127">在 Windows 上注销 PowerShell 事件提供程序</span><span class="sxs-lookup"><span data-stu-id="ff527-127">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="ff527-128">注册事件提供程序会在用于对事件进行解码的二进制库中放置锁。</span><span class="sxs-lookup"><span data-stu-id="ff527-128">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="ff527-129">若要更新此库，必须取消注册该提供程序以释放此锁定。</span><span class="sxs-lookup"><span data-stu-id="ff527-129">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="ff527-130">若要注销 PowerShell 提供程序，请从提升的 PowerShell 提示符中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="ff527-130">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="ff527-131">更新 PowerShell 后，运行 `$PSHOME\RegisterManifest.ps1` 以注册更新的事件提供程序。</span><span class="sxs-lookup"><span data-stu-id="ff527-131">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="ff527-132">启用脚本块日志记录</span><span class="sxs-lookup"><span data-stu-id="ff527-132">Enabling Script Block Logging</span></span>

<span data-ttu-id="ff527-133">启用脚本块日志记录时，PowerShell 将记录其处理的所有脚本块的内容。</span><span class="sxs-lookup"><span data-stu-id="ff527-133">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="ff527-134">启用后，任何新的 PowerShell 会话都将记录此信息。</span><span class="sxs-lookup"><span data-stu-id="ff527-134">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="ff527-135">如果使用脚本块日志记录作为诊断目的以外的任何内容，则建议启用受保护的事件日志记录，如下所述。</span><span class="sxs-lookup"><span data-stu-id="ff527-135">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="ff527-136">可以通过组策略或注册表设置来启用脚本块日志记录。</span><span class="sxs-lookup"><span data-stu-id="ff527-136">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="ff527-137">使用组策略</span><span class="sxs-lookup"><span data-stu-id="ff527-137">Using Group Policy</span></span>

<span data-ttu-id="ff527-138">若要启用自动脚本，请 `Turn on PowerShell Script Block
Logging` 在组策略中启用该功能 `Administrative Templates -> Windows
Components -> Windows PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="ff527-138">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="ff527-139">使用注册表</span><span class="sxs-lookup"><span data-stu-id="ff527-139">Using the Registry</span></span>

<span data-ttu-id="ff527-140">运行以下函数：</span><span class="sxs-lookup"><span data-stu-id="ff527-140">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="ff527-141">受保护的事件日志记录</span><span class="sxs-lookup"><span data-stu-id="ff527-141">Protected Event Logging</span></span>

<span data-ttu-id="ff527-142">提高系统日志记录的级别，可以提高记录的内容可能包含敏感数据的可能性。</span><span class="sxs-lookup"><span data-stu-id="ff527-142">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="ff527-143">例如，启用脚本日志记录后，可以将脚本使用的凭据或其他敏感数据写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="ff527-143">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="ff527-144">当包含记录的敏感数据的计算机受到威胁时，日志可以为攻击者提供扩展其范围所需的信息。</span><span class="sxs-lookup"><span data-stu-id="ff527-144">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="ff527-145">为了保护此信息，Windows 10 引入了受保护的事件日志记录。</span><span class="sxs-lookup"><span data-stu-id="ff527-145">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="ff527-146">受保护的事件日志记录使参与的应用程序可以加密写入事件日志的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="ff527-146">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="ff527-147">稍后，你可以通过更安全且集中的日志收集器来解密和处理这些日志。</span><span class="sxs-lookup"><span data-stu-id="ff527-147">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="ff527-148">使用 IETF 加密消息语法 (CMS) 标准保护事件日志内容。</span><span class="sxs-lookup"><span data-stu-id="ff527-148">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="ff527-149">CMS 使用公钥加密。</span><span class="sxs-lookup"><span data-stu-id="ff527-149">CMS uses public key cryptography.</span></span> <span data-ttu-id="ff527-150">用于对内容进行加密和解密的密钥保持独立。</span><span class="sxs-lookup"><span data-stu-id="ff527-150">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="ff527-151">公钥可以广泛共享，并且不是敏感数据。</span><span class="sxs-lookup"><span data-stu-id="ff527-151">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="ff527-152">使用此公钥加密的任何内容只能通过私钥进行解密。</span><span class="sxs-lookup"><span data-stu-id="ff527-152">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="ff527-153">有关公钥加密的详细信息，请参阅 [维基百科-公钥加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。</span><span class="sxs-lookup"><span data-stu-id="ff527-153">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="ff527-154">若要启用受保护的事件日志记录策略，请将一个公钥部署到具有要保护的事件日志数据的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="ff527-154">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="ff527-155">对应的私钥用于在更安全的位置（如中心事件日志收集器或 [SIEM][] 聚合器）后处理事件日志。</span><span class="sxs-lookup"><span data-stu-id="ff527-155">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="ff527-156">可以在 Azure 中设置 SIEM。</span><span class="sxs-lookup"><span data-stu-id="ff527-156">You can set up SIEM in Azure.</span></span> <span data-ttu-id="ff527-157">有关详细信息，请参阅 [通用 SIEM 集成](/cloud-app-security/siem)。</span><span class="sxs-lookup"><span data-stu-id="ff527-157">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="ff527-158">通过组策略启用受保护的事件日志记录</span><span class="sxs-lookup"><span data-stu-id="ff527-158">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="ff527-159">若要启用受保护的事件日志记录，请 `Enable Protected Event Logging` 在组策略中启用该功能 `Administrative Templates -> Windows Components
-> Event Logging` 。</span><span class="sxs-lookup"><span data-stu-id="ff527-159">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="ff527-160">此设置需要一个加密证书，你可以使用以下几种形式之一提供该证书：</span><span class="sxs-lookup"><span data-stu-id="ff527-160">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="ff527-161">64编码的 x.509 证书的内容 (例如，如 `Export` 证书管理器) 中的选项所提供的那样。</span><span class="sxs-lookup"><span data-stu-id="ff527-161">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="ff527-162">可在本地计算机证书存储 (中找到的证书的指纹，可通过 PKI 基础结构) 部署。</span><span class="sxs-lookup"><span data-stu-id="ff527-162">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="ff527-163">证书的完整路径 (可以是本地的，也可以是远程共享) 。</span><span class="sxs-lookup"><span data-stu-id="ff527-163">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="ff527-164">包含证书的目录的路径或证书 (可以是本地的，也可以是远程共享) 。</span><span class="sxs-lookup"><span data-stu-id="ff527-164">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="ff527-165">可在本地计算机证书存储 (中找到的证书的使用者名称，可通过 PKI 基础结构) 部署。</span><span class="sxs-lookup"><span data-stu-id="ff527-165">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="ff527-166">生成的证书必须具有 `Document Encryption` () 的增强型密钥用法 `1.3.6.1.4.1.311.80.1` ，并 `Data Encipherment` 启用或 `Key
Encipherment` 启用密钥用法。</span><span class="sxs-lookup"><span data-stu-id="ff527-166">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="ff527-167">不应将私钥部署到计算机日志记录事件。</span><span class="sxs-lookup"><span data-stu-id="ff527-167">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="ff527-168">应将其保存在一个安全的位置，以便对消息进行解密。</span><span class="sxs-lookup"><span data-stu-id="ff527-168">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="ff527-169">解密受保护的事件日志记录消息</span><span class="sxs-lookup"><span data-stu-id="ff527-169">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="ff527-170">下面的脚本将检索并解密，前提是你有私钥：</span><span class="sxs-lookup"><span data-stu-id="ff527-170">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="ff527-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff527-171">See also</span></span>

[<span data-ttu-id="ff527-172">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="ff527-172">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="ff527-173">向蓝色团队 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff527-173">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="ff527-174">通用 SIEM 集成</span><span class="sxs-lookup"><span data-stu-id="ff527-174">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
<span data-ttu-id="ff527-175">SIEM</span><span class="sxs-lookup"><span data-stu-id="ff527-175">[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management</span></span>
