---
title: 在 macOS 上安装 PowerShell
description: 介绍如何在 macOS 上安装 PowerShell
ms.date: 02/02/2021
ms.openlocfilehash: 3ae1fe0eb29b4d826221a2c11db19bc18c3efba7
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563209"
---
# <a name="installing-powershell-on-macos"></a>在 macOS 上安装 PowerShell

PowerShell 7.0 或更高版本需要 macOS 10.13 或更高版本。 GitHub [版本][]页面上提供有所有可用包。 安装包以后，从终端运行 `pwsh`。

> [!NOTE]
> PowerShell 7.1 是就地升级，升级后会删除 PowerShell Core 6.x 和 7.0。
>
> `/usr/local/microsoft/powershell/6` 文件夹被替换为 `/usr/local/microsoft/powershell/7`。
>
> 如果需要使用 PowerShell 7.1 并行运行 PowerShell Core 的更早版本，请使用[二进制存档](#binary-archives)方法安装所需的版本。

可采用多种方法在 macOS 上安装 PowerShell。 选择下列方法之一：

- 使用 Homebrew 安装。 Homebrew 是 macOS 的首选包管理器。
- 通过[直接下载](#installation-via-direct-download)安装 PowerShell
- 从[二进制存档](#binary-archives)安装

安装 PowerShell 后，应安装 [OpenSSL](#installing-dependencies)。 PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>通过 Homebrew 在 macOS 10.13 或更高版本上安装最新的稳定版本

如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。

现在，可以开始安装 PowerShell：

```sh
brew install --cask powershell
```

最后，验证安装是否正常运行：

```sh
pwsh
```

PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> 可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 `$PSVersionTable` 中显示的值。

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>通过 Homebrew 在 macOS 10.13 或更高版本上安装最新的预览版

安装 Homebrew 后，可以安装 PowerShell。 首先，安装 [Cask-Versions ][cask-versions] 包，通过它可安装替代版本的 cask 包：

```sh
brew tap homebrew/cask-versions
```

现在，可以开始安装 PowerShell：

```sh
brew install --cask powershell-preview
```

最后，验证安装是否正常运行：

```sh
pwsh-preview
```

PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> 可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。
> 然后刷新 `$PSVersionTable` 中显示的值。

稳定版本和 LTS 版本也支持使用 Homebrew tap 方法安装 PowerShell。

```sh
brew install powershell/tap/powershell
```

现在可以验证你的安装

```sh
pwsh
```

发布新版本的 PowerShell 时，只需运行以下命令即可。

```sh
brew upgrade powershell
```

> [!NOTE]
> 无论使用 cask 还是 tap 方法，在更新到较新版本的 PowerShell 时，请使用最初安装 PowerShell 所使用的相同方法。 如果使用其他方法，则打开新的 pwsh 会话时将继续使用较旧版本的 PowerShell。
>
> 如果决定使用其他方法，可以使用 [Homebrew link 方法](https://docs.brew.sh/Manpage#link-ln-options-formula)来解决此问题。

## <a name="installation-via-direct-download"></a>通过直接下载安装

请从[版本][]页中将 PKG 包 `powershell-7.1.2-osx-x64.pkg` 下载到 CentOS 计算机。

可以双击文件并按照提示操作，或者从终端安装：

```sh
sudo installer -pkg powershell-7.1.2-osx-x64.pkg -target /
```

安装 [OpenSSL](#installing-dependencies). PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

## <a name="install-as-a-net-global-tool"></a>作为 .NET 全局工具安装

如果你已安装 [.NET Core SDK](/dotnet/core/sdk)，则可以轻松地安装 PowerShell 作为 [.NET 全局工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

dotnet 工具安装程序将 `~/.dotnet/tools` 添加到 `PATH` 环境变量中。 但是，当前运行的 shell 没有更新的 `PATH`。 应该可以通过键入 `pwsh` 从新 shell 启动 PowerShell。

安装 [OpenSSL](#installing-dependencies). PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

## <a name="binary-archives"></a>二进制存档

已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。 使用此方法安装时，还必须手动安装所有依赖项。

安装 [OpenSSL](#installing-dependencies). PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

### <a name="installing-binary-archives-on-macos"></a>在 macOS 上安装二进制存档

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.2/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>安装依赖关系

PowerShell 远程处理和 CIM 操作均需要 OpenSSL。 如有需要，可通过 MacPorts 安装 OpenSSL。

> [!NOTE]
> 在同一系统上使用 MacPorts 和 Homebrew 时可能会出现问题。 但是，Homebrew 没有适用于 OpenSSL 1.0 的包。 有关详细信息，请参阅 [MacPorts 常见问题解答](https://trac.macports.org/wiki/FAQ)。

1. 安装 Xcode 命令行工具。 MacPorts 需要 Xcode 工具。

   ```sh
   xcode-select --install
   ```

1. 安装 MacPorts。 如需说明，请参阅[安装指南](https://www.macports.org/install.php)。
1. 通过运行 `sudo port selfupdate` 更新 MacPorts。
1. 通过运行 `sudo port upgrade outdated` 升级 MacPorts 包。
1. 通过运行 `sudo port install openssl10` 安装 OpenSSL。
1. 链接库，使其可供 PowerShell 使用：

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a>卸载 PowerShell

如果使用 Homebrew 安装 PowerShell，请使用以下命令进行卸载：

```sh
brew cask uninstall powershell
```

如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除路径。

> [!NOTE]
> 如果使用 Homebrew 安装，则此步骤并非必要步骤。

## <a name="paths"></a>路径

- `$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.2/`
- 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
- 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
- 将从 `~/.local/share/powershell/Modules` 中读取用户模块
- 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
- 将从 `$PSHOME/Modules` 中读取默认模块
- PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的每个主机配置。 因此主机特定的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。

由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。 因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.2/`，且符号链接位于 `/usr/local/bin/pwsh` 中。

## <a name="installation-support"></a>安装支持

Microsoft 支持本文档中的安装方法。 其他源可能会提供其他安装方法。 尽管这些工具和方法可能有效，但 Microsoft 无法支持这些方法。

## <a name="additional-resources"></a>其他资源

- [Homebrew Web][brew]
- [Homebrew Github 存储库][GitHub]
- [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
