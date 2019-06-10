# Touch Testing
-----------------------------------

GPIO 102 from touchscreen_test.exp does not appear to be a valid GPIO for this board.

What GPIO is this supposed to be?

Also do not have touch hardware to test with.


```
root@adsp-sc589-ezkit:~# cat /sys/kernel/debug/gpio 
gpiochip0: GPIOs 0-15, adi-gpio:
 gpio-14  (                    |adau1977            ) out hi    

gpiochip1: GPIOs 16-31, adi-gpio:
 gpio-30  (                    |mdio-reset          ) out hi    

gpiochip2: GPIOs 32-47, adi-gpio:
 gpio-32  (                    |spi0.32             ) out hi    
 gpio-38  (                    |spi2.38             ) out hi    
 gpio-44  (                    |spi0.44             ) out hi    

gpiochip3: GPIOs 48-63, adi-gpio:

gpiochip4: GPIOs 64-79, adi-gpio:

gpiochip5: GPIOs 80-95, adi-gpio:

gpiochip6: GPIOs 96-101, adi-gpio:

gpiochip8: GPIOs 480-495, parent: i2c/0-0022, mcp23017, can sleep:

gpiochip7: GPIOs 496-511, parent: i2c/0-0021, mcp23017, can sleep:
 gpio-504 P0.8 (adau1962-rst) out lo 
```
