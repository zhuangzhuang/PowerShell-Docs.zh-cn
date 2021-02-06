---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 82721b3d079c795e0ce6fcae1fba0eab93344b52
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597244"
---
# <span data-ttu-id="785c0-102">Get-Help</span><span class="sxs-lookup"><span data-stu-id="785c0-102">Get-Help</span></span>

## <span data-ttu-id="785c0-103">摘要</span><span class="sxs-lookup"><span data-stu-id="785c0-103">SYNOPSIS</span></span>
<span data-ttu-id="785c0-104">显示有关 PowerShell 命令和概念的信息。</span><span class="sxs-lookup"><span data-stu-id="785c0-104">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="785c0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="785c0-105">SYNTAX</span></span>

### <span data-ttu-id="785c0-106">AllUsersView（默认值）</span><span class="sxs-lookup"><span data-stu-id="785c0-106">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="785c0-107">DetailedView</span><span class="sxs-lookup"><span data-stu-id="785c0-107">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="785c0-108">示例</span><span class="sxs-lookup"><span data-stu-id="785c0-108">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="785c0-109">parameters</span><span class="sxs-lookup"><span data-stu-id="785c0-109">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="785c0-110">联机</span><span class="sxs-lookup"><span data-stu-id="785c0-110">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="785c0-111">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="785c0-111">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="785c0-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="785c0-112">DESCRIPTION</span></span>

<span data-ttu-id="785c0-113">`Get-Help`Cmdlet 显示有关 PowerShell 概念和命令（包括 cmdlet、函数、通用信息模型 (CIM) 命令、工作流、提供程序、别名和脚本）的信息。</span><span class="sxs-lookup"><span data-stu-id="785c0-113">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="785c0-114">若要获取 PowerShell cmdlet 的帮助，请键入 `Get-Help` 后跟 cmdlet 名称，如： `Get-Help Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-114">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="785c0-115">PowerShell 中的概念性帮助文章从 **about_** 开始，如 **about_Comparison_Operators**。</span><span class="sxs-lookup"><span data-stu-id="785c0-115">Conceptual help articles in PowerShell begin with **about_**, such as **about_Comparison_Operators**.</span></span> <span data-ttu-id="785c0-116">若要查看所有 **about_** 项目，请键入 `Get-Help about_*` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-116">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="785c0-117">若要查看特定项目，请键入 `Get-Help about_<article-name>` ，例如 `Get-Help about_Comparison_Operators` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-117">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="785c0-118">若要获取 PowerShell 提供程序的帮助，请键入， `Get-Help` 后跟提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="785c0-118">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="785c0-119">例如，若要获取有关证书提供程序的帮助，请键入 `Get-Help Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-119">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="785c0-120">您还可以键入 `help` 或 `man` ，这将一次显示一屏文本。</span><span class="sxs-lookup"><span data-stu-id="785c0-120">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="785c0-121">或， `<cmdlet-name> -?` 这等同于 `Get-Help` ，但仅适用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="785c0-121">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="785c0-122">`Get-Help` 从计算机上的帮助文件中获取它显示的帮助内容。</span><span class="sxs-lookup"><span data-stu-id="785c0-122">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="785c0-123">如果没有帮助文件， `Get-Help` 只显示有关 cmdlet 的基本信息。</span><span class="sxs-lookup"><span data-stu-id="785c0-123">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="785c0-124">某些 PowerShell 模块包括帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-124">Some PowerShell modules include help files.</span></span> <span data-ttu-id="785c0-125">从 PowerShell 3.0 开始，Windows 操作系统附带的模块不包含帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-125">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="785c0-126">若要下载或更新 PowerShell 3.0 中某个模块的帮助文件，请使用 `Update-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="785c0-126">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="785c0-127">你还可以在 Microsoft Docs 中联机查看 PowerShell 帮助文档。若要获取帮助文件的联机版本，请使用 **online** 参数，例如： `Get-Help Get-Process -Online` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-127">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="785c0-128">若要阅读所有 PowerShell 文档，请参阅 Microsoft Docs [Powershell 文档](/powershell)。</span><span class="sxs-lookup"><span data-stu-id="785c0-128">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="785c0-129">如果键入的 `Get-Help` 名称后跟帮助文章的确切名称，或按帮助文章的唯一名称键入 `Get-Help` 内容，将显示该文章的内容。</span><span class="sxs-lookup"><span data-stu-id="785c0-129">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="785c0-130">如果指定命令别名的确切名称，则会 `Get-Help` 显示原始命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-130">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="785c0-131">如果输入在多个帮助文章标题中出现的单词或单词模式， `Get-Help` 则将显示匹配标题的列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-131">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="785c0-132">如果输入未出现在任何帮助文章标题中的任何文本， `Get-Help` 将显示项目列表，其中包含其内容中的文本。</span><span class="sxs-lookup"><span data-stu-id="785c0-132">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="785c0-133">`Get-Help` 可以获取所有支持的语言和区域设置的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="785c0-133">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="785c0-134">`Get-Help` 首先在设置为 Windows 的区域设置中查找帮助文件，然后在父区域设置中查找， **例如 pt** **-BR**，然后在备用区域中。</span><span class="sxs-lookup"><span data-stu-id="785c0-134">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR**, and then in a fallback locale.</span></span> <span data-ttu-id="785c0-135">从 PowerShell 3.0 开始，如果在 `Get-Help` 回退区域设置中找不到帮助，它将在返回错误消息或显示自动生成的帮助之前，查找英语、 **en-us** 中的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="785c0-135">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US**, before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="785c0-136">有关 `Get-Help` 命令语法关系图中显示的符号的信息，请参阅 [about_Command_Syntax](./About/about_Command_Syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-136">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="785c0-137">有关参数属性（例如 **Required** 和 **Position**）的信息，请参阅 [about_Parameters](./About/about_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-137">For information about parameter attributes, such as **Required** and **Position**, see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="785c0-138">在 PowerShell 3.0 和 PowerShell 4.0 中， `Get-Help` 除非将模块导入到当前会话中，否则无法在模块中找到 **相关** 项目。</span><span class="sxs-lookup"><span data-stu-id="785c0-138">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="785c0-139">这是一个已知问题。</span><span class="sxs-lookup"><span data-stu-id="785c0-139">This is a known issue.</span></span> <span data-ttu-id="785c0-140">若要 **获取模块** 中的项目，请使用 `Import-Module` cmdlet 或通过运行模块中包含的 cmdlet 来导入模块。</span><span class="sxs-lookup"><span data-stu-id="785c0-140">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="785c0-141">示例</span><span class="sxs-lookup"><span data-stu-id="785c0-141">EXAMPLES</span></span>

### <span data-ttu-id="785c0-142">示例1：显示有关 cmdlet 的基本帮助信息</span><span class="sxs-lookup"><span data-stu-id="785c0-142">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="785c0-143">这些示例显示有关 cmdlet 的基本帮助信息 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-143">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="785c0-144">`Get-Help <cmdlet-name>` 是 cmdlet 的最简单和默认的语法 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-144">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="785c0-145">您可以省略 **Name** 参数。</span><span class="sxs-lookup"><span data-stu-id="785c0-145">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="785c0-146">语法 `<cmdlet-name> -?` 仅适用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="785c0-146">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="785c0-147">示例2：每次显示一页的基本信息</span><span class="sxs-lookup"><span data-stu-id="785c0-147">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="785c0-148">这些示例每次显示有关 cmdlet 的基本帮助信息 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-148">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="785c0-149">`help` 是在 `Get-Help` 内部运行 cmdlet 并每次显示一页结果的函数。</span><span class="sxs-lookup"><span data-stu-id="785c0-149">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="785c0-150">`man` 是函数的别名 `help` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-150">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="785c0-151">`Get-Help Format-Table` 沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="785c0-151">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="785c0-152">`Out-Host -Paging` 接收管道的输出，一次显示一个页面。</span><span class="sxs-lookup"><span data-stu-id="785c0-152">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="785c0-153">有关详细信息，请参阅 [托管主机](Out-Host.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-153">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="785c0-154">示例3：显示 cmdlet 的详细信息</span><span class="sxs-lookup"><span data-stu-id="785c0-154">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="785c0-155">这些示例显示有关 cmdlet 的更详细的帮助信息 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-155">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="785c0-156">**详细** 参数显示了帮助文章的详细视图，其中包括参数说明和示例。</span><span class="sxs-lookup"><span data-stu-id="785c0-156">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="785c0-157">**Full** 参数显示帮助文章的完整视图，其中包括参数说明、示例、输入和输出对象类型以及其他说明。</span><span class="sxs-lookup"><span data-stu-id="785c0-157">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="785c0-158">对于在计算机上安装了帮助文件的命令， **详细** 参数和 **完整** 参数仅有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-158">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="785c0-159">这些参数对于概念 (**about_**) 帮助文章不起作用。</span><span class="sxs-lookup"><span data-stu-id="785c0-159">The parameters aren't effective for the conceptual (**about_**) help articles.</span></span>

### <span data-ttu-id="785c0-160">示例4：使用参数显示 cmdlet 的选定部分</span><span class="sxs-lookup"><span data-stu-id="785c0-160">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="785c0-161">这些示例显示了 cmdlet 帮助的选定部分 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-161">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="785c0-162">**示例** 参数显示帮助文件的 **名称** 和 **摘要** 部分以及所有示例。</span><span class="sxs-lookup"><span data-stu-id="785c0-162">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="785c0-163">无法指定示例编号，因为 **示例** 参数是一个开关参数。</span><span class="sxs-lookup"><span data-stu-id="785c0-163">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="785c0-164">**Parameter** 参数只显示指定参数的描述。</span><span class="sxs-lookup"><span data-stu-id="785c0-164">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="785c0-165">如果仅指定星号 (`*`) 通配符，则它将显示所有参数的描述。</span><span class="sxs-lookup"><span data-stu-id="785c0-165">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="785c0-166">当 **参数** 指定参数名称（如 **GroupBy**）时，将显示有关该参数的信息。</span><span class="sxs-lookup"><span data-stu-id="785c0-166">When **Parameter** specifies a parameter name such as **GroupBy**, information about that parameter is shown.</span></span>

<span data-ttu-id="785c0-167">这些参数对于概念 (**about_**) 帮助文章无效。</span><span class="sxs-lookup"><span data-stu-id="785c0-167">These parameters aren't effective for the conceptual (**about_**) help articles.</span></span>

### <span data-ttu-id="785c0-168">示例5：显示帮助的联机版本</span><span class="sxs-lookup"><span data-stu-id="785c0-168">Example 5: Display online version of help</span></span>

<span data-ttu-id="785c0-169">此示例将 `Format-Table` 在默认 web 浏览器中显示该 cmdlet 的帮助文章的联机版本。</span><span class="sxs-lookup"><span data-stu-id="785c0-169">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="785c0-170">示例6：显示有关帮助系统的帮助</span><span class="sxs-lookup"><span data-stu-id="785c0-170">Example 6: Display help about the help system</span></span>

<span data-ttu-id="785c0-171">`Get-Help`不带参数的 cmdlet 显示有关 PowerShell 帮助系统的信息。</span><span class="sxs-lookup"><span data-stu-id="785c0-171">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="785c0-172">示例7：显示可用的帮助文章</span><span class="sxs-lookup"><span data-stu-id="785c0-172">Example 7: Display available help articles</span></span>

<span data-ttu-id="785c0-173">此示例显示了计算机上可用的所有帮助文章的列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-173">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="785c0-174">示例8：显示概念项目的列表</span><span class="sxs-lookup"><span data-stu-id="785c0-174">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="785c0-175">此示例显示 PowerShell 帮助中包含的概念文章的列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-175">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="785c0-176">所有这些文章都以 **about_** 的字符开头。</span><span class="sxs-lookup"><span data-stu-id="785c0-176">All these articles begin with the characters **about_**.</span></span> <span data-ttu-id="785c0-177">若要显示特定的帮助文件，请键入 `Get-Help \<about_article-name\>` ，例如 `Get-Help about_Signing` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-177">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="785c0-178">仅显示在计算机上安装了帮助文件的概念文章。</span><span class="sxs-lookup"><span data-stu-id="785c0-178">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="785c0-179">有关在 PowerShell 3.0 中下载和安装帮助文件的信息，请参阅 [Update-help](Update-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-179">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="785c0-180">示例9：在 cmdlet 帮助中搜索字词</span><span class="sxs-lookup"><span data-stu-id="785c0-180">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="785c0-181">此示例演示如何搜索 cmdlet 帮助文章中的单词。</span><span class="sxs-lookup"><span data-stu-id="785c0-181">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="785c0-182">`Get-Help` 使用 **Full** 参数获取的帮助信息 `Add-Member` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-182">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="785c0-183">**MamlCommandHelpInfo** 对象沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="785c0-183">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="785c0-184">`Out-String` 使用 **Stream** 参数将对象转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="785c0-184">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="785c0-185">`Select-String` 使用 **Pattern** 参数在字符串中搜索 **export-clixml**。</span><span class="sxs-lookup"><span data-stu-id="785c0-185">`Select-String` uses the **Pattern** parameter to search the string for **Clixml**.</span></span>

### <span data-ttu-id="785c0-186">示例10：显示包含单词的项目列表</span><span class="sxs-lookup"><span data-stu-id="785c0-186">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="785c0-187">此示例显示包含 word **远程处理** 的项目列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-187">This example displays a list of articles that include the word **remoting**.</span></span>

<span data-ttu-id="785c0-188">输入未出现在任何文章标题中的单词时，会 `Get-Help` 显示包含该单词的项目列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-188">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="785c0-189">示例11：显示特定于提供程序的帮助</span><span class="sxs-lookup"><span data-stu-id="785c0-189">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="785c0-190">此示例演示了获取特定于提供程序的帮助的两种方法 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-190">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="785c0-191">这些命令将获取有关如何 `Get-Item` 在 PowerShell SQL Server 提供程序的 **DataCollection** 节点中使用 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-191">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="785c0-192">第一个示例使用 `Get-Help` **Path** 参数来指定 SQL Server 提供程序的路径。</span><span class="sxs-lookup"><span data-stu-id="785c0-192">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="785c0-193">由于指定了提供程序的路径，因此可以从任何路径位置运行该命令。</span><span class="sxs-lookup"><span data-stu-id="785c0-193">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="785c0-194">第二个示例使用 `Set-Location` 导航到 SQL Server 提供程序的路径。</span><span class="sxs-lookup"><span data-stu-id="785c0-194">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="785c0-195">在该位置，无需 **路径** 参数 `Get-Help` 即可获取特定于提供程序的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-195">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="785c0-196">示例12：显示脚本的帮助</span><span class="sxs-lookup"><span data-stu-id="785c0-196">Example 12: Display help for a script</span></span>

<span data-ttu-id="785c0-197">此示例获取有关的帮助 `MyScript.ps1 script` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-197">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="785c0-198">有关如何为函数和脚本编写帮助的信息，请参阅 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-198">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="785c0-199">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="785c0-199">PARAMETERS</span></span>

### <span data-ttu-id="785c0-200">-Category</span><span class="sxs-lookup"><span data-stu-id="785c0-200">-Category</span></span>

<span data-ttu-id="785c0-201">只显示指定类别及其别名中的项的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-201">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="785c0-202">" **帮助** " 类别中有概念文章。</span><span class="sxs-lookup"><span data-stu-id="785c0-202">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="785c0-203">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="785c0-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="785c0-204">Alias</span><span class="sxs-lookup"><span data-stu-id="785c0-204">Alias</span></span>
- <span data-ttu-id="785c0-205">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="785c0-205">Cmdlet</span></span>
- <span data-ttu-id="785c0-206">提供程序</span><span class="sxs-lookup"><span data-stu-id="785c0-206">Provider</span></span>
- <span data-ttu-id="785c0-207">常规</span><span class="sxs-lookup"><span data-stu-id="785c0-207">General</span></span>
- <span data-ttu-id="785c0-208">常见问题解答</span><span class="sxs-lookup"><span data-stu-id="785c0-208">FAQ</span></span>
- <span data-ttu-id="785c0-209">术语表</span><span class="sxs-lookup"><span data-stu-id="785c0-209">Glossary</span></span>
- <span data-ttu-id="785c0-210">HelpFile</span><span class="sxs-lookup"><span data-stu-id="785c0-210">HelpFile</span></span>
- <span data-ttu-id="785c0-211">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="785c0-211">ScriptCommand</span></span>
- <span data-ttu-id="785c0-212">函数</span><span class="sxs-lookup"><span data-stu-id="785c0-212">Function</span></span>
- <span data-ttu-id="785c0-213">筛选器</span><span class="sxs-lookup"><span data-stu-id="785c0-213">Filter</span></span>
- <span data-ttu-id="785c0-214">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="785c0-214">ExternalScript</span></span>
- <span data-ttu-id="785c0-215">全部</span><span class="sxs-lookup"><span data-stu-id="785c0-215">All</span></span>
- <span data-ttu-id="785c0-216">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="785c0-216">DefaultHelp</span></span>
- <span data-ttu-id="785c0-217">工作流</span><span class="sxs-lookup"><span data-stu-id="785c0-217">Workflow</span></span>
- <span data-ttu-id="785c0-218">DscResource</span><span class="sxs-lookup"><span data-stu-id="785c0-218">DscResource</span></span>
- <span data-ttu-id="785c0-219">实例</span><span class="sxs-lookup"><span data-stu-id="785c0-219">Class</span></span>
- <span data-ttu-id="785c0-220">Configuration</span><span class="sxs-lookup"><span data-stu-id="785c0-220">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-221">-Component</span><span class="sxs-lookup"><span data-stu-id="785c0-221">-Component</span></span>

<span data-ttu-id="785c0-222">显示具有指定组件值（如 **Exchange**）的命令。</span><span class="sxs-lookup"><span data-stu-id="785c0-222">Displays commands with the specified component value, such as **Exchange**.</span></span> <span data-ttu-id="785c0-223">输入组件名称。</span><span class="sxs-lookup"><span data-stu-id="785c0-223">Enter a component name.</span></span>
<span data-ttu-id="785c0-224">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="785c0-224">Wildcard characters are permitted.</span></span> <span data-ttu-id="785c0-225">此参数对概念 (**About_**) 帮助的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="785c0-225">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-226">-Detailed</span><span class="sxs-lookup"><span data-stu-id="785c0-226">-Detailed</span></span>

<span data-ttu-id="785c0-227">将参数说明和示例添加到基本帮助显示。</span><span class="sxs-lookup"><span data-stu-id="785c0-227">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="785c0-228">仅当计算机上安装了帮助文件时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-228">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="785c0-229">它不会影响概念性 (**About_**) 帮助的显示。</span><span class="sxs-lookup"><span data-stu-id="785c0-229">It has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-230">-Examples</span><span class="sxs-lookup"><span data-stu-id="785c0-230">-Examples</span></span>

<span data-ttu-id="785c0-231">只显示名称、摘要和示例。</span><span class="sxs-lookup"><span data-stu-id="785c0-231">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="785c0-232">若要仅显示示例，请键入 `(Get-Help \<cmdlet-name\>).Examples` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-232">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="785c0-233">仅当计算机上安装了帮助文件时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-233">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="785c0-234">它不会影响概念性 (**About_**) 帮助的显示。</span><span class="sxs-lookup"><span data-stu-id="785c0-234">It has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-235">-Full</span><span class="sxs-lookup"><span data-stu-id="785c0-235">-Full</span></span>

<span data-ttu-id="785c0-236">显示 cmdlet 的整个帮助文章。</span><span class="sxs-lookup"><span data-stu-id="785c0-236">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="785c0-237">**Full** 包含参数说明和属性、示例、输入和输出对象类型以及其他说明。</span><span class="sxs-lookup"><span data-stu-id="785c0-237">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="785c0-238">仅当计算机上安装了帮助文件时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-238">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="785c0-239">它不会影响概念性 (**About_**) 帮助的显示。</span><span class="sxs-lookup"><span data-stu-id="785c0-239">It has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-240">-Functionality</span><span class="sxs-lookup"><span data-stu-id="785c0-240">-Functionality</span></span>

<span data-ttu-id="785c0-241">显示具有指定功能的项的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-241">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="785c0-242">输入功能。</span><span class="sxs-lookup"><span data-stu-id="785c0-242">Enter the functionality.</span></span> <span data-ttu-id="785c0-243">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="785c0-243">Wildcard characters are permitted.</span></span> <span data-ttu-id="785c0-244">此参数对概念 (**About_**) 帮助的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="785c0-244">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-245">-Name</span><span class="sxs-lookup"><span data-stu-id="785c0-245">-Name</span></span>

<span data-ttu-id="785c0-246">获取有关指定命令或概念的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-246">Gets help about the specified command or concept.</span></span> <span data-ttu-id="785c0-247">输入 cmdlet、函数、提供程序、脚本或工作流的名称，如 `Get-Member` 概念项目名称（如 `about_Objects` ）或别名（例如） `ls` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-247">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="785c0-248">允许在 cmdlet 和提供程序名称中使用通配符，但不能使用通配符来查找函数帮助和脚本帮助文章的名称。</span><span class="sxs-lookup"><span data-stu-id="785c0-248">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="785c0-249">若要获取不在环境变量中列出的路径中的脚本的帮助 `$env:Path` ，请键入该脚本的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="785c0-249">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="785c0-250">如果输入了帮助文章的确切名称，则会 `Get-Help` 显示项目内容。</span><span class="sxs-lookup"><span data-stu-id="785c0-250">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="785c0-251">如果输入在多个帮助文章标题中出现的单词或单词模式， `Get-Help` 则将显示匹配标题的列表。</span><span class="sxs-lookup"><span data-stu-id="785c0-251">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="785c0-252">如果输入的任何文本与任何帮助文章标题都不匹配，则会 `Get-Help` 显示项目列表，其中包含其内容中的文本。</span><span class="sxs-lookup"><span data-stu-id="785c0-252">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="785c0-253">概念文章的名称（例如 `about_Objects` ）必须以英语输入，即使在非英语版本的 PowerShell 中也是如此。</span><span class="sxs-lookup"><span data-stu-id="785c0-253">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-254">-Online</span><span class="sxs-lookup"><span data-stu-id="785c0-254">-Online</span></span>

<span data-ttu-id="785c0-255">在默认浏览器中显示帮助文章的联机版本。</span><span class="sxs-lookup"><span data-stu-id="785c0-255">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="785c0-256">此参数仅对 cmdlet、函数、工作流和脚本帮助文章有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-256">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="785c0-257">不能 `Get-Help` 在远程会话中将 Online 参数与一起使用。</span><span class="sxs-lookup"><span data-stu-id="785c0-257">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="785c0-258">有关在你编写的帮助文章中支持此功能的信息，请参阅 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)和 [支持联机帮助](/powershell/scripting/developer/module/supporting-online-help)以及 [为 PowerShell cmdlet 编写帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="785c0-258">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-259">-Parameter</span><span class="sxs-lookup"><span data-stu-id="785c0-259">-Parameter</span></span>

<span data-ttu-id="785c0-260">只显示指定参数的详细说明。</span><span class="sxs-lookup"><span data-stu-id="785c0-260">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="785c0-261">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="785c0-261">Wildcards are permitted.</span></span> <span data-ttu-id="785c0-262">此参数对概念 (**About_**) 帮助的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="785c0-262">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-263">-Path</span><span class="sxs-lookup"><span data-stu-id="785c0-263">-Path</span></span>

<span data-ttu-id="785c0-264">获取说明 cmdlet 在指定的提供程序路径中的工作方式的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-264">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="785c0-265">输入 PowerShell 提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="785c0-265">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="785c0-266">此参数获取自定义版本的 cmdlet 帮助文章，其中介绍了 cmdlet 在指定的 PowerShell 提供程序路径中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="785c0-266">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="785c0-267">此参数仅对有关提供程序 cmdlet 的帮助有效，并且仅当提供程序在其帮助文件中包含提供程序 cmdlet 帮助项目的自定义版本时才有效。</span><span class="sxs-lookup"><span data-stu-id="785c0-267">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="785c0-268">若要使用此参数，请安装包含该提供程序的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-268">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="785c0-269">若要查看提供程序路径的自定义 cmdlet 帮助，请访问提供程序路径位置并输入 `Get-Help` 命令，或从任意路径位置使用 **path** 参数 `Get-Help` 来指定提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="785c0-269">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="785c0-270">你还可以在 "帮助" 文章的 "提供程序帮助" 部分中找到 "自定义 cmdlet 帮助"。</span><span class="sxs-lookup"><span data-stu-id="785c0-270">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="785c0-271">有关 PowerShell 提供程序的详细信息，请参阅 [about_Providers](./About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="785c0-271">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-272">-Role</span><span class="sxs-lookup"><span data-stu-id="785c0-272">-Role</span></span>

<span data-ttu-id="785c0-273">显示为指定的用户角色自定义的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-273">Displays help customized for the specified user role.</span></span> <span data-ttu-id="785c0-274">输入角色。</span><span class="sxs-lookup"><span data-stu-id="785c0-274">Enter a role.</span></span> <span data-ttu-id="785c0-275">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="785c0-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="785c0-276">输入用户在组织中所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="785c0-276">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="785c0-277">某些 cmdlet 将在其帮助文件中显示不同的文本，具体取决于此参数的值。</span><span class="sxs-lookup"><span data-stu-id="785c0-277">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="785c0-278">此参数对核心 cmdlet 的帮助不起作用。</span><span class="sxs-lookup"><span data-stu-id="785c0-278">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="785c0-279">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="785c0-279">-ShowWindow</span></span>

<span data-ttu-id="785c0-280">在窗口中显示帮助主题以便于阅读。</span><span class="sxs-lookup"><span data-stu-id="785c0-280">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="785c0-281">该窗口包括 " **查找** " 搜索功能和 " **设置** " 框，使用该功能可以设置显示的选项，包括只显示帮助主题的选定部分的选项。</span><span class="sxs-lookup"><span data-stu-id="785c0-281">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="785c0-282">**ShowWindow** 参数支持 (cmdlet、函数、CIM 命令、脚本) 的帮助主题以及 **有关** 项目的概念。</span><span class="sxs-lookup"><span data-stu-id="785c0-282">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="785c0-283">它不支持提供程序帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-283">It does not support provider help.</span></span>

<span data-ttu-id="785c0-284">此参数已被引入 PowerShell 7.0。</span><span class="sxs-lookup"><span data-stu-id="785c0-284">This parameter was reintroduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="785c0-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="785c0-285">CommonParameters</span></span>

<span data-ttu-id="785c0-286">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="785c0-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="785c0-287">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="785c0-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="785c0-288">输入</span><span class="sxs-lookup"><span data-stu-id="785c0-288">INPUTS</span></span>

### <span data-ttu-id="785c0-289">无</span><span class="sxs-lookup"><span data-stu-id="785c0-289">None</span></span>

<span data-ttu-id="785c0-290">不能将对象向下发送到 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="785c0-290">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="785c0-291">输出</span><span class="sxs-lookup"><span data-stu-id="785c0-291">OUTPUTS</span></span>

### <span data-ttu-id="785c0-292">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="785c0-292">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="785c0-293">如果在没有 `Get-Help` 帮助文件的命令上运行，则将 `Get-Help` 返回表示自动生成的帮助的 **ExtendedCmdletHelpInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="785c0-293">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="785c0-294">System.String</span><span class="sxs-lookup"><span data-stu-id="785c0-294">System.String</span></span>

<span data-ttu-id="785c0-295">如果你获取了概念性帮助文章，则 `Get-Help` 会将其作为字符串返回。</span><span class="sxs-lookup"><span data-stu-id="785c0-295">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="785c0-296">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="785c0-296">MamlCommandHelpInfo</span></span>

<span data-ttu-id="785c0-297">如果收到包含帮助文件的命令，则 `Get-Help` 返回 **MamlCommandHelpInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="785c0-297">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="785c0-298">注释</span><span class="sxs-lookup"><span data-stu-id="785c0-298">NOTES</span></span>

<span data-ttu-id="785c0-299">PowerShell 3.0 不包含帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-299">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="785c0-300">若要下载并安装读取的帮助文件 `Get-Help` ，请使用 `Update-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="785c0-300">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="785c0-301">可以使用 `Update-Help` cmdlet 下载和安装 PowerShell 附带的核心命令的帮助文件，以及安装的任何模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-301">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="785c0-302">还可以使用它来更新帮助文件，以使计算机上的帮助永不过时。</span><span class="sxs-lookup"><span data-stu-id="785c0-302">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="785c0-303">你还可以阅读有关 PowerShell online 附带的命令的帮助文章，从 [Windows PowerShell 入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)开始。</span><span class="sxs-lookup"><span data-stu-id="785c0-303">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="785c0-304">`Get-Help` 显示针对 Windows 操作系统的区域设置或该区域设置的回退语言中的帮助。</span><span class="sxs-lookup"><span data-stu-id="785c0-304">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="785c0-305">如果没有主区域设置或回退区域设置的帮助文件，则 `Get-Help` 的行为就好像计算机上没有帮助文件。</span><span class="sxs-lookup"><span data-stu-id="785c0-305">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="785c0-306">若要获取有关不同区域设置的帮助，请使用 "控制面板" 中的 " **区域** 和 **语言** " 来更改设置。</span><span class="sxs-lookup"><span data-stu-id="785c0-306">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="785c0-307">在 Windows 10 上， **设置**， **时间 & 语言**。</span><span class="sxs-lookup"><span data-stu-id="785c0-307">On Windows 10, **Settings**, **Time & Language**.</span></span>

<span data-ttu-id="785c0-308">帮助的完整视图包括有关参数的信息表。</span><span class="sxs-lookup"><span data-stu-id="785c0-308">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="785c0-309">该表包括以下字段：</span><span class="sxs-lookup"><span data-stu-id="785c0-309">The table includes the following fields:</span></span>

- <span data-ttu-id="785c0-310">“必需”。</span><span class="sxs-lookup"><span data-stu-id="785c0-310">**Required**.</span></span> <span data-ttu-id="785c0-311">指示参数是必需的 (true) 还是可选的 (false)。</span><span class="sxs-lookup"><span data-stu-id="785c0-311">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="785c0-312">**位置**。</span><span class="sxs-lookup"><span data-stu-id="785c0-312">**Position**.</span></span> <span data-ttu-id="785c0-313">指示参数是命名参数还是位置 (数值) 。</span><span class="sxs-lookup"><span data-stu-id="785c0-313">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="785c0-314">位置参数必须出现在命令中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="785c0-314">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="785c0-315">**命名** 指示参数名称是必需的，但参数可以出现在命令中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="785c0-315">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="785c0-316">**数值** 指示参数名称是可选的，但当省略名称时，该参数必须位于由该数字指定的位置。</span><span class="sxs-lookup"><span data-stu-id="785c0-316">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="785c0-317">例如， `2` 指示当省略参数名称时，该参数必须是命令中的第二个或唯一一个未命名的参数。</span><span class="sxs-lookup"><span data-stu-id="785c0-317">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="785c0-318">当使用了参数名称时，该参数可以出现在命令中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="785c0-318">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="785c0-319">**默认值**。</span><span class="sxs-lookup"><span data-stu-id="785c0-319">**Default value**.</span></span> <span data-ttu-id="785c0-320">如果未在命令中包含参数，则 PowerShell 使用的参数值或默认行为。</span><span class="sxs-lookup"><span data-stu-id="785c0-320">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="785c0-321">接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="785c0-321">Accepts pipeline input.</span></span> <span data-ttu-id="785c0-322">指示是否可以 (true) 或不能 (false) 通过管道将对象发送到参数。</span><span class="sxs-lookup"><span data-stu-id="785c0-322">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="785c0-323">**按属性名称** 表示，流水线对象必须具有与参数名称相同的属性。</span><span class="sxs-lookup"><span data-stu-id="785c0-323">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="785c0-324">**接受通配符**。</span><span class="sxs-lookup"><span data-stu-id="785c0-324">**Accepts wildcard characters**.</span></span> <span data-ttu-id="785c0-325">指示参数的值是否可以包括通配符，如星号 (`*`) 或问号 (`?`) 。</span><span class="sxs-lookup"><span data-stu-id="785c0-325">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="785c0-326">相关链接</span><span class="sxs-lookup"><span data-stu-id="785c0-326">RELATED LINKS</span></span>

[<span data-ttu-id="785c0-327">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="785c0-327">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="785c0-328">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="785c0-328">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="785c0-329">Get-Command</span><span class="sxs-lookup"><span data-stu-id="785c0-329">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="785c0-330">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="785c0-330">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="785c0-331">Update-Help</span><span class="sxs-lookup"><span data-stu-id="785c0-331">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="785c0-332">编写基于注释的帮助主题</span><span class="sxs-lookup"><span data-stu-id="785c0-332">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="785c0-333">编写针对 PowerShell Cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="785c0-333">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

