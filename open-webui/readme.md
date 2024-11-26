# Open WebUI

## Install Open WebUI
Install [poetry](https://github.com/EDUnter/development-enviroment/blob/main/poetry/readme.md)

Create poetry env
```
mdkir open-webui
cd open-webui
poetry init -n
```

Change python version to 3.11.10
```
nvim pyproject.toml
```
```
[tool.poetry.dependencies]
python = "3.11.10"
```

Make sure global python from [pyenv](https://github.com/EDUnter/development-enviroment/blob/main/python/readme.md) is from 3.11.10 version before running the command down below
```
poetry env use python
```

Install open-webui
```
poetry add open-webui
```

## Run Open WebUI
Open Webui will be accessible through http://localhost:8080
```
poetry run open-webui serve
```

## Create a service for Open WebUI
Create the service
```
sudo nvim /etc/systemd/system/open-webui.service
```
```
[Unit]
Description=Open-WebUI Service
After=network.target

[Service]
Type=simple
User=edunter
WorkingDirectory=/home/edunter/Development/open-webui-app/
ExecStart=/home/edunter/.local/bin/poetry run open-webui serve
ExecStop=/bin/kill $MAINPID
Restart=always
Environment="PATH=/home/edunter/.local/bin:/usr/bin:/bin"

[Install]
WantedBy=multi-user.target
```

Reload daemon, start and enble the service to initialize Open WebUI at boot time 
```
sudo systemctl daemon-reload
sudo systemctl start open-webui.service
sudo systemctl enable open-webui.service
```
