# The STM32 Bootloader
---
The STM32 Bootloader lives on all STM32 chips. The bootloader is used to load files (bootloaders and/or firmware) onto the chip. Several TinyCLR OS supported boards use this bootloader.

These instructions apply to all STM32 chips with built in USB and DFU features.

## Loading the GHI Bootloader v2
The bootloader often comes pre-installed on our devices. It only needs to be installed once. It does not need to be reinstalled unless it becomes erased or corrupted.
1. Download and save the latest [bootloader file](ghi-bootloader.md#downloads) (v2.x.x).
2. Download and install the [DfuSe USB device firmware upgrade software](http://www.st.com/en/development-tools/stsw-stm32080.html#getsoftware-scroll) from STMicroelectronics (click on the blue [**Get Software**](http://www.st.com/en/development-tools/stsw-stm32080.html#getsoftware-scroll) button).
3. Run the DfuSeDemo program installed in the previous step. It should appear in the programs menu under `STMicroelectronics`.
4. Put your board in DFU (Device Firmware Upgrade) mode. Instructions for putting your device in DFU mode are found on the documents page for the board you are using. `STM Device in DFU Mode` should now appear under `Available DFU Devices` at the upper left of the DfuSe Demo program screen.
5. Near the bottom of the DfuSe Demo program window click on the `Choose...` button. Find the bootloader file you saved in step 1 (...Bootloader v2.x.x.dfu), click on it and click on the `Open` button.
6. Now click on the upgrade button. If a dialog box appears with `Your device was plugged in DFU mode...` click the `Yes` button.
7. You should see a message at the bottom of the DfuSe Demo window saying the upgrade was successful. Now reset the your device or click on the `Leave DFU mode` button.
8. Congratulations! You have successfully installed the GHI STM32 bootloader!

## Creating a DFU file
The DfuSe upgrade software only accepts DFU file types. You can create DFU files from .hex or .bin files using the DFU file manager software which is part of the [DfuSe USB device firmware upgrade software](http://www.st.com/en/development-tools/stsw-stm32080.html#getsoftware-scroll) download from step 2 of the above instructions.

If you haven't already, download the [DfuSe USB device firmware upgrade software](http://www.st.com/en/development-tools/stsw-stm32080.html#getsoftware-scroll) from STMicroelectronics (click on the blue [**Get Software**](http://www.st.com/en/development-tools/stsw-stm32080.html#getsoftware-scroll) button).

The instructions are slightly different depending on whether you are starting with a .hex or .bin file.

### From .hex files
1. Find and open the "Dfu file manager" program. It should appear in the programs menu under `STMicroelectronics`. Select `I want to generate a DFU file`.
2. Click on the `S19 or Hex...` button to select the .hex file.
3. Click `Generate...`
4. You now have a DFU file!

### From .bin files
1. Find and open the "Dfu file manager" program. It should appear in the programs menu under `STMicroelectronics`. Select `I want to generate a DFU file`.
2. Click on `Multi BIN...` button to select the .bin file.
3. Change the address to 08000000
4. Click on the `Add to list >>` button then click the `OK` button.
5. Click `Generate...`
6. You now have a DFU file!

## Uploading DFU Files
To set the STM32 chip in DFU mode, BOOT1 pin (if available) needs to be low and and BOOT0 needs to be high when the system powers up. If your system has a BOOT1 or BOOTA button, just hold the button down while powering the system up. The device manager will see a device called `STM Device in DFU Mode`.
1. Find and open the `DfuSe Demo` program (from the ST download higher in this page).
2. Under `Upgrade and Verify Action`, click the `Choose...` button and select the firmware DFU file you want to load.
3. Click the `Upgrade` button.
4. Click the `Leave DFU mode` button or reset the device.
5. Congratulations, your board is now running the loaded firmware!
