# MQTT_RaspberryPi_SERIVCE
Instructions to create a Raspberry pi service that listens to MQTT messages written in python

FOLLOW THE STEPS TO CREATE A SERVICE IN Raspberry pi NOOBS OS

1. Create your python script that does something.
2. Run the following command:

```chmod +x path/to/your/python/script.py```

3. Create a Systemd Unit File:
``` sudo nano /etc/systemd/system/my_service.service```

4. Add the following content:
```
[Unit]
Description=My Custom Service
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/python3 /path/to/your/script.py
WorkingDirectory=/path/to/your/script/directory
Restart=always

[Install]
WantedBy=multi-user.target
```

5. Run the command to inform systemd about the new Unit file
``` sudo systemctl daemon-reload```

6. Enable the service
``` sudo systemctl enable my_service.service```

7. Start the service for current session:
``` sudo systemctl start my_service.service ```

8. Check the status of the service
``` sudo systemctl status my_service.service ```

9. If there are issues, run this command to check the logs:
``` sudo journalctl -u my_service.service -xe ```



Following these steps would give you a great starting point to creating  your own service that runs everytime your raspberry pi is started
