---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597667"
---
# <span data-ttu-id="4a813-102">Write-Error</span><span class="sxs-lookup"><span data-stu-id="4a813-102">Write-Error</span></span>

## <span data-ttu-id="4a813-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4a813-103">SYNOPSIS</span></span>
<span data-ttu-id="4a813-104">将对象写入错误流。</span><span class="sxs-lookup"><span data-stu-id="4a813-104">Writes an object to the error stream.</span></span>

## <span data-ttu-id="4a813-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a813-105">SYNTAX</span></span>

### <span data-ttu-id="4a813-106">NoException（默认值）</span><span class="sxs-lookup"><span data-stu-id="4a813-106">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="4a813-107">WithException</span><span class="sxs-lookup"><span data-stu-id="4a813-107">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="4a813-108">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="4a813-108">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="4a813-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4a813-109">DESCRIPTION</span></span>

<span data-ttu-id="4a813-110">`Write-Error`Cmdlet 声明非终止错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-110">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="4a813-111">默认情况下，将错误随输出一起在错误流中发送到主机程序来显示。</span><span class="sxs-lookup"><span data-stu-id="4a813-111">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="4a813-112">若要编写非终止错误，请输入错误消息字符串、**ErrorRecord** 对象，或 **Exception** 对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-112">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="4a813-113">使用的其他参数 `Write-Error` 填充错误记录。</span><span class="sxs-lookup"><span data-stu-id="4a813-113">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="4a813-114">非终止错误将错误写入错误流，但它们不会停止命令处理。</span><span class="sxs-lookup"><span data-stu-id="4a813-114">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="4a813-115">如果在输入项的集合中的一个项上声明非终止错误，则该命令会继续处理集合中的其他项。</span><span class="sxs-lookup"><span data-stu-id="4a813-115">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="4a813-116">若要声明终止错误，请使用 `Throw` 关键字。</span><span class="sxs-lookup"><span data-stu-id="4a813-116">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="4a813-117">有关详细信息，请参阅 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)。</span><span class="sxs-lookup"><span data-stu-id="4a813-117">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="4a813-118">示例</span><span class="sxs-lookup"><span data-stu-id="4a813-118">EXAMPLES</span></span>

### <span data-ttu-id="4a813-119">示例1：为 RegistryKey 对象写入错误</span><span class="sxs-lookup"><span data-stu-id="4a813-119">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="4a813-120">当 `Get-ChildItem` cmdlet 返回 `Microsoft.Win32.RegistryKey` 对象（例如 `HKLM:` `HKCU:` PowerShell 注册表提供程序的或驱动器中的对象）时，此命令声明一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-120">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="4a813-121">示例2：将错误消息写入控制台</span><span class="sxs-lookup"><span data-stu-id="4a813-121">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="4a813-122">此命令声明一个非终止错误，并写入“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-122">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="4a813-123">此命令使用 **Message** 参数来指定消息，但省略可选的 **Message** 参数名称。</span><span class="sxs-lookup"><span data-stu-id="4a813-123">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="4a813-124">示例3：将错误写入控制台并指定类别</span><span class="sxs-lookup"><span data-stu-id="4a813-124">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="4a813-125">此命令声明一个非终止错误，并指定错误类别。</span><span class="sxs-lookup"><span data-stu-id="4a813-125">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="4a813-126">示例4：使用 Exception 对象编写错误</span><span class="sxs-lookup"><span data-stu-id="4a813-126">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="4a813-127">此命令使用 **Exception** 对象来声明一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-127">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="4a813-128">第一个命令使用哈希表来创建 **System.Exception** 对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-128">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="4a813-129">它将异常对象保存在 `$E` 变量中。</span><span class="sxs-lookup"><span data-stu-id="4a813-129">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="4a813-130">可以使用哈希表来创建具有空构造函数的类型的任何对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-130">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="4a813-131">第二个命令使用 `Write-Error` cmdlet 声明非终止错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-131">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="4a813-132">**Exception** 参数的值是变量中的 **异常** 对象 `$E` 。</span><span class="sxs-lookup"><span data-stu-id="4a813-132">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="4a813-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a813-133">PARAMETERS</span></span>

### <span data-ttu-id="4a813-134">-Category</span><span class="sxs-lookup"><span data-stu-id="4a813-134">-Category</span></span>

<span data-ttu-id="4a813-135">指定的错误类别。</span><span class="sxs-lookup"><span data-stu-id="4a813-135">Specifies the category of the error.</span></span> <span data-ttu-id="4a813-136">默认值为 **NotSpecified**。</span><span class="sxs-lookup"><span data-stu-id="4a813-136">The default value is **NotSpecified**.</span></span> <span data-ttu-id="4a813-137">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="4a813-137">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4a813-138">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="4a813-138">NotSpecified</span></span>
- <span data-ttu-id="4a813-139">OpenError</span><span class="sxs-lookup"><span data-stu-id="4a813-139">OpenError</span></span>
- <span data-ttu-id="4a813-140">CloseError</span><span class="sxs-lookup"><span data-stu-id="4a813-140">CloseError</span></span>
- <span data-ttu-id="4a813-141">DeviceError</span><span class="sxs-lookup"><span data-stu-id="4a813-141">DeviceError</span></span>
- <span data-ttu-id="4a813-142">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="4a813-142">DeadlockDetected</span></span>
- <span data-ttu-id="4a813-143">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="4a813-143">InvalidArgument</span></span>
- <span data-ttu-id="4a813-144">InvalidData</span><span class="sxs-lookup"><span data-stu-id="4a813-144">InvalidData</span></span>
- <span data-ttu-id="4a813-145">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="4a813-145">InvalidOperation</span></span>
- <span data-ttu-id="4a813-146">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="4a813-146">InvalidResult</span></span>
- <span data-ttu-id="4a813-147">InvalidType</span><span class="sxs-lookup"><span data-stu-id="4a813-147">InvalidType</span></span>
- <span data-ttu-id="4a813-148">MetadataError</span><span class="sxs-lookup"><span data-stu-id="4a813-148">MetadataError</span></span>
- <span data-ttu-id="4a813-149">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="4a813-149">NotImplemented</span></span>
- <span data-ttu-id="4a813-150">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="4a813-150">NotInstalled</span></span>
- <span data-ttu-id="4a813-151">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="4a813-151">ObjectNotFound</span></span>
- <span data-ttu-id="4a813-152">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="4a813-152">OperationStopped</span></span>
- <span data-ttu-id="4a813-153">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="4a813-153">OperationTimeout</span></span>
- <span data-ttu-id="4a813-154">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="4a813-154">SyntaxError</span></span>
- <span data-ttu-id="4a813-155">ParserError</span><span class="sxs-lookup"><span data-stu-id="4a813-155">ParserError</span></span>
- <span data-ttu-id="4a813-156">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="4a813-156">PermissionDenied</span></span>
- <span data-ttu-id="4a813-157">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="4a813-157">ResourceBusy</span></span>
- <span data-ttu-id="4a813-158">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="4a813-158">ResourceExists</span></span>
- <span data-ttu-id="4a813-159">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="4a813-159">ResourceUnavailable</span></span>
- <span data-ttu-id="4a813-160">ReadError</span><span class="sxs-lookup"><span data-stu-id="4a813-160">ReadError</span></span>
- <span data-ttu-id="4a813-161">WriteError</span><span class="sxs-lookup"><span data-stu-id="4a813-161">WriteError</span></span>
- <span data-ttu-id="4a813-162">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="4a813-162">FromStdErr</span></span>
- <span data-ttu-id="4a813-163">SecurityError</span><span class="sxs-lookup"><span data-stu-id="4a813-163">SecurityError</span></span>
- <span data-ttu-id="4a813-164">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="4a813-164">ProtocolError</span></span>
- <span data-ttu-id="4a813-165">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="4a813-165">ConnectionError</span></span>
- <span data-ttu-id="4a813-166">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="4a813-166">AuthenticationError</span></span>
- <span data-ttu-id="4a813-167">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="4a813-167">LimitsExceeded</span></span>
- <span data-ttu-id="4a813-168">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="4a813-168">QuotaExceeded</span></span>
- <span data-ttu-id="4a813-169">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="4a813-169">NotEnabled</span></span>

<span data-ttu-id="4a813-170">有关错误类别的信息，请参阅 [ErrorCategory 枚举](https://go.microsoft.com/fwlink/?LinkId=143600)。</span><span class="sxs-lookup"><span data-stu-id="4a813-170">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-171">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="4a813-171">-CategoryActivity</span></span>

<span data-ttu-id="4a813-172">指定导致错误的操作。</span><span class="sxs-lookup"><span data-stu-id="4a813-172">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-173">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="4a813-173">-CategoryReason</span></span>

<span data-ttu-id="4a813-174">指定活动导致错误的方式或原因。</span><span class="sxs-lookup"><span data-stu-id="4a813-174">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-175">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="4a813-175">-CategoryTargetName</span></span>

<span data-ttu-id="4a813-176">指定当发生错误时被处理的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="4a813-176">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-177">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="4a813-177">-CategoryTargetType</span></span>

<span data-ttu-id="4a813-178">指定当发生错误时被处理的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="4a813-178">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-179">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="4a813-179">-ErrorId</span></span>

<span data-ttu-id="4a813-180">指定 ID 字符串以标识错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-180">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="4a813-181">字符串应该是唯一的错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-181">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-182">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="4a813-182">-ErrorRecord</span></span>

<span data-ttu-id="4a813-183">指定一个表示错误的错误记录对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-183">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="4a813-184">使用对象的属性来描述错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-184">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="4a813-185">若要创建错误记录对象，请使用 `New-Object` cmdlet 或从自动变量中的数组获取错误记录对象 `$Error` 。</span><span class="sxs-lookup"><span data-stu-id="4a813-185">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-186">-Exception</span><span class="sxs-lookup"><span data-stu-id="4a813-186">-Exception</span></span>

<span data-ttu-id="4a813-187">指定一个表示错误的异常对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-187">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="4a813-188">使用对象的属性来描述错误。</span><span class="sxs-lookup"><span data-stu-id="4a813-188">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="4a813-189">若要创建异常对象，请使用哈希表或使用 `New-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a813-189">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-190">-Message</span><span class="sxs-lookup"><span data-stu-id="4a813-190">-Message</span></span>

<span data-ttu-id="4a813-191">指定错误的消息文本。</span><span class="sxs-lookup"><span data-stu-id="4a813-191">Specifies the message text of the error.</span></span> <span data-ttu-id="4a813-192">如果文本包含空格或特殊字符，则将其括在引号中。</span><span class="sxs-lookup"><span data-stu-id="4a813-192">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="4a813-193">还可以通过管道将消息字符串传递给 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="4a813-193">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-194">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="4a813-194">-RecommendedAction</span></span>

<span data-ttu-id="4a813-195">指定用户在解决或阻止错误时应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="4a813-195">Specifies the action that the user should take to resolve or prevent the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-196">-TargetObject</span><span class="sxs-lookup"><span data-stu-id="4a813-196">-TargetObject</span></span>

<span data-ttu-id="4a813-197">指定当发生错误时被处理的对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-197">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="4a813-198">输入对象、包含对象的变量或获取对象的命令。</span><span class="sxs-lookup"><span data-stu-id="4a813-198">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4a813-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a813-199">CommonParameters</span></span>

<span data-ttu-id="4a813-200">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4a813-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a813-201">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4a813-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a813-202">输入</span><span class="sxs-lookup"><span data-stu-id="4a813-202">INPUTS</span></span>

### <span data-ttu-id="4a813-203">System.String</span><span class="sxs-lookup"><span data-stu-id="4a813-203">System.String</span></span>

<span data-ttu-id="4a813-204">可以通过管道将包含错误消息的字符串传递给 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="4a813-204">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="4a813-205">输出</span><span class="sxs-lookup"><span data-stu-id="4a813-205">OUTPUTS</span></span>

### <span data-ttu-id="4a813-206">错误对象</span><span class="sxs-lookup"><span data-stu-id="4a813-206">Error object</span></span>

<span data-ttu-id="4a813-207">`Write-Error` 仅写入错误流。</span><span class="sxs-lookup"><span data-stu-id="4a813-207">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="4a813-208">它不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="4a813-208">It does not return any objects.</span></span>

## <span data-ttu-id="4a813-209">注释</span><span class="sxs-lookup"><span data-stu-id="4a813-209">NOTES</span></span>

<span data-ttu-id="4a813-210">`Write-Error` 不会更改自动变量的值 `$?` ，因此它不会指示终止错误情况。</span><span class="sxs-lookup"><span data-stu-id="4a813-210">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="4a813-211">若要通知终止错误，请使用 [$PSCmdlet ( # B1 ](/dotnet/api/system.management.automation.cmdlet.writeerror) 方法。</span><span class="sxs-lookup"><span data-stu-id="4a813-211">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="4a813-212">相关链接</span><span class="sxs-lookup"><span data-stu-id="4a813-212">RELATED LINKS</span></span>

[<span data-ttu-id="4a813-213">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4a813-213">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="4a813-214">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="4a813-214">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="4a813-215">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="4a813-215">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="4a813-216">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="4a813-216">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="4a813-217">Write-Host</span><span class="sxs-lookup"><span data-stu-id="4a813-217">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="4a813-218">Write-Output</span><span class="sxs-lookup"><span data-stu-id="4a813-218">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="4a813-219">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="4a813-219">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="4a813-220">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="4a813-220">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="4a813-221">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="4a813-221">Write-Warning</span></span>](Write-Warning.md)
