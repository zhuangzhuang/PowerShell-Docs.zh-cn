---
title: PowerShell 7.0 中的新增功能
description: PowerShell 7.0 中发布的新功能和更改
ms.date: 03/04/2020
ms.openlocfilehash: 3a5a1aaa0bd9dd1e0df7d6f5e6021678ed21dce4
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355266"
---
# <a name="whats-new-in-powershell-70"></a>PowerShell 7.0 中的新增功能

PowerShell 7.0 是 PowerShell 的一个版本，它开源、跨平台（Windows、macOS 和 Linux）且为管理异类环境和混合云而构建。

在此版本中，我们引入了一些新功能，包括：

- 使用 `ForEach-Object -Parallel` 实现管道并行化
- 新运算符：
  - 三元运算符：`a ? b : c`
  - 管道链运算符：`||` 和 `&&`
  - 空条件运算符：`??` 和 `??=`
- 简化且动态的错误视图和 `Get-Error` cmdlet，以便更轻松地调查错误
- 兼容层，使用户能够在隐式 Windows PowerShell 会话中导入模块
- 自动新版本通知
- 直接从 PowerShell 7 调用 DSC 资源的功能（实验性）

若要查看功能和修补程序的完整列表，请参阅[更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)。

## <a name="where-can-i-install-powershell"></a>可将 PowerShell 安装在何处？

PowerShell 7 当前支持 x64 上的以下操作系统，包括：

- Windows 8.1 和 10
- Windows Server 2012、2012 R2、2016 和 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL)/CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

此外，PowerShell 7.0 支持 ARM32 和 ARM64 版的 Debian、Ubuntu 和 ARM64 Alpine Linux。

查看首选操作系统 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)、[macOS](/powershell/scripting/install/installing-powershell-core-on-macos) 或 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux) 的安装说明。

虽然没有得到正式支持，但社区还提供了 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的包。

> [!NOTE]
> Debian 10 和 CentOS 8 目前不支持 WinRM 远程处理。 有关设置基于 SSH 的远程处理的详细信息，请参阅[通过 SSH 进行 PowerShell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

有关支持的操作系统和支持生命周期的最新信息，请参阅 [PowerShell 支持生命周期](/powershell/scripting/powershell-support-lifecycle)。

## <a name="running-powershell-7"></a>运行 PowerShell 7

PowerShell 7 和 Windows PowerShell 分别安装在不同的目录中。
这样，你可并行使用 PowerShell 7 与 Windows PowerShell 5.1。 对于 PowerShell Core 6.x，PowerShell 7 是删除 PowerShell Core 6.x 的就地升级。

- PowerShell 7 安装到 `%programfiles%\PowerShell\7`
- `%programfiles%\PowerShell\7` 文件夹已添加到 `$env:PATH`

PowerShell 7 安装程序包会升级之前版本的 PowerShell Core 6.x：

- Windows 上的 PowerShell Core 6.x：`%programfiles%\PowerShell\6` 已替换为 `%programfiles%\PowerShell\7`
- Linux：`/opt/microsoft/powershell/6` 已替换为 `/opt/microsoft/powershell/7`
- macOS：`/usr/local/microsoft/powershell/6` 已替换为 `/usr/local/microsoft/powershell/7`

> [!NOTE]
> 在 Windows PowerShell 中，用于启动 PowerShell 的可执行文件名为 `powershell.exe`。 在版本 6 及更高版本中，可执行文件的名称将改为支持并行执行。 用于启动 PowerShell 7 的可执行文件新名称为 `pwsh.exe`。 预览版本就地保留为 `pwsh-preview`，而不是 7 预览目录下的 `pwsh`。

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>改进了 Windows PowerShell 的向后兼容性

PowerShell 7.0 标记了转移到 .NET Core 3.1 的过程，从而大大改进了现有 Windows PowerShell 模块向后兼容性。 其中包括 Windows 上需要 GUI 功能（如 `Out-GridView` 和 `Show-Command`）的许多模块以及作为 Windows 的一部分提供的许多角色管理模块。

对于 Windows，新开关参数 UseWindowsPowerShell 将添加到 `Import-Module`。 此开关会在 PowerShell 7 中创建一个代理模块，该模块使用本地 Windows PowerShell 进程隐式运行该模块中包含的任何 cmdlet。 有关 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true) 的详细信息。

有关哪些 Microsoft 模块适用于 PowerShell 7.0 的详细信息，请参阅[模块兼容性表](https://aka.ms/PSModuleCompat)。

## <a name="parallel-execution-added-to-foreach-object"></a>添加到 ForEach-Object 的并行执行

循环访问集合中的项的 `ForEach-Object` cmdlet 现在使用新的 Parallel 参数实现内置并行。

默认情况下，并行脚本块使用启动并行任务的调用方的当前工作目录。

此示例从本地 Windows 计算机上的 5 个系统日志中检索 50,000 个日志条目：

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Parallel 参数指定为每个输入日志名称并行运行的脚本块。

新的 ThrottleLimit 参数限制在给定时间内并行运行的脚本块数量。 默认值为 5。

使用 `$_` 变量来表示脚本块中的当前输入对象。 使用 `$using:` 范围将变量引用传递给正在运行的脚本块。

有关 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&preserve-view=true) 的详细信息。

## <a name="ternary-operator"></a>三元运算符

PowerShell 7.0 引入了三元运算符，它的行为类似于简化的 `if-else` 语句。
PowerShell 的三元运算符是严格按照 C# 三元运算符语法建模而来的：

```
<condition> ? <if-true> : <if-false>
```

始终计算条件表达式，并将其结果转换为布尔以确定下一次计算的分支：

- 如果 `<condition>` 表达式为 true，则执行 `<if-true>` 表达式
- 如果 `<condition>` 表达式为 false，则执行 `<if-false>` 表达式

例如：

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

在此示例中，如果路径存在，则显示“路径存在”。 如果路径不存在，则显示“找不到路径”。

有关[关于假设情况](/powershell/module/microsoft.powershell.core/about/about_if)的详细信息。

## <a name="pipeline-chain-operators"></a>管道链运算符

PowerShell 7 实施 `&&` 和 `||` 运算符，以有条件地链接管道。 这些运算符在 PowerShell 中称为“管道链运算符”，与 shell（如 Bash 和 Zsh）中的 AND 和 OR 列表以及 Windows 命令 Shell (cmd.exe) 中的条件处理符号类似  。

如果左侧管道成功，则 `&&` 运算符将执行右侧管道。 相反，如果左侧管道失败，则 `||` 运算符将执行右侧管道。

> [!NOTE]
> 这些运算符使用 `$?` 和 `$LASTEXITCODE` 变量来确定管道是否失败。 这允许你将其与本机命令一起使用，而不只是与 cmdlet 或函数一起使用。

此处，第一个命令成功，执行第二个命令：

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

此处，第一个命令失败，不执行第二个命令：

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

此处，第一个命令成功，不执行第二个命令：

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

此处，第一个命令失败，因此执行第二个命令：

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

有关[关于管道链运算符](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7&preserve-view=true)的详细信息。

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null 合并运算符、赋值运算符和条件运算符

PowerShell 7 包括 Null 合并运算符 `??`、Null 条件赋值运算符 `??=` 和 Null 条件成员访问运算符 `?.` 和 `?[]`。

### <a name="null-coalescing-operator-"></a>Null 合并运算符 ??

如果 null 合并运算符 `??` 不为 null，则它返回其左操作数的值。
否则，它将计算右操作数并返回其结果。 如果左操作数的计算结果为非 null，则 `??` 运算符不会计算其右操作数。

```powershell
$x = $null
$x ?? 100
100
```

在下面的示例中，不会计算右操作数：

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Null 条件赋值运算符 ??=

仅当左操作数的计算结果为 null 时，null 条件赋值运算符 `??=` 才会将其右操作数的值赋值给其左操作数。 如果左操作数的计算结果为非 null，则 `??=` 运算符不会计算其右操作数。

```powershell
$x = $null
$x ??= 100
$x
100
```

在下例中，不计算右操作数：

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null 条件成员访问运算符 ?. 和 ?[]（实验性）

> [!NOTE]
> 这是名为 PSNullConditionalOperators 的实验性功能。 有关详细信息，请参阅[使用实验性功能](/powershell/scripting/learn/experimental-features)。

仅当操作数的计算结果为非 null，null 条件运算符才允许对其操作数进程成员访问 `?.` 或元素访问 `?[]`；否则，将返回 null。

> [!NOTE]
> 由于 PowerShell 允许 `?` 作为变量名称的一部分，因此使用这些运算符需要变量名称的形式规范。 因此，使用 `{}` 将变量名称括起来（如 `${a}`）或 `?` 是变量名称 `${a?}` 的一部分时需要形式规范。

在下面的示例中，将返回成员属性 Status 的值：

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

以下示例将返回 null，而不尝试访问成员名称 Status：

```powershell
$service = $Null
${Service}?.status
```

同样，使用 `?[]` 时，将返回元素的值：

```powershell
$a = 1..10
${a}?[0]
1
```

如果操作数为 null，则不会访问元素并返回 null：

```powershell
$a = $null
${a}?[0]
```

有关 [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&preserve-view=true) 的详细信息。

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>新视图 ConciseView 和 cmdlet Get-Error

PowerShell 7.0 具有新的默认视图 ConciseView，它增强了错误消息的显示，进而提高了交互式错误和脚本错误的可读性。 视图通过首选项变量 `$ErrorView` 可供用户选择。

使用 ConciseView，如果错误不是源自脚本或分析器错误，则它是单行错误消息：

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

如果在脚本执行期间发生错误或者错误是分析错误，则 PowerShell 将返回一条多行错误消息，其中包含错误、指针以及显示错误在该行中的位置的错误消息。 如果终端不支持 ANSI 颜色转义序列 (VT100)，则不会显示颜色。

![脚本中的错误显示](./media/What-s-New-in-PowerShell-70/myscript-error.png)

PowerShell 7 中的默认视图是 ConciseView。 之前的默认视图是 NormalView，你可通过设置首选项变量 `$ErrorView` 来选择它。

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> 向 `$Host.PrivateData` 添加新属性 ErrorAccentColor，以支持更改错误消息的主题色。

一个新的 cmdlet `Get-Error` 在需要时可提供完全符合条件的错误的完整详细视图。
默认情况下，该 cmdlet 将显示所发生的最后一个错误的完整详细信息（包括内部异常）。

![Get-Error 中的显示](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

`Get-Error` cmdlet 使用内置变量 `$Error` 支持来自管道的输入。
`Get-Error` 显示所有管道错误。

```powershell
$Error | Get-Error
```

`Get-Error` cmdlet 支持最新参数，允许你指定当前会话中要显示的错误数。

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

有关 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&preserve-view=true) 的详细信息。

## <a name="new-version-notification"></a>新版本通知

PowerShell 7 使用更新通知提醒用户是否存在 PowerShell 更新。
PowerShell 每天查询一次联机服务，以确定是否提供较新版本。

> [!NOTE]
> 在给定的 24 小时内的第一次会话期间进行更新检查。 出于性能原因，更新检查将在会话开始后的 3 秒内启动。 通知仅在后续会话开始时显示。

默认情况下，PowerShell 订阅两个不同通知通道之一，具体取决于其版本/分支。 受支持的正式发布 (GA) 版 PowerShell 仅返回已更新 GA 版本的通知。 预览版和候选发布 (RC) 版本会通知预览版、RC 和 GA 版本的更新。

可以使用 `$Env:POWERSHELL_UPDATECHECK` 环境变量更改更新通知行为。 支持以下值：

- `Default` 即与不定义 `$Env:POWERSHELL_UPDATECHECK` 相同
  - GA 版本通知 GA 版本的更新
  - 预览版/RC 版本通知 GA 版本和预览版的更新
- `Off` 即关闭更新通知功能
- `LTS` 仅通知长期服务 (LTS) GA 版本的更新

> [!NOTE]
> 环境变量 `$Env:POWERSHELL_UPDATECHECK` 在首次设置之前不存在。

若要仅为 `LTS` 版本设置版本通知，请执行以下操作：

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

若要为 `Default` 行为设置版本通知，请执行以下操作：

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

有关[关于更新通知](/powershell/module/microsoft.powershell.core/about/about_update_notifications)的详细信息。

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>使用 Invoke-DSCResource 的新 DSC 资源支持（实验性）

> [!NOTE]
> 这是名为 PSDesiredStateConfiguration.InvokeDscResource 的实验性功能。 有关详细信息，请参阅[使用实验性功能](/powershell/scripting/learn/experimental-features)。

`Invoke-DscResource` cmdlet 运行指定的 PowerShell 所需状态配置 (DSC) 资源的方法。

此 cmdlet 直接调用 DSC 资源，而无需创建配置文档。 使用此 cmdlet，配置管理产品可以使用 DSC 资源来管理 Windows 或 Linux。 在启用调试的情况下运行 DSC 引擎时，此 cmdlet 还可用于调试资源。

此命令调用名为 WindowsProcess 的资源的 Set 方法，并提供必需的路径和参数属性以启动指定的 Windows 进程   。

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

有关 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&preserve-view=true) 的详细信息。

## <a name="breaking-changes-and-improvements"></a>重大更改和改进

### <a name="breaking-changes"></a>重大更改

- 使更新通知支持 LTS 和默认通道 (#11132)
- 更新 Test-Connection，使其工作方式更类似于 Windows PowerShell 中的命令 (#10697)（感谢 @vexx32！）
- 保留 $? 对于 ParenExpression、SubExpression 和 ArrayExpression (#11040)
- 在 Start-Job 中将工作目录设置为当前目录 (#10920)（感谢 @iSazonov！）
- 使 $PSCulture 一致地反映会话中区域性更改 (#10138)（感谢 @iSazonov！）

### <a name="engine-updates-and-fixes"></a>引擎更新和修补程序

- 远程方案的断点 API 的改进 (#11312)
- 修复泄漏到其他运行空间的 PowerShell 类定义 (#11273)
- 修复由 7.0.0-Preview1 中添加的 FirstOrDefault 基元引起的格式设置回归 (#11258)
- 要在 PS7 遥测中跟踪的其他 Microsoft 模块 (#10751)
- 使已批准的功能成为非实验性功能 (#11303)
- 更新 ConciseView 以使用 TargetObject（如果适用）(#11075)
- 修复 CompletionCompleters 公共方法中的 NullReferenceException (#11274)
- 修复非 Windows 平台上的单元线程状态检查 (#11301)
- 更新设置 PSModulePath 以连接进程和计算机环境变量 (#11276)
- 将 .NET Core 升级到 3.1.0 (#11260)
- 修复 $env:PATH 前面的 $PSHOME 检测 (#11141)
- 允许 pwsh 继承 $env:PSModulePath 并允许 powershell.exe 正确启动 (#11057)
- 迁移到 .NET Core 3.1 预览版 1 (#10798)
- 在文件系统提供程序中重构重新分析标记检查 (#10431)（感谢 @iSazonov！）
- 将 CR 和新行替换为脚本日志记录中的 0x23CE 字符 (#10616)
- 通过从 AppDomain.CurrentDomain.ProcessExit 中取消注册事件处理程序来修复资源泄漏 (#10626)
- 添加对 ActionPreference.Break 的支持，以便在生成调试、错误、信息、进度、详细消息或警告消息时中断以进入调试程序 (#8205)（感谢 @KirkMunro！）
- 允许在 PowerShell Core 内启用控制面板加载项，而无需指定 .CPL 扩展。 (#9828)
- 在 -split 运算符中支持负数 (#8960)（感谢 @ece-jacob-scott！）

### <a name="general-cmdlet-updates-and-fixes"></a>常规 Cmdlet 更新和修补程序

- 修复 Raspbian 上有关 UnixStat 实验性功能中设置文件更改日期的问题 (#11313)
- 将 -AsPlainText 添加到 ConvertFrom-SecureString (#11142)
- 为 WinCompat 添加了 WindowsPS 版本检查 (#11148)
- 修复某些 WinCompat 方案中的错误报告 (#11259)
- 添加本机二进制解析程序 (#11032)（感谢 @iSazonov！）
- 更新字符宽度的计算以正确遵循 CJK 字符 (#11262)
- 添加适用于 macOS 的 Unblock-File (#11137)
- 修复 Get-PSCallStack 中的回归 (#11210)（感谢 @iSazonov！）
- 使用作业 cmdlet 时删除 ScheduledJob 模块的自动加载 (#11194)
- 将 OutputType 添加到 Get-Error cmdlet 并保留原始类型名称 (#10856)
- 修复 SupportsVirtualTerminal 属性中的空引用 (#11105)
- 在 Get-WinEvent 中添加限制检查 (#10648)（感谢 @iSazonov！）
- 修复命令运行时，以便 StopUpstreamCommandsException 不会填充到 -ErrorVariable 中 (#10840)
- 将本机命令的输出编码设置为 [Console]::OutputEncoding (#10824)
- 支持示例中的多行代码块 (#10776)（感谢 @Greg-Smulko！）
- 将 Culture 参数添加到 Select-String cmdlet (#10943)（感谢 @iSazonov！）
- 修复带有尾随反斜杠的 Start-Job 工作目录路径 (#11041)
- ConvertFrom-Json：默认展开集合 (#10861)（感谢 @danstur！）
- 将 Group-Object cmdlet 的区分大小写的哈希表与 -CaseSensitive 和 -AsHashtable 开关一起使用 (#11030)（感谢 @vexx32！）
- 如果在重新生成路径以具有正确的大小写时未能枚举文件，则处理异常 (#11014)
- 修复 ConciseView 以显示活动，而不是 myCommand (#11007)
- 允许 Web cmdlet 忽略 HTTP 错误状态 (#10466)（感谢 @vdamewood！）
- 修复多个 CommandInfo 到 Get-Command 的管道传递 (#10929)
- 重新添加适用于 Windows 的 Get-Counter cmdlet (#10933)
- 使 ConvertTo-Json 将 [AutomationNull]::Value 和 [NullString]::Value 视为 $null (#10957)
- 删除 ipv6 地址中的括号以进行 SSH 远程处理 (#10968)
- 修复发送到 pwsh 的命令只是空白时发生的崩溃 (#10977)
- 添加了跨平台 Get-Clipboard 和 Set-Clipboard (#10340)
- 修复文件系统对象原始路径的设置，使其不包含额外的尾随反斜杠 (#10959)
- 支持 ConvertTo-Json 为 $null (#10947)
- 在 Windows 上重新添加 Out-Printer 命令 (#10906)
- 修复包含空格的 Start-Job -WorkingDirectory (#10951)
- 为 PSConfiguration.cs 中的设置获取 null 时返回默认值 (#10963)（感谢 @iSazonov！）
- 将 IO 异常处理为非终止 (#10950)
- 添加 GraphicalHost 程序集，以启用 Out-GridView、Show-Command 和 Get-Help -ShowWindow (#10899)
- 在 Get-HotFix 中通过管道获取 ComputerName (#10852)（感谢 @kvprasoon！）
- 修复参数的 Tab 自动补全，以便其将公共参数显示为可用 (#10850)
- 修复 GetCorrectCasedPath() 以首先检查是否在调用 First() 之前返回了任何系统文件条目 (#10930)
- 在 Start-Job 中将工作目录设置为当前目录 (#10920)（感谢 @iSazonov！）
- 将 TabExpansion2 更改为不需要 -CursorColumn 并将其视为 $InputScript.Length (#10849)
- 处理主机不返回屏幕的行或列的情况 (#10938)
- 修复在不支持主题色的主机上使用主题色的问题 (#10937)
- 重新添加 Update-List 命令 (#10922)
- 更新 Clear-RecycleBin 的 FWLink Id (#10925)
- 在 Tab 自动补全期间，如果无法读取文件属性，则跳过文件 (#10910)
- 重新添加适用于 Windows 的 Clear-RecycleBin (#10909)
- 添加 `$env:__SuppressAnsiEscapeSequences` 以控制是否在输出中包含 VT 转义序列 (#10814)
- 添加 -NoEmphasize 参数来为 Select-String 输出着色 (#8963)（感谢 @derek-xia！）
- 重新添加 Get-HotFix cmdlet (#10740)
- 使 Add-Type 可用于托管 PowerShell 的应用程序 (#10587)
- 在 LanguagePrimitives.IsNullLike() 中使用更有效的计算顺序 (#10781)（感谢 @vexx32！）
- 在 Format-Hex 中改进对混合集合管道输入和输入管道流的处理 (#8674)（感谢 @vexx32！）
- 当值与预期类型不匹配时，在 SSHConnection 哈希表中使用类型转换 (#10720)（感谢 @SeeminglyScience！）
- 修复在设置 -TotalCount 时的 Get-Content -ReadCount 0 行为 (#10749)（感谢 @eugenesmlv！）
- 在 Get-WinEvent 中改写“拒绝访问”错误消息 (#10639)（感谢 @iSazonov！）
- 为枚举或类型受约束的变量赋值启用 Tab 自动补全 (#10646)
- 删除导致格式设置问题的未使用的 SourceLength 远程处理属性 (#10765)
- 将 -Delimiter 参数添加到 ConvertFrom-StringData (#10665)（感谢 @steviecoaster！）
- 将 Invoke-Command 与 SSH 配合使用时，为 ScriptBlock 添加位置参数 (#10721)（感谢 @machgo！）
- 如果 ConciseView 有多个行但没有脚本名称，则显示行上下文信息 (#10746)
- 添加对文件系统提供程序的 \\wsl$\ 路径的支持 (#10674)
- 在分析器中添加 TokenKind.QuestionMark 的缺失令牌文本 (#10706)
- 将每个 ForEach-Object -Parallel 运行脚本的当前工作目录设置为调用脚本的同一位置。 (#10672)
- 将 api-ms-win-core-file-l1-2-2.dll 替换为 FindFirstStreamW 和 FindNextStreamW API 的 Kernell32.dll (#10680)（感谢 @iSazonov！）
- 调整帮助格式设置脚本，使其提高 StrictMode 容限 (#10563)
- 将 -SecurityDescriptorSDDL 参数添加到 New-Service (#10483)（感谢 @kvprasoon！）
- 删除信息性输出，合并 Test-Connection 中的 ping 使用情况 (#10478)（感谢 @vexx32！）
- 读取特殊重新分析点，而不访问它们 (#10662)（感谢 @iSazonov！）
- 将 Clear-Host 输出定向到终端 (#10681)（感谢 @iSazonov！）
- 添加向后换行符以使用 Format-Table 和 -Property 进行分组 (#10653)
- 从 Get-Random 上的 -InputObject 中删除 [ValidateNotNullOrEmpty] 以允许使用空字符串 (#10644)
- 使建议系统字符串距离算法不区分大小写 (#10549)（感谢 @iSazonov！）
- 修复 ForEach-Object -Parallel 输入处理中的 null 引用异常 (#10577)
- 添加 PowerShell Core 组策略定义 (#10468)
- 更新控制台主机以支持用于可组合性方案的 XTPUSHSGR/XTPOPSGR VT 控件序列。 (#10208)
- 将 WorkingDirectory 参数添加到 Start-Job (#10324)（感谢 @davinci26！）
- 删除导致断点更改被错误地复制到主机运行空间调试程序的事件处理程序 (#10503)（感谢 @KirkMunro！）
- 将 api-ms-win-core-job-12-1-0.dll 替换为 Microsoft.PowerShell.Commands.NativeMethods P/Invoke API 中的 Kernell32.dll (#10417)（感谢 @iSazonov！）
- 修复变量赋值和 -OutVariable 中 New-Service 的错误输出 (#10444)（感谢 @kvprasoon！）
- 修复有关退出代码、命令行参数和带有空格的路径的全局工具问题 (#10461)
- 修复到 OneDrive 的递归 - 更改 FindFirstFileEx() 以使用 SafeFindHandle 类型 (#10405)
- 如果 NVDA 屏幕读取器处于活动状态，则跳过在 Windows 上自动加载 PSReadLine (#10385)
- 将 built-with-PowerShell 模块版本增加到 7.0.0.0 (#10356)
- 如果已存在同名类型，则添加在 Add-Type 中引发错误 (#9609)（感谢 @iSazonov！）

### <a name="performance"></a>性能

- 避免在 Parser.SaveError 中使用关闭 (#11006)
- 改进在创建新的正则表达式实例时的缓存 (#10657)（感谢 @iSazonov！）
- 改进对 types.ps1xml、typesV3.ps1xml 和 GetEvent.types.ps1xml 中的 PowerShell 内置类型数据的处理 (#10898)
- 更新 PSConfiguration.ReadValueFromFile，使其加快运行速度并提高内存效率 (#10839)
- 添加较小的性能改进以进行运行空间初始化 (#10569)（感谢 @iSazonov！）
- 使 ForEach-Object 更快地用于其常用方案 (#10454)，并使用许多运行空间修复 ForEach-Object -Parallel 性能问题 (#10455)

### <a name="code-cleanup"></a>代码清理

- 更改注释和元素文本以符合 Microsoft 标准 (#11304)
- 清理 Compiler.cs 中的样式问题 (#10368)（感谢 @iSazonov！）
- 为 CommaDelimitedStringCollection 删除未使用的类型转换器 (#11000)（感谢 @iSazonov！）
- 清理 InitialSessionState.cs 中的样式 (#10865)（感谢 @iSazonov！）
- PSSession 类的代码清理 (#11001)
- 删除未正常运行的“在首次运行 Get-Help 时运行 Get-Help 中的 Update-Help”功能 (#10974)
- 修复样式问题 (#10998)（感谢 @iSazonov！）
- 清除：使用内置类型别名 (#10882)（感谢 @iSazonov！）
- 在查询 ExecutionPolicy 设置时删除未使用的设置密钥 ConsolePrompting 并避免创建不必要的字符串 (#10985)
- 禁用每日生成的更新通知检查 (#10903)（感谢 @bergmeister！）
- 恢复 #10338 中丢失的调试 API (#10808)
- 删除不再使用的 WorkflowJobSourceAdapter 引用 (#10326)（感谢 @KirkMunro！）
- 通过修复 PreserveSig 属性清除跳转列表代码中的 COM 接口 (#9899)（感谢 @weltkante！）
- 添加描述为何 -ia 不是 -InformationAction 通用参数别名的注释 (#10703)（感谢 @KirkMunro！）
- 将 InvokeCommandCmdlet.cs 重命名为 InvokeExpressionCommand.cs (#10659)（感谢 @kilasuit！）
- 添加与更新通知相关的细微代码清理 (#10698)
- 删除远程处理安装脚本中弃用的工作流逻辑 (#10320)（感谢 @KirkMunro！）
- 更新帮助格式以使用正确的大小写 (#10678)（感谢 @tnieto88！）
- 清除上个月提交的 CodeFactor 样式问题 (#10591)（感谢 @iSazonov！）
- 修复 PSTernaryOperator 实验性功能描述中的拼写错误 (#10586)（感谢 @bergmeister！）
- 将 ActionPreference.Suspend 枚举值转换为不受支持的保留状态，并删除对在首选项变量中使用 ActionPreference.Ignore 的限制 (#10317)（感谢 @KirkMunro！）
- 将 ArrayList 替换为 List\<T>，以获取更具可读性且更可靠的代码，而无需更改功能 (#10333)（感谢 @iSazonov！）
- 对 TestConnectionCommand 进行代码样式修复 (#10439)（感谢 @vexx32！）
- 清除 AutomationEngine 并删除额外的 SetSessionStateDrive 方法调用 (#10416)（感谢 @iSazonov！）
- 将默认的 ParameterSetName 重命名回 ConvertTo-Csv 和 ConvertFrom-Csv 的分隔符 (#10425)

### <a name="tools"></a>工具

- 为 SDKToUse 属性添加默认设置，使其在 VS 中生成 (#11085)
- Install-Powershell.ps1：添加参数以使用 MSI 安装 (#10921)（感谢 @MJECloud！）
- 为 install-powershell.ps1 添加基本示例 (#10914)（感谢 @kilasuit！）
- 使 Install-PowerShellRemoting.ps1 处理 PowerShellHome 参数中的空字符串 (#10526)（感谢 @Orca88！）
- 在 install-powershell.sh 中从 /etc/lsb-release 切换到 /etc/os-release (#10773)（感谢 @Himura2la！）
- 在 Windows 上检查每日版本中的 pwsh.exe 和 pwsh (#10738)（感谢 @centreboard！）
- 删除 installpsh-osx.sh 中不必要的 tap (#10752)
- 更新 install-powershell.ps1 以检查是否已安装每日生成 (#10489)

### <a name="tests"></a>测试

- 使不可靠的 DSC 测试挂起 (#11131)
- 修复字符串数据测试以正确验证哈希表的密钥 (#10810)
- 卸载测试模块 (#11061)（感谢 @iSazonov！）
- 增加测试 URL 重试的间隔时间 (#11015)
- 更新测试以准确描述测试操作。 (#10928)（感谢 @romero126！）
- 暂时跳过运行不正常的测试 TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)
- 使事件处理程序泄漏测试稳定 (#10790)
- 同步 CI YAML 中的大写 (#10767)（感谢 @RDIL！）
- 添加针对事件处理程序泄漏修复的测试 (#10768)
- 添加 Get-ChildItem 测试 (#10507)（感谢 @iSazonov！）
- 将测试的不明确语言从开关切换到参数以确保准确性 (#10666)（感谢 @romero126！）
- 向 ForEach-Object -Parallel 测试添加实验性检查 (#10354)（感谢 @KirkMunro！）
- 更新 Alpine 验证的测试 (#10428)

### <a name="build-and-package-improvements"></a>生成和包改进

- 修复协调包生成的 Nuget 包签名 (#11316)
- 更新 PowerShell 库和 NuGet 中的依赖项 (#11323)
- 将 Microsoft.ApplicationInsights 从 2.11.0 升级到 2.12.0 (#11305)
- 将 Microsoft.CodeAnalysis.CSharp 从 3.3.1 升级到 3.4.0 (#11265)
- 更新 Debian 10 和 11 的包 (#11236)
- 仅启用 RC 之前的实验性功能 (#11162)
- 更新 macOS 最低版本 (#11163)
- 将 NJsonSchema 从 10.0.27 升级到 10.0.28 (#11170)
- 更新 Preview.5 的 README.md 和 metadata.json 中的链接 (#10854)
- 选择 PowerShell 拥有的符合性测试的文件 (#10837)
- 允许生成 win7x86 .msix 包。 （内部 10515）
- 允许将语义版本传递给 NormalizeVersion 函数 (#11087)
- 将 .NET Core 框架升级到 3.1-preview.3 (#11079)
- 在 /src/Modules 中将 PSReadLine 从 2.0.0-beta5 升级到 2.0.0-beta6 (#11078)
- 将 Newtonsoft.Json 从 12.0.2 升级到 12.0.3 (#11037) (#11038)
- 添加 Debian 10、11 和 CentOS 8 包 (#11028)
- 使用 ReleaseDate 字段上传 Build-Info Json 文件 (#10986)
- 将 .NET Core 框架升级到 3.1-preview.2 (#10993)
- 启用 x86 MSIX 包的生成 (#10934)
- 更新 build.psm1 中的 dotnet SDK 安装脚本 URL (#10927)
- 将 Markdig.Signed 从 0.17.1 升级到 0.18.0 (#10887)
- 将 ThreadJob 从 2.0.1 升级到 2.0.2 (#10886)
- 更新 AppX 清单和打包模块以符合 MS Store 要求 (#10878)
- 将 PowerShell SDK 的包引用更新为 preview.5（内部 10295）
- 更新 ThirdPartyNotices.txt (#10834)
- 将 Microsoft.PowerShell.Native 升级到 7.0.0-preview.3 (#10826)
- 将 Microsoft.ApplicationInsights 从 2.10.0 升级到 2.11.0 (#10608)
- 将 NJsonSchema 从 10.0.24 升级到 10.0.27 (#10756)
- 向生成系统添加 MacPorts 支持 (#10736)（感谢 @Lucius-Q-User！）
- 将 PackageManagement 从 1.4.4 升级到 1.4.5 (#10728)
- 将 NJsonSchema 从 10.0.23 升级到 10.0.24 (#10635)
- 添加环境变量以区分 MSI 中的客户端/服务器遥测 (#10612)
- 将 PSDesiredStateConfiguration 从 2.0.3 升级到 2.0.4 (#10603)
- 将 Microsoft.CodeAnalysis.CSharp 从 3.2.1 升级到 3.3.1 (#10607)
- 更新为 Net Core 3.0 RTM (#10604)（感谢 @bergmeister！）
- 更新 .MSIX 打包，使版本符合 Windows 应用商店要求 (#10588)
- 将 PowerShellGet 版本从 2.2 升级到 2.2.1 (#10382)
- 将 PackageManagement 版本从 1.4.3 升级到 1.4.4 (#10383)
- 更新 7.0.0-preview.4 的 README.md 和 metadata.json（内部 10011）
- 将 .Net Core 3.0 版本从预览版 9 升级到 RC1 (#10552)（感谢 @bergmeister！）
- 修复 ExperimentalFeature 列表生成（内部 9996）
- 将 PSReadLine 版本从 2.0.0-beta4 升级到 2.0.0-beta5 (#10536)
- 修复发布生成脚本以设置发布标记
- 将 Microsoft.PowerShell.Native 的版本更新为 7.0.0-preview.2 (#10519)
- 升级到 Netcoreapp3.0 preview9 (#10484)（感谢 @bergmeister！）
- 确保每日协调生成，知道它是每日生成 (#10464)
- 更新组合包生成以发布每日生成 (#10449)
- 删除 appveyor 引用 (#10445)（感谢 @RDIL！）
- 将 NJsonSchema 版本从 10.0.22 升级到 10.0.23 (#10421)
- 取消删除 linux-x64 生成文件夹，因为 Alpine 的某些依赖项需要它 (#10407)

### <a name="documentation-and-help-content"></a>文档和帮助内容

- 将更改日志重构到每个版本的一个日志中 (#11165)
- 修复 PowerShell 7 联机帮助文档的 Fwlink (#11071)
- 更新 CONTRIBUTING.md (#11096)（感谢 @mklement0！）
- 修复 README.md 中的安装文档链接 (#11083)
- 向 install-powershell.ps1 脚本添加示例 (#11024)（感谢 @kilasuit！）
- 修复 CHANGELOG.md 中的 Select-String 强调和 Import-DscResource (#10890)
- 从 powershell-beginners-guide.md 中删除过期链接 (#10926)
- 合并稳定且提供服务的更改日志 (#10527)
- 更新生成文档中已使用的 .NET 版本 (#10775)（感谢 @Greg-Smulko！）
- 将 MSDN 中的链接替换为 powershell-beginners-guide.md 中的 docs.microsoft.com (#10778)（感谢 @iSazonov！）
- 修复中断的 DSC 概述链接 (#10702)
- 更新 Support_Question.md，以链接到作为另一个社区资源的堆栈溢出 (#10638)（感谢 @mklement0！）
- 将处理器体系结构添加到分发请求模板 (#10661)
- 将新的 PowerShell MoL 书籍添加到学习 PowerShell Docs (#10602)
- 更新 v6.1.6 和 v6.2.3 版本的 README.md 和元数据 (#10523)
- 修复 README.md 中的拼写错误 (#10465)（感谢 @vedhasp！）
- 将对 PSKoans 模块的引用添加到学习资源文档 (#10369)（感谢 @vexx32！）
- 更新 7.0.0-preview.3 的 README.md 和 metadata.json（内部 #10393）
