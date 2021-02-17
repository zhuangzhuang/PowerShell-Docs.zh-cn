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
# <a name="installing-powershell-on-linux"></a>在 Linux 上安装 PowerShell

GitHub [版本][]页面上提供有所有可用包。 安装包以后，从终端运行 `pwsh`。 若已安装 [预览版](#installing-preview-releases)，请运行 `pwsh-preview`。

> [!NOTE]
> PowerShell 7 是就地升级，升级后会删除 PowerShell Core 6.x。
>
> `/usr/local/microsoft/powershell/6` 文件夹被替换为 `/usr/local/microsoft/powershell/7`。
>
> 如果需要与 PowerShell 7 并行运行 PowerShell 6，请使用[二进制存档](#binary-archives)方法重新安装 PowerShell 6。

对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]安装 PowerShell。 还可尝试直接使用 Linux [`tar.gz`存档][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

适用于 PowerShell 7.1 的官方支持平台版本

- Ubuntu 16.04/18.04/20.04（包括 ARM64）
- Ubuntu 19.10（通过 Snap 包）
- Debian 9/10
- CentOS 和 RHEL 7/8
- Fedora 30
- Alpine 3.11+（包括 ARM64）

适用于 PowerShell 7.0 的官方支持平台版本

- Ubuntu 16.04
- Ubuntu 18.04 和 20.04
- Debian 8
- Debian 9
- Debian 10
- Alpine 3.9 和 Alpine 3.10
- CentOS 7
- Red Hat Enterprise Linux (RHEL) 7
- Fedora 28
- Fedora 29
- Fedora 30
- openSUSE 42.3
- openSUSE Leap 15

社区支持的版本

- Ubuntu 18.10
- Ubuntu 19.10 和 20.10
- Arch Linux
- Kali
- Raspbian（试验版）

备选安装方法

- Snap 包
- 二进制存档
- .NET 全局工具

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>通过包存储库安装 - Ubuntu 16.04

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---ubuntu-1604"></a>通过直接下载进行安装 - Ubuntu 16.04

从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令失败，未满足依赖项。 下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-1604"></a>卸载 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>通过包存储库安装 - Ubuntu 18.04

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---ubuntu-1804"></a>通过直接下载安装 - Ubuntu 18.04

从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令失败，未满足依赖项。 下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-1804"></a>卸载 - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a>Ubuntu 20.04

### <a name="installation-via-package-repository---ubuntu-2004"></a>通过包存储库安装 - Ubuntu 20.04

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---ubuntu-2004"></a>通过直接下载进行安装 - Ubuntu 20.04

从[版本][]页中将 Debian 包 `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令失败，未满足依赖项。 下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-2004"></a>卸载 - Ubuntu 20.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

安装是通过 `snapd` 受到支持。 有关说明，请参阅 [Snap 包][snap]。

> [!NOTE]
> Ubuntu 18.10 是[支持社区](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。

## <a name="ubuntu-1910-and-2010"></a>Ubuntu 19.10 和 20.10

安装是通过 `snapd` 受到支持。 有关说明，请参阅 [Snap 包][snap]。

> [!NOTE]
> Ubuntu 19.10 是[社区支持](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>通过包存储库安装 - Debian 8

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>通过包存储库安装 - Debian 9

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo apt-get install powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---debian-9"></a>通过直接下载进行安装 - Debian 9

从[版本][]页中将 Debian 包 `powershell_7.1.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_7.1.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>卸载 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10 仅在 PowerShell 7.0 以及更新版本中受到支持。

### <a name="installation-via-package-repository---debian-10"></a>通过包存储库安装 - Debian 10

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到包存储库。

首选方法如下所示：

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

### <a name="installation-via-direct-download---debian-10"></a>通过直接下载进行安装 - Debian 10

从[版本][]页中将 tar.gz 包 `powershell-7.1.2-linux-x64.tar.gz` 下载到 Debian 计算机。

然后在终端中执行以下命令：

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

## <a name="alpine-39-and-310"></a>Alpine 3.9 和 Alpine 3.10

> [!NOTE]
> Alpine 3.9 和 Alpine 3.10 仅在 PowerShell 7.0 以及更新版本中受到支持。

### <a name="installation-via-direct-download---alpine-39-and-310"></a>通过直接下载进行安装 - Alpine 3.9 和 3.10

从[版本][]页中将 tar.gz 包 `powershell-7.1.2-linux-alpine-x64.tar.gz` 下载到 Alpine 计算机。

然后在终端中执行以下命令：

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

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> 此包可以在 Oracle Linux 7 上运行。

### <a name="installation-via-package-repository-preferred---centos-7"></a>通过包存储库安装（首选）- CentOS 7

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---centos-7"></a>通过直接下载进行安装 - CentOS 7

使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤即可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>卸载 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超级用户身份注册 Microsoft 存储库一次。 注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7

从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤即可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>卸载 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>OpenSUSE

### <a name="installation---opensuse-423"></a>安装 - openSUSE 42.3

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

### <a name="installation---opensuse-leap-15"></a>安装 - openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>卸载 - OpenSUSE 42.3、openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 仅在 PowerShell 6.1 以及更新版本中受到支持。

> [!NOTE]
> Fedora 29 和 Fedora 30 仅在 PowerShell 7.0 以及更新版本中受到支持。

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>通过包存储库安装（首选）- Fedora 28、Fedora 29 和 Fedora 30

为简化安装和更新，已将适用于 Linux 的 PowerShell 发布到正式的 Microsoft 存储库。

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>通过直接下载进行安装 - Fedora 28、Fedora 29 和 Fedora 30

从[版本][]页中将 RPM 包 `powershell-7.1.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。

然后在终端中执行以下命令：

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤即可安装 RPM：

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>卸载 - Fedora 28、Fedora 29 和 Fedora 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Arch 支持不受 Microsoft 的官方支持且由社区维护。

[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。

- 可使用[最新标记版本][arch-release]对其进行编译
- 可使用[最新 commit to master][arch-git] 对其进行编译
- 可使用[最新版本二进制文件][arch-bin]进行安装

AUR 中的包由社区维护，并无正式支持。

若要详细了解如何从 AUR 安装包，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或[在 Docker 中使用 PowerShell](powershell-in-docker.md)。

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap 包

### <a name="getting-snapd"></a>获取 snapd

需具备 `snapd` 才能运行 Snap。 按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。

### <a name="installation-via-snap"></a>通过 Snap 进行安装

为简化安装和更新，已向 [Snap 存储](https://snapcraft.io/store)发布适用于 Linux 的 PowerShell。

首选方法如下所示：

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

若要安装预览版本，请使用以下方法：

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

安装完成后，Snap 将自动升级。 可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 触发升级。

### <a name="uninstallation"></a>卸载

```sh
sudo snap remove powershell
```

或

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Kali 支持不受 Microsoft 的官方支持且由社区维护。

### <a name="installation---kali"></a>安装 - Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>卸载 - Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian 支持是实验性的。

当前仅 Raspbian Stretch 支持 PowerShell。

CoreCLR 和 PowerShell 仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。

下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。

### <a name="installation---raspbian"></a>安装 - Raspbian

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

或者，可以创建可启动 PowerShell 的符号链接，而无需指定到 `pwsh` 二进制文件的路径。

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>卸载 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a>安装预览版本

通过包存储库安装适用于 Linux 的 PowerShell 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。

直接下载安装不会更改包名称（文件名除外）。

下表包含使用各种包管理器安装稳定包和预览包的命令：

| 分配 |            稳定包命令            |               预览包命令                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu、Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS、RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a>作为 .NET 全局工具安装

如果你已安装 [.NET Core SDK](/dotnet/core/sdk)，则可以轻松地安装 PowerShell 作为 [.NET 全局工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

dotnet 工具安装程序将 `~/.dotnet/tools` 添加到 `PATH` 环境变量中。 但是，当前运行的 shell 没有更新的 `PATH`。 应该可以通过键入 `pwsh` 从新 shell 启动 PowerShell。

## <a name="binary-archives"></a>二进制存档

已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。

### <a name="dependencies"></a>依赖项

PowerShell 为所有 Linux 分发版生成可移植二进制文件。 但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，并且 PowerShell 也有相同要求。

下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。

| OS                 | 依赖项 |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.10       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Ubuntu 18.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind、libcurl、openssl-libs、libicu |
| openSUSE 42.3 | libcurl4、libopenssl1_0_0、libicu52_1 |
| openSUSE Leap 15 | libcurl4、libopenssl1_0_0、libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。 例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>安装 - 二进制存档

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>卸载二进制存档

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>路径

- `$PSHOME` 是 `/opt/microsoft/powershell/7/`
- 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
- 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
- 将从 `~/.local/share/powershell/Modules` 中读取用户模块
- 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
- 将从 `$PSHOME/Modules` 中读取默认模块
- PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的按主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。

PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。

## <a name="installation-support"></a>安装支持

Microsoft 支持本文档中的安装方法。 其他源可能会提供其他安装方法。 尽管这些工具和方法可能有效，但 Microsoft 无法支持这些方法。

<!-- link references -->
[版本]: https://aka.ms/PowerShell-Release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
