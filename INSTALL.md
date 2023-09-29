### Update system

```bash
sudo apt update && sudo apt upgrade -y
```

### Enable i2s and disable aux

```bash
sudo nano /boot/config.txt
```

Change `dtparam=audio=on` to `#dtparam=audio=on`.
Add `dtoverlay=hifiberry-dac` to the bottom.

### Install docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo systemctl start docker
rm get-docker.sh
```

### Setup ZOUDIO_daemon

Move `ZOUDIO_daemon.py` to `/home/pi` first.

```bash
sudo apt install python3-pip -y
sudo pip3 install pyserial
mkdir /home/pi/zoudio-commands

sudo nano /etc/rc.local
```

Add `sudo python3 /home/pi/zoudio-commands/ZOUDIO_daemon.py &`  to rc.local before `exit 0`.
Copy `ZOUDIO_daemon.py` to `zoudio-commands`

### Install and run shairport-sync

Move `shairport-sync.conf` to `/home/pi` first.

```bash
sudo docker run -d --restart unless-stopped --net host --device /dev/snd \
    --name shairport-sync -v /home/pi/zoudio-commands:/home/shairport-sync/zoudio-commands:Z \
    mikebrady/shairport-sync:latest
sudo docker cp shairport-sync.conf shairport-sync:/etc/shairport-sync.conf
sudo docker restart shairport-sync
```

### Reboot and enjoy

```bash
sudo reboot
```
