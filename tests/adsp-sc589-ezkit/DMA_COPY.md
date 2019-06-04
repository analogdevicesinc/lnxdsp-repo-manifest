# Generic GPIO Testing
-----------------------------------

#### This throws copy offset errors for every test at the moment:

Must set following in conf/local.conf
```
ANALOG_DEVICES_SRAM_ALLOC="1"
```

Run the test module:
```
modprobe dmacopy_module
```

