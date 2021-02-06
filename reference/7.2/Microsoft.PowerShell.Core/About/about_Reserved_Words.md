---
description: 列出不能用作标识符的保留字，因为它们在 PowerShell 中具有特殊含义。
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 95911e328a50c173235f47a7610393124781555d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603396"
---
# <a name="about-reserved-words"></a><span data-ttu-id="691d9-103">关于保留字</span><span class="sxs-lookup"><span data-stu-id="691d9-103">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="691d9-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="691d9-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="691d9-105">列出不能用作标识符的保留字，因为它们在 PowerShell 中具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="691d9-105">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="691d9-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="691d9-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="691d9-107">有些字词在 PowerShell 中具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="691d9-107">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="691d9-108">如果不使用引号显示这些字词，则 PowerShell 将尝试应用其特殊意义，而不是将其视为字符串。</span><span class="sxs-lookup"><span data-stu-id="691d9-108">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="691d9-109">若要在命令或脚本中使用这些字词作为参数参数，而不调用其特殊含义，请将保留字用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="691d9-109">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="691d9-110">下面是 PowerShell 中的保留字：</span><span class="sxs-lookup"><span data-stu-id="691d9-110">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="691d9-111">几个语言关键字（包括 `Foreach` 、、 `If` `For` 和 `While` ）都有其自己的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="691d9-111">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="691d9-112">若要查看它们，请键入 `Get-Help about_` 并添加关键字。</span><span class="sxs-lookup"><span data-stu-id="691d9-112">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="691d9-113">例如，若要获取有关该语句的信息 `Foreach` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="691d9-113">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="691d9-114">有关 `Filter` 语句或语句语法的信息 `Return` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="691d9-114">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="691d9-115">有关其他保留字的信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="691d9-115">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="691d9-116">并非每个保留字都有其自己的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="691d9-116">Not every reserved word has its own help article.</span></span> <span data-ttu-id="691d9-117">如果不 `Get-Help` 返回项目，则可以使用以下命令搜索与保留字相关的文章：</span><span class="sxs-lookup"><span data-stu-id="691d9-117">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="691d9-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="691d9-118">SEE ALSO</span></span>

- [<span data-ttu-id="691d9-119">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="691d9-119">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="691d9-120">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="691d9-120">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="691d9-121">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="691d9-121">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="691d9-122">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="691d9-122">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="691d9-123">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="691d9-123">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="691d9-124">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="691d9-124">about_Special_Characters</span></span>](about_Special_Characters.md)
