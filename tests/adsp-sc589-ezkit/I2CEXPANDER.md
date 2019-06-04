# I2C Expander Soft Switch
-----------------------------------

Make sure push button 1 is working:
```
BTN=80 #PUSHBUTTON1
echo ${BTN} > /sys/class/gpio/export
echo in > /sys/class/gpio/gpio${BTN}/direction

while [ true ]; do
    VAL=$(cat /sys/class/gpio/gpio${BTN}/value)
    if [ ${VAL} -eq "1" ]; then
        echo "Button pressed"
    fi
done

...

Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
Button pressed
```

Disable push button 1 enable through I2C expander:
```
GPIO=480 #PUSHBUTTON1_EN
echo ${GPIO} > /sys/class/gpio/export
echo out > /sys/class/gpio/gpio${GPIO}/direction
echo 1 > /sys/class/gpio/gpio${GPIO}/value
```

Make sure you no longer receive the "Button pressed" outputs when pressing the button:
```
BTN=80 #PUSHBUTTON1
echo ${BTN} > /sys/class/gpio/export
echo in > /sys/class/gpio/gpio${BTN}/direction

while [ true ]; do
    VAL=$(cat /sys/class/gpio/gpio${BTN}/value)
    if [ ${VAL} -eq "1" ]; then
        echo "Button pressed"
    fi
done
```