# Poetry

### Step 1 - Install Poetry

After installing poetry reload terminal

```shell
python -m pip install poetry
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

Before installing any dependency
```shell
sudo dnf group install "Development Tools"
sudo dnf install python3-devel python3-pip pkgconf cython
```

```shell
poetry add tensorflow matplotlib
```

If some dependency is having trouble building by source we can use a wheel.  
Exmaple for numpy
```shell
poetry shell
pip wheel --no-cache-dir --use-pep517 numpy==2.0.2
export PKG_CONFIG_PATH=$(python3 -m sysconfig | grep configdir | cut -d'"' -f2)/pkgconfig
```

If bulding, using the commands from above also fails.
```shell
poetry run pip install numpy
```

Check numpy version
```shell
poetry shell
python -c "import numpy; print(numpy.__version__)"e
```

### Step 5 - Get Poetry Environment Info Pato, in case its needed manual debugging

```shell
poetry env info
```

### Step 6 - Activate the Poetry Environment, in case its needed to manual activate. Otherwise, just use poerty shell to automatically activate poetry.

```shell
source your-poetry-venv/bin/activate
```

### Step 7: Add the Poetry Environment as a Jupyter Kernel

```shell
poetry shell
poetry run ipython kernel install --name "your-new-poetry-env-name" --user
```

### Other usefull stuff

#### Change poetry python version
```shell
poetry env use python
# poetry env use $(which python3.11)
# poetry env use /path/to/python3.11
```

#### Manage Jupyter Kernels
List jupyter kernels
```shell
jupyter kernelspec list
```

Unninstall jupyter kernel
```shell
jupyter kernelspec uninstall <kernel-name>
```

#### Check which packages were installed without poetry
```shell
poetry run pip freeze
```
