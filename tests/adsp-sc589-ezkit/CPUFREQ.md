# CPU Frequency Testing
-----------------------------------

Check current frequency (450 MHz)
```
root@adsp-sc589-ezkit:~# cpufreq-info

	cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
	Report errors and bugs to cpufreq@vger.kernel.org, please.
	analyzing CPU 0:
	  driver: sc5xx cpufreq
	  CPUs which run at the same hardware frequency: 0
	  CPUs which need to have their frequency coordinated by software: 0
	  maximum transition latency: 50.0 us.
	  hardware limits: 113 MHz - 450 MHz
	  available frequency steps: 450 MHz, 225 MHz, 113 MHz
	  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
	  current policy: frequency should be within 113 MHz and 450 MHz.
	                  The governor "performance" may decide which speed to use
	                  within this range.
	  current CPU frequency is 450 MHz (asserted by call to hardware).

```

Change frequency (225 MHz)
```
root@adsp-sc589-ezkit:~# cpufreq-set -f 225000
root@adsp-sc589-ezkit:~# cpufreq-info

	cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
	Report errors and bugs to cpufreq@vger.kernel.org, please.
	analyzing CPU 0:
	  driver: sc5xx cpufreq
	  CPUs which run at the same hardware frequency: 0
	  CPUs which need to have their frequency coordinated by software: 0
	  maximum transition latency: 50.0 us.
	  hardware limits: 113 MHz - 450 MHz
	  available frequency steps: 450 MHz, 225 MHz, 113 MHz
	  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
	  current policy: frequency should be within 113 MHz and 450 MHz.
	                  The governor "userspace" may decide which speed to use
	                  within this range.
	  current CPU frequency is 225 MHz (asserted by call to hardware).
```
