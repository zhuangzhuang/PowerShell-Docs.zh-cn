---
title: 附录 A - 帮助语法
description: 本文介绍如何阅读和理解 Get-Help 提供的 cmdlet 的语法。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99595599"
---
# <a name="appendix-a---help-syntax"></a>附录 A - 帮助语法

下面的示例演示了 `Get-EventLog` cmdlet 帮助的“语法”部分。

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

此示例只显示了帮助的相关部分。

语法主要由多组左方括号和右方括号 (`[]`) 组成。 它们具有两种不同的含义，具体取决于它们的使用方式。 方括号内包含的任何内容都是可选的，除非它们是一组空方括号 `[]`。 空方括号仅出现在 `<string[]>` 等数据类型之后。 这意味着特定参数可以接受多个该类型的值。

`Get-EventLog` 的第一个参数集中的第一个参数是 LogName。 LogName 由方括号括起来，这意味着它是一个位置参数。 换句话说，只要在正确的位置指定参数，就可选择指定该参数本身的名称。 参数名称后面的尖括号 (`<>`) 中的信息指示它需要单个字符串值。 整个参数名称和数据类型没有用方括号括起来的，因此在使用此参数集时需要 LogName 参数。

```powershell
Get-EventLog [-LogName] <String>
```

第二个参数是 InstanceId。 请注意，参数名称和数据类型都使用了方括号完全括起来。 这意味着 InstanceId 参数是可选参数，而不是强制参数。 另请注意，InstanceId 由其自身的方括号括起来。 与 LogName 参数一样，这意味着该参数是位置参数。 数据类型后是最后一组方括号。 这意味着它可以接受多个数组或逗号分隔列表形式的值。

```
[[-InstanceId] <Int64[]>]
```

第二个参数集具有 List 参数。 这是一个开关参数，因为参数名称后面没有数据类型。 如果指定了 List 参数，则值为 True 。 如果未指定，则值为 False。

```
[-List]
```

还可使用 Syntax 参数和 `Get-Command` 检索命令的语法信息。 这是我一直使用的一种便捷的快捷方式。 这可让我快速了解如何使用命令，而无需在多个页面中筛选帮助信息。 如果我最终需要更多信息，那么我将恢复使用实际帮助内容。

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

在 PowerShell 中使用帮助系统的次数越多，就越容易记住所有不同的细微差别。 不知不觉中，使用它会成为第二天性。
