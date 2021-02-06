---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 589c8cb36a91de510ffc30973fe70729700ad020
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596643"
---
# <span data-ttu-id="3d7b2-102">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3d7b2-102">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="3d7b2-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3d7b2-103">SYNOPSIS</span></span>
<span data-ttu-id="3d7b2-104">禁用一个或多个运行空间调试，并释放任何挂起的调试器停止。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-104">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="3d7b2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d7b2-105">SYNTAX</span></span>

### <span data-ttu-id="3d7b2-106">RunspaceNameParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="3d7b2-106">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3d7b2-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d7b2-107">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="3d7b2-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d7b2-108">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="3d7b2-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d7b2-109">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3d7b2-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3d7b2-110">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3d7b2-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3d7b2-111">DESCRIPTION</span></span>

<span data-ttu-id="3d7b2-112">`Disable-RunspaceDebug`Cmdlet 在一个或多个运行空间上禁用调试，并释放任何挂起的调试器停止。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-112">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="3d7b2-113">示例</span><span class="sxs-lookup"><span data-stu-id="3d7b2-113">EXAMPLES</span></span>

### <span data-ttu-id="3d7b2-114">1：禁用默认的运行空间调试器</span><span class="sxs-lookup"><span data-stu-id="3d7b2-114">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="3d7b2-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d7b2-115">PARAMETERS</span></span>

### <span data-ttu-id="3d7b2-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="3d7b2-116">-AppDomainName</span></span>

<span data-ttu-id="3d7b2-117">承载 PowerShell 运行空间的应用程序域的名称。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="3d7b2-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="3d7b2-118">-ProcessName</span></span>

<span data-ttu-id="3d7b2-119">承载 PowerShell 运行空间的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="3d7b2-120">-运行空间</span><span class="sxs-lookup"><span data-stu-id="3d7b2-120">-Runspace</span></span>

<span data-ttu-id="3d7b2-121">要禁用的一个或多个 **运行空间** 对象。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="3d7b2-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="3d7b2-122">-RunspaceId</span></span>

<span data-ttu-id="3d7b2-123">要禁用的一个或多个 **运行空间** Id 号。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="3d7b2-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="3d7b2-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="3d7b2-125">要禁用的一个或多个 **运行空间** guid。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="3d7b2-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="3d7b2-126">-RunspaceName</span></span>

<span data-ttu-id="3d7b2-127">要禁用的一个或多个 **运行空间** 名称。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="3d7b2-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d7b2-128">CommonParameters</span></span>

<span data-ttu-id="3d7b2-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d7b2-130">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3d7b2-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d7b2-131">输入</span><span class="sxs-lookup"><span data-stu-id="3d7b2-131">INPUTS</span></span>

## <span data-ttu-id="3d7b2-132">输出</span><span class="sxs-lookup"><span data-stu-id="3d7b2-132">OUTPUTS</span></span>

## <span data-ttu-id="3d7b2-133">注释</span><span class="sxs-lookup"><span data-stu-id="3d7b2-133">NOTES</span></span>

## <span data-ttu-id="3d7b2-134">相关链接</span><span class="sxs-lookup"><span data-stu-id="3d7b2-134">RELATED LINKS</span></span>

[<span data-ttu-id="3d7b2-135">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3d7b2-135">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="3d7b2-136">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3d7b2-136">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

