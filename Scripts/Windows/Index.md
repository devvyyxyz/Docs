!!!danger
Please ensure you understand the purpose of each script before running it, as some scripts may alter system settings or delete files. Always run with appropriate permissions, especially for scripts requiring administrative access.
!!!

## Download

[!file](https://github.com/devvyyxyz/windows-scripts/archive/refs/heads/main.zip)

## Scripts

+++ **ClearTempFolders**
   - **Description**: Clears temporary files from `%temp%` and `C:\Windows\Temp` folders, helping to free up disk space.
   - **Usage**: Run as administrator to ensure access to Windows temp files.

+++ **SystemInfo**
   - **Description**: Shows detailed system information, including OS version, CPU, and memory specs.
   - **Usage**: Simply run the script to display the information.

+++ **IPConfigRefresh**
   - **Description**: Refreshes network settings by releasing and renewing the IP address and clearing the DNS cache.
   - **Usage**: Useful for troubleshooting network issues or refreshing DNS.

+++ **DiskCleanup**
   - **Description**: Opens the Disk Cleanup tool for easy access to system file cleanup options.
   - **Usage**: Run the script to quickly access Disk Cleanup without navigating through settings.

+++ **CheckDisk**
   - **Description**: Runs Check Disk on the C: drive to find and fix potential disk errors.
   - **Usage**: Run as administrator to ensure access to all drive sectors.

+++ **ShutdownTimer**
   - **Description**: Sets a timer for an automatic shutdown after a specified period.
   - **Usage**: Enter the desired time in seconds when prompted.
+++

+++ **EnableFirewall**
   - **Description**: Enables Windows Firewall for all profiles, securing your system from unauthorized access.
   - **Usage**: Run as administrator to apply settings for all profiles.

+++ **DisableFirewall**
   - **Description**: Disables Windows Firewall, which can be helpful for testing purposes or specific network configurations.
   - **Usage**: Run as administrator for full effect.

+++ **ClearDNSCache**
   - **Description**: Clears the DNS cache to potentially resolve internet connectivity issues.
   - **Usage**: Run the script when experiencing DNS-related connectivity problems.

+++ **PingTest**
  - **Description**: Pings a specified website or IP address to check network connectivity.
  - **Usage**: Run the script and enter the address you want to ping when prompted.

+++ **EnableHibernation**
  - **Description**: Enables hibernation mode on the system, allowing you to save power without fully shutting down.
  - **Usage**: Run the script to enable hibernation functionality in Windows.

+++ **DisableHibernation**
   - **Description**: Disables hibernation mode, which can free up disk space if the feature is unused.
   - **Usage**: Run the script to remove hibernation functionality and clear the hibernation file.
+++

Here's the updated installation section for Windows:

---

## Installation
1. Clone this repository:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. No need to make scripts executable on Windows. Ensure you have the appropriate script interpreters (e.g., `bash` for `.sh` scripts) installed, such as through Git Bash or WSL (Windows Subsystem for Linux).

### Instructions

1. **Create a directory** for your scripts and the `README.md` file.
2. **Copy the script files** and `README.md` content into the respective files in the directory.
3. **Install an interpreter** for the scripts you intend to run, such as Git Bash for `.sh` files.
4. **Update the `<repository_url>` and `<repository_directory>`** in the README with your specific information.

Let me know if you need further modifications or additional scripts!