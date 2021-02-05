---
title: 帮助系统
description: 掌握帮助系统是成功使用 PowerShell 的关键。
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cfb12f57b7bb6c514f4e19a93dfe9c77245bd977
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598659"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="60482-103">第 2 章 - 帮助系统</span><span class="sxs-lookup"><span data-stu-id="60482-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="60482-104">两组 IT 专业人员在没有使用计算机的情况下参加了笔试，目的是确定他们的 PowerShell 技能水平。</span><span class="sxs-lookup"><span data-stu-id="60482-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="60482-105">PowerShell 初学者归为一个组，专家归为另一个组。</span><span class="sxs-lookup"><span data-stu-id="60482-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="60482-106">根据测试结果来看，两组人员掌握的技能水平似乎并没有太大差异。</span><span class="sxs-lookup"><span data-stu-id="60482-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="60482-107">两组人员又参加了第二个测试，该测试与第一个测试类似。</span><span class="sxs-lookup"><span data-stu-id="60482-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="60482-108">这次，允许他们使用安装了 PowerShell 的计算机，但计算机无法访问 Internet。</span><span class="sxs-lookup"><span data-stu-id="60482-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="60482-109">第二次测试的结果显示两组人员之间的技能水平存在巨大差异。</span><span class="sxs-lookup"><span data-stu-id="60482-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="60482-110">专家不一定总是知道答案，但是他们知道如何得到答案。</span><span class="sxs-lookup"><span data-stu-id="60482-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="60482-111">这两个组之间第一次测试和第二次测试得出的结果有何不同？</span><span class="sxs-lookup"><span data-stu-id="60482-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="60482-112">这两个测试的结果之间的差异是因为专家不会记忆如何在 PowerShell 中使用数千个命令。</span><span class="sxs-lookup"><span data-stu-id="60482-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="60482-113">他们了解如何在 PowerShell 中很好地利用帮助系统。</span><span class="sxs-lookup"><span data-stu-id="60482-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="60482-114">这样，他们就可以在需要时找到必要的命令，在找到这些命令后，也知道如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="60482-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="60482-115">我听闻 PowerShell 的发明者 Jeffrey Snover 讲过多次类似的故事。</span><span class="sxs-lookup"><span data-stu-id="60482-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="60482-116">掌握帮助系统是成功使用 PowerShell 的关键。</span><span class="sxs-lookup"><span data-stu-id="60482-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="60482-117">可发现性</span><span class="sxs-lookup"><span data-stu-id="60482-117">Discoverability</span></span>

<span data-ttu-id="60482-118">PowerShell 中的编译命令称为 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="60482-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="60482-119">Cmdlet 的发音为“command-let”（而不是 CMD-let）。</span><span class="sxs-lookup"><span data-stu-id="60482-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="60482-120">Cmdlet 名称采用单数形式的“动词-名词”命令形式，这样更易于被发现。</span><span class="sxs-lookup"><span data-stu-id="60482-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="60482-121">例如，用于确定正在运行哪些进程的 cmdlet 是 `Get-Process`，而用于检索服务及其状态的列表的 cmdlet 是 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="60482-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="60482-122">PowerShell 中还有其他类型的命令（例如别名和函数），本书后面部分将对其进行介绍。</span><span class="sxs-lookup"><span data-stu-id="60482-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="60482-123">术语 PowerShell 命令是一个通用术语，通常用于指代 PowerShell 中任何类型的命令，不管是 cmdlet、函数还是别名。</span><span class="sxs-lookup"><span data-stu-id="60482-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="60482-124">PowerShell 中的三个核心 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60482-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="60482-125">`Get-Member`（在第 3 章中介绍此内容）</span><span class="sxs-lookup"><span data-stu-id="60482-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="60482-126">我经常被问到的一个问题是如何确定 PowerShell 中的命令是什么？</span><span class="sxs-lookup"><span data-stu-id="60482-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="60482-127">`Get-Command` 和 `Get-Help` 均可用于确定命令。</span><span class="sxs-lookup"><span data-stu-id="60482-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="60482-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="60482-128">Get-Help</span></span>

<span data-ttu-id="60482-129">`Get-Help` 是多用途命令。</span><span class="sxs-lookup"><span data-stu-id="60482-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="60482-130">`Get-Help` 帮助你了解找到命令后如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="60482-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="60482-131">`Get-Help` 也可用于帮助查找命令，但与 `Get-Command` 相比，它采用不同且较为间接的方式。</span><span class="sxs-lookup"><span data-stu-id="60482-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="60482-132">使用 `Get-Help` 查找命令时，它首先根据提供的输入来搜索命令名称的通配符匹配项。</span><span class="sxs-lookup"><span data-stu-id="60482-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="60482-133">如果找不到匹配项，它将搜索帮助主题本身；如果还找不到匹配项，则返回错误。</span><span class="sxs-lookup"><span data-stu-id="60482-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="60482-134">与通常的看法相反，`Get-Help` 可用于查找没有帮助主题的命令。</span><span class="sxs-lookup"><span data-stu-id="60482-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="60482-135">关于 PowerShell 中的帮助系统，首先需要了解如何使用 `Get-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="60482-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="60482-136">以下命令用于显示 `Get-Help` 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="60482-137">从 PowerShell 版本 3 开始，操作系统不随附 PowerShell 帮助功能。</span><span class="sxs-lookup"><span data-stu-id="60482-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="60482-138">第一次为命令运行 `Get-Help` 时，系统将显示上一条消息。</span><span class="sxs-lookup"><span data-stu-id="60482-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="60482-139">如果使用的是 `help` 函数或 `man` 别名（而不是 `Get-Help` cmdlet），则不会收到此提示。</span><span class="sxs-lookup"><span data-stu-id="60482-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="60482-140">若要回答“是”，请按 <kbd>Y</kbd> 以运行 `Update-Help` cmdlet，默认情况下该 cmdlet 需要 Internet 访问权限。</span><span class="sxs-lookup"><span data-stu-id="60482-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="60482-141">可以大写或小写形式指定 `Y`。</span><span class="sxs-lookup"><span data-stu-id="60482-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="60482-142">下载帮助并完成更新后，将为指定的命令返回帮助主题：</span><span class="sxs-lookup"><span data-stu-id="60482-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="60482-143">花几分钟在计算机上运行该示例，查看输出，并注意信息的分组方式：</span><span class="sxs-lookup"><span data-stu-id="60482-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="60482-144">名称</span><span class="sxs-lookup"><span data-stu-id="60482-144">NAME</span></span>
- <span data-ttu-id="60482-145">摘要</span><span class="sxs-lookup"><span data-stu-id="60482-145">SYNOPSIS</span></span>
- <span data-ttu-id="60482-146">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="60482-146">SYNTAX</span></span>
- <span data-ttu-id="60482-147">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="60482-147">DESCRIPTION</span></span>
- <span data-ttu-id="60482-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="60482-148">RELATED LINKS</span></span>
- <span data-ttu-id="60482-149">REMARKS</span><span class="sxs-lookup"><span data-stu-id="60482-149">REMARKS</span></span>

<span data-ttu-id="60482-150">如你所见，帮助主题可能包含大量的信息，而这甚至不是全部的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="60482-151">虽然参数不是特定于 PowerShell 的，但也是向命令提供输入的一种方式。</span><span class="sxs-lookup"><span data-stu-id="60482-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="60482-152">`Get-Help` 具有许多参数，可以指定这些参数，使结果中返回整个帮助主题或其子集。</span><span class="sxs-lookup"><span data-stu-id="60482-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="60482-153">上一组结果中显示的帮助主题的语法部分列出了 `Get-Help` 的所有参数。</span><span class="sxs-lookup"><span data-stu-id="60482-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="60482-154">乍一看，似乎在六个不同的地方列出了相同的参数。</span><span class="sxs-lookup"><span data-stu-id="60482-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="60482-155">语法部分中的每个不同的块都是参数集。</span><span class="sxs-lookup"><span data-stu-id="60482-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="60482-156">这意味着 `Get-Help` cmdlet 具有六个不同的参数集。</span><span class="sxs-lookup"><span data-stu-id="60482-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="60482-157">如果仔细研究，就会发现每个参数集中至少有一个不同的参数。</span><span class="sxs-lookup"><span data-stu-id="60482-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="60482-158">参数集是互斥的。</span><span class="sxs-lookup"><span data-stu-id="60482-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="60482-159">一旦使用了其中某个参数集中独有的某个参数，就只能使用该参数集中包含的参数。</span><span class="sxs-lookup"><span data-stu-id="60482-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="60482-160">例如，无法同时指定 Full 和 Detailed 参数，因为它们位于不同的参数集中 。</span><span class="sxs-lookup"><span data-stu-id="60482-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="60482-161">以下每个参数都位于不同的参数集中：</span><span class="sxs-lookup"><span data-stu-id="60482-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="60482-162">完全</span><span class="sxs-lookup"><span data-stu-id="60482-162">Full</span></span>
- <span data-ttu-id="60482-163">详细信息</span><span class="sxs-lookup"><span data-stu-id="60482-163">Detailed</span></span>
- <span data-ttu-id="60482-164">示例</span><span class="sxs-lookup"><span data-stu-id="60482-164">Examples</span></span>
- <span data-ttu-id="60482-165">联机</span><span class="sxs-lookup"><span data-stu-id="60482-165">Online</span></span>
- <span data-ttu-id="60482-166">参数</span><span class="sxs-lookup"><span data-stu-id="60482-166">Parameter</span></span>
- <span data-ttu-id="60482-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="60482-167">ShowWindow</span></span>

<span data-ttu-id="60482-168">语法部分中的所有晦涩的语法（例如方括号和尖括号）均具有某些含义，本书的附录 A 中对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="60482-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="60482-169">尽管这些语法很重要，但对于不熟悉 PowerShell 且日常不使用它的人来说，通常难以记住这些晦涩的语法。</span><span class="sxs-lookup"><span data-stu-id="60482-169">While important, learning the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="60482-170">若要详细了解如何更好地理解晦涩的语法，请参阅[附录 A][]。</span><span class="sxs-lookup"><span data-stu-id="60482-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="60482-171">对于初学者而言，可以通过一种更简单的方法来获取相同的信息（纯语言内容除外）。</span><span class="sxs-lookup"><span data-stu-id="60482-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="60482-172">指定 `Get-Help` 的 Full 参数后，可返回整个帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="60482-173">花几分钟在计算机上运行该示例，查看输出，并注意信息的分组方式：</span><span class="sxs-lookup"><span data-stu-id="60482-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="60482-174">名称</span><span class="sxs-lookup"><span data-stu-id="60482-174">NAME</span></span>
- <span data-ttu-id="60482-175">摘要</span><span class="sxs-lookup"><span data-stu-id="60482-175">SYNOPSIS</span></span>
- <span data-ttu-id="60482-176">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="60482-176">SYNTAX</span></span>
- <span data-ttu-id="60482-177">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="60482-177">DESCRIPTION</span></span>
- <span data-ttu-id="60482-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="60482-178">PARAMETERS</span></span>
- <span data-ttu-id="60482-179">输入</span><span class="sxs-lookup"><span data-stu-id="60482-179">INPUTS</span></span>
- <span data-ttu-id="60482-180">输出</span><span class="sxs-lookup"><span data-stu-id="60482-180">OUTPUTS</span></span>
- <span data-ttu-id="60482-181">注释</span><span class="sxs-lookup"><span data-stu-id="60482-181">NOTES</span></span>
- <span data-ttu-id="60482-182">示例</span><span class="sxs-lookup"><span data-stu-id="60482-182">EXAMPLES</span></span>
- <span data-ttu-id="60482-183">相关链接</span><span class="sxs-lookup"><span data-stu-id="60482-183">RELATED LINKS</span></span>

<span data-ttu-id="60482-184">请注意，使用 Full 参数返回了几个额外部分，其中一个部分是 PARAMETERS 部分，该部分提供的信息比晦涩的 SYNTAX 部分还要多。</span><span class="sxs-lookup"><span data-stu-id="60482-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="60482-185">Full 参数是一个开关参数。</span><span class="sxs-lookup"><span data-stu-id="60482-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="60482-186">不需要值的参数称为开关参数。</span><span class="sxs-lookup"><span data-stu-id="60482-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="60482-187">如果指定了某个开关参数，其值为 true；否则为 false。</span><span class="sxs-lookup"><span data-stu-id="60482-187">When a switch parameter is specified, its value is true and when it's not, its value is false.</span></span>

<span data-ttu-id="60482-188">如果已在 PowerShell 控制台中学完了本章，你会注意到屏幕上掠过了上一个显示 `Get-Help` 的完整帮助主题的命令，但快到你无法阅读该命令。</span><span class="sxs-lookup"><span data-stu-id="60482-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="60482-189">还有更好的办法。</span><span class="sxs-lookup"><span data-stu-id="60482-189">There's a better way.</span></span>

<span data-ttu-id="60482-190">`Help` 是一个函数，它通过管道将 `Get-Help` 传递给名为 `more` 的函数，后者是 Windows 中 `more.com` 可执行文件的包装器。</span><span class="sxs-lookup"><span data-stu-id="60482-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="60482-191">在 PowerShell 控制台中，`help` 一次提供一页帮助信息。</span><span class="sxs-lookup"><span data-stu-id="60482-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="60482-192">在 ISE 中，其工作方式与 `Get-Help` 相同。</span><span class="sxs-lookup"><span data-stu-id="60482-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="60482-193">建议使用 `help` 函数，而不使用 `Get-Help` cmdlet，因为前者提供了更好的体验，而且需要键入的内容更少。</span><span class="sxs-lookup"><span data-stu-id="60482-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="60482-194">不过，减少键入的内容有时并非是好事。</span><span class="sxs-lookup"><span data-stu-id="60482-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="60482-195">如果要将命令另存为脚本或与他人共享命令，请确保使用完整的 cmdlet 和参数名称。</span><span class="sxs-lookup"><span data-stu-id="60482-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="60482-196">完整名称是自描述名称，这使它们更易于理解。</span><span class="sxs-lookup"><span data-stu-id="60482-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="60482-197">请考虑下一个需要阅读和理解你的命令的人。</span><span class="sxs-lookup"><span data-stu-id="60482-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="60482-198">也许这个人就是你自己。</span><span class="sxs-lookup"><span data-stu-id="60482-198">It could be you.</span></span> <span data-ttu-id="60482-199">你的同事和将来的你自己将感谢你。</span><span class="sxs-lookup"><span data-stu-id="60482-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="60482-200">尝试在 Windows 10 实验环境计算机上的 PowerShell 控制台中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="60482-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="60482-201">在 Windows 10 实验环境计算机上运行这些命令时，是否注意到上述命令的输出存在任何差异？</span><span class="sxs-lookup"><span data-stu-id="60482-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="60482-202">除了最后两个选项每次返回一页以外，结果都一样。</span><span class="sxs-lookup"><span data-stu-id="60482-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="60482-203">使用 `Help` 函数时，可使用<kbd>空格键</kbd>显示下一页内容，可使用 <kbd>Ctrl</kbd>+<kbd>C</kbd> 取消在 PowerShell 控制台中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="60482-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="60482-204">第一个示例使用 `Get-Help` cmdlet，第二个示例使用 `Help` 函数，第三个示例在使用 `Help` 函数时省略了 Name 参数。</span><span class="sxs-lookup"><span data-stu-id="60482-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="60482-205">Name 是一个位置参数，在该示例中按位置使用该参数。</span><span class="sxs-lookup"><span data-stu-id="60482-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="60482-206">这意味着只要在正确的位置指定值本身，就可以在不指定参数名称的情况下指定值。</span><span class="sxs-lookup"><span data-stu-id="60482-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="60482-207">如何知晓在哪个位置指定值？</span><span class="sxs-lookup"><span data-stu-id="60482-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="60482-208">可通过阅读帮助信息来了解，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="60482-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="60482-209">请注意，在前面的示例中，将 Parameter 参数与 Help 函数一起使用，以便仅返回 Name 参数的帮助主题中的信息 。</span><span class="sxs-lookup"><span data-stu-id="60482-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="60482-210">与手动筛选帮助主题内容（有时可能超过一百页）相比，这样做会方便许多。</span><span class="sxs-lookup"><span data-stu-id="60482-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="60482-211">根据这些结果，可以看到 Name 参数是位置参数，并且在按位置使用时必须在位置零（第一个位置）处指定。</span><span class="sxs-lookup"><span data-stu-id="60482-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="60482-212">如果指定了参数名称，则参数名称的指定顺序无关紧要。</span><span class="sxs-lookup"><span data-stu-id="60482-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="60482-213">另一条重要的信息是，Name 参数的值的预期数据类型是单个字符串，该字符串由 `<String>` 表示。</span><span class="sxs-lookup"><span data-stu-id="60482-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="60482-214">如果它接受多个字符串，则数据类型将列为 `<String[]>`。</span><span class="sxs-lookup"><span data-stu-id="60482-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="60482-215">有时，你不想显示命令的整个帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="60482-216">除了 Full 之外，还有许多其他参数可以用 `Get-Help` 或 `Help` 指定。</span><span class="sxs-lookup"><span data-stu-id="60482-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="60482-217">尝试在 Windows 10 实验环境计算机上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="60482-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="60482-218">我通常将 `help <command name>` 与 Full 或 Online 参数一起使用 。</span><span class="sxs-lookup"><span data-stu-id="60482-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="60482-219">如果只对示例感兴趣，可使用 Examples 参数；如果只对特定参数感兴趣，可使用 Parameter 参数 。</span><span class="sxs-lookup"><span data-stu-id="60482-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="60482-220">ShowWindow 参数在单独的可搜索窗口中打开帮助主题，如果有多个监视器，还可以在其他监视器上显示该窗口。</span><span class="sxs-lookup"><span data-stu-id="60482-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="60482-221">我没有使用 ShowWindow 参数，因为存在不显示整个帮助主题的已知 bug。</span><span class="sxs-lookup"><span data-stu-id="60482-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="60482-222">如果需要在单独的窗口中显示帮助，建议使用 Online 参数或 Full 参数，并通过管道将结果传递给 `Out-GridView`，如以下示例所示 。</span><span class="sxs-lookup"><span data-stu-id="60482-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="60482-223">`Out-GridView` cmdlet，以及 `Get-Help` cmdlet 的 ShowWindow 参数都需要具有 GUI（图形用户界面）的操作系统。</span><span class="sxs-lookup"><span data-stu-id="60482-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="60482-224">如果尝试在使用服务器核心（不带 GUI）安装选项安装的 Windows Server 上使用其中任意一个，会生成一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="60482-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="60482-225">要使用 `Get-Help` 查找命令，请对 Name 参数使用星号 (`*`) 通配符。</span><span class="sxs-lookup"><span data-stu-id="60482-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="60482-226">指定搜索命令时使用的字词，作为 Name 参数的值，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="60482-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="60482-227">在前面的示例中，不需要 `*` 通配符，如果省略它们，得到的结果相同。</span><span class="sxs-lookup"><span data-stu-id="60482-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="60482-228">`Get-Help` 自动在无提示的情况下添加通配符。</span><span class="sxs-lookup"><span data-stu-id="60482-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="60482-229">上一条命令生成的结果与在进程的两头指定 `*` 通配符得到的结果相同。</span><span class="sxs-lookup"><span data-stu-id="60482-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="60482-230">我喜欢添加这些通配符，因为这样可以始终得到一致的结果。</span><span class="sxs-lookup"><span data-stu-id="60482-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="60482-231">另外，这些通配符仅在某些方案中需要。</span><span class="sxs-lookup"><span data-stu-id="60482-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="60482-232">在值中间添加通配符后，将不再以自动添加的方式将通配符添加到指定的值上。</span><span class="sxs-lookup"><span data-stu-id="60482-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="60482-233">除非将 `*` 通配符添加到 `pr*cess` 的开头，或开头和结尾，否则该命令不返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="60482-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="60482-234">如果指定的值以破折号开头，则会生成错误，因为 PowerShell 将其解释为参数名称，但 `Get-Help` cmdlet 不存在此类参数名称。</span><span class="sxs-lookup"><span data-stu-id="60482-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="60482-235">如果要查找的是以 `-process` 结尾的命令，则只需将 `*` 通配符添加到值的开头即可。</span><span class="sxs-lookup"><span data-stu-id="60482-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="60482-236">使用 `Get-Help` 搜索 PowerShell 命令时，使用更宽泛而不是更具体的搜索信息。</span><span class="sxs-lookup"><span data-stu-id="60482-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="60482-237">之前搜索 `process` 时只找到名称中包含 `process` 的命令，并且只返回了那些结果。</span><span class="sxs-lookup"><span data-stu-id="60482-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="60482-238">使用 `Get-Help` 搜索 `processes` 时，它找不到命令名称的任何匹配项，因此它将搜索系统中 PowerShell 中的每个帮助主题，并返回找到的所有匹配项。</span><span class="sxs-lookup"><span data-stu-id="60482-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="60482-239">这使其返回大量结果。</span><span class="sxs-lookup"><span data-stu-id="60482-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="60482-240">使用 `Help` 搜索 `process` 返回了 10 个结果，而使用该命令搜索 `processes` 返回了 68 个结果。</span><span class="sxs-lookup"><span data-stu-id="60482-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="60482-241">如果只找到一个结果，将显示帮助主题本身，而不显示命令列表。</span><span class="sxs-lookup"><span data-stu-id="60482-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="60482-242">现在来破除一个误区，即 PowerShell 中的 `Help` 只能找到具有帮助主题的命令。</span><span class="sxs-lookup"><span data-stu-id="60482-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="60482-243">请注意，在前面的示例中，`more` 没有帮助主题，但 PowerShell 中的 `Help` 系统仍可以找到它。</span><span class="sxs-lookup"><span data-stu-id="60482-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="60482-244">它只找到一个匹配项，并返回了基本的语法信息，如果命令没有帮助主题，就会看到这些信息。</span><span class="sxs-lookup"><span data-stu-id="60482-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="60482-245">PowerShell 包含大量的概念性（关于）帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="60482-246">以下命令可用于返回系统上所有“关于”帮助主题的列表。</span><span class="sxs-lookup"><span data-stu-id="60482-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="60482-247">将结果限制为单个“关于”帮助主题会显示实际的帮助主题内容，而不是返回一个列表。</span><span class="sxs-lookup"><span data-stu-id="60482-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="60482-248">必须更新 PowerShell 中的帮助系统，才能显示“关于”帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="60482-249">如果由于某种原因计算机上的帮助系统的初始更新失败，则在成功运行 `Update-Help` cmdlet 之前，文件将不可用。</span><span class="sxs-lookup"><span data-stu-id="60482-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="60482-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="60482-250">Get-Command</span></span>

<span data-ttu-id="60482-251">`Get-Command` 的作用是帮助查找命令。</span><span class="sxs-lookup"><span data-stu-id="60482-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="60482-252">运行不带任何参数的 `Get-Command` 会返回系统上所有命令的列表。</span><span class="sxs-lookup"><span data-stu-id="60482-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="60482-253">以下示例演示使用 `Get-Command` cmdlet 确定存在的用于处理进程的命令：</span><span class="sxs-lookup"><span data-stu-id="60482-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="60482-254">请注意，在前面运行了 `Get-Command` 的示例中，使用了 Noun 参数，并且将 `Process` 指定为 Noun 参数的值 。</span><span class="sxs-lookup"><span data-stu-id="60482-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="60482-255">如果不知道如何使用 `Get-Command` cmdlet，该怎么办？</span><span class="sxs-lookup"><span data-stu-id="60482-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="60482-256">可以使用 `Get-Help` 显示 `Get-Command` 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="60482-257">Name、Noun 和 Verb 参数均接受通配符  。</span><span class="sxs-lookup"><span data-stu-id="60482-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="60482-258">下面的示例演示与 Name 参数一起使用的通配符：</span><span class="sxs-lookup"><span data-stu-id="60482-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="60482-259">我不喜欢将通配符与 `Get-Command` 的 Name 参数一起使用，因为它还返回不是本机 PowerShell 命令的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="60482-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="60482-260">如果要在 Name 参数中使用通配符，建议使用 CommandType 参数来限定结果 。</span><span class="sxs-lookup"><span data-stu-id="60482-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="60482-261">更好的选择是使用 Verb 或/和 Noun 参数，因为只有 PowerShell 命令同时具有谓词和名词 。</span><span class="sxs-lookup"><span data-stu-id="60482-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="60482-262">发现帮助主题中存在问题？</span><span class="sxs-lookup"><span data-stu-id="60482-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="60482-263">好消息是，PowerShell 的帮助主题是开放源代码主题，可以在 GitHub 上的 [PowerShell-Docs][] 存储库中找到。</span><span class="sxs-lookup"><span data-stu-id="60482-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="60482-264">将帮助主题公开，不仅可以为自己解决错误信息，还可以帮助其他所有人解决错误信息。</span><span class="sxs-lookup"><span data-stu-id="60482-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="60482-265">只需在 GitHub 上创建 PowerShell 文档存储库的分支、更新帮助主题以及提交拉取请求。</span><span class="sxs-lookup"><span data-stu-id="60482-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="60482-266">接受拉取请求后，所有人都可以使用更正后的文档。</span><span class="sxs-lookup"><span data-stu-id="60482-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="60482-267">更新帮助</span><span class="sxs-lookup"><span data-stu-id="60482-267">Updating Help</span></span>

<span data-ttu-id="60482-268">PowerShell 帮助主题的本地副本之前已更新了关于某个请求的命令的首次帮助信息。</span><span class="sxs-lookup"><span data-stu-id="60482-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="60482-269">建议定期更新帮助系统，因为可能会不时更新帮助内容。</span><span class="sxs-lookup"><span data-stu-id="60482-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="60482-270">`Update-Help` cmdlet 用于更新帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="60482-271">默认情况下，它需要访问 Internet，并且你需要以管理员身份运行提升的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="60482-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="60482-272">几个模块返回了错误，这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="60482-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="60482-273">如果计算机无法访问 Internet，则可以在另一台可以访问互联网的机器上使用 `Save-Help` cmdlet，首先将更新后的帮助信息保存到网络上的文件共享中，然后使用 `Update-Help` 的 SourcePath 参数为帮助主题指定此网络位置。</span><span class="sxs-lookup"><span data-stu-id="60482-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="60482-274">考虑在 PowerShell 中设置计划任务或向配置文件脚本添加一些逻辑，以定期更新计算机上的帮助内容。</span><span class="sxs-lookup"><span data-stu-id="60482-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="60482-275">下一章将介绍配置文件脚本。</span><span class="sxs-lookup"><span data-stu-id="60482-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="60482-276">总结</span><span class="sxs-lookup"><span data-stu-id="60482-276">Summary</span></span>

<span data-ttu-id="60482-277">在本章中，你了解了如何使用 `Get-Help` 和 `Get-Command` 来查找命令。</span><span class="sxs-lookup"><span data-stu-id="60482-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="60482-278">你了解了如何使用帮助系统来搞清楚在找到命令后如何使用这些命令。</span><span class="sxs-lookup"><span data-stu-id="60482-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="60482-279">你还了解了有可用更新时如何更新帮助主题的内容。</span><span class="sxs-lookup"><span data-stu-id="60482-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="60482-280">我对你的要求是每天学习一个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="60482-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="60482-281">审阅</span><span class="sxs-lookup"><span data-stu-id="60482-281">Review</span></span>

1. <span data-ttu-id="60482-282">`Get-Service` 的 DisplayName 参数是否是按位置使用的参数？</span><span class="sxs-lookup"><span data-stu-id="60482-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="60482-283">`Get-Process` cmdlet 有多少个参数集？</span><span class="sxs-lookup"><span data-stu-id="60482-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="60482-284">存在哪些用于处理事件日志的 PowerShell 命令？</span><span class="sxs-lookup"><span data-stu-id="60482-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="60482-285">哪个 PowerShell 命令可以返回计算机上运行的 PowerShell 进程的列表？</span><span class="sxs-lookup"><span data-stu-id="60482-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="60482-286">如何更新存储在计算机上的 PowerShell 帮助内容？</span><span class="sxs-lookup"><span data-stu-id="60482-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="60482-287">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="60482-287">Recommended Reading</span></span>

<span data-ttu-id="60482-288">如果想详细了解本章介绍的主题，建议阅读以下 PowerShell 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="60482-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="60482-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="60482-289">[Get-Help][]</span></span>
- <span data-ttu-id="60482-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="60482-290">[Get-Command][]</span></span>
- <span data-ttu-id="60482-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="60482-291">[Update-Help][]</span></span>
- <span data-ttu-id="60482-292">[Save-Help][]</span><span class="sxs-lookup"><span data-stu-id="60482-292">[Save-Help][]</span></span>
- <span data-ttu-id="60482-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="60482-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="60482-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="60482-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="60482-295">在下一章中，你将了解 `Get-Member` cmdlet 以及对象、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="60482-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[附录 A]: appendix-a.md
[Appendix A]: appendix-a.md
