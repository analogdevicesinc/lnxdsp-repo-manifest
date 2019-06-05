# PCIE EP
-----------------------------------

Failed, kernel log shows:

```
root@adsp-sc589-ezkit:~# dmesg | grep pcie
sc58x-pcie 310b8000.pcie: Link training failed
sc58x-pcie 310b8000.pcie: PORT_LINK_DEBUG0 = 94d100, PORT_LINK_DEBUG1 = 8200000
sc58x-pcie: probe of 310b8000.pcie failed with error -110
root@adsp-sc589-ezkit:~# lspci
```
