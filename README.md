# ZYNQ7010/7020_AD9363/AD9364/AD9361
####  Open source SDR hardware based on ZYNQ+AD936X

Project introduction video:https://www.youtube.com/watch?v=Qk-M8yRsKvs 

​                                               https://www.youtube.com/watch?v=xx4MXQSHmCM&t=153s

GSM signals received test:https://www.youtube.com/watch?v=yFEpSrWW0-w

FM signal received test:https://www.youtube.com/watch?v=ASb7dLIEmfY

Sine wave signal transmission test:https://www.youtube.com/watch?v=bfs_GfULIoA&t=55s

Local loopback signal test:https://www.youtube.com/watch?v=JOjsKboq0xA

The pluto-sdr firmware transplantation work is all completed, flashing the firmware without hacking the system, the default is AD9364.

Regarding the BOM cost, ZYNQ7010/ZYN17020 and AD9363 cost about 150-200 RMB when using the disassembled chip. The use of brand-new chips does not have bargaining power due to the small number of BOM costs around 1,000 RMB.

##### 1. Hardware solution

FPGA: ZYNQ7010/7020 (ZYNQ7010 and ZYNQ7020 can be replaced with each other, if you need more hardware resources, please use ZYNQ7020)

RF: AD9361/AD9363/AD9364 (the three chips can be replaced with each other, the difference lies in the bandwidth. Among them, AD9361 has better performance, try to use the ABCZ ending chip, which is different from BBCZ)

RAM Memory: DDR3 256M16

USB-PHY: USB3320C

GMAC-PHY: RTL8211E-VL (RTL8211E has two endings, VB and VL, where VB level is 3.3V/2.5V, VL is 1.8V)

QSPI FLASH: W25Q256 32MB

Power supply topology diagram

![power](images/power.png)

block design

![blockdesign](images/blockdesign.png)

##### 2. Software resources

Support Pluto-SDR firmware transplantation, OpenWiFi (ZYNQ7020 FPGA required), support adi official ZED+AD-FMCOMMS2/3/4 related firmware code

##### 3. PCB board design

Design software:  Altium Designer Kicad

Number of layers: 4 layers （signal layer[1]、GND[2]、POWER[3]、signal layer[4]）

Craft: JLC PCB Craft

Impedance: not supported

The impedance version will be tested in March 2021, and the openwifi port is currently undergoing normal transceiver tests.

##### 4. Differences compared to ADALM-PLUTO:

- Support for Zynq-7020 and Zynq-7010 in 400pin BGA package
- Support 2R2T transceiver mode
- 4 layer board to reduce cost
- SD slot for running real Linux distros
- Support Gigabit Ethernet

##### 5. Project display:

This is the PCB rendering

![2](images/grade.png)

This is the physical picture of the PCB

![](images/IMG_8132.JPG)

This is the details of the PCB RF part

![](images/IMG_8133.JPG)

Ethernet can work stably at 1000M (using single-arm routing for testing in the figure)

![eth](images/500m.JPG)

AD9363 initializes the normal graph using adi no-os test environment

<img src="images/csh.png" alt="eth" style="zoom:50%;" />

Pluto-uboot transplanted successfully

![eth](images/pluto-system.png)

Pluto firmware works fine

![](images/IMG_8016.PNG)

Receive GSM signal normally

![](images/iio.png)

Hack into AD9364 to receive FM signal

![pj](images/pj.png)

Two PCBAs receive and send each other test

![IMG_8018](images/IMG_8129.JPG)

PCBAs can be stacked on each other and connected through Gigabit switches and routers

![IMG_8018](images/IMG_8131.JPG)

Support SDR-SHARP

![sdrsharp](images/sdrsharp.jpg)

##### 6.TO DO LIST

- Continue to optimize the RF part to reach the adi official demo board indicators
- Impedance design based on four-layer pcb
- To be completed in January-February of 2021, to complete the relevant transplantation work of openwifi
- Design the impedance version in March 2021
- Conduct commercial index tests on the impedance version in April 2021
- When the commercial version is launched at the end of April 2021, it will support adi's official SDR firmware (ADRV9364 packet), openwifi, and openbts openbts, etc.

