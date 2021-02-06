---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 177e32106f37c59593bbecac13843f6603327cc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598894"
---
# <span data-ttu-id="5313d-102">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="5313d-102">Write-Verbose</span></span>

## <span data-ttu-id="5313d-103">摘要</span><span class="sxs-lookup"><span data-stu-id="5313d-103">SYNOPSIS</span></span>
<span data-ttu-id="5313d-104">将文本写入详细消息流。</span><span class="sxs-lookup"><span data-stu-id="5313d-104">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="5313d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5313d-105">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="5313d-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5313d-106">DESCRIPTION</span></span>

<span data-ttu-id="5313d-107">`Write-Verbose`Cmdlet 将文本写入 PowerShell 中的详细消息流。</span><span class="sxs-lookup"><span data-stu-id="5313d-107">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="5313d-108">通常，详细消息流用于传递有关命令处理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5313d-108">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="5313d-109">默认情况下，不显示详细消息流，但你可以通过更改变量的值 `$VerbosePreference` 或在任何命令中使用 **verbose** 通用参数来显示它。</span><span class="sxs-lookup"><span data-stu-id="5313d-109">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="5313d-110">示例</span><span class="sxs-lookup"><span data-stu-id="5313d-110">EXAMPLES</span></span>

### <span data-ttu-id="5313d-111">示例1：编写状态消息</span><span class="sxs-lookup"><span data-stu-id="5313d-111">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="5313d-112">这些命令使用 `Write-Verbose` cmdlet 来显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-112">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="5313d-113">默认情况下，不显示此消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-113">By default, the message is not displayed.</span></span>

<span data-ttu-id="5313d-114">第二个命令使用 **verbose** 通用参数，该参数显示任何详细消息，而不考虑变量的值 `$VerbosePreference` 。</span><span class="sxs-lookup"><span data-stu-id="5313d-114">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="5313d-115">示例2：设置 $VerbosePreference 并写入状态消息</span><span class="sxs-lookup"><span data-stu-id="5313d-115">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="5313d-116">这些命令使用 `Write-Verbose` cmdlet 来显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-116">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="5313d-117">默认情况下，不显示此消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-117">By default, the message is not displayed.</span></span>

<span data-ttu-id="5313d-118">第一个命令将 "Continue" 的值分配给 `$VerbosePreference` 首选项变量。</span><span class="sxs-lookup"><span data-stu-id="5313d-118">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="5313d-119">默认值 `SilentlyContinue` 禁止详细消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-119">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="5313d-120">第二个命令写入详细消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-120">The second command writes a verbose message.</span></span>

## <span data-ttu-id="5313d-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5313d-121">PARAMETERS</span></span>

### <span data-ttu-id="5313d-122">-Message</span><span class="sxs-lookup"><span data-stu-id="5313d-122">-Message</span></span>

<span data-ttu-id="5313d-123">指定要显示的消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-123">Specifies the message to display.</span></span> <span data-ttu-id="5313d-124">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="5313d-124">This parameter is required.</span></span> <span data-ttu-id="5313d-125">还可以通过管道将消息字符串传递给 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="5313d-125">You can also pipe a message string to `Write-Verbose`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5313d-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5313d-126">CommonParameters</span></span>

<span data-ttu-id="5313d-127">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5313d-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5313d-128">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5313d-128">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5313d-129">输入</span><span class="sxs-lookup"><span data-stu-id="5313d-129">INPUTS</span></span>

### <span data-ttu-id="5313d-130">System.String</span><span class="sxs-lookup"><span data-stu-id="5313d-130">System.String</span></span>

<span data-ttu-id="5313d-131">可以通过管道将包含消息的字符串传递给 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="5313d-131">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="5313d-132">输出</span><span class="sxs-lookup"><span data-stu-id="5313d-132">OUTPUTS</span></span>

### <span data-ttu-id="5313d-133">无</span><span class="sxs-lookup"><span data-stu-id="5313d-133">None</span></span>

<span data-ttu-id="5313d-134">`Write-Verbose` 仅写入详细消息流。</span><span class="sxs-lookup"><span data-stu-id="5313d-134">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="5313d-135">注释</span><span class="sxs-lookup"><span data-stu-id="5313d-135">NOTES</span></span>

- <span data-ttu-id="5313d-136">仅在该命令使用 **Verbose** 通用参数时才返回详细消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-136">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="5313d-137">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5313d-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="5313d-138">在 Windows PowerShell 后台作业和远程命令中， `$VerbosePreference` 作业会话和远程会话中的变量确定默认情况下是否显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="5313d-138">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="5313d-139">有关变量的详细信息 `$VerbosePreference` ，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5313d-139">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="5313d-140">相关链接</span><span class="sxs-lookup"><span data-stu-id="5313d-140">RELATED LINKS</span></span>

[<span data-ttu-id="5313d-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="5313d-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="5313d-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="5313d-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="5313d-143">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="5313d-143">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="5313d-144">Write-Error</span><span class="sxs-lookup"><span data-stu-id="5313d-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="5313d-145">Write-Host</span><span class="sxs-lookup"><span data-stu-id="5313d-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="5313d-146">Write-Information</span><span class="sxs-lookup"><span data-stu-id="5313d-146">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="5313d-147">Write-Output</span><span class="sxs-lookup"><span data-stu-id="5313d-147">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="5313d-148">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="5313d-148">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="5313d-149">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="5313d-149">Write-Warning</span></span>](Write-Warning.md)
