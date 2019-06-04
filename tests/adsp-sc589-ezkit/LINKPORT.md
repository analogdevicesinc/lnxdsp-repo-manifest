# Link Port
-----------------------------------


On ADSP-SC589 EZKit, I had to set these to get the /dev/linkport0 and /dev/linkport1 devices to show up:

```
&spi0 {
	...
	status = "disabled";
	...
};
```

```
&emac0 {
	/* Conflicts with lp1grp PB14 */
	/* snps,reset-gpio = <&gpb 14 0>; */
	/* snps,reset-active-low; */
	/* snps,reset-delays-us = <0 200 500>; */
	phy-handle = <&dp83867>;
	phy-mode = "rgmii";
	pinctrl-names = "default";
	pinctrl-0 = <&eth0_default>;
	status = "okay";
	mdio0 {
		compatible = "snps,dwmac-mdio";
		#address-cells = <1>;
		#size-cells = <0>;
		dp83867: ethernet-phy@0 {
			reg = <0>;
			ti,rx-internal-delay = <DP83867_RGMIIDCTL_2_00_NS>;
			ti,tx-internal-delay = <DP83867_RGMIIDCTL_2_00_NS>;
			ti,fifo-depth = <DP83867_PHYCR_FIFO_DEPTH_8_B_NIB>;
			ti,dp83867-rxctrl-strap-quirk;
		};
	};
};
```

I then did:
```
root@adsp-sc589-ezkit:~# modprobe adi_lp
Find dt node linkport0
of parse lp_div: 1
of parse data irq: 48, status irq: 49
Find dt node linkport1
of parse lp_div: 1
of parse data irq: 50, status irq: 51
```

```
root@adsp-sc589-ezkit:~# linkport_test 
linkport test failed 0 - 1
```