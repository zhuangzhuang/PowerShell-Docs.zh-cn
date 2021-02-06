---
description: 介绍如何在命令历史记录中获取和运行命令。
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 44e03bd37b0b2c5928fb3aa850f3f5b554ccf123
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597888"
---
# <a name="about-history"></a><span data-ttu-id="915b9-103">关于历史记录</span><span class="sxs-lookup"><span data-stu-id="915b9-103">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="915b9-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="915b9-104">Short Description</span></span>
<span data-ttu-id="915b9-105">介绍如何在命令历史记录中获取和运行命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-105">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="915b9-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="915b9-106">Long Description</span></span>

<span data-ttu-id="915b9-107">当你在命令提示符下输入命令时，PowerShell 会将命令保存在命令历史记录中。</span><span class="sxs-lookup"><span data-stu-id="915b9-107">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="915b9-108">你可以使用历史记录中的命令作为你的工作记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-108">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="915b9-109">而且，您可以从命令历史记录中调用并运行命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-109">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="915b9-110">PowerShell 具有两个不同的历史记录提供程序：内置历史记录和 **PSReadLine** 模块管理的历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-110">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="915b9-111">历史记录是分开管理的，但这两个历史记录均可用于加载 **PSReadLine** 的会话中。</span><span class="sxs-lookup"><span data-stu-id="915b9-111">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="915b9-112">使用 PSReadLine 历史记录</span><span class="sxs-lookup"><span data-stu-id="915b9-112">Using the PSReadLine history</span></span>

<span data-ttu-id="915b9-113">PSReadLine 历史记录跟踪所有 PowerShell 会话中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-113">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="915b9-114">历史记录将写入每个主机的中心文件。</span><span class="sxs-lookup"><span data-stu-id="915b9-114">The history is written to a central file per host.</span></span> <span data-ttu-id="915b9-115">该历史记录文件可供所有会话使用，并包含所有过去的历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-115">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="915b9-116">会话结束时不会删除历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-116">The history is not deleted when the session ends.</span></span> <span data-ttu-id="915b9-117">此外，这些 cmdlet 无法管理该历史记录 `*-History` 。</span><span class="sxs-lookup"><span data-stu-id="915b9-117">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="915b9-118">有关详细信息，请参阅 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="915b9-118">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="915b9-119">使用内置会话历史记录</span><span class="sxs-lookup"><span data-stu-id="915b9-119">Using the built-in session history</span></span>

<span data-ttu-id="915b9-120">内置历史记录只跟踪当前会话中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-120">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="915b9-121">历史记录不能用于其他会话，在会话结束时将被删除。</span><span class="sxs-lookup"><span data-stu-id="915b9-121">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="915b9-122">历史记录 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="915b9-122">History Cmdlets</span></span>

<span data-ttu-id="915b9-123">PowerShell 包含一组用于管理命令历史记录的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="915b9-123">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="915b9-124">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="915b9-124">Cmdlet</span></span>           | <span data-ttu-id="915b9-125">Alias</span><span class="sxs-lookup"><span data-stu-id="915b9-125">Alias</span></span>  | <span data-ttu-id="915b9-126">说明</span><span class="sxs-lookup"><span data-stu-id="915b9-126">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="915b9-127">获取命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-127">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="915b9-128">在命令历史记录中运行命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-128">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="915b9-129">将命令添加到命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-129">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="915b9-130">从命令历史记录中删除命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-130">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="915b9-131">用于管理历史记录的键盘快捷方式</span><span class="sxs-lookup"><span data-stu-id="915b9-131">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="915b9-132">在 PowerShell 控制台中，可以使用以下快捷方式管理命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-132">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="915b9-133"><kbd>向上键</kbd> -显示上一个命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-133"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="915b9-134"><kbd>向下键</kbd> -显示下一个命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-134"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="915b9-135"><kbd>F7</kbd> -显示命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-135"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="915b9-136"><kbd>ESC</kbd> -隐藏历史记录。</span><span class="sxs-lookup"><span data-stu-id="915b9-136"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="915b9-137"><kbd>F8</kbd> -查找命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-137"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="915b9-138">键入一个或多个字符，然后按 <kbd>F8</kbd>。</span><span class="sxs-lookup"><span data-stu-id="915b9-138">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="915b9-139">再次按 <kbd>F8</kbd> 。</span><span class="sxs-lookup"><span data-stu-id="915b9-139">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="915b9-140"><kbd>F9</kbd> -按历史记录 ID 查找命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-140"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="915b9-141">键入历史记录 ID，然后按 <kbd>F9</kbd>。</span><span class="sxs-lookup"><span data-stu-id="915b9-141">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="915b9-142">按 <kbd>F7</kbd> 查找 ID。</span><span class="sxs-lookup"><span data-stu-id="915b9-142">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="915b9-143"><kbd>#</kbd>`<string>`</kbd><kbd>选项卡</kbd> -搜索历史记录 `*<string>*` ，并返回最近的匹配项。</span><span class="sxs-lookup"><span data-stu-id="915b9-143"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="915b9-144">如果重复按 <kbd>tab</kbd> 键，则会循环遍历历史记录中的匹配项。</span><span class="sxs-lookup"><span data-stu-id="915b9-144">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="915b9-145">这些密钥绑定由控制台主机应用程序实现。</span><span class="sxs-lookup"><span data-stu-id="915b9-145">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="915b9-146">其他应用程序（如 Visual Studio Code 或 Windows 终端）可以具有不同的键绑定。</span><span class="sxs-lookup"><span data-stu-id="915b9-146">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="915b9-147">绑定可由 PSReadLine 模块重写。</span><span class="sxs-lookup"><span data-stu-id="915b9-147">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="915b9-148">启动 PowerShell 会话时，PSReadLine 会自动加载。</span><span class="sxs-lookup"><span data-stu-id="915b9-148">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="915b9-149">在加载 PSReadLine 的情况下， <kbd>F7</kbd> 和 <kbd>F9</kbd> 未绑定到任何函数。</span><span class="sxs-lookup"><span data-stu-id="915b9-149">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="915b9-150">PSReadLine 未提供等效功能。</span><span class="sxs-lookup"><span data-stu-id="915b9-150">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="915b9-151">有关详细信息，请参阅 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="915b9-151">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="915b9-152">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="915b9-152">MaximumHistoryCount</span></span>

<span data-ttu-id="915b9-153">`$MaximumHistoryCount`首选项变量确定 PowerShell 在命令历史记录中保存的最大命令数。</span><span class="sxs-lookup"><span data-stu-id="915b9-153">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="915b9-154">默认值为</span><span class="sxs-lookup"><span data-stu-id="915b9-154">The default value is</span></span>
4096.

<span data-ttu-id="915b9-155">例如，以下命令将减少 `$MaximumHistoryCount` 到100命令：</span><span class="sxs-lookup"><span data-stu-id="915b9-155">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="915b9-156">若要应用设置，请重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="915b9-156">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="915b9-157">若要为所有 PowerShell 会话保存新的变量值，请将赋值语句添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="915b9-157">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="915b9-158">有关配置文件的详细信息，请参阅 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="915b9-158">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="915b9-159">有关 `$MaximumHistoryCount` 首选项变量的详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="915b9-159">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="915b9-160">历史记录中的命令顺序</span><span class="sxs-lookup"><span data-stu-id="915b9-160">Order of Commands in the History</span></span>

<span data-ttu-id="915b9-161">命令完成执行时（而不是在输入命令时），会将命令添加到历史记录中。</span><span class="sxs-lookup"><span data-stu-id="915b9-161">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="915b9-162">如果命令需要一些时间才能完成，或命令在嵌套提示符下执行，则这些命令在历史记录中的显示顺序可能会不按顺序显示。</span><span class="sxs-lookup"><span data-stu-id="915b9-162">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="915b9-163">仅当退出提示级别时，才会完成在嵌套提示中执行的命令。</span><span class="sxs-lookup"><span data-stu-id="915b9-163">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="915b9-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="915b9-164">See Also</span></span>

- [<span data-ttu-id="915b9-165">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="915b9-165">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="915b9-166">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="915b9-166">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="915b9-167">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="915b9-167">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="915b9-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="915b9-168">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="915b9-169">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="915b9-169">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

