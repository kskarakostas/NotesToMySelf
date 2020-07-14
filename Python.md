# Python virtual ENV

**Set Up**
```bash
$ sudo apt-get install python-env
$ mkdir ./virtualenv
$ virtualenv -p /usr/bin/python2.7 ./virtualenv
```

**Set Up [2]**
```bash
$ sudo apt-get install python-env
$ mkdir ~/.p3_test
$ virtualenv -p `which python3` ~/.p3_test
```


**Activate**
```bash
$ source $HOME/.p3_test/bin/activate
```

**Deactivate**
```bash
$ deactivate
```

**Add alias**
```bash
alias p3_test='source $HOME/.p3_test/bin/activate'

```
