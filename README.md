# XGL-FlowIO
This repo contains all the files and information for setting up the FlowIO system using the instructions at: [https://www.softrobotics.io/flowio](https://www.softrobotics.io/flowio)
## Flashing the nRF52832 board
In step 6 "Microcontroller prep" of the flowio setup instructions when trying to burn the bootloader this error may apear. 
    
    0.6.2_s140_6.1.1.zip. Flow control is disabled, Dual bank, Touch 1200
    Touched serial port COM10
    
    Failed to upgrade target. Error is: Serial port could not be opened on COM10. Reason: could not open port 'COM10': FileNotFoundError(2, 'The system cannot find the file specified.', None, 2)
    Traceback (most recent call last):
      File "dfu\dfu_transport_serial.py", line 113, in open
      File "serial\serialwin32.py", line 33, in __init__
      File "serial\serialutil.py", line 244, in __init__
      File "serial\serialwin32.py", line 64, in open
    serial.serialutil.SerialException: could not open port 'COM10': FileNotFoundError(2, 'The system cannot find the file specified.', None, 2)
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "__main__.py", line 296, in serial
      File "dfu\dfu.py", line 226, in dfu_send_images
      File "dfu\dfu.py", line 157, in _dfu_send_image
      File "dfu\dfu_transport_serial.py", line 115, in open
    nordicsemi.exceptions.NordicSemiException: Serial port could not be opened on COM10. Reason: could not open port 'COM10': FileNotFoundError(2, 'The system cannot find the file specified.', None, 2)
    
    Possible causes:
    - Selected Bootloader version does not match the one on Bluefruit device.
        Please upgrade the Bootloader or select correct version in Tools->Bootloader.
    - Baud rate must be 115200, Flow control must be off.
    - Target is not in DFU mode. Ground DFU pin and RESET and release both to enter DFU mode.
If you run into this error then double press the reset button on the board until the board shows up as a drive in your file explorer under the name `NRF52BOOT`. You can then follow the bootloader steps like normal.
You may also run into the same issue when trying to upload new code to the board. This is also fixed in the same way. 

If the bootload still isn't working there are alternate ways to update the bootloader here: https://learn.adafruit.com/introducing-the-adafruit-nrf52840-feather/update-bootloader 