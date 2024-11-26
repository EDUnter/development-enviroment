# Open Webui

## Install Open Webui
Install [poetry]()

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

Make sure global python from pyenv is from 3.11.10 version before running the command down below
```
poetry env use python
```

Install open-webui
```
poetry add open-webui
```

## Run OpenWebui
```
poetry run open-webui serve
```
