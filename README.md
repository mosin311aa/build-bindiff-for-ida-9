# Build BinDiff For IDA 9

English | [简体中文](README.zh.md)

This is an unofficial repository, just for convenience. The original source code is available at [Google's BinDiff repository](https://github.com/google/bindiff).

Build logs and artifacts can be found in the [Actions tab](https://github.com/Lil-Ran/build-bindiff-for-ida-9/actions).

## Installation

To install the IDA plugin, download and unzip the artifact from the release page, then copy the dynamic library file in `ida` subdirectory to the `plugins` directory of your IDA installation.

## Compatibility

### IDA Version

The IDA version in the filename refers to from which we get the IDA SDK used during compilation. The build artifact can also be used with other IDA versions that use the same SDK. For example, a release built for IDA 9.1.250226 is also compatible with IDA 9.0 RC1 and 9.0 SP.

### OS

We build on these [GitHub-hosted runners](https://docs.github.com/en/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners):

- windows-2022
- ubuntu-24.04
- ubuntu-22.04 *(for who has older libc versions)*
- macos-14 *(Apple Silicon)*
- macos-13 *(Intel)*

Ubuntu builds are compatible with most Linux distributions that use same or newer versions of glibc.

## Custom Build

For those who want to build their own version, you can fork this repository and modify the `build.yml` file in the `.github/workflows` directory. The file is quite self-explanatory, but here are some tips:

- You should provide a direct link to the IDA SDK archive that can be downloaded without authentication.
- The `PATH_TO_IDASDK_CONTENT` variable should point to the directory that contains the `include` and `lib` directories of the IDA SDK. It is relative to the root of the archive.
- To reduce minutes and billing on GitHub Actions, remove any OS you don't need. Remove `binexport` steps can shorten the build time by 50%, if you don't need a BinExport plugin.

In forked repositories, actions are disabled by default. You can enable them in the repository settings under the "Actions" tab.
