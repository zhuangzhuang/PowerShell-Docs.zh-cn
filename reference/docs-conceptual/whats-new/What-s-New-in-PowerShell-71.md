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
# <a name="whats-new-in-powershell-71"></a>PowerShell 7.1 中的新增功能

2020 年 11 月 11 日，我们[宣布](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) PowerShell 7.1 正式发布。 在 PowerShell 7.0 建立的基础上，我们重点关注社区问题，并包括一些改进和修复。 我们致力于确保 PowerShell 仍然是一个稳定的高性能平台。

PowerShell 7.1 包括以下功能、更新和重大更改。

- 包含预测性 IntelliSense 的PSReadLine 2.1.0
- PowerShell 7.1 已发布到 Microsoft Store
- 为新 OS 版本更新了安装程序包，支持 ARM64
- 4 个新试验性功能和 2 个试验性功能晋升为主要功能
- 提高可用性的几项重大更改

有关更改的完整列表，请参阅 GitHub 库中的[更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md)。

## <a name="psreadline-210"></a>PSReadLine 2.1.0

PowerShell 7.1 还包括 PSReadLine 2.1.0。 此版本包含预测性 IntelliSense。 有关预测性 IntelliSense 功能的详细信息，请参阅 PowerShell 博客中的[公告](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/)。

## <a name="microsoft-store-installer-package"></a>Microsoft Store 安装程序包

PowerShell 7.1 已发布到 Microsoft Store。 你可以在 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 网站上或在 Windows 应用商店应用程序中找到 PowerShell 版本。

Microsoft Store 包的权益：

- 直接内置于 Windows 10 的自动更新
- 与其他软件分发机制（如 Intune 和 SCCM）集成

> [!NOTE]
> 不能修改存储在 `$PSHOME` 中的任何系统级配置设置。 其中包括 WSMAN 配置。 这可以防止远程会话连接到 PowerShell 的基于应用商店的安装。 支持用户级配置和 SSH 远程处理。

## <a name="other-installers"></a>其他安装程序

有关支持的操作系统和支持生命周期的最新信息，请参阅 [PowerShell 支持生命周期](/powershell/scripting/powershell-support-lifecycle)。

查看首选操作系统的安装说明：

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

此外，PowerShell 7.1 还支持 ARM32 和 ARM64 版的 Debian、Ubuntu 和 ARM64 Alpine Linux。

虽然没有得到正式支持，但社区还提供了 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的包。

> [!NOTE]
> Debian 10+、CentOS 8+、Ubuntu 20.04、Alpine 和 Arm 目前不支持 WinRM 远程处理。 有关设置基于 SSH 的远程处理的详细信息，请参阅[通过 SSH 进行 PowerShell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

## <a name="experimental-features"></a>实验性功能

有关实验性功能的详细信息，请参阅[使用实验性功能](../learn/experimental-features.md)。

以下试验性功能现在是此版本中的主要功能：

- [PSNullConditionalOperators](../learn/experimental-features.md#psnullconditionaloperators)
- [PSUnixFileStat](../learn/experimental-features.md#psunixfilestat)

此版本中添加了以下试验性功能：

- [Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - PowerShell 7.1 扩展了此试验功能，以将 Runspace 参数添加到所有 `*-PSBreakpoint` cmdlet。 “运行空间”参数会指定一个“运行空间”对象，以便可在指定的运行空间中与断点进行交互。

- [PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - 借助此功能可将 PowerShell 提供程序路径传递给不支持 PowerShell 路径语法的本机命令。

- [PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - 如果 `-replace` 运算符语句中的左操作数不是字符串，则此操作数会转换为字符串。 启用此功能后，转换不会使用区域性设置进行字符串转换。

- [PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) 为支持未来的预测 IntelliSense 插件奠定了基础。

## <a name="breaking-changes-and-improvements"></a>重大更改和改进

- 当本机命令写入 `stderr` 时，将 `$?` 修复为非 `$false` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))

  通常情况下，本机命令会写入 `stderr` 且不会指示失败。
  进行此更改后，只有在本机命令也具有非零退出代码时 `$?` 才会设置为 `$false`。 此更改与试验性功能 `PSNotApplyErrorActionToStderr`无关。

- 使 `$ErrorActionPreference` 不会影响本机命令的 `stderr` 输出 ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))

  通常情况下，本机命令会写入 `stderr` 且不会指示失败。
  进行此更改后，仍会在 ErrorRecord 对象中捕获 `stderr` 输出，但如果 ErrorRecord 来自本机命令，则运行时将不再适用 `$ErrorActionPreference` 。

- 在 `Get-Date` 上将 `-FromUnixTime` 重命名为 `-UnixTimeSeconds`，以允许 Unix 时间输入 ([#13084](https://github.com/PowerShell/PowerShell/pull/13084))（感谢 @aetos382！）

  在 7.1-preview.2 中添加了 `-FromUnixTime` 参数。 参数已重命名，以便更好地匹配数据类型。 此参数取整数值，表示自 1970 年 1 月 1 日 0:00:00 起的秒数。

  此示例将 Unix 时间（由 1970-01-01 0:00:00 以来的秒数表示）转换为 DateTime。

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- 允许显式指定的命名参数取代展开的哈希表中的同一个参数 (#13162)

  进行此更改后，展开中的命名参数将移到参数列表的末尾，这样在所有显式指定的命名参数被绑定后，它们就会被绑定。 当找不到指定的命名参数时，简单函数的参数绑定不会引发错误。 未知的命名参数绑定到简单函数的 `$args` 参数。 将展开移动到自变量列表的末尾将更改参数在 `$args`中的显示顺序。

  例如：

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  在以前的行为中，MyPath 未绑定到 `-Path`，因为它是自变量列表中的第三个自变量。 ## 因此它最终和 `Blah = "World"` 一起填充到“$args”中

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  进行此更改后，`@hash` 中的自变量将移到自变量列表的末尾。 MyPath 成为列表中的第一个自变量，因此它将绑定到 `-Path`。

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- 使开关参数 `-Qualifier` 不在 `Split-Path` 的位置 ([#12960](https://github.com/PowerShell/PowerShell/pull/12960))（感谢 @yecril71pl！）

- 未指定工作目录时，将工作目录解析为 `Start-Process` 的文本路径 ([#11946](https://github.com/PowerShell/PowerShell/pull/11946))（感谢 @NoMoreFood！）

- 在 Web cmdlet 中指定 `-OutFile` 参数，使其具有与 `-LiteralPath` 相同的作用 ([#11701](https://github.com/PowerShell/PowerShell/pull/11701))（感谢 @iSazonov！）

- 修复 `BigInteger` 数字文本的字符串参数绑定 ([#11634](https://github.com/PowerShell/PowerShell/pull/11634))（感谢 @vexx32！）

- 在 Windows 上，`Start-Process` 通过当前会话中的所有环境变量创建进程环境，同时使用 `-UseNewEnvironment` 创建新的默认进程环境 ([#10830](https://github.com/PowerShell/PowerShell/pull/10830))（感谢 @iSazonov！）

- 将 `ScriptBlock` 转换为委托时，不要将返回结果包装为 `PSObject` ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))

  将 `ScriptBlock` 转换为要在 C# 上下文中使用的委托类型时，将结果包装为 `PSObject` 会导致不必要的麻烦：

  - 当值转换为委托返回类型时，`PSObject` 实质上是已解包。 因此不需要 `PSObject`。
  - 如果委托返回类型为 `object`，则将其包装为 `PSObject` 会使其难以在 C# 代码中运行。

  进行此更改后，返回的对象是基础对象。
