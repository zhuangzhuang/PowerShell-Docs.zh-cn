---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 26ab9b9135eedafa0238eab5c07aa7abb7880ed4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603399"
---
# <span data-ttu-id="d7b85-102">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d7b85-102">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="d7b85-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d7b85-103">SYNOPSIS</span></span>
<span data-ttu-id="d7b85-104">启用对运行空间的调试，其中任何断点都将保留，直到附加调试器。</span><span class="sxs-lookup"><span data-stu-id="d7b85-104">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="d7b85-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d7b85-105">SYNTAX</span></span>

### <span data-ttu-id="d7b85-106">RunspaceNameParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="d7b85-106">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d7b85-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="d7b85-107">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="d7b85-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d7b85-108">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="d7b85-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d7b85-109">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="d7b85-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d7b85-110">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d7b85-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d7b85-111">DESCRIPTION</span></span>

<span data-ttu-id="d7b85-112">`Enable-RunspaceDebug`Cmdlet 在附加了调试器的情况下，允许在保留了任何断点的运行空间上进行调试。</span><span class="sxs-lookup"><span data-stu-id="d7b85-112">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="d7b85-113">示例</span><span class="sxs-lookup"><span data-stu-id="d7b85-113">EXAMPLES</span></span>

### <span data-ttu-id="d7b85-114">1：启用默认的运行空间调试器</span><span class="sxs-lookup"><span data-stu-id="d7b85-114">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="d7b85-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d7b85-115">PARAMETERS</span></span>

### <span data-ttu-id="d7b85-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="d7b85-116">-AppDomainName</span></span>

<span data-ttu-id="d7b85-117">承载 PowerShell 运行空间的应用程序域的名称。</span><span class="sxs-lookup"><span data-stu-id="d7b85-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="d7b85-118">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="d7b85-118">-BreakAll</span></span>

<span data-ttu-id="d7b85-119">使运行空间中任何正在运行的命令或脚本在步骤模式下停止，无论当前是否附加调试器。</span><span class="sxs-lookup"><span data-stu-id="d7b85-119">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="d7b85-120">脚本或命令将保持停止状态，直到附加调试器来调试当前的停止点。</span><span class="sxs-lookup"><span data-stu-id="d7b85-120">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d7b85-121">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="d7b85-121">-ProcessName</span></span>

<span data-ttu-id="d7b85-122">承载 PowerShell 运行空间的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="d7b85-122">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="d7b85-123">-运行空间</span><span class="sxs-lookup"><span data-stu-id="d7b85-123">-Runspace</span></span>

<span data-ttu-id="d7b85-124">要禁用的一个或多个 **运行空间** 对象。</span><span class="sxs-lookup"><span data-stu-id="d7b85-124">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="d7b85-125">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="d7b85-125">-RunspaceId</span></span>

<span data-ttu-id="d7b85-126">要禁用的一个或多个 **运行空间** Id 号。</span><span class="sxs-lookup"><span data-stu-id="d7b85-126">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="d7b85-127">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="d7b85-127">-RunspaceInstanceId</span></span>

<span data-ttu-id="d7b85-128">要禁用的一个或多个 **运行空间** guid。</span><span class="sxs-lookup"><span data-stu-id="d7b85-128">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="d7b85-129">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="d7b85-129">-RunspaceName</span></span>

<span data-ttu-id="d7b85-130">要禁用的一个或多个 **运行空间** 名称。</span><span class="sxs-lookup"><span data-stu-id="d7b85-130">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="d7b85-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d7b85-131">CommonParameters</span></span>

<span data-ttu-id="d7b85-132">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d7b85-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d7b85-133">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d7b85-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d7b85-134">输入</span><span class="sxs-lookup"><span data-stu-id="d7b85-134">INPUTS</span></span>

## <span data-ttu-id="d7b85-135">输出</span><span class="sxs-lookup"><span data-stu-id="d7b85-135">OUTPUTS</span></span>

## <span data-ttu-id="d7b85-136">注释</span><span class="sxs-lookup"><span data-stu-id="d7b85-136">NOTES</span></span>

## <span data-ttu-id="d7b85-137">相关链接</span><span class="sxs-lookup"><span data-stu-id="d7b85-137">RELATED LINKS</span></span>

[<span data-ttu-id="d7b85-138">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d7b85-138">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="d7b85-139">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="d7b85-139">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

