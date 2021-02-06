---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597039"
---
# PSConsoleHostReadLine

## 摘要
此函数是 PSReadLine 的主要入口点。

## SYNTAX

```
PSConsoleHostReadLine
```

## DESCRIPTION

`PSConsoleHostReadLine` 是 PSReadLine 模块的主入口点。 PowerShell 控制台主机会自动加载 PSReadLine 模块并调用此函数。 在正常操作情况下，不应从命令行使用此函数。

扩展点 `PSConsoleHostReadLine` 对于控制台主机是特殊的。 主机将调用具有此名称的任何别名、函数或脚本。 PSReadLine 定义此函数，使其从控制台主机调用。

## 示例

### 示例 1

不应从命令行使用此函数。

## PARAMETERS

## 输入

### 无

## 输出

### 无

## 注释

## 相关链接

[about_PSReadLine](./About/about_PSReadLine.md)

