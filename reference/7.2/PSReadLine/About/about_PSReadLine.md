---
description: PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于 PSReadLine
ms.openlocfilehash: ddc88dda3514e4279b6d91b023e26da88f645af7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685212"
---
# <a name="psreadline"></a><span data-ttu-id="48e6c-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="48e6c-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="48e6c-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="48e6c-105">Short Description</span></span>

<span data-ttu-id="48e6c-106">PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。</span><span class="sxs-lookup"><span data-stu-id="48e6c-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="48e6c-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="48e6c-107">Long Description</span></span>

<span data-ttu-id="48e6c-108">PSReadLine 2.2 为 PowerShell 控制台提供了强大的命令行编辑体验。</span><span class="sxs-lookup"><span data-stu-id="48e6c-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="48e6c-109">提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="48e6c-109">It provides:</span></span>

- <span data-ttu-id="48e6c-110">命令行的语法着色</span><span class="sxs-lookup"><span data-stu-id="48e6c-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="48e6c-111">语法错误的直观指示</span><span class="sxs-lookup"><span data-stu-id="48e6c-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="48e6c-112"> (编辑和历史记录的更好的多行体验) </span><span class="sxs-lookup"><span data-stu-id="48e6c-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="48e6c-113">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="48e6c-113">Customizable key bindings</span></span>
- <span data-ttu-id="48e6c-114">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="48e6c-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="48e6c-115">许多配置选项</span><span class="sxs-lookup"><span data-stu-id="48e6c-115">Many configuration options</span></span>
- <span data-ttu-id="48e6c-116">在 Cmd 模式下，Bash 样式完成 (可选，默认值为 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="48e6c-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="48e6c-117">Emacs yank/kill 循环</span><span class="sxs-lookup"><span data-stu-id="48e6c-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="48e6c-118">基于 PowerShell 令牌的 "word" 移动和终止</span><span class="sxs-lookup"><span data-stu-id="48e6c-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="48e6c-119">预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="48e6c-119">Predictive IntelliSense</span></span>

<span data-ttu-id="48e6c-120">PSReadLine 2.2.0 添加了两种新的预测 IntelliSense 功能：</span><span class="sxs-lookup"><span data-stu-id="48e6c-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="48e6c-121">添加了 **PredictionViewStyle** 参数，以允许选择新的 `ListView` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="48e6c-122">将 PSReadLine 连接到 `CommandPrediction` PS 7.1 中引入的 api 后，用户便可以导入可呈现自定义源的建议的预测器模块。</span><span class="sxs-lookup"><span data-stu-id="48e6c-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="48e6c-123">PSReadLine 需要 PowerShell 3.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="48e6c-124">PSReadLine 使用默认控制台主机、Visual Studio Code 和窗口终端。</span><span class="sxs-lookup"><span data-stu-id="48e6c-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="48e6c-125">它在 PowerShell ISE 中不起作用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="48e6c-126">PSReadLine 2.2.0 随 PowerShell 7.2 一起提供，并在所有支持的 PowerShell 版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="48e6c-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="48e6c-127">它可从 PowerShell 库安装。</span><span class="sxs-lookup"><span data-stu-id="48e6c-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="48e6c-128">若要在支持的 PowerShell 版本中安装 PSReadLine 2.2.0，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="48e6c-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="48e6c-129">从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="48e6c-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="48e6c-130">目前，PSReadLine 不能与屏幕阅读器很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="48e6c-131">Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。</span><span class="sxs-lookup"><span data-stu-id="48e6c-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="48e6c-132">如有必要，可以手动加载模块。</span><span class="sxs-lookup"><span data-stu-id="48e6c-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="48e6c-133">预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="48e6c-133">Predictive IntelliSense</span></span>

<span data-ttu-id="48e6c-134">预测 IntelliSense 是选项卡完成的补充，可帮助用户成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="48e6c-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="48e6c-135">它使用户能够基于用户历史记录和其他域特定插件中的匹配预测来发现、编辑和执行完整命令。</span><span class="sxs-lookup"><span data-stu-id="48e6c-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="48e6c-136">启用预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="48e6c-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="48e6c-137">默认情况下，禁用预测 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="48e6c-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="48e6c-138">若要启用预测，只需运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="48e6c-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="48e6c-139">**PredictionSource** 参数还可以接受插件特定于域和自定义的要求。</span><span class="sxs-lookup"><span data-stu-id="48e6c-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="48e6c-140">若要禁用预测 IntelliSense，只需运行：</span><span class="sxs-lookup"><span data-stu-id="48e6c-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="48e6c-141">类 **[PSConsoleReadLine]** 中提供了以下函数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="48e6c-142">基本编辑函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="48e6c-143">中止</span><span class="sxs-lookup"><span data-stu-id="48e6c-143">Abort</span></span>

<span data-ttu-id="48e6c-144">中止当前操作，例如增量历史记录搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="48e6c-145">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="48e6c-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="48e6c-146">AcceptAndGetNext</span></span>

<span data-ttu-id="48e6c-147">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-147">Attempt to execute the current input.</span></span> <span data-ttu-id="48e6c-148">如果可以 (如 AcceptLine) 执行，则在下一次调用 ReadLine 时，从历史记录中撤回下一项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="48e6c-149">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="48e6c-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-150">AcceptLine</span></span>

<span data-ttu-id="48e6c-151">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-151">Attempt to execute the current input.</span></span> <span data-ttu-id="48e6c-152">如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="48e6c-153">Cmd：`<Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="48e6c-154">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="48e6c-155">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="48e6c-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-156">AddLine</span></span>

<span data-ttu-id="48e6c-157">继续提示显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="48e6c-158">这可用于将多行输入作为单个命令输入，即使单个行自动完成输入也是如此。</span><span class="sxs-lookup"><span data-stu-id="48e6c-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="48e6c-159">Cmd：`<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="48e6c-160">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="48e6c-161">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="48e6c-162">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="48e6c-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-163">BackwardDeleteChar</span></span>

<span data-ttu-id="48e6c-164">删除光标前面的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="48e6c-165">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="48e6c-166">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="48e6c-167">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="48e6c-168">Vi 命令模式： `<X>` ， `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteinput"></a><span data-ttu-id="48e6c-169">BackwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="48e6c-169">BackwardDeleteInput</span></span>

<span data-ttu-id="48e6c-170">Like BackwardKillInput-从点到输入的开头删除文本，但不将已删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-170">Like BackwardKillInput - deletes text from the point to the start of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-171">Cmd：`<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="48e6c-172">Vi 插入模式： `<Ctrl+u>` ， `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="48e6c-173">Vi 命令模式： `<Ctrl+u>` ， `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="48e6c-174">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-174">BackwardDeleteLine</span></span>

<span data-ttu-id="48e6c-175">与 BackwardKillLine 一样，从点到行的开头删除文本，但不会将删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-175">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-176">Vi 命令模式： `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-176">Vi command mode: `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="48e6c-177">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-177">BackwardDeleteWord</span></span>

<span data-ttu-id="48e6c-178">删除上一个词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-178">Deletes the previous word.</span></span>

- <span data-ttu-id="48e6c-179">Vi 命令模式： `<Ctrl+w>` ， `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-179">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillinput"></a><span data-ttu-id="48e6c-180">BackwardKillInput</span><span class="sxs-lookup"><span data-stu-id="48e6c-180">BackwardKillInput</span></span>

<span data-ttu-id="48e6c-181">清除从输入开始到光标的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-181">Clear the text from the start of the input to the cursor.</span></span> <span data-ttu-id="48e6c-182">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-183">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-183">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="48e6c-184">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-184">BackwardKillLine</span></span>

<span data-ttu-id="48e6c-185">清除从当前逻辑行的开头到光标的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-185">Clear the text from the start of the current logical line to the cursor.</span></span> <span data-ttu-id="48e6c-186">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-186">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-187">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-187">Function is unbound.</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="48e6c-188">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-188">BackwardKillWord</span></span>

<span data-ttu-id="48e6c-189">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-189">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="48e6c-190">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-190">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="48e6c-191">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-191">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-192">Cmd： `<Ctrl+Backspace>` ， `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-192">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="48e6c-193">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-193">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="48e6c-194">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-194">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="48e6c-195">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-195">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="48e6c-196">CancelLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-196">CancelLine</span></span>

<span data-ttu-id="48e6c-197">取消当前输入，将输入保留在屏幕上，但返回到主机以便再次计算提示。</span><span class="sxs-lookup"><span data-stu-id="48e6c-197">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="48e6c-198">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-198">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="48e6c-199">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-199">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="48e6c-200">复制</span><span class="sxs-lookup"><span data-stu-id="48e6c-200">Copy</span></span>

<span data-ttu-id="48e6c-201">将所选区域复制到系统剪贴板。</span><span class="sxs-lookup"><span data-stu-id="48e6c-201">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="48e6c-202">如果未选择区域，则复制整行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-202">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="48e6c-203">Cmd：`<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-203">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="48e6c-204">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-204">CopyOrCancelLine</span></span>

<span data-ttu-id="48e6c-205">如果选择了文本，请将其复制到剪贴板，否则取消该行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-205">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="48e6c-206">Cmd：`<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-206">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="48e6c-207">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-207">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="48e6c-208">剪切</span><span class="sxs-lookup"><span data-stu-id="48e6c-208">Cut</span></span>

<span data-ttu-id="48e6c-209">删除所选区域将删除的文本放入系统剪贴板。</span><span class="sxs-lookup"><span data-stu-id="48e6c-209">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="48e6c-210">Cmd：`<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-210">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="48e6c-211">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-211">DeleteChar</span></span>

<span data-ttu-id="48e6c-212">删除光标下的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-212">Delete the character under the cursor.</span></span>

- <span data-ttu-id="48e6c-213">Cmd：`<Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-213">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="48e6c-214">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-214">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="48e6c-215">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-215">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="48e6c-216">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-216">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="48e6c-217">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="48e6c-217">DeleteCharOrExit</span></span>

<span data-ttu-id="48e6c-218">删除光标下的字符; 如果行为空，则退出该过程。</span><span class="sxs-lookup"><span data-stu-id="48e6c-218">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="48e6c-219">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-219">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="48e6c-220">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="48e6c-220">DeleteEndOfBuffer</span></span>

<span data-ttu-id="48e6c-221">删除到多行缓冲区的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-221">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="48e6c-222">Vi 命令模式： `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-222">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="48e6c-223">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-223">DeleteEndOfWord</span></span>

<span data-ttu-id="48e6c-224">删除到单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-224">Delete to the end of the word.</span></span>

- <span data-ttu-id="48e6c-225">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-225">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="48e6c-226">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="48e6c-226">DeleteLine</span></span>

<span data-ttu-id="48e6c-227">删除多行缓冲区的当前逻辑行，启用 "撤消"。</span><span class="sxs-lookup"><span data-stu-id="48e6c-227">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="48e6c-228">Vi 命令模式： `<d,d>` ， `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-228">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="48e6c-229">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="48e6c-229">DeletePreviousLines</span></span>

<span data-ttu-id="48e6c-230">删除多行缓冲区中以前请求的逻辑行和当前逻辑行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-230">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="48e6c-231">Vi 命令模式： `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-231">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="48e6c-232">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="48e6c-232">DeleteRelativeLines</span></span>

<span data-ttu-id="48e6c-233">从缓冲区的开头删除到多行缓冲区中的当前逻辑行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-233">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="48e6c-234">作为最多 Vi 命令，该 `<d,g,g>` 命令可以用一个指定绝对行号的数值参数预置，这一数字参数与当前行号一起构成了要删除的行范围。</span><span class="sxs-lookup"><span data-stu-id="48e6c-234">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="48e6c-235">如果未指定，则数值参数默认为1，这表示多行缓冲区中的第一个逻辑行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-235">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="48e6c-236">要从多行删除的实际行数将计算为当前逻辑行号和指定数值参数之间的差值，这可能是负数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-236">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="48e6c-237">因此，方法名称的 _相关_ 部分。</span><span class="sxs-lookup"><span data-stu-id="48e6c-237">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="48e6c-238">Vi 命令模式： `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-238">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="48e6c-239">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="48e6c-239">DeleteNextLines</span></span>

<span data-ttu-id="48e6c-240">删除多行缓冲区中的当前逻辑行和下一个请求的逻辑行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-240">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="48e6c-241">Vi 命令模式： `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-241">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="48e6c-242">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-242">DeleteLineToFirstChar</span></span>

<span data-ttu-id="48e6c-243">删除多行缓冲区中当前逻辑行的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-243">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="48e6c-244">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-244">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="48e6c-245">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="48e6c-245">DeleteToEnd</span></span>

<span data-ttu-id="48e6c-246">删除到行的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-246">Delete to the end of the line.</span></span>

- <span data-ttu-id="48e6c-247">Vi 命令模式： `<D>` ， `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-247">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="48e6c-248">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-248">DeleteWord</span></span>

<span data-ttu-id="48e6c-249">删除下一个词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-249">Delete the next word.</span></span>

- <span data-ttu-id="48e6c-250">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-250">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteinput"></a><span data-ttu-id="48e6c-251">ForwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="48e6c-251">ForwardDeleteInput</span></span>

<span data-ttu-id="48e6c-252">Like KillLine-从点到输入的末尾删除文本，但不将已删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-252">Like KillLine - deletes text from the point to the end of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-253">Cmd：`<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-253">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="48e6c-254">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-254">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="48e6c-255">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-255">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="48e6c-256">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-256">ForwardDeleteLine</span></span>

<span data-ttu-id="48e6c-257">删除从当前逻辑行的点到末尾的文本，但不将已删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-257">Deletes text from the point to the end of the current logical line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-258">函数未绑定</span><span class="sxs-lookup"><span data-stu-id="48e6c-258">Function is unbound</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="48e6c-259">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="48e6c-259">InsertLineAbove</span></span>

<span data-ttu-id="48e6c-260">在当前行的上方创建新的空行，而不考虑光标在当前行上的位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-260">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="48e6c-261">光标移动到新行的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-261">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="48e6c-262">Cmd：`<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-262">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="48e6c-263">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="48e6c-263">InsertLineBelow</span></span>

<span data-ttu-id="48e6c-264">在当前行下方创建新的空行，而不考虑光标在当前行上的位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-264">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="48e6c-265">光标移动到新行的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-265">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="48e6c-266">Cmd：`<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-266">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="48e6c-267">InvertCase</span><span class="sxs-lookup"><span data-stu-id="48e6c-267">InvertCase</span></span>

<span data-ttu-id="48e6c-268">反转当前字符的大小写，并移到下一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-268">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="48e6c-269">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-269">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="48e6c-270">KillLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-270">KillLine</span></span>

<span data-ttu-id="48e6c-271">清除从光标到输入末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-271">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="48e6c-272">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-272">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-273">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-273">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="48e6c-274">KillRegion</span><span class="sxs-lookup"><span data-stu-id="48e6c-274">KillRegion</span></span>

<span data-ttu-id="48e6c-275">终止光标和标记之间的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-275">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="48e6c-276">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-276">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="48e6c-277">KillWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-277">KillWord</span></span>

<span data-ttu-id="48e6c-278">清除从光标到当前单词末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-278">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="48e6c-279">如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-279">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="48e6c-280">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-280">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-281">Cmd： `<Alt+d>` ， `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-281">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="48e6c-282">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-282">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="48e6c-283">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-283">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="48e6c-284">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-284">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="48e6c-285">粘贴</span><span class="sxs-lookup"><span data-stu-id="48e6c-285">Paste</span></span>

<span data-ttu-id="48e6c-286">粘贴系统剪贴板中的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-286">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="48e6c-287">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-287">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="48e6c-288">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-288">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="48e6c-289">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-289">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48e6c-290">使用 **Paste** 函数时，剪贴板缓冲区的全部内容将粘贴到 PSReadLine 的输入缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-290">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="48e6c-291">然后，将输入缓冲区传递到 PowerShell 分析器。</span><span class="sxs-lookup"><span data-stu-id="48e6c-291">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="48e6c-292">使用控制台应用程序的 **右键单击** 粘贴方法粘贴的输入会一次复制到输入缓冲区中的一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-292">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="48e6c-293">复制换行符时，输入缓冲区会传递到分析器。</span><span class="sxs-lookup"><span data-stu-id="48e6c-293">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="48e6c-294">因此，每次对输入进行一次分析。</span><span class="sxs-lookup"><span data-stu-id="48e6c-294">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="48e6c-295">Paste 方法之间的区别导致了不同的执行行为。</span><span class="sxs-lookup"><span data-stu-id="48e6c-295">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="48e6c-296">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="48e6c-296">PasteAfter</span></span>

<span data-ttu-id="48e6c-297">在光标后面粘贴剪贴板，并将光标移动到粘贴文本的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-297">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="48e6c-298">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-298">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="48e6c-299">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="48e6c-299">PasteBefore</span></span>

<span data-ttu-id="48e6c-300">将剪贴板粘贴到光标之前，并将光标移动到粘贴文本的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-300">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="48e6c-301">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-301">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="48e6c-302">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="48e6c-302">PrependAndAccept</span></span>

<span data-ttu-id="48e6c-303">预置 "#" 并接受该行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-303">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="48e6c-304">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-304">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="48e6c-305">重做</span><span class="sxs-lookup"><span data-stu-id="48e6c-305">Redo</span></span>

<span data-ttu-id="48e6c-306">撤消撤消。</span><span class="sxs-lookup"><span data-stu-id="48e6c-306">Undo an undo.</span></span>

- <span data-ttu-id="48e6c-307">Cmd：`<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-307">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="48e6c-308">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-308">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="48e6c-309">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-309">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="48e6c-310">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="48e6c-310">RepeatLastCommand</span></span>

<span data-ttu-id="48e6c-311">重复最后一次文本修改。</span><span class="sxs-lookup"><span data-stu-id="48e6c-311">Repeat the last text modification.</span></span>

- <span data-ttu-id="48e6c-312">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-312">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="48e6c-313">RevertLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-313">RevertLine</span></span>

<span data-ttu-id="48e6c-314">将所有输入还原为当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-314">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="48e6c-315">Cmd：`<Escape>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-315">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="48e6c-316">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-316">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="48e6c-317">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-317">ShellBackwardKillWord</span></span>

<span data-ttu-id="48e6c-318">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-318">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="48e6c-319">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-319">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="48e6c-320">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-320">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="48e6c-321">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-321">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="48e6c-322">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-322">ShellKillWord</span></span>

<span data-ttu-id="48e6c-323">清除从光标到当前单词末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-323">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="48e6c-324">如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-324">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="48e6c-325">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-325">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="48e6c-326">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-326">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="48e6c-327">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="48e6c-327">SwapCharacters</span></span>

<span data-ttu-id="48e6c-328">交换当前字符和该字符之前的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-328">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="48e6c-329">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-329">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="48e6c-330">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-330">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="48e6c-331">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-331">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="48e6c-332">撤消</span><span class="sxs-lookup"><span data-stu-id="48e6c-332">Undo</span></span>

<span data-ttu-id="48e6c-333">撤消上一个编辑。</span><span class="sxs-lookup"><span data-stu-id="48e6c-333">Undo a previous edit.</span></span>

- <span data-ttu-id="48e6c-334">Cmd：`<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-334">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="48e6c-335">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-335">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="48e6c-336">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-336">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="48e6c-337">Vi 命令模式： `<Ctrl+z>` ， `<u>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-337">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="48e6c-338">UndoAll</span><span class="sxs-lookup"><span data-stu-id="48e6c-338">UndoAll</span></span>

<span data-ttu-id="48e6c-339">撤消对行的所有以前的编辑。</span><span class="sxs-lookup"><span data-stu-id="48e6c-339">Undo all previous edits for line.</span></span>

- <span data-ttu-id="48e6c-340">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-340">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="48e6c-341">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="48e6c-341">UnixWordRubout</span></span>

<span data-ttu-id="48e6c-342">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-342">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="48e6c-343">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-343">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="48e6c-344">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-344">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="48e6c-345">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-345">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="48e6c-346">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-346">ValidateAndAcceptLine</span></span>

<span data-ttu-id="48e6c-347">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-347">Attempt to execute the current input.</span></span> <span data-ttu-id="48e6c-348">如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-348">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="48e6c-349">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-349">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="48e6c-350">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-350">ViAcceptLine</span></span>

<span data-ttu-id="48e6c-351">接受行并切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="48e6c-351">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="48e6c-352">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-352">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="48e6c-353">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="48e6c-353">ViAcceptLineOrExit</span></span>

<span data-ttu-id="48e6c-354">与 Emacs 模式下的 DeleteCharOrExit 类似，但接受行而不是删除字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-354">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="48e6c-355">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-355">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="48e6c-356">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-356">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="48e6c-357">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-357">ViAppendLine</span></span>

<span data-ttu-id="48e6c-358">新行插入到当前行的下方。</span><span class="sxs-lookup"><span data-stu-id="48e6c-358">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="48e6c-359">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-359">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="48e6c-360">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-360">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="48e6c-361">删除上一个词，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-361">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="48e6c-362">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-362">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="48e6c-363">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-363">ViBackwardGlob</span></span>

<span data-ttu-id="48e6c-364">将光标移回上一个词的开头，仅使用空格作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-364">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="48e6c-365">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-365">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="48e6c-366">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="48e6c-366">ViDeleteBrace</span></span>

<span data-ttu-id="48e6c-367">查找匹配的大括号、圆括号或方括号，并删除其中的所有内容，包括大括号。</span><span class="sxs-lookup"><span data-stu-id="48e6c-367">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="48e6c-368">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-368">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="48e6c-369">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-369">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="48e6c-370">删除到单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-370">Delete to the end of the word.</span></span>

- <span data-ttu-id="48e6c-371">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-371">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="48e6c-372">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-372">ViDeleteGlob</span></span>

<span data-ttu-id="48e6c-373">删除下一个 glob (空格分隔的单词) 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-373">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="48e6c-374">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-374">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="48e6c-375">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-375">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="48e6c-376">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-376">Deletes until given character.</span></span>

- <span data-ttu-id="48e6c-377">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-377">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="48e6c-378">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-378">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="48e6c-379">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-379">Deletes until given character.</span></span>

- <span data-ttu-id="48e6c-380">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-380">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="48e6c-381">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-381">ViDeleteToChar</span></span>

<span data-ttu-id="48e6c-382">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-382">Deletes until given character.</span></span>

- <span data-ttu-id="48e6c-383">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-383">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="48e6c-384">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-384">ViDeleteToCharBackward</span></span>

<span data-ttu-id="48e6c-385">向后删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-385">Deletes backwards until given character.</span></span>

- <span data-ttu-id="48e6c-386">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-386">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="48e6c-387">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="48e6c-387">ViInsertAtBegining</span></span>

<span data-ttu-id="48e6c-388">切换到插入模式，并将光标置于行首。</span><span class="sxs-lookup"><span data-stu-id="48e6c-388">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="48e6c-389">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-389">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="48e6c-390">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="48e6c-390">ViInsertAtEnd</span></span>

<span data-ttu-id="48e6c-391">切换到插入模式，并将光标置于行的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-391">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="48e6c-392">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-392">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="48e6c-393">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-393">ViInsertLine</span></span>

<span data-ttu-id="48e6c-394">在当前行的上方插入新行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-394">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="48e6c-395">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-395">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="48e6c-396">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="48e6c-396">ViInsertWithAppend</span></span>

<span data-ttu-id="48e6c-397">从当前行位置追加。</span><span class="sxs-lookup"><span data-stu-id="48e6c-397">Append from the current line position.</span></span>

- <span data-ttu-id="48e6c-398">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-398">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="48e6c-399">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="48e6c-399">ViInsertWithDelete</span></span>

<span data-ttu-id="48e6c-400">删除当前字符并切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="48e6c-400">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="48e6c-401">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-401">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="48e6c-402">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="48e6c-402">ViJoinLines</span></span>

<span data-ttu-id="48e6c-403">联接当前行和下一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-403">Joins the current line and the next line.</span></span>

- <span data-ttu-id="48e6c-404">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-404">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="48e6c-405">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-405">ViReplaceLine</span></span>

<span data-ttu-id="48e6c-406">擦除整个命令行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-406">Erase the entire command line.</span></span>

- <span data-ttu-id="48e6c-407">Vi 命令模式： `<S>` ， `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-407">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="48e6c-408">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-408">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="48e6c-409">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-409">Replaces until given character.</span></span>

- <span data-ttu-id="48e6c-410">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-410">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="48e6c-411">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-411">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="48e6c-412">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-412">Replaces until given character.</span></span>

- <span data-ttu-id="48e6c-413">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-413">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="48e6c-414">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-414">ViReplaceToChar</span></span>

<span data-ttu-id="48e6c-415">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-415">Deletes until given character.</span></span>

- <span data-ttu-id="48e6c-416">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-416">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="48e6c-417">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-417">ViReplaceToCharBackward</span></span>

<span data-ttu-id="48e6c-418">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-418">Replaces until given character.</span></span>

- <span data-ttu-id="48e6c-419">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-419">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="48e6c-420">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-420">ViYankBeginningOfLine</span></span>

<span data-ttu-id="48e6c-421">从缓冲区的开头到游标的 Yank。</span><span class="sxs-lookup"><span data-stu-id="48e6c-421">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="48e6c-422">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-422">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="48e6c-423">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-423">ViYankEndOfGlob</span></span>

<span data-ttu-id="48e6c-424">从光标 Yank 到单词 (s) 的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-424">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="48e6c-425">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-425">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="48e6c-426">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-426">ViYankEndOfWord</span></span>

<span data-ttu-id="48e6c-427">从光标 Yank 到单词 (s) 的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-427">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="48e6c-428">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-428">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="48e6c-429">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="48e6c-429">ViYankLeft</span></span>

<span data-ttu-id="48e6c-430">Yank 字符 (s) 光标左侧。</span><span class="sxs-lookup"><span data-stu-id="48e6c-430">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="48e6c-431">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-431">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="48e6c-432">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-432">ViYankLine</span></span>

<span data-ttu-id="48e6c-433">Yank 整个缓冲区。</span><span class="sxs-lookup"><span data-stu-id="48e6c-433">Yank the entire buffer.</span></span>

- <span data-ttu-id="48e6c-434">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-434">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="48e6c-435">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-435">ViYankNextGlob</span></span>

<span data-ttu-id="48e6c-436">Yank 从 cursor 到下一个单词 () 的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-436">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="48e6c-437">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-437">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="48e6c-438">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-438">ViYankNextWord</span></span>

<span data-ttu-id="48e6c-439">Yank 在游标后) 的单词 (。</span><span class="sxs-lookup"><span data-stu-id="48e6c-439">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="48e6c-440">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-440">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="48e6c-441">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="48e6c-441">ViYankPercent</span></span>

<span data-ttu-id="48e6c-442">Yank 匹配的大括号。</span><span class="sxs-lookup"><span data-stu-id="48e6c-442">Yank to/from matching brace.</span></span>

- <span data-ttu-id="48e6c-443">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-443">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="48e6c-444">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-444">ViYankPreviousGlob</span></span>

<span data-ttu-id="48e6c-445">从单词 (开始，) 到游标。</span><span class="sxs-lookup"><span data-stu-id="48e6c-445">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="48e6c-446">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-446">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="48e6c-447">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-447">ViYankPreviousWord</span></span>

<span data-ttu-id="48e6c-448">Yank 在游标前)  (s。</span><span class="sxs-lookup"><span data-stu-id="48e6c-448">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="48e6c-449">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-449">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="48e6c-450">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="48e6c-450">ViYankRight</span></span>

<span data-ttu-id="48e6c-451">Yank 字符 (s) 光标右侧和右侧。</span><span class="sxs-lookup"><span data-stu-id="48e6c-451">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="48e6c-452">Vi 命令模式： `<y,l>` ， `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-452">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="48e6c-453">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-453">ViYankToEndOfLine</span></span>

<span data-ttu-id="48e6c-454">Yank 从游标到缓冲区的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-454">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="48e6c-455">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-455">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="48e6c-456">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-456">ViYankToFirstChar</span></span>

<span data-ttu-id="48e6c-457">从第一个非空白字符 Yank 到游标。</span><span class="sxs-lookup"><span data-stu-id="48e6c-457">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="48e6c-458">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-458">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="48e6c-459">Yank</span><span class="sxs-lookup"><span data-stu-id="48e6c-459">Yank</span></span>

<span data-ttu-id="48e6c-460">将最近终止的文本添加到输入中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-460">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="48e6c-461">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-461">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="48e6c-462">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="48e6c-462">YankLastArg</span></span>

<span data-ttu-id="48e6c-463">Yank 上一个历史记录行中的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-463">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="48e6c-464">如果使用参数，则第一次调用时，其行为就像 YankNthArg。</span><span class="sxs-lookup"><span data-stu-id="48e6c-464">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="48e6c-465">如果多次调用，则会循环访问历史记录，而 arg 会将方向设置 (负反转方向。 ) </span><span class="sxs-lookup"><span data-stu-id="48e6c-465">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="48e6c-466">Cmd：`<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-466">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="48e6c-467">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-467">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="48e6c-468">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="48e6c-468">YankNthArg</span></span>

<span data-ttu-id="48e6c-469">Yank 从上一历史记录行) 命令后 (第一个参数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-469">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="48e6c-470">对于参数，yank 从 0) 开始 (第 n 个参数，如果参数为负数，则从最后一个参数开始。</span><span class="sxs-lookup"><span data-stu-id="48e6c-470">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="48e6c-471">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-471">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="48e6c-472">YankPop</span><span class="sxs-lookup"><span data-stu-id="48e6c-472">YankPop</span></span>

<span data-ttu-id="48e6c-473">如果上一操作是 Yank 或 YankPop，则将以前的拔掉文本替换为下一个终止的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-473">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="48e6c-474">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-474">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="48e6c-475">游标移动函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-475">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="48e6c-476">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-476">BackwardChar</span></span>

<span data-ttu-id="48e6c-477">将光标向左移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-477">Move the cursor one character to the left.</span></span> <span data-ttu-id="48e6c-478">这可以将光标移到多行输入的上一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-478">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="48e6c-479">Cmd：`<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-479">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-480">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-480">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="48e6c-481">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-481">BackwardWord</span></span>

<span data-ttu-id="48e6c-482">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-482">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="48e6c-483">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-483">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-484">Cmd：`<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-484">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-485">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-485">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="48e6c-486">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-486">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-487">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-487">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="48e6c-488">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-488">BeginningOfLine</span></span>

<span data-ttu-id="48e6c-489">如果输入具有多个行，则移动到当前行的开头，或者，如果已位于行首，则移动到输入的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-489">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="48e6c-490">如果输入具有单行，则移动到输入的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-490">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="48e6c-491">Cmd：`<Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-491">Cmd: `<Home>`</span></span>
- <span data-ttu-id="48e6c-492">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-492">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="48e6c-493">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-493">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="48e6c-494">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-494">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="48e6c-495">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-495">EndOfLine</span></span>

<span data-ttu-id="48e6c-496">如果输入包含多行，则移动到当前行的末尾，或者，如果已位于行尾，则转到输入的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-496">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="48e6c-497">如果输入具有单行，则移动到输入的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-497">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="48e6c-498">Cmd：`<End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-498">Cmd: `<End>`</span></span>
- <span data-ttu-id="48e6c-499">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-499">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="48e6c-500">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-500">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="48e6c-501">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-501">ForwardChar</span></span>

<span data-ttu-id="48e6c-502">将光标向右移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-502">Move the cursor one character to the right.</span></span> <span data-ttu-id="48e6c-503">这可能会将光标移到下一行的多行输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-503">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="48e6c-504">Cmd：`<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-504">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="48e6c-505">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-505">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="48e6c-506">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-506">ForwardWord</span></span>

<span data-ttu-id="48e6c-507">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="48e6c-508">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-509">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-509">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="48e6c-510">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="48e6c-510">GotoBrace</span></span>

<span data-ttu-id="48e6c-511">中转到匹配的大括号、圆括号或方括号。</span><span class="sxs-lookup"><span data-stu-id="48e6c-511">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="48e6c-512">Cmd：`<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-512">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="48e6c-513">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-513">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="48e6c-514">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-514">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="48e6c-515">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="48e6c-515">GotoColumn</span></span>

<span data-ttu-id="48e6c-516">转到 arg 指示的列。</span><span class="sxs-lookup"><span data-stu-id="48e6c-516">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="48e6c-517">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-517">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="48e6c-518">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-518">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="48e6c-519">将光标移动到行中的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-519">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="48e6c-520">Vi 命令模式： `<^>` ， `<_>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-520">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="48e6c-521">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-521">MoveToEndOfLine</span></span>

<span data-ttu-id="48e6c-522">将光标移到输入的末尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-522">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="48e6c-523">Vi 命令模式： `<End>` ， `<$>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-523">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="48e6c-524">NextLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-524">NextLine</span></span>

<span data-ttu-id="48e6c-525">将光标移到下一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-525">Move the cursor to the next line.</span></span>

- <span data-ttu-id="48e6c-526">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-526">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="48e6c-527">NextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-527">NextWord</span></span>

<span data-ttu-id="48e6c-528">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-528">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="48e6c-529">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-529">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-530">Cmd：`<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-530">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="48e6c-531">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-531">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="48e6c-532">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-532">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="48e6c-533">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="48e6c-533">NextWordEnd</span></span>

<span data-ttu-id="48e6c-534">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-534">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="48e6c-535">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-535">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-536">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-536">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="48e6c-537">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-537">PreviousLine</span></span>

<span data-ttu-id="48e6c-538">将光标移到上一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-538">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="48e6c-539">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-539">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="48e6c-540">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-540">ShellBackwardWord</span></span>

<span data-ttu-id="48e6c-541">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-541">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="48e6c-542">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-542">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="48e6c-543">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-543">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="48e6c-544">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-544">ShellForwardWord</span></span>

<span data-ttu-id="48e6c-545">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-545">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="48e6c-546">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-546">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="48e6c-547">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-547">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="48e6c-548">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-548">ShellNextWord</span></span>

<span data-ttu-id="48e6c-549">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="48e6c-549">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="48e6c-550">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-550">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="48e6c-551">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-551">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="48e6c-552">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-552">ViBackwardChar</span></span>

<span data-ttu-id="48e6c-553">在 Vi 编辑模式下将光标左移一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-553">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="48e6c-554">这可以将光标移到多行输入的上一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-554">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="48e6c-555">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-555">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-556">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-556">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="48e6c-557">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-557">ViBackwardWord</span></span>

<span data-ttu-id="48e6c-558">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-558">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="48e6c-559">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-559">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-560">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-560">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="48e6c-561">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-561">ViForwardChar</span></span>

<span data-ttu-id="48e6c-562">在 Vi 编辑模式下将光标向右移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-562">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="48e6c-563">这可能会将光标移到下一行的多行输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-563">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="48e6c-564">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-564">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="48e6c-565">Vi 命令模式： `<RightArrow>` 、 `<Spacebar>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-565">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="48e6c-566">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-566">ViEndOfGlob</span></span>

<span data-ttu-id="48e6c-567">将光标移到单词的末尾，只使用空格作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-567">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="48e6c-568">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-568">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="48e6c-569">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-569">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="48e6c-570">移到上一个词的末尾，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-570">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="48e6c-571">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-571">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="48e6c-572">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="48e6c-572">ViGotoBrace</span></span>

<span data-ttu-id="48e6c-573">类似于 GotoBrace，但基于字符，而不是基于标记。</span><span class="sxs-lookup"><span data-stu-id="48e6c-573">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="48e6c-574">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-574">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="48e6c-575">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="48e6c-575">ViNextGlob</span></span>

<span data-ttu-id="48e6c-576">移到下一个单词，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-576">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="48e6c-577">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-577">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="48e6c-578">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-578">ViNextWord</span></span>

<span data-ttu-id="48e6c-579">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-579">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="48e6c-580">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="48e6c-580">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="48e6c-581">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-581">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="48e6c-582">历史记录函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-582">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="48e6c-583">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-583">BeginningOfHistory</span></span>

<span data-ttu-id="48e6c-584">移到历史记录中的第一项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-584">Move to the first item in the history.</span></span>

- <span data-ttu-id="48e6c-585">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-585">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="48e6c-586">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-586">ClearHistory</span></span>

<span data-ttu-id="48e6c-587">清除 PSReadLine 中的历史记录。</span><span class="sxs-lookup"><span data-stu-id="48e6c-587">Clears history in PSReadLine.</span></span> <span data-ttu-id="48e6c-588">这不会影响 PowerShell 历史记录。</span><span class="sxs-lookup"><span data-stu-id="48e6c-588">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="48e6c-589">Cmd：`<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-589">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="48e6c-590">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-590">EndOfHistory</span></span>

<span data-ttu-id="48e6c-591">移到历史记录中 (当前输入) 的最后一项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-591">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="48e6c-592">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-592">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="48e6c-593">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-593">ForwardSearchHistory</span></span>

<span data-ttu-id="48e6c-594">通过历史记录执行增量向前搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-594">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="48e6c-595">Cmd：`<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-595">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="48e6c-596">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-596">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="48e6c-597">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-597">HistorySearchBackward</span></span>

<span data-ttu-id="48e6c-598">将当前输入替换为 PSReadLine 历史记录中的 "previous" 项，该匹配项与开始与输入和光标之间的字符匹配。</span><span class="sxs-lookup"><span data-stu-id="48e6c-598">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="48e6c-599">Cmd：`<F8>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-599">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="48e6c-600">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="48e6c-600">HistorySearchForward</span></span>

<span data-ttu-id="48e6c-601">将当前输入替换为 PSReadLine 历史记录中与 start 与 input 和 cursor 之间的字符相匹配的 "next" 项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-601">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="48e6c-602">Cmd：`<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-602">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="48e6c-603">NextHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-603">NextHistory</span></span>

<span data-ttu-id="48e6c-604">将当前输入替换为 PSReadLine 历史记录中的 "next" 项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-604">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="48e6c-605">Cmd：`<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-605">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="48e6c-606">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-606">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="48e6c-607">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-607">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="48e6c-608">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-608">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="48e6c-609">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-609">PreviousHistory</span></span>

<span data-ttu-id="48e6c-610">将当前输入替换为 PSReadLine 历史记录中的 "previous" 项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-610">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="48e6c-611">Cmd：`<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-611">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="48e6c-612">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-612">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="48e6c-613">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-613">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="48e6c-614">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="48e6c-614">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="48e6c-615">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="48e6c-615">ReverseSearchHistory</span></span>

<span data-ttu-id="48e6c-616">通过历史记录执行增量向后搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-616">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="48e6c-617">Cmd：`<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-617">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="48e6c-618">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-618">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="48e6c-619">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-619">ViSearchHistoryBackward</span></span>

<span data-ttu-id="48e6c-620">提示输入搜索字符串并在 AcceptLine 上开始搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-620">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="48e6c-621">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-621">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="48e6c-622">Vi 命令模式： `</>` ， `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-622">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="48e6c-623">完成函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-623">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="48e6c-624">完成</span><span class="sxs-lookup"><span data-stu-id="48e6c-624">Complete</span></span>

<span data-ttu-id="48e6c-625">尝试对光标周围的文本执行完成。</span><span class="sxs-lookup"><span data-stu-id="48e6c-625">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="48e6c-626">如果有多个可能的完成，则使用最长的明确前缀完成。</span><span class="sxs-lookup"><span data-stu-id="48e6c-626">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="48e6c-627">如果尝试完成最长的明确完成，则会显示一个可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="48e6c-627">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="48e6c-628">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-628">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="48e6c-629">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="48e6c-629">MenuComplete</span></span>

<span data-ttu-id="48e6c-630">尝试对光标周围的文本执行完成。</span><span class="sxs-lookup"><span data-stu-id="48e6c-630">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="48e6c-631">如果有多个可能的完成，则使用最长的明确前缀完成。</span><span class="sxs-lookup"><span data-stu-id="48e6c-631">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="48e6c-632">如果尝试完成最长的明确完成，则会显示一个可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="48e6c-632">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="48e6c-633">Cmd： `<Ctrl+@>` ， `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-633">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="48e6c-634">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-634">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="48e6c-635">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="48e6c-635">PossibleCompletions</span></span>

<span data-ttu-id="48e6c-636">显示可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="48e6c-636">Display the list of possible completions.</span></span>

- <span data-ttu-id="48e6c-637">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-637">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="48e6c-638">Vi 插入模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-638">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="48e6c-639">Vi 命令模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-639">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="48e6c-640">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="48e6c-640">TabCompleteNext</span></span>

<span data-ttu-id="48e6c-641">尝试使用下一个可用完成来完成光标周围的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-641">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="48e6c-642">Cmd：`<Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-642">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="48e6c-643">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-643">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="48e6c-644">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="48e6c-644">TabCompletePrevious</span></span>

<span data-ttu-id="48e6c-645">尝试使用以前的可用完成功能完成光标周围的文本。</span><span class="sxs-lookup"><span data-stu-id="48e6c-645">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="48e6c-646">Cmd：`<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-646">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="48e6c-647">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-647">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="48e6c-648">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="48e6c-648">ViTabCompleteNext</span></span>

<span data-ttu-id="48e6c-649">结束当前编辑组（如果需要），并调用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="48e6c-649">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="48e6c-650">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-650">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="48e6c-651">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="48e6c-651">ViTabCompletePrevious</span></span>

<span data-ttu-id="48e6c-652">结束当前编辑组（如果需要），并调用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="48e6c-652">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="48e6c-653">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-653">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="48e6c-654">预测函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-654">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="48e6c-655">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-655">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="48e6c-656">使用 `InlineView` 作为预测的视图样式时，请接受 "内联建议" 的下一个单词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-656">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="48e6c-657">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-657">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="48e6c-658">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="48e6c-658">AcceptSuggestion</span></span>

<span data-ttu-id="48e6c-659">使用 `InlineView` 作为预测的视图样式时，请接受当前内联建议。</span><span class="sxs-lookup"><span data-stu-id="48e6c-659">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="48e6c-660">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-660">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="48e6c-661">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="48e6c-661">NextSuggestion</span></span>

<span data-ttu-id="48e6c-662">使用 `ListView` 作为预测的视图样式时，导航到列表中的下一个建议。</span><span class="sxs-lookup"><span data-stu-id="48e6c-662">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="48e6c-663">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-663">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="48e6c-664">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="48e6c-664">PreviousSuggestion</span></span>

<span data-ttu-id="48e6c-665">使用 `ListView` 作为预测的视图样式时，导航到列表中的上一个建议。</span><span class="sxs-lookup"><span data-stu-id="48e6c-665">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="48e6c-666">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-666">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="48e6c-667">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="48e6c-667">SwitchPredictionView</span></span>

<span data-ttu-id="48e6c-668">切换与之间的预测的视图 `InlineView` 样式 `ListView` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-668">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="48e6c-669">Cmd：`<F2>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-669">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="48e6c-670">杂项函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-670">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="48e6c-671">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="48e6c-671">CaptureScreen</span></span>

<span data-ttu-id="48e6c-672">启动交互屏幕捕获-向上/向下箭头选择 "线条"，将选定文本作为文本和 html 复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="48e6c-672">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="48e6c-673">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-673">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="48e6c-674">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="48e6c-674">ClearScreen</span></span>

<span data-ttu-id="48e6c-675">清除屏幕并在屏幕的顶部绘制当前线条。</span><span class="sxs-lookup"><span data-stu-id="48e6c-675">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="48e6c-676">Cmd：`<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-676">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="48e6c-677">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-677">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="48e6c-678">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-678">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="48e6c-679">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-679">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="48e6c-680">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="48e6c-680">DigitArgument</span></span>

<span data-ttu-id="48e6c-681">启动新的数字参数，使其传递到其他函数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-681">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="48e6c-682">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="48e6c-682">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="48e6c-683">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="48e6c-683">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="48e6c-684">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` 、 `<7>` 、 `<8>` 、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-684">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="48e6c-685">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="48e6c-685">InvokePrompt</span></span>

<span data-ttu-id="48e6c-686">清除当前提示符并调用 prompt 函数以重新显示提示符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-686">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="48e6c-687">适用于更改状态的自定义密钥处理程序，例如更改当前目录。</span><span class="sxs-lookup"><span data-stu-id="48e6c-687">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="48e6c-688">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-688">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="48e6c-689">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="48e6c-689">ScrollDisplayDown</span></span>

<span data-ttu-id="48e6c-690">将显示向下滚动一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="48e6c-690">Scroll the display down one screen.</span></span>

- <span data-ttu-id="48e6c-691">Cmd：`<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-691">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="48e6c-692">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-692">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="48e6c-693">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-693">ScrollDisplayDownLine</span></span>

<span data-ttu-id="48e6c-694">将显示向下滚动一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-694">Scroll the display down one line.</span></span>

- <span data-ttu-id="48e6c-695">Cmd：`<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-695">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="48e6c-696">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-696">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="48e6c-697">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="48e6c-697">ScrollDisplayToCursor</span></span>

<span data-ttu-id="48e6c-698">将显示滚动到光标处。</span><span class="sxs-lookup"><span data-stu-id="48e6c-698">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="48e6c-699">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-699">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="48e6c-700">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="48e6c-700">ScrollDisplayTop</span></span>

<span data-ttu-id="48e6c-701">向顶部滚动显示。</span><span class="sxs-lookup"><span data-stu-id="48e6c-701">Scroll the display to the top.</span></span>

- <span data-ttu-id="48e6c-702">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-702">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="48e6c-703">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="48e6c-703">ScrollDisplayUp</span></span>

<span data-ttu-id="48e6c-704">将显示向上滚动一屏。</span><span class="sxs-lookup"><span data-stu-id="48e6c-704">Scroll the display up one screen.</span></span>

- <span data-ttu-id="48e6c-705">Cmd：`<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-705">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="48e6c-706">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-706">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="48e6c-707">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-707">ScrollDisplayUpLine</span></span>

<span data-ttu-id="48e6c-708">将显示向上滚动一行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-708">Scroll the display up one line.</span></span>

- <span data-ttu-id="48e6c-709">Cmd：`<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-709">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="48e6c-710">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-710">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="48e6c-711">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="48e6c-711">SelfInsert</span></span>

<span data-ttu-id="48e6c-712">插入密钥。</span><span class="sxs-lookup"><span data-stu-id="48e6c-712">Insert the key.</span></span>

- <span data-ttu-id="48e6c-713">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-713">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="48e6c-714">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="48e6c-714">ShowCommandHelp</span></span>

<span data-ttu-id="48e6c-715">提供完整的 cmdlet 帮助视图。</span><span class="sxs-lookup"><span data-stu-id="48e6c-715">Provides a view of full cmdlet help.</span></span> <span data-ttu-id="48e6c-716">当光标位于完全展开的参数的末尾时，命中 `<F1>` 该键会将帮助的显示位置显示在该参数的位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-716">When the cursor is at the end of a fully-expanded parameter, hitting the `<F1>` key positions the display of help at the location of that parameter.</span></span>

<span data-ttu-id="48e6c-717">该帮助将使用来自 **Microsoft PowerShell** 的寻呼程序在备用屏幕缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="48e6c-717">The help is displayed on an alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span> <span data-ttu-id="48e6c-718">退出寻呼后，将返回到原始屏幕上的原始光标位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-718">When you exit the pager you are returned to the original cursor position on the original screen.</span></span> <span data-ttu-id="48e6c-719">此寻呼仅适用于新式终端应用程序，如 [Windows 终端](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)。</span><span class="sxs-lookup"><span data-stu-id="48e6c-719">This pager only works in modern terminal applications such as [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span></span>

- <span data-ttu-id="48e6c-720">Cmd：`<F1>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-720">Cmd: `<F1>`</span></span>
- <span data-ttu-id="48e6c-721">Emacs `<F1>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-721">Emacs: `<F1>`</span></span>
- <span data-ttu-id="48e6c-722">Vi 插入模式： `<F1>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-722">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="48e6c-723">Vi 命令模式： `<F1>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-723">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="48e6c-724">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="48e6c-724">ShowKeyBindings</span></span>

<span data-ttu-id="48e6c-725">显示所有绑定键。</span><span class="sxs-lookup"><span data-stu-id="48e6c-725">Show all bound keys.</span></span>

- <span data-ttu-id="48e6c-726">Cmd：`<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-726">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="48e6c-727">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-727">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="48e6c-728">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-728">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="48e6c-729">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="48e6c-729">ShowParameterHelp</span></span>

<span data-ttu-id="48e6c-730">提供参数的动态帮助，方法是将其显示在当前命令行（如）下面 `MenuComplete` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-730">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span> <span data-ttu-id="48e6c-731">当按下键时，光标必须位于完全展开的参数名称的末尾 `<Alt+h>` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-731">The cursor must be at the end of the fully-expanded parameter name when you press the `<Alt+h>` key.</span></span>

- <span data-ttu-id="48e6c-732">Cmd：`<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-732">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="48e6c-733">Emacs `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-733">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="48e6c-734">Vi 插入模式： `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-734">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="48e6c-735">Vi 命令模式： `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-735">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="48e6c-736">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="48e6c-736">ViCommandMode</span></span>

<span data-ttu-id="48e6c-737">将当前运行模式从 Vi-Insert 切换到 Vi-Command。</span><span class="sxs-lookup"><span data-stu-id="48e6c-737">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="48e6c-738">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-738">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="48e6c-739">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="48e6c-739">ViDigitArgumentInChord</span></span>

<span data-ttu-id="48e6c-740">启动新的数字参数，将其传递给其他函数，同时使用 vi 的鼠标左键之一。</span><span class="sxs-lookup"><span data-stu-id="48e6c-740">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="48e6c-741">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-741">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="48e6c-742">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="48e6c-742">ViEditVisually</span></span>

<span data-ttu-id="48e6c-743">在 $env： EDITOR 或 $env：视觉对象指定的文本编辑器中编辑命令行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-743">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="48e6c-744">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-744">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="48e6c-745">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-745">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="48e6c-746">ViExit</span><span class="sxs-lookup"><span data-stu-id="48e6c-746">ViExit</span></span>

<span data-ttu-id="48e6c-747">退出 shell。</span><span class="sxs-lookup"><span data-stu-id="48e6c-747">Exits the shell.</span></span>

- <span data-ttu-id="48e6c-748">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-748">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="48e6c-749">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="48e6c-749">ViInsertMode</span></span>

<span data-ttu-id="48e6c-750">切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="48e6c-750">Switch to Insert mode.</span></span>

- <span data-ttu-id="48e6c-751">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-751">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="48e6c-752">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="48e6c-752">WhatIsKey</span></span>

<span data-ttu-id="48e6c-753">阅读密钥，并告诉我密钥的绑定内容。</span><span class="sxs-lookup"><span data-stu-id="48e6c-753">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="48e6c-754">Cmd：`<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-754">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="48e6c-755">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-755">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="48e6c-756">选择函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-756">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="48e6c-757">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="48e6c-757">ExchangePointAndMark</span></span>

<span data-ttu-id="48e6c-758">将光标置于标记的位置，并将标记移到光标所在的位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-758">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="48e6c-759">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-759">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="48e6c-760">SelectAll</span><span class="sxs-lookup"><span data-stu-id="48e6c-760">SelectAll</span></span>

<span data-ttu-id="48e6c-761">选择整行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-761">Select the entire line.</span></span>

- <span data-ttu-id="48e6c-762">Cmd：`<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-762">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="48e6c-763">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-763">SelectBackwardChar</span></span>

<span data-ttu-id="48e6c-764">调整当前选定内容以包括前一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-764">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="48e6c-765">Cmd：`<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-765">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-766">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-766">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="48e6c-767">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-767">SelectBackwardsLine</span></span>

<span data-ttu-id="48e6c-768">调整当前所选内容，使其包括从光标到行的开头。</span><span class="sxs-lookup"><span data-stu-id="48e6c-768">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="48e6c-769">Cmd：`<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-769">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="48e6c-770">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-770">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="48e6c-771">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-771">SelectBackwardWord</span></span>

<span data-ttu-id="48e6c-772">调整当前所选内容以包含上一个词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-772">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="48e6c-773">Cmd：`<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-773">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="48e6c-774">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-774">Emacs: `<Alt+B>`</span></span>

### <a name="selectcommandargument"></a><span data-ttu-id="48e6c-775">SelectCommandArgument</span><span class="sxs-lookup"><span data-stu-id="48e6c-775">SelectCommandArgument</span></span>

<span data-ttu-id="48e6c-776">对命令自变量进行直观选择。</span><span class="sxs-lookup"><span data-stu-id="48e6c-776">Make visual selection of the command arguments.</span></span> <span data-ttu-id="48e6c-777">自变量的选择范围在脚本块内。</span><span class="sxs-lookup"><span data-stu-id="48e6c-777">Selection of arguments is scoped within a script block.</span></span> <span data-ttu-id="48e6c-778">根据游标位置，它会从最内层的脚本块搜索到最外部投影脚本块，并在脚本块范围中找到任何参数时停止。</span><span class="sxs-lookup"><span data-stu-id="48e6c-778">Based on the cursor position, it searches from the innermost script block to the outmost script block, and stops when it finds any arguments in a script block scope.</span></span>

<span data-ttu-id="48e6c-779">此函数用于 DigitArgument。</span><span class="sxs-lookup"><span data-stu-id="48e6c-779">This function honors DigitArgument.</span></span> <span data-ttu-id="48e6c-780">它将正值或负值参数值视为当前所选参数的正向或后向偏移量，如果未选择任何自变量，则将其视为当前光标位置。</span><span class="sxs-lookup"><span data-stu-id="48e6c-780">It treats the positive or negative argument values as the forward or backward offsets from the currently selected argument, or from the current cursor position when no argument is selected.</span></span>

- <span data-ttu-id="48e6c-781">Cmd：`<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-781">Cmd: `<Alt+a>`</span></span>
- <span data-ttu-id="48e6c-782">Emacs `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-782">Emacs: `<Alt+a>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="48e6c-783">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-783">SelectForwardChar</span></span>

<span data-ttu-id="48e6c-784">调整当前所选内容以包含下一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-784">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="48e6c-785">Cmd：`<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-785">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="48e6c-786">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-786">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="48e6c-787">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-787">SelectForwardWord</span></span>

<span data-ttu-id="48e6c-788">使用 ForwardWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-788">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="48e6c-789">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-789">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="48e6c-790">SelectLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-790">SelectLine</span></span>

<span data-ttu-id="48e6c-791">调整当前所选内容，使其包括从光标到行尾的内容。</span><span class="sxs-lookup"><span data-stu-id="48e6c-791">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="48e6c-792">Cmd：`<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-792">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="48e6c-793">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-793">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="48e6c-794">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-794">SelectNextWord</span></span>

<span data-ttu-id="48e6c-795">调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-795">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="48e6c-796">Cmd：`<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-796">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="48e6c-797">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-797">SelectShellBackwardWord</span></span>

<span data-ttu-id="48e6c-798">使用 ShellBackwardWord 调整当前所选内容，使其包含前一词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-798">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="48e6c-799">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-799">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="48e6c-800">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-800">SelectShellForwardWord</span></span>

<span data-ttu-id="48e6c-801">使用 ShellForwardWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-801">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="48e6c-802">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-802">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="48e6c-803">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="48e6c-803">SelectShellNextWord</span></span>

<span data-ttu-id="48e6c-804">使用 ShellNextWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-804">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="48e6c-805">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-805">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="48e6c-806">SetMark</span><span class="sxs-lookup"><span data-stu-id="48e6c-806">SetMark</span></span>

<span data-ttu-id="48e6c-807">标记光标的当前位置，以供后续编辑命令使用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-807">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="48e6c-808">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-808">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="48e6c-809">预测 IntelliSense 函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-809">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="48e6c-810">需要启用预测 IntelliSense 才能使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="48e6c-810">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="48e6c-811">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="48e6c-811">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="48e6c-812">接受预测 IntelliSense 中的下一个内嵌建议词。</span><span class="sxs-lookup"><span data-stu-id="48e6c-812">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="48e6c-813">此函数可以<kbd></kbd> + 通过运行以下命令与 Ctrl<kbd>F</kbd>绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-813">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="48e6c-814">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="48e6c-814">AcceptSuggestion</span></span>

<span data-ttu-id="48e6c-815">当光标位于当前行的末尾时，通过按 <kbd>右箭头</kbd> ，接受预测 IntelliSense 中的当前内联建议。</span><span class="sxs-lookup"><span data-stu-id="48e6c-815">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="48e6c-816">搜索函数</span><span class="sxs-lookup"><span data-stu-id="48e6c-816">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="48e6c-817">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="48e6c-817">CharacterSearch</span></span>

<span data-ttu-id="48e6c-818">读取字符并向前搜索该字符的下一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-818">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="48e6c-819">如果指定了参数，则向前搜索 (或向后) 对于第 n 个匹配项为负。</span><span class="sxs-lookup"><span data-stu-id="48e6c-819">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="48e6c-820">Cmd：`<F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-820">Cmd: `<F3>`</span></span>
- <span data-ttu-id="48e6c-821">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-821">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="48e6c-822">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-822">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="48e6c-823">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-823">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="48e6c-824">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-824">CharacterSearchBackward</span></span>

<span data-ttu-id="48e6c-825">读取字符并向后搜索该字符的下一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="48e6c-825">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="48e6c-826">如果指定了参数，则在第 n 个匹配项) 反向搜索时 (或转发。</span><span class="sxs-lookup"><span data-stu-id="48e6c-826">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="48e6c-827">Cmd：`<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-827">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="48e6c-828">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-828">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="48e6c-829">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-829">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="48e6c-830">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-830">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="48e6c-831">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="48e6c-831">RepeatLastCharSearch</span></span>

<span data-ttu-id="48e6c-832">重复上次记录的字符搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-832">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="48e6c-833">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-833">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="48e6c-834">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="48e6c-834">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="48e6c-835">重复上次记录的字符搜索，但采用相反方向。</span><span class="sxs-lookup"><span data-stu-id="48e6c-835">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="48e6c-836">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-836">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="48e6c-837">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="48e6c-837">RepeatSearch</span></span>

<span data-ttu-id="48e6c-838">像以前一样，重复最后一个搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-838">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="48e6c-839">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-839">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="48e6c-840">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-840">RepeatSearchBackward</span></span>

<span data-ttu-id="48e6c-841">像以前一样，重复最后一个搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-841">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="48e6c-842">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-842">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="48e6c-843">SearchChar</span><span class="sxs-lookup"><span data-stu-id="48e6c-843">SearchChar</span></span>

<span data-ttu-id="48e6c-844">阅读下一个字符，然后查找、前进，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-844">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="48e6c-845">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="48e6c-845">This is for 't' functionality.</span></span>

- <span data-ttu-id="48e6c-846">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-846">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="48e6c-847">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="48e6c-847">SearchCharBackward</span></span>

<span data-ttu-id="48e6c-848">读取下一个字符，然后查找它，向后移动，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-848">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="48e6c-849">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="48e6c-849">This is for 'T' functionality.</span></span>

- <span data-ttu-id="48e6c-850">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-850">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="48e6c-851">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="48e6c-851">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="48e6c-852">读取下一个字符，然后查找它，向后移动，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-852">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="48e6c-853">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="48e6c-853">This is for 'T' functionality.</span></span>

- <span data-ttu-id="48e6c-854">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-854">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="48e6c-855">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="48e6c-855">SearchCharWithBackoff</span></span>

<span data-ttu-id="48e6c-856">阅读下一个字符，然后查找、前进，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-856">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="48e6c-857">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="48e6c-857">This is for 't' functionality.</span></span>

- <span data-ttu-id="48e6c-858">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-858">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="48e6c-859">SearchForward</span><span class="sxs-lookup"><span data-stu-id="48e6c-859">SearchForward</span></span>

<span data-ttu-id="48e6c-860">提示输入搜索字符串并在 AcceptLine 上开始搜索。</span><span class="sxs-lookup"><span data-stu-id="48e6c-860">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="48e6c-861">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-861">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="48e6c-862">Vi 命令模式： `<?>` ， `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="48e6c-862">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="48e6c-863">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="48e6c-863">Custom Key Bindings</span></span>

<span data-ttu-id="48e6c-864">PSReadLine 支持使用 cmdlet 的自定义键绑定 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-864">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="48e6c-865">大多数自定义键绑定调用上述函数之一，例如</span><span class="sxs-lookup"><span data-stu-id="48e6c-865">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="48e6c-866">可以将 ScriptBlock 绑定到密钥。</span><span class="sxs-lookup"><span data-stu-id="48e6c-866">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="48e6c-867">ScriptBlock 可以执行任何所需的操作。</span><span class="sxs-lookup"><span data-stu-id="48e6c-867">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="48e6c-868">一些有用的示例包括</span><span class="sxs-lookup"><span data-stu-id="48e6c-868">Some useful examples include</span></span>

- <span data-ttu-id="48e6c-869">编辑命令行</span><span class="sxs-lookup"><span data-stu-id="48e6c-869">edit the command line</span></span>
- <span data-ttu-id="48e6c-870">打开新窗口 (例如，帮助) </span><span class="sxs-lookup"><span data-stu-id="48e6c-870">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="48e6c-871">更改目录而不更改命令行</span><span class="sxs-lookup"><span data-stu-id="48e6c-871">change directories without changing the command line</span></span>

<span data-ttu-id="48e6c-872">ScriptBlock 接收两个参数：</span><span class="sxs-lookup"><span data-stu-id="48e6c-872">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="48e6c-873">`$key` -一个作为触发自定义绑定的密钥的 **[ConsoleKeyInfo]** 对象。</span><span class="sxs-lookup"><span data-stu-id="48e6c-873">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="48e6c-874">如果将相同的 ScriptBlock 绑定到多个键，并且需要根据关键字执行不同的操作，则可以选中 $key。</span><span class="sxs-lookup"><span data-stu-id="48e6c-874">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="48e6c-875">许多自定义绑定会忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-875">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="48e6c-876">`$arg` -任意参数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-876">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="48e6c-877">大多数情况下，这将是用户从键绑定 DigitArgument 传递的整数参数。</span><span class="sxs-lookup"><span data-stu-id="48e6c-877">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="48e6c-878">如果绑定不接受参数，则忽略此参数是合理的。</span><span class="sxs-lookup"><span data-stu-id="48e6c-878">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="48e6c-879">我们来看一个示例，该示例将一个命令行添加到历史记录中，而不执行它。</span><span class="sxs-lookup"><span data-stu-id="48e6c-879">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="48e6c-880">如果您认为您忘记了某些事情，但又不想重新输入您已经输入的命令行，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-880">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="48e6c-881">你可以在 PSReadLine 模块文件夹中安装的文件中查看更多示例 `SamplePSReadLineProfile.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-881">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="48e6c-882">大多数键绑定使用一些 helper 函数来编辑命令行。</span><span class="sxs-lookup"><span data-stu-id="48e6c-882">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="48e6c-883">下一节将介绍这些 Api。</span><span class="sxs-lookup"><span data-stu-id="48e6c-883">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="48e6c-884">自定义键绑定支持 Api</span><span class="sxs-lookup"><span data-stu-id="48e6c-884">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="48e6c-885">以下函数是 PSConsoleReadLine 中的公共函数，但不能直接绑定到密钥。</span><span class="sxs-lookup"><span data-stu-id="48e6c-885">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="48e6c-886">大多数在自定义键绑定中很有用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-886">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="48e6c-887">向历史记录中添加一个命令行而不执行它。</span><span class="sxs-lookup"><span data-stu-id="48e6c-887">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="48e6c-888">清除终止环。</span><span class="sxs-lookup"><span data-stu-id="48e6c-888">Clear the kill-ring.</span></span>  <span data-ttu-id="48e6c-889">这主要用于测试。</span><span class="sxs-lookup"><span data-stu-id="48e6c-889">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="48e6c-890">从开始删除长度字符。</span><span class="sxs-lookup"><span data-stu-id="48e6c-890">Delete length characters from start.</span></span>  <span data-ttu-id="48e6c-891">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="48e6c-891">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="48e6c-892">根据用户首选项执行 Ding 操作。</span><span class="sxs-lookup"><span data-stu-id="48e6c-892">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="48e6c-893">这两个函数检索有关输入缓冲区的当前状态的有用信息。</span><span class="sxs-lookup"><span data-stu-id="48e6c-893">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="48e6c-894">第一种方案更常见用于简单情况。</span><span class="sxs-lookup"><span data-stu-id="48e6c-894">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="48e6c-895">如果绑定使用 Ast 执行更高级的操作，则会使用第二个。</span><span class="sxs-lookup"><span data-stu-id="48e6c-895">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="48e6c-896">这两个函数由使用 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-896">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="48e6c-897">第一个用于获取所有键绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-897">The first is used to get all key bindings.</span></span> <span data-ttu-id="48e6c-898">第二个用于获取特定的键绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-898">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="48e6c-899">此函数由 Get-PSReadLineOption 使用，并可能在自定义键绑定中不太有用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-899">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="48e6c-900">如果未在命令行上进行选择，则将在 "开始" 和 "长度" 中返回-1。</span><span class="sxs-lookup"><span data-stu-id="48e6c-900">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="48e6c-901">如果命令行上有选择，则返回选定内容的开始和长度。</span><span class="sxs-lookup"><span data-stu-id="48e6c-901">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="48e6c-902">在光标处插入字符或字符串。</span><span class="sxs-lookup"><span data-stu-id="48e6c-902">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="48e6c-903">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="48e6c-903">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="48e6c-904">这是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="48e6c-904">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="48e6c-905">它不支持递归，因此在自定义键绑定中不起作用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-905">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="48e6c-906">此函数由 Remove-PSReadLineKeyHandler 使用，并可能在自定义键绑定中不太有用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-906">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="48e6c-907">替换部分输入。</span><span class="sxs-lookup"><span data-stu-id="48e6c-907">Replace some of the input.</span></span> <span data-ttu-id="48e6c-908">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="48e6c-908">This operation supports undo/redo.</span></span> <span data-ttu-id="48e6c-909">这优先于删除后再执行 Insert，因为它被视为单个操作来撤消。</span><span class="sxs-lookup"><span data-stu-id="48e6c-909">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="48e6c-910">将光标移动到给定偏移量。</span><span class="sxs-lookup"><span data-stu-id="48e6c-910">Move the cursor to the given offset.</span></span> <span data-ttu-id="48e6c-911">不跟踪游标移动以便撤消。</span><span class="sxs-lookup"><span data-stu-id="48e6c-911">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="48e6c-912">此函数是 cmdlet PSReadLineOption 使用的帮助器方法，但可能对要临时更改设置的自定义密钥绑定很有用。</span><span class="sxs-lookup"><span data-stu-id="48e6c-912">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="48e6c-913">此帮助器方法用于接受 DigitArgument 的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="48e6c-913">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="48e6c-914">典型调用如下所示</span><span class="sxs-lookup"><span data-stu-id="48e6c-914">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="48e6c-915">说明</span><span class="sxs-lookup"><span data-stu-id="48e6c-915">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="48e6c-916">命令历史记录</span><span class="sxs-lookup"><span data-stu-id="48e6c-916">Command History</span></span>

<span data-ttu-id="48e6c-917">PSReadLine 维护一个历史记录文件，其中包含在命令行中输入的所有命令和数据。</span><span class="sxs-lookup"><span data-stu-id="48e6c-917">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="48e6c-918">这可能包含敏感数据（包括密码）。</span><span class="sxs-lookup"><span data-stu-id="48e6c-918">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="48e6c-919">例如，如果使用 cmdlet，则 `ConvertTo-SecureString` 密码将作为纯文本记录到历史记录文件中。</span><span class="sxs-lookup"><span data-stu-id="48e6c-919">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="48e6c-920">历史记录文件是一个名为的文件 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-920">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="48e6c-921">在 Windows 系统上，历史记录文件存储在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-921">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="48e6c-922">在非 Windows 系统上，历史记录文件存储在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或上 `$env:HOME/.local/share/powershell/PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="48e6c-922">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="48e6c-923">参与 PSReadLine 的反馈 &</span><span class="sxs-lookup"><span data-stu-id="48e6c-923">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="48e6c-924">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="48e6c-924">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="48e6c-925">可在 GitHub 页上随意提交拉取请求或提交反馈。</span><span class="sxs-lookup"><span data-stu-id="48e6c-925">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="48e6c-926">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48e6c-926">See Also</span></span>

<span data-ttu-id="48e6c-927">PSReadLine 会受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 库的严重影响。</span><span class="sxs-lookup"><span data-stu-id="48e6c-927">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
