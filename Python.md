# Python Reqs

# Table of Contents
1. Packages
2. Python Multiple versions
3. Python virtual ENV
4. Generic Tricks
 4.1. Get all ipython history
 4.2. Reload module


**Packages**
```bash
sudo apt-get install software-properties-common
sudo apt-add-repository universe
sudo apt-get update
sudo apt-get install git-all

sudo apt install python3-pip unzip python3-virtualenv python3-psutil xvfb -y
```
# Python Multiple versions

```bash
sudo apt-get install software-properties-common

# adding python repository 
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update

# install python 3.10
sudo apt install python3.10
```

Creating virtual environments with different versions of python

```bash

#if venv package for that version is not installed already
sudo apt install python9.6-venv
python9.6 -m venv p96_env
source p96_env/bin/activate
python --version

```


# Python virtual ENV

**Set Up**
```bash
sudo apt-get install python-env
mkdir ./virtualenv
virtualenv -p /usr/bin/python2.7 ./virtualenv
```

**Set Up [2]**
```bash
sudo apt-get install python-env
mkdir ~/.p3_test
virtualenv -p `which python3` ~/.p3_test

if grep -Fxq "p3_test" $HOME/.bashrc
then
	echo 'alias p3_test="source $HOME/.p3_test/bin/activate"' >> $HOME/.bashrc
fi
```


**Activate**
```bash
source $HOME/.p3_test/bin/activate
```

**Deactivate**
```bash
deactivate
```

**Add alias**
```bash
alias p3_test='source $HOME/.p3_test/bin/activate'

```
# Generic Tricks

## Ipython history

From within ipython save the history to filename.txt
```bash
%history -g -f filename.txt
```

## Ipython reload module

From within ipython save the history to filename.txt
```python
%load_ext autoreload
%autoreload 2
```
