# Poetry

### Step 1 - Install Poetry

After installing poetry reload terminal

```shell
python3 -m pip install poetry
```

### Step 2 - Verify Poetry Installation

```shell
poetry --version
```

### Step 3 - Initialize Poetry in your Jupyter Notebook project

```shell
poetry init
```

### Step 4 - Install dependencies

```shell
poetry add tensorflow matplotlib
```

### Step 5 - Get Poetry Environment Info Path


```shell
poetry env info --path
```

### Step 6 - Activate the Poetry Environment

```shell
source your-poetry-venv/bin/activate
```

### Step 7: Add the Poetry Environment as a Jupyter Kernel

```shell
ipython kernel install --name "your-new-poetry-env-name" --user
# OR poetry run ipython kernel install --name "tessaract-ocr-python-tuto" --user
