# 构建用于 IDA 9 的 BinDiff

[English](README.md) | 简体中文

这是一个非官方仓库，仅为方便使用。原始源码位于 [Google 的 BinDiff 仓库](https://github.com/google/bindiff)。

构建日志和产物可在 [Actions 页面](https://github.com/Lil-Ran/build-bindiff-for-ida-9/actions) 查看。

## 安装

要安装 IDA 插件，请从 release 页面下载并解压，然后将 `ida` 文件夹下的动态库文件复制到你的 IDA 安装目录的 `plugins` 文件夹中。

## 兼容性

### IDA 版本

文件名中的 IDA 版本指的是编译时所用的 IDA SDK 随附于该 IDA 版本。该构建产物也可用于使用相同 SDK 的其他 IDA 版本。例如，为 IDA 9.1.250226 构建的版本同样兼容 IDA 9.0 RC1 和 9.0 SP。

### 操作系统

我们在这些 [GitHub 托管运行器](https://docs.github.com/zh/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners) 上进行构建：

- windows-2022
- ubuntu-24.04
- ubuntu-22.04 *(适用于较低 libc 版本)*
- macos-14 *(Apple Silicon)*
- macos-13 *(Intel)*

Ubuntu 构建文件兼容大多数 Linux 发行版，只要它们使用相同或更新版本的 glibc。

## 自定义构建

如需自行构建，可 fork 本仓库并修改 `.github/workflows` 目录下的 `build.yml` 文件。该文件已经有足够的可读性，以下是一些提示：

- 你需要提供一个无需认证即可下载的 IDA SDK 压缩包直链。
- `PATH_TO_IDASDK_CONTENT` 变量应指向 IDA SDK 中包含 `include` 和 `lib` 目录的路径，相对于压缩包根目录。
- 若想减少 GitHub Actions 的运行时间和计费，可移除不需要的操作系统。若不需要 BinExport 插件，移除相关步骤可将构建时间缩短 50%。

Fork 后的仓库默认禁用 Actions，可在仓库设置的 "Actions" 标签页中启用。
