# Clock Control
-----------------------------------

Followed reprogram_clock/reprogram_clock_test.exp:

Build with CCLK_DIV_1=y
```
root@adsp-sc589-ezkit# dmesg | grep CGU0
CGU0_PLL 450 MHz
CGU0_SYSCLK 225 MHz
CGU0_CCLK 450 MHz
CGU0_SYS0 112 MHz
CGU0_DCLK 450 MHz
CGU0_OCLK 150 MHz
CGU0_SYS0 112 MHz
```


Build with CCLK_DIV_2=y, and notice that CGU0_CCLK drops to 225MHz
```
root@adsp-sc589-ezkit:~# dmesg | grep CGU0
CGU0_PLL 450 MHz
CGU0_SYSCLK 225 MHz
CGU0_CCLK 225 MHz
CGU0_SYS0 112 MHz
CGU0_DCLK 450 MHz
CGU0_OCLK 150 MHz
CGU0_SYS0 112 MHz
```
