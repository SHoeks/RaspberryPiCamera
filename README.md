# RaspberryPiCamera

## Battery saving options

These are options to help save battery life on the Raspberry Pi Zero with PiJuice

Turn OFF HDMI output
```bash
sudo /opt/vc/bin/tvservice -o
```

Turn ON HDMI output

```bash
sudo /opt/vc/bin/tvservice -p
```

Turn off Bluetooth: add following line to /boot/config.txt

```bash
dtoverlay=pi3-disable-bt
```

Turn off leds: add following lines to /boot/config.txt

```bash
dtparam=act_led_trigger=none
dtparam=act_led_activelow=on
```


## Python script for taking pictures

Script is used to take picture on button press using pin 18 and ground: http://razzpisampler.oreilly.com/ch07.html

```python
import RPi.GPIO as GPIO
import time
from picamera import PiCamera 

GPIO.setmode(GPIO.BCM)
GPIO.setup(18, GPIO.IN, pull_up_down=GPIO.PUD_UP)

img_path="/home/pi/Pictures/test/img__"
img_ext=".jpg"

camera = PiCamera()
time.sleep(2)
camera.resolution = (2592, 1944)
camera.image_effect = 'none'

while True:
	input_state = GPIO.input(18)
	if input_state == False:
		img_time = time.strftime("%Y_%m_%d_%H__%M_%S")
		print('taking picture')
		camera.capture(img_path + img_time + img_ext)
		time.sleep(0.2)
```
saved in /home/pi/Documents/TakePicturePiCam.py.

## Start python script at boot 

```bash
sudo crontab -e
```

Add the following line:

```bash
@reboot sudo python /home/pi/Documents/TakePicturePiCam.py
```

