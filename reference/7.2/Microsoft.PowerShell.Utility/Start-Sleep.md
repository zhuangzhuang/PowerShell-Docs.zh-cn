---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4d06fdd1d5a616c24a4dd7bec10ea4dadea4062
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603804"
---
# <span data-ttu-id="aea42-102">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="aea42-102">Start-Sleep</span></span>

## <span data-ttu-id="aea42-103">摘要</span><span class="sxs-lookup"><span data-stu-id="aea42-103">SYNOPSIS</span></span>
<span data-ttu-id="aea42-104">在指定的时间段内将脚本或会话中的活动挂起。</span><span class="sxs-lookup"><span data-stu-id="aea42-104">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="aea42-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aea42-105">SYNTAX</span></span>

### <span data-ttu-id="aea42-106">Seconds（默认值）</span><span class="sxs-lookup"><span data-stu-id="aea42-106">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="aea42-107">毫秒</span><span class="sxs-lookup"><span data-stu-id="aea42-107">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="aea42-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aea42-108">DESCRIPTION</span></span>

<span data-ttu-id="aea42-109">`Start-Sleep`Cmdlet 将在指定的时间段内将脚本或会话中的活动挂起。</span><span class="sxs-lookup"><span data-stu-id="aea42-109">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="aea42-110">你可以使用它完成许多任务，例如等待操作完成或在重复操作之前暂停。</span><span class="sxs-lookup"><span data-stu-id="aea42-110">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="aea42-111">示例</span><span class="sxs-lookup"><span data-stu-id="aea42-111">EXAMPLES</span></span>

### <span data-ttu-id="aea42-112">示例1：为所有命令休眠15秒</span><span class="sxs-lookup"><span data-stu-id="aea42-112">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="aea42-113">示例2：休眠所有命令1.5 秒</span><span class="sxs-lookup"><span data-stu-id="aea42-113">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="aea42-114">此示例将会话中的所有命令休眠一秒钟，一半半时间。</span><span class="sxs-lookup"><span data-stu-id="aea42-114">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="aea42-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aea42-115">PARAMETERS</span></span>

### <span data-ttu-id="aea42-116">-Milliseconds</span><span class="sxs-lookup"><span data-stu-id="aea42-116">-Milliseconds</span></span>

<span data-ttu-id="aea42-117">指定资源休眠的时间（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="aea42-117">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="aea42-118">该参数可以缩写为 **m**。</span><span class="sxs-lookup"><span data-stu-id="aea42-118">The parameter can be abbreviated as **m**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aea42-119">-Seconds</span><span class="sxs-lookup"><span data-stu-id="aea42-119">-Seconds</span></span>

<span data-ttu-id="aea42-120">指定资源休眠的时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="aea42-120">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="aea42-121">可以省略参数名称，也可以将其 **缩写为。**</span><span class="sxs-lookup"><span data-stu-id="aea42-121">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="aea42-122">从 PowerShell 6.2.0 开始，此参数现在接受小数值。</span><span class="sxs-lookup"><span data-stu-id="aea42-122">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aea42-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aea42-123">CommonParameters</span></span>

<span data-ttu-id="aea42-124">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aea42-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aea42-125">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="aea42-125">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="aea42-126">输入</span><span class="sxs-lookup"><span data-stu-id="aea42-126">INPUTS</span></span>

### <span data-ttu-id="aea42-127">System.Int32</span><span class="sxs-lookup"><span data-stu-id="aea42-127">System.Int32</span></span>

<span data-ttu-id="aea42-128">可以通过管道将秒数传递给 `Start-Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="aea42-128">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="aea42-129">输出</span><span class="sxs-lookup"><span data-stu-id="aea42-129">OUTPUTS</span></span>

### <span data-ttu-id="aea42-130">无</span><span class="sxs-lookup"><span data-stu-id="aea42-130">None</span></span>

<span data-ttu-id="aea42-131">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="aea42-131">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="aea42-132">注释</span><span class="sxs-lookup"><span data-stu-id="aea42-132">NOTES</span></span>

- <span data-ttu-id="aea42-133">还可以 `Start-Sleep` 通过其内置别名来引用 `sleep` 。</span><span class="sxs-lookup"><span data-stu-id="aea42-133">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="aea42-134">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="aea42-134">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="aea42-135">`Ctrl+C` 中断 `Start-Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="aea42-135">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="aea42-136">`Ctrl+C` 不会中断 `[Threading.Thread]::Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="aea42-136">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="aea42-137">有关详细信息，请参阅 [Thread 方法](/dotnet/api/system.threading.thread.sleep)。</span><span class="sxs-lookup"><span data-stu-id="aea42-137">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="aea42-138">相关链接</span><span class="sxs-lookup"><span data-stu-id="aea42-138">RELATED LINKS</span></span>

