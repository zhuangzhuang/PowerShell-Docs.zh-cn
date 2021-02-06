---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595409"
---
# <span data-ttu-id="0b014-102">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0b014-102">Get-RunspaceDebug</span></span>

## <span data-ttu-id="0b014-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0b014-103">SYNOPSIS</span></span>
<span data-ttu-id="0b014-104">显示运行空间调试选项。</span><span class="sxs-lookup"><span data-stu-id="0b014-104">Shows runspace debugging options.</span></span>

## <span data-ttu-id="0b014-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0b014-105">SYNTAX</span></span>

### <span data-ttu-id="0b014-106">RunspaceNameParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="0b014-106">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0b014-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="0b014-107">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="0b014-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="0b014-108">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="0b014-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="0b014-109">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="0b014-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="0b014-110">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0b014-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0b014-111">DESCRIPTION</span></span>

<span data-ttu-id="0b014-112">`Get-RunspaceDebug`Cmdlet 显示运行空间调试选项。</span><span class="sxs-lookup"><span data-stu-id="0b014-112">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="0b014-113">示例</span><span class="sxs-lookup"><span data-stu-id="0b014-113">EXAMPLES</span></span>

### <span data-ttu-id="0b014-114">1：显示默认运行空间调试程序的状态</span><span class="sxs-lookup"><span data-stu-id="0b014-114">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="0b014-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0b014-115">PARAMETERS</span></span>

### <span data-ttu-id="0b014-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="0b014-116">-AppDomainName</span></span>

<span data-ttu-id="0b014-117">承载 PowerShell 运行空间的应用程序域的名称。</span><span class="sxs-lookup"><span data-stu-id="0b014-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="0b014-118">-ProcessName</span></span>

<span data-ttu-id="0b014-119">承载 PowerShell 运行空间的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="0b014-119">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-120">-运行空间</span><span class="sxs-lookup"><span data-stu-id="0b014-120">-Runspace</span></span>

<span data-ttu-id="0b014-121">要禁用的一个或多个 **运行空间** 对象。</span><span class="sxs-lookup"><span data-stu-id="0b014-121">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="0b014-122">-RunspaceId</span></span>

<span data-ttu-id="0b014-123">要禁用的一个或多个 **运行空间** Id 号。</span><span class="sxs-lookup"><span data-stu-id="0b014-123">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="0b014-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="0b014-125">要禁用的一个或多个 **运行空间** guid。</span><span class="sxs-lookup"><span data-stu-id="0b014-125">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="0b014-126">-RunspaceName</span></span>

<span data-ttu-id="0b014-127">要禁用的一个或多个 **运行空间** 名称。</span><span class="sxs-lookup"><span data-stu-id="0b014-127">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b014-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b014-128">CommonParameters</span></span>

<span data-ttu-id="0b014-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0b014-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b014-130">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0b014-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0b014-131">输入</span><span class="sxs-lookup"><span data-stu-id="0b014-131">INPUTS</span></span>

## <span data-ttu-id="0b014-132">输出</span><span class="sxs-lookup"><span data-stu-id="0b014-132">OUTPUTS</span></span>

## <span data-ttu-id="0b014-133">注释</span><span class="sxs-lookup"><span data-stu-id="0b014-133">NOTES</span></span>

## <span data-ttu-id="0b014-134">相关链接</span><span class="sxs-lookup"><span data-stu-id="0b014-134">RELATED LINKS</span></span>

[<span data-ttu-id="0b014-135">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0b014-135">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="0b014-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0b014-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

