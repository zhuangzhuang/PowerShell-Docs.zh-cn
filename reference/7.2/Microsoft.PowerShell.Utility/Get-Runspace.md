---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 34843894cb6253e3d8e89072cf79cb9237d4fc19
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596024"
---
# <span data-ttu-id="437b6-102">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="437b6-102">Get-Runspace</span></span>

## <span data-ttu-id="437b6-103">摘要</span><span class="sxs-lookup"><span data-stu-id="437b6-103">SYNOPSIS</span></span>
<span data-ttu-id="437b6-104">获取 PowerShell 主机进程内的活动运行空间。</span><span class="sxs-lookup"><span data-stu-id="437b6-104">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="437b6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="437b6-105">SYNTAX</span></span>

### <span data-ttu-id="437b6-106">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="437b6-106">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="437b6-107">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="437b6-107">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="437b6-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="437b6-108">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="437b6-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="437b6-109">DESCRIPTION</span></span>

<span data-ttu-id="437b6-110">`Get-Runspace`Cmdlet 将获取 PowerShell 主机进程中的活动运行空间。</span><span class="sxs-lookup"><span data-stu-id="437b6-110">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="437b6-111">示例</span><span class="sxs-lookup"><span data-stu-id="437b6-111">EXAMPLES</span></span>

### <span data-ttu-id="437b6-112">示例1：获取运行空间</span><span class="sxs-lookup"><span data-stu-id="437b6-112">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="437b6-113">示例2：按 Id 获取运行空间</span><span class="sxs-lookup"><span data-stu-id="437b6-113">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="437b6-114">示例3：按名称获取运行空间</span><span class="sxs-lookup"><span data-stu-id="437b6-114">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="437b6-115">示例4：按 InstanceId 获取运行空间</span><span class="sxs-lookup"><span data-stu-id="437b6-115">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="437b6-116">在此示例中，我们使用参数标识可用的运行空间 `Name` ，并将返回对象存储到变量 `$activeRunspace` 。</span><span class="sxs-lookup"><span data-stu-id="437b6-116">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="437b6-117">这样，便可以在后续运行中使用运行 **空间** 的属性 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="437b6-117">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="437b6-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="437b6-118">PARAMETERS</span></span>

### <span data-ttu-id="437b6-119">-Id</span><span class="sxs-lookup"><span data-stu-id="437b6-119">-Id</span></span>

<span data-ttu-id="437b6-120">指定运行空间的 Id</span><span class="sxs-lookup"><span data-stu-id="437b6-120">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="437b6-121">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="437b6-121">-InstanceId</span></span>

<span data-ttu-id="437b6-122">指定正在运行的作业的实例 ID GUID。</span><span class="sxs-lookup"><span data-stu-id="437b6-122">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="437b6-123">-Name</span><span class="sxs-lookup"><span data-stu-id="437b6-123">-Name</span></span>

<span data-ttu-id="437b6-124">指定运行空间的名称</span><span class="sxs-lookup"><span data-stu-id="437b6-124">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="437b6-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="437b6-125">CommonParameters</span></span>

<span data-ttu-id="437b6-126">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="437b6-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="437b6-127">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="437b6-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="437b6-128">输入</span><span class="sxs-lookup"><span data-stu-id="437b6-128">INPUTS</span></span>

## <span data-ttu-id="437b6-129">输出</span><span class="sxs-lookup"><span data-stu-id="437b6-129">OUTPUTS</span></span>

### <span data-ttu-id="437b6-130">System.web. Management。</span><span class="sxs-lookup"><span data-stu-id="437b6-130">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="437b6-131">可以通过管道将命令结果传递 `Get-Runspace` 给 `Debug-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="437b6-131">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="437b6-132">注释</span><span class="sxs-lookup"><span data-stu-id="437b6-132">NOTES</span></span>

## <span data-ttu-id="437b6-133">相关链接</span><span class="sxs-lookup"><span data-stu-id="437b6-133">RELATED LINKS</span></span>

[<span data-ttu-id="437b6-134">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="437b6-134">Debug-Runspace</span></span>](Debug-Runspace.md)

