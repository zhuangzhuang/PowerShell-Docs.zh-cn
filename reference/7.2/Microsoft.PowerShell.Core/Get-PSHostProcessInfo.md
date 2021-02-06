---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 6528d25ea706ac63927ef3d23cf661489caae8aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599061"
---
# <span data-ttu-id="3b975-102">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="3b975-102">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="3b975-103">摘要</span><span class="sxs-lookup"><span data-stu-id="3b975-103">SYNOPSIS</span></span>
<span data-ttu-id="3b975-104">获取有关 PowerShell 主机的进程信息。</span><span class="sxs-lookup"><span data-stu-id="3b975-104">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="3b975-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3b975-105">SYNTAX</span></span>

### <span data-ttu-id="3b975-106">ProcessNameParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="3b975-106">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3b975-107">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="3b975-107">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="3b975-108">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3b975-108">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="3b975-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3b975-109">DESCRIPTION</span></span>

<span data-ttu-id="3b975-110">`Get-PSHostProcessInfo`Cmdlet 获取有关在本地计算机上运行的 PowerShell 主机进程的信息。</span><span class="sxs-lookup"><span data-stu-id="3b975-110">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="3b975-111">从 PowerShell 6.2 开始，非 Windows 平台上支持此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b975-111">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="3b975-112">示例</span><span class="sxs-lookup"><span data-stu-id="3b975-112">EXAMPLES</span></span>

### <span data-ttu-id="3b975-113">1：获取在系统上运行的 PowerShell 主机的列表</span><span class="sxs-lookup"><span data-stu-id="3b975-113">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="3b975-114">2：获取特定进程名称的 PowerShell 主机信息</span><span class="sxs-lookup"><span data-stu-id="3b975-114">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="3b975-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3b975-115">PARAMETERS</span></span>

### <span data-ttu-id="3b975-116">-Id</span><span class="sxs-lookup"><span data-stu-id="3b975-116">-Id</span></span>

<span data-ttu-id="3b975-117">按进程 ID 指定进程。</span><span class="sxs-lookup"><span data-stu-id="3b975-117">Specifies a process by the process ID.</span></span> <span data-ttu-id="3b975-118">若要获取进程 ID，请运行 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b975-118">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3b975-119">-Name</span><span class="sxs-lookup"><span data-stu-id="3b975-119">-Name</span></span>

<span data-ttu-id="3b975-120">按进程名称指定进程。</span><span class="sxs-lookup"><span data-stu-id="3b975-120">Specifies a process by the process name.</span></span> <span data-ttu-id="3b975-121">若要获取进程名称，请运行 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b975-121">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3b975-122">-Process</span><span class="sxs-lookup"><span data-stu-id="3b975-122">-Process</span></span>

<span data-ttu-id="3b975-123">按进程对象指定进程。</span><span class="sxs-lookup"><span data-stu-id="3b975-123">Specifies a process by the process object.</span></span> <span data-ttu-id="3b975-124">使用此参数的最简单方法是 `Get-Process` ：保存返回要在变量中输入的进程的命令的结果，然后将该变量指定为此参数的值。</span><span class="sxs-lookup"><span data-stu-id="3b975-124">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3b975-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b975-125">CommonParameters</span></span>

<span data-ttu-id="3b975-126">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3b975-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b975-127">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3b975-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3b975-128">输入</span><span class="sxs-lookup"><span data-stu-id="3b975-128">INPUTS</span></span>

### <span data-ttu-id="3b975-129">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="3b975-129">System.Diagnostics.Process</span></span>

<span data-ttu-id="3b975-130">可以通过管道将 **进程** 对象传递 `Get-Process` 给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b975-130">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="3b975-131">输出</span><span class="sxs-lookup"><span data-stu-id="3b975-131">OUTPUTS</span></span>

### <span data-ttu-id="3b975-132">Get-pshostprocessinfo。</span><span class="sxs-lookup"><span data-stu-id="3b975-132">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="3b975-133">注释</span><span class="sxs-lookup"><span data-stu-id="3b975-133">NOTES</span></span>

## <span data-ttu-id="3b975-134">相关链接</span><span class="sxs-lookup"><span data-stu-id="3b975-134">RELATED LINKS</span></span>

[<span data-ttu-id="3b975-135">Get-Process</span><span class="sxs-lookup"><span data-stu-id="3b975-135">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)

