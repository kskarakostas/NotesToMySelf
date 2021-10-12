# Python Reqs

**Packages**
```bash
sudo apt-get install software-properties-common
sudo apt-add-repository universe
sudo apt-get update
sudo apt-get install git-all

sudo apt install python3-pip unzip python3-virtualenv python3-psutil xvfb -y
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
