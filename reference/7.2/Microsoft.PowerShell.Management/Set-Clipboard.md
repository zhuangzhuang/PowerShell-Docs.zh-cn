---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 7772c3e7a5f7492713e0be9a94e92b8c41cd3dd4
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2020
ms.locfileid: "99603402"
---
# <span data-ttu-id="c924c-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="c924c-102">Set-Clipboard</span></span>

## <span data-ttu-id="c924c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c924c-103">SYNOPSIS</span></span>
<span data-ttu-id="c924c-104">设置剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="c924c-104">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="c924c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c924c-105">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c924c-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c924c-106">DESCRIPTION</span></span>

<span data-ttu-id="c924c-107">`Set-Clipboard`Cmdlet 设置剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="c924c-107">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="c924c-108">在 Linux 上，此 cmdlet 要求 `xclip` 实用工具在路径中。</span><span class="sxs-lookup"><span data-stu-id="c924c-108">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="c924c-109">示例</span><span class="sxs-lookup"><span data-stu-id="c924c-109">EXAMPLES</span></span>

### <span data-ttu-id="c924c-110">示例1：将文本复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="c924c-110">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="c924c-111">示例2：将文件的内容复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="c924c-111">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="c924c-112">此示例将文件的内容传输到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="c924c-112">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="c924c-113">在此示例中，我们将获得一个公共 ssh 密钥，以便可以将其粘贴到其他应用程序（例如 GitHub）中。</span><span class="sxs-lookup"><span data-stu-id="c924c-113">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="c924c-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c924c-114">PARAMETERS</span></span>

### <span data-ttu-id="c924c-115">-Append</span><span class="sxs-lookup"><span data-stu-id="c924c-115">-Append</span></span>

<span data-ttu-id="c924c-116">指示 cmdlet 不清除剪贴板，并向其追加内容。</span><span class="sxs-lookup"><span data-stu-id="c924c-116">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="c924c-117">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c924c-117">-Confirm</span></span>

<span data-ttu-id="c924c-118">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="c924c-118">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c924c-119">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c924c-119">-WhatIf</span></span>

<span data-ttu-id="c924c-120">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="c924c-120">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c924c-121">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="c924c-121">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c924c-122">-Value</span><span class="sxs-lookup"><span data-stu-id="c924c-122">-Value</span></span>

<span data-ttu-id="c924c-123">要添加到剪贴板中的字符串值。</span><span class="sxs-lookup"><span data-stu-id="c924c-123">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c924c-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c924c-124">CommonParameters</span></span>

<span data-ttu-id="c924c-125">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c924c-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c924c-126">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c924c-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c924c-127">输入</span><span class="sxs-lookup"><span data-stu-id="c924c-127">INPUTS</span></span>

### <span data-ttu-id="c924c-128">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c924c-128">System.String[]</span></span>

## <span data-ttu-id="c924c-129">输出</span><span class="sxs-lookup"><span data-stu-id="c924c-129">OUTPUTS</span></span>

## <span data-ttu-id="c924c-130">注释</span><span class="sxs-lookup"><span data-stu-id="c924c-130">NOTES</span></span>

<span data-ttu-id="c924c-131">在极少数情况下 `Set-Clipboard` ，当快速连续使用具有大量值的情况（例如在循环中）时，可能偶尔会从剪贴板获取空白值。</span><span class="sxs-lookup"><span data-stu-id="c924c-131">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="c924c-132">可以通过在循环中使用来解决此情况 `Start-Sleep -Milliseconds 1` 。</span><span class="sxs-lookup"><span data-stu-id="c924c-132">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="c924c-133">相关链接</span><span class="sxs-lookup"><span data-stu-id="c924c-133">RELATED LINKS</span></span>

[<span data-ttu-id="c924c-134">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="c924c-134">Get-Clipboard</span></span>](Get-Clipboard.md)
