---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 3b2c789225a1d76391015c39e3fc919ba65f0a1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595834"
---
# Get-PSReadLineOption

## 摘要
获取可配置的选项的值。

## SYNTAX

```
Get-PSReadLineOption [<CommonParameters>]
```

## DESCRIPTION

`Get-PSReadLineOption`Cmdlet 可返回可使用 cmdlet 配置的设置的当前状态 `Set-PSReadLineOption` 。 您可以使用返回的对象更改 **PSReadLine** 选项。 这为设置多种标记的语法着色选项提供了略微简单的方法。

## 示例

### 示例1：获取选项及其值

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "`e[93m"
CommentColor                           : "`e[32m"
ContinuationPromptColor                : "`e[97m"
DefaultTokenColor                      : "`e[97m"
EmphasisColor                          : "`e[96m"
ErrorColor                             : "`e[91m"
KeywordColor                           : "`e[92m"
MemberColor                            : "`e[97m"
NumberColor                            : "`e[97m"
OperatorColor                          : "`e[90m"
ParameterColor                         : "`e[90m"
SelectionColor                         : "`e[30;107m"
StringColor                            : "`e[36m"
TypeColor                              : "`e[37m"
VariableColor                          : "`e[92m"
```

此命令返回可用 PSReadLine 选项及其当前值的列表。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### PSConsoleReadLineOptions

当前选项的实例。 更改此对象的属性值将直接更新 PSReadLine 中的设置，而无需调用 `Set-PSReadLineOption` 。

## 注释

## 相关链接

[PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Set-PSReadLineOption.md)

[PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
