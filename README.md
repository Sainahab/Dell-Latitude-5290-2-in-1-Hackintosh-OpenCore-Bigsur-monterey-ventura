# Dell Latitude 5290 2 in 1 Hackintosh OpenCore Bigsur monterey ventura
 step by step guide to hackintosh your dell latitude 5290 2in 1

## Specifics

- CPU : Intel® Core™ i5-8350U Processor (6M Cache, up to 3.60 GHz)
- Graphics : Intel® UHD Graphics 620
- Memory : Samsung LPDDR3 16GB 1867MHZ (8GB * 2 Dual Channel)
- Display : 12.3 Inch 1920 X 1280 (WUXGA+) 3:2 10 Points Multi Touch
- Sound : Realtek ALC3253 (ALC225)
- Samsung NVMe SSD 512GB
- WiFi/Bluethooth : Intel BCM94352Z(DW1560) (WWAN Slot * 1)
- Battery : 42WHr


## BIOS Version / OpenCore Bootloader Version / macOS Version Supported

- BIOS : 1.17.0
- OpenCore Bootloader : v0.9 and Above
- macOS : Big Sur 11.7.10, Monterey 12.7, Ventura upto 13.3


## BIOS Setup

- Load Optimized Defaults

## Step by step how to :

# 1st Step is to boot Big sur
 - Follow dortania guide to make bootable usbstick for BIG SUR 11.7 macos (not montery/not ventura)  : https://dortania.github.io/OpenCore-Install-Guide/installer-guide/
# 2nd Step copy Big Sur EFI to usb
 - copy Efi folder (inside 1 - EFI BIG sur) to usb stick root.
 - now your usb root should have 2 folders {com.apple.recovery.boot & EFI}

<img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/com-efi-done.a6fb730e.png" alt="">

# 3nd Step config.plist config
 - download ProperTree and GenSMBIOS
            -   https://github.com/corpnewt/ProperTree
            -   https://github.com/corpnewt/GenSMBIOS
 - Next, let's open ProperTree and edit our config.plist:

    * ProperTree.command
      ** For macOS
    * ProperTree.bat
      ** For Windows

    Once ProperTree is running, open your config.plist by pressing Cmd/Ctrl + O and selecting the config.plist file on your USB.

 - For setting up the SMBIOS info, we'll use GenSMBIOS application.

    
    <img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/smbios.35dd8ead.png" alt="">

    Run GenSMBIOS, pick option 1 for downloading MacSerial and Option 3 for selecting out SMBIOS. 
    This will give us an output similar to the following:

        #######################################################
        #               MacBookPro15,2 SMBIOS Info                  #
        #######################################################

        Type:         MacBookPro15,2
        Serial:       C02KCYZLDNCW
        Board Serial: C02309301QXF2FRJC
        SmUUID:       A154B586-874B-4E57-A1FF-9D6E503E4580


        The Type part gets copied to Generic -> SystemProductName.

        The Serial part gets copied to Generic -> SystemSerialNumber.

        The Board Serial part gets copied to Generic -> MLB.

        The SmUUID part gets copied to Generic -> SystemUUID.

        We set Generic -> ROM to either an Apple ROM (dumped from a real Mac), your NIC MAC address, or any random MAC address (could be just 6 random bytes, for this guide we'll use 11223300 0000. After install follow the Fixing iServices ( https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html ) on how to find your real MAC Address)

        Reminder that you need an invalid serial! When inputting your serial number in Apple's Check Coverage Page , you should get a message such as "Unable to check coverage for this serial number."

        Automatic: YES

        Generates PlatformInfo based on Generic section instead of DataHub, NVRAM, and SMBIOS sections
        #Generic

# 4nd Step Booting the OpenCore USB

     - boot usb stick and finish instalation.

# 5nd Step : OpenCore Post-Install
     - follow this guide to Booting without USB and Fixing iServices

# 5nd Step update to Monterey or Ventura
    
     - download Monterey or ventura dmg and do the update but before rebooting make sure to replace EFI folder with corresponded files , for Moneterey use monterey EFi and ventura use ventura EFI  (don't forget to replace SMBIOS Info in the new EFI files) .