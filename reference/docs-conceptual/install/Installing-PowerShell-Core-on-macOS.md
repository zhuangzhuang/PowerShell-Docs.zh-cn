---
title: 在 macOS 上安装 PowerShell
description: 介绍如何在 macOS 上安装 PowerShell
ms.date: 02/02/2021
ms.openlocfilehash: 8132d88f4104696c5580a44b26247a24643f1b5b
ms.sourcegitcommit: 40b6d8e9b6d791ac69e2ff85224e900b21552bc1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2021
ms.locfileid: "99536537"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="52c7d-103">在 macOS 上安装 PowerShell</span><span class="sxs-lookup"><span data-stu-id="52c7d-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="52c7d-104">PowerShell 7.0 或更高版本需要 macOS 10.13 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="52c7d-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="52c7d-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="52c7d-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="52c7d-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="52c7d-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="52c7d-107">PowerShell 7.1 是就地升级，升级后会删除 PowerShell Core 6.x 和 7.0。</span><span class="sxs-lookup"><span data-stu-id="52c7d-107">PowerShell 7.1 is an in-place upgrade that removes PowerShell Core 6.x and 7.0.</span></span>
>
> <span data-ttu-id="52c7d-108">`/usr/local/microsoft/powershell/6` 文件夹被替换为 `/usr/local/microsoft/powershell/7`。</span><span class="sxs-lookup"><span data-stu-id="52c7d-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="52c7d-109">如果需要使用 PowerShell 7.1 并行运行 PowerShell Core 的更早版本，请使用[二进制存档](#binary-archives)方法安装所需的版本。</span><span class="sxs-lookup"><span data-stu-id="52c7d-109">If you need to run and older version of PowerShell core side-by-side with PowerShell 7.1, install the version you want using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="52c7d-110">可采用多种方法在 macOS 上安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52c7d-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="52c7d-111">选择下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="52c7d-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="52c7d-112">使用 Homebrew 安装。</span><span class="sxs-lookup"><span data-stu-id="52c7d-112">Install using Homebrew.</span></span> <span data-ttu-id="52c7d-113">Homebrew 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="52c7d-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="52c7d-114">通过[直接下载](#installation-via-direct-download)安装 PowerShell</span><span class="sxs-lookup"><span data-stu-id="52c7d-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="52c7d-115">从[二进制存档](#binary-archives)安装</span><span class="sxs-lookup"><span data-stu-id="52c7d-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="52c7d-116">安装 PowerShell 后，应安装 [OpenSSL](#installing-dependencies)。</span><span class="sxs-lookup"><span data-stu-id="52c7d-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="52c7d-117">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="52c7d-118">通过 Homebrew 在 macOS 10.13 或更高版本上安装最新的稳定版本</span><span class="sxs-lookup"><span data-stu-id="52c7d-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="52c7d-119">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="52c7d-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="52c7d-120">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52c7d-120">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell
```

<span data-ttu-id="52c7d-121">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="52c7d-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="52c7d-122">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52c7d-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="52c7d-123">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="52c7d-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="52c7d-124">通过 Homebrew 在 macOS 10.13 或更高版本上安装最新的预览版</span><span class="sxs-lookup"><span data-stu-id="52c7d-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="52c7d-125">安装 Homebrew 后，可以安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52c7d-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="52c7d-126">首先，安装 [Cask-Versions ][cask-versions] 包，通过它可安装替代版本的 cask 包：</span><span class="sxs-lookup"><span data-stu-id="52c7d-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="52c7d-127">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52c7d-127">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell-preview
```

<span data-ttu-id="52c7d-128">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="52c7d-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="52c7d-129">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52c7d-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="52c7d-130">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="52c7d-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="52c7d-131">然后刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="52c7d-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="52c7d-132">稳定版本和 LTS 版本也支持使用 Homebrew tap 方法安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52c7d-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="52c7d-133">现在可以验证你的安装</span><span class="sxs-lookup"><span data-stu-id="52c7d-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="52c7d-134">发布新版本的 PowerShell 时，只需运行以下命令即可。</span><span class="sxs-lookup"><span data-stu-id="52c7d-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="52c7d-135">无论使用 cask 还是 tap 方法，在更新到较新版本的 PowerShell 时，请使用最初安装 PowerShell 所使用的相同方法。</span><span class="sxs-lookup"><span data-stu-id="52c7d-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="52c7d-136">如果使用其他方法，则打开新的 pwsh 会话时将继续使用较旧版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52c7d-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="52c7d-137">如果决定使用其他方法，可以使用 [Homebrew link 方法](https://docs.brew.sh/Manpage#link-ln-options-formula)来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="52c7d-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="52c7d-138">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="52c7d-138">Installation via Direct Download</span></span>

<span data-ttu-id="52c7d-139">请从[版本][]页中将 PKG 包 `powershell-7.1.1-osx-x64.pkg` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="52c7d-139">Download the PKG package `powershell-7.1.1-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="52c7d-140">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="52c7d-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-7.1.1-osx-x64.pkg -target /
```

<span data-ttu-id="52c7d-141">安装 [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="52c7d-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="52c7d-142">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="52c7d-143">作为 .NET 全局工具安装</span><span class="sxs-lookup"><span data-stu-id="52c7d-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="52c7d-144">如果你已安装 [.NET Core SDK](/dotnet/core/sdk)，则可以轻松地安装 PowerShell 作为 [.NET 全局工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="52c7d-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="52c7d-145">dotnet 工具安装程序将 `~/.dotnet/tools` 添加到 `PATH` 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="52c7d-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="52c7d-146">但是，当前运行的 shell 没有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="52c7d-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="52c7d-147">应该可以通过键入 `pwsh` 从新 shell 启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52c7d-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="52c7d-148">安装 [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="52c7d-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="52c7d-149">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="52c7d-150">二进制存档</span><span class="sxs-lookup"><span data-stu-id="52c7d-150">Binary Archives</span></span>

<span data-ttu-id="52c7d-151">已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="52c7d-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="52c7d-152">使用此方法安装时，还必须手动安装所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="52c7d-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="52c7d-153">安装 [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="52c7d-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="52c7d-154">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="52c7d-155">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="52c7d-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.1/powershell-7.1.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.1/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="52c7d-156">安装依赖关系</span><span class="sxs-lookup"><span data-stu-id="52c7d-156">Installing dependencies</span></span>

<span data-ttu-id="52c7d-157">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="52c7d-158">如有需要，可通过 MacPorts 安装 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="52c7d-159">在同一系统上使用 MacPorts 和 Homebrew 时可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="52c7d-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="52c7d-160">但是，Homebrew 没有适用于 OpenSSL 1.0 的包。</span><span class="sxs-lookup"><span data-stu-id="52c7d-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="52c7d-161">有关详细信息，请参阅 [MacPorts 常见问题解答](https://trac.macports.org/wiki/FAQ)。</span><span class="sxs-lookup"><span data-stu-id="52c7d-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="52c7d-162">安装 Xcode 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="52c7d-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="52c7d-163">MacPorts 需要 Xcode 工具。</span><span class="sxs-lookup"><span data-stu-id="52c7d-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="52c7d-164">安装 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="52c7d-164">Install MacPorts.</span></span> <span data-ttu-id="52c7d-165">如需说明，请参阅[安装指南](https://www.macports.org/install.php)。</span><span class="sxs-lookup"><span data-stu-id="52c7d-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="52c7d-166">通过运行 `sudo port selfupdate` 更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="52c7d-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="52c7d-167">通过运行 `sudo port upgrade outdated` 升级 MacPorts 包。</span><span class="sxs-lookup"><span data-stu-id="52c7d-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="52c7d-168">通过运行 `sudo port install openssl10` 安装 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="52c7d-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="52c7d-169">链接库，使其可供 PowerShell 使用：</span><span class="sxs-lookup"><span data-stu-id="52c7d-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="52c7d-170">卸载 PowerShell</span><span class="sxs-lookup"><span data-stu-id="52c7d-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="52c7d-171">如果使用 Homebrew 安装 PowerShell，请使用以下命令进行卸载：</span><span class="sxs-lookup"><span data-stu-id="52c7d-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="52c7d-172">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52c7d-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="52c7d-173">若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除路径。</span><span class="sxs-lookup"><span data-stu-id="52c7d-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="52c7d-174">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="52c7d-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="52c7d-175">路径</span><span class="sxs-lookup"><span data-stu-id="52c7d-175">Paths</span></span>

- <span data-ttu-id="52c7d-176">`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.1/`</span><span class="sxs-lookup"><span data-stu-id="52c7d-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.1/`</span></span>
- <span data-ttu-id="52c7d-177">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="52c7d-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="52c7d-178">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="52c7d-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="52c7d-179">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="52c7d-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="52c7d-180">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="52c7d-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="52c7d-181">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="52c7d-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="52c7d-182">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="52c7d-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="52c7d-183">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="52c7d-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="52c7d-184">因此主机特定的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="52c7d-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="52c7d-185">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="52c7d-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="52c7d-186">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="52c7d-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="52c7d-187">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.1/`，且符号链接位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="52c7d-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.1/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="52c7d-188">安装支持</span><span class="sxs-lookup"><span data-stu-id="52c7d-188">Installation support</span></span>

<span data-ttu-id="52c7d-189">Microsoft 支持本文档中的安装方法。</span><span class="sxs-lookup"><span data-stu-id="52c7d-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="52c7d-190">其他源可能会提供其他安装方法。</span><span class="sxs-lookup"><span data-stu-id="52c7d-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="52c7d-191">尽管这些工具和方法可能有效，但 Microsoft 无法支持这些方法。</span><span class="sxs-lookup"><span data-stu-id="52c7d-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="52c7d-192">其他资源</span><span class="sxs-lookup"><span data-stu-id="52c7d-192">Additional Resources</span></span>

- <span data-ttu-id="52c7d-193">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="52c7d-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="52c7d-194">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="52c7d-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="52c7d-195">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="52c7d-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://aka.ms/powershell-release?tag=stable
[releases]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
