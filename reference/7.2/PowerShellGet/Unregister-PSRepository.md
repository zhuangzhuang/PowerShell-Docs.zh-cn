---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597031"
---
# <span data-ttu-id="f9578-102">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f9578-102">Unregister-PSRepository</span></span>

## <span data-ttu-id="f9578-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f9578-103">SYNOPSIS</span></span>
<span data-ttu-id="f9578-104">取消注册存储库。</span><span class="sxs-lookup"><span data-stu-id="f9578-104">Unregisters a repository.</span></span>

## <span data-ttu-id="f9578-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9578-105">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="f9578-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f9578-106">DESCRIPTION</span></span>

<span data-ttu-id="f9578-107">`Unregister-PSRepository`Cmdlet 将为当前用户注销存储库。</span><span class="sxs-lookup"><span data-stu-id="f9578-107">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="f9578-108">示例</span><span class="sxs-lookup"><span data-stu-id="f9578-108">EXAMPLES</span></span>

### <span data-ttu-id="f9578-109">示例1：取消注册存储库</span><span class="sxs-lookup"><span data-stu-id="f9578-109">Example 1: Unregister a repository</span></span>

<span data-ttu-id="f9578-110">此示例将注销名为 myNuGetSource 的存储库。</span><span class="sxs-lookup"><span data-stu-id="f9578-110">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="f9578-111">示例2：取消注册所有存储库</span><span class="sxs-lookup"><span data-stu-id="f9578-111">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="f9578-112">此示例使用 `Get-PSRepository` 来获取所有已注册的存储库，并使用管道运算符将其传递给 `Unregister-PSRepository` 以将其注销。</span><span class="sxs-lookup"><span data-stu-id="f9578-112">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="f9578-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9578-113">PARAMETERS</span></span>

### <span data-ttu-id="f9578-114">-Name</span><span class="sxs-lookup"><span data-stu-id="f9578-114">-Name</span></span>

<span data-ttu-id="f9578-115">指定要删除的存储库的名称数组。</span><span class="sxs-lookup"><span data-stu-id="f9578-115">Specifies an array of names of the repositories to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f9578-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9578-116">CommonParameters</span></span>

<span data-ttu-id="f9578-117">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f9578-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9578-118">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f9578-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9578-119">输入</span><span class="sxs-lookup"><span data-stu-id="f9578-119">INPUTS</span></span>

### <span data-ttu-id="f9578-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="f9578-120">System.String[]</span></span>

## <span data-ttu-id="f9578-121">输出</span><span class="sxs-lookup"><span data-stu-id="f9578-121">OUTPUTS</span></span>

### <span data-ttu-id="f9578-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="f9578-122">System.Object</span></span>

## <span data-ttu-id="f9578-123">注释</span><span class="sxs-lookup"><span data-stu-id="f9578-123">NOTES</span></span>

## <span data-ttu-id="f9578-124">相关链接</span><span class="sxs-lookup"><span data-stu-id="f9578-124">RELATED LINKS</span></span>

[<span data-ttu-id="f9578-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f9578-125">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="f9578-126">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f9578-126">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="f9578-127">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f9578-127">Set-PSRepository</span></span>](Set-PSRepository.md)
