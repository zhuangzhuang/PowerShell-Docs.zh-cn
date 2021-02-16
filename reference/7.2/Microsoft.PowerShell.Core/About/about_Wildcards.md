---
description: 介绍如何在 PowerShell 中使用通配符。
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 40620e54bb889d683192b346f3ba1c139895e4d0
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529968"
---
# <a name="about-wildcards"></a><span data-ttu-id="4cf84-103">关于通配符</span><span class="sxs-lookup"><span data-stu-id="4cf84-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="4cf84-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="4cf84-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4cf84-105">介绍如何在 PowerShell 中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4cf84-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4cf84-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="4cf84-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="4cf84-107">通配符表示一个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="4cf84-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="4cf84-108">您可以使用它们在命令中创建 word 模式。</span><span class="sxs-lookup"><span data-stu-id="4cf84-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="4cf84-109">通配符表达式与 `-like` 运算符或任何接受通配符的参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="4cf84-109">Wildcard expressions are used with the `-like` operator or with any parameter that accepts wildcards.</span></span>

<span data-ttu-id="4cf84-110">例如，若要匹配 `C:\Techdocs` 目录中具有文件扩展名的所有文件 `.ppt` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="4cf84-110">For example, to match all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="4cf84-111">在这种情况下，星号 (`*`) 通配符表示在文件扩展名之前出现的任何字符 `.ppt` 。</span><span class="sxs-lookup"><span data-stu-id="4cf84-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="4cf84-112">通配符表达式比正则表达式简单。</span><span class="sxs-lookup"><span data-stu-id="4cf84-112">Wildcard expressions are simpler than regular expressions.</span></span> <span data-ttu-id="4cf84-113">有关详细信息，请参阅 [about_Regular_Expressions](./about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4cf84-113">For more information, see [about_Regular_Expressions](./about_Regular_Expressions.md).</span></span>

<span data-ttu-id="4cf84-114">PowerShell 支持以下通配符：</span><span class="sxs-lookup"><span data-stu-id="4cf84-114">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="4cf84-115">通配符</span><span class="sxs-lookup"><span data-stu-id="4cf84-115">Wildcard</span></span>|<span data-ttu-id="4cf84-116">描述</span><span class="sxs-lookup"><span data-stu-id="4cf84-116">Description</span></span>               |<span data-ttu-id="4cf84-117">示例</span><span class="sxs-lookup"><span data-stu-id="4cf84-117">Example</span></span> |<span data-ttu-id="4cf84-118">匹配</span><span class="sxs-lookup"><span data-stu-id="4cf84-118">Match</span></span>        |<span data-ttu-id="4cf84-119">无匹配项</span><span class="sxs-lookup"><span data-stu-id="4cf84-119">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="4cf84-120">匹配零个或多个字符</span><span class="sxs-lookup"><span data-stu-id="4cf84-120">Match zero or more characters</span></span> | <span data-ttu-id="4cf84-121">的\*</span><span class="sxs-lookup"><span data-stu-id="4cf84-121">a\*</span></span>  | <span data-ttu-id="4cf84-122">aA、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="4cf84-122">aA, ag, Apple</span></span> | <span data-ttu-id="4cf84-123">香蕉</span><span class="sxs-lookup"><span data-stu-id="4cf84-123">banana</span></span> |
|<span data-ttu-id="4cf84-124">?</span><span class="sxs-lookup"><span data-stu-id="4cf84-124">?</span></span>       |<span data-ttu-id="4cf84-125">匹配该位置中的一个字符</span><span class="sxs-lookup"><span data-stu-id="4cf84-125">Match one character in that position</span></span> | <span data-ttu-id="4cf84-126">？ n</span><span class="sxs-lookup"><span data-stu-id="4cf84-126">?n</span></span> | <span data-ttu-id="4cf84-127">，在中，在</span><span class="sxs-lookup"><span data-stu-id="4cf84-127">an, in, on</span></span> | <span data-ttu-id="4cf84-128">为名</span><span class="sxs-lookup"><span data-stu-id="4cf84-128">ran</span></span> |
|<span data-ttu-id="4cf84-129">\[ \]</span><span class="sxs-lookup"><span data-stu-id="4cf84-129">\[ \]</span></span>   |<span data-ttu-id="4cf84-130">匹配一系列字符</span><span class="sxs-lookup"><span data-stu-id="4cf84-130">Match a range of characters</span></span> | <span data-ttu-id="4cf84-131">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="4cf84-131">\[a-l\]ook</span></span> | <span data-ttu-id="4cf84-132">书籍，库，查找</span><span class="sxs-lookup"><span data-stu-id="4cf84-132">book, cook, look</span></span> | <span data-ttu-id="4cf84-133">需要</span><span class="sxs-lookup"><span data-stu-id="4cf84-133">took</span></span> |
|<span data-ttu-id="4cf84-134">\[ \]</span><span class="sxs-lookup"><span data-stu-id="4cf84-134">\[ \]</span></span>   |<span data-ttu-id="4cf84-135">匹配特定字符</span><span class="sxs-lookup"><span data-stu-id="4cf84-135">Match specific characters</span></span> | <span data-ttu-id="4cf84-136">\[bc \] ook</span><span class="sxs-lookup"><span data-stu-id="4cf84-136">\[bc\]ook</span></span> | <span data-ttu-id="4cf84-137">书籍，库</span><span class="sxs-lookup"><span data-stu-id="4cf84-137">book, cook</span></span> | <span data-ttu-id="4cf84-138">自已</span><span class="sxs-lookup"><span data-stu-id="4cf84-138">hook</span></span> |

<span data-ttu-id="4cf84-139">可以在同一单词模式中包含多个通配符字符。</span><span class="sxs-lookup"><span data-stu-id="4cf84-139">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="4cf84-140">例如，若要查找名称以字母 **a** 到 **l** 开头的文本文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="4cf84-140">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="4cf84-141">许多 cmdlet 接受参数值中的通配符。</span><span class="sxs-lookup"><span data-stu-id="4cf84-141">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="4cf84-142">每个 cmdlet 的帮助主题描述了哪些参数接受通配符。</span><span class="sxs-lookup"><span data-stu-id="4cf84-142">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="4cf84-143">对于接受通配符的参数，其使用不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="4cf84-143">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="4cf84-144">可以在命令和脚本块中使用通配符，例如，创建表示属性值的单词模式。</span><span class="sxs-lookup"><span data-stu-id="4cf84-144">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="4cf84-145">例如，以下命令将获取 **ServiceType** 属性值包括 **Interactive** 的服务。</span><span class="sxs-lookup"><span data-stu-id="4cf84-145">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="4cf84-146">在下面的示例中， `If` 语句包含使用通配符查找属性值的条件。</span><span class="sxs-lookup"><span data-stu-id="4cf84-146">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="4cf84-147">如果还原点的 **描述** 包含 **PowerShell**，则该命令会将还原点的 **CreationTime** 属性的值添加到日志文件。</span><span class="sxs-lookup"><span data-stu-id="4cf84-147">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4cf84-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cf84-148">SEE ALSO</span></span>

[<span data-ttu-id="4cf84-149">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="4cf84-149">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="4cf84-150">about_If</span><span class="sxs-lookup"><span data-stu-id="4cf84-150">about_If</span></span>](about_If.md)

[<span data-ttu-id="4cf84-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="4cf84-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)

