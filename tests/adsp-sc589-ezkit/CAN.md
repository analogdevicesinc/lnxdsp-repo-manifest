
# CAN
-----------------------------------

Failed.  Can't start phy


Try to probe module:
```
root@adsp-sc589-ezkit:# modprobe sc5xx_can
sc5xx_can 31000200.can: sc5xx_can device registered(&reg_base=c78ef40a, rx_irq=23, tx_irq=24, err_irq=25, sclk=112500000)
sc5xx_can 31000a00.can: sc5xx_can device registered(&reg_base=b4f00185, rx_irq=26, tx_irq=27, err_irq=28, sclk=112500000)
adi-spi3 31042000.spi: chipselect 44 already in use
sc5xx_can 31000a00.can: Can't start can phy
Trying to free nonexistent resource <0000000031000a00-0000000031000ffe>
sc5xx_can: probe of 31000a00.can failed with error -22
```

Turning spi0 off in DTS:
```
&spi0 {
	pinctrl-names = "default";
	pinctrl-0 = <&spi0_default>;
	status = "disabled";
```

Now results in:
```
root@adsp-sc589-ezkit:~# modprobe sc5xx_can
sc5xx_can 31000200.can: sc5xx_can device registered(&reg_base=c78ef40a, rx_irq=23, tx_irq=24, err_irq=25, sclk=112500000)
sc5xx_can 31000a00.can: sc5xx_can device registered(&reg_base=b4f00185, rx_irq=26, tx_irq=27, err_irq=28, sclk=112500000)
sc5xx_can 31000a00.can: Can't start can phy
Trying to free nonexistent resource <0000000031000a00-0000000031000ffe>
```
