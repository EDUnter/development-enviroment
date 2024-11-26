# Open Webui

## Install Open Webui
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

## Run Open Webui
Open Webui will be accessible through http://localhost:8080
```
poetry run open-webui serve
```
