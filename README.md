# customarchy

A streamlined fork of [Omarchy](https://omarchy.org/), an opinionated Arch + Hyprland setup.

## Modifications

### Packages

- Removes `1password`, `kdenlive`, `mpv`, `obs-studio`, `signal-desktop`, `typora`, `xournalpp`
- Adds `bitwarden`, `vlc`, `visual-studio-code-bin`

### Other changes

- Removes `Service`, `Editor`, and `Gaming` entries from install menu
- Cleans up unnecessary `bash` and `git` aliases
- Sets default monitor scale to 1.5
- Maps Right Alt as the compose key
- Customizes `fastfetch` config

## Installation

> [!Note]
> Disk encryption must be enabled to use Omarchy as intended. The system will automatically log in the user once the disk is decrypted at boot. Bluetooth keyboards cannot be used to enter the password at startup, so you’ll need a wired keyboard or one with a 2.4 GHz dongle.

### [Manual Installation](https://learn.omacom.io/2/the-omarchy-manual/96/manual-installation)

1. Install Arch

    - [Download the Arch Linux ISO](https://archlinux.org/download/)
    - Flash it to a USB stick (e.g. with [balenaEtcher](https://etcher.balena.io/))
    - Disable Secure Boot in your BIOS
    - Boot off the USB stick

2. Connect to WiFi (if not using Ethernet)

    ```bash
    iwctl
    station wlan0 scan
    station wlan0 connect <tab>
    ```

    Select your network and enter the password.

3. Run `archinstall` and pick the following options:

    | Section | Option |
    |---------|--------|
    | Mirrors and repositories | Select regions > Your country |
    | Disk configuration | Partitioning > Default partitioning layout > Select disk (with space + return) |
    | Disk > File system | btrfs (default structure: yes + use compression) |
    | Disk > Disk encryption | Encryption type: LUKS + Encryption password + Partitions (select the one) |
    | Hostname | Give your computer a name |
    | Bootloader | Limine |
    | Authentication > Root password | Set yours |
    | Authentication > User account | Add a user > Superuser: Yes > Confirm and exit |
    | Applications > Audio | pipewire |
    | Network configuration | Copy ISO network config |
    | Timezone | Set yours |

4. After rebooting into your new Arch system and logging in with your user, run:

    ```bash
    eval "$(curl -fsSL https://raw.githubusercontent.com/Chaitanya-Keyal/customarchy/refs/heads/customarchy/boot.sh)"
    ```

    The script will:
    - Prompt for sudo
    - Ask for your name and email (to configure git and shortcuts)
    - Install all packages and apply configs (runtime: ~5–30 minutes)
    - When finished, it will ask permission to reboot.

### ISO Installation

> [!Warning]
> This method will erase all data on the selected drive and use full-disk encryption.

1. [Download the customarchy ISO](https://drive.google.com/drive/folders/1IlnJe-EzjWsO3Tsek3hRGpT_Bca7N4nK?usp=sharing)
2. Flash it to a USB stick (e.g. with [balenaEtcher](https://etcher.balena.io/))
3. Disable Secure Boot in your BIOS
4. Boot off the USB stick
