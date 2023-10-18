# ThinkSur-T430S
**I'm Not Responsible for Anything that Happens to Your Laptop, This EFI is Only for the Lazy people**
$${\color{red}DO \space IT \space AT \space YOUR \space OWN \space RISK}$$
**Please follow [Dortania's Guide](https://dortania.github.io/OpenCore-Install-Guide/)** instead

## My Spec:
 * CPU: Intel® Core™ i7-3520M 
 * GPU: Intel HD Graphics 4000  
 * Motherboard: Lenovo 2355JQU Ivy Bridge  
 * Wifi: Intel Centrino Advanced-N 6205  
 * Bluetooth: Broadcam  
 * Audio: ALC269VC Analog  
 * Ethernet: Intel 82579LM gigabit   
## Prerequisites
- [Python3](https://www.python.org/downloads/)
- A USB Drive 16GB+  
  
**Windows**
  - [Rufus](https://rufus.ie/en/)
  - [OpenCorePKG](https://github.com/acidanthera/OpenCorePkg/releases)

**MacOS**
  - [gibMacOS](https://github.com/corpnewt/gibMacOS)
  - [MountEFI](https://github.com/corpnewt/MountEFI)
## How to Install
1: **Download the EFI from the repository with**:  

    git clone https://github.com/Abdullah-Abdullah/ThinkSur-T430S   

  Or simply download it as a zip from `Code > Download ZIP`  

2: **Preparing the USB**:  
#### **Windows**:  
   - use [Rufus](https://github.com/Abdullah-78/BigThink-T430S#prerequisites) for formatting the USB as a FAT32  
   ![format-usb-rufus 43feba9e](https://github.com/Abdullah-78/BigThink-T430S/blob/main/Images/format-usb-rufus.43feba9e.png)

   - create a folder named `com.apple.recovery.boot` in the root of the USB drive, it should look like this:  
   ![com-efi-done a6fb730e](https://github.com/Abdullah-78/BigThink-T430S/blob/main/Images/com-efi-done.a6fb730e.jpeg)   

  - Open [OpenCorePKG](https://github.com/Abdullah-78/BigThink-T430S#prerequisites), navigate to `/Utilities/macrecovery/`, and open a new cmd from there as shown:
  ![open-cmd-current-folder 906148d4](https://github.com/Abdullah-78/BigThink-T430S/blob/main/Images/open-cmd-current-folder.906148d4.gif)

  - Type `python3 macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download` **or** `py macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download`  
   whatever works for you  

  - After downlaoding, you should get either `BaseSystem.dmg` and it's chunklist, or `RecoveryImage.dmg` and it's chunklist, put both of them in the `com.apple.recovery.boot` folder.

  

#### **MacOS**:  
  If you have access to another Mac, You could go with the same _online_ method as _Windows_, or an offline method (Which I recommend)

  Online Method:  
   - Basicly the same as we did in the _Windows_ method, but the main advantage of a mac is the offline method  

  Offline Method:
   - Open [gibMacOS](https://github.com/Abdullah-78/BigThink-T430S#prerequisites), double click `gibMacOS.command`, type `I` for printing the urls, and hit enter, you should see       MacOS versions as shown  
     ![MacOS Versions](https://github.com/Abdullah-78/BigThink-T430S/blob/main/Images/MacOS%20Versions.jpeg)

   -  look for the latest version for BigSur and type the number accordingly
   -  look for `InstallAssistant.pkg` and copy it's url  
   - Now that you have the url, download it using any download manager you perfer (I recommand `Wget`)

   - Once you're done downlaoding it, install it in you Mac by double clicking, and walk through the install  
       you should now see an app called `Install MacOS Big Sur`
   
   - Open Disk Utility and format your USB to `Mac OS Extended (Journaled)` with `GUID Partition Map` Scheme, and name it `MyVoulme`
 
   - Open the Terminal and paste this command:
       
           sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
       What this has done is copying the OS into your USB

   - Open [MountEFI](https://github.com/Abdullah-78/BigThink-T430S#prerequisites), double click `MountEFI.command`, you should see an option called `Install MacOS Big Sur`, type the number accordingly, this will mount the EFI partitoin of your USB
 
   - Copy the EFI folder into the `EFI` partition
 
2: **Booting**:  

 - Before booting from the usb, there is some BIOS settings you need to change:  
   **Disabled**:
   - Secure Boot
   - Fast Boot
   - ThunderBolt
     
   **Enabled**:
   - UEFI Only
   - CSM
   - Hyper-Threading
   - SATA Mode: AHCI
   - Virtualization
    
 - Once done, boot from the USB, and select `Install MacOS Big Sur`, give it a minute and it should boot into the recovery

 - open DiskUtility, click the view button, and show all devices, locate the HDD/SSD, and format it into `Apfs` with `GUID Partition Map` scheme, and name it what ever you want

 - Once done, select the install/restore MacOS Big Sur, and walk through the installation.

## Post Install  
If you managed to install it successfully then there is things I highly recommend you should do:  
 - Download [HeliPort](https://github.com/OpenIntelWireless/HeliPort/releases), and make it launch at login  
   **this enables the wifi**
 - Open the `System Preferences > Keyboard > Shortcuts > Mission Control`
   - **Mission Control** = `Control+Command+Up Arrow`
   - **Application Windows** = `Control+Command+Down Arrow`
   - **Move left a space** = `Control+Command+Right Arrow`
   - **Move right a space** = `Control+Command+Left Arrow`
     
   ***This enables the three fingers gestures***

## Troubleshooting
 - **Can't install the OS from the recovery because the image is corrupted or damaged**
   - If you are using a 2.0 USB, try 3.0
   - try an HDD/SSD 

       

  
  

