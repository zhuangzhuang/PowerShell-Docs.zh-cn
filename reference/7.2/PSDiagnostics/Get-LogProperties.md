---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: f532dd3ff46f14348437de531e80e94b192b13e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598062"
---
# <span data-ttu-id="d0e67-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d0e67-102">Get-LogProperties</span></span>

## <span data-ttu-id="d0e67-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d0e67-103">SYNOPSIS</span></span>
<span data-ttu-id="d0e67-104">检索 Windows 事件日志的属性。</span><span class="sxs-lookup"><span data-stu-id="d0e67-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="d0e67-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d0e67-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="d0e67-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d0e67-106">DESCRIPTION</span></span>

<span data-ttu-id="d0e67-107">此 cmdlet 将获取 Windows 事件日志的配置设置。</span><span class="sxs-lookup"><span data-stu-id="d0e67-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="d0e67-108">此 cmdlet 由 `Enable-PSTrace` 和 `Disable-PSTrace` cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="d0e67-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="d0e67-109">示例</span><span class="sxs-lookup"><span data-stu-id="d0e67-109">EXAMPLES</span></span>

### <span data-ttu-id="d0e67-110">示例1：获取 Windows PowerShell 事件日志的配置设置</span><span class="sxs-lookup"><span data-stu-id="d0e67-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="d0e67-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d0e67-111">PARAMETERS</span></span>

### <span data-ttu-id="d0e67-112">-Name</span><span class="sxs-lookup"><span data-stu-id="d0e67-112">-Name</span></span>

<span data-ttu-id="d0e67-113">事件提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="d0e67-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d0e67-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d0e67-114">CommonParameters</span></span>

<span data-ttu-id="d0e67-115">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d0e67-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d0e67-116">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d0e67-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d0e67-117">输入</span><span class="sxs-lookup"><span data-stu-id="d0e67-117">INPUTS</span></span>

### <span data-ttu-id="d0e67-118">System.String</span><span class="sxs-lookup"><span data-stu-id="d0e67-118">System.String</span></span>

## <span data-ttu-id="d0e67-119">输出</span><span class="sxs-lookup"><span data-stu-id="d0e67-119">OUTPUTS</span></span>

### <span data-ttu-id="d0e67-120">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="d0e67-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="d0e67-121">**PSDiagnostics** 模块将 **LogDetails** 类添加到 `Microsoft.PowerShell.Diagnostics` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="d0e67-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="d0e67-122">注释</span><span class="sxs-lookup"><span data-stu-id="d0e67-122">NOTES</span></span>

## <span data-ttu-id="d0e67-123">相关链接</span><span class="sxs-lookup"><span data-stu-id="d0e67-123">RELATED LINKS</span></span>

[<span data-ttu-id="d0e67-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d0e67-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="d0e67-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d0e67-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="d0e67-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d0e67-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)

