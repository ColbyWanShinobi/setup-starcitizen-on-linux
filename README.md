# Setup StarCitizen On Linux
This is intended as a rough guide for how to get Star Citizen working on Linux. It implies a small amount of general familiarity with Linux and is in no way intended for someone looking to install and use Linux for the first time.

Here's the environment this has been tested on:

- Distro: Ubuntu 22.04 LTS
- Kernel: 5.15.0-52-generic
- Motherboard/CPU/GPU Combo 1: 
    - Radeon RX 6900XT
    - X570 Aorus Master
    - R9 3900X
    - 128GB RAM
- Motherboard/CPU/GPU Combo 2: 
    - Radeon RX 5700XT
    - Z390 Designare
    - i9-9900K
    - 64GB RAM
- NVME SSD

This will hypothetically also work with Nvidia cards as well, but I haven't tried it in a while.

## Update your software repositories
```
sudo apt update
```

## Install the Required Dependencies
```
sudo apt install git make -y
```

## Install Lutris
https://github.com/lutris/lutris/releases

## Install Wine Dependencies
https://github.com/lutris/docs/blob/master/WineDependencies.md
```
sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install -y wine64 wine32 libasound2-plugins:i386 libsdl2-2.0-0:i386 libdbus-1-3:i386 libsqlite3-0:i386
```

## Install Drivers (AMD)
https://github.com/lutris/docs/blob/master/InstallingDrivers.md
```
sudo add-apt-repository ppa:kisak/kisak-mesa && sudo dpkg --add-architecture i386 && sudo apt update && sudo apt upgrade && sudo apt install libgl1-mesa-dri:i386 mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

## Install DXVK
https://github.com/doitsujin/dxvk/releases
```
tar -xvf dxvk-1.10.3.tar.gz 
cd dxvk-1.10.3/
./setup_dxvk.sh install
```

## System Config Change
https://lutris.net/games/star-citizen/
```
sudo nano /etc/sysctl.conf
```
Add this line to the file:
```
vm.max_map_count=16777216
```

Save and then run the following to apply the change
```
sudo sysctl -p
```

Now open the Lutris website, find the Star Citizen entry, and then click on the "Install" link. This should prompt you to open the Lutris app and then begin the installation.
https://lutris.net/games/star-citizen/ 
