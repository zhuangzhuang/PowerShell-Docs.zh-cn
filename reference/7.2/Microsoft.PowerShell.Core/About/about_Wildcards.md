---
description: 介绍如何在 PowerShell 中使用通配符。
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595404"
---
# <a name="about-wildcards"></a><span data-ttu-id="2ea8f-103">关于通配符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="2ea8f-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="2ea8f-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2ea8f-105">介绍如何在 PowerShell 中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ea8f-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="2ea8f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2ea8f-107">通配符表示一个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="2ea8f-108">您可以使用它们在命令中创建 word 模式。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="2ea8f-109">例如，若要获取文件扩展名为的目录中的所有文件 `C:\Techdocs` `.ppt` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="2ea8f-109">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="2ea8f-110">在这种情况下，星号 (`*`) 通配符表示在文件扩展名之前出现的任何字符 `.ppt` 。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-110">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="2ea8f-111">PowerShell 支持以下通配符：</span><span class="sxs-lookup"><span data-stu-id="2ea8f-111">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="2ea8f-112">通配符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-112">Wildcard</span></span>|<span data-ttu-id="2ea8f-113">说明</span><span class="sxs-lookup"><span data-stu-id="2ea8f-113">Description</span></span>               |<span data-ttu-id="2ea8f-114">示例</span><span class="sxs-lookup"><span data-stu-id="2ea8f-114">Example</span></span> |<span data-ttu-id="2ea8f-115">匹配</span><span class="sxs-lookup"><span data-stu-id="2ea8f-115">Match</span></span>        |<span data-ttu-id="2ea8f-116">无匹配项</span><span class="sxs-lookup"><span data-stu-id="2ea8f-116">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="2ea8f-117">匹配零个或多个字符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-117">Match zero or more characters</span></span> | <span data-ttu-id="2ea8f-118">的\*</span><span class="sxs-lookup"><span data-stu-id="2ea8f-118">a\*</span></span>  | <span data-ttu-id="2ea8f-119">aA、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="2ea8f-119">aA, ag, Apple</span></span> | <span data-ttu-id="2ea8f-120">香蕉</span><span class="sxs-lookup"><span data-stu-id="2ea8f-120">banana</span></span> |
|<span data-ttu-id="2ea8f-121">?</span><span class="sxs-lookup"><span data-stu-id="2ea8f-121">?</span></span>       |<span data-ttu-id="2ea8f-122">匹配该位置中的一个字符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-122">Match one character in that position</span></span> | <span data-ttu-id="2ea8f-123">？ n</span><span class="sxs-lookup"><span data-stu-id="2ea8f-123">?n</span></span> | <span data-ttu-id="2ea8f-124">，在中，在</span><span class="sxs-lookup"><span data-stu-id="2ea8f-124">an, in, on</span></span> | <span data-ttu-id="2ea8f-125">为名</span><span class="sxs-lookup"><span data-stu-id="2ea8f-125">ran</span></span> |
|<span data-ttu-id="2ea8f-126">\[ \]</span><span class="sxs-lookup"><span data-stu-id="2ea8f-126">\[ \]</span></span>   |<span data-ttu-id="2ea8f-127">匹配一系列字符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-127">Match a range of characters</span></span> | <span data-ttu-id="2ea8f-128">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="2ea8f-128">\[a-l\]ook</span></span> | <span data-ttu-id="2ea8f-129">书籍，库，查找</span><span class="sxs-lookup"><span data-stu-id="2ea8f-129">book, cook, look</span></span> | <span data-ttu-id="2ea8f-130">需要</span><span class="sxs-lookup"><span data-stu-id="2ea8f-130">took</span></span> |
|<span data-ttu-id="2ea8f-131">\[ \]</span><span class="sxs-lookup"><span data-stu-id="2ea8f-131">\[ \]</span></span>   |<span data-ttu-id="2ea8f-132">匹配特定字符</span><span class="sxs-lookup"><span data-stu-id="2ea8f-132">Match specific characters</span></span> | <span data-ttu-id="2ea8f-133">\[bc \] ook</span><span class="sxs-lookup"><span data-stu-id="2ea8f-133">\[bc\]ook</span></span> | <span data-ttu-id="2ea8f-134">书籍，库</span><span class="sxs-lookup"><span data-stu-id="2ea8f-134">book, cook</span></span> | <span data-ttu-id="2ea8f-135">自已</span><span class="sxs-lookup"><span data-stu-id="2ea8f-135">hook</span></span> |

<span data-ttu-id="2ea8f-136">可以在同一单词模式中包含多个通配符字符。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-136">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="2ea8f-137">例如，若要查找名称以字母 **a** 到 **l** 开头的文本文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="2ea8f-137">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="2ea8f-138">许多 cmdlet 接受参数值中的通配符。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-138">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="2ea8f-139">每个 cmdlet 的帮助主题描述了哪些参数接受通配符。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-139">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="2ea8f-140">对于接受通配符的参数，其使用不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-140">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="2ea8f-141">可以在命令和脚本块中使用通配符，例如，创建表示属性值的单词模式。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-141">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="2ea8f-142">例如，以下命令将获取 **ServiceType** 属性值包括 **Interactive** 的服务。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-142">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="2ea8f-143">在下面的示例中， `If` 语句包含使用通配符查找属性值的条件。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-143">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="2ea8f-144">如果还原点的 **描述** 包含 **PowerShell**，则该命令会将还原点的 **CreationTime** 属性的值添加到日志文件。</span><span class="sxs-lookup"><span data-stu-id="2ea8f-144">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="2ea8f-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ea8f-145">SEE ALSO</span></span>

[<span data-ttu-id="2ea8f-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="2ea8f-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="2ea8f-147">about_If</span><span class="sxs-lookup"><span data-stu-id="2ea8f-147">about_If</span></span>](about_If.md)

[<span data-ttu-id="2ea8f-148">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="2ea8f-148">about_Script_Blocks</span></span>](about_Script_Blocks.md)

