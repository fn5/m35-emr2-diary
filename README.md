# m35-emr2-diary

A set of notes around the Telstra Smart Wi-Fi Booster 3 - M35H-EMR2 made by Arcaydan. It seems to have Arcaydan model WE7202242TA / RE-TA

The objective of this repo is to share the notes and debug functionality for self-educational purposes.
I have grabbed a few of these and hoping to understand more about how they work. 
My contact details are on my profile page if you would like to help me out. I am doing my best to do this the right way but it is my first public exploration.

I have connected to the PL011 and dumped the output in two cases.

> Normal is without interruption

>Interrupt1 is with key input over the PL011. This produces a console.

## To-do
* Dump interactive responses to a console explore file
* Post photos of internals
* Post packet capture between SMG3 and this device on pairing (captured, just need to sanitise)
* Access web interface - the Gen 2 had one that I managed to get onto, but it does an infinite redirect either when factory reset or paired
* Dump any firmware
* Get root access
* Understand how firmware is checked/updated
  

## Hardware specs

### Wi-fi chips
BCM43684 / BCM43684CKRFBG

https://www.broadcom.com/products/wireless/wireless-lan-infrastructure/bcm43684

### SoC
**BCM6755**KFEBG

https://www.broadcom.com/products/wireless/wireless-lan-infrastructure/bcm6755

### RAM
Winbond W634GU6NB-09 4Gbit / 512M DDR3L SDRAM

https://www.winbond.com/hq/product/specialty-dram/ddr3-sdram/?__locale=en&partNo=W634GU6NB

### NAND
Winbond W25N01GV 1Gbit / 128MB 

https://www.winbond.com/hq/product/code-storage-flash-memory/qspinand-flash/?__locale=en&partNo=W25N01GV

### Serial
AMBA PL011 UART

## Software specs
U-Boot TPL 2019.07 A01 (Jul 02 2021 - 23:34:48 +0800)

U-Boot SPL 2019.07 A01 (Jul 02 2021 - 23:35:01 +0800)

U-Boot 2019.07 A01 (Dec 08 2022 - 15:40:53 +0800) Arcadyan Build, Build: 5.04L.02@314035

Linux version 4.19.151 (tim@sw2-build9) (gcc version 9.2.0 (Buildroot 2019.11.1)) #1 SMP PREEMPT Thu Dec 8 15:13:49 CST 2022

 

