# RaspberryPiCamera

## Battery saving options

Turn OFF USB chip
```
echo '1-1' |sudo tee /sys/bus/usb/drivers/usb/unbind
```

Turn ON USB chip
```
echo '1-1' |sudo tee /sys/bus/usb/drivers/usb/bind
```

