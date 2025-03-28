# Cursor

## Install Cursor
Download [Cursor](https://www.cursor.com/)

Make app image executable
```
chmod +x ~/Downloads/Cursor-0.47.9-x86_64.AppImage
```

## Install Ngrok
Install snapd
```
sudo dnf install -y snapd
```

Install ngrok
```
sudo snap install ngrok
sudo reboot
```

Go to [Ngrok](https://dashboard.ngrok.com/get-started/setup/linux) and save token
```
ngrok config add-authtoken <token>
```

## Install LMStudio
Go to [LMStudio](https://lmstudio.ai/download)
```
chmod +x ~/Downloads/LM-Studio-0.3.14-5-x64.AppImage
```

Run LMStudio App Image. Then go to `Discover -> Model Search -> search for qwen code and install it`.
After that, load the model. Let's start to configure LMStudio.
