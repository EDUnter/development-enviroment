# SearXNG

## Install SearXNG

```
cd ~/Development/
git clone https://github.com/searxng/searxng.git
cd searxng
nvim searx/settings.yml
```
Add json to "formats"
```
  formats:
    - html
    - json
```
```
sudo make docker.build
sudo docker image ls
PORT=32768
```

## Run SearXNG
```
docker run --rm -d -p 32768:8080 -v "${PWD}/searxng:/etc/searchxng" -e "BASE_URL=http://localhost:$PORT/" -e "INSTANCE_NAME=searxng_instance" searxng/searxng
```
