# Intel mgbe undi Driver Builder

This repository contains a GitHub Actions workflow designed to automatically build and release the **Intel mgbe undi UEFI Driver**.

It fetches the source code directly from the upstream repository: [intel/iotg-mgbe-undi-driver](https://github.com/intel/iotg-mgbe-undi-driver) and compiles it into EFI executables.

## 🚀 Features

- **Automated Builds**: Compiles the driver automatically on a schedule.
- **Multi-Target Support**: Builds both `DEBUG` and `RELEASE` versions for X64 architecture.
- **Automatic Releases**: Creates a GitHub Release containing the compiled `.efi` binaries.
- **Manual Trigger**: Supports manual workflow dispatch via the GitHub Actions UI.

## 🛠️ Build Artifacts

Every release includes the following files:

- `*_X64_DEBUG.efi`: The driver compiled with debug symbols (useful for troubleshooting).
- `*_X64_RELEASE.efi`: The optimized driver for production use.

## ⚙️ How It Works

The workflow is defined in `.github/workflows/build.yml`. It performs the following steps:

1.  **Checkout**: Clones the `main` branch of `intel/iotg-mgbe-undi-driver`.
2.  **Dependencies**: Installs necessary build tools (EDK2 BaseTools, NASM, IASL, etc.) on `ubuntu-22.04`.
3.  **Compilation**:
    - Sets up the EDK2 environment.
    - Compiles `IntelUndiPkg` for X64 using GCC5.
4.  **Release**: Uploads the resulting artifacts to the Releases page of this repository.

## 🔄 Usage

### Scheduled Builds
The workflow runs automatically on the **1st of every month at 02:00 UTC+8**.

### Manual Trigger
You can trigger a build manually at any time:
1.  Go to the **Actions** tab in this repository.
2.  Select the **Build Intel mgbe undi Driver** workflow.
3.  Click **Run workflow**.
4.  (Optional) Enter a specific `Release tag` if you want to override the default versioning.

## ⚠️ Disclaimer

This repository is a **build utility** and is not affiliated with Intel. The source code used for the build is retrieved from the public Intel repository. Please refer to the upstream repository for license and source code details.

---
*Upstream Repository: [intel/iotg-mgbe-undi-driver](https://github.com/intel/iotg-mgbe-undi-driver)*
