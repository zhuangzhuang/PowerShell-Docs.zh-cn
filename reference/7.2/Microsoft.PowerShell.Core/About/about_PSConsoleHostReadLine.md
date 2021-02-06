---
description: 说明如何创建自定义 PowerShell 在控制台提示符下读取输入的方式。
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 2f69cd4c0c8f65f4a963eae561647d6de30a067e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596033"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="a813c-103">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="a813c-103">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="a813c-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="a813c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a813c-105">说明如何创建自定义 PowerShell 在控制台提示符下读取输入的方式。</span><span class="sxs-lookup"><span data-stu-id="a813c-105">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="a813c-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="a813c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a813c-107">从 Windows PowerShell 3.0 开始，你可以编写一个名为 PSConsoleHostReadLine 的函数，用于重写处理控制台输入的默认方式。</span><span class="sxs-lookup"><span data-stu-id="a813c-107">Starting in Windows PowerShell 3.0, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="a813c-108">示例</span><span class="sxs-lookup"><span data-stu-id="a813c-108">EXAMPLES</span></span>

<span data-ttu-id="a813c-109">下面的示例启动记事本并从用户创建的文本文件获取输入：</span><span class="sxs-lookup"><span data-stu-id="a813c-109">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a><span data-ttu-id="a813c-110">REMARKS</span><span class="sxs-lookup"><span data-stu-id="a813c-110">REMARKS</span></span>

<span data-ttu-id="a813c-111">默认情况下，PowerShell 在所谓的 "加工模式" 下从控制台读取输入，在这种模式下，Windows 控制台子系统处理所有 keypresses、F7 菜单和其他输入。</span><span class="sxs-lookup"><span data-stu-id="a813c-111">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="a813c-112">按 Enter 或 Tab 键时，PowerShell 将获取已键入到该点的文本。</span><span class="sxs-lookup"><span data-stu-id="a813c-112">When you press Enter or Tab, PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="a813c-113">在按 Enter 或 Tab 之前，无法知道您按下了 Ctrl + R、Ctrl + A、Ctrl + E 或其他任何键。在 Windows PowerShell 3.0 中，PSConsoleHostReadLine 函数解决了此问题。</span><span class="sxs-lookup"><span data-stu-id="a813c-113">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell 3.0, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="a813c-114">在 PowerShell 控制台主机中定义名为 PSConsoleHostReadline 的函数时，PowerShell 将调用而不是 "加工模式" 输入机制。</span><span class="sxs-lookup"><span data-stu-id="a813c-114">When you define a function named PSConsoleHostReadline in the PowerShell console host, PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="a813c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a813c-115">SEE ALSO</span></span>

[<span data-ttu-id="a813c-116">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="a813c-116">about_Prompts</span></span>](about_Prompts.md)

