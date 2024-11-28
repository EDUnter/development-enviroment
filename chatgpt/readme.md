# Chat GPT

## Run Open WebUI as a desktop app

Install nodejs and electron

sudo dnf install nodejs npm
sudo npm install -g electron

Create the desktop app

mkdir electron-chatgpt
cd electron-chatgpt
npm init -y
npm install electron --save-dev
nvim index.js

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
    mainWindow.loadURL('https://chatgpt.com/'); // Replace with your desired URL

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

Test the app

npx electron .

Package the app

sudo npm install -g electron-packager
electron-packager . open-webui --platform=linux --arch=x64 --overwrite
cp -r open-webui ~/.local/share/

Create desktop icon

nvim ~/.local/share/applications/OpenWebUI.desktop

[Desktop Entry]
Name=Open WebUI
Exec=/home/edunter/.local/share/open-webui/open-webui
Icon=/home/edunter/.local/share/open-webui/open-webui-icon.png
StartupWMClass=electron-open-webui
Type=Application
Categories=Utility;

Notes:
If the window appears open in a new icon on dock use xprop and click in the open webui app to check the WM_CLASS.
If its WM_CLASS differs from the desktop parameter StartupWMClass, change it accordingly.

xprop | grep WM_CLASS
