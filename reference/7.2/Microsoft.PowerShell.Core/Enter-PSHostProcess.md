---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596638"
---
# Enter-PSHostProcess

## 摘要
连接到并进入与本地进程的交互会话。

## SYNTAX

### ProcessIdParameterSet（默认值）

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### PipeNameParameterSet

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## DESCRIPTION

`Enter-PSHostProcess`Cmdlet 使用本地进程连接到交互式会话并进入交互会话。 从 PowerShell 6.2 开始，非 Windows 平台上支持此 cmdlet。

远程交互式会话在已运行 PowerShell 的现有进程中运行，而不是创建一个新进程来托管 PowerShell 并运行远程会话。 如果要与指定进程上的远程会话交互，可以枚举正在运行的运行空间，然后通过运行或来选择要调试的运行 `Debug-Runspace` 空间 `Enable-RunspaceDebug` 。

要输入的进程必须承载 PowerShell ( # A0) 。
而你必须是发现该进程的计算机上“管理员”组的成员，或必须是运行启动进程的脚本的用户。

选择要调试的运行空间后，无论该运行空间当前是正在运行某个命令还是在调试器中已停止运行，都将为该运行空间打开一个远程调试会话。 你可以在其中按照调试其他远程会话脚本的相同方式调试该运行空间脚本。

运行两次 exit，先后离开调试会话和进程的交互会话，或通过运行现有调试器 Quit 命令停止脚本执行。

如果使用 Name 参数指定进程，并且只找到一个具有指定名称的进程，则进入该进程。 如果找到多个具有指定名称的进程，则 PowerShell 将返回错误，并列出所有使用指定名称找到的进程。

若要支持附加到远程计算机上的进程， `Enter-PSHostProcess` 可以在指定的远程计算机中启用该 cmdlet，以便在远程 PowerShell 会话中附加到本地进程。

## 示例

### 示例1：在 PowerShell ISE 进程内开始调试运行空间

在此示例中， `Enter-PSHostProcess` 从 PowerShell 控制台内运行以进入 POWERSHELL ISE 进程。 在生成的交互式会话中，可以通过运行来查找要调试的运行空间， `Get-Runspace` 然后调试运行空间。

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETERS

### -AppDomainName

如果省略，则指定要连接到的应用程序域名，使用 **DefaultAppDomain**。 用于 `Get-PSHostProcessInfo` 显示应用程序域名。

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

指定可与 PowerShell 连接的 **get-pshostprocessinfo** 对象。 使用 `Get-PSHostProcessInfo` 可获取对象。

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

按进程 ID 指定进程。 若要获取进程 ID，请运行 `Get-Process` cmdlet。

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

按进程名称指定进程。 若要获取进程名称，请运行 `Get-Process` cmdlet。 还可以在“任务管理器”中通过进程的“属性”对话框获取进程名称。

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Process

按进程对象指定进程。 使用此参数的最简单方法是 `Get-Process` ：保存返回要在变量中输入的进程的命令的结果，然后将该变量指定为此参数的值。

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomPipeName

获取或设置要连接到的自定义命名管道名称。 这通常与一起使用 `pwsh -CustomPipeName` 。

此参数是在 PowerShell 6.2 中引入的。

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Diagnostics.Process

## 输出

## 注释

`Enter-PSHostProcess` 无法输入运行命令的 PowerShell 会话的进程。 但是，可以输入另一个 PowerShell 会话的进程，或输入与正在运行的会话同时运行的 PowerShell ISE 会话 `Enter-PSHostProcess` 。

`Enter-PSHostProcess` 只能输入托管 PowerShell 的进程。 也就是说，它们已加载 PowerShell 引擎。

若要从进程内退出进程，请键入 **exit**，然后按 <kbd>enter</kbd>。

在 PowerShell 7.1 之前，通过 SSH 进行远程处理不支持第二个跃点的远程会话。 此功能仅限于使用 WinRM 的会话。 PowerShell 7.1 允许 `Enter-PSSession` 和 `Enter-PSHostProcess` 在任何交互式远程会话中工作。

## 相关链接

[Exit-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)

