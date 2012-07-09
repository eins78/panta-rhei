#!/bin/ash

# ONLINE STATUS 2 LED SCRIPT #
### inspired by http://wiki.openwrt.org/oldwiki/mod.led.sysloadled?s%5B%5D=led

# CONFIG

## location of the LED in OpenWRT file system, depends on router model
LED_PATH="/sys/devices/platform/leds-gpio/leds/tp-link:blue:system"       
LED_INIT=0   ## LED is off by default
LED_OFF=0    ## which value turns LED on
LED_ON=255   ## look it up in $LED_PATH/max_brightness (we want the script to do less)
SLEEP=3      ## how many seconds to wait between checks
WAIT=3       ## how long to wait for the PING

# HELPER VARS -- don't edit if you don't have to
LED=""$LED_PATH"/brightness"
PING_TARGET="8.8.8.8"  ## Google's DNS -- if it's down the net boring anyhow
OUTPUT="> /dev/null"

# DEBUG section
#echo "LED is $LED."
#echo "Current brightness is $(cat $LED)"
#OUTPUT=" " #uncommment this to enable output to shell

##### MAIN PROGRAMM #####

# LED is off by default
#echo $LED_INIT > $LED

# LOOP IT FOREVER
while true ; do
    ping -q -c1 -W $WAIT $PING_TARGET > /dev/null && echo $LED_ON > $LED || echo $LED_OFF > $LED
    sleep $SLEEP;
done

exit 0