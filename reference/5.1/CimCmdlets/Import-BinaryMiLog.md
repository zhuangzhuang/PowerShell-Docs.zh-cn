---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: b31d12f06a8d2e8e226908db9663446baf09a124
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194255"
---
# <span data-ttu-id="ea040-102">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="ea040-102">Import-BinaryMiLog</span></span>

## <span data-ttu-id="ea040-103">摘要</span><span class="sxs-lookup"><span data-stu-id="ea040-103">SYNOPSIS</span></span>
<span data-ttu-id="ea040-104">用于根据导出文件的内容重新创建已保存的对象。</span><span class="sxs-lookup"><span data-stu-id="ea040-104">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="ea040-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea040-105">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="ea040-106">说明</span><span class="sxs-lookup"><span data-stu-id="ea040-106">DESCRIPTION</span></span>

<span data-ttu-id="ea040-107">使用此 cmdlet 可根据创建的导出文件的内容重新创建已保存的对象 `Export-BinaryMILog` 。</span><span class="sxs-lookup"><span data-stu-id="ea040-107">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="ea040-108">此 cmdlet 类似于 `Import-Clixml` ，不同之处在于将 `Export-BinaryMILog` 生成的对象存储在二进制编码的文件中。</span><span class="sxs-lookup"><span data-stu-id="ea040-108">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="ea040-109">示例</span><span class="sxs-lookup"><span data-stu-id="ea040-109">EXAMPLES</span></span>

### <span data-ttu-id="ea040-110">示例 1-还原导出到文件的对象</span><span class="sxs-lookup"><span data-stu-id="ea040-110">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="ea040-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea040-111">PARAMETERS</span></span>

### <span data-ttu-id="ea040-112">-Path</span><span class="sxs-lookup"><span data-stu-id="ea040-112">-Path</span></span>

<span data-ttu-id="ea040-113">指定要在其中存储对象的二进制表示形式的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ea040-113">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="ea040-114">**Path** 参数支持通配符和相对路径。</span><span class="sxs-lookup"><span data-stu-id="ea040-114">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="ea040-115">如果路径解析为多个文件，则此 cmdlet 将生成错误。</span><span class="sxs-lookup"><span data-stu-id="ea040-115">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ea040-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea040-116">CommonParameters</span></span>
<span data-ttu-id="ea040-117">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ea040-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea040-118">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ea040-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea040-119">输入</span><span class="sxs-lookup"><span data-stu-id="ea040-119">INPUTS</span></span>

### <span data-ttu-id="ea040-120">无</span><span class="sxs-lookup"><span data-stu-id="ea040-120">None</span></span>

## <span data-ttu-id="ea040-121">输出</span><span class="sxs-lookup"><span data-stu-id="ea040-121">OUTPUTS</span></span>

### <span data-ttu-id="ea040-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="ea040-122">System.Object</span></span>

## <span data-ttu-id="ea040-123">注释</span><span class="sxs-lookup"><span data-stu-id="ea040-123">NOTES</span></span>

## <span data-ttu-id="ea040-124">相关链接</span><span class="sxs-lookup"><span data-stu-id="ea040-124">RELATED LINKS</span></span>
