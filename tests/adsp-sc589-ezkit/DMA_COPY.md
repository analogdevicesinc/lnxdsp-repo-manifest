# Generic GPIO Testing
-----------------------------------

#### This throws copy offset errors for every test at the moment:

Make sure to uncomment the following in linux-adi_4.16.bb
```
#If running DMA tests, then include the following patch as well (this disables CONFIG_ICC and enables CONFIG_ARCH_SRAM_ALLOC):
#SRC_URI += " \
#	file://Remove-CONFIG_ICC-and-use-CONFIG_ARCH_SRAM_ALLOC-for.patch \
#"
```

Run the test module:
```
modprobe dmacopy_module
```

