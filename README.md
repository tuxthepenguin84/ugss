<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/tuxthepenguin84/ugss">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Ultimate Game Streaming Server</h3>

  <p align="center">
    Build the Ultimate Game Streaming Server
    <br />
    <a href="https://github.com/tuxthepenguin84/ugss"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/tuxthepenguin84/ugss/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/tuxthepenguin84/ugss/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details open>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#hardware">Hardware</a></li>
        <li><a href="#software">Software</a></li>
      </ul>
    </li>
    <li><a href="#deploy-server">Deploy Server</a></li>
      <ul>
        <li><a href="#vm-configuration-optional">VM Configuration</a></li>
        <li><a href="#install-os">Install OS</a></li>
        <li><a href="#configure-os">Configure OS</a></li>
        <li><a href="#configure-additional-drive">Configure Additional Drive</a></li>
        <li><a href="#configure-gpu">Configure GPU</a></li>
      </ul>
    <li><a href="#streaming-software">Streaming Software</a></li>
      <ul>
        <li><a href="#sunshine">Sunshine</a></li>
        <li><a href="#moonlight">Moonlight</a></li>
        <li><a href="#moondeck">MoonDeck</a></li>
      </ul>
    <li><a href="#game-launchers">Game Launchers</a></li>
      <ul>
        <li><a href="#steam">Steam</a></li>
        <li><a href="#lutris">Lutris</a></li>
        <li><a href="#heroic-game-launcher">Heroic Game Launcher</a></li>
      </ul>
    <li><a href="#emulation">Emulation</a></li>
      <ul>
        <li><a href="#emudeck">EmuDeck</a></li>
      </ul>
    <li><a href="#utilities">Utilities</a></li>
      <ul>
        <li><a href="#xone">xone</a></li>
        <li><a href="#gamemode">GameMode</a></li>
        <li><a href="#mangohud">MangoHud</a></li>
        <li><a href="#goverlay">Goverlay</a></li>
        <li><a href="#protonup-qt">ProtonUp-QT</a></li>
      </ul>
    <li><a href="#additional-resources">Additional Resources</a></li>
    <li><a href="#other-considerations">Other Considerations</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## About The Project

This is a comprehensive guide on how to build the ultimate game streaming server. With a dedicated game streaming server all the processing and rendering is centralized and then streamed to any type of device.

Once complete you should be able to stream games to just about any device:

- Linux
- macOS
- Windows
- Raspberry Pi
- Steam Deck
- Steam Link
- Android
- iOS
- Amazon Fire tablets and TVs
- Apple TV
- ChromeOS
- PS Vita
- Xbox
- LG webOS TVs

[_But why?..._](https://www.youtube.com/watch?v=shbxUe-S2V8&pp=ygUUd2h5IHdoeSB3aHkgcHJlYWNoZXI%3D)

I got the idea for this when I tried using [Bazzite](https://github.com/ublue-os/bazzite) but ran into issues with Wayland on Nvidia and Fedora Atomic Desktops. Once I figured out the major components of what all was needed I decided I'd try to roll my own configuration on Ubuntu.

One of the key benefits of a game streaming server is that it allows you to centralize processing power in one place. This enables you to use smaller, more energy-efficient devices throughout your home to stream games to, rather than relying on powerful hardware at each location. For instance, streaming games to a Steam Deck can extend playtime by over twice as long (5+ hours) at higher quality compared to playing locally.

### Screenshots

[![Product Screen Shot 1][product-screenshot-1]](https://github.com/tuxthepenguin84/ugss/blob/master/images/screenshot1.png)
[![Product Screen Shot 2][product-screenshot-2]](https://github.com/tuxthepenguin84/ugss/blob/master/images/screenshot2.png)
[![Product Screen Shot 3][product-screenshot-3]](https://github.com/tuxthepenguin84/ugss/blob/master/images/screenshot3.png)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

### Hardware

- A physical server or VM
- Dedicated GPU (AMD, Intel, or Nvidia)
- Monitor and/or DisplayPort/HDMI Emulator
  - This will need to be plugged into your GPU and what you select here will determine the maximum resolution and refresh rate you can stream games at
  - For example, if you only care about 1080p at 60hz just about every monitor will do that or you can buy a generic [DisplayPort Emulator](https://www.amazon.com/gp/product/B08RC9V75B/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) or [HDMI Emulator](https://www.amazon.com/gp/product/B08RCH47KL/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1)
  - If you want a high refresh rate for gaming, for example 1440p at 144hz or 1080p at 240hz, you will need a [high refresh rate DisplayPort Emulator](https://www.amazon.com/gp/product/B0C2CNYCHX/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) or high refresh rate monitor. Be sure to verify the emulator supports the resolution and refresh rate you want.
- Any device listed in the About section above that you can stream your games to
- Optional: Keyboard, Mouse, Xbox Controller

### Software

- [Ubuntu 24.04 Desktop](https://ubuntu.com/download/desktop) - Desktop OS
- [Sunshine](https://github.com/LizardByte/Sunshine/) - Backend streaming service
- [Moonlight](https://moonlight-stream.org/) - Host client to connect to Sunshine

All other software listed below is optional but I imagine most people would be using Steam at a minimum.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- BUILD EXAMPLES -->

## Deploy Server

### VM Configuration

_If you won't be building your server as a VM skip this section_

1. Proxmox VM Configuration (adjust accordingly)
   - CPU: 16 Cores
     - Type: `Host`
   - Memory: 32 GB Memory
   - Storage
     - Controller: `VirtIO SCSI single`
     - Disks:
       - OS - 100GB
       - Games - 1TB (Optional)
       - Enable `SSD Emulation`, `IO thread`, & `Discard`
   - Graphics Card: `Standard VGA`
     - Set this to `None` after you attach your GPU, but we need a basic display out for the OS install
   - BIOS: `OVMF (UEFI)`
     - Make sure you add an EFI disk
     - Uncheck `Pre-enroll Keys` as this will enable Secure Boot by default which we don't need
1. Add your Ubuntu ISO as media for the CDROM drive

### Install OS

1. Boot to the ISO
1. Select the `Default Installation`
1. Skip the third party drivers and additional media formats unless you know you need it. We will be installing GPU drivers manually later.
1. Make sure the OS is installed to the 100GB drive
1. Uncheck `Require my password to log in`
1. Remove CD/ISO once installation is complete and reboot

### Configure OS

- Install Additional Packages

  ```
  sudo apt install -y build-essential curl dkms git openssh-server vim
  ```

- Use X11 for Nvidia

  - If you are using an Nvidia GPU you should use X11 rather than Wayland display server, if you are unsure of what you are currently running `echo $XDG_SESSION_TYPE`. To switch, logoff and click the gear in the bottom right and select `Ubuntu on Xorg`. `nvfbc`, NVIDIA Frame Buffer Capture allows you to capture direct to GPU memory, significantly improving performance. At the time of this writing `nvfbc` does not work on Wayland.

- Configure auto-login

  - Your server must also auto-login without a password. This should have been configured in the OS installation but if not, `Settings => System => Users` and enable `Automatic Login`

- Disable Screen Blanking

  - Disable any type of screen saver, suspend, or screen blanking. `Settings => Power => Screen Blanking` to `Never`

- Do Not Disturb Mode

  - Enable Do Not Disturb in the notifications bar to disable any popups.

- Enable SSH
  ```
  sudo systemctl enable ssh
  ```
- Install latest updates

  ```
  sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y && sudo apt clean
  ```

- Install QEMU Agent (Optional) - Only if your streaming server is a Proxmox VM
  ```
  sudo apt install -y qemu-guest-agent
  ```

### Configure Additional Drive

If you configured a secondary drive to store games

1. Run `lsblk` to find your secondary drive, `/dev/sdb` for example
1. Format drive
   ```
   (echo d; echo g; echo w) | sudo fdisk /dev/sdb
   sudo mkfs.ext4 /dev/sdb
   ```
1. Mount drive

   ```
   # Get the UUID of the drive
   lsblk -f

   # Create games mount point
   sudo mkdir /mnt/games

   # Append to /etc/fstab
   /dev/disk/by-uuid/<drive_uuid_here> /mnt/games ext4 noatime,nodiratime,nosuid,nodev,nofail 0 0

   # Appears that systemd is tied into fstab now
   sudo systemctl daemon-reload

   # Set perms on drive to local user (change your_userid)
   sudo chown -R your_userid:your_userid /mnt/games

   # Mount drive
   sudo mount -a

   # Verify drive is working
   df -hT
   ```

### Configure GPU

1. Shutdown VM or host and install GPU if you haven't already
   - Proxmox GPU Config
     - Remove the Standard VGA virtual adapter
     - Add PCI Device
     - Raw Device, select your GPU device
     - Enable `All Functions`
     - Enable `Primary GPU`
     - Enable `ROM-Bar`
     - Enable `PCI-Express`
1. Plug in monitor or DisplayPort/HDMI emulator to the GPU
1. Boot host back up

#### AMD

_Coming soon..._

#### Intel

_Coming soon..._

#### Nvidia

1. Download the latest version of [Nvidia 3060 - 570.169](https://us.download.nvidia.com/XFree86/Linux-x86_64/570.169/NVIDIA-Linux-x86_64-570.169.run)
   ```
   wget https://us.download.nvidia.com/XFree86/Linux-x86_64/570.169/NVIDIA-Linux-x86_64-570.169.run
   chmod +x NVIDIA-Linux-x86_64-570.169.run
   sudo ./NVIDIA-Linux-x86_64-570.169.run
   ```
1. Multiple kernel module types are available for this system. Which would you like to use? `MIT/GPL`
1. An alternate method of installing the NVIDIA driver was detected. `Continue installation`
1. The Nouveau kernel driver is currently in use by your system. This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.
   -> Nouveau can usually be disabled by adding files to the modprobe configuration directories and rebuilding the initramfs. `OK`
1. Would you like nvidia-installer to attempt to create these modprobe configuration files for you? `Yes`
1. One or more modprobe configuration files to disable Nouveau have been written. You will need to reboot your system and possibly rebuild the initramfs before these changes can take effect. Note if you later wish to reenable Nouveau, you will need to delete these files: /usr/lib/modprobe.d/nvidia-installer-disable-nouveau.conf, /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
   -> nvidia-installer is not able to perform some of the sanity checks which detect potential installation problems while Nouveau is loaded. Would you like to continue installation without these sanity checks, or abort installation, confirm that Nouveau has been properly disabled, and attempt installation again later? `Continue installation`
1. Install NVIDIA's 32-bit compatibility libraries? `Yes`
1. Would you like to rebuild the initramfs? `Yes`
1. Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver will be used when you restart X? Any pre-existing X configuration file will be backed up. `Yes`
1. Verify drivers are installed correctly: `nvidia-smi`
1. Reboot

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Streaming Software

### Sunshine

[Sunshine](https://github.com/LizardByte/Sunshine) Self-hosted game stream host for Moonlight.

1. Download the [latest version](https://github.com/LizardByte/Sunshine/releases) of [Sunshine v2025.122.141614](https://github.com/LizardByte/Sunshine/releases/download/v2025.122.141614/sunshine-ubuntu-24.04-amd64.deb)
   ```
   wget -O ~/Downloads/sunshine.deb https://github.com/LizardByte/Sunshine/releases/download/v2025.122.141614/sunshine-ubuntu-24.04-amd64.deb
   ```
1. Install Sunshine
   ```
   sudo apt install -y -f ~/Downloads/sunshine.deb
   ```
1. Create and reload udev rules for uinput to create mouse and gamepad events:
   ```
   echo 'KERNEL=="uinput", SUBSYSTEM=="misc", OPTIONS+="static_node=uinput", TAG="uaccess"' | \
   sudo tee /etc/udev/rules.d/60-sunshine.rules
   sudo udevadm control --reload-rules
   sudo udevadm trigger
   sudo modprobe uinput
   ```
1. Configure Sunshine service

   ```
   # ~/.config/systemd/user/sunshine.service
   [Unit]
   Description=Sunshine self-hosted game stream host for Moonlight.
   StartLimitIntervalSec=500
   StartLimitBurst=5

   [Service]
   ExecStart=/usr/bin/sunshine
   Restart=on-failure
   RestartSec=5s

   [Install]
   WantedBy=graphical-session.target
   ```

1. Configure Sunshine to start on boot
   ```
   systemctl --user enable sunshine
   ```
1. Start Sunshine
   ```
   systemctl --user start sunshine
   ```
1. Configure Sunshine remote admin access
   ```
   # ~/.config/sunshine/sunshine.conf
   origin_web_ui_allowed = wan
   ```
1. `reboot`

#### Configure Sunshine

The default configs will work for most people but adjust as necessary

- Sunshine is configured at `https://localhost:47990`
- [Sunshine Official Documentation](https://docs.lizardbyte.dev/projects/sunshine/en/latest/index.html)

#### Configure Sunshine Applications

Sunshine Applications are configurations that get applied based on how you want to connect to the Sunshine server. For example you can create an application that configures 720p at 60hz and then launches Steam in Big Picture mode, this would be the ideal setup for a Steam Deck. Another example might be an application that configures 1440p at 144hz and launches Steam in normal mode for a more traditional gaming setup.

Here are my applications I have setup.

- Desktop - This is "dynamic" in that it will apply the same resolution and refresh rate that the client connecting is using.
  - Do Command
    ```
    sh -c "xrandr --output DP-4 --mode \"${SUNSHINE_CLIENT_WIDTH}x${SUNSHINE_CLIENT_HEIGHT}\" --rate ${SUNSHINE_CLIENT_FPS} --output DP-1 --off"
    ```
  - Undo Command
    ```
    xrandr --output DP-1 --mode 1920x1080 --rate 60 --output DP-4 --off
    ```
- MoonDeckStream - This is configured to match the Steam Deck resolution and refresh rate.
  - Do Command
    ```
    xrandr --output DP-4 --mode 1280x800 --rate 60 --output DP-1 --off
    ```
  - Undo Command
    ```
    xrandr --output DP-1 --mode 1920x1080 --rate 60 --output DP-4 --off
    ```
  - Command
    ```
    /home/sam/MoonDeck/MoonDeckBuddy.AppImage --exec MoonDeckStream
    ```
  - Uncheck `Continue streaming if the application exits quickly`
- Steam Big Picture - Similar to Desktop but launches Steam in Big Picture Mode
  - Do Command
    ```
    sh -c "xrandr --output DP-4 --mode \"${SUNSHINE_CLIENT_WIDTH}x${SUNSHINE_CLIENT_HEIGHT}\" --rate ${SUNSHINE_CLIENT_FPS} --output DP-1 --off"
    ```
  - Undo Command
    ```
    xrandr --output DP-1 --mode 1920x1080 --rate 60 --output DP-4 --off
    ```
  - Detached Commands
    ```
    setsid steam steam://open/bigpicture
    ```

My setup will differ from yours but run `xrandr` (Assuming you are using X11 as xrandr does not work with Wayland) to get an idea of what displays you have and what resolutions they support. In my case, DP-1 is DisplayPort 1 which is a 1080p 60hz physical monitor, and DP-4 is DisplayPort 2 which is a high refresh rate DisplayPort Emulator.

### Moonlight

[Moonlight](https://moonlight-stream.org/) GameStream client for PCs (Windows, Mac, Linux, and Steam Link)

[Moonlight Setup Guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide)

### MoonDeck

[MoonDeck](https://github.com/FrogTheFrog/moondeck) is a plugin that makes it easier to manage your gamestream sessions from the Steam Deck and integrates with Sunshine. If you are wanting to stream games to your Steam Deck I highly recommend using this plugin.

There are two components:

- [MoonDeck](https://github.com/FrogTheFrog/moondeck) plugin which you install through [Ducky](https://github.com/SteamDeckHomebrew/decky-loader) on your Steam Deck
- [MoonDeck Buddy](https://github.com/FrogTheFrog/moondeck-buddy) which you install on your streaming server and integrates with Sunshine.

_MoonDeck Buddy requires Steam to be installed first_

1. Install MoonDeck Buddy Pre-reqs (FUSE)
   ```
   sudo add-apt-repository universe
   sudo apt update
   sudo apt install -y libfuse2t64
   ```
1. Download MoonDeck Buddy
   ```
   mkdir ~/MoonDeck
   wget -O ~/MoonDeck/MoonDeckBuddy.AppImage https://github.com/FrogTheFrog/moondeck-buddy/releases/download/v1.6.2/MoonDeckBuddy-1.6.2-x86_64.AppImage
   chmod +x ~/MoonDeck/MoonDeckBuddy.AppImage
   ```
1. Launch MoonDeck Buddy
   ```
   ~/MoonDeck/MoonDeckBuddy.AppImage
   ```
1. With MoonDeck Buddy running, look in your system tray for an Xbox controller icon, this indicates the service is running. If you right click the icon you can enable the service to _Start on system startup_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Game Launchers

### Steam

1. Download the Steam Debian package
   ```
   wget https://cdn.fastly.steamstatic.com/client/installer/steam.deb
   ```
1. Install Steam
   ```
   sudo apt install -y -f ./steam.deb
   ```
1. Launch Steam
   ```
   steam
   ```
1. Configure Steam to auto start on login
1. Under _Storage_ add /mnt/games mount point and set it as the default
1. Under _Compatibility_ enable `Enable Steam Play for all other titles`

### Lutris

[Lutris](https://lutris.net/) is an open gaming platform for Linux. Lutris helps you install and play video games from all eras and from most gaming systems.

[Wine](https://www.winehq.org/) must be installed before you install Lutris

```
sudo dpkg --add-architecture i386
sudo mkdir -pm755 /etc/apt/keyrings
wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo gpg --dearmor -o /etc/apt/keyrings/winehq-archive.key -
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/noble/winehq-noble.sources
sudo apt update
sudo apt install -y --install-recommends wine-stable
```

1. Download the [latest version](https://github.com/lutris/lutris/releases) of [Lutris 0.5.18](https://github.com/lutris/lutris/releases/download/v0.5.18/lutris_0.5.18_all.deb)
   ```
   wget -O ~/Downloads/lutris.deb https://github.com/lutris/lutris/releases/download/v0.5.18/lutris_0.5.18_all.deb
   ```
1. Install Lutris
   ```
   sudo apt install -y -f ~/Downloads/lutris.deb
   ```
1. Launch Lutris
   ```
   lutris
   ```

### Heroic Game Launcher

[Lutris](https://lutris.net/) is an open gaming platform for Linux. Lutris helps you install and play video games from all eras and from most gaming systems.

1. Download the [latest version](https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher/releases) of [Heroic 2.15.2](https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher/releases/download/v2.15.2/heroic_2.15.2_amd64.deb)
   ```
   wget -O ~/Downloads/heroic.deb https://github.com/Heroic-Games-Launcher/HeroicGamesLauncher/releases/download/v2.15.2/heroic_2.15.2_amd64.deb
   ```
1. Install Heroic Game Launcher
   ```
   sudo apt install -y -f ~/Downloads/heroic.deb
   ```
1. Launch Heroic Game Launcher
   ```
   heroic
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Emulation

### EmuDeck

[EmuDeck](https://emudeck.github.io/) is a collection of scripts that allows you to autoconfigure your Steam Deck (works on Linux too), it creates your roms directory structure and downloads all of the needed Emulators for you along with the best configurations for each of them. EmuDeck works great with Steam Rom Manager or with EmulationStation DE.

1. Download prereqs
   ```
   sudo apt install -y bash flatpak git jq libfuse2 rsync unzip zenity
   ```
1. Install EmuDeck
   ```
   curl -L https://raw.githubusercontent.com/dragoonDorise/EmuDeck/main/install.sh | bash
   ```
1. Walk through initial setup
1. Copy BIOS
1. Copy ROMs
1. Add Emulation Station to Steam
   1. In Steam, go to `Games` menu
   1. `Add a Non-Steam Game to My Library...`
   1. Select `ES-DE AppImage`
   1. Rename the application in Steam to `EmulationStation`

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Utilities

### xone

[xone](https://github.com/dlundqvist/xone) is a Linux kernel driver for Xbox One and Xbox Series X|S accessories. Useful if you have an Xbox controller you want to hook up locally to your streaming server.

```
mkdir ~/git
cd ~/git
git clone https://github.com/dlundqvist/xone
cd ~/git/xone
sudo ./install.sh
sudo xone-get-firmware.sh --skip-disclaimer
```

### GameMode

[GameMode](https://github.com/FeralInteractive/gamemode) can optimise Linux system performance on demand.

1. Install GameMode
   ```
   sudo apt install -y gamemode
   ```
1. At this point you can modify games to launch with GameMode by changing the Launch Options for a game in Steam
   ```
   gamemoderun %command%
   ```
   GameMode can be used with MangoHud
   ```
   gamemoderun mangohud %command%
   ```

### MangoHud

[MangoHud](https://github.com/flightlessmango/MangoHud) A Vulkan and OpenGL overlay for monitoring FPS, temperatures, CPU/GPU load and more.

1. Install MangoHud
   ```
   sudo apt install -y mangohud
   ```
1. Create a MangoHud config
   ```
   mkdir -p ~/.config/MangoHud/
   wget -O ~/.config/MangoHud/MangoHud.conf https://raw.githubusercontent.com/flightlessmango/MangoHud/master/data/MangoHud.conf
   ```
1. At this point you can modify games to launch with MangoHud by changing the Launch Options for a game in Steam
   ```
   mangohud %command%
   ```
   MangoHud can be used with GameMode
   ```
   gamemoderun mangohud %command%
   ```

### Goverlay

[Goverlay](https://github.com/benjamimgois/goverlay) is an opensource project that aims to create a Graphical UI to help manage Linux overlays. A GUI for managing MangoHud config.

1. Install Goverlay
   ```
   sudo apt install -y goverlay
   ```
1. Launch Goverlay
   ```
   goverlay
   ```

### ProtonUp-QT

[ProtonUp-QT](https://github.com/DavidoTek/ProtonUp-Qt) install and manage GE-Proton, Luxtorpeda & more for Steam and Wine-GE & more for Lutris with this graphical user interface.

1. Download the [latest version](https://github.com/DavidoTek/ProtonUp-Qt/releases) of [ProtonUp-Qt-2.10.2](https://github.com/DavidoTek/ProtonUp-Qt/releases/download/v2.10.2/ProtonUp-Qt-2.10.2-x86_64.AppImage)
   ```
   mkdir ~/ProtonUp-QT
   wget -O ~/ProtonUp-QT/ProtonUp-QT.AppImage https://github.com/DavidoTek/ProtonUp-Qt/releases/download/v2.10.2/ProtonUp-Qt-2.10.2-x86_64.AppImage
   chmod +x ~/ProtonUp-QT/ProtonUp-QT.AppImage
   ```
1. Run ProtonUp-QT
   ```
   ~/ProtonUp-QT/ProtonUp-QT.AppImage
   ```
1. From here you can add various compatibility tools such as GE-Proton for Steam

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ADDITIONAL RESOURCES -->

## Additional Resources

### [Awesome Sunshine](https://github.com/LizardByte/awesome-sunshine)

A collection of awesome Sunshine scripts, tools, guides and companion software.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- OTHER CONSIDERATIONS -->

## Other Considerations

### Steam Remote Play

My experience with Steam Remote Play is it has lower quality with lag issues, assuming you can launch the game.

### Parsec

More of a commercial application that has a free and paid tier, in my limited testing it works connecting from a Linux client to a Windows PC with good performance.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->

## Roadmap

- [ ] Ansible Script
- [ ] Salt State

See the [open issues](https://github.com/tuxthepenguin84/ugss/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->

## Contact

Project Link: [https://github.com/tuxthepenguin84/ugss](https://github.com/tuxthepenguin84/ugss)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments

- [othneildrew/Best-README-Template](https://github.com/othneildrew/Best-README-Template)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/tuxthepenguin84/ugss.svg?style=for-the-badge
[contributors-url]: https://github.com/tuxthepenguin84/ugss/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/tuxthepenguin84/ugss.svg?style=for-the-badge
[forks-url]: https://github.com/tuxthepenguin84/ugss/network/members
[stars-shield]: https://img.shields.io/github/stars/tuxthepenguin84/ugss.svg?style=for-the-badge
[stars-url]: https://github.com/tuxthepenguin84/ugss/stargazers
[issues-shield]: https://img.shields.io/github/issues/tuxthepenguin84/ugss.svg?style=for-the-badge
[issues-url]: https://github.com/tuxthepenguin84/ugss/issues
[license-shield]: https://img.shields.io/github/license/tuxthepenguin84/ugss.svg?style=for-the-badge
[license-url]: https://github.com/tuxthepenguin84/ugss/blob/master/LICENSE.txt
[product-screenshot-1]: images/screenshot1.png
[product-screenshot-2]: images/screenshot2.png
[product-screenshot-3]: images/screenshot3.png
