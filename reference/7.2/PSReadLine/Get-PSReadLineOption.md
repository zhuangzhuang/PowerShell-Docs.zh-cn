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
# <span data-ttu-id="8a07f-102">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="8a07f-102">Get-PSReadLineOption</span></span>

## <span data-ttu-id="8a07f-103">摘要</span><span class="sxs-lookup"><span data-stu-id="8a07f-103">SYNOPSIS</span></span>
<span data-ttu-id="8a07f-104">获取可配置的选项的值。</span><span class="sxs-lookup"><span data-stu-id="8a07f-104">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="8a07f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a07f-105">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="8a07f-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8a07f-106">DESCRIPTION</span></span>

<span data-ttu-id="8a07f-107">`Get-PSReadLineOption`Cmdlet 可返回可使用 cmdlet 配置的设置的当前状态 `Set-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="8a07f-107">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="8a07f-108">您可以使用返回的对象更改 **PSReadLine** 选项。</span><span class="sxs-lookup"><span data-stu-id="8a07f-108">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="8a07f-109">这为设置多种标记的语法着色选项提供了略微简单的方法。</span><span class="sxs-lookup"><span data-stu-id="8a07f-109">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="8a07f-110">示例</span><span class="sxs-lookup"><span data-stu-id="8a07f-110">EXAMPLES</span></span>

### <span data-ttu-id="8a07f-111">示例1：获取选项及其值</span><span class="sxs-lookup"><span data-stu-id="8a07f-111">Example 1: Get options and their values</span></span>

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

<span data-ttu-id="8a07f-112">此命令返回可用 PSReadLine 选项及其当前值的列表。</span><span class="sxs-lookup"><span data-stu-id="8a07f-112">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="8a07f-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a07f-113">PARAMETERS</span></span>

### <span data-ttu-id="8a07f-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a07f-114">CommonParameters</span></span>

<span data-ttu-id="8a07f-115">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8a07f-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a07f-116">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8a07f-116">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a07f-117">输入</span><span class="sxs-lookup"><span data-stu-id="8a07f-117">INPUTS</span></span>

### <span data-ttu-id="8a07f-118">无</span><span class="sxs-lookup"><span data-stu-id="8a07f-118">None</span></span>

<span data-ttu-id="8a07f-119">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a07f-119">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="8a07f-120">输出</span><span class="sxs-lookup"><span data-stu-id="8a07f-120">OUTPUTS</span></span>

### <span data-ttu-id="8a07f-121">PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="8a07f-121">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="8a07f-122">当前选项的实例。</span><span class="sxs-lookup"><span data-stu-id="8a07f-122">An instance of the current options.</span></span> <span data-ttu-id="8a07f-123">更改此对象的属性值将直接更新 PSReadLine 中的设置，而无需调用 `Set-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="8a07f-123">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="8a07f-124">注释</span><span class="sxs-lookup"><span data-stu-id="8a07f-124">NOTES</span></span>

## <span data-ttu-id="8a07f-125">相关链接</span><span class="sxs-lookup"><span data-stu-id="8a07f-125">RELATED LINKS</span></span>

[<span data-ttu-id="8a07f-126">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="8a07f-126">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="8a07f-127">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="8a07f-127">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="8a07f-128">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="8a07f-128">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="8a07f-129">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="8a07f-129">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
