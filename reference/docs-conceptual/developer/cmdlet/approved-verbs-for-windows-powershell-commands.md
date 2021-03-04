---
ms.date: 03/01/2021
ms.topic: reference
title: PowerShell 命令的已批准谓词
description: PowerShell 命令的已批准谓词
ms.openlocfilehash: 277472f141eb1ef2b7b0f19801c622a899e93665
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686075"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 命令的已批准谓词

PowerShell 对 cmdlet 的名称及其派生的 .NET 类使用谓词-名词对。
名称的谓词部分标识 cmdlet 执行的操作。 名称的名词部分标识在其中执行操作的实体。 例如，`Get-Command` cmdlet 可检索在 PowerShell 中注册的所有命令。

> [!NOTE]
> PowerShell 使用“谓词”一词来描述某个表示动作的单词，即使该词并不是英语中的标准谓词。 例如，“New”一词是有效的 PowerShell 谓词名称，因为它表示某个动作，而该词在英语中并不是谓词。

每个已批准谓词都定义了相应的别名前缀。 我们会对使用该谓词的命令使用别名中的这一别名前缀。 例如，`Import` 的别名前缀为 `ip`，相应地，`Import-Module` 的别名为 `ipmo`。 这是一种建议，并不是规则；特别是对于模仿其他环境中的常见命令的命令别名，无需遵守该建议。

## <a name="verb-naming-recommendations"></a>谓词命名建议

以下建议有助于为 cmdlet 选择适当的谓词，以确保你创建的 cmdlet、PowerShell 提供的 cmdlet 和其他人设计的 cmdlet 一致。

- 使用 PowerShell 提供的某一个预定义谓词名称
- 使用谓词描述操作的一般范围，然后使用参数进一步优化 cmdlet 的操作。
- 请勿使用已批准谓词的同义词。 例如，始终使用 `Remove`，切勿使用 `Delete` 或 `Eliminate`。
- 仅使用本主题中列出的每个谓词的形式。 例如，使用 `Get`，不要使用 `Getting` 或 `Gets`。
- 请勿使用以下预留谓词或别名。 在特殊情况下，PowerShell 语言或其少数 cmdlet 会使用这些谓词。
  - ForEach (foreach)
  - [Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)：以指定的形式或布局排列对象
  - [Group](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)：排列或关联一种或多种资源
  - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)
  - Sort (sr)
  - Tee (te)
  - Where (wh)

可以使用 `Get-Verb` cmdlet 获取谓词的完整列表。

## <a name="similar-verbs-for-different-actions"></a>不同操作的类似谓词

以下类似谓词表示不同的操作。

### <a name="new-vs-set"></a>New 与设置

使用谓词 `New` 新建资源。 使用谓词 `Set` 修改现有资源，如果没有现有资源，可以选择创建一个，例如 `Set-Variable` cmdlet。

### <a name="find-vs-search"></a>Find 与搜索

使用谓词 `Find` 查找对象。 使用谓词 `Search` 创建对容器中资源的引用。

### <a name="get-vs-read"></a>Get 与读取

使用谓词 `Get` 获取资源（例如文件）相关信息，或获取用于后续访问该资源的对象。 使用谓词 `Read` 打开资源并提取其中包含的信息。

### <a name="invoke-vs-start"></a>Invoke 与开始

使用谓词 `Invoke` 执行同步操作，例如运行命令并等待命令结束。 使用 `Start` 谓词开始异步操作，如启动自治进程。

### <a name="ping-vs-test"></a>Ping 与测试

使用谓词 `Test`。

## <a name="common-verbs"></a>常用谓词

PowerShell 使用 [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) 枚举类来定义可应用于几乎所有 cmdlet 的常规操作。 下表列出了大多数已定义谓词。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|将资源添加到容器，或将某一项附加到另一个项。 例如，`Add-Content` cmdlet 可向文件添加内容。 该谓词与 `Remove` 成对。|Append、Attach、Concatenate、Insert|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|删除容器中的所有资源，但不删除容器。 例如，`Clear-Content` cmdlet 可删除文件的内容，但不删除文件。|Flush、Erase、Release、Unmark、Unset、Nullify|
|[Close](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|更改资源的状态，使其不可访问、不适用或不可用。 该谓词与 `Open.` 成对||
|[Copy](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|将资源复制到另一个名称或另一个容器。 例如，`Copy-Item` cmdlet 将项（如文件）从数据存储中的一个位置复制到另一个位置。|Duplicate、Clone、Replicate、Sync|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|指定可让用户移动到资源中的操作。 例如，`Enter-PSSession` cmdlet 将用户置于交互式会话中。 该谓词与 `Exit` 成对。|Push、Into|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|将当前环境或上下文设置为最近使用的上下文。 例如，`Exit-PSSession` cmdlet 将用户置于用于启动交互式会话的会话中。 该谓词与 `Enter` 成对。|Pop、Out|
|[Find](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|查找容器中未知、隐含、可选或指定的对象。|搜索|
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|指定可检索资源的操作。 该谓词与 `Set` 成对。|Read、Open、Cat、Type、Dir、Obtain、Dump、Acquire、Examine、Find、Search|
|[Hide](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|使资源不可检测。 例如，名称包含谓词“Hide”的 cmdlet 可能会对用户隐藏服务。 该谓词与 `Show` 成对。|阻止|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|将多种资源合并为一种资源。 例如，`Join-Path` cmdlet 将路径与其某一子路径合并为一个路径。 该谓词与 `Split` 成对。|Combine、Unite、Connect、Associate|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|保护资源。 该谓词与 `Unlock` 成对。|Restrict、Secure|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|将资源从一个位置移动到另一个位置。 例如，`Move-Item` cmdlet 将项从数据存储中的一个位置移动到另一个位置。|Transfer、Name、Migrate|
|[New](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|创建资源。 （创建包含 `Set-Variable` cmdlet 等数据的资源时，也可以使用谓词 `Set`。）|Create、Generate、Build、Make、Allocate|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|更改资源的状态，使其可访问、适用或可用。 该谓词与 `Close` 成对。||
|[Optimize](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|提高资源的有效性。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|从堆栈顶部删除某一项。 例如，`Pop-Location` cmdlet 将当前位置更改为最近推入到堆栈中的位置。||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|向堆栈顶部添加某一项。 例如，`Push-Location` cmdlet 将当前位置推入到堆栈中。||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|将资源重置为撤消的状态。||
|[Remove](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|从容器中删除资源。 例如，`Remove-Variable` cmdlet 可删除变量及其值。 该谓词与 `Add` 成对。|Clear、Cut、Dispose、Discard、Erase|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|更改资源的名称。 例如，用于访问存储数据的 `Rename-Item` cmdlet 可更改数据存储中项的名称。|更改|
|[Reset](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|将资源设置回其初始状态。||
|[Resize](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(rz)|更改资源大小。||
|[Search](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|创建对容器中资源的引用。|Find、Locate|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|查找容器中的资源。 例如，`Select-String` cmdlet 可查找字符串和文件中的文本。|Find、Locate|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|替换现有资源上的数据或创建包含某些数据的资源。 例如，`Set-Date` cmdlet 可更改本地计算机上的系统时间。 （谓词 `New` 还可用于创建资源。）该谓词与 `Get` 成对。|Write、Reset、Assign、Configure|
|[Show](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|使资源对用户可见。 该谓词与 `Hide` 成对。|Display、Produce|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|绕过序列中的一个或多个资源或点。|Bypass、Jump|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|分离资源的各个部分。 例如，`Split-Path` cmdlet 可返回路径的不同部分。 该谓词与 `Join` 成对。|独立|
|[Step](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|移动到序列中的下一个点或资源。||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|指定在两种资源之间切换的操作，例如在两个位置、职责或状态之间进行切换。||
|[Undo](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|将资源设置为其以前的状态。||
|[Unlock](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (uk)|释放锁定的资源。 该谓词与 `Lock` 成对。|Release、Unrestrict、Unsecure|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|持续检查或监视资源是否发生更改。||

## <a name="communications-verbs"></a>通信谓词

PowerShell 使用 [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) 类来定义适用于通信的操作。 下表列出了大多数已定义谓词。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|在源和目标之间创建链接。 该谓词与 `Disconnect` 成对。|Join、Telnet|
|[Disconnect](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|断开源和目标之间的链接。 该谓词与 `Connect` 成对。|Break、Logoff|
|[Read](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|从源获取信息。 该谓词与 `Write` 成对。|Acquire、Prompt、Get|
|[Receive](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|接受从源发送的信息。 该谓词与 `Send` 成对。|Read、Accept、Peek|
|[Send](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|将信息传递到目标。 该谓词与 `Receive` 成对。|Put、Broadcast、Mail、Fax|
|[Write](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|向目标添加信息。 该谓词与 `Read` 成对。|Put、Print|

## <a name="data-verbs"></a>数据谓词

PowerShell 使用 [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) 类来定义适用于数据处理的操作。 下表列出了大多数已定义谓词。

|谓词名称（别名）|操作|要避免的同义词|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|通过复制数据来存储数据。|Save、Burn、Replicate、Sync|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|创建数据当前状态的快照或数据配置的快照。|差异|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|根据某一资源中的数据评估另一资源中的数据。|差异|
|[Compress](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|压缩资源的数据。 与 `Expand` 成对。|精简|
|[Convert](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|cmdlet 支持双向转换或 cmdlet 支持多种数据类型之间的转换时，将数据从一种表示形式更改为另一种表示形式。|Change、Resize、Resample|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|将一种主要的输入类型（cmdlet 名词表示输入）转换为一种或多种支持的输出类型。|Export、Output、Out|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|从一种或多种类型的输入转换为主要的输出类型（cmdlet 名词表示输出类型）。|Import、Input、In|
|[Dismount](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|从位置拆离命名实体。 该谓词与 `Mount` 成对。|Unmount、Unlink|
|[Edit](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|通过添加或删除内容来修改现有数据。|Change、Update、Modify|
|[Expand](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|将已压缩的资源的数据还原到其初始状态。 该谓词与 `Compress` 成对。|Explode、Uncompress|
|[Export](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|将主要输入封装到永久性数据存储（例如文件），或封装为交换格式。 该谓词与 `Import` 成对。|Extract、Backup|
|[Import](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|从永久性数据存储（例如文件）中存储的或以交换格式存储的数据创建资源。 例如，`Import-CSV` cmdlet 将数据从逗号分隔值 (CSV) 文件导入到其他 cmdlet 可以使用的对象。 该谓词与 `Export` 成对。|BulkLoad、Load|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|准备要使用的资源，并将其设置为默认状态。|Erase、Init、Renew、Rebuild、Reinitialize、Setup|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|对资源应用约束。|Quota|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|根据多个资源创建一个资源。|Combine、Join|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|将命名实体附加到某一位置。 该谓词与 `Dismount` 成对。|连接|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|将数据发送到环境之外。 例如，`Out-Printer` cmdlet 将数据发送到打印机。||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|使资源可供他人使用。 该谓词与 `Unpublish` 成对。|Deploy、Release、Install|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|将资源设置为预定义状态，例如 `Checkpoint` 设置的状态。 例如，`Restore-Computer` cmdlet 可在本地计算机上启动系统还原。|Repair、Return、Undo、Fix|
|[Save](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|保留数据以免丢失。||
|[Sync](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|确保两种及以上的资源处于相同状态。|Replicate、Coerce、Match|
|[Unpublish](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|使资源不可供他人使用。 该谓词与 `Publish` 成对。|Uninstall、Revert、Hide|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|将资源更新为最新内容，以保持其状态、准确性、一致性或合规性。 例如，`Update-FormatData` cmdlet 会更新格式化文件并将其添加到当前的 PowerShell 控制台。|Refresh、Renew、Recalculate、Re-index|

## <a name="diagnostic-verbs"></a>诊断谓词

PowerShell 使用 [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) 类来定义适用于诊断的操作。 下表列出了大多数已定义谓词。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|检查资源以诊断操作问题。|诊断|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|标识指定操作使用的资源，或检索关于资源的统计信息。|Calculate、Determine、Analyze|
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|将资源还原为可用状态|Fix、Restore|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|将资源的简略表示形式映射为更完整的表示形式。|Expand、Determine|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|验证资源的操作或一致性。|Diagnose、Analyze、Salvage、Verify|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|跟踪资源的活动。|Track、Follow、Inspect、Dig|

## <a name="lifecycle-verbs"></a>生命周期谓词

PowerShell 使用 [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 类来定义适用于资源生命周期的操作。 下表列出了大多数已定义谓词。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Approve](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|确认或同意资源或进程的状态。||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|确认资源的状态。|Certify|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|根据某一组输入文件（通常是源代码或声明性文件）创建项目（通常是二进制文件或文档）。该谓词是在 PowerShell 6 中添加的。||
|[Complete](/dotnet/api/system.management.automation.host.buffercelltype) (cp)|结束操作。||
|[Confirm](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|确认、证实或验证资源或进程的状态。|Acknowledge、Agree、Certify、Validate、Verify|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|拒绝、反对、阻止或抵制资源或进程的状态。|Block、Object、Refuse、Reject|
|[Deploy](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|将应用程序、网站或解决方案发送到远程目标，以便解决方案的使用者可以在部署完成后对其进行访问。 该谓词是在 PowerShell 6 中添加的。||
|[Disable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|将资源配置为不可用或非活动状态。 例如，`Disable-PSBreakpoint` cmdlet 使断点处于非活动状态。 该谓词与 `Enable` 成对。|Halt、Hide|
|[Enable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|将资源配置为可用或活动状态。 例如，`Enable-PSBreakpoint` cmdlet 使断点处于活动状态。 该谓词与 `Disable` 成对。|Start、Begin|
|[Install](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|将资源置于某个位置，并根据需要对其进行初始化。 该谓词与 `Uninstall` 成对。|设置|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|执行操作，例如运行命令或方法。|Run、Start|
|[Register](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|为存储库（例如数据库）中的资源创建一个条目。 该谓词与 `Unregister` 成对。||
|[Request](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|请求提供资源或请求权限。||
|[Restart](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|停止操作，然后再次启动。 例如，`Restart-Service` cmdlet 可停止服务，然后再次启动。|再循环|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|启动已挂起的操作。 例如，`Resume-Service` cmdlet 可启动已暂停的服务。 该谓词与 `Suspend` 成对。||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|启动操作。 例如，`Start-Service` cmdlet 可启动服务。 该谓词与 `Stop` 成对。|Launch、Initiate、Boot|
|[Stop](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|停止活动。 该谓词与 `Start` 成对。|End、Kill、Terminate、Cancel|
|[Submit](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|显示待审批的资源。|邮递|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|暂停活动。 例如，`Suspend-Service` cmdlet 可暂停服务。 该谓词与 `Resume` 成对。|暂停|
|[Uninstall](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|从指示的位置删除资源。 该谓词与 `Install` 成对。||
|[Unregister](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (ur)|从存储库中删除资源的条目。 该谓词与 `Register` 成对。|删除|
|[Wait](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|暂停操作，直到指定的事件发生。 例如，`Wait-Job` cmdlet 可暂停操作，直到一个或多个后台作业完成为止。|Sleep、Pause|

## <a name="security-verbs"></a>安全性谓词

PowerShell 使用 [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) 类来定义适用于安全性的操作。 下表列出了大多数已定义谓词。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|限制对资源的访问。 该谓词与 `Unblock` 成对。|Prevent、Limit、Deny|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|允许对资源的访问。 该谓词与 `Revoke` 成对。|Allow、Enable|
|[Protect](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|保护资源，以免受攻击或损失。 该谓词与 `Unprotect` 成对。|Encrypt、Safeguard、Seal|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|指定不允许访问资源的操作。 该谓词与 `Grant` 成对。|Remove、Disable|
|[Unblock](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|删除对资源的限制。 该谓词与 `Block` 成对。|Clear、Allow|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|从资源中删除为免受攻击或损失而添加的保护措施。 该谓词与 `Protect` 成对。|Decrypt、Unseal|

## <a name="other-verbs"></a>其他谓词

PowerShell 使用 [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) 类来定义不适合特定谓词名称类别（例如常用谓词、通信谓词、数据谓词、生命周期谓词或安全性谓词名称谓词）的规范谓词名称。

|谓词（别名）|操作|要避免的同义词|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|使用或加入资源以执行某些操作。||

## <a name="see-also"></a>另请参阅

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [Cmdlet 声明](./cmdlet-class-declaration.md)
- [Windows PowerShell 程序员指南](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Windows PowerShell Shell SDK](../windows-powershell-reference.md)
