# dev-instructions

Some general tips, tricks and instructions on how to start development with different tools.
Intended for quick reference: "How it was done...".
Everything is in random order

## Python

Python is usually already installed on debian/ubuntu based linuxes.
Command `python` usually refers to Python 2.x.x and `python3` refers to Python 3.x.x.

Some really useful pacakges to be installed:
```bash
sudo apt-get install python-pip
```
to install PyPi, Python Package Index, which you can use to add more awesome python packages. See https://pypi.python.org/pypi for more details.

```bash
sudo apt-get install ipython
```
Replaces the default python-interpreter with more user-friendlier version.


### Setting up virtual environments
Package `virtualenv` allows you to work easily with different python projects that might require different versions of Python and its packages.
Install simply with
```bash
sudo apt-get install python-virtualenv
```

To get most out of virtual environments, `virtualenvwrapper` is needed (see: https://virtualenvwrapper.readthedocs.org/en/latest/install.html ):
```bash
sudo pip install virtualenvwrapper
```
There are few more steps to do:
- Create folder `.virtualenvs` into your home folder.
- Then add these three lines to your `.bashrc` (or `.profile` etc.)
  - `devel` should be pointing your project folder (i.e. it can be different than `devel`)
```bash
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/devel
source /usr/local/bin/virtualenvwrapper.sh
```
- and finally use the updated bashrc: `source ~/.bashrc`.

Nex you want to start a project, say myproject. For that, create folder `myproject` under `devel`.
To create virtualenvironment that, when activated, automagically jumps to the project folder, use:
```bash
mkvirtualenv -a devel/myproject/ -i ipython -p python3 myproject
```
This will also install `ipython` and uses Python 3 rather than Python 2. Once the environment has been created it automatically activates and redirects to `devel/myproject`. To test that you have correct environment, check

    python --version

that should print "Python 3.".

- To list all created environments, use `workon`
- To **activate** the environment, use: `workon myproject`
- To **deactivate** the environment, use `deactivate`

