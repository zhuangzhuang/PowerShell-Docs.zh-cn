---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "99595808"
---
# <span data-ttu-id="598e1-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="598e1-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="598e1-103">摘要</span><span class="sxs-lookup"><span data-stu-id="598e1-103">SYNOPSIS</span></span>
<span data-ttu-id="598e1-104">从文件中导入值 `.PSD1` ，而不调用其内容。</span><span class="sxs-lookup"><span data-stu-id="598e1-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="598e1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="598e1-105">SYNTAX</span></span>

### <span data-ttu-id="598e1-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="598e1-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### <span data-ttu-id="598e1-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="598e1-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## <span data-ttu-id="598e1-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="598e1-108">DESCRIPTION</span></span>

<span data-ttu-id="598e1-109">`Import-PowerShellDataFile`Cmdlet 从文件中定义的哈希表中安全地导入键值对 `.PSD1` 。</span><span class="sxs-lookup"><span data-stu-id="598e1-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="598e1-110">可以使用文件内容导入这些值 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="598e1-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="598e1-111">但会 `Invoke-Expression` 运行文件中包含的任何代码。</span><span class="sxs-lookup"><span data-stu-id="598e1-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="598e1-112">这可能会产生不需要的结果或执行不安全的代码。</span><span class="sxs-lookup"><span data-stu-id="598e1-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="598e1-113">`Import-PowerShellDataFile` 导入数据而不调用代码。</span><span class="sxs-lookup"><span data-stu-id="598e1-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span> <span data-ttu-id="598e1-114">默认情况下，会出现500键限制，但 **SkipLimitCheck** 开关可能会绕过此限制。</span><span class="sxs-lookup"><span data-stu-id="598e1-114">By default there is a 500 key limit but can be bypassed with the **SkipLimitCheck** switch.</span></span>

## <span data-ttu-id="598e1-115">示例</span><span class="sxs-lookup"><span data-stu-id="598e1-115">EXAMPLES</span></span>

### <span data-ttu-id="598e1-116">示例1：从 PSD1 检索值</span><span class="sxs-lookup"><span data-stu-id="598e1-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="598e1-117">此示例检索存储在存储在文件中的哈希表中的键/值对 `Configuration.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="598e1-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="598e1-118">`Get-Content` 用于显示文件的内容 `Configuration.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="598e1-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="598e1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="598e1-119">PARAMETERS</span></span>

### <span data-ttu-id="598e1-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="598e1-120">-LiteralPath</span></span>

<span data-ttu-id="598e1-121">要导入的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="598e1-121">The path to the file being imported.</span></span> <span data-ttu-id="598e1-122">路径中的所有字符都被视为文本值。</span><span class="sxs-lookup"><span data-stu-id="598e1-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="598e1-123">不处理通配符。</span><span class="sxs-lookup"><span data-stu-id="598e1-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="598e1-124">-Path</span><span class="sxs-lookup"><span data-stu-id="598e1-124">-Path</span></span>

<span data-ttu-id="598e1-125">要导入的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="598e1-125">The path to the file being imported.</span></span> <span data-ttu-id="598e1-126">允许使用通配符，但只导入第一个匹配文件。</span><span class="sxs-lookup"><span data-stu-id="598e1-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="598e1-127">-SkipLimitCheck</span><span class="sxs-lookup"><span data-stu-id="598e1-127">-SkipLimitCheck</span></span>

<span data-ttu-id="598e1-128">默认情况下， `Import-PowerShellDataFile` 仅从文件中导入500键 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="598e1-128">By default `Import-PowerShellDataFile` imports only 500 keys from a `.psd1` file.</span></span> <span data-ttu-id="598e1-129">使用 **SkipLimitCheck** 导入超过500个键。</span><span class="sxs-lookup"><span data-stu-id="598e1-129">Use **SkipLimitCheck** to import more than 500 keys.</span></span>

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="598e1-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="598e1-130">CommonParameters</span></span>

<span data-ttu-id="598e1-131">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="598e1-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="598e1-132">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="598e1-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="598e1-133">输入</span><span class="sxs-lookup"><span data-stu-id="598e1-133">INPUTS</span></span>

## <span data-ttu-id="598e1-134">输出</span><span class="sxs-lookup"><span data-stu-id="598e1-134">OUTPUTS</span></span>

### <span data-ttu-id="598e1-135">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="598e1-135">System.Collections.Hashtable</span></span>

## <span data-ttu-id="598e1-136">注释</span><span class="sxs-lookup"><span data-stu-id="598e1-136">NOTES</span></span>

## <span data-ttu-id="598e1-137">相关链接</span><span class="sxs-lookup"><span data-stu-id="598e1-137">RELATED LINKS</span></span>

[<span data-ttu-id="598e1-138">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="598e1-138">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="598e1-139">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="598e1-139">Import-LocalizedData</span></span>](Import-LocalizedData.md)
