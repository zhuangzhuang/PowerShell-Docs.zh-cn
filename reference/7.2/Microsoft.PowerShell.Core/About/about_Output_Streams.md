---
description: 说明 PowerShell 中输出流的可用性和用途。
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 1dd6424ea14aa241b084a0a2c97a7e9bf6927518
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595842"
---
# <a name="about-output-streams"></a>关于输出流

## <a name="short-description"></a>简短说明
说明 PowerShell 中输出流的可用性和用途。

## <a name="long-description"></a>长说明

PowerShell 提供多个输出流。 流为不同类型的消息提供通道。 你可以使用关联的 cmdlet 或重定向写入这些流。 有关详细信息，请参阅 [about_Redirection](about_Redirection.md)。

PowerShell 支持以下输出流。

| 流# |      说明       | 引入  |    写入 Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **成功** 流     | PowerShell 2.0 | `Write-Output`      |
| 2        | **错误** 流       | PowerShell 2.0 | `Write-Error`       |
| 3        | **警告** 流     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **详细** 流     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **调试** 流       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **信息流** | PowerShell 5.0 | `Write-Information` |
| 不适用      | **进度** 流    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> **进度** 流不支持重定向。

## <a name="success-stream"></a>成功流

**成功** 流是正常、成功结果的默认流。
使用 `Write-Output` cmdlet 将对象显式写入此流。 此流用于通过 PowerShell 管道传递对象。 **成功** 流连接到本机应用程序的 **stdout** 流。

## <a name="error-stream"></a>错误流

**错误** 流是错误结果的默认流。 使用 `Write-Error` cmdlet 显式写入此流。 **错误** 流连接到本机应用程序的 **stderr** 流。 在大多数情况下，这些错误可能会终止执行管道。 写入到此流的错误也会添加到 `$Error` 自动变量。 有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

## <a name="warning-stream"></a>警告流

**警告** 流适用于不符合写入 **错误** 流的错误的错误条件。 正常情况下，这些警告不会终止执行。 警告不会写入 `$Error` 自动变量。 使用 `Write-Warning` cmdlet 显式写入此流。

## <a name="verbose-stream"></a>详细流

**详细** 流用于帮助用户在交互运行或从脚本中运行命令时排除其故障的消息。 使用 `Write-Verbose` cmdlet 将消息显式写入此流。 许多 cmdlet 提供详细的输出，有助于了解 cmdlet 的内部工作原理。 仅当使用 common 参数时，才会输出详细消息 `-Verbose` 。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

## <a name="debug-stream"></a>调试流

**调试** 流用于帮助脚本理解其代码失败的原因的消息。 使用 `Write-Debug` cmdlet 显式写入此流。 仅当使用 common 参数时，才会输出调试消息 `-Debug` 。 有关详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

调试消息适用于比最终用户更多的脚本和 cmdlet 开发人员。 这些调试消息可能包含深层故障排除所需的内部详细信息。

## <a name="information-stream"></a>信息流

**信息流** 旨在提供帮助用户了解脚本正在执行的操作的消息。 开发人员也可以使用它作为通过 PowerShell 传递信息的附加流。 开发人员可以标记流数据，并对该流进行特定的处理。 使用 `Write-Information` cmdlet 显式写入此流。

## <a name="progress-stream"></a>进度流

**进度** 流用于传达更长时间运行命令和脚本的进度的消息。 使用 `Write-Progress` cmdlet 将消息显式写入此流。 **进度** 流不支持重定向。

## <a name="see-also"></a>请参阅

- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
