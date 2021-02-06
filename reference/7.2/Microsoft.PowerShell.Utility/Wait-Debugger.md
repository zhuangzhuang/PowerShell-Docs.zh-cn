---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: a2ef114a43a63b18f5dc2d28acf7cbc0de8392bd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595622"
---
# <span data-ttu-id="431ec-102">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="431ec-102">Wait-Debugger</span></span>

## <span data-ttu-id="431ec-103">摘要</span><span class="sxs-lookup"><span data-stu-id="431ec-103">SYNOPSIS</span></span>
<span data-ttu-id="431ec-104">在脚本中运行下一个语句之前，停止调试器中的脚本。</span><span class="sxs-lookup"><span data-stu-id="431ec-104">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="431ec-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="431ec-105">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="431ec-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="431ec-106">DESCRIPTION</span></span>

<span data-ttu-id="431ec-107">在 cmdlet 后的点处停止 PowerShell 脚本执行引擎 `Wait-Debugger` ，并等待附加调试器。</span><span class="sxs-lookup"><span data-stu-id="431ec-107">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="431ec-108">这类似于 `Enable-RunspaceDebug -BreakAll` 在 DSC 资源中使用，但会在脚本中的特定点处中断。</span><span class="sxs-lookup"><span data-stu-id="431ec-108">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="431ec-109">完成后，请确保删除 `Wait-Debugger` 行。</span><span class="sxs-lookup"><span data-stu-id="431ec-109">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="431ec-110">当正在运行的脚本在处停止时，该脚本将会挂起 `Wait-Debugger` 。</span><span class="sxs-lookup"><span data-stu-id="431ec-110">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="431ec-111">示例</span><span class="sxs-lookup"><span data-stu-id="431ec-111">EXAMPLES</span></span>

### <span data-ttu-id="431ec-112">示例1：插入断点以进行调试</span><span class="sxs-lookup"><span data-stu-id="431ec-112">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="431ec-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="431ec-113">PARAMETERS</span></span>

### <span data-ttu-id="431ec-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="431ec-114">CommonParameters</span></span>

<span data-ttu-id="431ec-115">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="431ec-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="431ec-116">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="431ec-116">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="431ec-117">输入</span><span class="sxs-lookup"><span data-stu-id="431ec-117">INPUTS</span></span>

### <span data-ttu-id="431ec-118">无</span><span class="sxs-lookup"><span data-stu-id="431ec-118">None</span></span>

## <span data-ttu-id="431ec-119">输出</span><span class="sxs-lookup"><span data-stu-id="431ec-119">OUTPUTS</span></span>

### <span data-ttu-id="431ec-120">无</span><span class="sxs-lookup"><span data-stu-id="431ec-120">None</span></span>

## <span data-ttu-id="431ec-121">注释</span><span class="sxs-lookup"><span data-stu-id="431ec-121">NOTES</span></span>

## <span data-ttu-id="431ec-122">相关链接</span><span class="sxs-lookup"><span data-stu-id="431ec-122">RELATED LINKS</span></span>

[<span data-ttu-id="431ec-123">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="431ec-123">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)

