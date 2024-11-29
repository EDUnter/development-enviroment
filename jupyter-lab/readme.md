# Jupyter Lab

## Install Jupyter Lab
```
pip install jupyterlab
```

Install nodejs to install extensions
```
sudo dnf install -y nodejs
```

Install Nbdime
```
poetry add nbdime
```

Enable nbdime extensions
```
nbdime extensions --enable # [--sys-prefix/--user/--system]
nbdime config-git --enable  --global
```

Install dracula theme
```
pip install JLDracula
```

## Run Jupyter Lab
```
jupyter-lab
```

# Run Jupyter Lab as a desktop app
Install nodejs and electron
```
sudo dnf install nodejs npm
sudo npm install -g electron
```

Create the desktop app
```
mkdir electron-jupyter-lab
cd electron-jupyter-lab
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
    mainWindow.loadURL('http://localhost:8888/lab/workspaces/auto-y/tree/Development?token=8be27dbc78333497cf390033177bca290b916d89c83e2b4c'); // Replace with your desired URL

    // Remove the menu bar
    mainWindow.setMenuBarVisibility(false);

    // Optional: Uncomment to open dev tools during development
    // mainWindow.webContents.openDevTools();
});

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit();
    }
})
```

Test the app
```
npx electron .
```

Package the app
```
sudo npm install -g electron-packager
electron-packager . jupyter-lab --platform=linux --arch=x64 --overwrite
cp -r jupyter-lab-linux-x64/ ~/.local/share/jupyter-lab
```

Create desktop icon
```
nvim ~/.local/share/applications/JupyterLab.desktop
```
```
[Desktop Entry]
Name=Jupyter Lab
Exec=/home/edunter/.local/share/jupyter-lab/jupyter-lab
Icon=/home/edunter/.local/share/jupyter-lab/jupyter-lab-dracula-icon.png
StartupWMClass=electron-jupyter-lab
Type=Application
Categories=Utility;
```

Download icons
- [desktop shortcut icon](https://github.com/EDUnter/development-enviroment/blob/main/jupyter-lab/jupyter-lab-icon.png)
- [dracula desktop shortcut icon](https://github.com/EDUnter/development-enviroment/blob/main/jupyter-lab/jupyter-lab-dracula-icon.png)
```
cp ~/Downloads/jupyter-lab-icon.png /home/edunter/.local/share/jupyter-lab/jupyter-lab-icon.png
cp ~/Downloads/jupyter-lab-icon.png /home/edunter/.local/share/jupyter-lab/jupyter-lab-dracula-icon.png
```

Notes:  
If the window appears open in a new icon on dock use xprop and click in the open webui app to check the WM_CLASS.  
If its WM_CLASS differs from the desktop parameter `StartupWMClass`, change it accordingly.
```
xprop | grep WM_CLASS
```

## Create a service for Jupyter Lab
```
sudo nvim /etc/systemd/system/jupyter-lab.service
```
```
[Unit]
Description=Jupyter Lab
After=network.target

[Service]
Type=simple
User=edunter
Group=edunter
WorkingDirectory=/home/edunter
ExecStart=/home/edunter/.pyenv/shims/jupyter-lab --no-browser --ip=0.0.0.0
Restart=always

[Install]
WantedBy=multi-user.target
```
```
sudo systemctl daemon-reload
sudo systemctl start jupyter-lab
sudo systemctl enable jupyter-lab
sudo systemctl status jupyter-lab
```

## Run Jupyter Lab on terminal
Add alias for `jupyter-lab`
```
nvim .bashrc
```
```
alias jupyter-lab='/home/edunter/.local/share/jupyter-lab/jupyter-lab'
```

```
. .bashrc
jupyter-lab
```

## Keybinds
```
Name -> jupyter-lab
Command -> /home/edunter/.local/share/jupyter-lab/jupyter-lab
Shortcut -> Super+j
```
