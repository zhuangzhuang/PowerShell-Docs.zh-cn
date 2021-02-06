---
description: 描述可与任何 cmdlet 一起使用的参数。
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 44503e9c251cd3cccf9b879ceb71262c65d8e5e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596829"
---
# <a name="about-commonparameters"></a>关于 CommonParameters

## <a name="short-description"></a>简短说明

描述可与任何 cmdlet 一起使用的参数。

## <a name="long-description"></a>详细说明

常见参数是一组 cmdlet 参数，可用于任何 cmdlet。 它们是由 PowerShell 实现的，而不是由 cmdlet 开发人员实现的，并且可自动用于任何 cmdlet。

可以将通用参数与任何 cmdlet 一起使用，但它们可能对所有 cmdlet 不起作用。 例如，如果某个 cmdlet 没有生成任何详细输出，则使用 **verbose** common 参数不起作用。

通用参数还可用于使用 **CmdletBinding** 特性或 **Parameter** 特性的高级函数。

几个通用参数会替代使用 PowerShell 首选项变量设置的系统默认值或首选项。 与首选项变量不同，common 参数仅影响使用这些参数的命令。

有关详细信息，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。

以下列表显示了通用参数。 它们的别名列在括号中。

- **Debug** (db)
- **ErrorAction** (ea) 
- **ErrorVariable** (ev) 
- **InformationAction** (infa) 
- **InformationVariable** (iv) 
- **OutVariable** (ov-es) 
- **OutBuffer** (ob) 
- **PipelineVariable** (pv) 
- ) **详细** (vb
- **WarningAction** (wa) 
- **WarningVariable** (wv) 

**操作** 参数为 **ActionPreference** 类型值。
**ActionPreference** 是具有以下值的枚举：

| 名称             | 值 |
|------------------|-------|
| 挂起          | 5     |
| 忽略           | 4     |
| 查询          | 3     |
| 继续         | 2     |
| 停止             | 1     |
| SilentlyContinue | 0     |

可以将该名称或值与参数一起使用。

除通用参数外，许多 cmdlet 还提供风险缓解参数。 涉及系统风险或用户数据的 cmdlet 通常提供这些参数。

风险缓解参数包括：

- **WhatIf** (wi) 
- **确认** (cf) 

### <a name="common-parameter-descriptions"></a>常见参数说明

#### <a name="debug"></a>调试

显示有关命令所执行操作的程序员级别的详细信息。 仅当命令生成调试消息时，此参数才有效。 例如，当命令包含 cmdlet 时，此参数有效 `Write-Debug` 。

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

默认情况下，调试消息不会显示，因为变量的值 `$DebugPreference` 为 **SilentlyContinue**。

在交互模式下， **Debug** 参数会重写 `$DebugPreference` 当前命令的变量值，并将的值设置 `$DebugPreference` 为 **Inquire**。

在非交互模式下， **Debug** 参数会重写 `$DebugPreference` 当前命令的变量值，并将的值设置 `$DebugPreference` 为 **Continue**。

`-Debug:$true` 与的效果相同 `-Debug` 。 用于 `-Debug:$false` 禁止在 `$DebugPreference` 不 **SilentlyContinue**（这是默认值）时显示调试消息。

#### <a name="erroraction"></a>ErrorAction

确定 cmdlet 如何响应命令中的非终止错误。
此参数仅在命令生成非终止错误（如 cmdlet 中的错误）时才起作用 `Write-Error` 。

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**ErrorAction** 参数将重写 `$ErrorActionPreference` 当前命令的变量值。 由于变量的默认值 `$ErrorActionPreference` 为 **Continue**，将显示错误消息并继续执行，除非使用 **ErrorAction** 参数。

**ErrorAction** 参数不会影响终止错误 (如缺少数据、无效的参数或权限不足) 阻止命令成功完成。

`-ErrorAction:Continue` 显示错误消息并继续执行命令。 `Continue` 为默认值。

`-ErrorAction:Ignore` 禁止显示错误消息并继续执行命令。 与 **SilentlyContinue** 不同， **Ignore** 不会将错误消息添加到 `$Error` 自动变量。 在 PowerShell 3.0 中引入了 **Ignore** 值。

`-ErrorAction:Inquire` 显示错误消息并提示您进行确认，然后再继续执行。 此值很少使用。

`-ErrorAction:SilentlyContinue` 禁止显示错误消息并继续执行命令。

`-ErrorAction:Stop` 显示错误消息并停止执行命令。

`-ErrorAction:Suspend` 仅适用于 PowerShell 6 和更高版本中不支持的工作流。

> [!NOTE]
> 当在 `$ErrorAction` 命令中使用参数来运行脚本或函数时，ErrorAction 参数将重写，但不会替换首选项变量的值。

#### <a name="errorvariable"></a>ErrorVariable

**ErrorVariable** 在指定变量和自动变量中存储有关命令的错误消息 `$Error` 。 有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

默认情况下，新的错误消息将覆盖变量中已存储的错误消息。 若要将错误消息追加到变量内容，请在变量名之前键入一个加号 (`+`) 。

例如，下面的命令创建 `$a` 变量，然后在其中存储任何错误：

```powershell
Get-Process -Id 6 -ErrorVariable a
```

下面的命令将所有错误消息添加到 `$a` 变量：

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

以下命令显示的内容 `$a` ：

```powershell
$a
```

可以使用此参数来创建一个变量，该变量只包含来自特定命令的错误消息，不会影响 `$Error` 自动变量的行为。 `$Error`自动变量包含会话中所有命令的错误消息。 您可以使用数组表示法（如 `$a[0]` 或） `$error[1,2]` 来引用变量中存储的特定错误。

> [!NOTE]
> 自定义错误变量包含命令生成的所有错误，包括调用嵌套函数或脚本的错误。

#### <a name="informationaction"></a>InformationAction

在 PowerShell 5.0 中引入。 在使用该参数的命令或脚本内， **InformationAction** common 参数将覆盖 `$InformationPreference` 首选项变量的值，默认情况下，该参数设置为 **SilentlyContinue**。 `Write-Information`在带有 **InformationAction** 的脚本中使用时， `Write-Information` 会根据 **InformationAction** 参数的值来显示值。 有关的详细信息 `$InformationPreference` ，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` 在命令出现时停止命令或脚本 `Write-Information` 。

`-InformationAction:Ignore` 禁止显示信息性消息，并继续运行命令。 与 **SilentlyContinue** 不同， **忽略** 完全忘记密码的信息性消息;它不会将信息性消息添加到信息流。

`-InformationAction:Inquire` 显示你在命令中指定的信息性消息 `Write-Information` ，然后询问你是否要继续。

`-InformationAction:Continue` 显示信息性消息，并继续运行。

`-InformationAction:Suspend` 在 PowerShell Core 中不受支持，因为它仅适用于工作流。

`-InformationAction:SilentlyContinue` 不会影响信息性消息 (默认) 显示，脚本会继续而不会中断。

> [!NOTE]
> 当在 `$InformationAction` 命令中使用参数来运行脚本或函数时，InformationAction 参数将重写，但不会替换首选项变量的值。

#### <a name="informationvariable"></a>InformationVariable

在 PowerShell 5.0 中引入。 在使用它的命令或脚本中， **InformationVariable** 通用参数将通过添加命令指定的字符串存储在变量中 `Write-Information` 。 `Write-Information` 根据 **InformationAction** 通用参数的值显示值;如果未添加 **InformationAction** 通用参数，将根据 `Write-Information` 首选项变量的值来显示字符串 `$InformationPreference` 。 有关的详细信息 `$InformationPreference` ，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。

> [!NOTE]
> 信息变量包含命令生成的所有信息消息，包括调用嵌套函数或脚本的信息消息。

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

确定在通过管道发送任何对象之前要在缓冲区中累积的对象数。 如果省略此参数，则会在生成对象时将其发送。

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

此资源管理参数专用于高级用户。 当你使用此参数时，PowerShell 将数据批量发送到下一个 cmdlet `OutBuffer + 1` 。

下面的示例将在 `ForEach-Object` 使用 cmdlet 的进程块之间显示替换 `Write-Host` 。 显示以2个或的批次备用 `OutBuffer + 1` 。

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

除了通过管道发送输出之外，还将命令中的输出对象存储在指定的变量中。

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

若要将输出添加到变量，而不是替换可能已存储在该处的任何输出，请在变量名之前键入一个加号 (`+`) 。

例如，下面的命令创建 `$out` 变量，并在其中存储进程对象：

```powershell
Get-Process PowerShell -OutVariable out
```

以下命令将进程对象添加到 `$out` 变量：

```powershell
Get-Process iexplore -OutVariable +out
```

以下命令显示变量的内容 `$out` ：

```powershell
$out
```

> [!NOTE]
> **OutVariable** 参数创建的变量是 `[System.Collections.ArrayList]` 。

#### <a name="pipelinevariable"></a>PipelineVariable

当任何命名命令流过管道时， **PipelineVariable** 将当前管道元素的值存储为变量。

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

有效值为字符串，与任何变量名相同。

下面是 **PipelineVariable** 工作原理的示例。 在此示例中，将 **PipelineVariable** 参数添加到 `Foreach-Object` 命令中，以将命令的结果存储在变量中。 从1到10的数字范围进入第一个 `Foreach-Object` 命令，其结果存储在名为 **Left** 的变量中。

第一个命令的结果 `Foreach-Object` 将通过管道传递到第二个 `Foreach-Object` 命令中，该命令将筛选第一个命令返回的对象 `Foreach-Object` 。 第二个命令的结果存储在一个名为 **Right** 的变量中。

在第三 `Foreach-Object` 个命令中，通过 `Foreach-Object` 使用乘法运算符来处理前两个管道命令的结果（由 **左侧** 和 **右侧** 的变量表示）。 命令指示存储在 **左** 变量和 **右** 变量中的对象相乘，并指定结果应显示为 "左范围成员 * 右侧范围成员 = product"。

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>详细

显示有关命令所执行操作的详细信息。 此信息类似于跟踪或事务日志中的信息。 仅当命令生成详细消息时，此参数才有效。 例如，当命令包含 cmdlet 时，此参数有效 `Write-Verbose` 。

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**Verbose** 参数重写 `$VerbosePreference` 当前命令的变量值。 由于变量的默认值 `$VerbosePreference` 为 **SilentlyContinue**，因此默认情况下不显示详细消息。

`-Verbose:$true` 具有与相同的效果 `-Verbose`

`-Verbose:$false` 禁止显示详细消息。 如果的值 `$VerbosePreference` 不是 **SilentlyContinue** (默认) ，请使用此参数。

#### <a name="warningaction"></a>WarningAction

确定 cmdlet 如何响应命令中的警告。 **Continue** 为默认值。 仅当命令生成警告消息时，此参数才有效。 例如，当命令包含 cmdlet 时，此参数有效 `Write-Warning` 。

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**WarningAction** 参数将重写 `$WarningPreference` 当前命令的变量值。 由于变量的默认值 `$WarningPreference` 为 **Continue**，将显示警告，并且执行将继续，除非使用 **WarningAction** 参数。

`-WarningAction:Continue` 显示警告消息并继续执行命令。 `Continue` 为默认值。

`-WarningAction:Inquire` 显示警告消息并提示您进行确认，然后再继续执行。 此值很少使用。

`-WarningAction:SilentlyContinue` 禁止显示警告消息并继续执行命令。

`-WarningAction:Stop` 显示警告消息，并停止执行命令。

> [!NOTE]
> 当在 `$WarningAction` 命令中使用参数来运行脚本或函数时，WarningAction 参数将重写，但不会替换首选项变量的值。

#### <a name="warningvariable"></a>WarningVariable

存储有关指定变量中的命令的警告。

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

即使未向用户显示警告，所有生成的警告也将保存在变量中。

若要将警告追加到变量内容，而不是替换可能已存储在该处的任何警告，请在变量名之前键入一个加号 (`+`) 。

例如，下面的命令创建 `$a` 变量，然后在其中存储任何警告：

```powershell
Get-Process -Id 6 -WarningVariable a
```

以下命令将任何警告添加到 `$a` 变量：

```powershell
Get-Process -Id 2 -WarningVariable +a
```

以下命令显示的内容 `$a` ：

```powershell
$a
```

你可以使用此参数来创建一个仅包含特定命令中的警告的变量。 可以使用数组表示法（如 `$a[0]` 或） `$warning[1,2]` 来引用变量中存储的特定警告。

> [!NOTE]
> 警告变量包含命令生成的所有警告，包括调用嵌套函数或脚本的警告。

### <a name="risk-management-parameter-descriptions"></a>风险管理参数说明

#### <a name="whatif"></a>WhatIf

显示一条消息，该消息描述命令的效果，而不是执行命令。

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**WhatIf** 参数会重写 `$WhatIfPreference` 当前命令的变量值。 由于变量的默认值 `$WhatIfPreference` 为 0 (禁用了) ，因此在没有 **whatif** 参数的情况下，无法完成 **whatif** 行为。 有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)

`-WhatIf:$true` 与的效果相同 `-WhatIf` 。

`-WhatIf:$false` 取消当变量的值为1时产生的自动 WhatIf 行为 `$WhatIfPreference` 。

例如，以下命令使用 `-WhatIf` 命令中的参数 `Remove-Item` ：

```powershell
Remove-Item Date.csv -WhatIf
```

PowerShell 不会删除项目，而是列出要执行的操作和受影响的项目。 该命令生成以下输出：

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>确认

在执行命令前提示您进行确认。

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**Confirm** 参数重写 `$ConfirmPreference` 当前命令的变量值。 默认值为 true。 有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)

`-Confirm:$true` 与的效果相同 `-Confirm` 。

`-Confirm:$false` 取消自动确认，当的值 `$ConfirmPreference` 小于或等于该 cmdlet 的估计风险时，就会发生这种情况。

例如，以下命令将 **Confirm** 参数用于 `Remove-Item` 命令。 在删除项之前，PowerShell 会列出它将执行的操作和受影响的项，并请求批准。

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

确认响应选项如下所示：

|响应       |结果                                                     |
|---------------|-----------------------------------------------------------|
|是 (Y)         |执行操作。                                        |
|全部 (都是)  |执行所有操作并取消后续确认查询|
|               |此命令。                                          |
|不 (N) ：        |不要执行该操作。                                 |
|所有 (L) ： |不要执行任何操作并取消后续确认 |
|               |此命令的查询。                                  |
|挂起)  (：   |暂停命令并创建临时会话。          |
|帮助 (？ )        |显示这些选项的帮助。                            |

" **挂起** " 选项将命令置于保持状态，并创建一个临时嵌套会话，在该会话中，您可以选择 " **确认** " 选项。 嵌套会话的命令提示符包含两个额外的插入符号 ( # A2) ，以指示它是原始父命令的子操作。 可以在嵌套会话中运行命令和脚本。 若要结束嵌套会话并返回到原始命令的确认选项，请键入 "exit"。

在下面的示例中， **暂停** 选项 (S) 用于在用户检查命令参数帮助时暂时停止命令。 获取所需的信息后，用户键入 "exit" 结束嵌套提示，然后选择 "是" (y) 响应确认查询。

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>字

about_Common_Parameters

## <a name="see-also"></a>另请参阅

[about_Preference_Variables](about_Preference_Variables.md)

[Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)

[Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)

[Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

