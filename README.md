# TP-Link Archer C5 v4
## Installation via TFTP (Recovery mode)
<ul>
    <li> rename the OpenWrt-19.07.3-ramips-mt7620-tplink_c5-v4-squashfs-TFTP-recovery.bin to tp_recovery.bin</li>
   <li> start a TFTP server from IP address 192.168.0.66 and serve the image named tp_recovery.bin</li>
    <li> connect your device to the router LAN port (1-4)</li>
   <li> to start the TFTP recovery process on the router, press and hold the “Reset button” and then power up the router. Keep the “Reset button” pressed until the WPS LED turns on (it’s the LED with two arrows pointing in different directions)</li>
 </ul>
If everything went well, you should see a read request on your TFTP server

## Installation via serial connection
<ul>
    <li> rename the OpenWrt-19.07.2-ramips-mt7620-tplink_archer-c5-v4-squashfs-factory.bin to test.bin</li>
    <li> start a TFTP server from IP address 192.168.0.225 and serve the image named test.bin</li>
    <li>  connect your device to the router LAN port (1-4)</li>
   <li>  power up the router and press 4 on the console to stop the boot process</li>
  <li>  enter the following commands on the router console</li>
  </ul>
 ```
 tftp 0x80060000 test.bin
 erase tplink 0x20000 0x7a0000
 cp.b 0x80060000 0x20000 0x7a0000
 reset
```

 ### Stuck at bootloop
     * Setup everything the same as a serial connection. 
     * enter the following commands on the router console
 
```
erase tplink 0x20000 0x7a0000
cp.b 0x80060000 0x20000 0x7a0000
tftp 0x80060000 test.bin
erase tplink 0x20000 0x7a0000
cp.b 0x80060000 0x20000 0x7a0000
reset
```
## Update to stock
Force Flash `firmware_flash_stoc_by_openwrt_ru.bin` by OpenWrt web interface. After reboot, you will see the tplink interface at `192.168.0.1`. 
Then flash the latest firmware from the web interface. 

#### Check the pdf for more details. 

# Thanks
