---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 19129eb8a0b478d10fdbf1e35f15b7f86969b5fb
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194989"
---
# <span data-ttu-id="9ee49-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="9ee49-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="9ee49-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9ee49-103">SYNOPSIS</span></span>
<span data-ttu-id="9ee49-104">检索有关在 PowerShell 中注册的子系统的信息。</span><span class="sxs-lookup"><span data-stu-id="9ee49-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="9ee49-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9ee49-105">SYNTAX</span></span>

### <span data-ttu-id="9ee49-106">GetAllSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="9ee49-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="9ee49-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="9ee49-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="9ee49-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="9ee49-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="9ee49-109">说明</span><span class="sxs-lookup"><span data-stu-id="9ee49-109">DESCRIPTION</span></span>

<span data-ttu-id="9ee49-110">检索有关在 PowerShell 中注册的子系统的信息。</span><span class="sxs-lookup"><span data-stu-id="9ee49-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="9ee49-111">这是一项实验性功能。</span><span class="sxs-lookup"><span data-stu-id="9ee49-111">This is an experimental feature.</span></span> <span data-ttu-id="9ee49-112">只有启用此功能时，此 cmdlet 才可用 `PSSubsystemPluginModel` 。</span><span class="sxs-lookup"><span data-stu-id="9ee49-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="9ee49-113">有关详细信息，请参阅[使用实验性功能](/powershell/scripting/learn/experimental-features)。</span><span class="sxs-lookup"><span data-stu-id="9ee49-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="9ee49-114">利用此功能，可以将 `System.Management.Automation.dll` 的组件分隔到驻留在自己的程序集中的各个子系统。</span><span class="sxs-lookup"><span data-stu-id="9ee49-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="9ee49-115">这种隔离可减少核心 PowerShell 引擎的磁盘占用，并支持这些组件成为最小 PowerShell 安装的可选功能。</span><span class="sxs-lookup"><span data-stu-id="9ee49-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="9ee49-116">目前仅支持 CommandPredictor 子系统。</span><span class="sxs-lookup"><span data-stu-id="9ee49-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="9ee49-117">该子系统与 PSReadLine 模块一起使用，以提供自定义预测插件。</span><span class="sxs-lookup"><span data-stu-id="9ee49-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="9ee49-118">将来  ，Job、CommandCompleter、Remoting 和其他组件可以分隔到 `System.Management.Automation.dll` 外的子系统程序集。</span><span class="sxs-lookup"><span data-stu-id="9ee49-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="9ee49-119">示例</span><span class="sxs-lookup"><span data-stu-id="9ee49-119">EXAMPLES</span></span>

### <span data-ttu-id="9ee49-120">示例 1-显示所有可用子系统</span><span class="sxs-lookup"><span data-stu-id="9ee49-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="9ee49-121">示例 2-显示特定类型的所有可用子系统</span><span class="sxs-lookup"><span data-stu-id="9ee49-121">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="9ee49-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ee49-122">PARAMETERS</span></span>

### <span data-ttu-id="9ee49-123">-Kind</span><span class="sxs-lookup"><span data-stu-id="9ee49-123">-Kind</span></span>


<span data-ttu-id="9ee49-124">指定要返回的子系统的种类。</span><span class="sxs-lookup"><span data-stu-id="9ee49-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="9ee49-125">有效值为： `CommandPredictor` 。</span><span class="sxs-lookup"><span data-stu-id="9ee49-125">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9ee49-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="9ee49-126">-SubsystemType</span></span>

<span data-ttu-id="9ee49-127">指定要返回的子系统类型。</span><span class="sxs-lookup"><span data-stu-id="9ee49-127">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9ee49-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ee49-128">CommonParameters</span></span>

<span data-ttu-id="9ee49-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9ee49-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ee49-130">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9ee49-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ee49-131">输入</span><span class="sxs-lookup"><span data-stu-id="9ee49-131">INPUTS</span></span>

### <span data-ttu-id="9ee49-132">"SubsystemKind"。</span><span class="sxs-lookup"><span data-stu-id="9ee49-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="9ee49-133">System.Type</span><span class="sxs-lookup"><span data-stu-id="9ee49-133">System.Type</span></span>

## <span data-ttu-id="9ee49-134">输出</span><span class="sxs-lookup"><span data-stu-id="9ee49-134">OUTPUTS</span></span>

### <span data-ttu-id="9ee49-135">"SubsystemInfo"。</span><span class="sxs-lookup"><span data-stu-id="9ee49-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="9ee49-136">注释</span><span class="sxs-lookup"><span data-stu-id="9ee49-136">NOTES</span></span>

## <span data-ttu-id="9ee49-137">相关链接</span><span class="sxs-lookup"><span data-stu-id="9ee49-137">RELATED LINKS</span></span>

[<span data-ttu-id="9ee49-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="9ee49-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="9ee49-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="9ee49-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="9ee49-140">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="9ee49-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="9ee49-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="9ee49-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="9ee49-142">使用实验性功能</span><span class="sxs-lookup"><span data-stu-id="9ee49-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
