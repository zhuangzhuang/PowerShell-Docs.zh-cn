---
description: 自定义 PowerShell 行为的变量。
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: d8eadf88d486de4758b56738089f27e8adc3bc91
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603789"
---
# <a name="about-preference-variables"></a>关于首选项变量

## <a name="short-description"></a>简短说明

自定义 PowerShell 行为的变量。

## <a name="long-description"></a>长说明

PowerShell 包含一组变量，使你能够自定义其行为。 这些首选项变量的工作方式类似于基于 GUI 的系统中的选项。

首选项变量将影响 PowerShell 操作环境以及在环境中运行的所有命令。 在许多情况下，cmdlet 具有可用于覆盖特定命令的首选项行为的参数。

下表列出了首选项变量及其默认值。

|             变量             |       默认值       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | 高                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | 继续                  |
| `$ErrorView`                     | ConciseView               |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | 错误 (未记录)         |
| `$LogCommandLifecycleEvent`      | 错误 (未记录)         |
| `$LogEngineHealthEvent`          |  (记录为 True)              |
| `$LogEngineLifecycleEvent`       |  (记录为 True)              |
| `$LogProviderLifecycleEvent`     |  (记录为 True)              |
| `$LogProviderHealthEvent`        |  (记录为 True)              |
| `$MaximumHistoryCount`           | 4096                      |
| `$OFS`                           |  (空格字符 (`" "`) # A3 |
| `$OutputEncoding`                | UTF8Encoding 对象       |
| `$ProgressPreference`            | 继续                  |
| `$PSDefaultParameterValues`      |  (无-) 哈希表 |
| `$PSEmailServer`                 | （无）                    |
| `$PSModuleAutoLoadingPreference` | 全部                       |
| `$PSSessionApplicationName`      | wsman                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | 请参阅 [$PSSessionOption](#pssessionoption) |
| `$Transcript`                    | （无）                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | 继续                  |
| `$WhatIfPreference`              | False                     |

PowerShell 包括存储用户首选项的以下环境变量。 有关这些环境变量的详细信息，请参阅 [about_Environment_Variables](about_Environment_Variables.md)。

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> 首选项变量的更改仅对脚本和函数有效，前提是这些脚本或函数是在使用首选项的作用域中定义的。 有关详细信息，请参阅 [about_Scopes](about_Scopes.md)。

## <a name="working-with-preference-variables"></a>使用首选项变量

本文档介绍每个首选项变量。

若要显示特定首选项变量的当前值，请键入该变量的名称。 例如，下面的命令显示 `$ConfirmPreference` 变量的值。

```powershell
 $ConfirmPreference
```

```Output
High
```

若要更改变量的值，请使用赋值语句。 例如，下面的语句将 `$ConfirmPreference` 参数的值更改为 " **中**"。

```powershell
$ConfirmPreference = "Medium"
```

您设置的值特定于当前 PowerShell 会话。 若要使变量在所有 PowerShell 会话中生效，请将它们添加到 PowerShell 配置文件中。 有关详细信息，请参阅 [about_Profiles](about_Profiles.md)。

## <a name="working-remotely"></a>远程工作

在远程计算机上运行命令时，远程命令仅服从远程计算机的 PowerShell 客户端中的首选项设置。 例如，当你运行远程命令时，远程计算机的变量的值将 `$DebugPreference` 决定 PowerShell 对调试消息的响应方式。

有关远程命令的详细信息，请参阅 [about_Remote](about_Remote.md)。

### <a name="confirmpreference"></a>\$ConfirmPreference

确定在运行 cmdlet 或函数之前 PowerShell 是否自动提示你进行确认。

`$ConfirmPreference`变量的有效值为 "**高**"、"**中**" 或 "**低**"。 为 cmdlet 和函数分配了 **高**、 **中** 或 **低** 的风险。 当变量的值 `$ConfirmPreference` 小于或等于分配给 cmdlet 或函数的风险时，PowerShell 会在运行 cmdlet 或函数之前自动提示你进行确认。

如果该变量的值 `$ConfirmPreference` 为 " **无**"，则在运行 cmdlet 或函数之前，PowerShell 从不会自动提示您。

若要更改会话中所有 cmdlet 和函数的确认行为，请更改 `$ConfirmPreference` 变量的值。

若要为 `$ConfirmPreference` 单个命令重写，请使用 cmdlet 或函数的 **Confirm** 参数。 若要请求确认，请使用 `-Confirm` 。 若要取消确认，请使用 `-Confirm:$false` 。

有效值为 `$ConfirmPreference` ：

- **无**：不自动提示 PowerShell。 若要请求确认特定命令，请使用 cmdlet 或函数的 **Confirm** 参数。
- **低**：在运行具有低、中或高风险的 cmdlet 或函数之前，PowerShell 会提示进行确认。
- **中**： PowerShell 在运行 cmdlet 之前提示进行确认，或使用中等或高风险运行这些功能。
- **高**： PowerShell 在运行 cmdlet 或具有高风险的功能之前提示确认。

#### <a name="detailed-explanation"></a>详细说明

PowerShell 可以在执行操作之前自动提示你进行确认。 例如，当 cmdlet 或函数严重影响系统以删除数据或使用大量系统资源时。

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

风险的估计值是指作为其 **ConfirmImpact** 的 cmdlet 或函数的属性。 用户无法更改它。

可能会给系统带来风险的 cmdlet 和函数具有 **Confirm** 参数，可用于请求或取消对单个命令的确认。

由于大多数 cmdlet 和函数使用 **默认的风险** 值 **ConfirmImpact**，而默认值为 "高"，因此 `$ConfirmPreference` 很少发生自动确认。 但是，可以通过将的值更改为 "中" `$ConfirmPreference` 或 "**低**" 来激活自动确认。

#### <a name="examples"></a>示例

此示例显示 `$ConfirmPreference` 变量的默认值（ **高**）的效果。 **高** 值仅用于确认高风险 cmdlet 和函数。 由于大多数 cmdlet 和函数都是中等风险，因此它们不会自动确认并 `Remove-Item` 删除文件。 添加 `-Confirm` 到命令会提示用户进行确认。

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

使用 `-Confirm` 请求确认。

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

下面的示例演示了将的值更改为 " `$ConfirmPreference` **中**" 的效果。 由于大多数 cmdlet 和函数都是中等风险，因此它们会自动得到确认。 若要禁止显示单个命令的确认提示，请使用值为的 **Confirm** 参数 `$false` 。

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$DebugPreference

确定 PowerShell 如何响应脚本、cmdlet 或提供程序所生成的消息，或 `Write-Debug` 命令行中的命令。

某些 cmdlet 显示调试消息，这些消息通常是为程序员和技术支持专业人员设计的技术消息。 默认情况下，调试消息不会显示，但你可以通过更改的值来显示调试消息 `$DebugPreference` 。

可以使用 cmdlet 的 **Debug** 通用参数来显示或隐藏特定命令的调试消息。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止**：显示调试消息，并停止执行。 向控制台写入错误。
- **Inquire**：显示调试消息，并询问您是否要继续。 将 **Debug** common 参数添加到命令时，在将该命令配置为生成调试消息时，将更改该变量的值 `$DebugPreference` 以进行 **查询**。
- **继续**：显示调试消息，并继续执行。
- **SilentlyContinue**： (默认值) 不起作用。 调试消息不会显示，执行将继续进行而不中断。

#### <a name="examples"></a>示例

下面的示例演示在 `$DebugPreference` 命令行中输入命令时更改值的影响 `Write-Debug` 。
更改会影响所有调试消息，包括 cmdlet 和脚本生成的消息。 示例显示了 **Debug** 参数，该参数显示或隐藏与单个命令相关的调试消息。

此示例显示 `$DebugPreference` 变量的默认值 **SilentlyContinue** 的效果。 默认情况下， `Write-Debug` cmdlet 的调试消息不会显示并且处理将继续进行。 使用 **Debug** 参数时，它将覆盖单个命令的首选项。 将显示调试消息。

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

此示例显示了 `$DebugPreference` 具有 **Continue** 值的效果。 调试消息随即显示，命令继续处理。

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

此示例使用 **Debug** 参数，其中的值 `$false` 为，以禁止将消息用于单个命令。 不显示调试消息。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

此示例显示 `$DebugPreference` 设置为 " **停止** " 值的效果。 将显示调试消息，并停止该命令。

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

此示例使用 **Debug** 参数，其中的值 `$false` 为，以禁止将消息用于单个命令。 调试消息不会显示并且不会停止处理。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

此示例显示了 `$DebugPreference` 设置为 **查询** 值的效果。 将显示调试消息，并提示用户进行确认。

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

此示例使用 **Debug** 参数，其中的值 `$false` 为，以禁止将消息用于单个命令。 调试消息不会显示并继续处理。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

确定 PowerShell 如何响应非终止错误，该错误不会停止 cmdlet 处理。 例如，在命令行或脚本、cmdlet 或提供程序中，如 cmdlet 生成的错误 `Write-Error` 。

可以使用 cmdlet 的 **ErrorAction** 通用参数来覆盖特定命令的首选项。

有效值如下：

- **Break** -在发生错误或引发异常时输入调试器。
- **继续**： (默认值) 显示错误消息并继续执行。
- **Ignore**：禁止显示错误消息并继续执行命令。 **Ignore** 值专用于按命令使用，而不是用作保存的首选项。 **Ignore** 不是变量的有效值 `$ErrorActionPreference` 。
- **Inquire**：显示错误消息，并询问您是否要继续。
- **SilentlyContinue**：不起作用。 错误消息不会显示，执行将继续进行而不中断。
- **停止**：显示错误消息并停止执行。 除生成的错误外， **停止** 值还会将 ActionPreferenceStopException 对象生成到错误流。
  流 (stream)
- **挂起**：自动挂起工作流作业以便进一步进行调查。 调查后，工作流可以恢复。 " **挂起** " 值适用于按命令使用，而不是用作保存的首选项。 **挂起** 不是变量的有效值 `$ErrorActionPreference` 。

`$ErrorActionPreference`**ErrorAction** 参数不会影响 PowerShell 响应终止处理停止 cmdlet 的错误的方式。 有关 **ErrorAction** 通用参数的详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

#### <a name="examples"></a>示例

这些示例显示变量的不同值的影响 `$ErrorActionPreference` 。 **ErrorAction** 参数用于重写 `$ErrorActionPreference` 值。

此示例显示 `$ErrorActionPreference` 默认值 " **Continue**"。 生成非终止错误。 消息随即显示并且处理继续。

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error: Test Error
Hello World
```

此示例显示 `$ErrorActionPreference` 默认值 **Inquire**。 将生成一个错误，并显示一个操作提示。

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

此示例显示 `$ErrorActionPreference` 设置为 **SilentlyContinue**。
错误消息将被取消。

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

此示例显示 `$ErrorActionPreference` 设置为 " **停止**"。 它还显示生成到变量的额外对象 `$Error` 。

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error: Test Error

ErrorRecord                 : Test Error
WasThrownFromThrowStatement : False
TargetSite                  : System.Collections.ObjectModel.Collection`1[System.Management.Automation.PSObject]
                              Invoke(System.Collections.IEnumerable)
StackTrace                  :    at System.Management.Automation.Runspaces.PipelineBase.Invoke(IEnumerable input)
                                 at Microsoft.PowerShell.Executor.ExecuteCommandHelper(Pipeline tempPipeline,
                              Exception& exceptionThrown, ExecutionOptions options)
Message                     : The running command stopped because the preference variable "ErrorActionPreference" or
                              common parameter is set to Stop: Test Error
Data                        : {System.Management.Automation.Interpreter.InterpretedFrameInfo}
InnerException              :
HelpLink                    :
Source                      : System.Management.Automation
HResult                     : -2146233087

Write-Error: Test Error
```

### <a name="errorview"></a>\$ErrorView

确定 PowerShell 中错误消息的显示格式。

有效值如下：

- **ConciseView**： (默认值) 提供简洁的错误消息和高级模块生成器的重构视图。 如果错误来自命令行，则为单行错误消息。 否则，你将收到一条多行错误消息，其中包含错误和指向错误显示在该行中出现位置的错误。 如果终端支持虚拟终端，则使用 ANSI 颜色代码提供颜色着色。 可以在处更改强调颜色 `$Host.PrivateData.ErrorAccentColor` 。 使用 `Get-Error` cmdlet 提供完全限定的错误的综合性详细视图，包括内部异常。

  PowerShell 7 中添加了 **ConciseView** 。

- **NormalView**：为大多数用户设计的详细视图。 包含错误说明和错误中涉及的对象的名称。

- **CategoryView**：一种简洁的结构化视图，适用于生产环境。 其格式如下所示：

  {Category}： ( {TargetName}： {TargetType} ) ： [{Activity}]，{Reason}

有关 **CategoryView** 中的字段的详细信息，请参阅 [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) 类。

#### <a name="examples"></a>示例

此示例演示当的值 `$ErrorView` 为默认值 **ConciseView** 时，如何显示错误。 `Get-ChildItem` 用于查找不存在的目录。

```powershell
Get-ChildItem -path 'C:\NoRealDirectory'
```

```Output
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.
```

此示例演示当的值 `$ErrorView` 为默认值 **ConciseView** 时，如何显示错误。 `Script.ps1` 运行，并引发语句中的错误 `Get-Item` 。

```powershell
./Script.ps1
```

```Output
Get-Item: C:\Script.ps1
Line |
  11 | Get-Item -Path .\stuff
     | ^ Cannot find path 'C:\demo\stuff' because it does not exist.
```

此示例演示如何在的值 `$ErrorView` 更改为 **NormalView** 时显示错误。 `Get-ChildItem` 用于查找不存在的文件。

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

此示例演示当的值 `$ErrorView` 更改为 **CategoryView** 时出现的相同错误。

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

此示例演示的值 `$ErrorView` 仅影响错误显示。 它不会更改自动变量中存储的错误对象的结构 `$Error` 。 有关 `$Error` 自动变量的信息，请参阅 [about_automatic_variables](about_Automatic_Variables.md)。

下面的命令使用与错误数组中的最新错误（**元素 0**）关联的 **ErrorRecord** 对象，并在列表中设置所有错误对象属性的格式。

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

确定显示中包含多少个枚举项。 此变量不影响基础对象，仅影响显示。 如果的值 `$FormatEnumerationLimit` 小于枚举项的数目，则 PowerShell 会添加一个省略号 (`...`) 以指示未显示的项。

**有效值**：整数 (`Int32`) 

**默认值**：4

#### <a name="examples"></a>示例

此示例演示如何使用 `$FormatEnumerationLimit` 变量来改善枚举项的显示。

此示例中的命令将生成一个表，该表列出了在计算机上运行的所有服务，一个用于 **运行** 服务，另一个用于 **已停止** 的服务。 它使用 `Get-Service` 命令获取所有服务，然后将结果通过管道发送到 `Group-Object` cmdlet，后者按服务状态对结果进行分组。

结果是一个表，其中列出了 " **名称** " 列中的状态和 " **组** " 列中的进程。 若要更改列标签，请使用哈希表，请参阅 [about_Hash_Tables](about_Hash_Tables.md)。 有关详细信息，请参阅 [格式表](xref:Microsoft.PowerShell.Utility.Format-Table)中的示例。

查找的当前值 `$FormatEnumerationLimit` 。

```powershell
$FormatEnumerationLimit
```

```Output
4
```

列出按 **状态** 分组的所有服务。 每个状态的 " **组** " 列中最多列出了四个服务，因为 `$FormatEnumerationLimit` 值为 **4**。

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

若要增加列出的项数，请将的值增加 `$FormatEnumerationLimit` 到 **1000**。 使用 `Get-Service` 和 `Group-Object` 显示服务。

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

`Format-Table`与 **Wrap** 参数一起使用以显示服务列表。

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

`$InformationPreference`利用变量，可以设置要向用户显示的信息流首选项。 具体而言，是通过添加 [写入信息](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet 添加到命令或脚本的信息性消息。 如果使用 **InformationAction** 参数，则其值将覆盖变量的值 `$InformationPreference` 。 `Write-Information` 是在 PowerShell 5.0 中引入的。

有效值如下：

- **Stop**：在命令出现时停止命令或脚本 `Write-Information` 。
- **Inquire**：显示你在命令中指定的信息性消息 `Write-Information` ，然后询问你是否要继续。
- **继续**：显示信息性消息，并继续运行。
- "**挂起**" 仅适用于 PowerShell 6 和更高版本中不支持的工作流。
- **SilentlyContinue**： (默认值) 不起作用。 不显示信息性消息，该脚本将继续进行而不中断。

### <a name="logevent"></a>\$Log * 事件

**日志 * 事件** 首选项变量确定哪些类型的事件将写入事件查看器中的 PowerShell 事件日志。 默认情况下，只记录引擎和提供程序事件。 但你可以使用 **log * 事件** 首选项变量来自定义日志，如记录有关命令的事件。

**日志 * 事件** 首选项变量如下所示：

- `$LogCommandHealthEvent`：记录命令初始化和处理中的错误和异常。 默认值为 `$false` (未记录) 。
- `$LogCommandLifecycleEvent`：记录命令和命令管道的启动和停止，以及命令发现中的安全异常。 默认值为 `$false` (未记录) 。
- `$LogEngineHealthEvent`：记录会话的错误和失败。 默认值为 `$true` (记录) 。
- `$LogEngineLifecycleEvent`：记录会话的开始和结束。 默认值为 `$true` (记录) 。
- `$LogProviderHealthEvent`：记录提供程序错误，如读取和写入错误、查找错误以及调用错误。 默认值为 `$true` (记录) 。
- `$LogProviderLifecycleEvent`：日志添加和删除 PowerShell 提供程序。 默认值为 `$true` (记录) 。 有关 PowerShell 提供程序的信息，请参阅 [about_Providers](about_Providers.md)。

若要启用 **Log * 事件**，请键入变量，其值 `$true` 为，例如：

```powershell
$LogCommandLifeCycleEvent = $true
```

若要禁用事件类型，请使用值键入变量 `$false` ，例如：

```powershell
$LogCommandLifeCycleEvent = $false
```

启用的事件仅对当前 PowerShell 控制台有效。 若要将配置应用到所有控制台，请将变量设置保存到 PowerShell 配置文件中。 有关详细信息，请参阅 [about_Profiles](about_Profiles.md)。

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

确定在当前会话的命令历史记录中保存的命令数。

**有效值**： 1-32768 (`Int32`) 

**默认值**：4096

若要确定命令历史记录中当前保存的命令数，请键入：

```powershell
(Get-History).Count
```

若要查看已保存在会话历史记录中的命令，请使用 `Get-History` cmdlet。 有关详细信息，请参阅 [about_History](about_History.md)。

### <a name="ofs"></a>\$.OFS

 (.OFS 的输出字段分隔符) 指定将转换为字符串的数组元素分隔的字符。

**有效值**：任何字符串。

**默认值**： Space

默认情况下，该 `$OFS` 变量不存在，并且输出文件分隔符为空格，但您可以添加此变量并将其设置为任何字符串。 可以 `$OFS` 通过键入在会话中更改的值 `$OFS="<value>"` 。

> [!NOTE]
> 如果需要在 `" "` 脚本、模块或配置输出中 () 的空间的默认值，请小心，不要在 `$OFS` 代码中的其他位置更改默认值。

#### <a name="examples"></a>示例

此示例显示当数组转换为字符串时，将使用空格来分隔值。 在这种情况下，整数数组存储在一个变量中，然后将该变量强制转换为字符串。

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

若要更改分隔符，请 `$OFS` 通过为变量赋值来添加变量。
变量必须命名为 `$OFS` 。

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

若要还原默认行为，可以 () 分配一个空格， `" "` `$OFS` 或删除该变量。 以下命令将删除该变量，然后验证该分隔符是否为空格。

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

确定 PowerShell 在向其他应用程序发送文本时所使用的字符编码方法。

例如，如果应用程序将 Unicode 字符串返回到 PowerShell，你可能需要将值更改为 **UnicodeEncoding** ，以便正确发送字符。

有效值如下：派生自编码类的对象，例如 **ASCIIEncoding**、 **SBCSCodePageEncoding**、 **UTF7Encoding**、 **UTF8Encoding**、 **UTF32Encoding** 和 **UnicodeEncoding**。

**默认值**： UTF8Encoding 对象 (UTF8Encoding) 

#### <a name="examples"></a>示例

此示例演示如何在使用 Unicode 字符（如中文）为语言本地化的计算机上，使 Windows **findstr.exe** 命令在 PowerShell 中运行。

第一个命令查找值 `$OutputEncoding` 。 由于值是编码对象，因此只显示其 **encoding.encodingname** 属性。

```powershell
$OutputEncoding.EncodingName
```

在此示例中， **findstr.exe** 命令用于搜索文件中存在的两个中文字符 `Test.txt` 。 在 Windows 命令提示符下运行此 **findstr.exe** 命令时 (**cmd.exe**) ， **findstr.exe** 将查找文本文件中的字符。 但是，当你在 PowerShell 中运行相同的 **findstr.exe** 命令时，将找不到这些字符，因为 PowerShell 会将它们发送到 ASCII 文本中的 **findstr.exe** 而不是 Unicode 文本。

```powershell
findstr <Unicode-characters>
```

若要在 PowerShell 中运行命令，请将的值设置 `$OutputEncoding` 为控制台的 **OutputEncoding** 属性的值，该属性基于为 Windows 选择的区域设置。 由于 **OutputEncoding** 是控制台的静态属性，因此请在命令中使用双冒号 (`::`) 。

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

编码更改后， **findstr.exe** 命令将查找 Unicode 字符。

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

确定 PowerShell 如何响应脚本、cmdlet 或提供程序生成的进度更新，如 [写入-进度](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet 生成的进度栏。
`Write-Progress`Cmdlet 可创建显示命令状态的进度栏。

有效值如下：

- **停止**：不显示进度栏。 相反，它将显示一条错误消息并停止执行。
- **Inquire**：不显示进度栏。 提示继续操作。 如果你通过 `Y` 或 `A` 进行回复，它会显示进度栏。
- **继续**： (默认值) 显示进度栏，并继续执行操作。
- **SilentlyContinue**：执行命令，但不显示进度栏。

### <a name="psemailserver"></a>\$PSEmailServer

指定用于发送电子邮件的默认电子邮件服务器。 发送电子邮件的 cmdlet （如 [send-mailmessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet）使用此首选项变量。

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

为 cmdlet 和高级函数的参数指定默认值。
的值 `$PSDefaultParameterValues` 是一个哈希表，其中的键由 cmdlet 名称和参数名称组成，该名称由冒号 (`:`) 分隔。 值是指定的自定义默认值。

`$PSDefaultParameterValues` 是在 PowerShell 3.0 中引入的。

有关此首选项变量的详细信息，请参阅 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

启用和禁用会话中模块的自动导入。 **All** 为默认值。 无论变量的值是什么，都可以使用 [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 导入模块。

有效值是：

- **所有**：首次使用时自动导入模块。 若要导入模块，请获取或使用模块中的任何命令。 例如，使用 `Get-Command`。
- **ModuleQualified**：仅当用户使用模块中的模块限定名称时，才会自动导入模块。 例如，如果用户键入，则 `MyModule\MyCommand` PowerShell 将导入 **MyModule** 模块。
- **None**：在会话中禁用自动导入模块。 若要导入模块，请使用 `Import-Module` cmdlet。

有关自动导入模块的详细信息，请参阅 [about_Modules](about_Modules.md)。

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

指定远程命令的默认应用程序名称，该命令使用 (WS-MANAGEMENT) 技术管理的 "Web 服务"。 有关详细信息，请参阅 [关于 Windows 远程管理](/windows/win32/winrm/about-windows-remote-management)。

系统默认应用程序名称为 `WSMAN` ，但你可以使用此首选项变量更改默认值。

应用程序名称是连接 URI 中的最后一个节点。 例如，下面的示例 URI 中的应用程序名称为 `WSMAN` 。

`http://Server01:8080/WSMAN`

如果远程命令未指定连接 URI 或应用程序名称，则使用默认应用程序名称。

**WinRM** 服务使用应用程序名称来选择用于处理连接请求的侦听器。 参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值相匹配。

若要覆盖系统默认值和此变量的值，并为特定会话选择不同的应用程序名称，请使用 [新的 PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [Enter-Pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession)或 [调用命令](xref:Microsoft.PowerShell.Core.Invoke-Command)cmdlet 的 **ConnectionURI** 或 **ApplicationName** 参数。

`$PSSessionApplicationName`首选项变量是在本地计算机上设置的，但它指定了远程计算机上的侦听器。 如果你指定的应用程序名称在远程计算机上不存在，则用于建立会话的命令将失败。

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

指定用于在当前会话中创建的 **pssession** 的默认会话配置。

此首选项变量是在本地计算机上设置的，但它指定了位于远程计算机上的会话配置。

变量的值 `$PSSessionConfigurationName` 是完全限定的资源 URI。

默认值 `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` 表示远程计算机上的 **Microsoft PowerShell** 会话配置。

如果只指定配置名称，则会预置以下架构 URI：

`http://schemas.microsoft.com/PowerShell/`

你可以使用 `New-PSSession` 、 `Enter-PSSession` 或 cmdlet 的 ConfigurationName 参数覆盖默认值，并为特定会话选择不同的会话配置 `Invoke-Command` 。

您可以随时更改此变量的值。 当你执行此操作时，请记住，你选择的会话配置必须在远程计算机上存在。 否则，创建使用会话配置的会话的命令将失败。

当远程用户创建连接到此计算机的会话时，此首选项变量不会确定使用的本地会话配置。
但是，你可以使用本地会话配置的权限来确定哪些用户可以使用它们。

### <a name="pssessionoption"></a>\$PSSessionOption

建立远程会话中高级用户选项的默认值。
这些选项首选项会替代会话选项的系统默认值。

`$PSSessionOption`变量包含 **PSSessionOption** 对象。 有关详细信息，请参阅 [PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption)。
对象的每个属性都表示一个会话选项。 例如， **NoCompression** 属性将在会话期间启用数据压缩。

默认情况下，该 `$PSSessionOption` 变量包含一个 **PSSessionOption** 对象，该对象具有所有选项的默认值，如下所示。

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

有关这些选项的说明和详细信息，请参阅 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。 有关远程命令和会话的详细信息，请参阅 [about_Remote](about_Remote.md) 和 [about_PSSessions](about_PSSessions.md)。

若要更改首选项变量的值 `$PSSessionOption` ，请使用 `New-PSSessionOption` cmdlet 创建一个 **PSSessionOption** 对象，该对象具有你喜欢的选项值。 将输出保存在一个名为的变量中 `$PSSessionOption` 。

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

若要 `$PSSessionOption` 在每个 powershell 会话中使用首选项变量，请将 `New-PSSessionOption` 创建该变量的命令添加 `$PSSessionOption` 到 powershell 配置文件中。 有关详细信息，请参阅 [about_Profiles](about_Profiles.md)。

您可以为特定的远程会话设置自定义选项。 您设置的选项优先于系统默认值和 `$PSSessionOption` 首选项变量的值。

若要设置自定义会话选项，请使用 `New-PSSessionOption` cmdlet 创建 **PSSessionOption** 对象。 然后，在创建会话的 cmdlet （例如、和）中，使用 **PSSessionOption** 对象作为 **SessionOption** 参数的值 `New-PSSession` `Enter-PSSession` `Invoke-Command` 。

### <a name="transcript"></a>$Transcript

用于 `Start-Transcript` 指定脚本文件的名称和位置。 如果未指定 **path** 参数的值，则将 `Start-Transcript` 使用全局变量的值中的路径 `$Transcript` 。 如果尚未创建此变量，请将这些 `Start-Transcript` 脚本 `$Home\My Documents` 作为文件存储在目录中 `\PowerShell_transcript.<time-stamp>.txt` 。

### <a name="verbosepreference"></a>\$VerbosePreference

确定 PowerShell 如何响应脚本、cmdlet 或提供程序生成的详细消息，如 [写入-详细](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet 生成的消息。
详细消息描述执行命令所执行的操作。

默认情况下，不显示详细消息，但是您可以通过更改的值来更改此行为 `$VerbosePreference` 。

可以使用 cmdlet 的 **verbose** 通用参数来显示或隐藏特定命令的详细消息。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止**：显示详细消息和错误消息，然后停止执行。
- **Inquire**：显示详细消息，然后显示一条提示，询问您是否要继续。
- **继续**：显示详细消息，然后继续执行。
- **SilentlyContinue**： (默认) 不显示详细消息。 继续执行。

#### <a name="examples"></a>示例

这些示例显示了不同的值的效果 `$VerbosePreference` ，并显示了 **Verbose** 参数重写首选项值。

此示例显示 **SilentlyContinue** 值（这是默认值）的效果。 此命令使用 **message** 参数，但不会将消息写入 PowerShell 控制台。

```powershell
Write-Verbose -Message "Verbose message test."
```

使用 **详细** 参数时，将写入消息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

此示例显示了 **Continue** 值的效果。 `$VerbosePreference`变量设置为 **Continue** ，并显示消息。

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

此示例使用 **Verbose** 参数，该参数的值为 `$false` ，它将重写 **Continue** 值。 不显示此消息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

此示例显示了 **停止** 值的影响。 `$VerbosePreference`变量设置为 "**停止**"，并显示消息。 命令已停止。

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

此示例使用 **Verbose** 参数，该参数的值为 `$false` ，它将替代 **停止** 值。 不显示此消息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

此示例显示了 **Inquire** 值的效果。 `$VerbosePreference`变量设置为 **Inquire**。 消息随即显示，并提示用户进行确认。

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

此示例使用带有 `$false` 替代 **Inquire** 值的值的详细参数。 系统不会提示用户并且不显示消息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

确定 PowerShell 如何响应脚本、cmdlet 或提供程序生成的警告消息，如 [写入警告](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet 生成的消息。

默认情况下，会显示警告消息并继续执行，但你可以通过更改的值来更改此行为 `$WarningPreference` 。

可以使用 cmdlet 的 **WarningAction** common 参数确定 PowerShell 如何响应特定命令中的警告。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止**：显示警告消息和错误消息，然后停止执行。
- **Inquire**：显示警告消息，然后提示继续操作。
- **继续**： (默认值) 显示警告消息，然后继续执行。
- **SilentlyContinue**：不显示警告消息。 继续执行。

#### <a name="examples"></a>示例

这些示例显示了不同的值的效果 `$WarningPreference` 。
**WarningAction** 参数将覆盖首选项值。

此示例显示默认值的效果，然后 **继续**。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

此示例使用值为 **SilentlyContinue** 的 **WarningAction** 参数来禁止显示警告。 不显示此消息。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

此示例将 `$WarningPreference` 变量更改为 **SilentlyContinue** 值。 不显示此消息。

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

此示例在生成警告时使用 **WarningAction** 参数停止。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

此示例将 `$WarningPreference` 变量更改为 **Inquire** 值。 系统将提示用户进行确认。

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

此示例使用值为 **SilentlyContinue** 的 **WarningAction** 参数。 命令将继续执行，并且不会显示任何消息。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

此示例将 `$WarningPreference` 值更改为 " **Stop**"。

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

此示例将 **WarningAction** 与 **Inquire** 值一起使用。 出现警告时，系统将提示用户。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$WhatIfPreference

确定是否自动为支持它的每个命令启用 **WhatIf** 。 启用 **WhatIf** 后，该 cmdlet 会报告命令的预期效果，但不会执行命令。

有效值如下：

- **False** (**0**，未启用) ： (默认) **WhatIf** 不自动启用。 若要手动启用此参数，请使用 cmdlet 的 **WhatIf** 参数。
- **True** (**1**，已启用) ：自动对支持该功能的任何命令启用 **WhatIf** 。 用户可以使用值为 **False** 的 **WhatIf** 参数手动禁用它，如 `-WhatIf:$false` 。

#### <a name="examples"></a>示例

这些示例显示了不同的值的效果 `$WhatIfPreference` 。
它们演示如何使用 **WhatIf** 参数覆盖特定命令的首选项值。

此示例显示 `$WhatIfPreference` 变量设置为默认值 **False** 的影响。 使用 `Get-ChildItem` 验证该文件是否存在。
`Remove-Item` 删除文件。 删除文件后，可以通过验证删除 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

此示例演示在的值为 False 时使用 **WhatIf** 参数的效果 `$WhatIfPreference` 。 

请确保该文件已存在。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

使用 **WhatIf** 参数确定尝试删除文件的结果。

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

验证文件是否未被删除。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

此示例显示 `$WhatIfPreference` 变量设置为值 **True** 后的效果。 使用 `Remove-Item` 删除文件时，会显示文件的路径，但不会删除文件。

尝试删除文件。 将显示一条消息，其中显示在运行时将会发生什么情况 `Remove-Item` ，但不会删除该文件。

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

使用 `Get-ChildItem` 验证文件是否未被删除。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

此示例演示如何在的值为 True 时删除文件 `$WhatIfPreference` 。  它使用值为的 **WhatIf** 参数 `$false` 。 使用 `Get-ChildItem` 验证是否已删除该文件。

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

下面是不 `Get-Process` 支持 **whatif** 并且 `Stop-Process` 支持 **whatif** 的 cmdlet 示例。 `$WhatIfPreference`变量的值为 **True**。

`Get-Process` 不支持 **WhatIf**。 执行命令时，它将显示 **Winword** 进程。

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` 支持 **WhatIf**。 **Winword** 进程未停止。

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

您可以 `Stop-Process` 通过使用值为的 **whatif** 参数来重写 **whatif** 行为 `$false` 。 **Winword** 进程已停止。

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

若要验证 **Winword** 进程是否已停止，请使用 `Get-Process` 。

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)

