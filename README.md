# ADBS_Feedr

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
