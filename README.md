# BigThink-T430S
A Pre-built MacOS BigSur EFi for Lenovo ThinkPad T430S

## My Spec:
 * CPU: I7 3520M  
 * GPU: Intel HD Graphics 4000  
 * Motherboard: Lenovo 2355JQU Ivy Bridge  
 * Wifi: Intel Centrino Advanced-N 6205  
 * Bluetooth: Broadcam  
 * Audio: ALC 296VC Analog  
 * Ethernet: Intel 82579LM gigabit   

 _`Note: I'm Not Responsible for Anything that Happens to Your Laptop, Double Check That You Have the Exact Same Laptop`_

## How to Install
0: **Make sure you have `Python3` Installed in your system**  

1: **Download the EFI from the repository with**:  

    git clone https://github.com/Abdullah-78/BigThink-T430S   

  Or simply download it as a zip from `Code > Download ZIP`  

2: **Preparing the USB**:  
#### **Windows**:  
   - use `Rufus` for formatting the USB as a FAT32  

     - _`Note`: if you are planning to do it from windows, then you would need to create a folder named `com.apple.recovery.boot` in the root of the USB drive, it shoulf look like this:_  
   ![com-efi-done a6fb730e](https://github.com/Abdullah-78/BigThink-T430S/assets/115571443/2677f74d-1986-4adc-8066-c8d7218f56d5)   

  - Downlaod [OpenCorePKG](https://github.com/acidanthera/OpenCorePkg/releases), navigate to `/Utilities/macrecovery/`, and open a new cmd from there, and type `python3 macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download` or `py macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download`  
   whatever works for you  

  - After downlaoding, you should get either `BaseSystem,dmg` and it's chunklist, or `RecoveryImage.dmg` and it's chunklist, put whatever appears in the `com.apple.recovery.boot` folder.

  

#### **MacOS**:  
  If you have access to another Mac, You could go with the same _online_ method as _Windows_, or an offline method (Which I recommend)

  Online Method:  
   - Basicly the same as we did in the _Windows_ method, but the main advantage of a mac is the offline method

  Offline Method:
   - Downlaod [gibMacOS](https://github.com/corpnewt/gibMacOS), double click `gibMacOS.command`, type `I` for printing the urls, and hit enter, you should see MacOS versions, look for the latest version for BigSur and type the number accordingly, look for `InstallAssistant.pkg` and copy it's url
       Now that you have the url, download it using any download manager you perfer (I recommand `Wget`)

   - Once you're done downlaoding it, install it in you Mac by double click, and walk through the install
       you should now see an app called `Install MacOS Big Sur`
   
   - Open DiskUtility and format your USB to `Mac OS Extended (Journaled)` with `GUID Partition Map` Scheme, and name it `MyVoulme`
 
   - Open the Terminal and paste this command:
       
           sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
       What this has done is copying the OS into your USB

   - Download [MountEFI](https://github.com/corpnewt/MountEFI), double click `MountEFI.command`, you should see an option called `Install MacOS Big Sur`, type the number accordingly, this will mount the EFI partitoin of your USB
 
   - Copy my EFI folder into the `EFI` partition
 
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

       

  
  

