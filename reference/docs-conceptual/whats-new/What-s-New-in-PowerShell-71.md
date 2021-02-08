---
title: PowerShell 7.1 中的新增功能
description: PowerShell 7.1 中发布的新功能和更改
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577201"
---
# <a name="whats-new-in-powershell-71"></a><span data-ttu-id="a9595-103">PowerShell 7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="a9595-103">What's New in PowerShell 7.1</span></span>

<span data-ttu-id="a9595-104">2020 年 11 月 11 日，我们[宣布](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) PowerShell 7.1 正式发布。</span><span class="sxs-lookup"><span data-stu-id="a9595-104">On November 11, 2020 we [announced](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) the general availability of PowerShell 7.1.</span></span> <span data-ttu-id="a9595-105">在 PowerShell 7.0 建立的基础上，我们重点关注社区问题，并包括一些改进和修复。</span><span class="sxs-lookup"><span data-stu-id="a9595-105">Building on the foundation established in PowerShell 7.0, our efforts focused on community issues and include a number of improvements and fixes.</span></span> <span data-ttu-id="a9595-106">我们致力于确保 PowerShell 仍然是一个稳定的高性能平台。</span><span class="sxs-lookup"><span data-stu-id="a9595-106">We are committed to ensuring that PowerShell remains a stable and performant platform.</span></span>

<span data-ttu-id="a9595-107">PowerShell 7.1 包括以下功能、更新和重大更改。</span><span class="sxs-lookup"><span data-stu-id="a9595-107">PowerShell 7.1 includes the following features, updates, and breaking changes.</span></span>

- <span data-ttu-id="a9595-108">包含预测性 IntelliSense 的PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a9595-108">PSReadLine 2.1.0, which includes Predictive IntelliSense</span></span>
- <span data-ttu-id="a9595-109">PowerShell 7.1 已发布到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="a9595-109">PowerShell 7.1 has been published to the Microsoft Store</span></span>
- <span data-ttu-id="a9595-110">为新 OS 版本更新了安装程序包，支持 ARM64</span><span class="sxs-lookup"><span data-stu-id="a9595-110">Installer packages updated for new OS versions with support for ARM64</span></span>
- <span data-ttu-id="a9595-111">4 个新试验性功能和 2 个试验性功能晋升为主要功能</span><span class="sxs-lookup"><span data-stu-id="a9595-111">4 new experimental features and 2 experimental features promoted to mainstream</span></span>
- <span data-ttu-id="a9595-112">提高可用性的几项重大更改</span><span class="sxs-lookup"><span data-stu-id="a9595-112">Several breaking changes to improve usability</span></span>

<span data-ttu-id="a9595-113">有关更改的完整列表，请参阅 GitHub 库中的[更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md)。</span><span class="sxs-lookup"><span data-stu-id="a9595-113">For a complete list of changes, see the [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in the GitHub repository.</span></span>

## <a name="psreadline-210"></a><span data-ttu-id="a9595-114">PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a9595-114">PSReadLine 2.1.0</span></span>

<span data-ttu-id="a9595-115">PowerShell 7.1 还包括 PSReadLine 2.1.0。</span><span class="sxs-lookup"><span data-stu-id="a9595-115">PowerShell 7.1 also include PSReadLine 2.1.0.</span></span> <span data-ttu-id="a9595-116">此版本包含预测性 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="a9595-116">This version includes Predictive IntelliSense.</span></span> <span data-ttu-id="a9595-117">有关预测性 IntelliSense 功能的详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/)。</span><span class="sxs-lookup"><span data-stu-id="a9595-117">For more information about the Predictive IntelliSense feature, see the [announcement](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in the PowerShell blog.</span></span>

## <a name="microsoft-store-installer-package"></a><span data-ttu-id="a9595-118">Microsoft Store 安装程序包</span><span class="sxs-lookup"><span data-stu-id="a9595-118">Microsoft Store installer package</span></span>

<span data-ttu-id="a9595-119">PowerShell 7.1 已发布到 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="a9595-119">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="a9595-120">你可以在 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 网站上或在 Windows 应用商店应用程序中找到 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="a9595-120">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="a9595-121">Microsoft Store 包的权益：</span><span class="sxs-lookup"><span data-stu-id="a9595-121">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="a9595-122">直接内置于 Windows 10 的自动更新</span><span class="sxs-lookup"><span data-stu-id="a9595-122">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="a9595-123">与其他软件分发机制（如 Intune 和 SCCM）集成</span><span class="sxs-lookup"><span data-stu-id="a9595-123">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

> [!NOTE]
> <span data-ttu-id="a9595-124">不能修改存储在 `$PSHOME` 中的任何系统级配置设置。</span><span class="sxs-lookup"><span data-stu-id="a9595-124">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="a9595-125">其中包括 WSMAN 配置。</span><span class="sxs-lookup"><span data-stu-id="a9595-125">This includes the WSMAN configuration.</span></span> <span data-ttu-id="a9595-126">这可以防止远程会话连接到 PowerShell 的基于应用商店的安装。</span><span class="sxs-lookup"><span data-stu-id="a9595-126">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="a9595-127">支持用户级配置和 SSH 远程处理。</span><span class="sxs-lookup"><span data-stu-id="a9595-127">User-level configurations and SSH remoting are supported.</span></span>

## <a name="other-installers"></a><span data-ttu-id="a9595-128">其他安装程序</span><span class="sxs-lookup"><span data-stu-id="a9595-128">Other installers</span></span>

<span data-ttu-id="a9595-129">有关支持的操作系统和支持生命周期的最新信息，请参阅 [PowerShell 支持生命周期](/powershell/scripting/powershell-support-lifecycle)。</span><span class="sxs-lookup"><span data-stu-id="a9595-129">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

<span data-ttu-id="a9595-130">查看首选操作系统的安装说明：</span><span class="sxs-lookup"><span data-stu-id="a9595-130">Check the installation instructions for your preferred operating system:</span></span>

- [<span data-ttu-id="a9595-131">Windows</span><span class="sxs-lookup"><span data-stu-id="a9595-131">Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows)
- [<span data-ttu-id="a9595-132">macOS</span><span class="sxs-lookup"><span data-stu-id="a9595-132">macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos)
- [<span data-ttu-id="a9595-133">Linux</span><span class="sxs-lookup"><span data-stu-id="a9595-133">Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux)

<span data-ttu-id="a9595-134">此外，PowerShell 7.1 还支持 ARM32 和 ARM64 版的 Debian、Ubuntu 和 ARM64 Alpine Linux。</span><span class="sxs-lookup"><span data-stu-id="a9595-134">Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="a9595-135">虽然没有得到正式支持，但社区还提供了 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的包。</span><span class="sxs-lookup"><span data-stu-id="a9595-135">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="a9595-136">Debian 10+、CentOS 8+、Ubuntu 20.04、Alpine 和 Arm 目前不支持 WinRM 远程处理。</span><span class="sxs-lookup"><span data-stu-id="a9595-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine and Arm currently do not support WinRM remoting.</span></span> <span data-ttu-id="a9595-137">有关设置基于 SSH 的远程处理的详细信息，请参阅[通过 SSH 进行 PowerShell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。</span><span class="sxs-lookup"><span data-stu-id="a9595-137">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="experimental-features"></a><span data-ttu-id="a9595-138">实验性功能</span><span class="sxs-lookup"><span data-stu-id="a9595-138">Experimental Features</span></span>

<span data-ttu-id="a9595-139">有关实验性功能的详细信息，请参阅[使用实验性功能](../learn/experimental-features.md)。</span><span class="sxs-lookup"><span data-stu-id="a9595-139">For more information about the Experimental Features, see [Using Experimental Features](../learn/experimental-features.md).</span></span>

<span data-ttu-id="a9595-140">以下试验性功能现在是此版本中的主要功能：</span><span class="sxs-lookup"><span data-stu-id="a9595-140">The following experimental features are now mainstream features in this release:</span></span>

- [<span data-ttu-id="a9595-141">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="a9595-141">PSNullConditionalOperators</span></span>](../learn/experimental-features.md#psnullconditionaloperators)
- [<span data-ttu-id="a9595-142">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="a9595-142">PSUnixFileStat</span></span>](../learn/experimental-features.md#psunixfilestat)

<span data-ttu-id="a9595-143">此版本中添加了以下试验性功能：</span><span class="sxs-lookup"><span data-stu-id="a9595-143">The following experimental features were added in this release:</span></span>

- [<span data-ttu-id="a9595-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="a9595-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - <span data-ttu-id="a9595-145">PowerShell 7.1 扩展了此试验功能，以将 Runspace 参数添加到所有 `*-PSBreakpoint` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a9595-145">PowerShell 7.1 extends this experimental feature to add the **Runspace** parameter to all `*-PSBreakpoint` cmdlets.</span></span> <span data-ttu-id="a9595-146">“运行空间”参数会指定一个“运行空间”对象，以便可在指定的运行空间中与断点进行交互。</span><span class="sxs-lookup"><span data-stu-id="a9595-146">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

- <span data-ttu-id="a9595-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - 借助此功能可将 PowerShell 提供程序路径传递给不支持 PowerShell 路径语法的本机命令。</span><span class="sxs-lookup"><span data-stu-id="a9595-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - This feature allows you to pass PowerShell provider paths to native commands that don't support PowerShell path syntax.</span></span>

- <span data-ttu-id="a9595-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - 如果 `-replace` 运算符语句中的左操作数不是字符串，则此操作数会转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="a9595-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span> <span data-ttu-id="a9595-149">启用此功能后，转换不会使用区域性设置进行字符串转换。</span><span class="sxs-lookup"><span data-stu-id="a9595-149">With the feature enabled, the conversion does not use Culture settings for string conversion.</span></span>

- <span data-ttu-id="a9595-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) 为支持未来的预测 IntelliSense 插件奠定了基础。</span><span class="sxs-lookup"><span data-stu-id="a9595-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) lays the groundwork to support future Predictive IntelliSense plug-ins.</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="a9595-151">重大更改和改进</span><span class="sxs-lookup"><span data-stu-id="a9595-151">Breaking Changes and Improvements</span></span>

- <span data-ttu-id="a9595-152">当本机命令写入 `stderr` 时，将 `$?` 修复为非 `$false` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span><span class="sxs-lookup"><span data-stu-id="a9595-152">Fix `$?` to not be `$false` when native command writes to `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span></span>

  <span data-ttu-id="a9595-153">通常情况下，本机命令会写入 `stderr` 且不会指示失败。</span><span class="sxs-lookup"><span data-stu-id="a9595-153">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="a9595-154">进行此更改后，只有在本机命令也具有非零退出代码时 `$?` 才会设置为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="a9595-154">With this change `$?` is set to `$false` only when the native command also has a non-zero exit code.</span></span> <span data-ttu-id="a9595-155">此更改与试验性功能 `PSNotApplyErrorActionToStderr`无关。</span><span class="sxs-lookup"><span data-stu-id="a9595-155">This change is unrelated to the experimental feature `PSNotApplyErrorActionToStderr`.</span></span>

- <span data-ttu-id="a9595-156">使 `$ErrorActionPreference` 不会影响本机命令的 `stderr` 输出 ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span><span class="sxs-lookup"><span data-stu-id="a9595-156">Make `$ErrorActionPreference` not affect `stderr` output of native commands ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span></span>

  <span data-ttu-id="a9595-157">通常情况下，本机命令会写入 `stderr` 且不会指示失败。</span><span class="sxs-lookup"><span data-stu-id="a9595-157">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="a9595-158">进行此更改后，仍会在 ErrorRecord 对象中捕获 `stderr` 输出，但如果 ErrorRecord 来自本机命令，则运行时将不再适用 `$ErrorActionPreference` 。</span><span class="sxs-lookup"><span data-stu-id="a9595-158">With this change, `stderr` output is still captured in **ErrorRecord** objects, but the runtime no longer applies `$ErrorActionPreference` if the **ErrorRecord** comes from a native command.</span></span>

- <span data-ttu-id="a9595-159">在 `Get-Date` 上将 `-FromUnixTime` 重命名为 `-UnixTimeSeconds`，以允许 Unix 时间输入 ([#13084](https://github.com/PowerShell/PowerShell/pull/13084))（感谢 @aetos382！）</span><span class="sxs-lookup"><span data-stu-id="a9595-159">Rename `-FromUnixTime` to `-UnixTimeSeconds` on `Get-Date` to allow Unix time input ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Thanks @aetos382!)</span></span>

  <span data-ttu-id="a9595-160">在 7.1-preview.2 中添加了 `-FromUnixTime` 参数。</span><span class="sxs-lookup"><span data-stu-id="a9595-160">The `-FromUnixTime` parameter was added during 7.1-preview.2.</span></span> <span data-ttu-id="a9595-161">参数已重命名，以便更好地匹配数据类型。</span><span class="sxs-lookup"><span data-stu-id="a9595-161">The parameter was renamed to better match the data type.</span></span> <span data-ttu-id="a9595-162">此参数取整数值，表示自 1970 年 1 月 1 日 0:00:00 起的秒数。</span><span class="sxs-lookup"><span data-stu-id="a9595-162">This parameter takes an integer value that represents in seconds since January 1, 1970, 0:00:00.</span></span>

  <span data-ttu-id="a9595-163">此示例将 Unix 时间（由 1970-01-01 0:00:00 以来的秒数表示）转换为 DateTime。</span><span class="sxs-lookup"><span data-stu-id="a9595-163">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- <span data-ttu-id="a9595-164">允许显式指定的命名参数取代展开的哈希表中的同一个参数 (#13162)</span><span class="sxs-lookup"><span data-stu-id="a9595-164">Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)</span></span>

  <span data-ttu-id="a9595-165">进行此更改后，展开中的命名参数将移到参数列表的末尾，这样在所有显式指定的命名参数被绑定后，它们就会被绑定。</span><span class="sxs-lookup"><span data-stu-id="a9595-165">With this change, the named parameters from splatting are moved to the end of the parameter list so that they are bound after all explicitly specified named parameters are bound.</span></span> <span data-ttu-id="a9595-166">当找不到指定的命名参数时，简单函数的参数绑定不会引发错误。</span><span class="sxs-lookup"><span data-stu-id="a9595-166">Parameter binding for simple functions doesn't throw an error when a specified named parameter cannot be found.</span></span> <span data-ttu-id="a9595-167">未知的命名参数绑定到简单函数的 `$args` 参数。</span><span class="sxs-lookup"><span data-stu-id="a9595-167">Unknown named parameters are bound to the `$args` parameter of the simple function.</span></span> <span data-ttu-id="a9595-168">将展开移动到自变量列表的末尾将更改参数在 `$args`中的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="a9595-168">Moving splatting to the end of the argument list changes the order the parameters appears in `$args`.</span></span>

  <span data-ttu-id="a9595-169">例如：</span><span class="sxs-lookup"><span data-stu-id="a9595-169">For example:</span></span>

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  <span data-ttu-id="a9595-170">在以前的行为中，MyPath 未绑定到 `-Path`，因为它是自变量列表中的第三个自变量。</span><span class="sxs-lookup"><span data-stu-id="a9595-170">In the previous behavior, **MyPath** is not bound to `-Path` because it's the third argument in the argument list.</span></span> <span data-ttu-id="a9595-171">## 因此它最终和 `Blah = "World"` 一起填充到“$args”中</span><span class="sxs-lookup"><span data-stu-id="a9595-171">## So it ends up being stuffed into '$args' along with `Blah = "World"`</span></span>

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  <span data-ttu-id="a9595-172">进行此更改后，`@hash` 中的自变量将移到自变量列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="a9595-172">With this change, the arguments from `@hash` are moved to the end of the argument list.</span></span> <span data-ttu-id="a9595-173">MyPath 成为列表中的第一个自变量，因此它将绑定到 `-Path`。</span><span class="sxs-lookup"><span data-stu-id="a9595-173">**MyPath** becomes the first argument in the list, so it is bound to `-Path`.</span></span>

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- <span data-ttu-id="a9595-174">使开关参数 `-Qualifier` 不在 `Split-Path` 的位置 ([#12960](https://github.com/PowerShell/PowerShell/pull/12960))（感谢 @yecril71pl！）</span><span class="sxs-lookup"><span data-stu-id="a9595-174">Make the switch parameter `-Qualifier` not positional for `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Thanks @yecril71pl!)</span></span>

- <span data-ttu-id="a9595-175">未指定工作目录时，将工作目录解析为 `Start-Process` 的文本路径 ([#11946](https://github.com/PowerShell/PowerShell/pull/11946))（感谢 @NoMoreFood！）</span><span class="sxs-lookup"><span data-stu-id="a9595-175">Resolve the working directory as literal path for `Start-Process` when it's not specified ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Thanks @NoMoreFood!)</span></span>

- <span data-ttu-id="a9595-176">在 Web cmdlet 中指定 `-OutFile` 参数，使其具有与 `-LiteralPath` 相同的作用 ([#11701](https://github.com/PowerShell/PowerShell/pull/11701))（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a9595-176">Make `-OutFile` parameter in web cmdlets to work like `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="a9595-177">修复 `BigInteger` 数字文本的字符串参数绑定 ([#11634](https://github.com/PowerShell/PowerShell/pull/11634))（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="a9595-177">Fix string parameter binding for `BigInteger` numeric literals ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Thanks @vexx32!)</span></span>

- <span data-ttu-id="a9595-178">在 Windows 上，`Start-Process` 通过当前会话中的所有环境变量创建进程环境，同时使用 `-UseNewEnvironment` 创建新的默认进程环境 ([#10830](https://github.com/PowerShell/PowerShell/pull/10830))（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a9595-178">On Windows, `Start-Process` creates a process environment with all the environment variables from current session, using `-UseNewEnvironment` creates a new default process environment ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="a9595-179">将 `ScriptBlock` 转换为委托时，不要将返回结果包装为 `PSObject` ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span><span class="sxs-lookup"><span data-stu-id="a9595-179">Do not wrap return result in `PSObject` when converting a `ScriptBlock` to a delegate ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span></span>

  <span data-ttu-id="a9595-180">将 `ScriptBlock` 转换为要在 C# 上下文中使用的委托类型时，将结果包装为 `PSObject` 会导致不必要的麻烦：</span><span class="sxs-lookup"><span data-stu-id="a9595-180">When a `ScriptBlock` is converted to a delegate type to be used in C# context, wrapping the result in a `PSObject` brings unneeded troubles:</span></span>

  - <span data-ttu-id="a9595-181">当值转换为委托返回类型时，`PSObject` 实质上是已解包。</span><span class="sxs-lookup"><span data-stu-id="a9595-181">When the value is converted to the delegate return type, the `PSObject` essentially gets unwrapped.</span></span> <span data-ttu-id="a9595-182">因此不需要 `PSObject`。</span><span class="sxs-lookup"><span data-stu-id="a9595-182">So the `PSObject` is unneeded.</span></span>
  - <span data-ttu-id="a9595-183">如果委托返回类型为 `object`，则将其包装为 `PSObject` 会使其难以在 C# 代码中运行。</span><span class="sxs-lookup"><span data-stu-id="a9595-183">When the delegate return type is `object`, it gets wrapped in a `PSObject` making it hard to work with in C# code.</span></span>

  <span data-ttu-id="a9595-184">进行此更改后，返回的对象是基础对象。</span><span class="sxs-lookup"><span data-stu-id="a9595-184">After this change, the returned object is the underlying object.</span></span>
