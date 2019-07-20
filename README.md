# PiOLED
PiOLED service for Raspberry Pi

The `stats.py` code is taken from https://learn.adafruit.com/pi-hole-ad-blocker-with-pi-zero-w/ and made a service. I made these changes to the original script:
  - change `time.sleep(.1)` interval for display refresh to `time.sleep(1)` as this is enough
  - to catch `requests.exceptions.ConnectionError` on `requests.get()` 
    - this is necessary because the `containerd` is marked as started successfully when the Pi hole is not fully running and the script would get that exception


## Install

- needs pip3:
```
    sudo apt-get install -y python3-pip
```
- enable I2C bus via `raspi-config`
- clone the repository to `/srv/`:
```
    git clone https://github.com/vladak/PiOLED.git /srv/PiOLED
```
- copy `PiOLED.service` file to `/etc/systemd/system/PiOLED.service`:
- enable the service:
```
sudo systemctl enable PiOLED
```
- if the file `/etc/systemd/system/PiOLED.service` changes, run:
```
sudo systemctl daemon-reload
```
- to start the service:
```
sudo systemctl start PiOLED
sudo systemctl status PiOLED
```
