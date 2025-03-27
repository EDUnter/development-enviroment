# Bolt

## Install Bolt
Clone repo
```
git clone https://github.com/coleam00/bolt.new-any-llm.git
cd bolt.new-any-llm/
```

Provide Ollama API key
```
mv .env.example .env
nvim .env.example
```
```
OLLAMA_API_BASE_URL=http://127.0.0.1:11434
```

Install dependencies and test it
```
sudo npm install -g pnpm
pnpm install
pnpm run dev
```

## Run Bolt as a desktop app
Install nodejs, npm and electron
```
sudo dnf install nodejs npm
sudo npm install -g electron
```

Create the desktop app
```
mkdir electron-bolt
cd electron-bolt
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
    mainWindow.loadURL('http://localhost:3000'); // Replace with your desired URL

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
electron-packager . bolt --platform=linux --arch=x64 --overwrite
cp -r bolt-linux-x64/ ~/.local/share/bolt
```

Create desktop shortcut
```
nvim ~/.local/share/applications/bolt.desktop
```
```
[Desktop Entry]
Name=Bolt
Exec=/home/edunter/.local/share/bolt
Icon=/home/edunter/.local/share/bolt/bolt-icon.png
StartupWMClass=electron-bolt
Type=Application
Categories=Utility;
```

Download [desktop shortcut icon](https://github.com/EDUnter/development-enviroment/blob/main/bolt/bolt-icon.png)
```
cp -r ~/Downloads/bolt-icon.png ~/.local/share/bolt
```

Notes: If the window appears open in a new icon on dock use xprop and click in the open webui app to check the WM_CLASS. If its WM_CLASS differs from the desktop parameter StartupWMClass, change it accordingly.
```
xprop | grep WM_CLASS
```

# Keybindings
```
Name -> bolt
Command -> /home/edunter/.local/share/bolt/bolt
Shortcut -> Super+o
```
