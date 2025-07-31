
# Instructions To Flash Custom Rom
- Download the ROM package along with boot, dtbo, vendor_boot (links mentioned in post) and firmware as specified on post if not included in rom.
- Put downloaded files in a folder (your platform tools folder preferred)
- Reboot to fastboot (hold power + volume down button)
- In your PC, open terminal where you copied the above files and run the following commands:
```
fastboot flash boot boot.img
```
```
fastboot flash dtbo dtbo.img
```
```
fastboot flash vendor_boot vendor_boot.img
```
```
fastboot reboot recovery
```
- Format data via recovery (optional if flashing on the same ROM)
- Select "Reboot to recovery" (Advanced → Reboot to recovery)
- Select "Apply update" in recovery
- In your PC terminal, run adb sideload firmware.zip (replace firmware.zip with the downloaded firmware name)
- Then reboot recovery (not necessary tho) and select "Apply update"
- In your PC terminal, run adb sideload rom.zip (replace rom.zip with the downloaded ROM package name)
- If you are flashing a vanilla build and want to flash GApps, select "Reboot to recovery" (installation ends at 47% (95% for A16 builds) displayed on your PC terminal) and then sideload GApps by selecting "Apply update". Skip this step if you are already flashing a GApps build
- Reboot to system
 
# Some common errors:

First of all recovery here refers to boot.img, dtbo.img and vendor_boot.img files

- SPL downgrade, Flash aborted
  - If you got error something like that then you need an older recovery then the build itself. You can get recovery from older builds of any rom and then flash the rom you want.
  
- The downloaded rom package extension is .bin
  - You just need to rename the package and change .bin to .zip

- Device rebooted to classic bootloader whatever it is, maybe I will attach image too to clarify more
  - Nothing to worry just choose reboot bootloader and flash stock fastboot rom
![Classic Bootloader](https://i.ibb.co/1Y92zFXj/IMG-20250513-201944-808.jpg)   

- While sideloading rom it shows status 3 and flash aborted
  - You need to update adb version

- Device not showing in fastboot or adb
  - Maybe you need to install drivers, check Xiaomi Pad 6 Official or AOSP group for drivers

- fastboot is not recognised as an internal or external command
  - You need platform tools, check Xiaomi Pad 6 Official or AOSP group for adb or adbplus
