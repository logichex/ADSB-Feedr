# ADSB Feedr

A small project to revive old hardware, handfull of components and a glimpse-compatible LCD display, very 80s-90s look for a fancy ADSB feeder.

Below is a list of dust collecting hardware I used to bring this ADSB feeder to operation.

- Old TV Box, what i had is WeChip V8 box. It's clone of any machine out there, has an Amlogic S905W 2GB Ram 16GB Emmc, running on Android 7 out of box. What i liked about this device was that UART port was available for my purposes, relatively powerful processing capability and passive cooling. Ideal mini-power device.

- Since my TV box came with almost non-supported wireless chip, a USB wifi adapter was used.
  
- An RTL-SDR receiver, something like 10+ years of age but still strong.Based on RTL2832u.

- Optional Arduino Nano and LCD display. Arduino is primarily used as display I have two options built, one is the fancier 16x2 i2c blue LCD and other is classical 4 digit 7 segment display, which i had one in junk box from an old satellite receiver.

- Other radio stuff, Low Noise Amp, 1090mhz filter, cabling etc.

- While there feeder works without Arduino, i wanted to use this tvbox with other capabilities out of ADSB stuff, like energy monitoring and some other automations not related to ADSB feeds.


Make python script executable 
sudo chmod +x /usr/local/bin/adsb_lcd_sender.py

Make python script service
sudo nano /etc/systemd/system/adsb-lcd.service

Add below to file created above:

[Unit]
Description=ADS-B LCD Sender
After=network.target

[Service]
ExecStart=/usr/local/bin/adsb_lcd_sender.py
Restart=always
User=pi

[Install]
WantedBy=multi-user.target

Save the file, enable and start service

sudo systemctl enable adsb-lcd
sudo systemctl start adsb-lcd
