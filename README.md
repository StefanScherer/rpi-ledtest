# ledtest

## Preparation

Flash Raspbian

Enable SSH

    touch /Volumes/boot/ssh

Enable WiFi

    vi /Volumes/boot/wpa_suplicant.conf

Insert this

    country=DE # Your 2-digit country code
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    network={
        ssid="InsertYourSSID"
        psk="InsertYourPSK"
        key_mgmt=WPA-PSK
    }

Boot Raspbian for the first time. SSH into it with user `pi`and adjust hostname in network settings

    sudo raspi-config

Prepare your Raspbian 

https://tutorials-raspberrypi.de/raspberry-pi-ws2812-ws2811b-rgb-led-streifen-steuern/

Blacklist `snd_bcm2835`

    sudo vi /etc/modprobe.d/snd-blacklist.conf

Add this 

    blacklist snd_bcm2835

Adjust config.txt

    sudo vi /boot/config.txt

Comment out `dtparam=audio=on`

    #dtparam=audio=on

Reboot

    sudo reboot

## Installation

Install pipenv package manager

    pip install --user pipenv

Allow GPIO access from Python scripts without sudo

    sudo chown root $(pipenv run which python)
    sudo chmod 4755 $(pipenv run which python)

## Run the program

    pipenv run python strandtest.py -c


## Visual Studio Code

https://www.hanselman.com/blog/VisualStudioCodeRemoteDevelopmentOverSSHToARaspberryPiIsButter.aspx
