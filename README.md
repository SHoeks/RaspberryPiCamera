# RaspberryPiCamera

## Battery saving options

Turn OFF USB chip
```bash
echo '1-1' |sudo tee /sys/bus/usb/drivers/usb/unbind
```

Turn ON USB chip
```bash
echo '1-1' |sudo tee /sys/bus/usb/drivers/usb/bind
```

Turn OFF HDMI output
```bash
sudo /opt/vc/bin/tvservice -o
```

Turn ON HDMI output

```bash
sudo /opt/vc/bin/tvservice -p
Total = 4hrs 11mins
```
