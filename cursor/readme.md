# Cursor

## Install Cursor
Download [Cursor](https://www.cursor.com/)

Make app image executable
```
chmod +x ~/Downloads/Cursor-0.47.9-x86_64.AppImage
```

## Install Cloudflare and setup a tunnel
Download [Cloudflare .rpm](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/)
```
sudo dnf install -y ~/Downloads/cloudflared-linux-x86_64.rpm
```

Follow this [instructions](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/) to setup a tunnel (step 1 should be enough).

Create the tunnel
```
OLLAMA_ORIGINS=* ollama serve
cloudflared tunnel --url http://localhost:11434 --http-host-header="localhost:11434"
```

## Configure cursor
Pull a coding model
```
ollama pull qwen2.5-coder
```

Go to `Cursor Settings -> Models -> Click Add model and write 'qwen2.5-coder'.
Then scroll down to OpenAI API Key and write 'ollama' as the api key.
Also, under 'Override OpenAI Base URL' put the link cloudflare provided for accessing the tunnel and add '/v1' to the end of it.

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

Create the tunnel
```
ngrok http 11434 --host-header="localhost:11434"
```
Now, return to [Configure cursor](#configure-cursor).

