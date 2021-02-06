---
description: PowerShell 记录来自引擎、提供程序和 cmdlet 的内部操作。
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: e74e357d81eddf87ad27d023eb9a8ba2977156e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597653"
---
# <a name="about-logging-non-windows"></a>关于记录非 Windows

## <a name="short-description"></a>简短说明
PowerShell 记录来自引擎、提供程序和 cmdlet 的内部操作。

## <a name="long-description"></a>长说明

Powershell 日志详细信息。 例如，PowerShell 将记录启动和停止引擎以及启动和停止提供程序等操作。 它还将记录有关 PowerShell 命令的详细信息。

PowerShell 日志的位置取决于目标平台。 在 **Linux** 上，可以使用将 PowerShell 日志到 **syslog** 和 **rsyslog** 。 有关详细信息，请参阅 Linux 计算机的本地 `man` 页面。 在 **macOS** 上，使用 **os_log** 日志记录系统。 有关详细信息，请参阅 [os_log 开发人员文档](https://developer.apple.com/documentation/os/os_log)。

## <a name="viewing-powershell-log-output-on-linux"></a>在 Linux 上查看 PowerShell 日志输出

可以使用 Linux 上 **syslog** 中的日志以及通常用于查看 **syslog** 内容的任何工具。

日志条目的格式使用以下模板：

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|字段        |说明                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |生成日志条目的日期/时间。            |
|`MACHINENAME`|生成日志的系统的名称。      |
|`PID`        |写入日志项的进程的进程 ID。 |
|`COMMITID`   |`git commit`用于生成生成的 ID 或标记。   |
|`TID`        |写入日志项的线程的线程 ID。   |
|`CID`        |日志条目的十六进制通道标识符。            |
|             |10 = 操作，11 = 分析                         |
|`EVENTID`    |日志条目的事件标识符。                  |
|`TASK`       |事件项的任务标识符                 |
|`OPCODE`     |事件项的操作码                          |
|`LEVEL`      |事件项的日志级别                       |
|`MESSAGE`    |与事件项关联的消息             |

> [!NOTE]
> `EVENTID`、 `TASK` 、 `OPCODE` 和与 `LEVEL` 日志记录到 Windows 事件日志时使用的值相同。

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>使用 rsyslog 筛选 PowerShell 日志条目

通常情况下，会将 PowerShell 日志条目写入 `location/file` **syslog** 的默认值。 但是，可以将条目重定向到自定义文件。

1. 为 PowerShell 日志配置创建会议，并为) 提供小于 50 (的数字 `50-default.conf` ，如 `40-powershell.conf` 。 文件应位于下 `/etc/rsyslog.d` 。

1. 将以下条目添加到文件：

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. 请确保 `/etc/rsyslog.conf` 包含新的文件。 通常，它将具有如下所示的一般包含语句：

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   如果不是，则需要手动添加 include 语句。

1. 请确保正确设置属性和权限。

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. 将所有权设置为 **root**。

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. 设置访问权限： **root** 具有读/写权限， **用户** 已读取。

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>查看 macOS 上的 PowerShell 日志输出

在 macOS 上查看 PowerShell 日志输出的最简单方法是使用 **控制台** 应用程序。

1. 搜索 **控制台** 应用程序并启动它。
1. 在 " **设备**" 下选择计算机名称。
1. 在 **搜索** 字段中， `pwsh` 为 PowerShell 主二进制文件输入。
1. 将搜索筛选器从更改 `Any` 为 `Process` 。
1. 执行操作。
1. 还可以选择保存搜索以便将来使用。

若要在 **控制台** 中筛选 PowerShell 的特定进程实例，该变量 `$pid` 包含进程 ID。

1. 在 **搜索** 字段中输入 **PID** (进程 ID) 。
1. 将搜索筛选器更改为 `PID` 。
1. 执行操作。

### <a name="viewing-powershell-log-output-from-a-command-line"></a>从命令行查看 PowerShell 日志输出

`log`命令可用于从命令行查看 PowerShell 日志条目。

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>保留 PowerShell 日志输出

默认情况下，PowerShell 使用 macOS 上默认的仅内存日志记录。 此行为可以更改为使用命令启用持久性 `log config` 。

以下脚本启用信息级别的日志记录和持久性：

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

以下命令将 PowerShell 日志记录还原为默认状态：

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

启用持久性后， `log show` 可以使用命令来导出日志项。 此命令提供用于导出最后 N 项、自给定时间之后的项或给定时间跨度内的项的选项。

例如，以下命令导出后的项 `9am on April 5 of 2018` ：

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

可以 `log` 通过运行来获取有关 `log show --help` 更多详细信息的帮助。

> [!TIP]
> 在 PowerShell 提示符或脚本中执行任何日志命令时，请使用双引号将整个谓词字符串和内的单引号括起来。 这样就无需在谓词字符串中转义双引号字符。

你可能还需要考虑将事件日志保存到更安全的位置，例如中央事件日志收集器或 [SIEM][] 聚合器。 可以在 Azure 中设置 SIEM。 有关详细信息，请参阅 [通用 SIEM 集成](/cloud-app-security/siem)。

## <a name="configuring-logging-on-a-non-windows-system"></a>在非 Windows 系统上配置日志记录

在 Windows 上，通过创建 ETW 跟踪侦听器或使用事件查看器启用分析日志记录来配置日志记录。 在 Linux 和 macOS 上，使用文件配置日志记录 `powershell.config.json` 。 本部分的其余部分将讨论如何在非 Windows 系统上配置 PowerShell 日志记录。

默认情况下，PowerShell 启用到操作通道的信息日志记录。 这意味着 PowerShell 生成的任何日志输出都标记为操作，并且将记录一个大于信息性的日志 (跟踪) 级别。 有时，诊断可能需要额外的日志输出，例如详细日志输出或启用分析日志输出。

文件 `powershell.config.json` 是驻留在 PowerShell 目录中的 **JSON** 格式的文件 `$PSHOME` 。 每个 PowerShell 安装都使用其自己的此文件的副本。 对于正常操作，此文件保持不变。 尽管它可能很有用，但要更改文件中的某些设置，以便进行诊断或区分同一系统上的多个 PowerShell 版本，甚至区分同一版本的多个副本 (参阅 `LogIdentity` 下表中的) 。

下面的代码是一个示例配置：

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

下表列出了用于配置 PowerShell 日志记录的属性。 用星号标记的值（如 `Operational*` ）在文件中未提供任何值时指示默认值。

|属性   |值        |说明                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`| (字符串名称)  |要在日志记录时使用的名称。 默认情况下，  |
|           |powershell   |powershell 是标识。 此值可以是|
|           |              |用于说明两个      |
|           |              |PowerShell 安装的实例，例如 |
|           |              |作为发布和 beta 版本。 此值为 |
|           |              |还用于将日志输出重定向到        |
|           |              |Linux 上的单独文件。 请参阅|
|           |              |**rsyslog** 。                           |
|`LogChannels`|营业  |要启用的通道。 分隔值|
|           |分析      |指定多个时使用逗号。  |
|`LogLevel`   |Always        |指定单个值。 该值启用  |
|           |严重      |本身以及它上面的所有值        |
|           |错误         |向左列出。                            |
|           |警告       |                                             |
|           |条|                                             |
|           |详细       |                                             |
|           |调试         |                                             |
|`LogKeywords`|Runspace      |关键字提供限制日志记录的功能|
|           |管道      |PowerShell 中的特定组件。 通过 |
|           |协议      |默认情况下，将启用并更改所有关键字 |
|           |Transport     |此值仅适用于           |
|           |主机          |专用故障排除。                |
|           |Cmdlet       |                                             |
|           |序列化程序    |                                             |
|           |会话       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>请参阅

有关 Linux **syslog** 和 **rsyslog** 信息，请参阅 linux 计算机的本地 `man` 页面。

有关 macOS **os_log** 信息，请参阅 [os_log 开发人员文档](https://developer.apple.com/documentation/os/os_log)。

[about_Logging_Windows](about_Logging_Windows.md)

[通用 SIEM 集成](/cloud-app-security/siem)

<!-- link references -->
SIEM
