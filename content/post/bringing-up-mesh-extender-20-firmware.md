+++
date = "2017-04-27"
title = "Bringing up the  Mesh Extender 2.0 firmware image in NZ"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-26146254920056714" itemprop="description articleBody">
Here in NZ with our friends from the NZ Red Cross IT &amp; Telecommunications Emergency Response Unit (ERU), we are getting ready to use some of the prototype Mesh Extender 2.0s as part of a Red Cross South Island exercise. <br/>
<br/>
While I just managed to get the 8 prototype units built up in time to fly out, I didn't have time to get the firmware image ready.  So that's what I have been doing for the past couple of days here.<br/>
<br/>
One of the big problems for getting the firmware working, is that with the RFD900+ radio on the serial port, it's rather hard to tell what is happening during the boot process.  Couple that with some ~5 - 20 minute boot delays that I was trying to debug, this was not ideal.<br/>
<br/>
My solution has been to enable the busybox httpd on the Mesh Extenders early in the boot process, and write some scripts that emit progress messages to a web page, similar to the Linux console boot messages.  The result is that after only 20 seconds from power-on, I can start seeing what is going on.  Here is the result after I implemented this and fixed a number of the delay problems:<br/>
<br/>
<h1>
<span>Serval Mesh Extender 2.0 -- Booting</span></h1>
<span>System booting for 85 seconds.</span><br/>
<table padding="2"><tbody>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+20</span></td><td><span>Entering S47mountstuff</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+21</span></td><td><span>Making sure bulk storage unmounted</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+21</span></td><td><span>Checking integrity of /serval</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+23</span></td><td><span>Checking integrity of /serval-var</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+28</span></td><td><span>Checking integrity of /dos</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+36</span></td><td><span>Mounted /dos</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+36</span></td><td><span>Mounted /serval</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+36</span></td><td><span>Finished mounting file systems</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+36</span></td><td><span>Reading Radio EEPROM settings</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Read Radio EEPROM settings (5 lines)</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Exiting S47mountstuff</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Entering S49servald</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Reseting /etc/inittab to default</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>/etc/inittab ok</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Setting up SERVALINSTANCE_PATH</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+43</span></td><td><span>Checking if RFD900 requires re-flashing</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+75</span></td><td><span>Starting servald, lbard and otaupdate</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+76</span></td><td><span>Finished S49servald</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+78</span></td><td><span>Entering S50dropbear</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+78</span></td><td><span>Locking root password</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+78</span></td><td><span>Enabling SSH login</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+80</span></td><td><span>Setting root password</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+83</span></td><td><span>Entering S94captiveportal</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+83</span></td><td><span>Starting dnsmasq</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+84</span></td><td><span>Started 5 dnsmasq processes</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+84</span></td><td><span>Exiting S94captiveportal</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+84</span></td><td><span>Entering S99mountcheck</span></td></tr>
<tr><td bgcolor="#00ff00"><span>OK</span></td><td><span>BOOT+85</span></td><td><span>Exiting S99mountcheck</span></td></tr>
</tbody></table>
<hr/>
<h2>
<span>System dmesg output</span></h2>
<pre><span>[    0.000000] Linux version 3.18.45 (serval@meshextender-imaging) (gcc version 4.8.3 (OpenWrt/Linaro GCC 4.8-2014.04 r49389) ) #15 Fri Apr 28 07:55:02 CST 2017
[    0.000000] MyLoader: sysp=d578547a, boardp=f5f9d079, parts=d5c8c478
[    0.000000] bootconsole [early0] enabled
[    0.000000] CPU0 revision is: 00019374 (MIPS 24Kc)
[    0.000000] SoC: Atheros AR9330 rev 1
[    0.000000] Determined physical RAM map:
[    0.000000]  memory: 04000000 @ 00000000 (usable)
[    0.000000] Initrd not found or empty - disabling initrd
[    0.000000] Zone ranges:
[    0.000000]   Normal   [mem 0x00000000-0x03ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00000000-0x03ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x03ffffff]
[    0.000000] On node 0 totalpages: 16384
[    0.000000] free_area_init_node: node 0, pgdat 8036a0f0, node_mem_map 81000000
[    0.000000]   Normal zone: 128 pages used for memmap
[    0.000000]   Normal zone: 0 pages reserved
[    0.000000]   Normal zone: 16384 pages, LIFO batch:3
[    0.000000] Primary instruction cache 64kB, VIPT, 4-way, linesize 32 bytes.
[    0.000000] Primary data cache 32kB, 4-way, VIPT, cache aliases, linesize 32 bytes
[    0.000000] pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 16256
[    0.000000] Kernel command line:  board=GL-AR150 mtdparts=spi0.0:256k(u-boot)ro,64k(u-boot-env)ro,16000k(firmware),64k(art)ro console=ttyATH0,115200 rootfstype=squashfs,jffs2 noinitrd
[    0.000000] PID hash table entries: 256 (order: -2, 1024 bytes)
[    0.000000] Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
[    0.000000] Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Writing ErrCtl register=00000000
[    0.000000] Readback ErrCtl register=00000000
[    0.000000] Memory: 60880K/65536K available (2533K kernel code, 149K rwdata, 540K rodata, 224K init, 188K bss, 4656K reserved)
[    0.000000] SLUB: HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:51
[    0.000000] Clocks: CPU:400.000MHz, DDR:400.000MHz, AHB:200.000MHz, Ref:25.000MHz
[    0.000000] Calibrating delay loop... 265.42 BogoMIPS (lpj=1327104)
[    0.080000] pid_max: default: 32768 minimum: 301
[    0.080000] Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.090000] Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
[    0.100000] NET: Registered protocol family 16
[    0.100000] MIPS: machine is GL AR150
[    0.590000] Switched to clocksource MIPS
[    0.590000] NET: Registered protocol family 2
[    0.600000] TCP established hash table entries: 1024 (order: 0, 4096 bytes)
[    0.600000] TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
[    0.600000] TCP: Hash tables configured (established 1024 bind 1024)
[    0.610000] TCP: reno registered
[    0.610000] UDP hash table entries: 256 (order: 0, 4096 bytes)
[    0.620000] UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
[    0.630000] NET: Registered protocol family 1
[    0.630000] PCI: CLS 0 bytes, default 32
[    0.630000] futex hash table entries: 256 (order: -1, 3072 bytes)
[    0.650000] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.650000] jffs2: version 2.2 (NAND) (SUMMARY) (LZMA) (RTIME) (CMODE_PRIORITY) (c) 2001-2006 Red Hat, Inc.
[    0.660000] msgmni has been set to 118
[    0.680000] io scheduler noop registered
[    0.680000] io scheduler deadline registered (default)
[    0.690000] Serial: 8250/16550 driver, 1 ports, IRQ sharing disabled
[    0.690000] ar933x-uart: ttyATH0 at MMIO 0x18020000 (irq = 11, base_baud = 1562500) is a AR933X UART
[    0.700000] console [ttyATH0] enabled
[    0.710000] bootconsole [early0] disabled
[    0.720000] m25p80 spi0.0: found w25q128, expected m25p80
[    0.720000] m25p80 spi0.0: w25q128 (16384 Kbytes)
[    0.730000] 4 cmdlinepart partitions found on MTD device spi0.0
[    0.730000] Creating 4 MTD partitions on "spi0.0":
[    0.740000] 0x000000000000-0x000000040000 : "u-boot"
[    0.740000] 0x000000040000-0x000000050000 : "u-boot-env"
[    0.750000] 0x000000050000-0x000000ff0000 : "firmware"
[    0.780000] 2 uimage-fw partitions found on MTD device firmware
[    0.780000] 0x000000050000-0x000000170000 : "kernel"
[    0.790000] 0x000000170000-0x000000ff0000 : "rootfs"
[    0.790000] mtd: device 4 (rootfs) set to be root filesystem
[    0.800000] 1 squashfs-split partitions found on MTD device rootfs
[    0.810000] 0x0000005a0000-0x000000ff0000 : "rootfs_data"
[    0.810000] 0x000000ff0000-0x000001000000 : "art"
[    0.830000] libphy: ag71xx_mdio: probed
[    1.430000] ag71xx ag71xx.0: connected to PHY at ag71xx-mdio.1:04 [uid=004dd041, driver=Generic PHY]
[    1.440000] eth0: Atheros AG71xx at 0xb9000000, irq 4, mode:MII
[    2.030000] ag71xx-mdio.1: Found an AR7240/AR9330 built-in switch
[    2.060000] eth1: Atheros AG71xx at 0xba000000, irq 5, mode:GMII
[    2.060000] TCP: cubic registered
[    2.070000] NET: Registered protocol family 17
[    2.070000] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[    2.080000] 8021q: 802.1Q VLAN Support v1.8
[    2.100000] VFS: Mounted root (squashfs filesystem) readonly on device 31:4.
[    2.100000] Freeing unused kernel memory: 224K (80388000 - 803c0000)
[    3.350000] init: Console is alive
[    3.350000] init: - watchdog -
[    3.360000] random: kmodloader urandom read with 5 bits of entropy available
[    5.490000] usbcore: registered new interface driver usbfs
[    5.500000] usbcore: registered new interface driver hub
[    5.500000] usbcore: registered new device driver usb
[    5.560000] SCSI subsystem initialized
[    5.570000] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.580000] ehci-platform: EHCI generic platform driver
[    5.580000] ehci-platform ehci-platform: EHCI Host Controller
[    5.590000] ehci-platform ehci-platform: new USB bus registered, assigned bus number 1
[    5.600000] ehci-platform ehci-platform: irq 3, io mem 0x1b000000
[    5.620000] ehci-platform ehci-platform: USB 2.0 started, EHCI 1.00
[    5.620000] hub 1-0:1.0: USB hub found
[    5.620000] hub 1-0:1.0: 1 port detected
[    5.640000] usbcore: registered new interface driver usb-storage
[    6.470000] init: - preinit -
[    9.720000] eth0: link up (100Mbps/Full duplex)
[   10.690000] jffs2: notice: (348) jffs2_build_xattr_subsystem: complete building xattr subsystem, 0 of xdatum (0 unchecked, 0 orphan) and 0 of xref (0 dead, 0 orphan) found.
[   10.700000] mount_root: switching to jffs2 overlay
[   10.750000] eth0: link down
[   10.770000] procd: - early -
[   10.770000] procd: - watchdog -
[   11.460000] procd: - ubus -
[   12.470000] procd: - init -
[   14.000000] NET: Registered protocol family 10
[   14.050000] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   14.080000] Loading modules backported from Linux version v4.4-rc5-1913-gc8fdf68
[   14.080000] Backport generated by backports.git backports-20151218-0-g2f58d9d
[   14.100000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.150000] mmc_spi spi0.1: SD/MMC host mmc0, no DMA, no WP, no poweroff
[   14.160000] nf_conntrack version 0.5.0 (954 buckets, 3816 max)
[   14.180000] mmc0: host does not support reading read-only switch, assuming write-enable
[   14.190000] mmc0: new SDHC card on SPI
[   14.200000] mmcblk0: mmc0:0000 SD16G 14.4 GiB 
[   14.210000]  mmcblk0: p1 p2 p3
[   14.250000] usbcore: registered new interface driver ums-alauda
[   14.280000] usbcore: registered new interface driver ums-cypress
[   14.290000] usbcore: registered new interface driver ums-datafab
[   14.290000] usbcore: registered new interface driver ums-freecom
[   14.300000] usbcore: registered new interface driver ums-isd200
[   14.320000] usbcore: registered new interface driver ums-jumpshot
[   14.330000] usbcore: registered new interface driver ums-karma
[   14.340000] usbcore: registered new interface driver ums-sddr09
[   14.350000] usbcore: registered new interface driver ums-sddr55
[   14.360000] usbcore: registered new interface driver ums-usbat
[   14.370000] usbcore: registered new interface driver usbserial
[   14.370000] usbcore: registered new interface driver usbserial_generic
[   14.380000] usbserial: USB Serial support registered for generic
[   14.420000] xt_time: kernel timezone is -0000
[   14.430000] usbcore: registered new interface driver ark3116
[   14.430000] usbserial: USB Serial support registered for ark3116
[   14.450000] usbcore: registered new interface driver belkin_sa
[   14.450000] usbserial: USB Serial support registered for Belkin / Peracom / GoHubs USB Serial Adapter
[   14.530000] usbcore: registered new interface driver ch341
[   14.530000] usbserial: USB Serial support registered for ch341-uart
[   14.540000] usbcore: registered new interface driver cp210x
[   14.550000] usbserial: USB Serial support registered for cp210x
[   14.550000] usbcore: registered new interface driver cypress_m8
[   14.560000] usbserial: USB Serial support registered for DeLorme Earthmate USB
[   14.570000] usbserial: USB Serial support registered for HID-&gt;COM RS232 Adapter
[   14.570000] usbserial: USB Serial support registered for Nokia CA-42 V2 Adapter
[   14.580000] usbcore: registered new interface driver ftdi_sio
[   14.590000] usbserial: USB Serial support registered for FTDI USB Serial Device
[   14.700000] PPP generic driver version 2.4.2
[   14.700000] NET: Registered protocol family 24
[   14.780000] ath: EEPROM regdomain: 0x0
[   14.780000] ath: EEPROM indicates default country code should be used
[   14.780000] ath: doing EEPROM country-&gt;regdmn map search
[   14.780000] ath: country maps to regdmn code: 0x3a
[   14.780000] ath: Country alpha2 being used: US
[   14.780000] ath: Regpair used: 0x3a
[   14.790000] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.790000] ieee80211 phy0: Atheros AR9330 Rev:1 mem=0xb8100000, irq=2
[   23.820000] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.880000] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.110000] eth0: link up (100Mbps/Full duplex)
[   26.110000] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.070000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.280000] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.380000] IPv6: ADDRCONF(NETDEV_UP): adhoc0: link is not ready
[   32.620000] adhoc0: Created IBSS using preconfigured BSSID 02:ca:ff:dd:ca:ce
[   32.620000] adhoc0: Creating new IBSS network, BSSID 02:ca:ff:dd:ca:ce
[   32.630000] IPv6: ADDRCONF(NETDEV_CHANGE): adhoc0: link becomes ready
[   36.180000] EXT4-fs (mmcblk0p2): couldn't mount as ext3 due to feature incompatibilities
[   36.190000] EXT4-fs (mmcblk0p2): couldn't mount as ext2 due to feature incompatibilities
[   36.240000] EXT4-fs (mmcblk0p2): mounted filesystem with ordered data mode. Opts: (null)
[   36.320000] EXT4-fs (mmcblk0p3): couldn't mount as ext3 due to feature incompatibilities
[   36.330000] EXT4-fs (mmcblk0p3): couldn't mount as ext2 due to feature incompatibilities
[   36.400000] EXT4-fs (mmcblk0p3): mounted filesystem with ordered data mode. Opts: (null)
[   37.540000] random: nonblocking pool is initialized
</span></pre>
<hr/>
<address>
</address>
<span>Last modified: Fri Apr 28 09:50:53 NZST 2017</span><br/>
<br/>
So now we can boot a Mesh Extender in under 90 seconds and know where it is up to in the meantime.<br/>
<br/>
In the process, I discovered that using ext2 instead of ext4 was a really bad idea, as on the slow microSD interface we have checking the filesystem can take 8 minutes, even when empty. <br/>
<br/>
Now to update the other seven, and get out into the nice New Zealand sunshine that has been taunting me all morning, and start testing!<br/>
<br/>

<a href="https://1.bp.blogspot.com/-npJUJk-tp9E/WQKGE4IvQyI/AAAAAAAAGK8/11qS5zhaXBAVqd5o7HdljFVwlL2ohPzMQCLcB/s1600/View-Outside-NZ-RC-ERU-Exercise-20170428.jpg"><img src="https://1.bp.blogspot.com/-npJUJk-tp9E/WQKGE4IvQyI/AAAAAAAAGK8/11qS5zhaXBAVqd5o7HdljFVwlL2ohPzMQCLcB/s400/View-Outside-NZ-RC-ERU-Exercise-20170428.jpg"/></a>
<div></div>
</div>