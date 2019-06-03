# Generic GPIO Testing
-----------------------------------

Run the following and watch GPIO77 toggle on/off on the board
```
LED=77
echo ${LED} > /sys/class/gpio/export
echo out > /sys/class/gpio/gpio${LED}/direction

while [ true ]; do
    echo 1 > /sys/class/gpio/gpio${LED}/value
    usleep 250000
    echo 0 > /sys/class/gpio/gpio${LED}/value
    usleep 250000
done
```

Run the following and ensure the "Button pressed" message is display when pressing the push button (GPIO80) on the board:
```
BTN=80
echo ${BTN} > /sys/class/gpio/export
echo in > /sys/class/gpio/gpio${BTN}/direction

while [ true ]; do
    VAL=$(cat /sys/class/gpio/gpio${BTN}/value)
    if [ ${VAL} -eq "1" ]; then
        echo "Button pressed"
    fi
done
```

