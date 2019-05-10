# OProfile Testing
-----------------------------------

```
root@adsp-sc589-ezkit:~# echo -1 > /proc/sys/kernel/perf_event_paranoid
root@adsp-sc589-ezkit:~# echo 0 > /proc/sys/kernel/kptr_restrict
root@adsp-sc589-ezkit:~# modprobe oprofile
root@adsp-sc589-ezkit:~# operf --vmlinux=/boot/vmlinux-4.16.0 whetstone 10000
root@adsp-sc589-ezkit:~# opreport -l

Using /home/root/oprofile_data/samples/ for samples directory.

WARNING! Some of the events were throttled. Throttling occurs when
the initial sample rate is too high, causing an excessive number of
interrupts.  Decrease the sampling frequency. Check the directory
/home/root/oprofile_data/samples/current/stats/throttled
for the throttled event names.

CPU: ARM Cortex-A5, speed 445 MHz (estimated)
Counted CPU_CYCLES events (CPU cycle) with a unit mask of 0x00 (No unit mask) count 100000
samples  %        image name               symbol name
11064    81.0549  whetstone                /usr/bin/whetstone
2474     18.1245  libm-2.28.so             /lib/libm-2.28.so
10        0.0733  vmlinux-4.16.0           __do_softirq
7         0.0513  vmlinux-4.16.0           queue_work_on
5         0.0366  ld-2.28.so               /lib/ld-2.28.so
4         0.0293  vmlinux-4.16.0           stmmac_tx_clean
3         0.0220  vmlinux-4.16.0           ip_rcv_finish
3         0.0220  vmlinux-4.16.0           stmmac_poll
3         0.0220  vmlinux-4.16.0           tcp_ack
2         0.0147  vmlinux-4.16.0           __do_div64
2         0.0147  vmlinux-4.16.0           __sync_icache_dcache
2         0.0147  vmlinux-4.16.0           cpu_v7_set_pte_ext
2         0.0147  vmlinux-4.16.0           dql_completed
2         0.0147  vmlinux-4.16.0           inet_gro_receive
2         0.0147  vmlinux-4.16.0           ip_local_deliver_finish
2         0.0147  vmlinux-4.16.0           ip_rcv
2         0.0147  vmlinux-4.16.0           net_rx_action
2         0.0147  vmlinux-4.16.0           stmmac_xmit
2         0.0147  vmlinux-4.16.0           tcp_ack_update_rtt
2         0.0147  vmlinux-4.16.0           tcp_rcv_established
2         0.0147  vmlinux-4.16.0           tcp_v4_rcv
1         0.0073  libc-2.28.so             /lib/libc-2.28.so
1         0.0073  vmlinux-4.16.0           __bpf_prog_run32
1         0.0073  vmlinux-4.16.0           __local_bh_enable_ip
1         0.0073  vmlinux-4.16.0           __netdev_alloc_skb
1         0.0073  vmlinux-4.16.0           __netif_receive_skb_core
1         0.0073  vmlinux-4.16.0           __netif_schedule
1         0.0073  vmlinux-4.16.0           __tcp_ack_snd_check
1         0.0073  vmlinux-4.16.0           __und_usr
1         0.0073  vmlinux-4.16.0           alloc_set_pte
1         0.0073  vmlinux-4.16.0           complete_walk
1         0.0073  vmlinux-4.16.0           copy_page
1         0.0073  vmlinux-4.16.0           dev_gro_receive
1         0.0073  vmlinux-4.16.0           do_exit
1         0.0073  vmlinux-4.16.0           do_page_fault
1         0.0073  vmlinux-4.16.0           dput.part.7
1         0.0073  vmlinux-4.16.0           dwmac_enable_dma_transmission
1         0.0073  vmlinux-4.16.0           enh_desc_get_rx_status
1         0.0073  vmlinux-4.16.0           fget
1         0.0073  vmlinux-4.16.0           filemap_map_pages
1         0.0073  vmlinux-4.16.0           finish_task_switch
1         0.0073  vmlinux-4.16.0           get_page_from_freelist
1         0.0073  vmlinux-4.16.0           gptmr_read_sched
1         0.0073  vmlinux-4.16.0           ip_local_deliver
1         0.0073  vmlinux-4.16.0           memcpy
1         0.0073  vmlinux-4.16.0           mod_timer
1         0.0073  vmlinux-4.16.0           napi_complete_done
1         0.0073  vmlinux-4.16.0           napi_gro_complete
1         0.0073  vmlinux-4.16.0           napi_gro_receive
1         0.0073  vmlinux-4.16.0           nfs_lookup_revalidate
1         0.0073  vmlinux-4.16.0           nfs_permission
1         0.0073  vmlinux-4.16.0           page_remove_rmap
1         0.0073  vmlinux-4.16.0           perf_event_mmap
1         0.0073  vmlinux-4.16.0           raw_local_deliver
1         0.0073  vmlinux-4.16.0           release_pages
1         0.0073  vmlinux-4.16.0           rpcauth_lookup_credcache
1         0.0073  vmlinux-4.16.0           sched_clock
1         0.0073  vmlinux-4.16.0           schedule
1         0.0073  vmlinux-4.16.0           skb_free_head
1         0.0073  vmlinux-4.16.0           skb_gro_reset_offset
1         0.0073  vmlinux-4.16.0           skb_release_all
1         0.0073  vmlinux-4.16.0           skb_release_data
1         0.0073  vmlinux-4.16.0           sock_def_readable
1         0.0073  vmlinux-4.16.0           strnlen_user
1         0.0073  vmlinux-4.16.0           tcp_data_queue
1         0.0073  vmlinux-4.16.0           tcp_delack_timer
1         0.0073  vmlinux-4.16.0           tcp_schedule_loss_probe
1         0.0073  vmlinux-4.16.0           tcp_urg
1         0.0073  vmlinux-4.16.0           tcp_v4_early_demux
1         0.0073  vmlinux-4.16.0           tcp_write_xmit
1         0.0073  vmlinux-4.16.0           unmap_page_range
1         0.0073  vmlinux-4.16.0           v7_dma_inv_range
1         0.0073  vmlinux-4.16.0           xprt_release
1         0.0073  vmlinux-4.16.0           xs_data_ready
```