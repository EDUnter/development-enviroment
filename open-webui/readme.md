# Open WebUI

## Install Open WebUI
Install [poetry](https://github.com/EDUnter/development-enviroment/blob/main/poetry/readme.md)

Create poetry env
```
mkdir open-web-ui
cd open-web-ui
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

## Run Open WebUI as a desktop app
Install nodejs and electron
```
sudo dnf install nodejs npm
sudo npm install -g electron
```

Create the desktop app
```
mkdir electron-open-webui
cd electron-open-webui
npm init -y
npm install electron --save-dev
nvim index.js
```
```
const { app, BrowserWindow } = require('electron');

let mainWindow;

app.on('ready', () => {
    mainWindow = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
            contextIsolation: true,
            enableRemoteModule: false,
            nodeIntegration: false,
        },
    });

    // Load your web app
    mainWindow.loadURL('http://localhost:8080'); // Replace with your desired URL

    // Remove the menu bar
    mainWindow.setMenuBarVisibility(false);

    // Optional: Uncomment to open dev tools during development
    // mainWindow.webContents.openDevTools();
});

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit();
    }
});
```

Test the app
```
npx electron .
```

Package the app
```
sudo npm install -g electron-packager
electron-packager . open-webui --platform=linux --arch=x64 --overwrite
cp -r open-webui ~/.local/share/
```

Create desktop icon
```
nvim ~/.local/share/applications/OpenWebUI.desktop
```
```
[Desktop Entry]
Name=Open WebUI
Exec=/home/edunter/.local/share/open-webui/open-webui
Icon=/home/edunter/.local/share/open-webui/open-webui-icon.png
StartupWMClass=electron-open-webui
Type=Application
Categories=Utility;
```

Download [desktop shortcut icon](https://github.com/EDUnter/development-enviroment/blob/main/open-webui/open-webui-icon.png)
```
cp ~/Downloads/open-webui-icon.png /home/edunter/.local/share/open-webui/open-webui-icon.png
```

Notes:  
If the window appears open in a new icon on dock use xprop and click in the open webui app to check the WM_CLASS.  
If its WM_CLASS differs from the desktop parameter `StartupWMClass`, change it accordingly.
```
xprop | grep WM_CLASS
```

## Keybindings
```
Name -> open-webui
Command -> /home/edunter/.local/share/open-webui/open-webui
Shortcut -> Super+u
```
