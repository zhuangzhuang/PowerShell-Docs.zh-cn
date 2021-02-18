---
ms.date: 12/14/2020
title: 使用 PowerShell 中的实验性功能
description: 列出了目前可用的实验性功能及其用法。
ms.openlocfilehash: 556ae8d877b670b119b7b5b958a52488aad16241
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500117"
---
# <a name="using-experimental-features-in-powershell"></a>使用 PowerShell 中的实验性功能

PowerShell 中的实验性功能支持提供了一种机制，可便于实验性功能与 PowerShell 或 PowerShell 模块中的现有稳定功能共存。

实验性功能是指设计尚未最终确定的功能。 此类功能可供用户进行测试和提供反馈。 一旦实验性功能最终确定下来，设计变更就变成了中断性变更。

> [!CAUTION]
> 实验性功能不适合在生产环境中使用，因为允许变更成为中断性变更。 实验性功能不受官方支持。 不过，我们非常期望收到你的反馈和 Bug 报告。 你可以在 [GitHub 源存储库](https://github.com/PowerShell/PowerShell/issues/new/choose)中提出问题。

若要详细了解如何启用或禁用这些功能，请参阅 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)。

## <a name="available-features"></a>可用功能

本文介绍了可用的实验性功能及其用法。

|                            名称                            |   6.2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive（PS 7.0 及更高版本中的主要支持）                        | &check; |         |         |         |
| PSUseAbbreviationExpansion（PS 7.0 及更高版本中的主要支持）         | &check; |         |         |         |
| PSNullConditionalOperators（PS 7.1 及更高版本中的主要支持）         |         | &check; |         |         |
| PSUnixFileStat（仅限非 Windows - PS 7.1 及更高版本中的主要支持）  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

在 PowerShell 7.0 中，此实验性功能可在 `Debug-Runspace` 和 `Debug-Job` cmdlet 上启用 BreakAll 参数，以允许用户在附加调试器时决定是否要让 PowerShell 在当前位置立即中断。

在 PowerShell 7.1 中，此实验性功能还可将“运行空间”参数添加到 `*-PSBreakpoint` cmdlet。

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

“运行空间”参数会指定一个“运行空间”对象，以便可在指定的运行空间中与断点进行交互。

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

在此示例中，将启动一个作业，并将一个断点设置为当运行 `Set-PSBreakPoint` 时中断。 运行空间存储在变量中，并通过“运行空间”参数传递到 `Get-PSBreakPoint` 命令。 然后，则可以在 `$breakpoint` 变量中查看断点。

## <a name="psansirendering"></a>PSAnsiRendering

该试验是在 PowerShell 7.2 中添加的。 借助此功能，可更改 PowerShell 引擎如何输出文本并添加 `$PSStyle` 自动变量来控制字符串输出的 ANSI 呈现。

```powershell
PS> $PSStyle

Name            MemberType Definition
----            ---------- ----------
Reset           Property   string AttributesOff {get;set;}
Background      Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;set;}
Blink           Property   string Blink {get;set;}
BlinkOff        Property   string BlinkOff {get;set;}
Bold            Property   string Bold {get;set;}
BoldOff         Property   string BoldOff {get;set;}
Foreground      Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;set;}
Formatting      Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;set;}
Hidden          Property   string Hidden {get;set;}
HiddenOff       Property   string HiddenOff {get;set;}
OutputRendering Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Reverse         Property   string Reverse {get;set;}
ReverseOff      Property   string ReverseOff {get;set;}
Italic          Property   string Standout {get;set;}
ItalicOff       Property   string StandoutOff {get;set;}
Underline       Property   string Underlined {get;set;}
Underline Off   Property   string UnderlinedOff {get;set;}
```

基成员会返回映射到其名称的 ANSI 转义序列的字符串。 值可设置为允许自定义。

有关详细信息，请参阅 [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

> [!NOTE]
> C# 开发人员可将 `PSStyle` 作为单一实例访问。 用法如下所示：
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle` 存在于 System.Management.Automation 命名空间中。

除了有权访问 `$PSStyle` 外，这还引入了对 PowerShell 引擎的更改。 PowerShell 格式系统已更新，现遵循 `$PSStyle.OutputRendering`。

- 添加了 `StringDecorated` 类型来处理 ANSI 转义字符串。
- 添加了 `string IsDecorated` 布尔属性，它会根据字符串是包含 ESC 还是 C1 CSI 来返回字符串是否包含 ANSI 转义序列。
- `Length` 属性仅返回没有 ANSI 转义序列的文本的长度。
- `StringDecorated Substring(int contentLength)` 方法会返回一个子字符串，该字符串从索引 0 处开始，一直到超出 ANSI 转义序列的内容长度。 如果表格式设置要截断字符串，并保留未占用可打印字符空间的 ANSI 转义序列，则需要使用此方法。
- `string ToString()` 方法保持不变，并返回字符串的纯文本版本。
- `Ansi` 参数为 true 时，`string ToString(bool Ansi)` 方法返回原始 ANSI 嵌入字符串。 否则，返回已删除 ANSI 转义序列的纯文本版本。

## <a name="psansiprogress"></a>PSAnsiProgress

该试验是在 PowerShell 7.2 中添加的。 此功能添加了 `$PSStyle.Progress` 成员并允许你控制进度视图栏呈现。

- `$PSStyle.Progress.Style` - 设置呈现样式的 ANSI 字符串。
- `$PSStyle.Progress.MaxWidth` - 设置视图的最大宽度。 控制台宽度设置为 `0`。
  默认为 `120`
- `$PSStyle.Progress.View` - 具有 `Minimal` 和 `Classic` 值的枚举。 `Classic` 为现有呈现，无更改。 `Minimal` 为单行最小呈现。 `Minimal` 为默认值。

下面的示例将呈现样式更新为最小进度栏。

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> 必须启用 PSAnsiRendering 试验性功能才能使用此功能。

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

在 CommandNotFoundException  后根据模糊匹配搜索来建议可能命令。

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

如果 `-replace` 运算符语句中的左操作数不是字符串，则此操作数会转换为字符串。

如果此功能是禁用的，`-replace` 运算符会执行区分区域性的字符串转换。
例如，如果区域性设置为“法语(fr)”，则值 `1.2` 会转换为字符串 `1,2`。

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

如果此功能是启用的：

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

支持在非 Windows 系统上编译为 MOF，并支持在没有 LCM 的情况下使用 `Invoke-DSCResource`。

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

此功能用于检查在 shell 中键入的命令，如果所有命令都是隐式远程处理代理命令，且组成了简单管道，那么这些命令会一起进行批处理，并作为一个远程管道进行调用。

示例：

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

如上所示，如果批处理功能是启用的，所有三个隐式远程处理代理命令（`Get-AllProcesses`、`Select-Custom`、`Group-Stuff`）都在远程会话中运行，并且管道中的结果是返回给客户端的唯一数据。 这不仅减少了在客户端与远程会话之间来回发送的数据量，还减少了对象序列化和反序列化的量。

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

如果使用 FileSystem 提供程序的 PSDrive 路径传递给本机命令，那么解析的文件路径就会传递给本机命令。 也就是说，像 `code temp:/test.txt` 这样的命令现在可以正常运行了。

另外，在 Windows 上，如果路径以 `~` 开头，那么路径会解析为完整路径，并传递给本机命令。 在这两种情况下，路径都会规范化为相关操作系统的目录分隔符。

- 如果路径不是 PSDrive 或 `~`（在 Windows 上），则不会进行路径规范化
- 如果路径是用单引号引住，则不会进行解析，而是被视为文本

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

启用此实验性功能后，从本机命令重定向的错误记录（例如，使用重定向运算符 (`2>&1`) 时）不会写入到 `$Error` 变量，并且首选项变量 `$ErrorActionPreference` 不会影响重定向的输出。

许多本机命令都会写入到 `stderr`，来将其作为获取额外信息的备用流。 查找错误时，此行为可能会导致混淆，如果将 `$ErrorActionPreference` 设置为静音输出的状态，则用户可能会丢失额外的输出信息。

当本机命令包含非零的退出代码时，`$?` 会设置为 `$false`。 如果退出代码为零，`$?` 会设置为 `$true`。

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

为 Null 条件成员访问运算符引入新的运算符，即 `?.` 和 `?[]`。 Null 成员访问运算符可用于标量类型和数组类型。 如果变量不为 null，则返回被访问成员的值。 如果变量的值为 null，则返回 null。

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

只有在 `$x` 不为 null 的情况下，才访问 `propname` 属性并返回它的值。 同样，只有在 `$x` 不为 null 的情况下，才使用索引器。 如果 `$x` 为 null，则返回 null。

`?.` 和 `?[]` 运算符是成员访问运算符，不允许在变量名称和运算符之间有空格。

由于 PowerShell 允许 `?` 作为变量名称的一部分，因此如果在使用运算符时变量名称和运算符之间没有空格，必须消除歧义。 为了消除歧义，变量必须在变量名称两边使用 `{}`（如 `${x?}?.propertyName` 或 `${y}?[0]`）。

> [!NOTE]
> 此功能已退出实验性阶段，并已成为 PowerShell 7.1 及更高版本中的主要支持功能。

## <a name="pstempdrive"></a>PSTempDrive

创建映射到用户的临时目录路径的 `TEMP:` PSDrive。

> [!NOTE]
> 此功能已退出实验性阶段，并已成为 PowerShell 7 及更高版本中的主要支持功能。

## <a name="psunixfilestat"></a>PSUnixFileStat

此功能提供了新行为，可以在文件系统提供程序的输出中添加来自 Unix stat  API 的数据，以促进生成更类似于 Unix 的文件列表。 它在名为 UnixStat  的文件系统提供程序中添加新的注释属性，其中包含来自基础 Unix 类型系统的 `stat(2)` API 的通用表达式。

`Get-ChildItem` 的输出应如下所示：

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

> [!NOTE]
> 此功能已退出实验性阶段，并已成为 PowerShell 7.1 及更高版本中的主要支持功能。

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

此功能支持对缩写的 cmdlet 和函数进行 Tab 自动补全：

例如：

- `i-psdf<tab>` 返回 `Import-PowerShellDataFile`。
- `u-akvmssdr<tab>` 返回 `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

这只适用于 Tab 自动补全（交互式使用），因此 `i-psdf` 在脚本中不是有效的 cmdlet 名称。

> [!NOTE]
> 此功能已退出实验性阶段，并已成为 PowerShell 7 及更高版本中的主要支持功能。

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

此功能在 PowerShell 中启用子系统插件模型。 利用此功能，可以将 `System.Management.Automation.dll` 的组件分隔到驻留在自己的程序集中的各个子系统。 这种隔离可减少核心 PowerShell 引擎的磁盘占用，并支持这些组件成为最小 PowerShell 安装的可选功能。

目前仅支持 CommandPredictor 子系统。 该子系统与 PSReadLine 模块一起使用，以提供自定义预测插件。 将来  ，Job、CommandCompleter、Remoting 和其他组件可以分隔到 `System.Management.Automation.dll` 外的子系统程序集。

试验性功能包括新的 cmdlet [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem)。 只有启用此功能时，此 cmdlet 才可用。 此 cmdlet 将返回有关系统上可用子系统的信息。
