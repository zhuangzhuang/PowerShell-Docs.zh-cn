---
title: 在 Linux 上安装 PowerShell
description: 介绍如何在各种 Linux 分发版上安装 PowerShell
ms.date: 02/02/2021
ms.openlocfilehash: 1e7fabdc94ba70a91eb5c6425893bc5af640e584
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563295"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="69eb9-103">在 Linux 上安装 PowerShell</span><span class="sxs-lookup"><span data-stu-id="69eb9-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="69eb9-104">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="69eb9-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="69eb9-105">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="69eb9-106">若已安装 [预览版](#installing-preview-releases)，请运行 `pwsh-preview`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-107">PowerShell 7 是就地升级，升级后会删除 PowerShell Core 6.x。</span><span class="sxs-lookup"><span data-stu-id="69eb9-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="69eb9-108">`/usr/local/microsoft/powershell/6` 文件夹被替换为 `/usr/local/microsoft/powershell/7`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="69eb9-109">如果需要与 PowerShell 7 并行运行 PowerShell 6，请使用[二进制存档](#binary-archives)方法重新安装 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="69eb9-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="69eb9-110">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="69eb9-111">还可尝试直接使用 Linux [`tar.gz`存档][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="69eb9-112">适用于 PowerShell 7.1 的官方支持平台版本</span><span class="sxs-lookup"><span data-stu-id="69eb9-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="69eb9-113">Ubuntu 16.04/18.04/20.04（包括 ARM64）</span><span class="sxs-lookup"><span data-stu-id="69eb9-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="69eb9-114">Ubuntu 19.10（通过 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="69eb9-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="69eb9-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="69eb9-115">Debian 9/10</span></span>
- <span data-ttu-id="69eb9-116">CentOS 和 RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="69eb9-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="69eb9-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="69eb9-117">Fedora 30</span></span>
- <span data-ttu-id="69eb9-118">Alpine 3.11+（包括 ARM64）</span><span class="sxs-lookup"><span data-stu-id="69eb9-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="69eb9-119">适用于 PowerShell 7.0 的官方支持平台版本</span><span class="sxs-lookup"><span data-stu-id="69eb9-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="69eb9-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="69eb9-121">Ubuntu 18.04 和 20.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="69eb9-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="69eb9-122">Debian 8</span></span>
- <span data-ttu-id="69eb9-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="69eb9-123">Debian 9</span></span>
- <span data-ttu-id="69eb9-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="69eb9-124">Debian 10</span></span>
- <span data-ttu-id="69eb9-125">Alpine 3.9 和 Alpine 3.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="69eb9-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-126">CentOS 7</span></span>
- <span data-ttu-id="69eb9-127">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="69eb9-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="69eb9-128">Fedora 28</span></span>
- <span data-ttu-id="69eb9-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="69eb9-129">Fedora 29</span></span>
- <span data-ttu-id="69eb9-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="69eb9-130">Fedora 30</span></span>
- <span data-ttu-id="69eb9-131">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="69eb9-131">openSUSE 42.3</span></span>
- <span data-ttu-id="69eb9-132">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="69eb9-132">openSUSE Leap 15</span></span>

<span data-ttu-id="69eb9-133">社区支持的版本</span><span class="sxs-lookup"><span data-stu-id="69eb9-133">Community supported releases</span></span>

- <span data-ttu-id="69eb9-134">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="69eb9-135">Ubuntu 19.10 和 20.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="69eb9-136">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="69eb9-136">Arch Linux</span></span>
- <span data-ttu-id="69eb9-137">Kali</span><span class="sxs-lookup"><span data-stu-id="69eb9-137">Kali</span></span>
- <span data-ttu-id="69eb9-138">Raspbian（试验版）</span><span class="sxs-lookup"><span data-stu-id="69eb9-138">Raspbian (experimental)</span></span>

<span data-ttu-id="69eb9-139">备选安装方法</span><span class="sxs-lookup"><span data-stu-id="69eb9-139">Alternate install methods</span></span>

- <span data-ttu-id="69eb9-140">Snap 包</span><span class="sxs-lookup"><span data-stu-id="69eb9-140">Snap Package</span></span>
- <span data-ttu-id="69eb9-141">二进制存档</span><span class="sxs-lookup"><span data-stu-id="69eb9-141">Binary Archives</span></span>
- <span data-ttu-id="69eb9-142">.NET 全局工具</span><span class="sxs-lookup"><span data-stu-id="69eb9-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="69eb9-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="69eb9-144">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="69eb9-145">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-146">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-146">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-147">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-148">注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="69eb9-149">通过直接下载进行安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="69eb9-150">从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-150">Download the Debian package `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="69eb9-151">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="69eb9-152">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="69eb9-153">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="69eb9-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="69eb9-154">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="69eb9-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="69eb9-156">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="69eb9-157">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-158">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-158">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-159">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-160">注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="69eb9-161">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="69eb9-162">从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-162">Download the Debian package `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="69eb9-163">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="69eb9-164">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="69eb9-165">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="69eb9-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="69eb9-166">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="69eb9-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="69eb9-168">通过包存储库安装 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="69eb9-169">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-170">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-170">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-171">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-172">注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="69eb9-173">通过直接下载进行安装 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="69eb9-174">从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-174">Download the Debian package `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="69eb9-175">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="69eb9-176">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="69eb9-177">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="69eb9-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="69eb9-178">卸载 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="69eb9-179">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-179">Ubuntu 18.10</span></span>

<span data-ttu-id="69eb9-180">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="69eb9-181">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="69eb9-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-182">Ubuntu 18.10 是[支持社区](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="69eb9-183">Ubuntu 19.10 和 20.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="69eb9-184">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="69eb9-185">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="69eb9-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-186">Ubuntu 19.10 是[社区支持](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="69eb9-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="69eb9-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="69eb9-188">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="69eb9-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="69eb9-189">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-190">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-190">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-191">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-192">注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="69eb9-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="69eb9-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="69eb9-194">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="69eb9-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="69eb9-195">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-196">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-196">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-197">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-198">注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="69eb9-199">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="69eb9-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="69eb9-200">从[版本][]页中将 Debian 包 `powershell_7.1.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-200">Download the Debian package `powershell_7.1.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="69eb9-201">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="69eb9-202">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="69eb9-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="69eb9-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="69eb9-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-204">Debian 10 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="69eb9-205">通过包存储库安装 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="69eb9-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="69eb9-206">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-207">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-207">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="69eb9-208">通过直接下载进行安装 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="69eb9-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="69eb9-209">从[版本][]页中将 tar.gz 包 `powershell-7.1.2-linux-x64.tar.gz` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-209">Download the tar.gz package `powershell-7.1.2-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="69eb9-210">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-210">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="69eb9-211">Alpine 3.9 和 Alpine 3.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-212">Alpine 3.9 和 Alpine 3.10 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="69eb9-213">通过直接下载进行安装 - Alpine 3.9 和 3.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="69eb9-214">从[版本][]页中将 tar.gz 包 `powershell-7.1.2-linux-alpine-x64.tar.gz` 下载到 Alpine 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-214">Download the tar.gz package `powershell-7.1.2-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="69eb9-215">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-215">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="69eb9-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-217">此包可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="69eb9-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="69eb9-218">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="69eb9-219">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-220">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-221">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="69eb9-222">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="69eb9-223">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-223">Using [CentOS 7][], download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="69eb9-224">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="69eb9-225">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="69eb9-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="69eb9-226">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="69eb9-228">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="69eb9-229">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="69eb9-230">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-231">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="69eb9-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="69eb9-232">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="69eb9-233">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="69eb9-234">从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-234">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="69eb9-235">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="69eb9-236">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="69eb9-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="69eb9-237">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="69eb9-238">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="69eb9-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="69eb9-239">安装 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="69eb9-239">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="69eb9-240">安装 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="69eb9-240">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="69eb9-241">卸载 - OpenSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="69eb9-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="69eb9-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="69eb9-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-243">Fedora 28 仅在 PowerShell 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-244">Fedora 29 和 Fedora 30 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="69eb9-245">通过包存储库安装（首选）- Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="69eb9-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="69eb9-246">为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="69eb9-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="69eb9-247">通过直接下载进行安装 - Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="69eb9-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="69eb9-248">从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="69eb9-248">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="69eb9-249">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="69eb9-250">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="69eb9-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="69eb9-251">卸载 - Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="69eb9-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="69eb9-252">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="69eb9-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-253">Arch 支持不受 Microsoft 的官方支持且由社区维护。</span><span class="sxs-lookup"><span data-stu-id="69eb9-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="69eb9-254">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="69eb9-255">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="69eb9-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="69eb9-256">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="69eb9-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="69eb9-257">可使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="69eb9-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="69eb9-258">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="69eb9-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="69eb9-259">若要详细了解如何从 AUR 安装包，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或[在 Docker 中使用 PowerShell](powershell-in-docker.md)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="69eb9-261">Snap 包</span><span class="sxs-lookup"><span data-stu-id="69eb9-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="69eb9-262">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="69eb9-262">Getting snapd</span></span>

<span data-ttu-id="69eb9-263">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="69eb9-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="69eb9-264">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="69eb9-265">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="69eb9-265">Installation via Snap</span></span>

<span data-ttu-id="69eb9-266">为简化安装和更新，已向 [Snap 存储](https://snapcraft.io/store)发布适用于 Linux 的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="69eb9-267">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="69eb9-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="69eb9-268">若要安装预览版本，请使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="69eb9-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="69eb9-269">安装完成后，Snap 将自动升级。</span><span class="sxs-lookup"><span data-stu-id="69eb9-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="69eb9-270">可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 触发升级。</span><span class="sxs-lookup"><span data-stu-id="69eb9-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="69eb9-271">卸载</span><span class="sxs-lookup"><span data-stu-id="69eb9-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="69eb9-272">或</span><span class="sxs-lookup"><span data-stu-id="69eb9-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="69eb9-273">Kali</span><span class="sxs-lookup"><span data-stu-id="69eb9-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-274">Kali 支持不受 Microsoft 的官方支持且由社区维护。</span><span class="sxs-lookup"><span data-stu-id="69eb9-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="69eb9-275">安装 - Kali</span><span class="sxs-lookup"><span data-stu-id="69eb9-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="69eb9-276">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="69eb9-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="69eb9-277">Raspbian</span><span class="sxs-lookup"><span data-stu-id="69eb9-277">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="69eb9-278">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="69eb9-278">Raspbian support is experimental.</span></span>

<span data-ttu-id="69eb9-279">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-279">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="69eb9-280">CoreCLR 和 PowerShell 仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="69eb9-280">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="69eb9-281">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="69eb9-281">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="69eb9-282">安装 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="69eb9-282">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="69eb9-283">或者，可以创建可启动 PowerShell 的符号链接，而无需指定到 `pwsh` 二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="69eb9-283">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="69eb9-284">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="69eb9-284">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="69eb9-285">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="69eb9-285">Installing Preview Releases</span></span>

<span data-ttu-id="69eb9-286">通过包存储库安装适用于 Linux 的 PowerShell 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-286">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="69eb9-287">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="69eb9-287">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="69eb9-288">下表包含使用各种包管理器安装稳定包和预览包的命令：</span><span class="sxs-lookup"><span data-stu-id="69eb9-288">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="69eb9-289">分配</span><span class="sxs-lookup"><span data-stu-id="69eb9-289">Distribution(s)</span></span> |            <span data-ttu-id="69eb9-290">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="69eb9-290">Stable Command</span></span>            |               <span data-ttu-id="69eb9-291">预览包命令</span><span class="sxs-lookup"><span data-stu-id="69eb9-291">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="69eb9-292">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="69eb9-292">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="69eb9-293">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="69eb9-293">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="69eb9-294">Fedora</span><span class="sxs-lookup"><span data-stu-id="69eb9-294">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="69eb9-295">作为 .NET 全局工具安装</span><span class="sxs-lookup"><span data-stu-id="69eb9-295">Install as a .NET Global tool</span></span>

<span data-ttu-id="69eb9-296">如果你已安装 [.NET Core SDK](/dotnet/core/sdk)，则可以轻松地安装 PowerShell 作为 [.NET 全局工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="69eb9-296">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="69eb9-297">dotnet 工具安装程序将 `~/.dotnet/tools` 添加到 `PATH` 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="69eb9-297">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="69eb9-298">但是，当前运行的 shell 没有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="69eb9-298">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="69eb9-299">应该可以通过键入 `pwsh` 从新 shell 启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="69eb9-299">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="69eb9-300">二进制存档</span><span class="sxs-lookup"><span data-stu-id="69eb9-300">Binary Archives</span></span>

<span data-ttu-id="69eb9-301">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="69eb9-301">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="69eb9-302">依赖项</span><span class="sxs-lookup"><span data-stu-id="69eb9-302">Dependencies</span></span>

<span data-ttu-id="69eb9-303">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="69eb9-303">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="69eb9-304">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，并且 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="69eb9-304">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="69eb9-305">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-305">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="69eb9-306">OS</span><span class="sxs-lookup"><span data-stu-id="69eb9-306">OS</span></span>                 | <span data-ttu-id="69eb9-307">依赖项</span><span class="sxs-lookup"><span data-stu-id="69eb9-307">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="69eb9-308">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-308">Ubuntu 16.04</span></span>       | <span data-ttu-id="69eb9-309">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="69eb9-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="69eb9-310">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="69eb9-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="69eb9-311">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="69eb9-311">Ubuntu 17.10</span></span>       | <span data-ttu-id="69eb9-312">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="69eb9-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="69eb9-313">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="69eb9-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="69eb9-314">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="69eb9-314">Ubuntu 18.04</span></span>       | <span data-ttu-id="69eb9-315">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="69eb9-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="69eb9-316">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="69eb9-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="69eb9-317">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="69eb9-317">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="69eb9-318">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="69eb9-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="69eb9-319">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="69eb9-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="69eb9-320">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="69eb9-320">Debian 9 (Stretch)</span></span> | <span data-ttu-id="69eb9-321">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="69eb9-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="69eb9-322">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="69eb9-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="69eb9-323">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-323">CentOS 7</span></span> <br> <span data-ttu-id="69eb9-324">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-324">Oracle Linux 7</span></span> <br> <span data-ttu-id="69eb9-325">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="69eb9-325">RHEL 7</span></span> | <span data-ttu-id="69eb9-326">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="69eb9-326">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="69eb9-327">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="69eb9-327">openSUSE 42.3</span></span> | <span data-ttu-id="69eb9-328">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="69eb9-328">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="69eb9-329">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="69eb9-329">openSUSE Leap 15</span></span> | <span data-ttu-id="69eb9-330">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="69eb9-330">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="69eb9-331">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="69eb9-331">Fedora 27</span></span> <br> <span data-ttu-id="69eb9-332">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="69eb9-332">Fedora 28</span></span> | <span data-ttu-id="69eb9-333">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="69eb9-333">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="69eb9-334">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="69eb9-334">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="69eb9-335">例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="69eb9-335">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="69eb9-336">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="69eb9-336">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="69eb9-337">Linux</span><span class="sxs-lookup"><span data-stu-id="69eb9-337">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="69eb9-338">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="69eb9-338">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="69eb9-339">路径</span><span class="sxs-lookup"><span data-stu-id="69eb9-339">Paths</span></span>

- <span data-ttu-id="69eb9-340">`$PSHOME` 是 `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="69eb9-340">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="69eb9-341">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="69eb9-341">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="69eb9-342">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="69eb9-342">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="69eb9-343">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="69eb9-343">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="69eb9-344">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="69eb9-344">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="69eb9-345">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="69eb9-345">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="69eb9-346">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="69eb9-346">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="69eb9-347">配置文件采用 PowerShell 的按主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="69eb9-347">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="69eb9-348">PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="69eb9-348">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="69eb9-349">安装支持</span><span class="sxs-lookup"><span data-stu-id="69eb9-349">Installation support</span></span>

<span data-ttu-id="69eb9-350">Microsoft 支持本文档中的安装方法。</span><span class="sxs-lookup"><span data-stu-id="69eb9-350">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="69eb9-351">其他源可能会提供其他安装方法。</span><span class="sxs-lookup"><span data-stu-id="69eb9-351">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="69eb9-352">尽管这些工具和方法可能有效，但 Microsoft 无法支持这些方法。</span><span class="sxs-lookup"><span data-stu-id="69eb9-352">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[版本]: https://aka.ms/PowerShell-Release?tag=stable
[releases]: https://aka.ms/PowerShell-Release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
