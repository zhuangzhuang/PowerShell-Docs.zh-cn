---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603591"
---
# <span data-ttu-id="0e7a7-102">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="0e7a7-102">Invoke-DscResource</span></span>

## <span data-ttu-id="0e7a7-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0e7a7-103">SYNOPSIS</span></span>
<span data-ttu-id="0e7a7-104"> (DSC) 资源运行指定的 PowerShell 所需状态配置的方法。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-104">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="0e7a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0e7a7-105">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="0e7a7-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e7a7-106">DESCRIPTION</span></span>

<span data-ttu-id="0e7a7-107">`Invoke-DscResource` cmdlet 运行指定的 PowerShell 所需状态配置 (DSC) 资源的方法。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-107">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="0e7a7-108">此 cmdlet 直接调用 DSC 资源，而无需创建配置文档。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-108">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="0e7a7-109">使用此 cmdlet，配置管理产品可以使用 DSC 资源来管理 windows 或 Linux。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-109">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="0e7a7-110">在启用调试的情况下运行 DSC 引擎时，此 cmdlet 还可用于调试资源。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-110">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="0e7a7-111">`Invoke-DscResource` 是 PowerShell 7 中的实验性功能。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-111">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="0e7a7-112">若要使用 cmdlet，必须使用以下命令启用它。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-112">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="0e7a7-113">示例</span><span class="sxs-lookup"><span data-stu-id="0e7a7-113">EXAMPLES</span></span>

### <span data-ttu-id="0e7a7-114">示例1：通过指定资源的必需属性来调用该资源的 Set 方法</span><span class="sxs-lookup"><span data-stu-id="0e7a7-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="0e7a7-115">此示例调用名为 **WindowsProcess** 的资源的 **Set** 方法，并提供必需的 **路径** 和 **参数** 属性来启动指定的 Windows 进程。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-115">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="0e7a7-116">示例2：为指定模块调用资源的测试方法</span><span class="sxs-lookup"><span data-stu-id="0e7a7-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="0e7a7-117">此示例调用名为 **WindowsProcess** 的资源的 **测试** 方法，该资源位于名为 **PSDesiredStateConfiguration** 的模块中。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-117">This example invokes the **Test** method of a resource named **WindowsProcess**, which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="0e7a7-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0e7a7-118">PARAMETERS</span></span>

### <span data-ttu-id="0e7a7-119">-方法</span><span class="sxs-lookup"><span data-stu-id="0e7a7-119">-Method</span></span>

<span data-ttu-id="0e7a7-120">指定此 cmdlet 调用的资源的方法。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="0e7a7-121">此参数可接受的值包括： **Get**、 **Set** 和 **Test**。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-121">The acceptable values for this parameter are: **Get**, **Set**, and **Test**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e7a7-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="0e7a7-122">-ModuleName</span></span>

<span data-ttu-id="0e7a7-123">指定此 cmdlet 从中调用指定资源的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e7a7-124">-Name</span><span class="sxs-lookup"><span data-stu-id="0e7a7-124">-Name</span></span>

<span data-ttu-id="0e7a7-125">指定要启动的 DSC 资源的名称。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e7a7-126">-Property</span><span class="sxs-lookup"><span data-stu-id="0e7a7-126">-Property</span></span>

<span data-ttu-id="0e7a7-127">分别在哈希表中将资源属性名称及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e7a7-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e7a7-128">CommonParameters</span></span>

<span data-ttu-id="0e7a7-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0e7a7-130">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0e7a7-131">输入</span><span class="sxs-lookup"><span data-stu-id="0e7a7-131">INPUTS</span></span>

### <span data-ttu-id="0e7a7-132">System.String</span><span class="sxs-lookup"><span data-stu-id="0e7a7-132">System.String</span></span>

### <span data-ttu-id="0e7a7-133">ModuleSpecification。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-133">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="0e7a7-134">输出</span><span class="sxs-lookup"><span data-stu-id="0e7a7-134">OUTPUTS</span></span>

### <span data-ttu-id="0e7a7-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="0e7a7-135">System.Object</span></span>

## <span data-ttu-id="0e7a7-136">注释</span><span class="sxs-lookup"><span data-stu-id="0e7a7-136">NOTES</span></span>

- <span data-ttu-id="0e7a7-137">以前，Windows PowerShell 5.1 资源在系统上下文下运行，除非使用 key **PsDscRunAsCredential** 通过用户上下文指定。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-137">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="0e7a7-138">在 PowerShell 7.0 中，资源在用户的上下文中运行，并且不再支持 **PsDscRunAsCredential** 。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-138">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="0e7a7-139">使用此密钥的以前的配置将引发异常。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-139">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="0e7a7-140">从 PowerShell 7 中， `Invoke-DscResource` 不再支持调用 WMI DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-140">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="0e7a7-141">这包括 PSDesiredStateConfiguration 中的文件和日志资源  。</span><span class="sxs-lookup"><span data-stu-id="0e7a7-141">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="0e7a7-142">相关链接</span><span class="sxs-lookup"><span data-stu-id="0e7a7-142">RELATED LINKS</span></span>

[<span data-ttu-id="0e7a7-143">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="0e7a7-143">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="0e7a7-144">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="0e7a7-144">Get-DscResource</span></span>](Get-DscResource.md)
