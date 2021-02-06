---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 2efe75730ef7d35618dc0d1fbf7a8d6f8a5db5ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597049"
---
# <span data-ttu-id="89483-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="89483-102">Read-Host</span></span>

## <span data-ttu-id="89483-103">摘要</span><span class="sxs-lookup"><span data-stu-id="89483-103">SYNOPSIS</span></span>
<span data-ttu-id="89483-104">从控制台读取一行输入。</span><span class="sxs-lookup"><span data-stu-id="89483-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="89483-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89483-105">SYNTAX</span></span>

### <span data-ttu-id="89483-106">AsString（默认值）</span><span class="sxs-lookup"><span data-stu-id="89483-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="89483-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="89483-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="89483-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="89483-108">DESCRIPTION</span></span>

<span data-ttu-id="89483-109">`Read-Host`Cmdlet 从控制台读取一行输入。</span><span class="sxs-lookup"><span data-stu-id="89483-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="89483-110">可使用它来提示用户输入数据。</span><span class="sxs-lookup"><span data-stu-id="89483-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="89483-111">因为可以将输入保存为安全字符串，所以可以使用此 cmdlet 来提示用户输入安全数据（如密码）以及共享的数据。</span><span class="sxs-lookup"><span data-stu-id="89483-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="89483-112">示例</span><span class="sxs-lookup"><span data-stu-id="89483-112">EXAMPLES</span></span>

### <span data-ttu-id="89483-113">示例1：将控制台输入保存到变量</span><span class="sxs-lookup"><span data-stu-id="89483-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="89483-114">此示例显示字符串 "请输入你的年龄：" 作为提示。</span><span class="sxs-lookup"><span data-stu-id="89483-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="89483-115">输入值并按下 Enter 键时，该值将存储在 `$Age` 变量中。</span><span class="sxs-lookup"><span data-stu-id="89483-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="89483-116">示例2：将控制台输入另存为安全字符串</span><span class="sxs-lookup"><span data-stu-id="89483-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="89483-117">此示例显示字符串 "Enter a Password：" 作为提示。</span><span class="sxs-lookup"><span data-stu-id="89483-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="89483-118">输入值时，将在 `*` 控制台上显示星号 () 以替代输入。</span><span class="sxs-lookup"><span data-stu-id="89483-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="89483-119">按下 Enter 键时，该值将作为 **SecureString** 对象存储在 `$pwd_secure_string` 变量中。</span><span class="sxs-lookup"><span data-stu-id="89483-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="89483-120">示例3：掩码输入和纯文本字符串</span><span class="sxs-lookup"><span data-stu-id="89483-120">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="89483-121">此示例显示字符串 "Enter a Password：" 作为提示。</span><span class="sxs-lookup"><span data-stu-id="89483-121">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="89483-122">输入值时，将在 `*` 控制台上显示星号 () 以替代输入。</span><span class="sxs-lookup"><span data-stu-id="89483-122">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="89483-123">按下 Enter 键时，该值将作为纯文本 **字符串** 对象存储在 `$pwd_string` 变量中。</span><span class="sxs-lookup"><span data-stu-id="89483-123">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="89483-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89483-124">PARAMETERS</span></span>

### <span data-ttu-id="89483-125">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="89483-125">-AsSecureString</span></span>

<span data-ttu-id="89483-126">指示该 cmdlet 显示星号 (`*`) 用户键入作为输入的字符。</span><span class="sxs-lookup"><span data-stu-id="89483-126">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="89483-127">使用此参数时，该 cmdlet 的输出 `Read-Host` 是 **SecureString** 对象， (**SecureString**) 。</span><span class="sxs-lookup"><span data-stu-id="89483-127">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89483-128">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="89483-128">-MaskInput</span></span>

<span data-ttu-id="89483-129">指示该 cmdlet 显示星号 (`*`) 用户键入作为输入的字符。</span><span class="sxs-lookup"><span data-stu-id="89483-129">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="89483-130">当你使用此参数时，该 cmdlet 的输出 `Read-Host` 是一个 **字符串** 对象。</span><span class="sxs-lookup"><span data-stu-id="89483-130">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="89483-131">这样，你就可以安全地提示输入以纯文本形式返回的密码，而不是 **SecureString**。</span><span class="sxs-lookup"><span data-stu-id="89483-131">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89483-132">-Prompt</span><span class="sxs-lookup"><span data-stu-id="89483-132">-Prompt</span></span>

<span data-ttu-id="89483-133">指定提示的文本。</span><span class="sxs-lookup"><span data-stu-id="89483-133">Specifies the text of the prompt.</span></span>
<span data-ttu-id="89483-134">键入一个字符串。</span><span class="sxs-lookup"><span data-stu-id="89483-134">Type a string.</span></span>
<span data-ttu-id="89483-135">如果该字符串包含空格，请将其括在引号中。</span><span class="sxs-lookup"><span data-stu-id="89483-135">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="89483-136">PowerShell 将向你输入的文本追加一个冒号 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="89483-136">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89483-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89483-137">CommonParameters</span></span>

<span data-ttu-id="89483-138">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="89483-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89483-139">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="89483-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89483-140">输入</span><span class="sxs-lookup"><span data-stu-id="89483-140">INPUTS</span></span>

### <span data-ttu-id="89483-141">无</span><span class="sxs-lookup"><span data-stu-id="89483-141">None</span></span>

<span data-ttu-id="89483-142">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89483-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="89483-143">输出</span><span class="sxs-lookup"><span data-stu-id="89483-143">OUTPUTS</span></span>

### <span data-ttu-id="89483-144">System.String 或 System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="89483-144">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="89483-145">如果使用 **AsSecureString** 参数，则 `Read-Host` 将返回 **SecureString**。</span><span class="sxs-lookup"><span data-stu-id="89483-145">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="89483-146">否则，它将返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="89483-146">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="89483-147">注释</span><span class="sxs-lookup"><span data-stu-id="89483-147">NOTES</span></span>

## <span data-ttu-id="89483-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="89483-148">RELATED LINKS</span></span>

[<span data-ttu-id="89483-149">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="89483-149">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="89483-150">Get-Host</span><span class="sxs-lookup"><span data-stu-id="89483-150">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="89483-151">Write-Host</span><span class="sxs-lookup"><span data-stu-id="89483-151">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="89483-152">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="89483-152">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
