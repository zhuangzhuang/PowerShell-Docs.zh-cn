---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
schema: 2.0.0
ms.openlocfilehash: 5cb8ddbd06f8b7fdbadae0b7c738e26a68ff5c48
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597273"
---
# <span data-ttu-id="c08df-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="c08df-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="c08df-102">摘要</span><span class="sxs-lookup"><span data-stu-id="c08df-102">SYNOPSIS</span></span>
<span data-ttu-id="c08df-103">检索有关在 PowerShell 中注册的子系统的信息。</span><span class="sxs-lookup"><span data-stu-id="c08df-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="c08df-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c08df-104">SYNTAX</span></span>

### <span data-ttu-id="c08df-105">GetAllSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="c08df-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="c08df-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="c08df-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="c08df-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="c08df-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="c08df-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c08df-108">DESCRIPTION</span></span>

<span data-ttu-id="c08df-109">检索有关在 PowerShell 中注册的子系统的信息。</span><span class="sxs-lookup"><span data-stu-id="c08df-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="c08df-110">这是一项实验性功能。</span><span class="sxs-lookup"><span data-stu-id="c08df-110">This is an experimental feature.</span></span> <span data-ttu-id="c08df-111">只有启用此功能时，此 cmdlet 才可用 `PSSubsystemPluginModel` 。</span><span class="sxs-lookup"><span data-stu-id="c08df-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="c08df-112">有关详细信息，请参阅[使用实验性功能](/powershell/scripting/learn/experimental-features)。</span><span class="sxs-lookup"><span data-stu-id="c08df-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="c08df-113">利用此功能，可以将 `System.Management.Automation.dll` 的组件分隔到驻留在自己的程序集中的各个子系统。</span><span class="sxs-lookup"><span data-stu-id="c08df-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="c08df-114">这种隔离可减少核心 PowerShell 引擎的磁盘占用，并支持这些组件成为最小 PowerShell 安装的可选功能。</span><span class="sxs-lookup"><span data-stu-id="c08df-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="c08df-115">目前仅支持 CommandPredictor 子系统。</span><span class="sxs-lookup"><span data-stu-id="c08df-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="c08df-116">该子系统与 PSReadLine 模块一起使用，以提供自定义预测插件。</span><span class="sxs-lookup"><span data-stu-id="c08df-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="c08df-117">将来  ，Job、CommandCompleter、Remoting 和其他组件可以分隔到 `System.Management.Automation.dll` 外的子系统程序集。</span><span class="sxs-lookup"><span data-stu-id="c08df-117">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="c08df-118">示例</span><span class="sxs-lookup"><span data-stu-id="c08df-118">EXAMPLES</span></span>

### <span data-ttu-id="c08df-119">示例 1-显示所有可用子系统</span><span class="sxs-lookup"><span data-stu-id="c08df-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="c08df-120">示例 2-显示特定类型的所有可用子系统</span><span class="sxs-lookup"><span data-stu-id="c08df-120">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="c08df-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c08df-121">PARAMETERS</span></span>

### <span data-ttu-id="c08df-122">-Kind</span><span class="sxs-lookup"><span data-stu-id="c08df-122">-Kind</span></span>


<span data-ttu-id="c08df-123">指定要返回的子系统的种类。</span><span class="sxs-lookup"><span data-stu-id="c08df-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="c08df-124">有效值为： `CommandPredictor` 。</span><span class="sxs-lookup"><span data-stu-id="c08df-124">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="c08df-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="c08df-125">-SubsystemType</span></span>

<span data-ttu-id="c08df-126">指定要返回的子系统类型。</span><span class="sxs-lookup"><span data-stu-id="c08df-126">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="c08df-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c08df-127">CommonParameters</span></span>

<span data-ttu-id="c08df-128">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c08df-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c08df-129">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c08df-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c08df-130">输入</span><span class="sxs-lookup"><span data-stu-id="c08df-130">INPUTS</span></span>

### <span data-ttu-id="c08df-131">"SubsystemKind"。</span><span class="sxs-lookup"><span data-stu-id="c08df-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="c08df-132">System.Type</span><span class="sxs-lookup"><span data-stu-id="c08df-132">System.Type</span></span>

## <span data-ttu-id="c08df-133">输出</span><span class="sxs-lookup"><span data-stu-id="c08df-133">OUTPUTS</span></span>

### <span data-ttu-id="c08df-134">"SubsystemInfo"。</span><span class="sxs-lookup"><span data-stu-id="c08df-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="c08df-135">注释</span><span class="sxs-lookup"><span data-stu-id="c08df-135">NOTES</span></span>

## <span data-ttu-id="c08df-136">相关链接</span><span class="sxs-lookup"><span data-stu-id="c08df-136">RELATED LINKS</span></span>

[<span data-ttu-id="c08df-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="c08df-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="c08df-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="c08df-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="c08df-139">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="c08df-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="c08df-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="c08df-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="c08df-141">使用实验性功能</span><span class="sxs-lookup"><span data-stu-id="c08df-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
