# Python

## PyEnv
Install PyEnv
```
curl https://pyenv.run | bash
```
Add PyEnv to `.bashrc`
```
nvim ~/.bashrc
```
```
# PyEnv
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```
Reload bash shell
```
. .bashrc
```

## Install Python through PyEnv
First install sqlite
```
sudo dnf install sqlite sqlite-devel
```

Install python 3.11.10, as an example
```
pyenv install 3.11.10
```
Add python3.11.10 to pyenv global
```
pyenv global python3.11.10
# Append multiple python versions to pyenv
pyenv global python3.11.10 python3.13.0
```

