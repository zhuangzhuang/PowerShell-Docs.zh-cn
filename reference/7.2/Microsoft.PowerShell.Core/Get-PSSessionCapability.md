---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: e81302a442294a7eeab81c6e8e1c6b7fd0cfb5fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598280"
---
# <span data-ttu-id="6b6ae-102">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="6b6ae-102">Get-PSSessionCapability</span></span>

## <span data-ttu-id="6b6ae-103">摘要</span><span class="sxs-lookup"><span data-stu-id="6b6ae-103">SYNOPSIS</span></span>
<span data-ttu-id="6b6ae-104">获取受约束的会话配置上的特定用户的功能。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-104">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="6b6ae-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b6ae-105">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="6b6ae-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6b6ae-106">DESCRIPTION</span></span>

<span data-ttu-id="6b6ae-107">**PSSessionCapability** cmdlet 获取特定用户对受约束会话配置的功能。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-107">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="6b6ae-108">使用此 cmdlet 审核用户的自定义会话配置。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-108">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="6b6ae-109">从 Windows PowerShell 5.0 开始，你可以使用会话配置中的 **RoleDefinitions** 属性) 文件 (。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-109">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="6b6ae-110">使用此属性，你可以基于组成员身份向用户授予针对单个受约束的终结点的不同功能。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-110">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="6b6ae-111">通过让你确定授予用户的确切功能， **PSSessionCapability** cmdlet 可降低审核这些终结点时的复杂性。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-111">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="6b6ae-112">默认情况下， **PSSessionCapability** cmdlet 返回指定用户可在指定终结点中运行的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-112">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="6b6ae-113">这等效于指定终结点中运行 **Get 命令** 的用户。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-113">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="6b6ae-114">当使用 *Full* 参数运行时，此 cmdlet 将返回 **InitialSessionState** 对象。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-114">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="6b6ae-115">此对象包含有关指定的用户将与指定的终结点交互的 PowerShell 运行空间的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-115">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="6b6ae-116">它包括语言模式、执行策略和环境变量等信息。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-116">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="6b6ae-117">示例</span><span class="sxs-lookup"><span data-stu-id="6b6ae-117">EXAMPLES</span></span>

### <span data-ttu-id="6b6ae-118">示例1：获取可用于用户的命令</span><span class="sxs-lookup"><span data-stu-id="6b6ae-118">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="6b6ae-119">当连接到本地计算机上的 Endpoint1 约束终结点时，此示例将返回可供用户 CONTOSO\User 使用的命令。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-119">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="6b6ae-120">示例2：获取有关用户的运行空间的详细信息</span><span class="sxs-lookup"><span data-stu-id="6b6ae-120">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="6b6ae-121">此示例返回有关用户 CONTOSO\User 连接到 Endpoint1 约束终结点时将与之交互的运行空间的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-121">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="6b6ae-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b6ae-122">PARAMETERS</span></span>

### <span data-ttu-id="6b6ae-123">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6b6ae-123">-ConfigurationName</span></span>

<span data-ttu-id="6b6ae-124">指定正在检查)  (终结点的受约束的会话配置。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-124">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b6ae-125">-Full</span><span class="sxs-lookup"><span data-stu-id="6b6ae-125">-Full</span></span>

<span data-ttu-id="6b6ae-126">指示此 cmdlet 返回指定的约束终结点上指定用户的整个初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-126">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b6ae-127">-Username</span><span class="sxs-lookup"><span data-stu-id="6b6ae-127">-Username</span></span>

<span data-ttu-id="6b6ae-128">指定正在检查其功能的用户。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-128">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b6ae-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b6ae-129">CommonParameters</span></span>

<span data-ttu-id="6b6ae-130">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b6ae-131">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6b6ae-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b6ae-132">输入</span><span class="sxs-lookup"><span data-stu-id="6b6ae-132">INPUTS</span></span>

## <span data-ttu-id="6b6ae-133">输出</span><span class="sxs-lookup"><span data-stu-id="6b6ae-133">OUTPUTS</span></span>

### <span data-ttu-id="6b6ae-134">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="6b6ae-134">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="6b6ae-135">System.web. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="6b6ae-135">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="6b6ae-136">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="6b6ae-136">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="6b6ae-137">注释</span><span class="sxs-lookup"><span data-stu-id="6b6ae-137">NOTES</span></span>

## <span data-ttu-id="6b6ae-138">相关链接</span><span class="sxs-lookup"><span data-stu-id="6b6ae-138">RELATED LINKS</span></span>

[<span data-ttu-id="6b6ae-139">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="6b6ae-139">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)

