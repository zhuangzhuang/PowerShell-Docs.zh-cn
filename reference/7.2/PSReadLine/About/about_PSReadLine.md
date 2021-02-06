---
description: PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于 PSReadLine
ms.openlocfilehash: 4836abfec465ba7cdfb6800c1e60104fba19ce08
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "99595607"
---
# <a name="psreadline"></a><span data-ttu-id="50ed9-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="50ed9-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="50ed9-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="50ed9-105">Short Description</span></span>

<span data-ttu-id="50ed9-106">PSReadLine 在 PowerShell 控制台中提供改进的命令行编辑体验。</span><span class="sxs-lookup"><span data-stu-id="50ed9-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="50ed9-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="50ed9-107">Long Description</span></span>

<span data-ttu-id="50ed9-108">PSReadLine 2.2 为 PowerShell 控制台提供了强大的命令行编辑体验。</span><span class="sxs-lookup"><span data-stu-id="50ed9-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="50ed9-109">提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="50ed9-109">It provides:</span></span>

- <span data-ttu-id="50ed9-110">命令行的语法着色</span><span class="sxs-lookup"><span data-stu-id="50ed9-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="50ed9-111">语法错误的直观指示</span><span class="sxs-lookup"><span data-stu-id="50ed9-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="50ed9-112"> (编辑和历史记录的更好的多行体验) </span><span class="sxs-lookup"><span data-stu-id="50ed9-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="50ed9-113">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="50ed9-113">Customizable key bindings</span></span>
- <span data-ttu-id="50ed9-114">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="50ed9-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="50ed9-115">许多配置选项</span><span class="sxs-lookup"><span data-stu-id="50ed9-115">Many configuration options</span></span>
- <span data-ttu-id="50ed9-116">在 Cmd 模式下，Bash 样式完成 (可选，默认值为 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="50ed9-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="50ed9-117">Emacs yank/kill 循环</span><span class="sxs-lookup"><span data-stu-id="50ed9-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="50ed9-118">基于 PowerShell 令牌的 "word" 移动和终止</span><span class="sxs-lookup"><span data-stu-id="50ed9-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="50ed9-119">预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="50ed9-119">Predictive IntelliSense</span></span>

<span data-ttu-id="50ed9-120">PSReadLine 2.2.0 添加了两种新的预测 IntelliSense 功能：</span><span class="sxs-lookup"><span data-stu-id="50ed9-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="50ed9-121">添加了 **PredictionViewStyle** 参数，以允许选择新的 `ListView` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="50ed9-122">将 PSReadLine 连接到 `CommandPrediction` PS 7.1 中引入的 api 后，用户便可以导入可呈现自定义源的建议的预测器模块。</span><span class="sxs-lookup"><span data-stu-id="50ed9-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="50ed9-123">PSReadLine 需要 PowerShell 3.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="50ed9-124">PSReadLine 使用默认控制台主机、Visual Studio Code 和窗口终端。</span><span class="sxs-lookup"><span data-stu-id="50ed9-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="50ed9-125">它在 PowerShell ISE 中不起作用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="50ed9-126">PSReadLine 2.2.0 随 PowerShell 7.2 一起提供，并在所有支持的 PowerShell 版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="50ed9-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="50ed9-127">它可从 PowerShell 库安装。</span><span class="sxs-lookup"><span data-stu-id="50ed9-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="50ed9-128">若要在支持的 PowerShell 版本中安装 PSReadLine 2.2.0，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="50ed9-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="50ed9-129">从 PowerShell 7.0 开始，如果检测到屏幕阅读器程序，PowerShell 会跳过在 Windows 上自动加载 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="50ed9-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="50ed9-130">目前，PSReadLine 不能与屏幕阅读器很好地配合使用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="50ed9-131">Windows 上 PowerShell 7.0 的默认呈现和格式设置正常。</span><span class="sxs-lookup"><span data-stu-id="50ed9-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="50ed9-132">如有必要，可以手动加载模块。</span><span class="sxs-lookup"><span data-stu-id="50ed9-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="50ed9-133">预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="50ed9-133">Predictive IntelliSense</span></span>

<span data-ttu-id="50ed9-134">预测 IntelliSense 是选项卡完成的补充，可帮助用户成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="50ed9-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="50ed9-135">它使用户能够基于用户历史记录和其他域特定插件中的匹配预测来发现、编辑和执行完整命令。</span><span class="sxs-lookup"><span data-stu-id="50ed9-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="50ed9-136">启用预测 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="50ed9-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="50ed9-137">默认情况下，禁用预测 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="50ed9-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="50ed9-138">若要启用预测，只需运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="50ed9-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="50ed9-139">**PredictionSource** 参数还可以接受插件特定于域和自定义的要求。</span><span class="sxs-lookup"><span data-stu-id="50ed9-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="50ed9-140">若要禁用预测 IntelliSense，只需运行：</span><span class="sxs-lookup"><span data-stu-id="50ed9-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="50ed9-141">类 **[PSConsoleReadLine]** 中提供了以下函数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="50ed9-142">基本编辑函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="50ed9-143">中止</span><span class="sxs-lookup"><span data-stu-id="50ed9-143">Abort</span></span>

<span data-ttu-id="50ed9-144">中止当前操作，例如增量历史记录搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="50ed9-145">Emacs `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="50ed9-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="50ed9-146">AcceptAndGetNext</span></span>

<span data-ttu-id="50ed9-147">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-147">Attempt to execute the current input.</span></span> <span data-ttu-id="50ed9-148">如果可以 (如 AcceptLine) 执行，则在下一次调用 ReadLine 时，从历史记录中撤回下一项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="50ed9-149">Emacs `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="50ed9-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-150">AcceptLine</span></span>

<span data-ttu-id="50ed9-151">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-151">Attempt to execute the current input.</span></span> <span data-ttu-id="50ed9-152">如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="50ed9-153">Cmd：`<Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="50ed9-154">Emacs `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="50ed9-155">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="50ed9-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-156">AddLine</span></span>

<span data-ttu-id="50ed9-157">继续提示显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="50ed9-158">这可用于将多行输入作为单个命令输入，即使单个行自动完成输入也是如此。</span><span class="sxs-lookup"><span data-stu-id="50ed9-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="50ed9-159">Cmd：`<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="50ed9-160">Emacs `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="50ed9-161">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="50ed9-162">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="50ed9-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-163">BackwardDeleteChar</span></span>

<span data-ttu-id="50ed9-164">删除光标前面的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="50ed9-165">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="50ed9-166">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="50ed9-167">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="50ed9-168">Vi 命令模式： `<X>` ， `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="50ed9-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-169">BackwardDeleteLine</span></span>

<span data-ttu-id="50ed9-170">与 BackwardKillLine 一样，从点到行的开头删除文本，但不会将删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-171">Cmd：`<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="50ed9-172">Vi 插入模式： `<Ctrl+u>` ， `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="50ed9-173">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="50ed9-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-174">BackwardDeleteWord</span></span>

<span data-ttu-id="50ed9-175">删除上一个词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-175">Deletes the previous word.</span></span>

- <span data-ttu-id="50ed9-176">Vi 命令模式： `<Ctrl+w>` ， `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="50ed9-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-177">BackwardKillLine</span></span>

<span data-ttu-id="50ed9-178">清除输入从输入开始到光标。</span><span class="sxs-lookup"><span data-stu-id="50ed9-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="50ed9-179">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-180">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="50ed9-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-181">BackwardKillWord</span></span>

<span data-ttu-id="50ed9-182">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="50ed9-183">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="50ed9-184">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-185">Cmd： `<Ctrl+Backspace>` ， `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="50ed9-186">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="50ed9-187">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="50ed9-188">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="50ed9-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-189">CancelLine</span></span>

<span data-ttu-id="50ed9-190">取消当前输入，将输入保留在屏幕上，但返回到主机以便再次计算提示。</span><span class="sxs-lookup"><span data-stu-id="50ed9-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="50ed9-191">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="50ed9-192">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="50ed9-193">复制</span><span class="sxs-lookup"><span data-stu-id="50ed9-193">Copy</span></span>

<span data-ttu-id="50ed9-194">将所选区域复制到系统剪贴板。</span><span class="sxs-lookup"><span data-stu-id="50ed9-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="50ed9-195">如果未选择区域，则复制整行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="50ed9-196">Cmd：`<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="50ed9-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-197">CopyOrCancelLine</span></span>

<span data-ttu-id="50ed9-198">如果选择了文本，请将其复制到剪贴板，否则取消该行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="50ed9-199">Cmd：`<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="50ed9-200">Emacs `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="50ed9-201">剪切</span><span class="sxs-lookup"><span data-stu-id="50ed9-201">Cut</span></span>

<span data-ttu-id="50ed9-202">删除所选区域将删除的文本放入系统剪贴板。</span><span class="sxs-lookup"><span data-stu-id="50ed9-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="50ed9-203">Cmd：`<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="50ed9-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-204">DeleteChar</span></span>

<span data-ttu-id="50ed9-205">删除光标下的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="50ed9-206">Cmd：`<Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="50ed9-207">Emacs `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="50ed9-208">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="50ed9-209">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="50ed9-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="50ed9-210">DeleteCharOrExit</span></span>

<span data-ttu-id="50ed9-211">删除光标下的字符; 如果行为空，则退出该过程。</span><span class="sxs-lookup"><span data-stu-id="50ed9-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="50ed9-212">Emacs `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="50ed9-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="50ed9-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="50ed9-214">删除到多行缓冲区的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="50ed9-215">Vi 命令模式： `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="50ed9-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-216">DeleteEndOfWord</span></span>

<span data-ttu-id="50ed9-217">删除到单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="50ed9-218">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="50ed9-219">Deleteline.invoke</span><span class="sxs-lookup"><span data-stu-id="50ed9-219">DeleteLine</span></span>

<span data-ttu-id="50ed9-220">删除多行缓冲区的当前逻辑行，启用 "撤消"。</span><span class="sxs-lookup"><span data-stu-id="50ed9-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="50ed9-221">Vi 命令模式： `<d,d>` ， `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="50ed9-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="50ed9-222">DeletePreviousLines</span></span>

<span data-ttu-id="50ed9-223">删除多行缓冲区中以前请求的逻辑行和当前逻辑行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="50ed9-224">Vi 命令模式： `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="50ed9-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="50ed9-225">DeleteRelativeLines</span></span>

<span data-ttu-id="50ed9-226">从缓冲区的开头删除到多行缓冲区中的当前逻辑行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="50ed9-227">作为最多 Vi 命令，该 `<d,g,g>` 命令可以用一个指定绝对行号的数值参数预置，这一数字参数与当前行号一起构成了要删除的行范围。</span><span class="sxs-lookup"><span data-stu-id="50ed9-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="50ed9-228">如果未指定，则数值参数默认为1，这表示多行缓冲区中的第一个逻辑行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="50ed9-229">要从多行删除的实际行数将计算为当前逻辑行号和指定数值参数之间的差值，这可能是负数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="50ed9-230">因此，方法名称的 _相关_ 部分。</span><span class="sxs-lookup"><span data-stu-id="50ed9-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="50ed9-231">Vi 命令模式： `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="50ed9-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="50ed9-232">DeleteNextLines</span></span>

<span data-ttu-id="50ed9-233">删除多行缓冲区中的当前逻辑行和下一个请求的逻辑行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="50ed9-234">Vi 命令模式： `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="50ed9-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="50ed9-236">删除多行缓冲区中当前逻辑行的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="50ed9-237">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="50ed9-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="50ed9-238">DeleteToEnd</span></span>

<span data-ttu-id="50ed9-239">删除到行的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="50ed9-240">Vi 命令模式： `<D>` ， `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="50ed9-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-241">DeleteWord</span></span>

<span data-ttu-id="50ed9-242">删除下一个词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-242">Delete the next word.</span></span>

- <span data-ttu-id="50ed9-243">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="50ed9-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-244">ForwardDeleteLine</span></span>

<span data-ttu-id="50ed9-245">与 ForwardKillLine 一样，从点到行尾删除文本，但不会将删除的文本放入 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-246">Cmd：`<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="50ed9-247">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="50ed9-248">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="50ed9-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="50ed9-249">InsertLineAbove</span></span>

<span data-ttu-id="50ed9-250">在当前行的上方创建新的空行，而不考虑光标在当前行上的位置。</span><span class="sxs-lookup"><span data-stu-id="50ed9-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="50ed9-251">光标移动到新行的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="50ed9-252">Cmd：`<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="50ed9-253">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="50ed9-253">InsertLineBelow</span></span>

<span data-ttu-id="50ed9-254">在当前行下方创建新的空行，而不考虑光标在当前行上的位置。</span><span class="sxs-lookup"><span data-stu-id="50ed9-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="50ed9-255">光标移动到新行的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="50ed9-256">Cmd：`<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="50ed9-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="50ed9-257">InvertCase</span></span>

<span data-ttu-id="50ed9-258">反转当前字符的大小写，并移到下一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="50ed9-259">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="50ed9-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-260">KillLine</span></span>

<span data-ttu-id="50ed9-261">清除从光标到输入末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="50ed9-262">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-263">Emacs `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="50ed9-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="50ed9-264">KillRegion</span></span>

<span data-ttu-id="50ed9-265">终止光标和标记之间的文本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="50ed9-266">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="50ed9-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-267">KillWord</span></span>

<span data-ttu-id="50ed9-268">清除从光标到当前单词末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="50ed9-269">如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="50ed9-270">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-271">Cmd： `<Alt+d>` ， `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="50ed9-272">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="50ed9-273">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="50ed9-274">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="50ed9-275">粘贴</span><span class="sxs-lookup"><span data-stu-id="50ed9-275">Paste</span></span>

<span data-ttu-id="50ed9-276">粘贴系统剪贴板中的文本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="50ed9-277">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="50ed9-278">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="50ed9-279">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50ed9-280">使用 **Paste** 函数时，剪贴板缓冲区的全部内容将粘贴到 PSReadLine 的输入缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="50ed9-281">然后，将输入缓冲区传递到 PowerShell 分析器。</span><span class="sxs-lookup"><span data-stu-id="50ed9-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="50ed9-282">使用控制台应用程序的 **右键单击** 粘贴方法粘贴的输入会一次复制到输入缓冲区中的一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="50ed9-283">复制换行符时，输入缓冲区会传递到分析器。</span><span class="sxs-lookup"><span data-stu-id="50ed9-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="50ed9-284">因此，每次对输入进行一次分析。</span><span class="sxs-lookup"><span data-stu-id="50ed9-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="50ed9-285">Paste 方法之间的区别导致了不同的执行行为。</span><span class="sxs-lookup"><span data-stu-id="50ed9-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="50ed9-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="50ed9-286">PasteAfter</span></span>

<span data-ttu-id="50ed9-287">在光标后面粘贴剪贴板，并将光标移动到粘贴文本的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="50ed9-288">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="50ed9-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="50ed9-289">PasteBefore</span></span>

<span data-ttu-id="50ed9-290">将剪贴板粘贴到光标之前，并将光标移动到粘贴文本的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="50ed9-291">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="50ed9-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="50ed9-292">PrependAndAccept</span></span>

<span data-ttu-id="50ed9-293">预置 "#" 并接受该行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="50ed9-294">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="50ed9-295">重做</span><span class="sxs-lookup"><span data-stu-id="50ed9-295">Redo</span></span>

<span data-ttu-id="50ed9-296">撤消撤消。</span><span class="sxs-lookup"><span data-stu-id="50ed9-296">Undo an undo.</span></span>

- <span data-ttu-id="50ed9-297">Cmd：`<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="50ed9-298">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="50ed9-299">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="50ed9-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="50ed9-300">RepeatLastCommand</span></span>

<span data-ttu-id="50ed9-301">重复最后一次文本修改。</span><span class="sxs-lookup"><span data-stu-id="50ed9-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="50ed9-302">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="50ed9-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-303">RevertLine</span></span>

<span data-ttu-id="50ed9-304">将所有输入还原为当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="50ed9-305">Cmd：`<Escape>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="50ed9-306">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="50ed9-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="50ed9-308">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="50ed9-309">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="50ed9-310">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="50ed9-311">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="50ed9-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-312">ShellKillWord</span></span>

<span data-ttu-id="50ed9-313">清除从光标到当前单词末尾的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="50ed9-314">如果光标位于单词之间，则会将输入从光标处清除到下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="50ed9-315">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="50ed9-316">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="50ed9-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="50ed9-317">SwapCharacters</span></span>

<span data-ttu-id="50ed9-318">交换当前字符和该字符之前的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="50ed9-319">Emacs `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="50ed9-320">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="50ed9-321">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="50ed9-322">撤消</span><span class="sxs-lookup"><span data-stu-id="50ed9-322">Undo</span></span>

<span data-ttu-id="50ed9-323">撤消上一个编辑。</span><span class="sxs-lookup"><span data-stu-id="50ed9-323">Undo a previous edit.</span></span>

- <span data-ttu-id="50ed9-324">Cmd：`<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="50ed9-325">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="50ed9-326">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="50ed9-327">Vi 命令模式： `<Ctrl+z>` ， `<u>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="50ed9-328">UndoAll</span><span class="sxs-lookup"><span data-stu-id="50ed9-328">UndoAll</span></span>

<span data-ttu-id="50ed9-329">撤消对行的所有以前的编辑。</span><span class="sxs-lookup"><span data-stu-id="50ed9-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="50ed9-330">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="50ed9-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="50ed9-331">UnixWordRubout</span></span>

<span data-ttu-id="50ed9-332">清除从当前单词开头到光标的输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="50ed9-333">如果光标位于单词之间，则会从上一个字的开头到光标清除输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="50ed9-334">清除的文本会置于 kill 循环中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="50ed9-335">Emacs `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="50ed9-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="50ed9-337">尝试执行当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-337">Attempt to execute the current input.</span></span> <span data-ttu-id="50ed9-338">如果当前输入不完整 (例如，缺少右括号、方括号或引号，则继续提示符将显示在下一行，PSReadLine 将等待键编辑当前输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="50ed9-339">Emacs `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="50ed9-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-340">ViAcceptLine</span></span>

<span data-ttu-id="50ed9-341">接受行并切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="50ed9-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="50ed9-342">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="50ed9-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="50ed9-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="50ed9-344">与 Emacs 模式下的 DeleteCharOrExit 类似，但接受行而不是删除字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="50ed9-345">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="50ed9-346">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="50ed9-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-347">ViAppendLine</span></span>

<span data-ttu-id="50ed9-348">新行插入到当前行的下方。</span><span class="sxs-lookup"><span data-stu-id="50ed9-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="50ed9-349">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="50ed9-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="50ed9-351">删除上一个词，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="50ed9-352">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="50ed9-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-353">ViBackwardGlob</span></span>

<span data-ttu-id="50ed9-354">将光标移回上一个词的开头，仅使用空格作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="50ed9-355">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="50ed9-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="50ed9-356">ViDeleteBrace</span></span>

<span data-ttu-id="50ed9-357">查找匹配的大括号、圆括号或方括号，并删除其中的所有内容，包括大括号。</span><span class="sxs-lookup"><span data-stu-id="50ed9-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="50ed9-358">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="50ed9-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="50ed9-360">删除到单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="50ed9-361">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="50ed9-362">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-362">ViDeleteGlob</span></span>

<span data-ttu-id="50ed9-363">删除下一个 glob (空格分隔的单词) 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="50ed9-364">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="50ed9-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="50ed9-366">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-366">Deletes until given character.</span></span>

- <span data-ttu-id="50ed9-367">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="50ed9-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="50ed9-369">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-369">Deletes until given character.</span></span>

- <span data-ttu-id="50ed9-370">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="50ed9-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-371">ViDeleteToChar</span></span>

<span data-ttu-id="50ed9-372">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-372">Deletes until given character.</span></span>

- <span data-ttu-id="50ed9-373">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="50ed9-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="50ed9-375">向后删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="50ed9-376">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="50ed9-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="50ed9-377">ViInsertAtBegining</span></span>

<span data-ttu-id="50ed9-378">切换到插入模式，并将光标置于行首。</span><span class="sxs-lookup"><span data-stu-id="50ed9-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="50ed9-379">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="50ed9-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="50ed9-380">ViInsertAtEnd</span></span>

<span data-ttu-id="50ed9-381">切换到插入模式，并将光标置于行的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="50ed9-382">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="50ed9-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-383">ViInsertLine</span></span>

<span data-ttu-id="50ed9-384">在当前行的上方插入新行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="50ed9-385">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="50ed9-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="50ed9-386">ViInsertWithAppend</span></span>

<span data-ttu-id="50ed9-387">从当前行位置追加。</span><span class="sxs-lookup"><span data-stu-id="50ed9-387">Append from the current line position.</span></span>

- <span data-ttu-id="50ed9-388">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="50ed9-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="50ed9-389">ViInsertWithDelete</span></span>

<span data-ttu-id="50ed9-390">删除当前字符并切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="50ed9-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="50ed9-391">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="50ed9-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="50ed9-392">ViJoinLines</span></span>

<span data-ttu-id="50ed9-393">联接当前行和下一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="50ed9-394">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="50ed9-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-395">ViReplaceLine</span></span>

<span data-ttu-id="50ed9-396">擦除整个命令行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-396">Erase the entire command line.</span></span>

- <span data-ttu-id="50ed9-397">Vi 命令模式： `<S>` ， `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="50ed9-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="50ed9-399">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-399">Replaces until given character.</span></span>

- <span data-ttu-id="50ed9-400">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="50ed9-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="50ed9-402">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-402">Replaces until given character.</span></span>

- <span data-ttu-id="50ed9-403">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="50ed9-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-404">ViReplaceToChar</span></span>

<span data-ttu-id="50ed9-405">删除到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-405">Deletes until given character.</span></span>

- <span data-ttu-id="50ed9-406">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="50ed9-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="50ed9-408">替换到给定的字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-408">Replaces until given character.</span></span>

- <span data-ttu-id="50ed9-409">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="50ed9-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="50ed9-411">从缓冲区的开头到游标的 Yank。</span><span class="sxs-lookup"><span data-stu-id="50ed9-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="50ed9-412">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="50ed9-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="50ed9-414">从光标 Yank 到单词 (s) 的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="50ed9-415">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="50ed9-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-416">ViYankEndOfWord</span></span>

<span data-ttu-id="50ed9-417">从光标 Yank 到单词 (s) 的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="50ed9-418">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="50ed9-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="50ed9-419">ViYankLeft</span></span>

<span data-ttu-id="50ed9-420">Yank 字符 (s) 光标左侧。</span><span class="sxs-lookup"><span data-stu-id="50ed9-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="50ed9-421">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="50ed9-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-422">ViYankLine</span></span>

<span data-ttu-id="50ed9-423">Yank 整个缓冲区。</span><span class="sxs-lookup"><span data-stu-id="50ed9-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="50ed9-424">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="50ed9-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-425">ViYankNextGlob</span></span>

<span data-ttu-id="50ed9-426">Yank 从 cursor 到下一个单词 () 的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="50ed9-427">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="50ed9-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-428">ViYankNextWord</span></span>

<span data-ttu-id="50ed9-429">Yank 在游标后) 的单词 (。</span><span class="sxs-lookup"><span data-stu-id="50ed9-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="50ed9-430">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="50ed9-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="50ed9-431">ViYankPercent</span></span>

<span data-ttu-id="50ed9-432">Yank 匹配的大括号。</span><span class="sxs-lookup"><span data-stu-id="50ed9-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="50ed9-433">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="50ed9-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="50ed9-435">从单词 (开始，) 到游标。</span><span class="sxs-lookup"><span data-stu-id="50ed9-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="50ed9-436">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="50ed9-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-437">ViYankPreviousWord</span></span>

<span data-ttu-id="50ed9-438">Yank 在游标前)  (s。</span><span class="sxs-lookup"><span data-stu-id="50ed9-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="50ed9-439">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="50ed9-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="50ed9-440">ViYankRight</span></span>

<span data-ttu-id="50ed9-441">Yank 字符 (s) 光标右侧和右侧。</span><span class="sxs-lookup"><span data-stu-id="50ed9-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="50ed9-442">Vi 命令模式： `<y,l>` ， `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="50ed9-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="50ed9-444">Yank 从游标到缓冲区的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="50ed9-445">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="50ed9-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-446">ViYankToFirstChar</span></span>

<span data-ttu-id="50ed9-447">从第一个非空白字符 Yank 到游标。</span><span class="sxs-lookup"><span data-stu-id="50ed9-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="50ed9-448">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="50ed9-449">Yank</span><span class="sxs-lookup"><span data-stu-id="50ed9-449">Yank</span></span>

<span data-ttu-id="50ed9-450">将最近终止的文本添加到输入中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="50ed9-451">Emacs `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="50ed9-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="50ed9-452">YankLastArg</span></span>

<span data-ttu-id="50ed9-453">Yank 上一个历史记录行中的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="50ed9-454">如果使用参数，则第一次调用时，其行为就像 YankNthArg。</span><span class="sxs-lookup"><span data-stu-id="50ed9-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="50ed9-455">如果多次调用，则会循环访问历史记录，而 arg 会将方向设置 (负反转方向。 ) </span><span class="sxs-lookup"><span data-stu-id="50ed9-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="50ed9-456">Cmd：`<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="50ed9-457">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="50ed9-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="50ed9-458">YankNthArg</span></span>

<span data-ttu-id="50ed9-459">Yank 从上一历史记录行) 命令后 (第一个参数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="50ed9-460">对于参数，yank 从 0) 开始 (第 n 个参数，如果参数为负数，则从最后一个参数开始。</span><span class="sxs-lookup"><span data-stu-id="50ed9-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="50ed9-461">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="50ed9-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="50ed9-462">YankPop</span></span>

<span data-ttu-id="50ed9-463">如果上一操作是 Yank 或 YankPop，则将以前的拔掉文本替换为下一个终止的文本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="50ed9-464">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="50ed9-465">游标移动函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="50ed9-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-466">BackwardChar</span></span>

<span data-ttu-id="50ed9-467">将光标向左移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="50ed9-468">这可以将光标移到多行输入的上一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="50ed9-469">Cmd：`<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-470">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="50ed9-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-471">BackwardWord</span></span>

<span data-ttu-id="50ed9-472">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="50ed9-473">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-474">Cmd：`<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-475">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="50ed9-476">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-477">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="50ed9-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-478">BeginningOfLine</span></span>

<span data-ttu-id="50ed9-479">如果输入具有多个行，则移动到当前行的开头，或者，如果已位于行首，则移动到输入的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="50ed9-480">如果输入具有单行，则移动到输入的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="50ed9-481">Cmd：`<Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="50ed9-482">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="50ed9-483">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="50ed9-484">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="50ed9-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-485">EndOfLine</span></span>

<span data-ttu-id="50ed9-486">如果输入包含多行，则移动到当前行的末尾，或者，如果已位于行尾，则转到输入的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="50ed9-487">如果输入具有单行，则移动到输入的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="50ed9-488">Cmd：`<End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="50ed9-489">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="50ed9-490">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="50ed9-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-491">ForwardChar</span></span>

<span data-ttu-id="50ed9-492">将光标向右移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="50ed9-493">这可能会将光标移到下一行的多行输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="50ed9-494">Cmd：`<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="50ed9-495">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="50ed9-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-496">ForwardWord</span></span>

<span data-ttu-id="50ed9-497">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="50ed9-498">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-499">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="50ed9-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="50ed9-500">GotoBrace</span></span>

<span data-ttu-id="50ed9-501">中转到匹配的大括号、圆括号或方括号。</span><span class="sxs-lookup"><span data-stu-id="50ed9-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="50ed9-502">Cmd：`<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="50ed9-503">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="50ed9-504">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="50ed9-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="50ed9-505">GotoColumn</span></span>

<span data-ttu-id="50ed9-506">转到 arg 指示的列。</span><span class="sxs-lookup"><span data-stu-id="50ed9-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="50ed9-507">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="50ed9-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="50ed9-509">将光标移动到行中的第一个非空白字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="50ed9-510">Vi 命令模式： `<^>` ， `<_>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="50ed9-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-511">MoveToEndOfLine</span></span>

<span data-ttu-id="50ed9-512">将光标移到输入的末尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="50ed9-513">Vi 命令模式： `<End>` ， `<$>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="50ed9-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-514">NextLine</span></span>

<span data-ttu-id="50ed9-515">将光标移到下一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="50ed9-516">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="50ed9-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-517">NextWord</span></span>

<span data-ttu-id="50ed9-518">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="50ed9-519">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-520">Cmd：`<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="50ed9-521">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="50ed9-522">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="50ed9-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="50ed9-523">NextWordEnd</span></span>

<span data-ttu-id="50ed9-524">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="50ed9-525">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-526">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="50ed9-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-527">PreviousLine</span></span>

<span data-ttu-id="50ed9-528">将光标移到上一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="50ed9-529">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="50ed9-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-530">ShellBackwardWord</span></span>

<span data-ttu-id="50ed9-531">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="50ed9-532">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="50ed9-533">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="50ed9-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-534">ShellForwardWord</span></span>

<span data-ttu-id="50ed9-535">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="50ed9-536">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="50ed9-537">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="50ed9-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-538">ShellNextWord</span></span>

<span data-ttu-id="50ed9-539">将光标向前移动到当前单词的末尾，或者在单词之间向前移动，直到成为下一个单词的结尾。</span><span class="sxs-lookup"><span data-stu-id="50ed9-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="50ed9-540">Word 边界由 PowerShell 令牌定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="50ed9-541">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="50ed9-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-542">ViBackwardChar</span></span>

<span data-ttu-id="50ed9-543">在 Vi 编辑模式下将光标左移一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="50ed9-544">这可以将光标移到多行输入的上一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="50ed9-545">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-546">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="50ed9-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-547">ViBackwardWord</span></span>

<span data-ttu-id="50ed9-548">将光标移回到当前单词的开头，或者在单词之间移动，如果为，则将光标移到上一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="50ed9-549">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-550">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="50ed9-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-551">ViForwardChar</span></span>

<span data-ttu-id="50ed9-552">在 Vi 编辑模式下将光标向右移动一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="50ed9-553">这可能会将光标移到下一行的多行输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="50ed9-554">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="50ed9-555">Vi 命令模式： `<RightArrow>` 、 `<Spacebar>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="50ed9-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-556">ViEndOfGlob</span></span>

<span data-ttu-id="50ed9-557">将光标移到单词的末尾，只使用空格作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="50ed9-558">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="50ed9-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="50ed9-560">移到上一个词的末尾，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="50ed9-561">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="50ed9-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="50ed9-562">ViGotoBrace</span></span>

<span data-ttu-id="50ed9-563">类似于 GotoBrace，但基于字符，而不是基于标记。</span><span class="sxs-lookup"><span data-stu-id="50ed9-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="50ed9-564">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="50ed9-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="50ed9-565">ViNextGlob</span></span>

<span data-ttu-id="50ed9-566">移到下一个单词，只使用空格作为单词分隔符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="50ed9-567">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="50ed9-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-568">ViNextWord</span></span>

<span data-ttu-id="50ed9-569">将光标向前移动到下一个单词的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="50ed9-570">字边界由一组可配置的字符集定义。</span><span class="sxs-lookup"><span data-stu-id="50ed9-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="50ed9-571">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="50ed9-572">历史记录函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="50ed9-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-573">BeginningOfHistory</span></span>

<span data-ttu-id="50ed9-574">移到历史记录中的第一项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="50ed9-575">Emacs `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="50ed9-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-576">ClearHistory</span></span>

<span data-ttu-id="50ed9-577">清除 PSReadLine 中的历史记录。</span><span class="sxs-lookup"><span data-stu-id="50ed9-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="50ed9-578">这不会影响 PowerShell 历史记录。</span><span class="sxs-lookup"><span data-stu-id="50ed9-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="50ed9-579">Cmd：`<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="50ed9-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-580">EndOfHistory</span></span>

<span data-ttu-id="50ed9-581">移到历史记录中 (当前输入) 的最后一项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="50ed9-582">Emacs `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="50ed9-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-583">ForwardSearchHistory</span></span>

<span data-ttu-id="50ed9-584">通过历史记录执行增量向前搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="50ed9-585">Cmd：`<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="50ed9-586">Emacs `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="50ed9-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-587">HistorySearchBackward</span></span>

<span data-ttu-id="50ed9-588">将当前输入替换为 PSReadLine 历史记录中的 "previous" 项，该匹配项与开始与输入和光标之间的字符匹配。</span><span class="sxs-lookup"><span data-stu-id="50ed9-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="50ed9-589">Cmd：`<F8>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="50ed9-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="50ed9-590">HistorySearchForward</span></span>

<span data-ttu-id="50ed9-591">将当前输入替换为 PSReadLine 历史记录中与 start 与 input 和 cursor 之间的字符相匹配的 "next" 项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="50ed9-592">Cmd：`<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="50ed9-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-593">NextHistory</span></span>

<span data-ttu-id="50ed9-594">将当前输入替换为 PSReadLine 历史记录中的 "next" 项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="50ed9-595">Cmd：`<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="50ed9-596">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="50ed9-597">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="50ed9-598">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="50ed9-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-599">PreviousHistory</span></span>

<span data-ttu-id="50ed9-600">将当前输入替换为 PSReadLine 历史记录中的 "previous" 项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="50ed9-601">Cmd：`<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="50ed9-602">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="50ed9-603">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="50ed9-604">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="50ed9-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="50ed9-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="50ed9-605">ReverseSearchHistory</span></span>

<span data-ttu-id="50ed9-606">通过历史记录执行增量向后搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="50ed9-607">Cmd：`<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="50ed9-608">Emacs `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="50ed9-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="50ed9-610">提示输入搜索字符串并在 AcceptLine 上开始搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="50ed9-611">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="50ed9-612">Vi 命令模式： `</>` ， `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="50ed9-613">完成函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="50ed9-614">完成</span><span class="sxs-lookup"><span data-stu-id="50ed9-614">Complete</span></span>

<span data-ttu-id="50ed9-615">尝试对光标周围的文本执行完成。</span><span class="sxs-lookup"><span data-stu-id="50ed9-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="50ed9-616">如果有多个可能的完成，则使用最长的明确前缀完成。</span><span class="sxs-lookup"><span data-stu-id="50ed9-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="50ed9-617">如果尝试完成最长的明确完成，则会显示一个可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="50ed9-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="50ed9-618">Emacs `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="50ed9-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="50ed9-619">MenuComplete</span></span>

<span data-ttu-id="50ed9-620">尝试对光标周围的文本执行完成。</span><span class="sxs-lookup"><span data-stu-id="50ed9-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="50ed9-621">如果有多个可能的完成，则使用最长的明确前缀完成。</span><span class="sxs-lookup"><span data-stu-id="50ed9-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="50ed9-622">如果尝试完成最长的明确完成，则会显示一个可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="50ed9-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="50ed9-623">Cmd： `<Ctrl+@>` ， `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="50ed9-624">Emacs `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="50ed9-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="50ed9-625">PossibleCompletions</span></span>

<span data-ttu-id="50ed9-626">显示可能的完成列表。</span><span class="sxs-lookup"><span data-stu-id="50ed9-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="50ed9-627">Emacs `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="50ed9-628">Vi 插入模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="50ed9-629">Vi 命令模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="50ed9-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="50ed9-630">TabCompleteNext</span></span>

<span data-ttu-id="50ed9-631">尝试使用下一个可用完成来完成光标周围的文本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="50ed9-632">Cmd：`<Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="50ed9-633">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="50ed9-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="50ed9-634">TabCompletePrevious</span></span>

<span data-ttu-id="50ed9-635">尝试使用以前的可用完成功能完成光标周围的文本。</span><span class="sxs-lookup"><span data-stu-id="50ed9-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="50ed9-636">Cmd：`<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="50ed9-637">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="50ed9-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="50ed9-638">ViTabCompleteNext</span></span>

<span data-ttu-id="50ed9-639">结束当前编辑组（如果需要），并调用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="50ed9-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="50ed9-640">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="50ed9-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="50ed9-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="50ed9-642">结束当前编辑组（如果需要），并调用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="50ed9-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="50ed9-643">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="50ed9-644">杂项函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-644">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="50ed9-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="50ed9-646">接受内嵌或所选建议的下一个单词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-646">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="50ed9-647">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="50ed9-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="50ed9-648">AcceptSuggestion</span></span>

<span data-ttu-id="50ed9-649">接受当前内联或所选的建议。</span><span class="sxs-lookup"><span data-stu-id="50ed9-649">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="50ed9-650">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-650">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="50ed9-651">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="50ed9-651">CaptureScreen</span></span>

<span data-ttu-id="50ed9-652">启动交互屏幕捕获-向上/向下箭头选择 "线条"，将选定文本作为文本和 html 复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="50ed9-652">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="50ed9-653">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-653">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="50ed9-654">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="50ed9-654">ClearScreen</span></span>

<span data-ttu-id="50ed9-655">清除屏幕并在屏幕的顶部绘制当前线条。</span><span class="sxs-lookup"><span data-stu-id="50ed9-655">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="50ed9-656">Cmd：`<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-656">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="50ed9-657">Emacs `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-657">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="50ed9-658">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-658">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="50ed9-659">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-659">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="50ed9-660">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="50ed9-660">DigitArgument</span></span>

<span data-ttu-id="50ed9-661">启动新的数字参数，使其传递到其他函数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-661">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="50ed9-662">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="50ed9-662">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="50ed9-663">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="50ed9-663">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="50ed9-664">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` 、 `<7>` 、 `<8>` 、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-664">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="50ed9-665">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="50ed9-665">InvokePrompt</span></span>

<span data-ttu-id="50ed9-666">清除当前提示符并调用 prompt 函数以重新显示提示符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-666">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="50ed9-667">适用于更改状态的自定义密钥处理程序，例如更改当前目录。</span><span class="sxs-lookup"><span data-stu-id="50ed9-667">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="50ed9-668">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-668">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="50ed9-669">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="50ed9-669">ScrollDisplayDown</span></span>

<span data-ttu-id="50ed9-670">将显示向下滚动一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="50ed9-670">Scroll the display down one screen.</span></span>

- <span data-ttu-id="50ed9-671">Cmd：`<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-671">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="50ed9-672">Emacs `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-672">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="50ed9-673">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-673">ScrollDisplayDownLine</span></span>

<span data-ttu-id="50ed9-674">将显示向下滚动一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-674">Scroll the display down one line.</span></span>

- <span data-ttu-id="50ed9-675">Cmd：`<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-675">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="50ed9-676">Emacs `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-676">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="50ed9-677">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="50ed9-677">ScrollDisplayToCursor</span></span>

<span data-ttu-id="50ed9-678">将显示滚动到光标处。</span><span class="sxs-lookup"><span data-stu-id="50ed9-678">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="50ed9-679">Emacs `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-679">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="50ed9-680">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="50ed9-680">ScrollDisplayTop</span></span>

<span data-ttu-id="50ed9-681">向顶部滚动显示。</span><span class="sxs-lookup"><span data-stu-id="50ed9-681">Scroll the display to the top.</span></span>

- <span data-ttu-id="50ed9-682">Emacs `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-682">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="50ed9-683">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="50ed9-683">ScrollDisplayUp</span></span>

<span data-ttu-id="50ed9-684">将显示向上滚动一屏。</span><span class="sxs-lookup"><span data-stu-id="50ed9-684">Scroll the display up one screen.</span></span>

- <span data-ttu-id="50ed9-685">Cmd：`<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-685">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="50ed9-686">Emacs `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-686">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="50ed9-687">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-687">ScrollDisplayUpLine</span></span>

<span data-ttu-id="50ed9-688">将显示向上滚动一行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-688">Scroll the display up one line.</span></span>

- <span data-ttu-id="50ed9-689">Cmd：`<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-689">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="50ed9-690">Emacs `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-690">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="50ed9-691">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="50ed9-691">SelfInsert</span></span>

<span data-ttu-id="50ed9-692">插入密钥。</span><span class="sxs-lookup"><span data-stu-id="50ed9-692">Insert the key.</span></span>

- <span data-ttu-id="50ed9-693">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-693">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="50ed9-694">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="50ed9-694">ShowKeyBindings</span></span>

<span data-ttu-id="50ed9-695">显示所有绑定键。</span><span class="sxs-lookup"><span data-stu-id="50ed9-695">Show all bound keys.</span></span>

- <span data-ttu-id="50ed9-696">Cmd：`<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-696">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="50ed9-697">Emacs `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-697">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="50ed9-698">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-698">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="50ed9-699">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="50ed9-699">ViCommandMode</span></span>

<span data-ttu-id="50ed9-700">将当前运行模式从 Vi-Insert 切换到 Vi-Command。</span><span class="sxs-lookup"><span data-stu-id="50ed9-700">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="50ed9-701">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-701">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="50ed9-702">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="50ed9-702">ViDigitArgumentInChord</span></span>

<span data-ttu-id="50ed9-703">启动新的数字参数，将其传递给其他函数，同时使用 vi 的鼠标左键之一。</span><span class="sxs-lookup"><span data-stu-id="50ed9-703">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="50ed9-704">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-704">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="50ed9-705">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="50ed9-705">ViEditVisually</span></span>

<span data-ttu-id="50ed9-706">在 $env： EDITOR 或 $env：视觉对象指定的文本编辑器中编辑命令行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-706">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="50ed9-707">Emacs `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-707">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="50ed9-708">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-708">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="50ed9-709">ViExit</span><span class="sxs-lookup"><span data-stu-id="50ed9-709">ViExit</span></span>

<span data-ttu-id="50ed9-710">退出 shell。</span><span class="sxs-lookup"><span data-stu-id="50ed9-710">Exits the shell.</span></span>

- <span data-ttu-id="50ed9-711">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-711">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="50ed9-712">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="50ed9-712">ViInsertMode</span></span>

<span data-ttu-id="50ed9-713">切换到插入模式。</span><span class="sxs-lookup"><span data-stu-id="50ed9-713">Switch to Insert mode.</span></span>

- <span data-ttu-id="50ed9-714">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-714">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="50ed9-715">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="50ed9-715">WhatIsKey</span></span>

<span data-ttu-id="50ed9-716">阅读密钥，并告诉我密钥的绑定内容。</span><span class="sxs-lookup"><span data-stu-id="50ed9-716">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="50ed9-717">Cmd：`<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-717">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="50ed9-718">Emacs `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-718">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="50ed9-719">选择函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-719">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="50ed9-720">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="50ed9-720">ExchangePointAndMark</span></span>

<span data-ttu-id="50ed9-721">将光标置于标记的位置，并将标记移到光标所在的位置。</span><span class="sxs-lookup"><span data-stu-id="50ed9-721">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="50ed9-722">Emacs `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-722">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="50ed9-723">SelectAll</span><span class="sxs-lookup"><span data-stu-id="50ed9-723">SelectAll</span></span>

<span data-ttu-id="50ed9-724">选择整行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-724">Select the entire line.</span></span>

- <span data-ttu-id="50ed9-725">Cmd：`<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-725">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="50ed9-726">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-726">SelectBackwardChar</span></span>

<span data-ttu-id="50ed9-727">调整当前选定内容以包括前一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-727">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="50ed9-728">Cmd：`<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-728">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-729">Emacs `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-729">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="50ed9-730">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-730">SelectBackwardsLine</span></span>

<span data-ttu-id="50ed9-731">调整当前所选内容，使其包括从光标到行的开头。</span><span class="sxs-lookup"><span data-stu-id="50ed9-731">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="50ed9-732">Cmd：`<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-732">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="50ed9-733">Emacs `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-733">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="50ed9-734">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-734">SelectBackwardWord</span></span>

<span data-ttu-id="50ed9-735">调整当前所选内容以包含上一个词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-735">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="50ed9-736">Cmd：`<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-736">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="50ed9-737">Emacs `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-737">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="50ed9-738">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-738">SelectForwardChar</span></span>

<span data-ttu-id="50ed9-739">调整当前所选内容以包含下一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-739">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="50ed9-740">Cmd：`<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-740">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="50ed9-741">Emacs `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-741">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="50ed9-742">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-742">SelectForwardWord</span></span>

<span data-ttu-id="50ed9-743">使用 ForwardWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-743">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="50ed9-744">Emacs `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-744">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="50ed9-745">SelectLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-745">SelectLine</span></span>

<span data-ttu-id="50ed9-746">调整当前所选内容，使其包括从光标到行尾的内容。</span><span class="sxs-lookup"><span data-stu-id="50ed9-746">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="50ed9-747">Cmd：`<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-747">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="50ed9-748">Emacs `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-748">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="50ed9-749">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-749">SelectNextWord</span></span>

<span data-ttu-id="50ed9-750">调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-750">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="50ed9-751">Cmd：`<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-751">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="50ed9-752">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-752">SelectShellBackwardWord</span></span>

<span data-ttu-id="50ed9-753">使用 ShellBackwardWord 调整当前所选内容，使其包含前一词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-753">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="50ed9-754">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-754">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="50ed9-755">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-755">SelectShellForwardWord</span></span>

<span data-ttu-id="50ed9-756">使用 ShellForwardWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-756">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="50ed9-757">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-757">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="50ed9-758">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="50ed9-758">SelectShellNextWord</span></span>

<span data-ttu-id="50ed9-759">使用 ShellNextWord 调整当前所选内容以包含下一个单词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-759">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="50ed9-760">函数未绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-760">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="50ed9-761">SetMark</span><span class="sxs-lookup"><span data-stu-id="50ed9-761">SetMark</span></span>

<span data-ttu-id="50ed9-762">标记光标的当前位置，以供后续编辑命令使用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-762">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="50ed9-763">Emacs `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-763">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="50ed9-764">预测 IntelliSense 函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-764">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="50ed9-765">需要启用预测 IntelliSense 才能使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="50ed9-765">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="50ed9-766">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="50ed9-766">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="50ed9-767">接受预测 IntelliSense 中的下一个内嵌建议词。</span><span class="sxs-lookup"><span data-stu-id="50ed9-767">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="50ed9-768">此函数可以<kbd></kbd> + 通过运行以下命令与 Ctrl<kbd>F</kbd>绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-768">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="50ed9-769">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="50ed9-769">AcceptSuggestion</span></span>

<span data-ttu-id="50ed9-770">当光标位于当前行的末尾时，通过按 <kbd>右箭头</kbd> ，接受预测 IntelliSense 中的当前内联建议。</span><span class="sxs-lookup"><span data-stu-id="50ed9-770">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="50ed9-771">搜索函数</span><span class="sxs-lookup"><span data-stu-id="50ed9-771">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="50ed9-772">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="50ed9-772">CharacterSearch</span></span>

<span data-ttu-id="50ed9-773">读取字符并向前搜索该字符的下一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-773">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="50ed9-774">如果指定了参数，则向前搜索 (或向后) 对于第 n 个匹配项为负。</span><span class="sxs-lookup"><span data-stu-id="50ed9-774">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="50ed9-775">Cmd：`<F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-775">Cmd: `<F3>`</span></span>
- <span data-ttu-id="50ed9-776">Emacs `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-776">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="50ed9-777">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-777">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="50ed9-778">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-778">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="50ed9-779">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-779">CharacterSearchBackward</span></span>

<span data-ttu-id="50ed9-780">读取字符并向后搜索该字符的下一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="50ed9-780">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="50ed9-781">如果指定了参数，则在第 n 个匹配项) 反向搜索时 (或转发。</span><span class="sxs-lookup"><span data-stu-id="50ed9-781">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="50ed9-782">Cmd：`<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-782">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="50ed9-783">Emacs `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-783">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="50ed9-784">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-784">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="50ed9-785">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-785">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="50ed9-786">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="50ed9-786">RepeatLastCharSearch</span></span>

<span data-ttu-id="50ed9-787">重复上次记录的字符搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-787">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="50ed9-788">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-788">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="50ed9-789">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="50ed9-789">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="50ed9-790">重复上次记录的字符搜索，但采用相反方向。</span><span class="sxs-lookup"><span data-stu-id="50ed9-790">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="50ed9-791">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-791">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="50ed9-792">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="50ed9-792">RepeatSearch</span></span>

<span data-ttu-id="50ed9-793">像以前一样，重复最后一个搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-793">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="50ed9-794">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-794">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="50ed9-795">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-795">RepeatSearchBackward</span></span>

<span data-ttu-id="50ed9-796">像以前一样，重复最后一个搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-796">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="50ed9-797">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-797">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="50ed9-798">SearchChar</span><span class="sxs-lookup"><span data-stu-id="50ed9-798">SearchChar</span></span>

<span data-ttu-id="50ed9-799">阅读下一个字符，然后查找、前进，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-799">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="50ed9-800">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="50ed9-800">This is for 't' functionality.</span></span>

- <span data-ttu-id="50ed9-801">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-801">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="50ed9-802">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="50ed9-802">SearchCharBackward</span></span>

<span data-ttu-id="50ed9-803">读取下一个字符，然后查找它，向后移动，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-803">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="50ed9-804">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="50ed9-804">This is for 'T' functionality.</span></span>

- <span data-ttu-id="50ed9-805">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-805">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="50ed9-806">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="50ed9-806">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="50ed9-807">读取下一个字符，然后查找它，向后移动，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-807">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="50ed9-808">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="50ed9-808">This is for 'T' functionality.</span></span>

- <span data-ttu-id="50ed9-809">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-809">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="50ed9-810">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="50ed9-810">SearchCharWithBackoff</span></span>

<span data-ttu-id="50ed9-811">阅读下一个字符，然后查找、前进，然后再返回一个字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-811">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="50ed9-812">这适用于 "t" 功能。</span><span class="sxs-lookup"><span data-stu-id="50ed9-812">This is for 't' functionality.</span></span>

- <span data-ttu-id="50ed9-813">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-813">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="50ed9-814">SearchForward</span><span class="sxs-lookup"><span data-stu-id="50ed9-814">SearchForward</span></span>

<span data-ttu-id="50ed9-815">提示输入搜索字符串并在 AcceptLine 上开始搜索。</span><span class="sxs-lookup"><span data-stu-id="50ed9-815">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="50ed9-816">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-816">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="50ed9-817">Vi 命令模式： `<?>` ， `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="50ed9-817">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="50ed9-818">自定义键绑定</span><span class="sxs-lookup"><span data-stu-id="50ed9-818">Custom Key Bindings</span></span>

<span data-ttu-id="50ed9-819">PSReadLine 支持使用 cmdlet 的自定义键绑定 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-819">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="50ed9-820">大多数自定义键绑定调用上述函数之一，例如</span><span class="sxs-lookup"><span data-stu-id="50ed9-820">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="50ed9-821">可以将 ScriptBlock 绑定到密钥。</span><span class="sxs-lookup"><span data-stu-id="50ed9-821">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="50ed9-822">ScriptBlock 可以执行任何所需的操作。</span><span class="sxs-lookup"><span data-stu-id="50ed9-822">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="50ed9-823">一些有用的示例包括</span><span class="sxs-lookup"><span data-stu-id="50ed9-823">Some useful examples include</span></span>

- <span data-ttu-id="50ed9-824">编辑命令行</span><span class="sxs-lookup"><span data-stu-id="50ed9-824">edit the command line</span></span>
- <span data-ttu-id="50ed9-825">打开新窗口 (例如，帮助) </span><span class="sxs-lookup"><span data-stu-id="50ed9-825">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="50ed9-826">更改目录而不更改命令行</span><span class="sxs-lookup"><span data-stu-id="50ed9-826">change directories without changing the command line</span></span>

<span data-ttu-id="50ed9-827">ScriptBlock 接收两个参数：</span><span class="sxs-lookup"><span data-stu-id="50ed9-827">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="50ed9-828">`$key` -一个作为触发自定义绑定的密钥的 **[ConsoleKeyInfo]** 对象。</span><span class="sxs-lookup"><span data-stu-id="50ed9-828">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="50ed9-829">如果将相同的 ScriptBlock 绑定到多个键，并且需要根据关键字执行不同的操作，则可以选中 $key。</span><span class="sxs-lookup"><span data-stu-id="50ed9-829">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="50ed9-830">许多自定义绑定会忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-830">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="50ed9-831">`$arg` -任意参数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-831">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="50ed9-832">大多数情况下，这将是用户从键绑定 DigitArgument 传递的整数参数。</span><span class="sxs-lookup"><span data-stu-id="50ed9-832">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="50ed9-833">如果绑定不接受参数，则忽略此参数是合理的。</span><span class="sxs-lookup"><span data-stu-id="50ed9-833">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="50ed9-834">我们来看一个示例，该示例将一个命令行添加到历史记录中，而不执行它。</span><span class="sxs-lookup"><span data-stu-id="50ed9-834">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="50ed9-835">如果您认为您忘记了某些事情，但又不想重新输入您已经输入的命令行，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-835">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="50ed9-836">你可以在 PSReadLine 模块文件夹中安装的文件中查看更多示例 `SamplePSReadLineProfile.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-836">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="50ed9-837">大多数键绑定使用一些 helper 函数来编辑命令行。</span><span class="sxs-lookup"><span data-stu-id="50ed9-837">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="50ed9-838">下一节将介绍这些 Api。</span><span class="sxs-lookup"><span data-stu-id="50ed9-838">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="50ed9-839">自定义键绑定支持 Api</span><span class="sxs-lookup"><span data-stu-id="50ed9-839">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="50ed9-840">以下函数是 PSConsoleReadLine 中的公共函数，但不能直接绑定到密钥。</span><span class="sxs-lookup"><span data-stu-id="50ed9-840">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="50ed9-841">大多数在自定义键绑定中很有用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-841">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="50ed9-842">向历史记录中添加一个命令行而不执行它。</span><span class="sxs-lookup"><span data-stu-id="50ed9-842">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="50ed9-843">清除终止环。</span><span class="sxs-lookup"><span data-stu-id="50ed9-843">Clear the kill-ring.</span></span>  <span data-ttu-id="50ed9-844">这主要用于测试。</span><span class="sxs-lookup"><span data-stu-id="50ed9-844">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="50ed9-845">从开始删除长度字符。</span><span class="sxs-lookup"><span data-stu-id="50ed9-845">Delete length characters from start.</span></span>  <span data-ttu-id="50ed9-846">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="50ed9-846">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="50ed9-847">根据用户首选项执行 Ding 操作。</span><span class="sxs-lookup"><span data-stu-id="50ed9-847">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="50ed9-848">这两个函数检索有关输入缓冲区的当前状态的有用信息。</span><span class="sxs-lookup"><span data-stu-id="50ed9-848">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="50ed9-849">第一种方案更常见用于简单情况。</span><span class="sxs-lookup"><span data-stu-id="50ed9-849">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="50ed9-850">如果绑定使用 Ast 执行更高级的操作，则会使用第二个。</span><span class="sxs-lookup"><span data-stu-id="50ed9-850">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="50ed9-851">这两个函数由使用 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-851">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="50ed9-852">第一个用于获取所有键绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-852">The first is used to get all key bindings.</span></span> <span data-ttu-id="50ed9-853">第二个用于获取特定的键绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-853">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="50ed9-854">此函数由 Get-PSReadLineOption 使用，并可能在自定义键绑定中不太有用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-854">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="50ed9-855">如果未在命令行上进行选择，则将在 "开始" 和 "长度" 中返回-1。</span><span class="sxs-lookup"><span data-stu-id="50ed9-855">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="50ed9-856">如果命令行上有选择，则返回选定内容的开始和长度。</span><span class="sxs-lookup"><span data-stu-id="50ed9-856">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="50ed9-857">在光标处插入字符或字符串。</span><span class="sxs-lookup"><span data-stu-id="50ed9-857">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="50ed9-858">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="50ed9-858">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="50ed9-859">这是 PSReadLine 的主要入口点。</span><span class="sxs-lookup"><span data-stu-id="50ed9-859">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="50ed9-860">它不支持递归，因此在自定义键绑定中不起作用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-860">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="50ed9-861">此函数由 Remove-PSReadLineKeyHandler 使用，并可能在自定义键绑定中不太有用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-861">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="50ed9-862">替换部分输入。</span><span class="sxs-lookup"><span data-stu-id="50ed9-862">Replace some of the input.</span></span> <span data-ttu-id="50ed9-863">此操作支持撤消/重做。</span><span class="sxs-lookup"><span data-stu-id="50ed9-863">This operation supports undo/redo.</span></span> <span data-ttu-id="50ed9-864">这优先于删除后再执行 Insert，因为它被视为单个操作来撤消。</span><span class="sxs-lookup"><span data-stu-id="50ed9-864">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="50ed9-865">将光标移动到给定偏移量。</span><span class="sxs-lookup"><span data-stu-id="50ed9-865">Move the cursor to the given offset.</span></span> <span data-ttu-id="50ed9-866">不跟踪游标移动以便撤消。</span><span class="sxs-lookup"><span data-stu-id="50ed9-866">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="50ed9-867">此函数是 cmdlet PSReadLineOption 使用的帮助器方法，但可能对要临时更改设置的自定义密钥绑定很有用。</span><span class="sxs-lookup"><span data-stu-id="50ed9-867">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="50ed9-868">此帮助器方法用于接受 DigitArgument 的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="50ed9-868">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="50ed9-869">典型调用如下所示</span><span class="sxs-lookup"><span data-stu-id="50ed9-869">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="50ed9-870">说明</span><span class="sxs-lookup"><span data-stu-id="50ed9-870">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="50ed9-871">命令历史记录</span><span class="sxs-lookup"><span data-stu-id="50ed9-871">Command History</span></span>

<span data-ttu-id="50ed9-872">PSReadLine 维护一个历史记录文件，其中包含在命令行中输入的所有命令和数据。</span><span class="sxs-lookup"><span data-stu-id="50ed9-872">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="50ed9-873">这可能包含敏感数据（包括密码）。</span><span class="sxs-lookup"><span data-stu-id="50ed9-873">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="50ed9-874">例如，如果使用 cmdlet，则 `ConvertTo-SecureString` 密码将作为纯文本记录到历史记录文件中。</span><span class="sxs-lookup"><span data-stu-id="50ed9-874">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="50ed9-875">历史记录文件是一个名为的文件 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-875">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="50ed9-876">在 Windows 系统上，历史记录文件存储在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-876">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="50ed9-877">在非 Windows 系统上，历史记录文件存储在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或上 `$env:HOME/.local/share/powershell/PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="50ed9-877">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="50ed9-878">参与 PSReadLine 的反馈 &</span><span class="sxs-lookup"><span data-stu-id="50ed9-878">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="50ed9-879">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="50ed9-879">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="50ed9-880">可在 GitHub 页上随意提交拉取请求或提交反馈。</span><span class="sxs-lookup"><span data-stu-id="50ed9-880">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="50ed9-881">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50ed9-881">See Also</span></span>

<span data-ttu-id="50ed9-882">PSReadLine 会受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 库的严重影响。</span><span class="sxs-lookup"><span data-stu-id="50ed9-882">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
