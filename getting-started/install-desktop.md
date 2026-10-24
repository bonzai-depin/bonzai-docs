# Install BonzAI Desktop

## Download 4.1.0

These are the four release files dated 23 October 2026. Installer and checksum links were checked on 24 October 2026. Sizes are approximate; downloaded models need additional space.

| Computer | Installer | Size | Checksum |
| --- | --- | --- | --- |
| macOS — Apple Silicon (ARM64) | [Download](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-arm64.dmg) | 2.92 GB | [SHA-256](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-arm64.dmg.SHA256SUMS) |
| Windows — x64 | [Download](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-windows-x64-setup.exe) | 4.17 GB | [SHA-256](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-windows-x64-setup.exe.SHA256SUMS) |
| Linux — amd64, NVIDIA CUDA | [Download](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-linux-amd64-cuda.deb) | 5.09 GB | [SHA-256](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-linux-amd64-cuda.deb.SHA256SUMS) |
| Linux — amd64, AMD ROCm | [Download](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-linux-amd64-rocm.deb) | 4.61 GB | [SHA-256](https://pub-c63241af101045fb837462e5c4c67e33.r2.dev/releases/BonzAI-4.1.0-linux-amd64-rocm.deb.SHA256SUMS) |

Choose **Apple Silicon** for an M-series Mac; this release list does not include an Intel Mac installer. Choose **CUDA** for a supported NVIDIA GPU on Linux, or **ROCm** for a supported AMD GPU. Both Linux packages are `.deb` files for amd64 systems. A package’s presence does not mean every GPU supports its backend; check [hardware and model choices](system-requirements.md).

## Install and start

1. Download the matching installer and leave room for the application, temporary installation files and at least one model.
2. On macOS, open the DMG and install the app. On Windows, run the setup executable. On a compatible Debian/Ubuntu Linux system, install the downloaded `.deb` through your package manager.
3. Open BonzAI and allow its local AI services to start.
4. Begin with **Chat**. Review the suggested model or choose a smaller model from the library.
5. Confirm the model download and wait until it is ready. Ask for one useful result.

You do not need a wallet or token balance for local creation. The installer and model downloads are separate: installing the app does not install every model in its catalog.

## Check the download

Download the matching `.SHA256SUMS` file. Compare its hash with the installer’s SHA-256 hash before opening the installer. For example:

macOS:

```sh
shasum -a 256 BonzAI-4.1.0-arm64.dmg
```

Windows PowerShell:

```powershell
Get-FileHash .\BonzAI-4.1.0-windows-x64-setup.exe -Algorithm SHA256
```

Linux (CUDA example):

```sh
sha256sum BonzAI-4.1.0-linux-amd64-cuda.deb
```

The complete hash must match, ignoring letter case. A checksum detects a changed or incomplete download; it is not a substitute for using the official release source. If it differs, download the installer again.

## Updating and keeping your work

Before updating, finish active work, quit BonzAI and back up important local outputs, datasets and agent/team data. Install the matching newer package. Keep existing model and data folders unless you intend to remove them; replacing the application and deleting user data are different operations.

If your operating system blocks installation, record the exact warning and use the [troubleshooting guide](../reference/troubleshooting.md). Do not disable system-wide protections to make an installer run.

**Next:** [Your first 10 minutes](first-10-minutes.md) · [What’s new](whats-new.md)
