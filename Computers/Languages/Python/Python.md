# Packages
<hr width=100% style="border: 1px solid rgb(200,200,200)">

[Conflicting Python versions](https://discuss.python.org/t/sharing-packages-between-different-python-versions/52279/5)
## Package Directory
<hr width=75% style="border: 1px solid rgb(175,175,175)">

`/usr/lib/python3/dist-packages`
`/usr/lib/python3.##/`


## Package Managers
<hr width=75% style="border: 1px solid rgb(175,175,175)">

`apt`
`pip`
`pipx`

### `apt`
<hr width=25% style="border: 1px solid rgb(150,150,150)">

Friendly

### `pip`
<hr width=25% style="border: 1px solid rgb(150,150,150)">

Always use [pip](https://pip.pypa.io/en/stable/user_guide/#context-and-followup) via a Python executable (of any version)
`$ python3.10 -m pip COMMAND`
`$ python3.10 -m pip install --upgrade pip`
`$ python3.10 -m pip check`
`$ alias pip=python3.10 -m pip`
#### Installing Packages
`$ pip install "somepackage>=1,<2"`  -  to run pip module as script inside Python interpreter
`$ pip install "somepackage==1.6.9"`  -  exact
`$ pip install "somepackage~=1.6.0"`  -  Any `1.6.*` that's geq `>=1.6.0`
#### Upgrading Packages
`$ pip install --upgrade somepackage`
#### Listing Packages
`$ pip list --not-required --user`
- `--not-required`  -  packages which are not solely a dependency
- `--user`  -  locally installed packages
#### Other
##### site-packages
`$ python3.10 -c "import sys; print(sys.path)"`
##### Distro Specific `pip`
Using [ensurepip](https://docs.python.org/3/library/ensurepip.html)
`$ pythonX.Y -m ensurepip --upgrade`
By default installs `pipX` & `pipX.Y` into the currently active virtual environment, otherwise:
- `--user`  -  Installs `pip` locally in user site packages (`~/.local/lib/python3.10/site-packages`)
- `--root DIR`  -  Installs `pip` using `DIR` as the root directory.
- `--altinstall`  -  Does **not** install `pipX`
- `--default-pip`  -  Additionally installs `pip`

## Virtual Environments
<hr width=75% style="border: 1px solid rgb(175,175,175)">

 - [List of Environments](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe)
 - `virtualenv`
 - `venv`
 - `pipenv`
 - `pipx`

### `virtualenv`
<hr width=25% style="border: 1px solid rgb(150,150,150)">

#### Creation
##### isolated via `pipx`
`$ pipx install virtualenv`
`$ virtualenv -p /usr/bin/python3.10 myenv`
##### system-wide via `python`
`$ python3 -m pip install --user virtualenv`
`$ python3 -m virtualenv -p /usr/bin/python3.10 myenv`
##### `virtualenv` [Options](https://virtualenv.pypa.io/en/latest/cli_interface.html)
- `--system-site-packages`  -  include global system packages
- `--python` or `-p`  -  python executable
#### Usage
##### Directly
`$ myenv/bin/pip install whatever`  -  only installed to `myenv`
##### Activated
`$ source myenv/bin/activate`
`(myenv) $ pip install whatever`  -  only installed to `myenv`
`(myenv) $ deactivate`
#### requirements.txt
`(myenv) $ pip freeze > requirements.txt`
`(myenv) $ pip install -r requirements.txt`


> [!note]
> `venv` is a [subset](https://virtualenv.pypa.io/en/latest/) of `virutalenv`
> `python3.10 -m venv ~/myenv`

### `pipenv`
<hr width=25% style="border: 1px solid rgb(150,150,150)">

#### Installation
`$ /usr/bin/python3 -m pip install --user pipenv`  -  choose Python version
`$ /usr/bin/python3 -m pip install --user --upgrade pipenv`  -  upgrades `pipenv`
#### Usage
`$ cd myproject`
`$ echo "import whatever" > main.py`
`$ /usr/bin/python3 -m pipenv install whatever`
`$ /usr/bin/python3 -m pipenv run /usr/bin/python3.10 main.py`
#### Project Migration
`$ cd myproject`
`$ /usr/bin/python3 -m pipenv -rm`  -  Destroys global mapping of *environment* to directory
`$ mv ../myproject $NEWPATH && cd $NEWPATH/myproject`
`$ /usr/bin/python3 -m pipenv install`  -  Recreates the *environment* in the new directory
##### `pipenv` Options
- 

---
# Other
<hr width=100% style="border: 1px solid rgb(200,200,200)">

## Python Version Specific Modules
<hr width=75% style="border: 1px solid rgb(175,175,175)">

`$ python3.10`
`>>> help('modules')`
`ModuleNotFoundError: No module named '_cffi_backend'`
`>>> exit()`
`python3 -m pip install cffi`
`$ python3.10 -m pip install --upgrade pip`


/snap/gtk-common-themes/1535/share/icons/elementary-xfce/apps/{16,24,32,48,64,129}/atom.png
/snap/kde-frameworks-5-core18/35/usr/share/icons/breeze/apps/48