# Write Code to Remove the Rust Module

## Step 2: Run It

```bash
bash build_image.sh
insmod r4l_e1000_demo.ko
ip link set eth0 up
ip addr add broadcast 10.0.2.255 dev eth0
ip addr add 10.0.2.15/255.255.255.0 dev eth0 
ip route add default via 10.0.2.1
ping 10.0.2.2
rmmod r4l_e1000_demo
dmesg
```

```
~ # ls -l
total 68
drwxr-xr-x    2 1000     1000             0 Jul 21 16:32 bin
drwxr-xr-x    7 1000     1000             0 Jul 21 16:33 dev
drwxr-xr-x    3 1000     1000             0 Jul 14 15:24 etc
lrwxrwxrwx    1 0        0               11 Jul 21 16:32 linuxrc -> bin/busybox
dr-xr-xr-x  105 0        0                0 Jul 21 16:33 proc
-rw-r--r--    1 1000     1000         61312 Jul 21 16:32 r4l_e1000_demo.ko
drwx------    2 0        0                0 Jul 16 15:14 root
-rw-r--r--    1 0        0             4512 Jul 21 16:26 rust_helloworld.ko
drwxr-xr-x    2 1000     1000             0 Jul 21 16:32 sbin
dr-xr-xr-x   12 0        0                0 Jul 21 16:33 sys
drwxr-xr-x    4 1000     1000             0 Jul 14 15:24 usr
[   34.354895] ls (80) used greatest stack depth: 13920 bytes left
~ # insmod r4l_e1000_demo.ko
[   88.337656] r4l_e1000_demo: loading out-of-tree module taints kernel.
[   88.343972] r4l_e1000_demo: Rust for linux e1000 driver demo (init)
[   88.345117] r4l_e1000_demo: Rust for linux e1000 driver demo (probe): None
[   88.532900] ACPI: \_SB_.LNKC: Enabled at IRQ 11
[   88.560393] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[   88.565907] insmod (81) used greatest stack depth: 11192 bytes left
~ # ip link set eth0 up
[   91.535636] r4l_e1000_demo: Rust for linux e1000 driver demo (net device open)
[   91.539294] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[   91.541637] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
~ # [   91.547710] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[   91.558565] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=0, tdh=0, rdt=7, rdh=0
[   91.559433] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   91.559874] r4l_e1000_demo: pending_irqs: 3
[   91.561129] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[   91.570801] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=1, tdh=1, rdt=7, rdh=0
[   91.571414] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   91.571785] r4l_e1000_demo: pending_irqs: 3
[   91.572150] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[   92.561830] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=2, tdh=2, rdt=7, rdh=0
[   92.562518] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   92.562709] r4l_e1000_demo: pending_irqs: 3
[   92.562870] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[   93.610580] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=3, tdh=3, rdt=7, rdh=0
[   93.611307] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   93.611541] r4l_e1000_demo: pending_irqs: 3
[   93.611711] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[   93.612689] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=4, tdh=4, rdt=7, rdh=0
[   93.613376] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   93.613687] r4l_e1000_demo: pending_irqs: 3
[   93.613835] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[   93.937767] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=5, tdh=5, rdt=7, rdh=0
[   93.938414] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   93.938579] r4l_e1000_demo: pending_irqs: 3
[   93.939418] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)

~ # [   97.509433] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=6, tdh=6, rdt=7, 0
[   97.509857] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[   97.510161] r4l_e1000_demo: pending_irqs: 3
[   97.510678] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
ip addr add broadcast 10.0.2.255 dev eth0
[   98.971884] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[   98.973756] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
ip: RTNETLINK answers: Invalid argument
~ # ip addr add 10.0.2.15/255.255.255.0 dev eth0 
[  103.895703] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[  103.895994] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
~ # [  105.425140] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=7, tdh=7, rdt=7, 0
[  105.425740] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[  105.426329] r4l_e1000_demo: pending_irqs: 3
[  105.426546] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)

~ # ip route add default via 10.0.2.1
~ # ping 10.0.2.2
PING 10.0.2.2 (10.0.2.2): 56 data bytes
[  110.387102] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=0, tdh=0, rdt=7, rdh=0
[  110.387819] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[  110.387939] r4l_e1000_demo: pending_irqs: 131
[  110.388580] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
[  110.390566] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=1, tdh=1, rdt=0, rdh=1
[  110.390990] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[  110.391182] r4l_e1000_demo: pending_irqs: 131
[  110.392074] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
64 bytes from 10.0.2.2: seq=0 ttl=255 time=15.405 ms
[  111.400118] r4l_e1000_demo: Rust for linux e1000 driver demo (net device start_xmit) tdt=2, tdh=2, rdt=1, rdh=2
[  111.401488] r4l_e1000_demo: Rust for linux e1000 driver demo (handle_irq)
[  111.401934] r4l_e1000_demo: pending_irqs: 131
[  111.402313] r4l_e1000_demo: Rust for linux e1000 driver demo (napi poll)
64 bytes from 10.0.2.2: seq=1 ttl=255 time=4.222 ms
^C
--- 10.0.2.2 ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max = 4.222/9.813/15.405 ms
~ # rmmod r4l_e1000_demo
[  118.096418] r4l_e1000_demo: Rust for linux e1000 driver demo (exit)
[  118.098116] r4l_e1000_demo: Rust for linux e1000 driver demo (remove)
[  118.098362] r4l_e1000_demo: Rust for linux e1000 driver demo (device_remove)
[  118.100384] r4l_e1000_demo: Rust for linux e1000 driver demo (net device stop)
[  118.101282] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
[  118.111780] r4l_e1000_demo: Rust for linux e1000 driver demo (net device get_stats64)
~ # insmod r4l_e1000_demo.ko
[  124.658889] r4l_e1000_demo: Rust for linux e1000 driver demo (init)
[  124.659524] r4l_e1000_demo: Rust for linux e1000 driver demo (probe): None
[  124.660201] r4l_e1000_demo 0000:00:03.0: BAR 0: can't reserve [mem 0xfeb80000-0xfeb9ffff]
[  124.660804] r4l_e1000_demo: probe of 0000:00:03.0 failed with error -16
~ # lsmod | grep r4l
r4l_e1000_demo 40960 0 - Live 0xffffffffc03a9000 (O)
~ # 
```