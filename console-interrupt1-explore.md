
### help
```
=> help
?         - alias for 'help'
arc_cnt_ramboot- ARC ramboot procedure base on rambootcounter
arc_preinit- ARC launches prepare service
arc_ramboot- ARC ramboot procedure
arc_upgrade_fit- ARC upgrade FIT image and switch to it
arc_wps_ramboot- ARC ramboot procedure if WPS button was pressed
base      - print or set address offset
bca_test  - Broadcom test commands
bdinfo    - print Board Info structure
blkcache  - block cache diagnostics and control
boot      - boot default, i.e., run 'bootcmd'
bootd     - boot default, i.e., run 'bootcmd'
bootefi   - Boots an EFI payload from memory
bootelf   - Boot from an ELF image in memory
bootm     - boot application image from memory
bootp     - boot image via network using BOOTP/TFTP protocol
bootvx    - Boot vxWorks from an ELF image
chpart    - change active partition
cmp       - memory compare
coninfo   - print console devices and information
cp        - memory copy
crc32     - checksum calculation
dcache    - enable or disable data cache
dm        - Driver model low level access
echo      - echo args to console
editenv   - edit environment variable
env       - environment handling commands
exit      - exit script
false     - do nothing, unsuccessfully
fdt       - flattened device tree utility commands
fstype    - Look up a filesystem type
go        - start application at address 'addr'
gpio      - query and control gpio pins
gpt       - GUID Partition Table
help      - print command description/usage
icache    - enable or disable instruction cache
iminfo    - print header information for application image
imxtract  - extract a part of a multi-image
itest     - return true/false on integer compare
led       - manage LEDs
ln        - Create a symbolic link
load      - load binary file from a filesystem
loadb     - load binary file over serial line (kermit mode)
loads     - load S-Record file over serial line
loadx     - load binary file over serial line (xmodem mode)
loady     - load binary file over serial line (ymodem mode)
loop      - infinite loop on address range
ls        - list files in a directory (default /)
md        - memory display
mm        - memory modify (auto-incrementing address)
mmc       - MMC sub system
mmcinfo   - display MMC info
mtd       - MTD utils
mtdparts  - define flash/nand partitions
mw        - memory write (fill)
nand      - NAND sub-system
nboot     - boot from NAND device
nfs       - boot image via network using NFS protocol
nm        - memory modify (constant address)
part      - disk partition related commands
ping      - send ICMP ECHO_REQUEST to network host
pinmux    - show pin-controller muxing
pmc       - Broadcom pmc commands
printenv  - print environment variables
reset     - Perform RESET of the CPU
run       - run commands in an environment variable
save      - save file to a filesystem
saveenv   - save environment variables to persistent storage
sdk       - Broadcom SDK support commands
setenv    - set environment variables
setexpr   - set environment variable as the result of eval expression
sf        - SPI flash sub-system
showvar   - print local hushshell variables
size      - determine a file's size
sleep     - delay execution for some time
source    - run script from memory
test      - minimal test like /bin/sh
tftpboot  - boot image via network using TFTP protocol
true      - do nothing, successfully
ubi       - ubi commands
ubifsload - load file from an UBIFS filesystem
ubifsls   - list files in a directory
ubifsmount- mount UBIFS volume
ubifsumount- unmount UBIFS volume
usb       - USB sub-system
usbboot   - boot from USB device
version   - print monitor, compiler and linker version
wdt       - Watchdog sub-system
```

### printenv

```
=> printenv
IMAGE=NAND:2M,128M
MCB=142f
arc_ov_id=0
boardid=WE7202242TA
bootcmd=arc_preinit;printenv;sdk boot_img
bootdelay=2
env_boot_magic=16384@0x40000,0xad000
ethact=systemport@0x80400000
ethaddr=[[ETHADDR]]
fdtcontroladdr=1defd888
filesize=500
init=/sbin/preinit
ipaddr=192.168.1.1
mtddevname=image
mtddevnum=1
mtdids=nand0=spi1.0
mtdparts=spi1.0:2097152(loader),131072000@2097152(image)
nand_erasesize=20000
nand_oobsize=40
nand_writesize=800
netmask=255.255.255.0
nummacaddrs=10
partition=nand0,1
rambootcounter=0
serverip=192.168.1.100
stderr=serial0
stdin=serial0
stdout=serial0

Environment size: 583/8188 bytes
```

### sdk
```
=> sdk
sdk - Broadcom SDK support commands

Usage:
sdk
force
 - Without arguments, display if forced image updates are enabled
force [force value] <[Boot Flash Type] [Image Flash Type]>
 - Enable(value=1)/Disable(value=0) forced image updates. All compatibility checks are ignored if enabled
 - If boot and image flash types are not detected, then they need to be specified as 2nd and 3rd args
 - Valid flash type values = [NAND|SPINAND|EMMC|NOR]
restoredefault
 - Delete contents of /data so that it gets populated with default values
metadata
metadata [committed] [valid],[valid]
 - without arguments, parse and display metadata
 - set metadata values (example "metadata 1 1,2" for both images valid and #1 committed)
 - NOTE: Must do a sw reset for metadata changes to take affect
flash_img_upgrade [-s] <filename> [conf]
flash_img_upgrade [-i] <filename> [<img> [<conf>]]
 - Download and flash an image upgrade bundle via TFTP
 - NOTE: Must do a sw reset to use the new image
load_img [boardid]
load_img [<img> [<boardid>]]
 - Load image from flash into DDR.
boot_img [boardid]
boot_img [<img> [<boardid>]]
 - Boot linux from image in flash.
[Legend - Optional Parameters]
 -s:      Skip downloading the image via tftp. Assume it is already at ${fileaddr}
 -i:      Inactive. Mark new image as inactive i.e do not commit image
 img:     Image index for flashing/booting. Valid values: [1|2]. Default index is determined from metadata
 boardid: Boardid to determine boot configuration. If omitted default configuration node is used
 conf:    Configuration name used for flashing img bundle. If omitted default configuration node is used

httpd_start
 - without arguments, start httpd server
otp set <row> <val> fuses <val> at <row> to OTP . Warning! otp fuse operations are irreverisble
otp get <row>       reads content at <row> from  OTP
otp secure          Achtung!!!!! This command will turn board to MFG boot secure mode.
                    On success the board will be halted and must be power cycled.
```

### pmc
```
=> pmc
pmc - Broadcom pmc commands

Usage:
pmc {avs | closeavs | cmd | log | pvtmon | tracktemp}
    - avs [enable | disable | show]
    - closeavs [<island>] <margin_mv_slow> <margin_mv_fast> [<maximum_mv> <minimum_mv>]
    - cmd <cmdnum> [<param1> [<param2> [<param3>]]]
    - log [<logtype>]
    - pvtmon [<select> [<island>]]
    - tracktemp [status | on | off]

=> pmc log

---start of pmc firmware boot log---
0001: PMC_VER:3.2.2
0002: $Change: 265063 $
0003: TS:200227_1013
0004: CHID:6755
0005: CREV:a1
0006: scratch: 0x00010000
0007: scratch: 0x00010001
0008: PARTID:47622 CFAM:6750 skipped chip id validation
0009: scratch: 0x00020000
0010: RO SVT 3401 HVT 1803 LVT 3603
0011: scratch: 0x00030000
0012: scratch: 0x00030022
0013: scratch: 0x00040000
0014: scratch: 0x00050000
0015: scratch: 0x00050001
0016: scratch: 0x00050002
0017: scratch: 0x00cc0000
0018: scratch: 0x00000000
0019: scratch: 0x00cc00ff
0020: scratch: 0x000002c6
0021: DAC: 682
0022: scratch: 0x000c0000
0023: scratch: 0x00000336
0024: DAC: 618
0025: scratch: 0x000c0001
0026: scratch: 0x00000317
0027: scratch: 0x000c0002
0028: scratch: 0x00000026
0029: DAC: 682
0030: scratch: 0x000c0003
0031: scratch: 0x00050003
0032: Dump all RO's on startup
0033: dev addr 0x25 RO type SVT value 4838 RO type HVT value 2946
0034: dev addr 0x30 RO type SVT value 4945 RO type HVT value 2957
0035: dev addr 0x31 RO type SVT value 4898 RO type HVT value 2872
0036: dev addr 0x32 RO type SVT value 4903 RO type HVT value 2957
0037: dev addr 0x33 RO type SVT value 4908 RO type HVT value 2940
0038: dev addr 0x34 RO type SVT value 4847 RO type HVT value 2918
0039: dev addr 0x35 RO type SVT value 4897 RO type HVT value 2911
0040: dev addr 0x36 RO type SVT value 4883 RO type HVT value 2928
0041: dev addr 0x37 RO type SVT value 4996 RO type HVT value 2966
0042: dev addr 0x38 RO type SVT value 4908 RO type HVT value 2948
0043: dev addr 0x39 RO type SVT value 4936 RO type HVT value 2917
0044: dev addr 0x3a RO type SVT value 4927 RO type HVT value 2953
0045: dev addr 0x3b RO type SVT value 4895 RO type HVT value 2961
0046: scratch: 0x00050004
0047: scratch: 0x00050005
0048: DAC: 682
0049: Dump all RO's on vhigh_mv 1006
0050: dev addr 0x25 RO type SVT value 4838 RO type HVT value 2947
0051: dev addr 0x30 RO type SVT value 4946 RO type HVT value 2958
0052: dev addr 0x31 RO type SVT value 4899 RO type HVT value 2872
0053: dev addr 0x32 RO type SVT value 4904 RO type HVT value 2955
0054: dev addr 0x33 RO type SVT value 4908 RO type HVT value 2940
0055: dev addr 0x34 RO type SVT value 4848 RO type HVT value 2919
0056: dev addr 0x35 RO type SVT value 4896 RO type HVT value 2910
0057: dev addr 0x36 RO type SVT value 4884 RO type HVT value 2929
0058: dev addr 0x37 RO type SVT value 4995 RO type HVT value 2967
0059: dev addr 0x38 RO type SVT value 4908 RO type HVT value 2949
0060: dev addr 0x39 RO type SVT value 4937 RO type HVT value 2916
0061: dev addr 0x3a RO type SVT value 4929 RO type HVT value 2954
0062: dev addr 0x3b RO type SVT value 4895 RO type HVT value 2962
0063: DAC: 618
0064: Dump all RO's on vlow_mv 969
0065: dev addr 0x25 RO type SVT value 4536 RO type HVT value 2692
0066: dev addr 0x30 RO type SVT value 4636 RO type HVT value 2701
0067: dev addr 0x31 RO type SVT value 4593 RO type HVT value 2618
0068: dev addr 0x32 RO type SVT value 4597 RO type HVT value 2698
0069: dev addr 0x33 RO type SVT value 4604 RO type HVT value 2683
0070: dev addr 0x34 RO type SVT value 4542 RO type HVT value 2663
0071: dev addr 0x35 RO type SVT value 4594 RO type HVT value 2656
0072: dev addr 0x36 RO type SVT value 4581 RO type HVT value 2674
0073: dev addr 0x37 RO type SVT value 4685 RO type HVT value 2708
0074: dev addr 0x38 RO type SVT value 4603 RO type HVT value 2693
0075: dev addr 0x39 RO type SVT value 4633 RO type HVT value 2662
0076: dev addr 0x3a RO type SVT value 4626 RO type HVT value 2697
0077: dev addr 0x3b RO type SVT value 4590 RO type HVT value 2705
0078: RO[0] target_ro 3401 low_ro 4535 slope 10133 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 833
0079: RO[1] target_ro 1803 low_ro 2618 slope 8466 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 852
0080: RO[2] target_ro 3603 low_ro 65535 vlow_mv 969 dac_low 618 high_ro 65535 vhigh_mv 1006 dac_high 682
0081: RO[3] target_ro 3603 low_ro 5018 slope 8200 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 758
0082: RO[4] target_ro 3401 low_ro 4716 slope 10300 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 813
0083: RO[5] target_ro 2785 low_ro 3929 slope 8500 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 805
0084: RO[6] target_ro 1803 low_ro 2764 slope 8633 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 833
0085: RO[7] target_ro 4882 low_ro 6760 slope 10900 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 758
0086: RO[8] target_ro 4528 low_ro 6338 slope 13800 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 809
0087: RO[9] target_ro 3713 low_ro 5237 slope 11333 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 805
0088: RO[10] target_ro 2426 low_ro 3759 slope 11566 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 828
0089: RO[11] target_ro 14053 low_ro 19793 slope 31033 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 743
0090: RO[12] target_ro 12892 low_ro 18271 slope 39533 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 802
0091: RO[13] target_ro 10698 low_ro 15178 slope 32900 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 802
0092: RO[14] target_ro 6847 low_ro 10764 slope 34300 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 829
0093: RO[15] target_ro 10186 low_ro 14368 slope 25766 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 770
0094: RO[16] target_ro 9008 low_ro 12515 slope 30133 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 827
0095: RO[17] target_ro 7496 low_ro 10730 slope 25800 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 816
0096: RO[18] target_ro 4715 low_ro 7375 slope 25400 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 842
0097: RO[19] target_ro 9514 low_ro 13731 slope 24166 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 756
0098: RO[20] target_ro 8296 low_ro 12503 slope 29066 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 793
0099: RO[21] target_ro 6959 low_ro 10895 slope 24933 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 777
0100: RO[22] target_ro 4550 low_ro 7439 slope 24566 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 826
0101: RO[23] target_ro 5546 low_ro 8379 slope 16066 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 753
0102: RO[24] target_ro 4824 low_ro 7431 slope 18500 vlow_mv 969 dac_low 618 vhigh_mv 1006 dac_high 682 voltage_mv 797
0103: avs_dac 499 predict_mv 852 avs_mv 901 calc_margin_mv 49 calc_swreg_mv 2009 dac_high 682 dac_low 618
0104: DAC: 682
0105: Dump all RO's on vhigh_mv 1007
0106: dev addr 0x25 RO type SVT value 4837 RO type HVT value 2947
0107: dev addr 0x30 RO type SVT value 4946 RO type HVT value 2957
0108: dev addr 0x31 RO type SVT value 4899 RO type HVT value 2873
0109: dev addr 0x32 RO type SVT value 4903 RO type HVT value 2956
0110: dev addr 0x33 RO type SVT value 4909 RO type HVT value 2941
0111: dev addr 0x34 RO type SVT value 4848 RO type HVT value 2919
0112: dev addr 0x35 RO type SVT value 4896 RO type HVT value 2911
0113: dev addr 0x36 RO type SVT value 4884 RO type HVT value 2929
0114: dev addr 0x37 RO type SVT value 4996 RO type HVT value 2967
0115: dev addr 0x38 RO type SVT value 4908 RO type HVT value 2949
0116: dev addr 0x39 RO type SVT value 4935 RO type HVT value 2918
0117: dev addr 0x3a RO type SVT value 4929 RO type HVT value 2954
0118: dev addr 0x3b RO type SVT value 4894 RO type HVT value 2962
0119: DAC: 531
0120: Dump all RO's on vlow_mv 918
0121: dev addr 0x25 RO type SVT value 4099 RO type HVT value 2331
0122: dev addr 0x30 RO type SVT value 4194 RO type HVT value 2337
0123: dev addr 0x31 RO type SVT value 4155 RO type HVT value 2259
0124: dev addr 0x32 RO type SVT value 4158 RO type HVT value 2333
0125: dev addr 0x33 RO type SVT value 4165 RO type HVT value 2320
0126: dev addr 0x34 RO type SVT value 4105 RO type HVT value 2301
0127: dev addr 0x35 RO type SVT value 4156 RO type HVT value 2297
0128: dev addr 0x36 RO type SVT value 4147 RO type HVT value 2313
0129: dev addr 0x37 RO type SVT value 4241 RO type HVT value 2343
0130: dev addr 0x38 RO type SVT value 4165 RO type HVT value 2332
0131: dev addr 0x39 RO type SVT value 4197 RO type HVT value 2301
0132: dev addr 0x3a RO type SVT value 4189 RO type HVT value 2336
0133: dev addr 0x3b RO type SVT value 4151 RO type HVT value 2343
0134: RO[0] target_ro 3401 low_ro 4099 slope 10136 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 834
0135: RO[1] target_ro 1803 low_ro 2258 slope 8424 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 852
0136: RO[2] target_ro 3603 low_ro 65535 vlow_mv 918 dac_low 531 high_ro 65535 vhigh_mv 1007 dac_high 682
0137: RO[3] target_ro 3603 low_ro 4659 slope 8273 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 762
0138: RO[4] target_ro 3401 low_ro 4272 slope 10315 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 815
0139: RO[5] target_ro 2785 low_ro 3563 slope 8506 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 806
0140: RO[6] target_ro 1803 low_ro 2396 slope 8602 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 834
0141: RO[7] target_ro 4882 low_ro 6281 slope 11041 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 763
0142: RO[8] target_ro 4528 low_ro 5740 slope 13835 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 811
0143: RO[9] target_ro 3713 low_ro 4748 slope 11356 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 806
0144: RO[10] target_ro 2426 low_ro 3264 slope 11534 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 829
0145: RO[11] target_ro 14053 low_ro 18424 slope 31506 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 748
0146: RO[12] target_ro 12892 low_ro 16559 slope 39726 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 805
0147: RO[13] target_ro 10698 low_ro 13743 slope 33205 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 806
0148: RO[14] target_ro 6847 low_ro 9304 slope 34082 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 829
0149: RO[15] target_ro 10186 low_ro 13251 slope 25890 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 773
0150: RO[16] target_ro 9008 low_ro 11226 slope 30123 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 828
0151: RO[17] target_ro 7496 low_ro 9630 slope 25630 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 816
0152: RO[18] target_ro 4715 low_ro 6314 slope 24958 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 839
0153: RO[19] target_ro 9514 low_ro 12676 slope 24397 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 759
0154: RO[20] target_ro 8296 low_ro 11245 slope 29164 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 794
0155: RO[21] target_ro 6959 low_ro 9815 slope 25041 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 778
0156: RO[22] target_ro 4550 low_ro 6400 slope 24342 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 825
0157: RO[23] target_ro 5546 low_ro 7689 slope 16041 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 755
0158: RO[24] target_ro 4824 low_ro 6645 slope 18356 vlow_mv 918 dac_low 531 vhigh_mv 1007 dac_high 682 voltage_mv 796
0159: avs_dac 503 predict_mv 852 avs_mv 901 calc_margin_mv 49 calc_swreg_mv 2021 dac_high 682 dac_low 531
0160: AVS closed on dac_code 503 calc_swreg_mv 2021 target_mv 901 calc_swreg_dac 144
0161: AVS island 0 margin_mv_slow 80 margin_mv_fast 40 maximum_mv 1034 minimum_mv 859
0162: DAC: 503
0163: Setting Thresholds for 0 hi 3795 lo 3722
0164: Setting Thresholds for 1 hi 2183 lo 2120
0165: Setting Thresholds for 2 hi 2309 lo 2242
0166: Setting R48_0 Thresholds hi 3825 lo 3758
0167: Setting R48_1 Thresholds hi 3759 lo 3686
0168: Setting R48_2 Thresholds hi 3091 lo 3025
0169: Setting R48_3 Thresholds hi 2145 lo 2082
0170: Setting R48_4 Thresholds hi 5206 lo 5108
0171: Setting R48_5 Thresholds hi 5100 lo 4981
0172: Setting R48_6 Thresholds hi 4116 lo 4028
0173: Setting R48_7 Thresholds hi 2852 lo 2771
0174: Setting R48_8 Thresholds hi 14919 lo 14620
0175: Setting R48_9 Thresholds hi 14221 lo 13932
0176: Setting R48_10 Thresholds hi 11829 lo 11583
0177: Setting R48_11 Thresholds hi 8044 lo 7818
0178: Setting R48_12 Thresholds hi 10970 lo 10752
0179: Setting R48_13 Thresholds hi 10211 lo 9984
0180: Setting R48_14 Thresholds hi 8413 lo 8226
0181: Setting R48_15 Thresholds hi 5706 lo 5529
0182: Setting R48_16 Thresholds hi 10498 lo 10191
0183: Setting R48_17 Thresholds hi 9512 lo 9229
0184: Setting R48_18 Thresholds hi 7637 lo 7459
0185: Setting R48_19 Thresholds hi 5441 lo 5270
0186: Setting R48_20 Thresholds hi 5981 lo 5841
0187: Setting R48_21 Thresholds hi 5387 lo 5256
0188: scratch: 0x00050006
0189: scratch: 0x00050008
0190: scratch: 0x00060000
0191: scratch: 0x00070000
0192: scratch: 0x00080000

====end of pmc firmware boot log====
start showing pmc firmware live log, press any key to stop ...

... key pressed, stop showing pmc firmware live log.
=>
```

### tftp
```
=> tftp
*** Warning: no boot file name; using 'C0A80101.img'
Using systemport@0x80400000 device
TFTP from server 192.168.1.100; our IP address is 192.168.1.1
Filename 'C0A80101.img'.
Load address: 0x1000000
Loading: *
TFTP error: 'File not found' (1)
Not retrying...
```
